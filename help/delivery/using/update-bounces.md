---
product: campaign
title: Atualizar qualificação de rejeição após uma interrupção do ISP
description: Saiba como atualizar a qualificação de rejeição após uma interrupção do ISP
feature: Deliverability
hide: true
hidefromtoc: true
source-git-commit: f320c905f50c69a40678729b009a4c238a462e3c
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 36%

---

# Atualizar devoluções incorretas após uma interrupção do ISP {#update-bounces}

![](../../assets/common.svg)

## Contexto{#update-bounce-context}

No caso de uma interrupção de um ISP, os emails enviados por meio do Campaign não podem ser entregues com êxito ao recipient: esses emails serão marcados incorretamente como rejeições.

Problemas globais no Apple ou no Gmail, por exemplo, podem resultar em mensagens de email enviadas para endereços de email válidos do Apple ou do Gmail terem sido devolvidas incorretamente como endereços de email inválidos pelos servidores ISP com as seguintes respostas:

* &quot;550 5.1.1 &#39;endereço de e-mail&#39;: a pesquisa de usuário foi bem-sucedida, mas nenhum registro de usuário foi encontrado.&quot;

* &quot;550 &#39;endereço de email&#39; recipient rejeitado&quot;

Observe que se o diferimento for rejeitado com a mensagem &quot;452 ação solicitada&quot;: tente novamente mais tarde&quot; estão sendo observados - eles são repetidos automaticamente e nenhuma ação é necessária. Eles devem melhorar à medida que o ISP recupera a capacidade total.

>[!NOTE]
>
>Você pode verificar o Apple System Status Dashboard em [esta página](https://www.apple.com/br/support/systemstatus/){_blank}.
>
>Você pode verificar o Painel de status do Google Workspace em [esta página](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}.

## Impacto{#update-bounce-impact}

No caso de uma interrupção de um ISP, os emails enviados por meio do Campaign não podem ser entregues com êxito ao recipient: esses emails serão marcados incorretamente como rejeições.

De acordo com a lógica padrão de manipulação de rejeição, o Adobe Campaign adicionou automaticamente esses recipients à lista de quarentena com uma configuração **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corrigir isso, você precisa atualizar a tabela de quarentena no Campaign localizando e removendo esses recipients ou alterando seus **[!UICONTROL Status]** para **[!UICONTROL Valid]** para que o fluxo de trabalho de limpeza noturna os remova.

Para encontrar os recipients afetados por esse problema, consulte as instruções abaixo.

## Processo para atualização{#update-bounce-update}

Você precisa executar um query na tabela de quarentena para filtrar todos os recipients afetados - por exemplo, para o Apple, os endereços que incluem, @icloud.com, @me.com, @mac.com - que foram potencialmente afetados pela interrupção para que possam ser removidos da lista de quarentena e incluídos em futuros deliveries de email do Campaign.

Com base no período do incidente e no ISP, abaixo estão as diretrizes recomendadas para esta consulta.

* Para ambientes do Campaign v8 e Campaign Classic v7 com informações de regra de email de entrada no **[!UICONTROL Error text]** campo da lista de quarentena:

   * **O texto de erro (texto de quarentena)** contém &quot;Momen_Code10_InvalidRecipient&quot;
   * **Domínio de email (@domain)** igual a domain1.com OR **Domínio de email (@domain)** igual a domain2.com OR **Domínio de email (@domain)** igual a domain3.com
   * **Atualizar status (@lastModified)** em ou após MM/DD/AAAA HH:MM:SS AM
   * **Atualizar status (@lastModified)** em ou antes de MM/DD/AAAA HH:MM:PM SS

* Para instâncias do Campaign Classic v7 com informações de resposta de rejeição SMTP no **[!UICONTROL Error text]** campo da lista de quarentena:

   * **Texto de erro (texto em quarentena)** contém &quot;550-5.1.1&quot; AND **Texto de erro (texto em quarentena)** contém &quot;support.ISP.com&quot;

      onde &quot;support.ISP.com&quot; pode ser: &quot;support.apple.com&quot; ou &quot;support.google.com&quot;, por exemplo

   * **Atualizar status (@lastModified)** em ou após MM/DD/AAAA HH:MM:SS AM
   * **Atualizar status (@lastModified)** em ou antes de MM/DD/AAAA HH:MM:PM SS


Depois de ter a lista de recipients afetados, você pode defini-los como um status **[!UICONTROL Valid]** para que sejam removidos da lista de quarentena pelo fluxo de trabalho **[!UICONTROL Database cleanup]** ou simplesmente excluí-los da tabela.

**Tópicos relacionados:**
* [Compreender as falhas de entrega](understanding-delivery-failures.md)
* [Qualificação de email de rejeição](understanding-delivery-failures.md#bounce-mail-qualification)
