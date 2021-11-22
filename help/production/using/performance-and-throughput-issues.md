---
product: campaign
title: Problemas de desempenho e de taxa de transferência
description: Problemas de desempenho e de taxa de transferência
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 11%

---

# Problemas de desempenho e de taxa de transferência{#performance-and-throughput-issues}

![](../../assets/v7-only.svg)

Primeiro, você deve verificar se tem a build mais recente instalada. Isso garante que você tenha os recursos e as correções de erros mais recentes.

Consulte a [Notas de versão](../../rn/using/latest-release.md) para obter mais informações sobre o conteúdo de cada versão.

## Hardware e infraestrutura {#hardware-and-infrastructure}

As diretrizes gerais para os requisitos de hardware para o Campaign Classic no local estão detalhadas neste [página](https://helpx.adobe.com/br/campaign/kb/hardware-sizing-guide.html).

A equipe de consultoria pode fornecer aos clientes hospedados uma ferramenta que permite visualizar facilmente qual espaço é usado por vários tipos de tabelas no banco de dados, bem como o espaço usado no site SFTP. Além disso, fornece ferramentas que permitem limpar dados desnecessários. Contato [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) se você precisar que essa ferramenta seja implementada. Veja algumas coisas importantes a serem verificadas usando esta ferramenta:

* Se o tamanho do índice for maior que o tamanho da tabela, será necessário haver vácuo.
* Verifique as tabelas com o máximo de borrão. Se estas tabelas forem frequentemente utilizadas, devem ser aspiradas.
* O bloqueio do banco de dados pode fazer com que os emails parem de ser enviados.

A Adobe Campaign também fornece uma [ferramenta](../../production/using/monitoring-processes.md#manual-monitoring) para verificar o uso da CPU e da RAM. Use essa ferramenta e observe indicadores específicos como: **Memória**, **Trocar memória**, **Disco**, **Processos ativos**. Se os valores forem muito altos, tente reduzir o número de workflows ou agendar workflows para iniciar em momentos diferentes.

## Verificação do banco de dados {#database-performances}

Na maioria das vezes, os problemas de desempenho estão vinculados à manutenção do banco de dados. Estes são os itens principais a serem verificados:

* Configuração: recomendamos verificar a configuração inicial da plataforma Adobe Campaign e executar uma verificação completa de hardware.
* Instalação e configuração da plataforma Adobe Campaign: verifique as opções de configuração de rede e capacidade de entrega da plataforma.
* Manutenção do banco de dados: verifique se a tarefa de limpeza do banco de dados está operacional e se a manutenção do banco de dados está agendada e executada corretamente. Verifique o número e o tamanho das tabelas de trabalho.
* Diagnóstico em tempo real: verifique os arquivos de log do processo e da plataforma e monitore a atividade do banco de dados ao recriar o problema.

>[!NOTE]
>
>Para obter mais informações, consulte esta seção: [Desempenho do banco de dados](../../production/using/database-performances.md).

## Configuração do aplicativo {#application-configuration}

Esta é uma lista de artigos relacionados às práticas recomendadas de configuração de aplicativos:

* MTA e MTAChild processos e memória: o **mta** O módulo distribui mensagens para seu **mtachild** módulos filho. Cada **mtachild** prepara mensagens antes de solicitar uma autorização do servidor de estatísticas e as envia. Consulte esta [página](../../installation/using/email-deliverability.md) para obter mais informações.
* Configuração TLS: não é recomendado ativar o TLS globalmente porque ele pode reduzir a taxa de transferência. Em vez disso, as configurações de TLS por domínio, gerenciadas pela equipe de deliverability, devem ser ajustadas dependendo das necessidades. Consulte esta [página](../../installation/using/email-deliverability.md#mx-configuration) para obter mais informações.
* DKIM: para garantir o nível de segurança do DKIM, o 1024b é o tamanho de criptografia recomendado pela prática recomendada. As chaves DKIM inferiores não serão consideradas válidas pela maioria dos provedores de acesso. Consulte [esta página](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=pt-BR#authentication).

## Problemas na capacidade de delivery {#deliverability-issues}

Esta é uma lista de práticas recomendadas e artigos relacionados à capacidade de entrega:

* Idoneidade do IP: se a reputação do IP não for boa o suficiente, haverá um impacto no desempenho. O **Monitoramento da capacidade de entrega** O módulo do oferece várias ferramentas para rastrear o desempenho da capacidade de entrega da sua plataforma. Consulte esta [página](../../delivery/using/monitoring-deliverability.md).
* Aquecimento de IP: o aquecimento de IP é executado pela equipe de deliverability. Isso envolve aumentar gradualmente o número de emails por meio de novos IPs, durante um período de algumas semanas.
* Configuração da afinidade IP: uma configuração incorreta de afinidade IP pode parar completamente os emails (nome incorreto do operador/afinidade na configuração) ou reduzir a taxa de transferência (pequeno número de IPs na afinidade). Consulte esta [página](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Tamanho do email: o tamanho do email tem uma função importante na taxa de transferência. O tamanho máximo recomendado de email é de 60 KB. Consulte esta [página](https://helpx.adobe.com/legal/product-descriptions/campaign.html). No [Taxa de transferência da entrega](../../reporting/using/global-reports.md#delivery-throughput) verifique o número de bytes transferidos por hora.
* Grande número de destinatários inválidos: quando há um grande número de recipients inválidos, ele pode afetar o throughput. O MTA continua tentando reenviar emails para destinatários inválidos. Certifique-se de que o banco de dados seja bem mantido.
* Quantidade de personalização: se um delivery permanecer em &quot;Personalization in progress&quot;, verifique o JavaScript usado em blocos de personalização.

>[!NOTE]
>
>Consulte também a [Capacidade de entrega](../../delivery/using/about-deliverability.md) seção. Para obter informações mais detalhadas sobre a capacidade de delivery, consulte o [Manual de práticas recomendadas de capacidade de delivery da Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR).
