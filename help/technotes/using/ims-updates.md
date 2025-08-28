---
product: campaign
title: Nota técnica - Atualize seu ambiente para se conectar ao Adobe Campaign com IMS
description: Campaign — atualizações de IMS
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 62fc46e45078fce56eadda3518251e61244bf5d0
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 6%

---

# Como atualizar seu ambiente para se conectar ao Adobe Campaign com IMS {#acc-ims-faq}



Em 30 de junho de 2021, foram feitas alterações nos recursos de logon do [Adobe Identity Management System](https://helpx.adobe.com/br/enterprise/using/identity.html) (IMS) que podem afetar sua capacidade de continuar usando o Adobe Campaign. Saiba como garantir que continue usando o Adobe Campaign Classic v7 sem interrupções.

## O que mudou?

O Adobe Identity Management Service (IMS) parou de oferecer suporte a versões antigas do Internet Explorer em **30 de junho de 2021**. [Saiba mais](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

A Adobe deseja preservar a funcionalidade do IMS para todos os clientes após 30 de junho de 2021. O IMS faz parte da estrutura de segurança que permite aos usuários fazer logon no console do cliente, ou seja, no Adobe Campaign.

Para preservar essa funcionalidade, os clientes devem atualizar o Console do Cliente no computador de cada usuário e garantir que a atualização mais recente da sua [versão do Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), com o **Internet Explorer 11** integrado, esteja instalada no computador de cada usuário.

## Você será afetado?

Se você estiver se conectando ao Campaign [por meio de uma Adobe ID](../../integrations/using/about-adobe-id.md), através do Adobe Identity Management Service (IMS) e executando uma versão mais antiga do Campaign do que as listadas abaixo, você será afetado.

Se você já atualizou, mas está usando uma versão antiga do Microsoft Internet Explorer, é necessário atualizar para o Internet Explorer 11.

## Como atualizar?

* Como cliente hospedado, o Adobe já atualizou sua(s) instância(s) para a versão mais recente.

* Como cliente local/híbrido, você precisa atualizar para uma das versões mais recentes listadas acima para se beneficiar do novo Console do Cliente e garantir uma transição contínua **antes de 30 de junho de 2021**.

  A atualização para uma das novas versões listadas abaixo é obrigatória:

   * Gold Standard 11. [Saiba mais](../../rn/using/gold-standard.md)
   * Campaign versão 21.1.3. [Saiba mais](../../rn/using/latest-release.md)
   * Campaign versão 20.2.5.
   * Campaign versão 20.1.4.
   * Campaign versão 19.2.4.

  Essas versões são fornecidas com um novo protocolo de conexão. A atualização é obrigatória para o servidor do Campaign e o Console do Cliente: depois que todas as instâncias forem atualizadas, o Console do Cliente precisará ser atualizado para essa versão, bem como poder se conectar ao Campaign após **30 de junho de 2021**.

Além disso, verifique se a última atualização da sua [versão do Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), com o **Internet Explorer 11** integrado, está instalada no computador de cada usuário.

## Perguntas frequentes

**Como posso verificar minha versão do Campaign?**

Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


**Como posso verificar se estou usando o IMS?**

Para verificar o modo de conexão, você pode:

* Inicie o Console do cliente do Campaign e acesse as configurações de conexão da instância. Se a opção **Conectar com um Adobe ID** estiver selecionada, você estará usando o Adobe IMS.

  ![](../../integrations/using/assets/ims_1.png)

ou

* Inicie o Console do cliente do Campaign e verifique a janela de conexão. Se estiver se conectando com uma Adobe ID, como mostrado na tela abaixo, você está usando o IMS.

  ![](../../integrations/using/assets/adobeID.png)

**Mensagem de Aviso de Conexão**

A seguinte mensagem de aviso estará visível para os usuários se eles precisarem atualizar o Console do Cliente ou usar uma versão antiga do Microsoft Internet Explorer: **É necessário instalar a última atualização do Windows e/ou seus aplicativos Adobe.**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

Se aparecer esse aviso, instale as atualizações mais recentes do sistema operacional que você está usando. [Saiba mais](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

Se você não atualizou sua versão do Internet Explorer, verá a seguinte mensagem e não poderá mais se conectar ao Adobe Campaign:

![](../../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>Em caso de dúvidas sobre essas alterações, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Links úteis

* [Atualizar o ambiente](../../production/using/build-upgrade.md)
* [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md)
* [Disponibilizar o novo Console do cliente para os usuários](../../installation/using/client-console-availability-for-windows.md)
* [Instalar o console do cliente do Campaign](../../installation/using/installing-the-client-console.md)
* [Acessar a Distribuição de Software da Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=pt-BR)
* [Baixar compilação do Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
