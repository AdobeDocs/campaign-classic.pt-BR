---
product: campaign
title: Recomendações de dimensionamento de hardware para o Campaign Classic v7
description: Recomendações de dimensionamento de hardware para o Campaign Classic v7
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: c47e73a0-dbd8-43f5-a363-7e6783dc7685
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '2512'
ht-degree: 1%

---

# Recomendações para dimensionamento de hardware{#hardware-sizing-reco}



## Visão geral

>[!CAUTION]
>
>Este artigo é fornecido apenas como um guia de exemplo geral. Você deve se envolver com o Gerente de sucesso do cliente da Adobe Campaign para medir o tamanho exato da implantação antes de iniciar o projeto do Campaign. **Não** adquirir ou implantar qualquer infraestrutura ou hardware até que isso seja feito.

Este documento fornece recomendações gerais para a implantação do Adobe Campaign Classic v7 em seu data center local ou ambiente de nuvem virtualizado. Esse tipo de implantação, chamada de **híbrido** ou **mid-sourcing**, coloca a instância de marketing do Campaign e o banco de dados de marketing sob seu controle operacional, enquanto usa os serviços do Adobe Cloud Messaging para enviar emails, mensagens SMS ou SMPP e coletar dados de rastreamento de aberturas, devoluções e cliques de email.

A instância de marketing é a parte da arquitetura do Adobe Campaign que orienta toda a atividade de marketing e armazena todos os dados de recipients e dados analíticos retornados por campanhas. A instância de marketing é um conjunto de servidores locais que executam os serviços da Adobe Campaign e um banco de dados relacional.

>[!CAUTION]
>
>As informações neste documento não se aplicam se você estiver usando uma instância do Adobe Campaign totalmente hospedada (implantada em Adobe Cloud Services).

A compatibilidade de software é detalhada na seção [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).


### Cenários

Diagramas de implantação e recomendações de dimensionamento de hardware são fornecidos para três cenários representativos:

