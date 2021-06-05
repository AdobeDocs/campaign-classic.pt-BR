---
product: campaign
title: Arquitetura geral
description: Saiba como instalar e configurar o Campaign Classic.
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: 04e6dc17-427b-4745-84cc-bf45c03dbf81
source-git-commit: 4a41aea9edfe5e6ca0454049cbb2892449eec153
workflow-type: tm+mt
source-wordcount: '1340'
ht-degree: 0%

---

# Arquitetura geral{#general-architecture}

A implantação típica da solução Adobe Campaign consiste nos seguintes componentes:

* **Ambiente de cliente personalizado**

   Interface gráfica intuitiva na qual os usuários podem se comunicar e rastrear ofertas de marketing, criar campanhas, revisar e gerenciar todas as atividades, programas e planos de marketing - incluindo emails, fluxos de trabalho e páginas de aterrissagem -, criar e gerenciar perfis de clientes e definir tipos de público-alvo do cliente.

* **Ambiente de desenvolvimento**

   Software do lado do servidor que executa as campanhas de marketing por meio de canais de comunicação escolhidos, incluindo emails, SMS, notificações por push, mala direta, Web ou social, com base nas regras e fluxos de trabalho definidos na interface do usuário.

* **Contêineres de Banco de Dados**

   Com base na tecnologia de banco de dados relacional, o banco de dados do Adobe Campaign armazena todas as informações dos clientes, componentes da campanha, ofertas e workflows, bem como os resultados da campanha em contêineres de banco de dados do cliente.

A Adobe Campaign é baseada em uma SOA (Service Oriented Architecture, arquitetura orientada a serviços) e inclui vários módulos funcionais. Esses módulos podem ser implantados em um ou mais computadores, em uma ou várias instâncias, dependendo das restrições em termos de escalabilidade, disponibilidade e isolamento do serviço. O escopo das configurações de implantação é, portanto, muito amplo e abrange um único computador central, inclusive vários servidores dedicados em vários sites.

>[!NOTE]
>
>Como fornecedor de software, especificamos infraestruturas de hardware e software compatíveis. As recomendações de hardware fornecidas aqui são apenas para fins informativos e são baseadas em nossa experiência. A Adobe não é responsável pelas decisões tomadas com base nas mesmas. Ele também dependerá de suas regras e práticas de negócios, bem como da importância e dos níveis de desempenho necessários do projeto.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Caso contrário, a instalação, as atualizações e a manutenção em todos os componentes de uma plataforma Adobe Campaign são da responsabilidade do(s) administrador(es) da máquina que os hospeda. Isso inclui a implementação dos pré-requisitos para aplicativos do Adobe Campaign, bem como a conformidade com a [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md) entre componentes do Campaign.

## Camada de apresentação {#presentation-layer}

O aplicativo pode ser acessado de diferentes maneiras, dependendo das necessidades dos usuários: Integração avançada de cliente, cliente thin ou API.

* **Cliente** avançado: A principal interface de usuário do aplicativo é um cliente avançado, em outras palavras, um aplicativo nativo (Windows) que se comunica com o servidor de aplicativos Adobe Campaign exclusivamente com protocolos padrão de Internet (SOAP, HTTP etc.). Esse console oferece excelente facilidade de uso para produtividade, usa pouca largura de banda (por meio do uso de um cache local) e foi projetado para facilitar a implantação. Esse console pode ser implantado a partir de um navegador da Internet, pode ser atualizado automaticamente e não requer nenhuma configuração de rede específica porque gera apenas tráfego HTTP(S).
* **Cliente** fino: Algumas partes do aplicativo podem ser acessadas por um navegador da Web simples usando uma interface de usuário HTML, incluindo o módulo de relatórios, estágios de aprovação de delivery, funcionalidades do módulo Marketing Distribuído (central/local), monitoramento de instância etc. Esse modo possibilita incluir as funcionalidades do Adobe Campaign em uma intranet ou uma extranet.
* **Integração por meio das APIs**: Em certos casos, o sistema pode ser chamado de aplicativo externo usando as APIs de serviços da Web expostas por meio do protocolo SOAP.

## Camada lógica do aplicativo {#logical-application-layer}

O Adobe Campaign é uma plataforma única com diferentes aplicativos que se combinam para criar uma arquitetura aberta e escalável. A plataforma Adobe Campaign é escrita em uma camada de aplicativo flexível e pode ser facilmente configurada para atender às necessidades comerciais de uma empresa. Isso acomoda as necessidades crescentes da empresa de uma perspectiva funcional e de uma perspectiva técnica. A arquitetura distribuída garante a escalabilidade linear do sistema, de milhares de mensagens a milhões de mensagens.

O Adobe Campaign depende de um conjunto de processos do lado do servidor que funcionam juntos.

Os principais processos são:

**Servidor de aplicativos**  (nlserver web)

Esse processo expõe toda a gama de funcionalidades do Adobe Campaign por meio de APIs de Serviços da Web (SOAP - HTTP + XML). Além disso, ele pode gerar dinamicamente as páginas da Web usadas para acesso baseado em HTML (relatórios, formulários Web etc.). Para isso, esse processo inclui um servidor JSP Apache Tomcat. Esse é o processo ao qual o console se conecta.

