---
solution: Campaign Classic
product: campaign
title: Assimilar segmentos do Adobe Experience Platform no Campaign
description: Saiba como assimilar públicos-alvo do Adobe Experience Platform no Campaign Classic.
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: 9b3254c16eed784846db87d27f9f5de009dafdc3
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# Assimilar segmentos do Adobe Experience Platform no Campaign {#destinations}

Para assimilar o Adobe Experience Platform no Campaign e usá-los em seus workflows, primeiro é necessário conectar o Adobe Campaign como um Adobe Experience Platform **Destination** e configurá-lo com o segmento a ser exportado.

Depois que o Destino for configurado, os dados serão exportados para o local de armazenamento e você precisará criar um fluxo de trabalho dedicado no Campaign Classic para assimilá-lo.

## Conectar o Adobe Campaign como um destino

Na Adobe Experience Platform, configure uma conexão com o Adobe Campaign selecionando um local de armazenamento para os segmentos exportados. Essas etapas também permitem selecionar os segmentos a serem exportados e especificar campos XDM adicionais para inclusão.

Para obter mais informações, consulte a [documentação de Destinos](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

Após o Destino ter sido configurado, o Adobe Experience Platform cria um arquivo .txt ou .csv delimitado por tabulação no local de armazenamento fornecido. Esta operação é agendada e executada uma vez por 24 horas.

Agora você pode configurar um fluxo de trabalho do Campaign Classic para assimilar o segmento no Campaign.

## Criar um workflow de importação no Campaign Classic

Depois que o Campaign Classic tiver sido configurado como um Destino, será necessário criar um fluxo de trabalho dedicado para importar o arquivo que foi exportado pelo Adobe Experience Platform.

Para fazer isso, é necessário adicionar e configurar uma atividade **[!UICONTROL File transfer]** . Para obter mais informações sobre como configurar essa atividade, consulte [esta seção](../../workflow/using/file-transfer.md).

![](assets/rtcdp-file-transfer.png)

Em seguida, você pode criar o workflow de acordo com suas necessidades (atualizar o banco de dados usando os dados do segmento, enviar deliveries entre canais para o segmento, etc.)

Como exemplo, o workflow abaixo baixa o arquivo do local de armazenamento diariamente e atualiza o banco de dados do Campaign com os dados do segmento.

![](assets/rtcdp-workflow.png)
