---
title: Arquitetura geral
seo-title: Arquitetura geral
description: Arquitetura geral
seo-description: null
page-status-flag: never-activated
uuid: 686bc660-2403-4bab-a4ea-9b872adf8fa0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 7c28c179-eb18-437e-baf2-25829566c766
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Arquitetura geral{#general-architecture}

A implantação típica da solução Adobe Campaign consiste nos seguintes componentes:

* **Ambiente de cliente personalizado**

   Interface gráfica intuitiva na qual os usuários podem se comunicar e rastrear ofertas de marketing, criar campanhas, revisar e gerenciar todas as atividades de marketing, programas e planos - incluindo emails, fluxos de trabalho e páginas de aterrissagem -, criar e gerenciar perfis de clientes e definir tipos de público-alvo do cliente.

* **Ambiente de desenvolvimento**

   Software do lado do servidor que executa campanhas de marketing por meio de canais de comunicação escolhidos, incluindo emails, SMS, notificações por push, mala direta, Web ou social, com base nas regras e fluxos de trabalho definidos na interface do usuário.

* **Contêineres de banco de dados**

   Com base na tecnologia de banco de dados relacional, o banco de dados do Adobe Campaign armazena todas as informações dos clientes, componentes da campanha, ofertas e fluxos de trabalho, bem como os resultados da campanha nos contêineres do banco de dados do cliente.

O Adobe Campaign é baseado em uma SOA (Service Oriented Architecture, arquitetura orientada a serviços) e abrange vários módulos funcionais. Esses módulos podem ser implantados em um ou mais computadores, em uma ou várias instâncias, dependendo das restrições em termos de escalabilidade, disponibilidade e isolamento do serviço. O escopo das configurações de implantação é, portanto, muito amplo e abrange um único computador central até configurações que incluem vários servidores dedicados em vários sites.

>[!NOTE]
>
>Como fornecedor de software, especificamos infraestruturas de hardware e software compatíveis. As recomendações de hardware fornecidas aqui são apenas para fins informativos e são baseadas em nossa experiência. A Adobe não será responsável por nenhuma decisão tomada com base neles. Ele também dependerá de suas regras e práticas de negócios e da importância e dos níveis de desempenho necessários do projeto.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Caso contrário, a instalação, as atualizações e a manutenção em todos os componentes de uma plataforma do Adobe Campaign serão da responsabilidade do(s) administrador(es) da máquina que os hospeda. Isso inclui a implementação dos pré-requisitos para aplicativos do Adobe Campaign, bem como a conformidade com a Matriz [de](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) compatibilidade entre componentes.

## Camada de apresentação {#presentation-layer}

O aplicativo pode ser acessado de diferentes maneiras, dependendo das necessidades dos usuários: Integração de cliente avançado, cliente thin ou API.

* **Cliente** avançado: A principal interface de usuário do aplicativo é um cliente avançado, ou seja, um aplicativo nativo (Windows) que se comunica com o servidor de aplicativos do Adobe Campaign exclusivamente com protocolos padrão da Internet (SOAP, HTTP etc.). Esse console proporciona excelente facilidade de utilização para produtividade, utiliza pouca largura de banda (através do uso de um cache local) e foi projetado para fácil implantação. Esse console pode ser implantado a partir de um navegador da Internet, pode ser atualizado automaticamente e não requer nenhuma configuração específica da rede, pois gera apenas tráfego HTTP(S).
* **Cliente** fino: Determinadas partes do aplicativo podem ser acessadas por meio de um navegador da Web simples usando uma interface de usuário HTML, incluindo o módulo de relatório, estágios de aprovação de entrega, funcionalidades do módulo de Marketing Distribuído (central/local), monitoramento de instância etc. Esse modo permite incluir funcionalidades do Adobe Campaign em uma intranet ou uma extranet.
* **Integração por meio das APIs**: Em certos casos, o sistema pode ser chamado a partir de aplicativos externos usando as APIs de serviços da Web expostas por meio do protocolo SOAP.

## Camada lógica do aplicativo {#logical-application-layer}

O Adobe Campaign é uma plataforma única com aplicativos diferentes que se combinam para criar uma arquitetura aberta e escalável. A plataforma do Adobe Campaign é escrita em uma camada de aplicativo flexível e é facilmente configurável para atender às necessidades comerciais de uma empresa. Isso acomoda as necessidades crescentes da empresa de uma perspectiva funcional e de uma perspectiva técnica. A arquitetura distribuída garante a escalabilidade linear do sistema, aumentando de milhares de mensagens para milhões de mensagens.

O Adobe Campaign depende de um conjunto de processos do lado do servidor que funcionam juntos.

Os principais processos são:

**Servidor** de aplicativos (nlserver web)

Esse processo expõe toda a gama de funcionalidades do Adobe Campaign por meio de APIs de serviços da Web (SOAP - HTTP + XML). Além disso, ele pode gerar dinamicamente as páginas da Web usadas para acesso com base em HTML (relatórios, formulários da Web etc.). Para isso, esse processo inclui um servidor JSP Apache Tomcat. Esse é o processo ao qual o console se conecta.

**Mecanismo** de fluxo de trabalho (nlserver wfserver)

Ele executa os processos de fluxo de trabalho definidos no aplicativo.

Também lida com fluxos de trabalho técnicos executados periodicamente, incluindo:

* Acompanhamento: Recuperando e consolidando registros de rastreamento. Ele permite que você recupere os logs do servidor de redirecionamento e crie os indicadores agregados usados pelo módulo de relatório.
* Limpeza: Limpeza do banco de dados. Usado para expurgar registros antigos e evitar o crescimento exponencial do banco de dados.
* Faturamento: Envio automático de um relatório de atividade para a plataforma (tamanho do banco de dados, número de ações de marketing etc.).

**Servidor** de entrega (nlserver mta)

O Adobe Campaign tem funcionalidade nativa de transmissão por email. Esse processo funciona como um agente de transferência de mensagens SMTP (MTA). Ele realiza a personalização &quot;um para um&quot; das mensagens e trata de sua entrega física. Funciona usando trabalhos de entrega e lida com tentativas automáticas. Além disso, quando o rastreamento é ativado, ele substitui automaticamente os URLs para que apontem para o servidor de redirecionamento.

Esse processo pode lidar com a personalização e o envio automático para um roteador de terceiros para SMS, fax e mala direta.

**Servidor** de redirecionamento (nlserver webmdl)

Para email, o Adobe Campaign trata automaticamente do rastreamento aberto e de cliques (o rastreamento transacional no nível do site é outra possibilidade). Para isso, os URLs incorporados nas mensagens de email são reescritos para apontar para este módulo, que registra a passagem do usuário da Internet antes de redirecioná-los para o URL necessário.

Para garantir a maior disponibilidade, esse processo é totalmente independente do banco de dados: os outros processos de servidor se comunicam com ele usando chamadas SOAP (HTTP, HTTP(S) e XML) apenas. Tecnicamente, essa funcionalidade é implementada em um módulo de extensão de um servidor HTTP (extensão ISAPI no IIS, ou em um módulo DSO Apache etc.) e está disponível somente no Windows.

Outros processos mais técnicos também estão disponíveis:

**Gerenciar emails** de rejeição (nlserver inMail)

Esse processo permite que você automaticamente pegue emails de caixas de correio configuradas para receber mensagens que são retornadas em caso de falha na entrega. Essas mensagens passam por um processamento baseado em regras para determinar os motivos da não entrega (destinatário desconhecido, cota excedida etc.) e para atualizar o status de entrega no banco de dados.

Todas essas operações são totalmente automáticas e pré-configuradas.

**Status** de entrega de SMS (nlserver sms)

Esse processo chama o roteador SMS para coletar o status de progresso e atualizar o banco de dados.

**Gravando mensagens** de log (nlserver syslogd)

Esse processo técnico captura mensagens de registro e rastreamentos gerados pelos outros processos e as grava no disco rígido. Isso disponibiliza amplas informações para diagnóstico em caso de problemas.

**Gravando registros** de rastreamento (nlserver trackinglogd)

Esse processo salva em disco os registros de rastreamento gerados pelo processo de redirecionamento.

**Gravando eventos** de entrada (nlserver interactiond)

Esse processo garante a gravação no disco de eventos de entrada, dentro da estrutura de Interação.

**Módulos** de supervisão (nlserver watchdog)

Este processo técnico atua como um processo principal que dá origem aos outros. Ele também os monitora e os reinicializa automaticamente em caso de incidentes, mantendo assim o tempo máximo de funcionamento do sistema.

**Servidor** de estatísticas (nlserver stat)

Esse processo mantém estatísticas sobre o número de conexões, as mensagens enviadas para cada servidor de e-mail para o qual as mensagens são enviadas, bem como suas limitações (o maior número de conexões simultâneas, mensagens por hora/ e/ou conexão). Ela também permite federar várias instâncias ou máquinas se elas compartilharem os mesmos endereços IP públicos.

>[!NOTE]
>
>A lista completa dos módulos do Adobe Campaign está disponível [neste documento](../../production/using/operating-principle.md).

## Camada de persistência {#persistence-layer}

O banco de dados é usado como uma camada de persistência e contém quase todas as informações gerenciadas pelo Adobe Campaign. Isso inclui dados funcionais (perfis, assinaturas, conteúdo etc.), dados técnicos (trabalhos e registros de entrega, registros de rastreamento etc.) e dados de trabalho (compras, clientes potenciais).

A confiabilidade do banco de dados é de extrema importância, pois a maioria dos componentes do Adobe Campaign exigem acesso ao banco de dados para executar suas tarefas (com a exceção notável do módulo de redirecionamento).

A plataforma vem predefinida com um mercado de dados centralizado no marketing ou pode facilmente se sentar em um data mart e esquema existentes usando qualquer um dos principais RDBMS (Relational Database Management Systems). Todos os dados no data mart são acessados pela plataforma Adobe Campaign por meio de chamadas SQL do Adobe Campaign para o banco de dados. O Adobe Campaign também fornece um complemento completo das ferramentas Extrair transformação e carga (ETL) para executar a importação e exportação de dados para dentro e para fora do sistema.
