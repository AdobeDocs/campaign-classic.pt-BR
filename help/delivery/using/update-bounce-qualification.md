---
solution: Campaign Classic
product: campaign
title: Atualizar qualificação de rejeição após uma interrupção do ISP
description: Saiba como atualizar a qualificação de rejeição após uma interrupção do ISP.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
translation-type: tm+mt
source-git-commit: 7c161862a4ce2e86e7968fd61af6b8ca28d6623f
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 59%

---

# Atualizar devoluções incorretas após a interrupção da Apple {#update-bounce-qualification.md}

## Contexto

Em 26 de abril de 2021, um problema global na Apple resultou no envio incorreto de algumas mensagens de email enviadas para endereços de email válidos da Apple como endereços de email inválidos por servidores da Apple com a seguinte resposta:  &quot;550 5.1.1 <email address>: a pesquisa de usuário foi bem-sucedida, mas nenhum registro de usuário foi encontrado.&quot;

Esse problema ocorreu em 26/4 e durou de 7:00 às 1:00 EST.

No caso de uma interrupção de um ISP, os emails enviados por meio do Campaign não podem ser entregues com êxito ao recipient: esses emails serão marcados incorretamente como rejeições.

>[!NOTE]
>
>Você pode verificar o Painel de status do sistema da Apple em [this page](https://www.apple.com/support/systemstatus/).

De acordo com a lógica padrão de manipulação de rejeição, o Adobe Campaign adicionou automaticamente esses recipients à lista de quarentena com uma configuração **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corrigir isso, você precisa atualizar a tabela de quarentena no Campaign localizando e removendo esses recipients ou alterando seus **[!UICONTROL Status]** para **[!UICONTROL Valid]** para que o fluxo de trabalho de limpeza noturna os remova.

Para encontrar os recipients que foram afetados por esse problema do , ou caso isso aconteça novamente com qualquer outro ISP, consulte as instruções abaixo.

## Processo para atualização

Você precisará executar um query na tabela de quarentena para filtrar todos os recipients da Apple - que inclui, @icloud.com, @me.com, @mac.com - que foram potencialmente afetados pela interrupção para que possam ser removidos da lista de quarentena e incluídos em futuros deliveries de email do Campaign.

Com base no período do incidente, abaixo estão as diretrizes recomendadas para esse query.

>[!IMPORTANT]
>
>Essas datas/horas são baseadas no fuso horário padrão do leste (EST). Ajuste para o fuso horário da sua instância.

* Para instâncias do Campaign com informações de resposta de rejeição SMTP no campo **[!UICONTROL Error text]** da lista de quarentena:

   * **O texto de erro (texto de quarentena)** contém &quot;pesquisa de usuário bem-sucedida, mas nenhum registro de usuário encontrado&quot; E o texto  **Erro (texto de quarentena)** contém &quot;support.apple.com&quot;
   * **Atualizar status (@lastModified)** em ou após 26/4/2021 07:00:00
   * **Atualizar status (@lastModified)** em ou antes de 26/04/2021 13:00:00 PM

* Para instâncias do Campaign com informações de regra de Email de entrada no campo **[!UICONTROL Error text]** da lista de quarentena:

   * **O texto de erro (texto de quarentena)** contém &quot;Momen_Code10_InvalidRecipient&quot;
   * **Email domain (@domain)** equal to icloud.com&quot; OR Email domain (@domain) equal to me.com&quot; OR Email domain (@domain) equal to mac.com&quot;
   * **Atualizar status (@lastModified)** em ou após 26/4/2021 07:00:00
   * **Atualizar status (@lastModified)** em ou antes de 26/04/2021 13:00:00 PM

Depois de ter a lista de recipients afetados, você pode defini-los como um status **[!UICONTROL Valid]** para que sejam removidos da lista de quarentena pelo fluxo de trabalho **[!UICONTROL Database cleanup]** ou simplesmente excluí-los da tabela.

**Tópicos relacionados:**
* [Compreender as falhas de delivery](../../delivery/using/understanding-delivery-failures.md)
* [Qualificação de email de rejeição](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
