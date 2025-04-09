---
product: campaign
title: Arquitetura geral do Campaign Classic
description: Aprenda a instalar e configurar Campaign Classic
feature: Installation, Architecture
audience: installation
content-type: reference
level: Intermediate, Experienced
topic-tags: architecture-and-hosting-models
exl-id: 04e6dc17-427b-4745-84cc-bf45c03dbf81
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '1342'
ht-degree: 0%

---

# Arquitetura geral{#general-architecture}



A solução Adobe Campaign típica implantação consiste nos seguintes componentes:

* **Ambiente personalizado do cliente**

  Interface gráfica intuitiva na qual os usuários podem se comunicar e rastrear ofertas de marketing, criar campanhas, revisar e gerenciar todas as atividades de marketing, programas e planos, incluindo emails, fluxos de trabalho e páginas de aterrissagem, criar e gerenciar perfis de clientes e definir tipos de público-alvo do cliente.

* **Ambiente de desenvolvimento**

  Software do lado do servidor que executa as campanhas de marketing por meio de canais de comunicação escolhidos, incluindo emails, SMS, notificações por push, correspondência direta, Web ou redes sociais, com base nas regras e fluxos de trabalho definidos na interface do usuário.

* **Contêineres do Banco de Dados**

  Com base na tecnologia de banco de dados relacional, o banco de dados do Adobe Campaign armazena todas as informações dos clientes, componentes da campanha, ofertas e workflows, bem como resultados da campanha em containers de banco de dados do cliente.

O Adobe Campaign é baseado em uma SOA (Service-Oriented Architecture, arquitetura orientada a serviços) e inclui vários módulos funcionais. Esses módulos podem ser implantados em um ou mais computadores, em uma ou várias instâncias, dependendo das restrições em termos de escalabilidade, disponibilidade e isolamento de serviço. O escopo das configurações de implantação é, portanto, muito amplo e abrange um único computador central até configurações que incluem vários servidores dedicados em vários sites.

>[!NOTE]
>
>Como fornecedor de software, especificamos infraestruturas de hardware e software compatíveis. As recomendações de hardware fornecidas aqui são somente para fins informativos e baseiam-se em nossa experiência. A Adobe não será responsável por quaisquer decisões tomadas com base nelas. Isso também dependerá de suas regras e práticas de negócios e da importância e dos níveis de desempenho necessários do projeto.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Salvo indicação expressa em contrário, a instalação, as atualizações e a manutenção de todos os componentes de uma plataforma Adobe Campaign são de responsabilidade do(s) administrador(es) da máquina que os hospeda. Isso inclui a implementação dos pré-requisitos para aplicativos do Adobe Campaign, bem como a conformidade com a [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md) do Campaign entre componentes.

## Camada de apresentação {#presentation-layer}

O aplicativo pode ser acessado de diferentes maneiras, dependendo das necessidades dos usuários: rich client, Thin client ou API integration.

* **Cliente avançado**: a principal interface de usuário do aplicativo é um cliente avançado, em outras palavras, um aplicativo nativo (Windows) que se comunica com o servidor de aplicativos do Adobe Campaign exclusivamente com protocolos padrão de Internet (SOAP, HTTP etc.). Esse console oferece excelente facilidade de uso para produtividade, usa pouca largura de banda (por meio do uso de um cache local) e foi projetado para facilitar a implantação. Esse console pode ser implantado a partir de um navegador da Internet, pode ser atualizado automaticamente e não requer nenhuma configuração de rede específica porque gera apenas tráfego HTTP(S).
* **Thin client**: determinadas partes do aplicativo podem ser acessadas por meio de um navegador da Web simples usando uma interface de usuário do HTML, incluindo o módulo de relatórios, estágios de aprovação de entrega, funcionalidades do módulo Marketing Distribuído (central/local), monitoramento de instâncias etc. Esse modo permite incluir funcionalidades do Adobe Campaign em uma intranet ou extranet.
* **Integração por meio das APIs**: em certos casos, o sistema pode ser chamado a partir de um aplicativo externo usando as APIs de Serviços Web expostas pelo protocolo SOAP.

## Camada de aplicativo lógica {#logical-application-layer}

Adobe Campaign é uma única plataforma com diferentes aplicativos que se combinam para criar uma arquitetura aberta e dimensionável. A plataforma de Adobe Campaign é escrita em uma camada de aplicativo flexível e é facilmente configurável para atender às necessidades comerciais de uma empresa. Isso acomoda as crescentes necessidades da empresa a partir de uma perspectiva funcional, bem como de uma perspectiva técnica. A arquitetura distribuída garante que o sistema linear escalabilidade escala de milhares de mensagens para milhões de mensagens.

Adobe Campaign depende de um conjunto de processos de lado do servidor que trabalham juntos.

Os principais processos são:

**Servidor de aplicativos** (nlserver web)

Esse processo expõe a gama completa de funcionalidades do Adobe Campaign por meio de APIs de serviços da Web (SOAP - HTTP + XML). Além disso, ele pode gerar dinamicamente as páginas da Web usadas para o acesso baseado em HTML (relatórios, formulários Web etc.). Para fazer isso, esse processo inclui um servidor JSP Apache Tomcat. Esse é o processo ao qual o console se conecta.

