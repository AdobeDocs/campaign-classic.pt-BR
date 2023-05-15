---
product: campaign
title: Atualizar qualificação de rejeição após uma interrupção do ISP
description: Saiba como atualizar a qualificação de rejeição após uma interrupção do ISP
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 100%

---

# Atualizar as rejeições permanentes incorretas após uma interrupção do ISP {#update-bounces}



## Contexto{#update-bounce-context}

No caso de uma interrupção de um ISP, os emails enviados por meio do Campaign não podem ser entregues com êxito ao recipient: esses emails serão marcados incorretamente como rejeições.

Problemas globais na Apple ou no Gmail, por exemplo, podem fazer com que algumas mensagens de email enviadas para endereços de email válidos da Apple ou do Gmail sejam incorretamente devolvidas como endereços de email inválidos pelos servidores ISP com as seguintes respostas de devolução:

* “550 5.1.1 &#39;endereço de email&#39;: a pesquisa de usuário foi bem-sucedida, mas nenhum registro de usuário foi encontrado.”

* “Recipient do &#39;endereço de email&#39; 550 rejeitado”

Observe que se o deferimento for rejeitado com a mensagem “452 ação solicitada cancelada: tente novamente mais tarde”, eles serão automaticamente repetidos e nenhuma ação será necessária. Eles devem melhorar à medida que o ISP recupera a capacidade total.

>[!NOTE]
>
>Você pode verificar o Painel de status do sistema da Apple [nesta página](https://www.apple.com/br/support/systemstatus/){_blank}.
>
>Você pode verificar o Painel de status do Google Workspace [nesta página](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}.

## Impacto{#update-bounce-impact}

No caso de uma interrupção de um ISP, os emails enviados por meio do Campaign não podem ser entregues com êxito ao recipient: esses emails serão marcados incorretamente como rejeições.

De acordo com a lógica padrão de manipulação de rejeição, o Adobe Campaign adicionou automaticamente esses recipients à lista de quarentena com uma configuração **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corrigir isso, você precisa atualizar a tabela de quarentena no Campaign localizando e removendo esses recipients ou alterando seus **[!UICONTROL Status]** para **[!UICONTROL Valid]** para que o fluxo de trabalho de limpeza noturna os remova.

Para encontrar os recipients afetados por esse problema, consulte as instruções abaixo.

## Processo para atualização{#update-bounce-update}

Você precisa executar uma consulta na tabela de quarentena para filtrar todos os recipients afetados - por exemplo, para Apple, os endereços que incluem @icloud.com, @me.com, @mac.com - que foram potencialmente afetados pela interrupção, para que possam ser removidos da lista de quarentena e incluídos em futuras entregas de email do Campaign.

Com base no período do incidente e no ISP, abaixo estão as diretrizes recomendadas para esta consulta.

* Para ambientes do Campaign com informações de regra de Email de entrada no campo **[!UICONTROL Error text]** da lista de quarentena:

   * **O texto de erro (texto de quarentena)** contém &quot;Momen_Code10_InvalidRecipient&quot;
   * **Domínio de email (@domain)** igual a domain1.com OU **Domínio de email (@domain)** igual a domain2.com OU **Domínio de email (@domain)** igual a domain3.com
   * **Atualizar status (@lastModified)** em ou após MM/DD/AAAA HH:MM:SS AM
   * **Atualizar status (@lastModified)** em ou antes de MM/DD/AAAA HH:MM:SS PM

* Para ambientes do Campaign com informações de resposta de rejeição SMTP no campo **[!UICONTROL Error text]** da lista de quarentena:

   * **Texto de erro (texto de quarentena)** contém “550-5.1.1” E **Texto de erro (texto de quarentena)** contém “support.ISP.com”

      em que “support.ISP.com” pode ser: “support.apple.com” ou “support.google.com” por exemplo

   * **Atualizar status (@lastModified)** em ou após MM/DD/AAAA HH:MM:SS AM
   * **Atualizar status (@lastModified)** em ou antes de MM/DD/AAAA HH:MM:SS PM


Depois de ter a lista de recipients afetados, você pode defini-los como um status **[!UICONTROL Valid]** para que sejam removidos da lista de quarentena pelo fluxo de trabalho **[!UICONTROL Database cleanup]** ou simplesmente excluí-los da tabela.

**Tópicos relacionados:**
* [Compreender as falhas de entrega](understanding-delivery-failures.md)
* [Qualificação de email de rejeição](understanding-delivery-failures.md#bounce-mail-qualification)