**Mecanismo de fluxo de trabalho**  (nlserver wfserver)

Ele executa os processos de workflow definidos no aplicativo.

Também lida com workflows técnicos executados periodicamente, incluindo:

* Rastreamento: Recuperação e consolidação de logs de rastreamento. Ele permite recuperar os logs do servidor de redirecionamento e criar os indicadores agregados usados pelo módulo de relatórios.
* Limpeza: Limpeza do banco de dados. Usado para limpar registros antigos e evitar o crescimento exponencial do banco de dados.
* Faturamento: Envio automático de um relatório de atividade para a plataforma (tamanho do banco de dados, número de ações de marketing, número de perfis ativos etc.).

**Servidor de entrega**  (nlserver mta)

A Adobe Campaign tem funcionalidade nativa de transmissão de email. Esse processo funciona como um agente de transferência de email SMTP (MTA). Ele executa a personalização &quot;um para um&quot; de mensagens e manipula sua entrega física. Funciona usando tarefas de delivery e lida com tentativas automáticas. Além disso, quando o rastreamento é ativado, ele substitui automaticamente os URLs para que apontem para o servidor de redirecionamento.

Esse processo pode lidar com a personalização e o envio automático para um roteador de terceiros para SMS, fax e mala direta.

**Servidor de redirecionamento**  (nlserver webmdl)

Para email, o Adobe Campaign trata automaticamente o rastreamento de cliques e aberturas (o rastreamento transacional no nível do site é uma outra possibilidade). Para isso, os URLs incorporados nas mensagens de email são reescritos para apontar para esse módulo, que registra a passagem do usuário da Internet antes de redirecioná-los para o URL necessário.

Para garantir a maior disponibilidade, esse processo é totalmente independente do banco de dados: os outros processos de servidor se comunicam com ele usando chamadas SOAP (HTTP, HTTP(S) e XML) somente. Tecnicamente, essa funcionalidade é implementada em um módulo de extensão de um servidor HTTP (extensão ISAPI no IIS, um módulo DSO Apache etc.) e está disponível somente no Windows.

Outros processos mais técnicos também estão disponíveis:

**Gestão de emails de devolução**  (nlserver inMail)

Esse processo permite que você selecione automaticamente emails de caixas de correio configuradas para receber mensagens devolvidas em caso de falha de delivery. Essas mensagens passam por um processamento com base em regras para determinar os motivos para não entrega (recipient desconhecido, cota excedida, etc.) e para atualizar o status do delivery no banco de dados.

Todas essas operações são totalmente automáticas e pré-configuradas.

**Status do delivery de SMS**  (nlserver sms)

Esse processo pesquisa o roteador SMS para coletar o status de progresso e atualizar o banco de dados.

**Gravando mensagens de log**  (nlserver syslogd)

Esse processo técnico captura mensagens de log e rastreamentos gerados pelos outros processos e as grava no disco rígido. Isso disponibiliza amplas informações para diagnóstico em caso de problemas.

**Gravação de logs de rastreamento**  (nlserver trackinglogd)

Esse processo salva em disco os logs de rastreamento gerados pelo processo de redirecionamento.

**Gravação de eventos de entrada**  (nlserver interactiond)

Esse processo garante o registro no disco de eventos de entrada, dentro da estrutura de Interação.

**Supervisão de módulos**  (nlserver watchdog)

Este processo técnico funciona como um processo principal que cria os outros. Ele também os monitora e reinicializa automaticamente em caso de incidentes, mantendo assim o tempo máximo de atividade do sistema.

**Servidor**  de Estatísticas (nlserver stat)

Esse processo mantém estatísticas sobre o número de conexões, as mensagens enviadas para cada servidor de email para o qual as mensagens são enviadas, bem como suas limitações (o maior número de conexões simultâneas, mensagens por hora/e ou conexão). Também permite federar várias instâncias ou máquinas se elas compartilharem os mesmos endereços IP públicos.

>[!NOTE]
>
>A lista completa de módulos Adobe Campaign está disponível em [this document](../../production/using/operating-principle.md).

## Camada de persistência {#persistence-layer}

O banco de dados é usado como uma camada de persistência e contém quase todas as informações gerenciadas pelo Adobe Campaign. Isso inclui dados funcionais (perfis, assinaturas, conteúdo etc.), dados técnicos (tarefas e logs do delivery, logs de rastreamento etc.) e dados de trabalho (compras, clientes em potencial).

A confiabilidade do banco de dados é de extrema importância, pois a maioria dos componentes do Adobe Campaign requer acesso ao banco de dados para executar suas tarefas (com a exceção notável do módulo de redirecionamento).

A plataforma vem predefinida com um data mart centralizado no marketing ou pode facilmente se sentar em um data mart e um schema existentes usando qualquer um dos principais RDBMS (Relational Database Management Systems). Todos os dados no data mart são acessados pela plataforma Adobe Campaign por meio de chamadas SQL do Adobe Campaign para o banco de dados. A Adobe Campaign também fornece um complemento completo das ferramentas Extrair transformação e carregamento (ETL) para executar a importação e exportação de dados para dentro e para fora do sistema.
