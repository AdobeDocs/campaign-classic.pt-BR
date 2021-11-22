---
product: campaign
title: Assimilar segmentos da Adobe Experience Platform no Campaign
description: Saiba como assimilar públicos-alvo do Adobe Experience Platform no Campaign Classic.
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 100%

---

# Assimilar segmentos da Adobe Experience Platform no Campaign {#destinations}

![](../../assets/common.svg)

Para assimilar públicos da Adobe Experience Platform no Campaign e usá-los em seus workflows, primeiro é necessário conectar o Adobe Campaign como um **Destino** da Adobe Experience Platform e configurá-lo com o segmento a ser exportado.

Depois que o Destino for configurado, os dados serão exportados para o local de armazenamento e você precisará criar um fluxo de trabalho dedicado no Campaign Classic para assimilá-los.

## Conectar o Adobe Campaign como um destino

Na Adobe Experience Platform, configure uma conexão com o Adobe Campaign selecionando um local de armazenamento para os segmentos exportados. Essas etapas também permitem selecionar os segmentos a serem exportados e especificar campos XDM adicionais para inclusão.

Para obter mais informações, consulte a [Documentação de destinos](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=pt-BR).

Após o Destino ser configurado, a Adobe Experience Platform cria um arquivo .txt ou .csv delimitado por tabulação no local de armazenamento fornecido. Esta operação é agendada e executada uma vez a cada 24 horas.

Agora você pode configurar um fluxo de trabalho do Campaign Classic para assimilar o segmento no Campaign.

## Criar um fluxo de trabalho de importação no Campaign Classic

Depois que o Campaign Classic for configurado como um Destino, será necessário criar um fluxo de trabalho dedicado para importar o arquivo que foi exportado pela Adobe Experience Platform.

Para fazer isso, é necessário adicionar e configurar uma atividade **[!UICONTROL File transfer]**. Para obter mais informações sobre como configurar essa atividade, consulte [esta seção](../../workflow/using/file-transfer.md).

![](assets/rtcdp-file-transfer.png)

Em seguida, você pode criar o fluxo de trabalho de acordo com suas necessidades (atualizar o banco de dados usando os dados do segmento, enviar deliveries entre canais para o segmento etc.)

Como exemplo, o fluxo de trabalho abaixo faz o download do arquivo do local de armazenamento diariamente e atualiza o banco de dados do Campaign com os dados do segmento.

![](assets/rtcdp-workflow.png)
