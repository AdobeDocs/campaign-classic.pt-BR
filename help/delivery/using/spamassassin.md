---
product: campaign
title: SpamAssassin
description: Saiba como configurar a detecção de spam por email com o SpamAssassin
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Email, Deliverability
role: User
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
TQID: https://experienceleague.adobe.com/nZB19N90xSjDCNnibtwcPBm75SSyxkq1hQxICXCOg2A
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 273
ht-degree: 100%

---

# SpamAssassin{#spamassassin}

O Adobe Campaign pode ser configurado para trabalhar com o [SpamAssassin](https://spamassassin.apache.org), um serviço de terceiros usado para filtragem de spam por email. Isso permite que você marque emails para determinar se uma mensagem corre o risco de ser considerada spam pelas ferramentas anti-spam usadas no recebimento.

O SpamAssassin aproveita uma variedade de técnicas de detecção de spam, incluindo:

* Detecção de spam com base em DNS e soma de verificação difusa
* Filtragem Bayesiana
* Programas externos
* Listas de bloqueios
* Bancos de dados online

>[!NOTE]
>
>O SpamAssassin deve ser instalado e configurado no servidor de aplicativos do Adobe Campaign. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-spamassassin.md).
>
>As regras que determinam se um elemento é spam ou não são gerenciadas por meio do SpamAssassin e podem ser editadas por um administrador com privilégios.

## Usar o SpamAssassin no Campaign {#using-spamassassin}

Após criar sua entrega de email e definir seu conteúdo, siga as etapas abaixo para avaliar os riscos.

Para obter mais informações sobre criar e configurar uma entrega, consulte [esta página](about-email-channel.md).

1. Acesse a guia **[!UICONTROL Preview]**.
1. Selecione um destinatário para pré-visualizar sua entrega.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Se você não selecionar um destinatário, a verificação anti-spam não poderá ser executada.

1. Uma mensagem de aviso dará o resultado do teste. Se um alto nível de risco for detectado, a seguinte mensagem de aviso será exibida:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Clique no link **[!UICONTROL More...]** próximo ao aviso.
1. Selecione a guia **[!UICONTROL Anti-spam checking]**.
1. Acesse a seção **[!UICONTROL Points / Rule / Description]** para exibir os motivos para esse risco.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Sempre que você clicar no **[!UICONTROL Anti-spam checking]**, o serviço SpamAssassin será acionado e a mensagem será analisada novamente para detecção anti-spam. Altere o conteúdo antes de executar a análise anti-spam novamente.
