---
product: campaign
title: Configuração de IMS
description: Saiba como se conectar via Adobe ID
feature: Configuration
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 99%

---

# Configuração de IMS{#configuring-ims}

>[!IMPORTANT]
>
>Como usuário de serviços hospedados ou gerenciados do Campaign, sua implementação do Adobe IMS é de propriedade da Adobe. As etapas descritas abaixo se aplicam apenas a clientes locais e híbridos.
> A implementação do Adobe IMS só deve ser executada por administradores técnicos da Adobe. Entre em contato com seu representante da Adobe para iniciar o processo de implementação.

## Pré-requisitos {#prerequisites}

* Você deve ter um nome e um ID de organização da Adobe Experience Cloud. Para encontrar seu ID de organização, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=pt-BR){_blank}.
* Você precisa adicionar usuários na Experience Cloud. Para obter mais informações, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=pt-BR){_blank}.

>[!NOTE]
>
>Verifique se os seus usuários estão vinculados aos grupos da Adobe Experience Cloud que serão sincronizados com o Adobe Campaign. [Saiba mais](#configuring-the-external-account).

## Atualização do console {#updating-the-console}

Para usar esta funcionalidade, é imprescindível instalar a versão mais recente do console do cliente.

## Instalação do pacote {#installing-the-package}

Você deve instalar o pacote **[!UICONTROL Integration with the Adobe Experience Cloud]** integrado. A instalação de um pacote de integração é a mesma de um pacote padrão, que é detalhada [nesta página](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configuração da conta externa {#configuring-the-external-account}

Configure a conta externa da **Adobe Experience Cloud** no **[!UICONTROL Administration > Platform > External accounts]**.

![](assets/ims_5.png)

Insira a seguinte informação:

* Informações de conexão do servidor IMS usado (ID e segredo). Essas informações são fornecidas pela equipe de atendimento ao cliente da Adobe. Para obter mais informações, consulte as [Perguntas frequentes dos administradores da Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=pt-BR).

  O endereço do **[!UICONTROL Callback server]** deve ser especificado em **https**. Esse campo corresponde ao URL de acesso da sua instância do Adobe Campaign.

* ID da organização: para encontrar seu ID de organização, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=pt-BR){_blank}.

* Máscara de associação: esse campo permite definir a sintaxe que permitirá que os nomes de configuração no Painel Enterprise sejam sincronizados com os grupos no Adobe Campaign. Se você usar a sintaxe “Campaign - tenant_id - (.&#42;)”, o grupo de segurança criado no Adobe Campaign será vinculado ao nome de configuração “Campaign - tenant_id - internal_name” no Painel Enterprise.

* Informações de conexão da Adobe Experience Cloud, que é o nome do locatário da Adobe Experience Cloud.
