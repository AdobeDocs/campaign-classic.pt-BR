---
title: Validação
seo-title: Validação
description: Validação
seo-description: null
page-status-flag: never-activated
uuid: e3cd96ef-4f5d-4e17-9fec-5eaa4d835cb1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
discoiquuid: c363a7cf-81a5-4c02-a021-b822eeeadd03
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 70f51ba3937d0f20d9a488c61b52b7ec4396fa5e

---


# Validação{#validating}

Os conceitos globais ao validar uma entrega são apresentados [nesta seção](../../delivery/using/steps-validating-the-delivery.md).

O arquivo de saída de uma entrega de mala direta é gerado durante a análise de entrega. O conteúdo do arquivo depende das colunas de saída selecionadas (consulte o arquivo [de](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)Extração).

>[!NOTE]
>
>A fase de análise é detalhada em [Análise da entrega](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

Durante a fase de análise, o arquivo é gerado, mas as informações relativas aos recipients (ou seja, logs do delivery) não são atualizadas. Assim, você pode cancelar esse trabalho sem correr nenhum risco.

Check the result of the analysis and the content of the output file before clicking **[!UICONTROL Confirm delivery]**. Uma mensagem de confirmação permite iniciar o delivery.

A confirmação do envio inicia a extração dos dados no arquivo especificado.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

You can then close the wizard and look at the delivery logs via the **[!UICONTROL Delivery]** tab, accessible via the delivery details.

You can configure the delivery logs retrieval mode from the **[!UICONTROL Analysis]** tab of the delivery properties.

Há dois modos:

* **[!UICONTROL Messages are considered sent after validation]** (modo padrão): neste modo de função, todos os logs de transmissão são atualizados quando o operador confirma o envio (seu status passa de &quot;Entrega pendente&quot; para &quot;Enviada&quot;) e a entrega é automaticamente definida como **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : esse modo permite atualizar os logs de rede via um arquivo externo enviado pelo provedor de serviços. Nesse caso, um workflow para processar essas informações precisa ser usado para atualizar o status broadlog.

   >[!NOTE]
   >
   >In this case, the delivery&#39;s status also needs to be changed to **[!UICONTROL Finished]** by the user as soon as the broadlogs are updated.
