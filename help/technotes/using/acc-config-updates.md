---
product: campaign
title: Technote - Atualizações de configuração do Adobe Campaign
description: Atualizações de configuração do Adobe Campaign
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '1125'
ht-degree: 18%

---

# Atualizações de configuração do Adobe Campaign em 2021 {#acc-config-updates}

![](../../assets/v7-only.svg)

A infraestrutura e as configurações devem ser atualizadas regularmente com as compilações e correções de produtos mais recentes. Essas correções são necessárias para garantir a continuidade do serviço e a segurança. Além disso, as atualizações serão necessárias para se alinharem às alterações de terceiros.

Como um **Cliente hospedado ou Managed Services**, o Adobe informará você sobre atualizações de build em intervalos regulares. Você deverá atualizar de acordo com as recomendações para garantir a conformidade.

Como um **Cliente local ou híbrido**, você deve atualizar sua implementação a intervalos regulares, de acordo com as builds mais recentes.

Por motivos de segurança, agora é necessário atualizar para uma das versões listadas abaixo. Além das etapas de atualização padrão, algumas tarefas manuais devem ser executadas para garantir que seu ambiente esteja seguro e pronto para futuras alterações de sistemas de Adobe ou de terceiros.

>[!NOTE]
>
>Em caso de dúvidas sobre essas alterações, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Atualizações de segurança {#acc-security-updates}

As versões mais recentes do Campaign vêm com uma correção de segurança que reforça a proteção contra problemas de SSRF (Server Side Request Forgery). Saiba mais [nesta página](https://helpx.adobe.com/br/security/products/campaign/apsb21-04.html).

**Você será afetado?**

Se o ambiente estiver em uma build inferior à listada abaixo, você será afetado:

* Gold Standard 11. [Saiba mais](../../rn/using/gold-standard.md)
* Campaign versão 21.1.1. [Saiba mais](../../rn/using/latest-release.md)
* Campaign versão 20.2.5. [Saiba mais](../../rn/using/release--2020.md#release-20-2-5-build-9188)
* Campaign versão 20.1.4. [Saiba mais](../../rn/using/release--2020.md#release-20-1-4-build-9126)
* Campaign versão 19.2.4. [Saiba mais](../../rn/using/release--2019.md#release-19-2-4-build-9082)
* Campaign versão 19.1.8. [Saiba mais](../../rn/using/release--2019.md#release-19-1-8-build-9039)

Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Como atualizar?**

Você precisa atualizar para uma das builds mais recentes listadas acima.

* Como um cliente híbrido, o Adobe informará sobre as datas de atualização programadas para suas instâncias de mid-sourcing. O Adobe recomenda que você atualize sua instância de marketing também.

   A nova build é compatível com a versão do Campaign Classic 17.9, mas o Adobe recomenda enfaticamente uma atualização em todas as instâncias para lidar com vulnerabilidades de segurança

* Como cliente local, você deve atualizar instâncias de marketing e mid-sourcing para a build mais recente.

>[!CAUTION]
>
>Se não for possível atualizar dentro do período de tempo recomendado, **você deve entrar em contato com a equipe de Atendimento ao cliente da Adobe para aplicar uma correção de segurança manual de curto prazo em suas instâncias**.

## Atualização do console do cliente do Campaign Classic  {#acc-cc-updates}

O **disponível** as versões do console abaixo devem ser instaladas para resolver uma regressão identificada recentemente. Essa regressão impedia o uso de alguns componentes do Console do cliente, como o seletor de datas e o gerenciamento de imagens nos deliveries. **Atualização do console** é obrigatório.

* Versão mais recente do Gold Standard 11 9032@10c2709. [Saiba mais](../../rn/using/gold-standard.md)
* Campaign versão 20.1.4. [Saiba mais](../../rn/using/release--2020.md#release-20-1-4-build-9126)
* Campaign versão 19.2.4. [Saiba mais](../../rn/using/release--2019.md#release-19-2-4-build-9082)
* Campaign versão 19.1.8. [Saiba mais](../../rn/using/release--2019.md#release-19-1-8-build-9039)

## Atualização do sistema Adobe Identity Management (IMS)

O Adobe Identity Service (IMS) interromperá o suporte a versões antigas do Internet Explorer da **30 de junho de 2021**. [Saiba mais](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

É necessária uma atualização do Console do cliente do Campaign para garantir a compatibilidade com o Adobe IMS.

**Você será afetado?**

Se você estiver se conectando ao Campaign [por meio de uma Adobe ID](../../integrations/using/about-adobe-id.md), por meio do Adobe Identity Management Service (IMS), a atualização para uma das novas versões listadas abaixo é obrigatória:

* Gold Standard 11. [Saiba mais](../../rn/using/gold-standard.md)
* Campaign versão 21.1.1. [Saiba mais](../../rn/using/latest-release.md)
* Campaign versão 20.2.5. [Saiba mais](../../rn/using/release--2020.md#release-20-2-5-build-9188)
* Campaign versão 20.1.4. [Saiba mais](../../rn/using/release--2020.md#release-20-1-4-build-9126)
* Campaign versão 19.2.4. [Saiba mais](../../rn/using/release--2019.md#release-19-2-4-build-9082)
* Campaign versão 19.1.8. [Saiba mais](../../rn/using/release--2019.md#release-19-1-8-build-9039)

Essas versões são fornecidas com um novo protocolo de conexão: a atualização é obrigatória para o servidor do Campaign e o Console do cliente poderem se conectar ao Campaign após **30 de junho de 2021**.

Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Como atualizar?**

Como cliente hospedado, o Adobe trabalhará com você para atualizar suas instâncias para a versão mais recente em breve.

Como cliente local/híbrido, você precisa atualizar para uma das versões mais recentes para se beneficiar do novo Console do cliente e garantir uma transição contínua **antes de 30 de junho de 2021**.

Depois que todas as instâncias forem atualizadas, o Console do cliente também precisará ser atualizado para essa versão.

* Saiba como acessar o [Adobe Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

* [Saiba como instalar o Console do cliente do Campaign](../../installation/using/installing-the-client-console.md).

## Integração com Experience Cloud Triggers {#acc-triggers-updates}

O serviço de autenticação oAuth herdado chegou ao fim da vida útil. A autenticação da integração dos acionadores, originalmente baseada na configuração da autenticação oAUTH para acessar o pipeline, foi movida para o Adobe I/O. Modo de autenticação oAuth herdado com o Campaign [foi aposentado](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) on **Setembro de 2021**. Os ambientes hospedados se beneficiarão de uma extensão até **23 de fevereiro de 2022**. Como cliente local ou híbrido, entre em contato com o Atendimento ao cliente do Adobe para estender o suporte até fevereiro de 2022. Você deve fornecer [o AppID do aplicativo OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) para a Adobe.

**Você será afetado?**

Se suas instâncias estiverem em execução em uma **versão anterior ao Campaign 19.1.8, 20.2.4, Gold Standard 11**, você está usando uma versão mais antiga da integração de acionadores por meio da autenticação oAuth: **é necessário atualizar para uma versão mais recente e migrar para o Adobe I/O**.

A atualização para uma das novas versões listadas abaixo é obrigatória:

* Gold Standard 11. [Saiba mais](../../rn/using/gold-standard.md)
* Campaign versão 21.1.1. [Saiba mais](../../rn/using/latest-release.md)
* Campaign versão 20.2.5. [Saiba mais](../../rn/using/release--2020.md#release-20-2-5-build-9188)
* Campaign versão 19.1.8. [Saiba mais](../../rn/using/release--2019.md#release-19-1-8-build-9039)

Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Como atualizar?**

Depois que as instâncias são atualizadas para uma versão mais recente, todos os clientes precisam seguir a [mover o procedimento para o novo modo de autenticação](../../integrations/using/configuring-adobe-io.md). Isso requer gerar o novo token de Adobe I/O e usá-lo na implementação.  

Além disso, para ambientes híbridos, os clientes precisam garantir que o pipeline de assimilação esteja configurado na instância de mid-sourcing. [Saiba mais](../../integrations/using/configuring-pipeline.md).

[Saiba como migrar para o Adobe I/O](../../integrations/using/configuring-adobe-io.md).

## Atualizações de APNs {#acc-apns-updates}

### API do provedor APNs com base em HTTP/2

Since **31 de março de 2021**, o serviço Apple Push Notification (APNs) não oferece mais suporte ao protocolo binário herdado. [Leia mais](https://developer.apple.com/news/?id=c88acm2b).

**Você é afetado?**

Se suas instâncias estiverem em execução em uma **versão anterior ao Campaign 21.1,** e ao enviar notificações por push com o protocolo binário Apple herdado, é necessário atualizar para a API do provedor APNs baseada em HTTP/2.

Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Como atualizar?**

Como cliente hospedado, se você tiver atualizado para a nova build, o Adobe já atualizou suas instâncias para a API baseada em HTTP/2.

Como cliente local/híbrido, você precisa atualizar sua configuração.

### Atualizações de certificado raiz APNs

Em 29 de março de 2021, uma atualização de infraestrutura do serviço de Notificação por Push (APNs) da Apple afetou o canal Adobe Campaign Classic iOS. Uma alteração na configuração do sistema operacional é **mandatory** para evitar a interrupção do canal de push do iOS.

Saiba mais sobre as alterações de APNs [nesta página](https://developer.apple.com/news/?id=7gx0a2lp).

**Você será afetado?**

Se estiver usando o Campaign para enviar notificações por push em dispositivos iOS, você será afetado.

**Como atualizar?**

Como cliente hospedado, nenhuma ação é necessária: O Adobe já incorporou o novo certificado raiz ao seu ambiente.

Como cliente local/híbrido, é necessário atualizar sua configuração para garantir uma transição contínua **antes de 29 de março de 2021**.

[Saiba como incorporar o novo certificado](ios-certificate-update.md).

## Links úteis

* [Atualizar seu ambiente](../../production/using/build-upgrade.md)
* [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md)
* [Baixar a build do Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html)
* [Disponibilizar o novo Console do cliente para os usuários](../../installation/using/client-console-availability-for-windows.md)
