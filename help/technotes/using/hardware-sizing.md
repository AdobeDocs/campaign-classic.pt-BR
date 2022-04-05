---
product: campaign
title: Recomendações para dimensionamento de hardware para o Campaign Classic v7
description: Recomendações para dimensionamento de hardware para o Campaign Classic v7
exl-id: c47e73a0-dbd8-43f5-a363-7e6783dc7685
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '2512'
ht-degree: 1%

---

# Recomendações para dimensionamento de hardware{#hardware-sizing-reco}

![](../../assets/v7-only.svg)

## Visão geral

>[!CAUTION]
>
>Este artigo é fornecido apenas como um guia de exemplo geral. Você deve se envolver com o Gerente de sucesso do cliente da Adobe Campaign para medir o dimensionamento exato da implantação antes de iniciar o projeto do Campaign. **Não** adquirir ou implantar qualquer infraestrutura ou hardware até que isso seja feito.

Este documento fornece recomendações gerais para a implantação do Adobe Campaign Classic v7 no seu data center local ou no ambiente de nuvem virtualizada. Esse tipo de implantação, chamada de **híbrido** ou **mid-sourcing**, coloca a instância de marketing do Campaign e o banco de dados de marketing sob seu controle operacional, enquanto usa os serviços da Adobe Cloud Messaging para enviar emails, mensagens SMS ou SMPP e coletar dados de rastreamento de cliques, rejeição e abertura de email.

A instância de marketing é a parte da arquitetura do Adobe Campaign que direciona todas as atividades de marketing e armazena todos os dados e dados analíticos do recipient retornados pelas campanhas. A instância de marketing é um conjunto de servidores locais que executam serviços da Adobe Campaign e um banco de dados relacional.

>[!CAUTION]
>
>As informações neste documento não se aplicam se você estiver usando uma instância do Adobe Campaign totalmente hospedada (implantada em Adobe Cloud Services).

A compatibilidade de software é detalhada no [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).


### Cenários

Os diagramas de implantação e as recomendações de dimensionamento de hardware são fornecidos para três cenários representativos:

