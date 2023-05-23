---
product: campaign
title: Nota técnica - Atualizações de configuração do Adobe Campaign
description: Atualizações de configuração do Adobe Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 19%

---

# Atualizações de configuração do Adobe Campaign 2021 {#acc-config-updates}



A infraestrutura e as configurações devem ser atualizadas regularmente com as compilações e correções de produto mais recentes. Essas correções são necessárias para garantir a continuidade do serviço e a segurança. Além disso, as atualizações serão necessárias para se alinharem a alterações de terceiros.

Como um **Cliente hospedado ou Managed Services**, o Adobe informará sobre atualizações de build em intervalos regulares. Você deverá fazer upgrade de acordo com as recomendações para garantir a conformidade.

Como um **Cliente local ou híbrido**, você deve atualizar sua implementação em intervalos regulares, de acordo com as builds mais recentes.

Por motivos de segurança, você deve atualizar para uma das versões listadas abaixo. Além das etapas de atualização padrão, algumas tarefas manuais devem ser realizadas para garantir que seu ambiente esteja seguro e pronto para futuras alterações do Adobe ou de sistemas de terceiros.

>[!NOTE]
>
>Em caso de dúvidas sobre essas alterações, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Atualizações de segurança {#acc-security-updates}

As versões mais recentes do Campaign vêm com uma correção de segurança que reforça a proteção contra problemas de SSRF (Server Side Request Forgery). Saiba mais [nesta página](https://helpx.adobe.com/br/security/products/campaign/apsb21-04.html).

**Você será afetado?**

Se o seu ambiente estiver em uma build inferior às listadas abaixo, você será afetado:

* Gold Standard 11. [Saiba mais](../../rn/using/gold-standard.md)
* Campaign versão 21.1.1. [Saiba mais](../../rn/using/latest-release.md)
* Campaign versão 20.2.5. [Saiba mais](../../rn/using/release--2020.md#release-20-2-5-build-9188)
* Campaign versão 20.1.4. [Saiba mais](../../rn/using/release--2020.md#release-20-1-4-build-9126)
* Campaign versão 19.2.4. [Saiba mais](../../rn/using/release--2019.md#release-19-2-4-build-9082)
* Campaign versão 19.1.8. [Saiba mais](../../rn/using/release--2019.md#release-19-1-8-build-9039)

Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Como atualizar?**

Você precisa atualizar para uma das builds mais recentes listadas acima.

* Como cliente híbrido, o Adobe informará sobre as datas de atualização programadas para suas instâncias de mid-sourcing. A Adobe recomenda que você também atualize sua instância de marketing.

   A nova build é compatível com a versão Campaign Classic 17.9, mas o Adobe recomenda que todas as instâncias sejam atualizadas para solucionar vulnerabilidades de segurança

* Como cliente local, você deve atualizar as instâncias de marketing e mid-sourcing para a build mais recente.

>[!CAUTION]
>
>Se não for possível atualizar dentro do período recomendado, **você deve entrar em contato com a equipe de Atendimento ao cliente da Adobe para aplicar uma correção manual de segurança de curto prazo em suas instâncias**.

## Atualização do console do cliente do Campaign Classic  {#acc-cc-updates}

A variável **agora disponível** as versões do console abaixo devem ser instaladas para resolver uma regressão identificada recentemente. Essa regressão impediu o uso de alguns componentes do Console do cliente, como o seletor de datas e o gerenciamento de imagens nos deliveries. **Atualização do console** é obrigatório.

* Versão mais recente do Gold Standard 11 9032@10c2709. [Saiba mais](../../rn/using/gold-standard.md)
* Campaign versão 20.1.4. [Saiba mais](../../rn/using/release--2020.md#release-20-1-4-build-9126)
* Campaign versão 19.2.4. [Saiba mais](../../rn/using/release--2019.md#release-19-2-4-build-9082)
* Campaign versão 19.1.8. [Saiba mais](../../rn/using/release--2019.md#release-19-1-8-build-9039)

## Atualização do Adobe Identity Management System (IMS)

O Adobe Identity Service (IMS) deixará de oferecer suporte a versões antigas do Internet Explorer do **30 de junho de 2021**. [Saiba mais](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Uma atualização do console do cliente do Campaign é necessária para garantir a compatibilidade com o Adobe IMS.

**Você será afetado?**

Se estiver se conectando ao Campaign [por meio de uma Adobe ID](../../integrations/using/about-adobe-id.md), pelo Adobe Identity Management Service (IMS), a atualização para uma das novas versões listadas abaixo é obrigatória:

* Gold Standard 11. [Saiba mais](../../rn/using/gold-standard.md)
* Campaign versão 21.1.1. [Saiba mais](../../rn/using/latest-release.md)
* Campaign versão 20.2.5. [Saiba mais](../../rn/using/release--2020.md#release-20-2-5-build-9188)
* Campaign versão 20.1.4. [Saiba mais](../../rn/using/release--2020.md#release-20-1-4-build-9126)
* Campaign versão 19.2.4. [Saiba mais](../../rn/using/release--2019.md#release-19-2-4-build-9082)
* Campaign versão 19.1.8. [Saiba mais](../../rn/using/release--2019.md#release-19-1-8-build-9039)

Essas versões são fornecidas com um novo protocolo de conexão: a atualização é obrigatória para que o servidor do Campaign e o Console do cliente possam se conectar ao Campaign após **30 de junho de 2021**.

Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Como atualizar?**

Como cliente hospedado, o Adobe trabalhará com você para atualizar suas instâncias para a versão mais recente em breve.

Como cliente local/híbrido, você precisa atualizar para uma das versões mais recentes para se beneficiar do novo console do cliente e garantir uma transição contínua **antes de 30 de junho de 2021**.

Depois que todas as instâncias forem atualizadas, o Console do cliente também precisará ser atualizado para essa versão.

* Saiba como acessar o [Adobe Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=pt-BR).

* [Saiba como instalar o console do cliente do Campaign](../../installation/using/installing-the-client-console.md).

## Integração com o Experience Cloud Triggers {#acc-triggers-updates}

O serviço de autenticação oAuth herdado chegou ao fim da vida útil. A autenticação da integração de acionadores, originalmente baseada na configuração da autenticação oAUTH para acessar o pipeline de assimilação, foi movida para o Adobe I/O. Modo de autenticação oAuth herdado com o Campaign [foi retirado](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) em **Setembro de 2021**. Os ambientes hospedados se beneficiarão de uma extensão até **23 de fevereiro de 2022**. Como cliente no local ou híbrido, entre em contato com o Atendimento ao cliente da Adobe para estender o suporte até fevereiro de 2022. Você deve fornecer [o AppID do aplicativo OAuth](../../integrations/using/configuring-pipeline.md#step-optional) para a Adobe.

**Você será afetado?**

Se suas instâncias estiverem sendo executadas em um **versão anterior ao Campaign 19.1.8, 20.2.4, Gold Standard 11**, você estará usando uma versão mais antiga da integração de acionadores por meio da autenticação oAuth: **você precisa atualizar para uma versão mais recente e mudar para o Adobe I/O**.

A atualização para uma das novas versões listadas abaixo é obrigatória:

* Gold Standard 11. [Saiba mais](../../rn/using/gold-standard.md)
* Campaign versão 21.1.1. [Saiba mais](../../rn/using/latest-release.md)
* Campaign versão 20.2.5. [Saiba mais](../../rn/using/release--2020.md#release-20-2-5-build-9188)
* Campaign versão 19.1.8. [Saiba mais](../../rn/using/release--2019.md#release-19-1-8-build-9039)

Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Como atualizar?**

Depois que as instâncias forem atualizadas para uma versão mais recente, todos os clientes precisarão seguir o [mover procedimento para o novo modo de autenticação](../../integrations/using/configuring-adobe-io.md). Isso requer que você gere o novo token de Adobe I/O e use-o na implementação.  

Além disso, para ambientes híbridos, os clientes precisam garantir que o pipeline de assimilação esteja configurado na instância de mid-sourcing. [Saiba mais](../../integrations/using/configuring-pipeline.md).

[Saiba como migrar para o Adobe I/O](../../integrations/using/configuring-adobe-io.md).

## Atualizações de APNs {#acc-apns-updates}

### API do provedor APNs com base em HTTP/2

Desde **31 de março de 2021**, o serviço de notificação por push da Apple (APNs) não oferece mais suporte ao protocolo binário herdado. [Leia mais](https://developer.apple.com/news/?id=c88acm2b).

**Você será afetado?**

Se suas instâncias estiverem sendo executadas em um **versão anterior ao Campaign 21.1,** e você enviar notificações por push com o protocolo binário herdado do Apple, será necessário atualizar para a API do provedor APNs com base em HTTP/2.

Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Como atualizar?**

Como cliente hospedado, se você atualizou para a nova build, o Adobe já atualizou suas instâncias para a API baseada em HTTP/2.

Como cliente local/híbrido, você precisa atualizar sua configuração.

### Atualizações de certificado raiz APNs

Em 29 de março de 2021, uma atualização de infraestrutura do serviço de notificação por push (APNs) da Apple afetou o canal do Adobe Campaign Classic iOS. Uma alteração na configuração do SO é **obrigatório** para evitar a interrupção do canal de push do iOS.

Saiba mais sobre alterações de APNs [nesta página](https://developer.apple.com/news/?id=7gx0a2lp).

**Você será afetado?**

Se você estiver usando o Campaign para enviar notificações por push em dispositivos iOS, você será afetado.

**Como atualizar?**

Como cliente hospedado, nenhuma ação é necessária: o Adobe já incorporou o novo certificado raiz ao seu ambiente.

Como cliente local/híbrido, você precisa atualizar sua configuração para garantir uma transição contínua **antes de 29 de março de 2021**.

[Saiba como incorporar o novo certificado](ios-certificate-update.md).

## Links úteis

* [Atualizar o ambiente](../../production/using/build-upgrade.md)
* [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md)
* [Baixar build de Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html)
* [Disponibilizar o novo Console do cliente para os usuários](../../installation/using/client-console-availability-for-windows.md)
