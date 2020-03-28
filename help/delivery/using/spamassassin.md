---
title: SpamAssassin
seo-title: SpamAssassin
description: SpamAssassin
seo-description: null
page-status-flag: never-activated
uuid: 4f439432-4215-42ed-8f92-b4ca8dd92726
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: d41658ab-ee79-4a5c-a165-d94b81eb2b33
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# SpamAssassin{#spamassassin}

## Sobre o SpamAssassin {#about-spamassassin}

O Adobe Campaign pode ser configurado para trabalhar com o [SpamAssassin](https://spamassassin.apache.org), um serviço de terceiros usado para filtragem de spam por email. Isso permite que você marque emails para determinar se uma mensagem corre o risco de ser considerada spam pelas ferramentas anti-spam usadas no recebimento.

O SpamAssassin aproveita uma variedade de técnicas de detecção de spam, incluindo:

* Detecção de spam com base em DNS e soma de verificação difusa
* Filtragem Bayesiana
* Programas externos
* Blacklists
* Bancos de dados online

>[!NOTE]
>
>O SpamAssassin deve ser instalado e configurado no servidor de aplicativos do Adobe Campaign. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-spamassassin.md).
>
>As regras que determinam se um elemento é spam ou não são gerenciadas por meio do SpamAssassin e podem ser editadas por um administrador com privilégios.

## Utilização do SpamAssassin {#using-spamassassin}

Após criar seu delivery de email e definir seu conteúdo, siga as etapas abaixo para avaliar os riscos.

Para obter mais informações sobre criar e configurar um delivery, consulte [esta página](../../delivery/using/about-email-channel.md).

1. Acesse a guia **[!UICONTROL Preview]**.
1. Selecione um recipient para pré-visualizar seu delivery.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Se você não selecionar um recipient, a verificação anti-spam não poderá ser executada.

1. Uma mensagem de aviso dará o resultado do teste. Se um alto nível de risco for detectado, a seguinte mensagem de aviso será exibida:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Clique no link **[!UICONTROL More...]** próximo ao aviso.
1. Selecione a guia **[!UICONTROL Anti-spam checking]**.
1. Acesse a seção **[!UICONTROL Points / Rule / Description]** para exibir os motivos para esse risco.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Sempre que a **[!UICONTROL Verificação anti-spam]** é selecionada, o serviço SpamAssassin é acionado e a mensagem é analisada novamente para detecção anti-spam. Altere o conteúdo antes de executar a análise anti-spam novamente.