**Mecanismo de fluxo de trabalho** (nlserver wfserver)

Ele executa os processos de workflow definidos no aplicativo.

Também lida com workflows técnicos executados periodicamente, incluindo:

* Rastreamento: recuperação e consolidação de logs de rastreamento. Ela permite recuperar os logs do servidor de redirecionamento e criar os indicadores agregados usados pelo módulo de relatórios.
* Limpeza: limpeza do banco de dados. Usado para eliminar registros antigos e evitar que o banco de dados cresça exponencialmente.
* Faturamento: envio automático de um relatório de atividade para a plataforma (tamanho do banco de dados, número de ações do marketing, número de perfis ativos etc.).

**Servidor de** entrega (nlserver mta)

O Adobe Campaign tem a funcionalidade nativa de transmissão por email. Esse processo funciona como um agente de transferência de email SMTP (MTA). Ele executa a personalização &quot;um para um&quot; das mensagens e lida com a entrega física. Ele funciona usando processos de entrega e lida com tentativas automáticas. Além disso, quando o rastreamento é ativado, ele substitui automaticamente os URLs para que eles apontem para o servidor de redirecionamento.

Esse processo pode lidar com a personalização e o envio automático para um roteador de terceiros para SMS, fax e correspondência direta.

**Servidor de redirecionamento** (nlserver webmdl)

Para email, Adobe Campaign lida automaticamente com aberturas e rastreamento de cliques (rastreamento transacionais no nível do site é uma possibilidade adicional). Para isso, os URLs incorporados nas mensagens de email são reescritos solicitar para apontar para essa módulo, que registra a passagem das usuário da internet antes de redirecioná-las para a URL necessária.

Para garantir maior disponibilidade, esse processo é totalmente independente do banco de dados: os outros processos do servidor se comunicam com ele usando chamadas SOAP (HTTP, HTTP(S) e XML) somente. Tecnicamente, essa funcionalidade é implementada em uma extensão módulo de um servidor HTTP (extensão ISAPI em IIS, ou um DSO Apache módulo etc.) e está disponível apenas no Windows.

Outros processos mais técnicos também estão disponíveis:

**Gerenciamento de emails rejeitados** (nlserver inMail)

Esse processo permite que você colete automaticamente emails de caixas de correio configuradas para receber mensagens devolvidas que são retornadas em caso de falha de delivery. Essas mensagens são submetidas a processamento com base em regras para determinar os motivos para a não entrega (recipient desconhecido, cota excedida etc.) e para atualizar o status do delivery no banco de dados.

Todas essas operações são totalmente automáticas e pré-configuradas.

**Status de entrega de SMS** (nlserver sms)

Esse processo pesquisa o roteador SMS para coletar o status do progresso e atualizar o banco de dados.

**Gravação de mensagens** de log (nlserver syslogd)

Esse processo técnico captura mensagens de log e rastreamentos gerados pelos outros processos e as grava no disco rígido. Isso disponibiliza amplas informações para diagnóstico em caso de problemas.

**Gravando logs de rastreamento** (nlserver trackinglogd)

Esse processo salva em disco os logs de rastreamento gerados pelo processo de redirecionamento.

**Gravando eventos de entrada** (nlserver interactiond)

Esse processo garante o registro em disco de eventos de entrada, dentro da estrutura de interação.

**Supervisão de módulos** (watchdog nlserver)

Esse processo técnico atua como um processo primário que gera os outros. Ele também os monitora e os relaunifica automaticamente em caso de incidentes, mantendo assim o tempo máximo de atividade do sistema.

**Servidor de** estatísticas (nlserver stat)

Esse processo mantém estatísticas sobre o número de conexões, as mensagens enviadas para cada servidor de email para as quais as mensagens são enviadas, bem como suas limitações (maior número de conexões simultâneas, mensagens por hora/e ou conexão). Também permite federar várias instâncias ou máquinas se elas compartilham os mesmos endereços IP públicos.

>[!NOTE]
>
>A lista completa de módulos do Adobe Campaign está disponível em [este documento](../../production/using/operating-principle.md).

## Camada de persistência {#persistence-layer}

O banco de dados é usado como uma camada de persistência e contém quase todas as informações gerenciadas pelo Adobe Campaign. Isso inclui dados funcionais (perfis, assinaturas, conteúdo etc.), dados técnicos (tarefas e logs do delivery, logs de rastreamento etc.) e dados de trabalho (compras, leads).

A confiabilidade do banco de dados é de extrema importância porque a maioria dos componentes do Adobe Campaign requer acesso ao banco de dados para executar suas tarefas (com a exceção notável do módulo de redirecionamento).

A plataforma vem predefinida com um armazém de dados centralizado em marketing ou pode facilmente se encaixar em um armazém de dados e esquema existentes usando qualquer um dos principais Sistemas de Gerenciamento de Banco de Dados Relacional (RDBMS). Todos os dados no data mart são acessados pela plataforma Adobe Campaign por meio de chamadas SQL do Adobe Campaign para o banco de dados. O Adobe Campaign também fornece um complemento completo de ferramentas de ETL (Extract Transform and Load, Transformação e Carregamento de Extração) para executar a importação e exportação de dados para dentro e para fora do sistema.
