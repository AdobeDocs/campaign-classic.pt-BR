---
product: campaign
title: Nota técnica - Atualize seu ambiente para se conectar ao Adobe Campaign com o IMS
description: Campaign - Atualizações IMS
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 11%

---

# Como atualizar seu ambiente para se conectar ao Adobe Campaign com o IMS {#acc-ims-faq}



Em 30 de junho de 2021, alterações foram feitas ao [Sistema Adobe Identity Management](https://helpx.adobe.com/br/enterprise/using/identity.html) Recursos de logon do (IMS) que podem afetar sua capacidade de continuar a usar o Adobe Campaign. Saiba como garantir que você continue usando o Adobe Campaign Classic v7 sem interrupções.

## O que mudou?

O Adobe Identity Management Service (IMS) parou de oferecer suporte às versões antigas do Internet Explorer em **30 de junho de 2021**. [Saiba mais](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

A Adobe deseja preservar a funcionalidade IMS para todos os clientes desde 30 de junho de 2021. O IMS faz parte da estrutura de segurança que permite aos usuários fazer logon no Console do cliente, portanto, no Adobe Campaign.

Para preservar essa funcionalidade, os clientes devem atualizar o Console do cliente na máquina de cada usuário e garantir a atualização mais recente de seu [Versão do Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), com **Internet Explorer 11** integrado, é instalado na máquina de cada usuário.

## Você será afetado?

Se você estiver se conectando ao Campaign [por meio de uma Adobe ID](../../integrations/using/about-adobe-id.md), por meio do Adobe Identity Management Service (IMS) e executando uma versão mais antiga do Campaign do que as listadas abaixo, você será afetado.

Se você já atualizou, mas estiver usando uma versão antiga do Microsoft Internet Explorer, será necessário atualizar para o Internet Explorer 11.

## Como atualizar?

* Como cliente hospedado, o Adobe já atualizou suas instâncias para a versão mais recente.

* Como cliente local/híbrido, é necessário atualizar para uma das versões mais recentes listadas acima para se beneficiar do novo Console do cliente e garantir uma transição contínua **antes de 30 de junho de 2021**.

   A atualização para uma das novas versões listadas abaixo é obrigatória:

   * Gold Standard 11. [Saiba mais](../../rn/using/gold-standard.md)
   * Campaign versão 21.1.3. [Saiba mais](../../rn/using/latest-release.md)
   * Campaign versão 20.2.5. [Saiba mais](../../rn/using/release--2020.md#release-20-2-5-build-9188)
   * Campaign versão 20.1.4. [Saiba mais](../../rn/using/release--2020.md#release-20-1-4-build-9126)
   * Campaign versão 19.2.4. [Saiba mais](../../rn/using/release--2019.md#release-19-2-4-build-9082)

   Essas versões são fornecidas com um novo protocolo de conexão. A atualização é obrigatória para o servidor do Campaign e o Console do cliente: depois que todas as instâncias forem atualizadas, o Console do Cliente precisará ser atualizado para essa versão e também para se conectar ao Campaign após **30 de junho de 2021**.

Além disso, verifique a atualização mais recente de seu [Versão do Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), com **Internet Explorer 11** integrado, é instalado na máquina de cada usuário.

## Perguntas frequentes

**Como posso verificar minha versão do Campaign?**

Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


**Como posso verificar se uso o IMS?**

Para verificar o modo de conexão, é possível:

* Inicie o Console do Cliente do Campaign e acesse as configurações de conexão da instância. Se a variável **Conectar-se com uma Adobe ID** estiver selecionada, você está usando o Adobe IMS.

   ![](../../integrations/using/assets/ims_1.png)

ou

* Inicie o Console do Cliente do Campaign e verifique sua janela de conexão. Se estiver se conectando com uma Adobe ID, como mostrado na tela abaixo, você está usando o IMS.

   ![](../../integrations/using/assets/adobeID.png)

**Mensagem de aviso de conexão**

A seguinte mensagem de aviso está visível para os usuários se eles precisarem atualizar seu console do cliente ou usar uma versão antiga do Microsoft Internet Explorer: **Você precisa instalar a atualização mais recente para o Windows e/ou seus aplicativos Adobe.**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

Caso veja esse aviso, certifique-se de instalar as atualizações mais recentes do sistema operacional que você está usando. [Saiba mais](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

Se você não atualizou a versão do Internet Explorer, verá a seguinte mensagem e não poderá mais se conectar ao Adobe Campaign:

![](../../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>Em caso de dúvidas sobre essas alterações, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Links úteis

* [Atualizar seu ambiente](../../production/using/build-upgrade.md)
* [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md)
* [Disponibilizar o novo Console do cliente para os usuários](../../installation/using/client-console-availability-for-windows.md)
* [Instalar o console do cliente do Campaign](../../installation/using/installing-the-client-console.md)
* [Acesse a Distribuição de software Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)
* [Baixar a build do Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html)
