---
title: Configuração de IMS
seo-title: Configuração de IMS
description: Configuração de IMS
seo-description: null
page-status-flag: never-activated
uuid: b659d29f-2a27-4a7b-b5ca-f44c3271dd4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: 279d0548-c876-4d5f-a195-48618bd5e9d1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Configuração de IMS{#configuring-ims}

## Pré-requisitos {#prerequisites}

Para usar a integração com o IMS:

* Você deve ter uma organização da Adobe Marketing Cloud e as IDs IMS (fornecido ao se conectar pela primeira vez à Adobe Marketing Cloud).
* Você precisa adicionar usuários na Marketing Cloud. Para obter mais informações, consulte esta página: [https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html).

>[!NOTE]
>
>Verifique se os seus usuários estão vinculados aos grupos da Adobe Marketing Cloud que serão sincronizados com o Adobe Campaign. Consulte [Configuração da conta](#configuring-the-external-account)externa.

## Atualização do console {#updating-the-console}

Para usar essa funcionalidade, é fundamental instalar a versão mais recente do console.

## Instalação do pacote {#installing-the-package}

Você deve instalar o **[!UICONTROL Integration with the Adobe Experience Cloud]** pacote. A instalação de um pacote de integração é a mesma de um pacote padrão, que é detalhada [nesta página](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configuração da conta externa {#configuring-the-external-account}

Configure the **Adobe Experience Cloud** external account in **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Essa configuração é reservada para o administrador técnico.

![](assets/ims_5.png)

Insira a seguinte informação:

* Informações de conexão do servidor IMS usado (ID e segredo). Essas informações são fornecidas pelo suporte da Adobe. Para obter mais informações, consulte as [Perguntas frequentes dos administradores da Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/mcloud/faq.html).

   The **[!UICONTROL Callback server]** address must be specified in **https**. Esse campo corresponde à URL de acesso da sua instância do Adobe Campaign.

* IMS organization ID: this information is available on the Experience Cloud (in **[!UICONTROL Administration > Experience Cloud Details]** ) and is provided when you first connect to the Adobe Experience Cloud.
* Máscara de associação: esse campo permite definir a sintaxe que permitirá que os nomes de configuração no Painel Enterprise sejam sincronizados com os grupos no Adobe Campaign. Se você usar a sintaxe &quot;Campaign - tenant_id - (.*)&quot;, o grupo de segurança criado no Adobe Campaign será vinculado ao nome de configuração &quot;Campaign - tenant_id - internal_name&quot; no Painel Enterprise.

   >[!CAUTION]
   >
   >A máscara de associação é essencial para a conexão através da Adobe ID para funcionar corretamente.

* Informações de conexão da Adobe Experience Cloud, principalmente 
           o nome do locatário da Adobe Experience Cloud.

