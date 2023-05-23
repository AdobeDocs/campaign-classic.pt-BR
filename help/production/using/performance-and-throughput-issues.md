---
product: campaign
title: Problemas de desempenho e de taxa de transferência
description: Problemas de desempenho e de taxa de transferência
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 11%

---

# Problemas de desempenho e de taxa de transferência{#performance-and-throughput-issues}



Primeiro, verifique se a build mais recente está instalada. Isso garante que você tenha os recursos e as correções de erros mais recentes.

Consulte a [Notas de versão](../../rn/using/latest-release.md) para obter mais informações sobre o conteúdo de cada versão.

## Hardware e infraestrutura {#hardware-and-infrastructure}

As diretrizes gerais para requisitos de hardware para Campaign Classic no local estão detalhadas neste [página](https://helpx.adobe.com/br/campaign/kb/hardware-sizing-guide.html).

A equipe de consultoria pode fornecer aos clientes hospedados uma ferramenta que permite visualizar facilmente quanto espaço é usado por vários tipos de tabelas no banco de dados, bem como o espaço usado no site SFTP. Além disso, fornece ferramentas para permitir a limpeza de dados desnecessários. Contato [Atendimento ao cliente Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) se precisar que essa ferramenta seja implementada. Estas são algumas coisas importantes a serem verificadas usando essa ferramenta:

* Se o tamanho do índice for maior que o tamanho da tabela, será necessário um vácuo.
* Verifique as tabelas que têm o máximo de expansão. Se essas tabelas forem usadas com frequência, elas precisam ser aspiradas.
* O bloqueio do banco de dados pode fazer com que os emails parem de ser enviados.

A Adobe Campaign também fornece uma [ferramenta](../../production/using/monitoring-processes.md#manual-monitoring) para verificar o uso da CPU e da RAM. Use essa ferramenta e observe indicadores específicos como: **Memória**, **Trocar memória**, **Disco**, **Processos ativos**. Se os valores forem muito altos, você pode tentar reduzir o número de workflows ou agendar workflows para que sejam iniciados em momentos diferentes.

## Verificação do banco de dados {#database-performances}

Na maioria das vezes, os problemas de desempenho estão vinculados à manutenção do banco de dados. Estes são os principais itens a serem verificados:

* Configuração: recomendamos verificar a configuração inicial da plataforma Adobe Campaign e executar uma verificação completa de hardware.
* Instalação e configuração da plataforma Adobe Campaign: verifique a configuração da rede e as opções de capacidade de entrega da plataforma.
* Manutenção do banco de dados: verifique se a tarefa de limpeza do banco de dados está operacional e se a manutenção do banco de dados foi agendada e executada corretamente. Verifique o número e o tamanho das tabelas de trabalho.
* Diagnóstico em tempo real: verifique o processo e os arquivos de log da plataforma e monitore a atividade do banco de dados ao recriar o problema.

>[!NOTE]
>
>Para obter mais informações, consulte esta seção: [Desempenho do banco de dados](../../production/using/database-performances.md).

## Configuração do aplicativo {#application-configuration}

Esta é uma lista de artigos relacionados às práticas recomendadas de configuração do aplicativo:

* Processos e memória MTA e MTAChild: a **mta** O módulo distribui mensagens para seus **mtachild** módulos filhos. Each **mtachild** prepara as mensagens antes de solicitar uma autorização do servidor de estatísticas e enviá-las. Consulte esta [página](../../installation/using/email-deliverability.md) para obter mais informações.
* Configuração do TLS: não é recomendável ativar o TLS globalmente, pois ele pode reduzir a taxa de transferência. Em vez disso, as configurações TLS por domínio, gerenciadas pela equipe de avaliação do delivery, devem ser ajustadas de acordo com as necessidades. Consulte esta [página](../../installation/using/email-deliverability.md#mx-configuration) para obter mais informações.
* DKIM: para garantir o nível de segurança do DKIM, o 1024b é o tamanho de criptografia recomendado pela prática recomendada. As chaves DKIM inferiores não serão consideradas válidas pela maioria dos provedores de acesso. Consulte [esta página](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=pt-BR#authentication).

## Problemas na capacidade de delivery {#deliverability-issues}

Esta é uma lista de práticas recomendadas e artigos relacionados à capacidade de entrega:

* Reputação de IP: se a reputação de IP não for boa o suficiente, haverá um impacto no desempenho. A variável **Monitoramento da entregabilidade** O módulo oferece várias ferramentas para acompanhar o desempenho da capacidade de delivery da sua plataforma. Consulte esta [página](../../delivery/using/monitoring-deliverability.md).
* Aquecimento de IP: o aquecimento de IP é executado pela equipe de entrega. Isso envolve o aumento gradual do número de emails por meio de novos IPs durante um período de algumas semanas.
* Configuração de afinidade IP: uma configuração de afinidade IP incorreta pode interromper os emails completamente (operador incorreto/nome de afinidade na configuração) ou reduzir a taxa de transferência (pequeno número de IPs na afinidade). Consulte esta [página](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Tamanho do email: o tamanho do email desempenha uma função importante na taxa de transferência. O tamanho máximo recomendado do email é de 60 KB. Consulte esta [página](https://helpx.adobe.com/legal/product-descriptions/campaign.html). No [Taxa de transferência de entrega](../../reporting/using/global-reports.md#delivery-throughput) verifique o número de bytes transferidos por hora.
* Large number of invalid recipients: quando houver um grande número de recipients inválidos, isso poderá afetar a taxa de transferência. O MTA continua tentando enviar emails novamente para destinatários inválidos. Verifique se o banco de dados foi bem mantido.
* Amount of personalization: se um delivery permanecer em &quot;Personalization in progress&quot;, verifique o JavaScript usado nos blocos de personalização.

>[!NOTE]
>
>Consulte também a [Capacidade de entrega](../../delivery/using/about-deliverability.md) seção. Para obter informações mais detalhadas sobre a capacidade de delivery, consulte o [Manual de práticas recomendadas de capacidade de delivery da Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR).
