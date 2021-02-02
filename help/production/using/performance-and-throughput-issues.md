---
solution: Campaign Classic
product: campaign
title: Problemas de desempenho e de taxa de transferência
description: Problemas de desempenho e de taxa de transferência
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 8%

---


# Problemas de desempenho e de taxa de transferência{#performance-and-throughput-issues}

Primeiro, você deve verificar se tem a versão mais recente instalada. Isso garante que você tenha os recursos e as correções de erros mais recentes.

Consulte as [Notas de versão](../../rn/using/latest-release.md) para obter mais informações sobre o conteúdo de cada versão.

## Hardware e infraestrutura {#hardware-and-infrastructure}

As diretrizes gerais para os requisitos de hardware para Campaign Classic no local estão detalhadas nesta [página](https://helpx.adobe.com/br/campaign/kb/hardware-sizing-guide.html).

A equipe de consultoria pode fornecer aos clientes hospedados uma ferramenta que permite que você visualização facilmente quanto espaço é usado por vários tipos de tabelas no banco de dados, bem como o espaço usado no site SFTP. Além disso, fornece ferramentas que permitem a limpeza de dados desnecessários. Entre em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) se precisar que essa ferramenta seja implementada. Estas são algumas coisas importantes para verificar usando esta ferramenta:

* Se o tamanho do índice for maior que o tamanho da tabela, será necessário haver vácuo.
* Verifique as tabelas com o máximo de borrão. Se estas tabelas forem frequentemente utilizadas, devem ser aspiradas.
* O bloqueio do banco de dados pode fazer com que emails parem de ser enviados.

A Adobe Campaign também fornece uma [ferramenta](../../production/using/monitoring-processes.md#manual-monitoring) para verificar o uso da CPU e da RAM. Use essa ferramenta e observe indicadores específicos, como: **Memória**, **Trocar Memória**, **Disco**, **Processos Ativos**. Se os valores forem muito altos, você pode tentar reduzir o número de workflows ou agendar workflows para start em momentos diferentes.

## Verificação de banco de dados {#database-performances}

Na maioria das vezes, os problemas de desempenho estão vinculados à manutenção do banco de dados. Estes são os itens principais a serem verificados:

* Configuração: recomendamos verificar a configuração inicial da plataforma Adobe Campaign e executar uma verificação completa de hardware.
* Instalação e configuração da plataforma Adobe Campaign: verifique as opções de configuração de rede e de fornecimento da plataforma.
* Manutenção do banco de dados: verifique se a tarefa de limpeza do banco de dados está operacional e se a manutenção do banco de dados está programada e executada corretamente. Verifique o número e o tamanho das tabelas de trabalho.
* Diagnóstico em tempo real: verifique o processo e os arquivos de log da plataforma, em seguida, monitore a atividade do banco de dados ao recriar o problema.

>[!NOTE]
>
>Para obter mais informações, consulte esta seção: [Desempenho do banco de dados](../../production/using/database-performances.md).

## Configuração do aplicativo {#application-configuration}

Esta é uma lista de artigos relacionados às práticas recomendadas de configuração do aplicativo:

* Processos e memória MTA e MTAChild: o módulo **mta** distribui mensagens para seus módulos filho **mtachild**. Cada **mtachild** prepara mensagens antes de solicitar uma autorização do servidor de estatísticas e enviá-las. Consulte esta [página](../../installation/using/email-deliverability.md) para obter mais informações.
* Configuração TLS: não é recomendável ativar o TLS globalmente, pois ele pode reduzir o throughput. Em vez disso, as configurações TLS por domínio, gerenciadas pela equipe de entrega, devem ser ajustadas, dependendo das necessidades. Consulte esta [página](../../installation/using/email-deliverability.md#mx-configuration) para obter mais informações.
* DKIM: para garantir o nível de segurança do DKIM, o tamanho de criptografia recomendado é 1024b. As chaves DKIM inferiores não serão consideradas válidas pela maioria dos provedores de acesso. Consulte esta [página](../../delivery/using/technical-recommendations.md#dkim) e esta [nota técnica](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html).

## Problemas com delivery {#deliverability-issues}

Esta é uma lista de práticas recomendadas e artigos relacionados à entrega:

* reputação do IP: se a reputação do IP não for boa o suficiente, haverá um impacto no desempenho. O módulo **Deliverability Monitoring** oferta várias ferramentas para rastrear o desempenho da sua plataforma. Consulte esta [página](../../delivery/using/monitoring-deliverability.md).
* Aquecimento de IP: o aquecimento de IP é realizado pela equipe de entrega. Isso envolve aumentar gradualmente o número de emails por meio de novos IPs, durante um período de poucas semanas.
* Configuração de afinidade IP: uma configuração incorreta de afinidade de IP pode parar completamente os emails (nome incorreto do operador/afinidade na configuração) ou reduzir o throughput (pequeno número de IPs na afinidade). Consulte esta [página](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Tamanho do email: o tamanho do email desempenha um papel importante na throughput. O tamanho máximo de email recomendado é de 60 KB. Consulte esta [página](https://helpx.adobe.com/legal/product-descriptions/campaign.html). No relatório [throughput do Delivery](../../reporting/using/global-reports.md#delivery-throughput), verifique o número de bytes transferidos por hora.
* Grande número de recipient inválidos: quando há um grande número de recipient inválidos, isso pode afetar o throughput. O MTA continua tentando enviar emails novamente para recipient inválidos. Certifique-se de que seu banco de dados seja bem mantido.
* Quantidade de personalização: se um delivery permanecer em &quot;Personalização em andamento&quot;, verifique o JavaScript usado em alocos de personalização.

>[!NOTE]
>
>Consulte também a seção [Pontos chave de entregabilidade](../../delivery/using/deliverability-key-points.md).
