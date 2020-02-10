---
title: Melhorando sua reputação ao usar o Adobe Campaign Classic
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
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Aprimoramento da reputação{#improve-reputation}

Para evitar esgotar seus destinatários, exclua endereços de email duplicados do destino. Esta etapa protege a reputação de envio e garante um bom gerenciamento de quarentena. O Adobe Campaign oferece as ferramentas necessárias para implementar essas recomendações e evitar o risco de serem proibidas pelo ISP.

Para evitar duplicações tanto quanto possível, devem ser realizadas as seguintes ações:

* As importações devem ser configuradas cuidadosamente
* Preste atenção ao modificar endereços de email
* Prestar atenção durante as importações automáticas
* Os perfis devem ser classificados em pastas diferentes

Quarantine management is presented in [this section](../../delivery/using/understanding-quarantine-management.md).

Abaixo você encontrará detalhes sobre o gerenciamento de duplicatas e quarentena.

Você pode monitorar o volume de email enviado por endereço IP. Uma extensão de esquema é necessária para isso. É necessário estender a tabela de endereços para adicionar o &quot;identificador público&quot; e criar um fluxo de trabalho para extrair e exibir os dados. Entre em contato com a Adobe se precisar.

## Duplicatas {#duplicates}

Ter endereços de email duplicados pode ter várias consequências:

* A mesma mensagem é enviada mais de uma vez. Mesmo se o Campaign executar um procedimento de desduplicação por padrão antes de enviar, não há nada que impeça o envio da mesma mensagem por ações diferentes com o mesmo conteúdo quando um destino é dividido.
* Solicitações de cancelamento de assinatura não respeitadas. Se um destinatário cancelar a inscrição depois de receber uma mensagem, seu perfil duplicado ainda será qualificado para mensagens futuras.

Além desta revisão lateral dos procedimentos de aceitação, esta situação levará os usuários a considerar as mensagens como spam e a acionar um procedimento de lista negra no ISP.

Você deve ser especialmente prudente ao executar operações no banco de dados:

* As importações devem ser meticulosamente configuradas, em especial ao escolher a chave de reconciliação.
* Endereços de email alterados também podem ser uma fonte de duplicatas. Em particular, dois endereços com domínios diferentes podem ser roteados para a mesma caixa de correio, por exemplo, no caso de uma empresa que mudou de nome e manteve o domínio anterior por um determinado período de tempo: joe.doe@amce-co.com e joe.doe@acme-rebranded.com.
* As importações automáticas, sejam elas de listas ou de outros bancos de dados, são elementos a serem considerados ao gerenciar perfis. O que acontece quando você exclui ou move um perfil em outra partição? Ele pode ser recriado na partição inicial por uma importação automática, por exemplo, quando um pedido de compra é feito.
* O armazenamento de perfis em pastas diferentes pode ser implementado usando exibições em vez de partições. Dessa forma, você tem certeza de que os perfis estão na mesma partição física e, ao mesmo tempo, permite que os direitos adequados sejam exibidos e gerenciados.

Há, todos os mesmos, casos em que duplicatas entre as diferentes partições são normais. Por exemplo, ao enviar para terceiros ou entidades de empresas diferentes, é lógico que a mesma pessoa seja um destinatário por motivos diferentes. No entanto, raramente é normal encontrar duplicatas na mesma partição.

## Quarenta {#quarantines}

O Adobe Campaign gerencia uma lista de endereços em quarentena. Os destinatários cujos endereços estão em quarentena são excluídos por padrão durante a análise de entrega: não são visados. Um endereço de email pode ser colocado em quarentena, por exemplo, quando a caixa de entrada está cheia ou se o endereço não existe. Em todos os casos, a quarentena corresponde às regras específicas a seguir descritas.

Quarantine management is presented in [this section](../../delivery/using/understanding-quarantine-management.md).