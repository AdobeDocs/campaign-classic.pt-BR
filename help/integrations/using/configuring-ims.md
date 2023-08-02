---
product: campaign
title: Configuração de IMS
description: Saiba como se conectar via Adobe ID
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '357'
ht-degree: 100%

---

# Configuração de IMS{#configuring-ims}



>[!IMPORTANT]
>
>A implementação do Adobe IMS é estritamente reservada aos administradores técnicos da Adobe. Entre em contato com seu executivo da Adobe para iniciar o processo de implementação.

## Pré-requisitos {#prerequisites}

Para usar a integração com o IMS:

* Você deve ter um nome e um ID de organização da Adobe Experience Cloud. Para encontrar seu ID de organização, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=pt-BR){_blank}.
* Você precisa adicionar usuários na Experience Cloud. Para obter mais informações, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=pt-BR){_blank}.

>[!NOTE]
>
>Verifique se os seus usuários estão vinculados aos grupos da Adobe Experience Cloud que serão sincronizados com o Adobe Campaign. [Saiba mais](#configuring-the-external-account).

## Atualização do console {#updating-the-console}

Para usar essa funcionalidade, é fundamental instalar a versão mais recente do console.

## Instalação do pacote {#installing-the-package}

Você deve instalar o pacote **[!UICONTROL Integration with the Adobe Experience Cloud]** integrado. A instalação de um pacote de integração é a mesma de um pacote padrão, que é detalhada [nesta página](../../installation/using/installing-campaign-standard-packages.md).

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

* ID da organização: para encontrar seu ID de organização, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=pt-BR){_blank}.
* Máscara de associação: esse campo permite definir a sintaxe que permitirá que os nomes de configuração no Painel Enterprise sejam sincronizados com os grupos no Adobe Campaign. Se você usar a sintaxe “Campaign - tenant_id - (.&#42;)”, o grupo de segurança criado no Adobe Campaign será vinculado ao nome de configuração “Campaign - tenant_id - internal_name” no Painel Enterprise.

  >[!CAUTION]
  >
  >A máscara de associação é essencial para a conexão através da Adobe ID para funcionar corretamente.

* Informações de conexão da Adobe Experience Cloud, principalmente o nome do locatário da Adobe Experience Cloud.
