---
product: campaign
title: Gerenciar solicitações de privacidade
description: Saiba mais sobre solicitações de privacidade
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
source-git-commit: a8044037e889f59d4288a0746001e84d319f6bcf
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 100%

---

# Sobre solicitações de privacidade {#privacy-requests}

![](../../assets/v7-only.svg)

Para a apresentação geral sobre o Gerenciamento de privacidade, consulte [esta seção](privacy-management.md).

Essa informação se aplica a GDPR, CCPA, PDPA e LGPD. Para obter mais informações sobre esses requisitos, consulte [esta seção](privacy-management.md#privacy-management-regulations).

>[!NOTE]
>
>A recusa pela venda de informações pessoais, específica para o CCPA, é explicada nesta [seção](#sale-of-personal-information-ccpa).

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

Para facilitar a conformidade com a privacidade, o Adobe Campaign permite manipular solicitações de Acesso e Exclusão. O **direito de acesso** e o **direito ao esquecimento** (solicitação de exclusão) estão descritos [nesta seção](privacy-management.md#right-access-forgotten).

O Adobe Campaign oferece aos controladores de dados duas possibilidades para executar solicitações de acesso e exclusão de privacidade:

* Na **interface do Adobe Campaign**: a cada solicitação de privacidade, o controlador de dados cria uma nova solicitação de privacidade no Adobe Campaign. Consulte [esta seção](privacy-requests-ui.md).
* Pela **API**: o Adobe Campaign fornece uma API que permite o processo automático de solicitações de privacidade usando SOAP. Consulte [esta seção](privacy-requests-api.md).

>[!NOTE]
>
>Para obter mais informações sobre dados pessoais e as diferentes entidades que gerenciam os dados (Controlador de dados, Operador de dados e Titular de dados), consulte [Dados pessoais e Personalidades](privacy-and-recommendations.md#personal-data).

## Pré-requisitos {#prerequesites}

O Adobe Campaign oferece ferramentas de Controladores de dados para criar e processar solicitações de privacidade de dados armazenados no Adobe Campaign. No entanto, é responsabilidade do Controlador de dados gerenciar o relacionamento com o Titular de dados (email, atendimento ao cliente ou um portal da web).

É sua responsabilidade como Controlador de dados confirmar a identidade do Titular de dados que faz a solicitação e pede a confirmação de que os dados retornados ao solicitante pertençam ao Titular de dados.

## Instalação do pacote de privacidade {#install-privacy-package}

Para usar esse recurso, é necessário instalar o **[!UICONTROL Privacy Data Protection Regulation]** pacote através do menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]**. Para obter mais informações sobre instalação de pacotes, consulte a [documentação detalhada](../../installation/using/installing-campaign-standard-packages.md).

Duas novas pastas, específicas para a privacidade, foram criadas em **[!UICONTROL Administration]** > **[!UICONTROL Platform]**:

* **[!UICONTROL Privacy Requests]**: é aqui que você irá criar suas solicitações de privacidade e rastreará sua evolução.
* **[!UICONTROL Namespaces]**: é aqui que você irá definir o campo que será usado para identificar o Titular de dados no banco de dados do Adobe Campaign.

![](assets/privacy-folders.png)

Em **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**, três workflows técnicos são executados diariamente para processar solicitações de privacidade.

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**: esse workflow gera os dados do recipient armazenados no Adobe Campaign e o disponibiliza para download na tela da solicitação de privacidade.
* **[!UICONTROL Delete privacy requests data]**: esse workflow exclui os dados do recipient armazenados no Adobe Campaign.
* **[!UICONTROL Privacy request cleanup]**: esse workflow apaga os arquivos de solicitação de acesso criados há mais de 90 dias.

Em **[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]**, o direito nomeado **[!UICONTROL Privacy Data Right]** foi adicionado. Esse direito nomeado é necessário para que os controladores de dados possam usar as ferramentas de privacidade. Isso permite que eles criem novas solicitações, rastreiem sua evolução, usem a API, etc.

![](assets/privacy-right.png)

## Namespaces {#namesspaces}

Antes de criar solicitações de privacidade, é necessário definir o namespace que será usado. Este é o campo que será usado para identificar o Titular de dados no banco de dados do Adobe Campaign.

Três namespaces estão disponíveis para pronta utilização: email, telefone fixo e celular. Se você precisar de um namespace diferente (um campo personalizado de recipient, por exemplo), poderá criar um novo em **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

>[!NOTE]
>
>Para um desempenho ideal, é recomendável usar namespaces prontos para uso.
