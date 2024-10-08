---
product: campaign
title: Atualizar qualificação de rejeição após a interrupção da Apple em 2021
description: Saiba como atualizar a qualificação de rejeição após a interrupção da Apple em 2021
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 100%

---

# Atualizar rejeições incorretas após a interrupção da Apple {#update-bounce-qualification.md}

## Contexto

Em 26 de abril de 2021, um problema global na Apple resultou no envio de algumas mensagens de email enviadas para endereços de email válidos da Apple como endereços de email inválidos por servidores da Apple com a seguinte resposta: &quot;550 5.1.1 &#39;endereço de e-mail&#39;: a pesquisa de usuário foi bem-sucedida, mas nenhum registro de usuário foi encontrado.&quot;

Esse problema ocorreu em 26/4 e durou de 7h à 1h EST.

>[!NOTE]
>
>Você pode verificar o Painel de status do sistema da Apple [nesta página](https://www.apple.com/br/support/systemstatus/).

No caso de uma interrupção de um ISP, os emails enviados por meio do Campaign não podem ser entregues com êxito ao destinatário: esses emails serão marcados incorretamente como rejeições.

De acordo com a lógica padrão de manipulação de rejeição, o Adobe Campaign adicionou automaticamente esses destinatários à lista de quarentena com uma configuração **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corrigir isso, você precisa atualizar a tabela de quarentena no Campaign localizando e removendo esses destinatários ou alterando seus **[!UICONTROL Status]** para **[!UICONTROL Valid]** para que o fluxo de trabalho de limpeza noturna os remova.

Para encontrar os destinatários que foram afetados por esse problema, ou caso isso aconteça novamente com qualquer outro ISP, consulte as instruções abaixo.

## Processo para atualização

Você precisará fazer uma consulta na tabela de quarentena para filtrar todos os destinatários da Apple, que incluem @icloud.com, @me.com, @mac.com, que foram possivelmente afetados pela interrupção para que possam ser removidos da lista de quarentena e incluídos em futuras entregas de email do Campaign.

Com base no período do incidente, abaixo estão as diretrizes recomendadas para esse query.

>[!IMPORTANT]
>
>Essas datas/horas são baseadas no fuso horário padrão do leste (EST). Ajuste para o fuso horário da sua instância.

* Para instâncias do Campaign com informações de resposta de rejeição SMTP no campo **[!UICONTROL Error text]** da lista de quarentena:

   * **O texto de erro (texto de quarentena)** contém “A pesquisa de usuário foi bem-sucedida, mas nenhum registro de usuário foi encontrado” E **o texto de erro (texto de quarentena)** contém “support.apple.com”
   * **Atualizar status (@lastModified)** em ou após 26/04/2021 07:00:00 AM
   * **Atualizar status (@lastModified)** em ou antes de 26/04/2021 01:00:00 PM

* Para instâncias do Campaign com informações de regra de email de entrada no campo **[!UICONTROL Error text]** da lista de quarentena:

   * **O texto de erro (texto de quarentena)** contém “Momen_Code10_InvalidRecipient”
   * **Domínio de email (@domain)** igual a icloud.com OU **domínio de email (@domain)** igual a me.com OU **domínio de email (@domain)** igual a mac.com
   * **Atualizar status (@lastModified)** em ou após 26/04/2021 07:00:00 AM
   * **Atualizar status (@lastModified)** em ou antes de 26/04/2021 01:00:00 PM

Depois de ter a lista de destinatários afetados, você pode defini-los como um status **[!UICONTROL Valid]** para que sejam removidos da lista de quarentena pelo fluxo de trabalho **[!UICONTROL Database cleanup]** ou simplesmente excluí-los da tabela.

**Tópicos relacionados:**
* [Entender as falhas de entrega](understanding-delivery-failures.md)
* [Qualificação de email de rejeição](understanding-delivery-failures.md#bounce-mail-qualification)