1. [Tamanho moderado](#scenario-1) - 5 milhões de recipients ativos no sistema
1. [Tamanho grande](#scenario-2) - 20 milhões de destinatários ativos no sistema
1. [Enterprise](#scenario-3) - 50 milhões de recipients ativos, com mensagens transacionais

### Suposições

Este documento também presume os seguintes tipos de uso para todos os três cenários:

* Grandes campanhas de email são enviadas duas vezes por semana, para aproximadamente 50% de seus destinatários ativos
* Correspondências diretas são geradas uma vez por mês para cada recipient no sistema
* Mensalmente, mensagens SMS são enviadas para aproximadamente 10% dos recipients ativos
* O schema de banco de dados que define cada recipient foi estendido com uma tabela adicional, contendo cerca de 200 bytes de dados para cada recipient
* O módulo de interação do Adobe Campaign é usado para adicionar ofertas a emails de saída
* Os dados de rastreamento de email são retidos no sistema Campaign por 90 dias

## Orientações gerais

O Campaign é um aplicativo centrado em banco de dados, e o desempenho do servidor de banco de dados é essencial. A execução de workflows, segmentação, uploads de dados de rastreamento, Interações de entrada, análises e outras atividades geram atividades de banco de dados. Em geral, o tamanho e a frequência dessas operações determinam o tamanho dos servidores de banco de dados.

Os servidores de aplicativos na instância de marketing exigem CPU e memória suficientes para executar workflows e responder a chamadas de API SOAP, incluindo solicitações de usuários do Console do Campaign. Os requisitos de CPU podem ser significativos para workflows que usam interações de saída com regras de oferta complexas, workflows que executam JavaScript personalizado e aplicativos da Web com níveis de tráfego altos.

Os aplicativos Web do Campaign também podem ser implantados nos servidores de aplicativos da instância de marketing ou em sistemas de servidor Web separados. Como as cargas de trabalho dos aplicativos Web entram em conflito com fluxos de trabalho críticos e usuários do Console do Campaign, os aplicativos Web e as interações de entrada podem ser implantados em servidores separados, para garantir que a funcionalidade principal do Campaign seja executada de forma confiável com bom desempenho.

Para segurança e disponibilidade, a Adobe recomenda separar o tráfego da Internet do tráfego gerado pelos usuários empresariais. Por esse motivo, os diagramas contêm dois grupos de servidores: o servidor Web (voltado para a Internet Web1 e Web2) e os servidores de aplicativos (processos comerciais App1 e App2).

É um requisito legal para que os remetentes de email comerciais tenham uma página da Web de recusa funcional. A Adobe recomenda ter máquinas redundantes em cada servidor de grupo para cenários de failover. Isso é especialmente verdadeiro se o Adobe Campaign hospeda as páginas de opção.

### Proxies reversos

A arquitetura do Campaign impõe alta segurança usando SSL sobre HTTP (HTTPS) para comunicação entre sua instância de marketing e o Adobe Cloud Messaging. A segurança, a confiabilidade e a disponibilidade são aplicadas por meio do uso de proxies reversos em uma sub-rede DMZ (zona desmilitarizada) para isolar e proteger os servidores e o banco de dados da instância de marketing.

### Balanceador de carga

O balanceador de carga dos servidores de aplicativos é definido em uma configuração ativa/passiva, com HTTPS terminado no proxy. O balanceador de carga dos servidores da Web é definido em uma configuração ativa/ativa, com HTTPS terminado no proxy.

O Adobe fornece a lista exclusiva de caminhos de URL que podem ser retransmitidos para o servidor do Adobe Campaign no ambiente de implantação.

### Arquitetura

A arquitetura geral é quase idêntica, independentemente dos volumes. Os requisitos de segurança e alta disponibilidade exigem no mínimo quatro servidores; dois servidores se nenhum WebApps for usado. A diferença na configuração varia principalmente na configuração do hardware, como núcleo da CPU e memória.

## Cenário 1: implantação de tamanho moderado{#scenario-1}

![](assets/scenario-1.png)

Volume estimado:

| Canal | Volume |
| ----------------------- | ----------------- |
| Destinatários ativos | 5 milhões |
| Email | 4,2 milhões/mês |
| Correspondência direta | 1 milhão/mês |
| SMS móvel | 100 mil/mês |
| Volume máximo diário de email | 500 |

Para esses volumes, um par de sistemas de servidores de aplicativos da Adobe Campaign fornece toda a funcionalidade para os usuários do cliente Adobe Campaign e para a execução do fluxo de trabalho. Para 5 milhões de destinatários ativos e esse volume de e-mail, as cargas de trabalho do servidor de aplicativos não consomem muita CPU nem E/S; a maior parte da carga está no banco de dados.

Os servidores Web da Adobe Campaign são exibidos na zona segura.

### Servidores de aplicativos e Web

Esse cenário recomenda instalar o Adobe Campaign em quatro máquinas, com as seguintes especificações:

**CPU quad-core de 3 Ghz ou mais, 8 GB de RAM, RAID 1 ou 10, 2 SSD de 80 GB**

Esses sistemas criam o Servidor de aplicativos da instância de marketing, que oferece suporte direto aos usuários do Console do Campaign e executa os workflows da campanha.

Proxies reversos em um tráfego de balanceamento de carga DMZ para os servidores Web da Adobe Campaign. Não há nenhum requisito para instalar a pilha de software Adobe Campaign em máquinas proxy; qualquer software de proxy reverso ou equipamento de rede pode ser usado.

Os recursos de aceitação/recusa de assinatura e da central de preferências podem ser fornecidos pelo Campaign ou pelo seu próprio site. Se optar por implementar essa funcionalidade no seu site, certifique-se de que as informações de preferência e subscrição sejam propagadas para o banco de dados de marketing do Campaign. Normalmente, isso é feito criando arquivos de extração que são carregados automaticamente pelos workflows do Campaign.

O consumo de espaço em disco dos servidores de aplicativos depende do período de retenção de arquivos trocados com provedores de serviços terceirizados (por exemplo, fornecedores de impressão para mala direta) e do tamanho e retenção de arquivos simples importados, como assinaturas ou atualizações de preferências do seu site, ou extrações do seu próprio CRM ou sistemas de marketing.

### Banco de dados

As recomendações de hardware para o servidor de banco de dados são as seguintes:

**CPU de 4 núcleos de 3 Ghz+, 16 GB de RAM, RAID 1 ou 10, SSD de 128 GB no mínimo**

A estimativa de memória assume um cache completo de aproximadamente 500.000 recipients para um grande lançamento de campanha, além de espaço em buffer RDBMS para execução de workflows, importação de dados de rastreamento e outras atividades simultâneas.

Estima-se que o espaço em disco necessário no banco de dados para armazenar todos os dados técnicos do Adobe Campaign (campanhas, rastreamento, tabelas de trabalho etc.) seja de aproximadamente 35 GB com base em um período de retenção de três meses. Se você optar por reter os dados de rastreamento por seis meses, o tamanho do banco de dados aumentará para aproximadamente 40 GB e a retenção de 12 meses aumentará o tamanho do banco de dados para aproximadamente 45 GB. Os dados do recipient consomem cerca de 5 GB para esse ambiente.

>[!CAUTION]
>
>Essa estimativa não inclui dados adicionais do cliente. Se você estiver planejando replicar colunas ou tabelas adicionais de dados do cliente no banco de dados do Adobe Campaign, será necessário estimar o requisito de espaço em disco adicional para ele. Os segmentos/listas carregados também exigem mais armazenamento, dependendo de seu tamanho, frequência e período de retenção.

Considere também que, devido ao volume de informações processadas diariamente, o IOPS do servidor de banco de dados é essencial. Por exemplo, em um dia de pico, você pode implantar campanhas direcionadas a um total de 500.000 destinatários. Para executar cada campanha, o Adobe Campaign insere 500.000 registros em uma tabela que contém aproximadamente 12 milhões de registros (a tabela de log de delivery). Para fornecer desempenho aceitável durante a implantação da campanha, a Adobe recomenda um mínimo de 60.000 IOPS de leitura/gravação aleatória de 4 KB para este cenário.


## Cenário 2: implantação em grande escala{#scenario-2}

![](assets/scenario-2.png)

Volume estimado:

| Canal | Volume |
| ----------------------- | ----------------- |
| Destinatários ativos | 20 milhões |
| Email | 42 milhões/mês |
| Correspondência direta | 10 milhões/mês |
| SMS móvel | 1.000.000/mês |
| Volume máximo diário de email | 5,000,000 |

### Servidores de aplicativos e Web

Nesse cenário, a Adobe recomenda instalar o Adobe Campaign em quatro máquinas, dois servidores de aplicativos e dois servidores Web, com as seguintes especificações:

**CPU quad-core de 3 Ghz ou mais, 8 GB de RAM, RAID 1 ou 10, SSD de 80 GB**

Os servidores de aplicativos oferecem suporte direto aos usuários do Console do Campaign e à execução de workflows da campanha. Essa funcionalidade é implantada em dois servidores idênticos para alta disponibilidade, compartilhando um sistema de arquivos NAS (Network-Attached Storage, armazenamento conectado à rede) para permitir o failover.

Os servidores Web hospedam aplicativos Web do Campaign compatíveis com 10 milhões de destinatários ativos no sistema.

Consulte [Cenário 1: implantação de tamanho moderado](#scenario-1) para obter mais comentários sobre proxies, centros de preferências/tratamento de assinaturas e uso do espaço em disco.

### Banco de dados

As recomendações de hardware para o servidor de banco de dados são as seguintes:

**CPU de 8 núcleos de 3 Ghz, 64 GB de RAM, RAID 1 ou 10, 2 SSD de 320 GB ou RAID 10, SSD de 640 GB no mínimo**

A estimativa de memória assume um cache completo de aproximadamente 5.000.000 recipients para um grande lançamento de campanha, além de espaço em buffer RDBMS para execução de workflows, importação de dados de rastreamento e outras atividades simultâneas.

Estima-se que o espaço em disco necessário no banco de dados para armazenar todos os dados técnicos do Adobe Campaign (campanhas, rastreamento, tabelas de trabalho etc.) seja de aproximadamente 280 GB com base em um período de retenção de 3 meses. Se você optar por reter os dados de rastreamento por seis meses, o tamanho do banco de dados aumentará para aproximadamente 450 GB e a retenção de 12 meses aumentará o tamanho do banco de dados para aproximadamente 900 GB. Os dados do recipient consomem cerca de 15 GB para esse ambiente.

## Cenário 3: implantação corporativa com o centro de mensagens{#scenario-3}

![](assets/scenario-3.png)

Volume estimado:

| Canal | Volume |
| ----------------------- | ----------------- |
| Destinatários ativos | 50 milhões |
| Email | 108 milhões/mês |
| Correspondência direta | 25 milhões/mês |
| SMS móvel | 2,5 milhões/mês |
| Mensagens transacionais | 2,5 milhões/mês |
| Volume máximo diário de email | 2,5 milhões |


A implantação que apoia 50 milhões de destinatários é essencialmente a mesma [Cenário 2](#scenario-2): o tráfego do aplicativo web do Campaign é roteado para os servidores web do Campaign, de modo que a explosão do tráfego web após uma grande inicialização de campanha não afeta os workflows do Campaign e os usuários do Console do cliente.

Essa implantação também inclui chamadas do Centro de mensagens, orientadas por seus próprios sites e aplicativos.


### Servidores de aplicativos e Web

Nesse cenário, a Adobe recomenda instalar o Adobe Campaign em quatro máquinas, da seguinte maneira:

* Servidores de aplicativos
   **Dois sistemas, CPU quad-core de 3 Ghz ou mais, 8 GB de RAM, RAID 1 ou 10, SSD de 80 GB**

* Servidores da Web
   **Dois sistemas, CPU quad-core de 3 GHz ou mais, 16 GB de RAM, RAID 1 ou 10, SSD de 80 GB**


Os servidores de aplicativos oferecem suporte direto aos usuários do Console do Campaign e à execução de workflows da campanha. Essa funcionalidade é implantada em dois servidores idênticos para alta disponibilidade, compartilhando um sistema de arquivos NAS (Network-Attached Storage, armazenamento conectado à rede) para permitir o failover.

Os servidores Web hospedam aplicativos Web do Campaign compatíveis com 10 milhões de destinatários ativos no sistema.

Consulte [Cenário 1: implantação de tamanho moderado](#scenario-1) para obter mais comentários sobre proxies, centros de preferências/tratamento de assinaturas e uso do espaço em disco.

### Banco de dados

As recomendações de hardware para o servidor de banco de dados são as seguintes:

**CPU de 8 núcleos de 3 Ghz+, 96 GB de RAM, RAID 1 ou 10, SSD de 1,5 TB no mínimo**

A estimativa de memória assume um cache completo de aproximadamente 12.500.000 recipients para um grande lançamento de campanha, além de espaço em buffer RDBMS para execução de workflows, importação de dados de rastreamento e outras atividades simultâneas.

Estima-se que o espaço em disco necessário no banco de dados para armazenar todos os dados técnicos do Adobe Campaign (campanhas, rastreamento, tabelas de trabalho etc.) seja de aproximadamente 700 GB com base em um período de retenção de 3 meses. Se você optar por reter os dados de rastreamento por seis meses, o tamanho do banco de dados aumentará para aproximadamente 1,2 TB e a retenção de 12 meses aumentará o tamanho do banco de dados para aproximadamente 2 TB. Os dados do recipient consomem cerca de 50 GB para esse ambiente.

## Diretrizes para Alteração de Pressupostos

As suposições feitas para esses cenários têm um impacto significativo nas recomendações de hardware e na arquitetura de implantação. Esta seção discute diretrizes sobre diferentes suposições. Entre em contato com a equipe de consultoria da Adobe Campaign para obter recomendações específicas que atendam aos seus requisitos.

* **Número de destinatários**
Os destinatários ativos exigem espaço de armazenamento e espaço de buffer de banco de dados, de modo que mais destinatários geralmente exigem mais memória e capacidade de CPU no servidor de banco de dados. Os aumentos de armazenamento são relativamente pequenos para os próprios recipients, mas podem ser significativos para os dados de rastreamento de eventos mantidos para campanhas de email.

* **Tamanho da campanha de email**
A frequência de inicializações de campanha afeta os requisitos de CPU do servidor de banco de dados. Combinadas com mala direta, interações de entrada e outros fluxos de trabalho, as operações de segmentação para campanhas de email colocam uma carga significativa no servidor de banco de dados.

* **Frequência da correspondência direta**
A frequência das correspondências diretas pode afetar os requisitos de CPU do servidor de banco de dados. Combinadas com lançamentos de campanhas e outros workflows, as operações de segmentação para mala direta colocam uma carga significativa no servidor de banco de dados.

* **Volume de Mensagens SMS**
Como o tamanho da campanha de email, o volume de mensagens SMS não coloca grandes cargas nos servidores do Campaign localizados no local; a carga está principalmente nos servidores de mensagens da nuvem do Adobe. A segmentação para campanhas de SMS, como email e correspondência direta, pode colocar uma carga significativa no banco de dados de marketing. Portanto, a frequência de inicializações de campanha de SMS e a complexidade da segmentação são mais relevantes do que o volume de mensagens SMS.

* **Complexidade do esquema do banco de dados**
A quantidade de dados para cada destinatário ativo requer espaço de armazenamento e espaço de buffer de banco de dados, portanto, mais destinatários geralmente exigem mais memória e CPU no servidor de banco de dados. Esquemas complexos também exigem que mais tabelas sejam unidas para segmentação, de modo que as operações de segmentação podem ser executadas muito mais lentamente e exigem mais CPU e memória do banco de dados quando os dados são distribuídos em várias tabelas.

   A memória do servidor de banco de dados é estimada garantindo que o pool de buffer do banco de dados possa ser grande o suficiente para conter todos os dados do destinatário, além de tabelas temporárias para a execução de workflows, além de uma margem para outras operações do banco de dados.

* **Uso de interação de saída**
As regras de interação no modo de lote são avaliadas em workflows que transmitem toda a complexidade do cálculo para o banco de dados. O principal fator do esforço no banco de dados é o número total de ofertas qualificadas computadas durante uma chamada do mecanismo (tamanho alvo X número médio de ofertas por recipient antes de manter as N melhores ofertas). A velocidade da CPU do servidor de banco de dados é o primeiro fator de desempenho.

* **Interações de entrada ou uso da API SOAP**
As regras e ofertas de interação de entrada são avaliadas no banco de dados de marketing, o que requer recursos significativos do servidor de banco de dados, especialmente CPU. O uso intenso de Interações de entrada ou APIs SOAP requer servidores da Web separados para separar a carga de trabalho da execução de workflows do Campaign.

* **Período de retenção de dados de rastreamento**
Aumentar a retenção de dados de rastreamento para além de 90 dias requer mais armazenamento no banco de dados e pode retardar o sistema, pois a inserção de novos dados de rastreamento vai para tabelas grandes. Os dados de rastreamento não são úteis para segmentação de campanha após 90 dias, portanto, é recomendado um período de retenção mais curto.

   Os dados de rastreamento devem ser movidos para o Adobe Analytics ou outro sistema de análise se você precisar de uma análise de longo prazo da experiência de marketing do recipient.

## Virtualização

Todos os servidores do Campaign são bons candidatos para virtualização. Vários problemas devem ser solucionados para garantir a disponibilidade e o desempenho apropriados.

* **Configuração de failover**
Servidores em cluster, por exemplo, servidores de aplicativos redundantes em um proxy com balanceamento de carga, devem ser implantados em hardware separado para garantir que ambas as VMs não fiquem inativas em caso de falha de hardware.

* **Configuração de E/S**
Qualquer configuração RAID recomendada deve ser mantida para a segurança do banco de dados, para garantir que a perda de um dispositivo de armazenamento não cause perda de dados.

* **Desempenho de E/S**
A classificação de IOPS recomendada para o armazenamento de banco de dados deve ser respeitada. Serviços em nuvem como o Amazon EC2 podem não fornecer o desempenho necessário e devem ser cuidadosamente avaliados. Por exemplo, os volumes de SSD provisionados com o Amazon EC2 estão classificados atualmente em 20.000 IOPS cada. Saiba mais em [Documentação do Amazon](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html)), de modo que uma configuração RAID de 4 volumes seria classificada em 80.000 IOPS, o que pode não ser suficiente.

A Adobe recomenda testes de desempenho para qualquer implantação virtualizada do Adobe Campaign antes de colocar o sistema em produção.

## Tópicos relacionados

* [Processos de monitoramento de campanha](../../production/using/monitoring-processes.md)
* [Arquitetura geral do Campaign](../../installation/using/general-architecture.md)
* [Problemas de desempenho e taxa de transferência](../../production/using/performance-and-throughput-issues.md)
* [Lista de verificação de segurança e privacidade](../../installation/using/get-started-security-privacy.md)
