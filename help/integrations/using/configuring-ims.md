---
product: campaign
title: Configuração de IMS
description: Saiba como se conectar via Adobe ID
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '345'
ht-degree: 100%

---

# Configuração de IMS{#configuring-ims}

![](../../assets/common.svg)

>[!IMPORTANT]
>
>A implementação do Adobe IMS é estritamente reservada aos administradores técnicos da Adobe. Entre em contato com seu executivo da Adobe para iniciar o processo de implementação.

## Pré-requisitos {#prerequisites}

Para usar a integração com o IMS:

* Você deve ter uma organização da Adobe Experience Cloud e as IDs IMS (fornecidas quando você se conecta pela primeira vez à Adobe Experience Cloud).
* Você precisa adicionar usuários na Experience Cloud. Para obter mais informações, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=pt-BR).

>[!NOTE]
>
>Verifique se os seus usuários estão vinculados aos grupos da Adobe Experience Cloud que serão sincronizados com o Adobe Campaign. Consulte [Configuração da conta externa](#configuring-the-external-account).

## Atualização do console {#updating-the-console}

Para usar essa funcionalidade, é fundamental instalar a versão mais recente do console.

## Instalação do pacote {#installing-the-package}

Você deve instalar o pacote **[!UICONTROL Integration with the Adobe Experience Cloud]**. A instalação de um pacote de integração é a mesma de um pacote padrão, que é detalhada [nesta página](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configuração da conta externa {#configuring-the-external-account}

Configure a conta externa da **Adobe Experience Cloud** no **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Essa configuração é reservada para o administrador técnico.

![](assets/ims_5.png)

Insira a seguinte informação:

* Informações de conexão do servidor IMS usado (ID e segredo). Essas informações são fornecidas pelo suporte da Adobe. Para obter mais informações, consulte as [Perguntas frequentes dos administradores da Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=pt-BR).

   O endereço do **[!UICONTROL Callback server]** deve ser especificado em **https**. Esse campo corresponde ao URL de acesso da sua instância do Adobe Campaign.

* ID da organização IMS: essa informação está disponível na Experience Cloud (em **[!UICONTROL Administration > Experience Cloud Details]**) e é fornecida ao se conectar pela primeira vez à Adobe Experience Cloud.
* Máscara de associação: esse campo permite definir a sintaxe que permitirá que os nomes de configuração no Painel Enterprise sejam sincronizados com os grupos no Adobe Campaign. Se você usar a sintaxe &quot;Campaign - tenant_id - (.*)&quot;, o grupo de segurança criado no Adobe Campaign será vinculado ao nome de configuração &quot;Campaign - tenant_id - internal_name&quot; no Painel Enterprise.

   >[!CAUTION]
   >
   >A máscara de associação é essencial para a conexão através da Adobe ID para funcionar corretamente.

* Informações de conexão da Adobe Experience Cloud, principalmente o nome do locatário da Adobe Experience Cloud.
