---
product: campaign
title: SpamAssassin
description: Saiba como configurar a detecção de spam por email com o SpamAssassin
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: ht
source-wordcount: '255'
ht-degree: 100%

---

# SpamAssassin{#spamassassin}

## Sobre o SpamAssassin {#about-spamassassin}

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

## Utilização do SpamAssassin {#using-spamassassin}

Após criar seu delivery de email e definir seu conteúdo, siga as etapas abaixo para avaliar os riscos.

Para obter mais informações sobre criar e configurar um delivery, consulte [esta página](about-email-channel.md).

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
>Sempre que você clicar no **[!UICONTROL Anti-spam checking]**, o serviço SpamAssassin será acionado e a mensagem será analisada novamente para detecção anti-spam. Altere o conteúdo antes de executar a análise anti-spam novamente.