1. [Tamanho moderado](#scenario-1) - 5 milhões de destinatários ativos no sistema
1. [Tamanho Grande](#scenario-2) - 20 milhões de beneficiários ativos no sistema
1. [Empresa](#scenario-3) - 50 milhões de destinatários ativos, com mensagens transacionais

### Pressupostos

Este documento também assume os seguintes tipos de uso para todos os três cenários:

* Grandes campanhas de email são enviadas duas vezes por semana, para aproximadamente 50% dos recipients ativos
* As malas diretas são geradas uma vez por mês para cada recipient no sistema
* As mensagens SMS são enviadas para aproximadamente 10% dos recipients ativos a cada mês
* O schema de banco de dados que define cada recipient foi estendido com uma tabela adicional, contendo cerca de 200 bytes de dados para cada recipient.
* O módulo Adobe Campaign Interaction é usado para adicionar ofertas a emails de saída
* Os dados de rastreamento de email são retidos no sistema de Campanha por 90 dias

## Orientações gerais

O Campaign é um aplicativo centrado em banco de dados e o desempenho do servidor de banco de dados é essencial. A execução de workflows, segmentação, rastreamento de uploads de dados, interações de entrada, análises e outras atividades geram atividade do banco de dados. Em geral, o tamanho e a frequência dessas operações determinam o tamanho dos servidores de banco de dados.

Os servidores de aplicativos em sua instância de marketing exigem CPU e memória suficientes para executar workflows e responder a chamadas de API SOAP, incluindo solicitações de usuários do Console do Campaign. Os requisitos da CPU podem ser significativos para workflows que usam interações de saída com regras de oferta complexas, workflows que executam Javascript personalizado e aplicativos da Web com altos níveis de tráfego.

Aplicativos da Web do Campaign também podem ser implantados nos servidores de aplicativos da instância de marketing ou em sistemas de servidores da Web separados. Como as cargas de trabalho de aplicativos da Web estão em conflito com fluxos de trabalho críticos e usuários do Campaign Console, as aplicações Web e as interações de entrada podem ser implantadas em servidores separados, para garantir que a funcionalidade principal do Campaign funcione de forma confiável com bom desempenho.

Para segurança e disponibilidade, o Adobe recomenda separar o tráfego da Internet do tráfego gerado pelos usuários empresariais. Por esse motivo, os diagramas contêm dois grupos de servidores: o servidor Web (Web1 e Web2 voltadas para a Internet) e os servidores de aplicativos (processos de negócios App1 e App2).

É um requisito legal que os remetentes de email comercialmente tenham uma página da Web de opção funcional. O Adobe recomenda ter uma máquina redundante em cada servidor de grupo para cenários de failover. Isso é especialmente verdadeiro se o Adobe Campaign hospedar as páginas de opção de não participação.

### Proxies inversos

A arquitetura do Campaign impõe alta segurança usando SSL sobre HTTP (HTTPS) para se comunicar entre sua instância de marketing e o Adobe Cloud Messaging. A segurança, confiabilidade e disponibilidade são aplicadas usando proxies reversos em uma sub-rede &quot;zona desmilitarizada&quot; (DMZ) para isolar e proteger os servidores e o banco de dados das instâncias de marketing.

### Balanceador de carga

O balanceador de carga dos servidores de aplicativos é configurado em uma configuração ativa/passiva, com HTTPS terminado no proxy. O balanceador de carga dos servidores da Web é configurado em uma configuração ativa/ativa, com HTTPS terminado no proxy.

O Adobe fornece a lista exclusiva de caminhos de URL que podem ser retransmitidos para o servidor Adobe Campaign em seu ambiente de implantação.

### Arquitetura

A arquitetura geral é quase idêntica independentemente dos volumes. Os requisitos de segurança e alta disponibilidade impõem um mínimo de quatro servidores; dois servidores se nenhum WebApps for usado. A diferença na configuração varia principalmente na configuração do hardware, como núcleo da CPU e memória.

## Cenário 1: Implantação de tamanho moderado{#scenario-1}

![](assets/scenario-1.png)

Volume estimado:

| Canal  | Volume |
| ----------------------- | ----------------- |
| Destinatários ativos | 5 milhões |
| Email | 4,2 milhões/mês |
| Correspondência direta | 1 milhão/mês |
| SMS Mobile | 100.000/mês |
| Volume de email diário de pico | 500 |

Para esses volumes, um par de sistemas de servidor de aplicativos Adobe Campaign fornece toda a funcionalidade para usuários do Adobe Campaign Client e execução de workflow. Para 5 milhões de recipients ativos e esse volume de email, as cargas de trabalho do servidor de aplicativos não são intensivas de CPU ou E/S; a maior parte do estresse está no banco de dados.

Os servidores da Web da Adobe Campaign são mostrados na zona segura.

### Servidores da Web e de aplicativos

Esse cenário recomenda instalar o Adobe Campaign em quatro computadores, com a seguinte especificação:

**CPU quad-core de 3 Ghz+, 8 GB de RAM, RAID 1 ou 10, 2 SSD de 80 GB**

Esses sistemas criam a instância de marketing do Servidor de aplicativos, que oferece suporte direto aos usuários do Console do Campaign e executa os workflows da campanha.

Proxies reversos em um tráfego de balanceamento de carga em DMZ para os servidores da Web da Adobe Campaign. Não há necessidade de instalar a pilha de software Adobe Campaign em máquinas proxy; pode ser utilizado qualquer software de proxy reverso ou equipamento de rede.

Os recursos de participação/não participação e centro de preferências de assinatura podem ser fornecidos pelo Campaign ou por seu próprio site. Se você optar por implementar essa funcionalidade em seu site, deve garantir que as informações de preferência e subscrição sejam propagadas para o banco de dados de marketing do Campaign. Normalmente, é feito criando arquivos de extração que são carregados automaticamente pelos workflows do Campaign.

O consumo de espaço em disco nos Servidores de Aplicativos depende do período de retenção de arquivos trocados com provedores de serviços de terceiros (por exemplo, fornecedores de impressão por Mala Direta) e do tamanho e retenção de arquivos simples importados, como atualizações de assinatura ou preferências de seu site, ou extrações de seu próprio CRM ou sistemas de marketing.

### Banco de dados

As recomendações de hardware para o servidor de banco de dados são as seguintes:

**CPU de 3 Ghz+ 4 núcleos, RAM de 16 GB, RAID 1 ou 10, SSD mínimo de 128 GB**

A estimativa de memória assume o armazenamento em cache total de aproximadamente 500.000 recipients para uma grande inicialização de campanha, além de espaço em buffer RDBMS para executar workflows, importar dados de rastreamento e outras atividades simultâneas.

Estima-se que o espaço em disco necessário no banco de dados para armazenar todos os dados técnicos do Adobe Campaign (campanhas, rastreamento, tabelas de trabalho e assim por diante) seja de aproximadamente 35 GB com base em um período de retenção de três meses. Se você optar por manter os dados de rastreamento por 6 meses, o tamanho do banco de dados aumenta para aproximadamente 40 GB e a retenção de 12 meses aumenta o tamanho do banco de dados para aproximadamente 45 GB. Os dados do destinatário consomem cerca de 5 GB para esse ambiente.

>[!CAUTION]
>
>Essa estimativa não inclui dados adicionais do cliente. Se você estiver planejando replicar colunas ou tabelas adicionais de dados do cliente no banco de dados do Adobe Campaign, será necessário estimar o requisito adicional de espaço em disco para ele. Segmentos/listas carregadas também exigem mais armazenamento, dependendo de seu tamanho, frequência e período de retenção.

Considere também que, devido ao volume de informações processadas diariamente, o IOPS do servidor de banco de dados é essencial. Por exemplo, em um dia de pico, você pode implantar campanhas direcionadas a um total de 500.000 recipients. Para executar cada campanha, o Adobe Campaign insere 500.000 registros em uma tabela contendo aproximadamente 12 milhões de registros (a tabela de log do delivery). Para fornecer desempenho aceitável durante a implantação da campanha, o Adobe recomenda um mínimo de 60.000 IOPS aleatórios de leitura/gravação de 4 KB para este cenário.


## Cenário 2: Implantação de grande porte{#scenario-2}

![](assets/scenario-2.png)

Volume estimado:

| Canal  | Volume |
| ----------------------- | ----------------- |
| Destinatários ativos | 20 milhões |
| Email | 42 milhões/mês |
| Correspondência direta | 10 milhões/mês |
| SMS Mobile | 1.000.000/mês |
| Volume de email diário de pico | 5.000.000 |

### Servidores da Web e de aplicativos

Nesse cenário, o Adobe recomenda instalar o Adobe Campaign em quatro máquinas, dois servidores de aplicativos e dois servidores da Web, com a seguinte especificação:

**CPU quad-core de 3 Ghz+, 8 GB de RAM, RAID 1 ou 10, SSD de 80 GB**

Os servidores de aplicativos são compatíveis diretamente com os usuários do Console do Campaign e com a execução de workflows da campanha. Essa funcionalidade é implantada em dois servidores idênticos para alta disponibilidade, compartilhando um sistema de arquivos NAS (Network-Attached Storage, armazenamento conectado à rede) para permitir failover.

Os servidores da Web hospedam aplicativos da Web do Campaign compatíveis com 10 milhões de recipients ativos no sistema.

Consulte [Cenário 1: Implantação de tamanho moderado](#scenario-1) para obter mais comentários sobre proxies, centros de preferências/manuseio de assinatura e uso de espaço em disco.

### Banco de dados

As recomendações de hardware para o servidor de banco de dados são as seguintes:

**CPU de 8 núcleos de 3 Ghz+, 64 GB de RAM, RAID 1 ou 10, 2 SSD de 320 GB ou RAID 10, SSD de 640 GB mínimo**

A estimativa de memória assume o armazenamento em cache total de aproximadamente 5.000.000 recipients para uma grande inicialização de campanha, além de espaço em buffer RDBMS para executar workflows, importar dados de rastreamento e outras atividades simultâneas.

Estima-se que o espaço em disco necessário no banco de dados para armazenar todos os dados técnicos do Adobe Campaign (campanhas, rastreamento, tabelas de trabalho e assim por diante) seja de aproximadamente 280 GB com base em um período de retenção de 3 meses. Se você optar por manter os dados de rastreamento por 6 meses, o tamanho do banco de dados aumenta para aproximadamente 450 GB e a retenção de 12 meses aumenta o tamanho do banco de dados para aproximadamente 900 GB. Os dados do destinatário consomem cerca de 15 GB para esse ambiente.

## Cenário 3: Implantação empresarial com o Centro de mensagens{#scenario-3}

![](assets/scenario-3.png)

Volume estimado:

| Canal  | Volume |
| ----------------------- | ----------------- |
| Destinatários ativos | 50 milhões |
| Email | 108 milhões/mês |
| Correspondência direta | 25 milhões/mês |
| SMS Mobile | 2,5 milhões/mês |
| Mensagens transacionais | 2,5 milhões/mês |
| Volume de email diário de pico | 2,5 milhões |


A implantação que oferece suporte a 50 milhões de recipients é essencialmente a mesma mostrada em [Cenário 2](#scenario-2): O tráfego de aplicativos Web do Campaign é roteado para servidores Web do Campaign, de modo que as rastras de tráfego da Web após grandes inicializações de campanha não afetam os workflows do Campaign e os usuários do Console do cliente.

Essa implantação também inclui chamadas do Centro de Mensagens, movidas de seus próprios sites e aplicativos.


### Servidores da Web e de aplicativos

Nesse cenário, o Adobe recomenda instalar o Adobe Campaign em quatro computadores, da seguinte maneira:

* Servidores de aplicativos
   **Dois sistemas, CPU quad-core de 3 Ghz+, RAM de 8 GB, RAID 1 ou 10, SSD de 80 GB**

* Servidores da Web
   **Dois sistemas, CPU quad-core de 3 Ghz+, RAM de 16 GB, RAID 1 ou 10, SSD de 80 GB**


Os servidores de aplicativos são compatíveis diretamente com os usuários do Console do Campaign e com a execução de workflows da campanha. Essa funcionalidade é implantada em dois servidores idênticos para alta disponibilidade, compartilhando um sistema de arquivos NAS (Network-Attached Storage, armazenamento conectado à rede) para permitir failover.

Os servidores da Web hospedam aplicativos da Web do Campaign compatíveis com 10 milhões de recipients ativos no sistema.

Consulte [Cenário 1: Implantação de tamanho moderado](#scenario-1) para obter mais comentários sobre proxies, centros de preferências/manuseio de assinatura e uso de espaço em disco.

### Banco de dados

As recomendações de hardware para o servidor de banco de dados são as seguintes:

**CPU de 8 núcleos de 3 Ghz+, 96 GB de RAM, RAID 1 ou 10, SSD mínimo de 1,5 TB**

A estimativa de memória assume o armazenamento em cache total de aproximadamente 12.500.000 recipients para uma grande inicialização de campanha, além de espaço em buffer RDBMS para executar workflows, importar dados de rastreamento e outras atividades simultâneas.

Estima-se que o espaço em disco necessário no banco de dados para armazenar todos os dados técnicos do Adobe Campaign (campanhas, rastreamento, tabelas de trabalho e assim por diante) seja de aproximadamente 700 GB com base em um período de retenção de 3 meses. Se você optar por manter os dados de rastreamento por 6 meses, o tamanho do banco de dados aumenta para aproximadamente 1,2 TB e a retenção de 12 meses aumenta o tamanho do banco de dados para aproximadamente 2 TB. Os dados do destinatário consomem cerca de 50 GB para esse ambiente.

## Orientações para a alteração de pressupostos

As suposições feitas para esses cenários têm um impacto significativo nas recomendações de hardware e na arquitetura de implantação. Esta seção discute as diretrizes sobre diferentes suposições. Entre em contato com a equipe de consultoria da Adobe Campaign para obter recomendações específicas para atender aos seus requisitos.

* **Número de Recipients**
Os recipients ativos exigem espaço de armazenamento e espaço de buffer de banco de dados, de modo que, em geral, mais recipients exigem mais memória e capacidade da CPU no servidor de banco de dados. Os aumentos de armazenamento são relativamente pequenos para os próprios recipients, mas podem ser significativos para os dados de rastreamento de eventos mantidos para campanhas de email.

* **Tamanho da campanha por email**
A frequência de inicializações de campanha afeta os requisitos de CPU do servidor de banco de dados. Combinadas com mala direta, interações de entrada e outros fluxos de trabalho, as operações de segmentação para campanhas de email colocam uma carga significativa no servidor de banco de dados.

* **Frequência de correspondência direta**
A frequência de malas diretas pode afetar os requisitos da CPU do servidor de banco de dados. Combinadas com inicializações de campanha e outros workflows, as operações de segmentação de mala direta colocavam uma carga significativa no servidor de banco de dados.

* **Volume de mensagens SMS**
Assim como o tamanho da campanha por email, o volume de mensagens SMS não coloca grandes cargas nos servidores do Campaign localizados no local; a carga é principalmente nos servidores do Adobe Cloud Messaging na nuvem. A segmentação para campanhas de SMS, como email e mala direta, pode colocar uma carga significativa no banco de dados de marketing. Portanto, a frequência de lançamentos de campanha de SMS e a complexidade da segmentação são mais relevantes do que o volume de mensagens SMS.

* **Complexidade do esquema do banco de dados**
A quantidade de dados para cada recipient ativo requer espaço de armazenamento e espaço de buffer de banco de dados, de modo que mais recipients geralmente exigem mais memória e CPU no servidor de banco de dados. Esquemas complexos também exigem mais tabelas para serem unidas para segmentação, de modo que as operações de segmentação podem ser executadas muito mais lentamente e exigem mais CPU e memória do banco de dados quando os dados são distribuídos em várias tabelas.

   A memória do servidor de banco de dados é estimada garantindo que o pool de buffer do banco de dados possa ser grande o suficiente para conter todos os dados do recipient, além de tabelas temporárias para executar workflows, além de uma margem para outras operações do banco de dados.

* **Uso de interação de saída**
As regras de Interação no modo de lote são avaliadas em workflows que entregam toda a complexidade de cálculo ao banco de dados. O principal fator de esforço no banco de dados é o número total de ofertas elegíveis computadas durante uma chamada de mecanismo (tamanho do target X número médio de ofertas por recipient antes de manter as N melhores ofertas). A velocidade da CPU do servidor de banco de dados é o primeiro fator de desempenho.

* **Interações de entrada ou uso de API SOAP**
As regras e ofertas de interação de entrada são avaliadas no banco de dados de marketing, exigindo recursos significativos do servidor de banco de dados, especialmente a CPU. O uso intenso de Interações de entrada ou APIs SOAP requer servidores da Web separados para separar a carga de trabalho da execução de workflows do Campaign.

* **Período de retenção de dados de rastreamento**
Aumentar a retenção de dados de rastreamento além de 90 dias requer mais armazenamento de banco de dados e pode retardar o sistema porque a inserção de novos dados de rastreamento vai para tabelas grandes. O rastreamento de dados não é útil para a segmentação da campanha após 90 dias, portanto, o período de retenção mais curto é recomendado.

   Os dados de rastreamento devem ser movidos para o Adobe Analytics ou outro sistema de análise se você precisar de uma análise de longo prazo da experiência de marketing do recipient.

## Virtualização

Todos os servidores do Campaign são bons candidatos à virtualização. Vários problemas devem ser abordados para garantir disponibilidade e desempenho adequados.

* **Configuração de failover**
Os servidores em cluster, por exemplo, servidores de aplicativos redundantes em um proxy com balanceamento de carga, devem ser implantados em hardware separado para garantir que ambas as VMs não desçam caso haja falha de hardware.

* **Configuração de E/S**
Qualquer configuração RAID recomendada deve ser mantida para segurança do banco de dados, para garantir que a perda de um dispositivo de armazenamento não cause perda de dados.

* **Desempenho de E/S**
A classificação de IOPS recomendada para armazenamento de banco de dados deve ser respeitada. Serviços em nuvem como o Amazon EC2 podem não fornecer o desempenho necessário e devem ser cuidadosamente avaliados. Por exemplo, os volumes de SSD provisionados pelo Amazon EC2 são classificados atualmente em 20.000 IOPS cada. Saiba mais em [Documentação do Amazon](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html)), portanto, uma configuração RAID de 4 volumes seria classificada em 80.000 IOPS, o que pode não ser suficiente.

O Adobe recomenda testes de desempenho para qualquer implantação virtualizada do Adobe Campaign antes de colocar o sistema em produção.

## Tópicos relacionados

* [Processos de monitoramento de campanha](../../production/using/monitoring-processes.md)
* [Arquitetura geral do Campaign](../../installation/using/general-architecture.md)
* [Problemas de desempenho e de taxa de transferência](../../production/using/performance-and-throughput-issues.md)
* [Lista de verificação de segurança e privacidade](../../installation/using/get-started-security-privacy.md)
