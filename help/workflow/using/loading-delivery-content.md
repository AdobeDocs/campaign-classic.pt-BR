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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '320'
ht-degree: 100%

---


# Carregamento de conteúdo de delivery{#loading-delivery-content}

Se o conteúdo de delivery estiver disponível em um arquivo HTML localizado em servidores Amazon S3, FTP ou SFTP, é possível carregar facilmente esse conteúdo nos deliveries do Adobe Campaign.

Para fazer isso:

1. Se ainda não tiver definido uma conexão entre o Adobe Campaign e o servidor (S)FTP que hospeda os arquivos de conteúdo, crie uma nova conta externa S3, FTP ou SFTP em **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**. Especifique nesta conta externa o endereço e as credenciais usadas para estabelecer a conexão com o servidor S3 ou (S)FTP.

   Veja um exemplo de uma conta externa S3:

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. Crie um novo workflow, por exemplo, em **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Adicione uma atividade **[!UICONTROL File transfer]** ao workflow e a configure especificando:

   * A conta externa a ser usada para se conectar ao servidor S3 ou (S)FTP.
   * O caminho do arquivo no servidor S3 ou (S)FTP.

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. Adicione uma atividade **[!UICONTROL Delivery]** e conecte-a à transição de saída da atividade **[!UICONTROL File transfer]**. Configure como apresentado a seguir:

   * Delivery: de acordo com suas necessidades, pode ser um delivery específico que já foi criado no sistema ou um novo delivery com base em um template existente.
   * Recipients: neste exemplo, é considerado que o target é especificado no próprio delivery.
   * Conteúdo: mesmo que o conteúdo seja importado na atividade anterior, selecione **[!UICONTROL Specified in the delivery]**. Como o conteúdo é importado diretamente de um arquivo localizado em um servidor remoto, ele não tem identificador quando processado pelo workflow e não pode ser identificado como proveniente do evento de entrada.
   * Ação a executar: selecione **[!UICONTROL Save]** para salvar o delivery e acessá-lo a partir de **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** após a execução do workflow.

   ![](assets/delivery_loadcontent_activityexample.png)

1. Na guia **[!UICONTROL Script]** da atividade **[!UICONTROL Delivery]**, adicione o seguinte comando para carregar o conteúdo do arquivo importado no delivery:

   ```
   delivery.content.md.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. Salve e execute o workflow. Um novo delivery com o conteúdo carregado é criado em **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

>[!NOTE]
>
>As práticas recomendadas e a solução de problemas no uso do servidor SFTP são detalhadas [nesta página](../../platform/using/sftp-server-usage.md).
