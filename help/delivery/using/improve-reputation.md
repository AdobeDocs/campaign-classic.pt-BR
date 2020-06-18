---
title: Melhoria da reputação ao usar o Adobe Campaign Classic
description: Saiba mais sobre como melhorar sua reputação ao usar o Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 537cbdec1ec88da1c759f6ca8eafe383c55a61d3
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 90%

---


# Aprimoramento da reputação{#improve-reputation}

Para não esgotar os recipients, exclua endereços de email duplicados do destino. Essa etapa protege a reputação de envio e garante um bom gerenciamento de quarentena. O Adobe Campaign oferta as ferramentas necessárias para implementar essas recomendações e evitar o risco de ser adicionado a uma lista de blocos pelo ISP.

Para evitar ao máximo as duplicações, as seguintes ações devem ser realizadas:

* As importações devem ser configuradas cuidadosamente
* Preste atenção ao modificar endereços de email
* Preste atenção durante as importações automáticas
* Os perfis devem ser classificados em pastas diferentes

O gerenciamento de quarentena é apresentado [nesta seção](../../delivery/using/understanding-quarantine-management.md).

Abaixo você encontrará detalhes sobre o gerenciamento de duplicidade e quarentena.

Você pode monitorar o volume de emails enviados por endereço IP. Uma extensão de esquema é necessária para isso. É necessário estender a tabela de endereços para adicionar o &quot;identificador público&quot; e criar um fluxo de trabalho para extrair e exibir os dados. Entre em contato com a Adobe se precisar.

## Duplicidades {#duplicates}

Ter endereços de email duplicados pode ter várias consequências:

* A mesma mensagem é enviada mais de uma vez. Mesmo se o Campaign executar um procedimento de desduplicação por padrão antes de enviar, não há nada que impeça o envio da mesma mensagem por ações diferentes com o mesmo conteúdo quando um target é dividido.
* Solicitações de cancelamento de assinatura não respeitadas. Se um recipient cancelar a inscrição depois de receber uma mensagem, o perfil duplicado ainda será qualificado para mensagens futuras.

Além dessa revisão lateral dos procedimentos de aceitação, essa situação provavelmente levará os usuários a considerar as mensagens como spam e a acionar um procedimento de lista de bloqueio no ISP.

Você deve agir com cautela especial ao executar operações no banco de dados:

* As importações devem ser meticulosamente configuradas, em especial ao escolher a chave de reconciliação.
* Endereços de email alterados também podem ser uma fonte de duplicidades. Em particular, dois endereços com domínios diferentes podem ser roteados para a mesma caixa de correio, por exemplo, no caso de uma empresa que mudou de nome e manteve o domínio anterior por um determinado período de tempo: joe.doe@amce-co.com e joe.doe@acme-rebranded.com.
* As importações automáticas, sejam elas de listas ou de outros bancos de dados, são elementos a serem considerados durante o gerenciamento de perfis. O que acontece quando você exclui ou move um perfil em outra partição? Ele pode ser recriado na partição inicial por uma importação automática, por exemplo, quando um pedido de compra é feito.
* O armazenamento de perfis em pastas diferentes pode ser implementado usando exibições em vez de partições. Dessa forma, você tem certeza de que os perfis estão na mesma partição física e, ao mesmo tempo, permite que os direitos adequados sejam exibidos e gerenciados.

Há, contudo, casos em que duplicidades entre as diferentes partições são normais. Por exemplo, ao enviar para terceiros ou entidades de empresas diferentes, é lógico que a mesma pessoa seja um recipient por vários motivos. No entanto, raramente é normal encontrar duplicidades na mesma partição.

## Quarentenas {#quarantines}

O Adobe Campaign gerencia uma lista de endereços em quarentena. Os recipients cujos endereços estão em quarentena são excluídos por padrão durante a análise de delivery: não são direcionados. Um endereço de email pode ser colocado em quarentena, por exemplo, quando a caixa de entrada estiver cheia ou se o endereço não existir. Em todos os casos, a quarentena corresponde às regras específicas a seguir descritas.

O gerenciamento de quarentena é apresentado [nesta seção](../../delivery/using/understanding-quarantine-management.md).