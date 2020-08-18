---
title: Carregamento de conteúdo de delivery
seo-title: Carregamento de conteúdo de delivery
description: Carregamento de conteúdo de delivery
seo-description: null
page-status-flag: never-activated
uuid: f2004fb0-9beb-463f-9903-10f291b3663e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 3667da3d-4940-4128-8878-f1ee67216f56
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ee4addc88c6169603122259437d5cb0362851aa6
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 71%

---


# Carregamento de conteúdo de delivery{#loading-delivery-content}

Se o conteúdo de delivery estiver disponível em um arquivo HTML localizado em servidores Amazon S3, FTP ou SFTP, é possível facilmente carregar esse conteúdo nas deliverys do Adobe Campaign.

Para fazer isso:

1. If you haven&#39;t already defined a connection between Adobe Campaign and the (S)FTP server hosting the content files, create a new S3, FTP or SFTP external account in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**. Especifique nesta conta externa o endereço e as credenciais usadas para estabelecer a conexão com o servidor S3 ou (S)FTP.

   Veja um exemplo de uma conta externa S3:

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. Create a new workflow, for example from **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Adicione uma atividade **[!UICONTROL File transfer]** ao seu workflow e configure-a especificando:

   * A conta externa a ser usada para se conectar ao servidor S3 ou (S)FTP.
   * O caminho do arquivo no servidor S3 ou (S)FTP.

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. Add a **[!UICONTROL Delivery]** activity and connect it to the outbound transition of the **[!UICONTROL File transfer]** activity. Configure como apresentado a seguir:

   * Delivery: de acordo com suas necessidades, pode ser um delivery específico que já foi criado no sistema ou um novo delivery com base em um template existente.
   * Recipients: neste exemplo, é considerado que o target é especificado no próprio delivery.
   * Content: Even if the content is imported in the previous activity, select **[!UICONTROL Specified in the delivery]**. Como o conteúdo é importado diretamente de um arquivo localizado em um servidor remoto, ele não tem identificador quando processado pelo workflow e não pode ser identificado como proveniente do evento de entrada.
   * Action to perform: Select **[!UICONTROL Save]** to save the delivery and be able to access it from **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** once the workflow is executed.

   ![](assets/delivery_loadcontent_activityexample.png)

1. Na guia **[!UICONTROL Script]** da atividade **[!UICONTROL Delivery]**, adicione o seguinte comando para carregar o conteúdo do arquivo importado no delivery:

   ```
   delivery.content.md.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. Salve e execute o workflow. A new delivery with the loaded content is created under **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

>[!NOTE]
>
>As práticas recomendadas e a solução de problemas no uso do servidor SFTP são detalhadas [nesta página](../../platform/using/sftp-server-usage.md).
