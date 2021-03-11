---
solution: Campaign Classic
product: campaign
title: Nota técnica
description: Nota técnica
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 87844fae046dff69193d3462c802057499f406ef
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 11%

---


# Atualizações de configuração do Adobe Campaign - março de 2021 {#acc-config-updates}

Você precisa manter sua infraestrutura e configurações atualizadas com as builds e correções de produtos mais recentes. Essas correções são obrigatórias para garantir a continuidade e a segurança do serviço.

Os usuários da campanha precisam atualizar para uma das versões mais recentes abaixo:

* Gold Standard 11. [Saiba mais](../rn/using/gold-standard.md)
* Campaign versão 21.1.1. [Saiba mais](../rn/using/latest-release.md)
* Campaign versão 20.3.3. [Saiba mais](../rn/using/release--20-3.md)
* Campaign versão 20.2.4. [Saiba mais](../rn/using/release--20-2.md)
* Campaign versão 20.1.4. [Saiba mais](../rn/using/release--20-1.md)
* Campaign versão 19.2.4. [Saiba mais](../rn/using/release--19-2.md)
* Campaign versão 19.1.8. [Saiba mais](../rn/using/release--19-1.md)

Esses builds garantem a continuidade de determinados serviços do Campaign: Experience Cloud Triggers integração, autenticação APNs e o novo protocolo de conexão que afeta o mecanismo de autenticação do Adobe Identity Management Service (IMS).

Como cliente hospedado, nenhuma ação é necessária: O Adobe é o proprietário das atualizações de atualização e configuração da build para você.

Como cliente local/híbrido, é necessário atualizar para uma das versões listadas acima. Além disso, você precisa executar algumas tarefas manuais para garantir que seu ambiente esteja seguro e pronto para futuras alterações de sistemas Adobe ou de terceiros.

## Atualizações de segurança

As versões mais recentes do Campaign são fornecidas com uma correção de segurança que reforça a proteção contra problemas de falsificação de solicitação do lado do servidor (SSRF). Saiba mais [nesta página](https://helpx.adobe.com/security/products/campaign/apsb21-04.html).

**Você é afetado?**

Se o ambiente estiver em uma build inferior à Campanha 21.1, você será afetado.

**Como atualizar?**

Você precisa atualizar para uma das builds mais recentes listadas acima.

* Como um cliente híbrido, o Adobe atualizará a instância mid-sourcing para a nova versão e você é altamente recomendado atualizar a instância de marketing também.

   A nova build é compatível com pelo menos a versão do Campaign Classic 17.9, mas para evitar qualquer lacuna de segurança, o Adobe recomenda que todas as instâncias sejam atualizadas para uma nova build. 

* Como cliente local, você deve atualizar instâncias de marketing e mid-sourcing para uma nova build.

>[!CAUTION]
>
>Se não for possível atualizar por enquanto, **você deve entrar em contato com a equipe de Atendimento ao Cliente do Adobe para aplicar manualmente uma correção de segurança em suas instâncias**.


## Atualização do console do cliente do Campaign

A build Gold Standard 11 mais recente corrige uma regressão que impedia o uso de alguns componentes do console, como o seletor de datas e o gerenciamento de imagens nos deliveries. A atualização do console é obrigatória.

[Saiba mais](../rn/using/gold-standard.md).

## Conectar-se ao Campaign por meio do IMS

O Adobe Identity Service (IMS) deixará de oferecer suporte às versões antigas do Internet Explorer a partir de 30 de junho de 2021. [Saiba mais](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html). O Console do Campaign foi atualizado para garantir a compatibilidade com o IMS.

**Você é afetado?**

Se estiver se conectando ao Campaign [por meio de um Adobe ID](../integrations/using/about-adobe-id.md), por meio do Adobe Identity Service (IMS), a atualização para uma das novas versões listadas acima é obrigatória para o servidor do Campaign e o console do cliente poderem se conectar ao Campaign após **30 de junho de 2021**.

**Como atualizar?**

Como cliente hospedado, nenhuma ação é necessária: O Adobe já atualizou suas instâncias para uma versão mais recente.

Como cliente local/híbrido, é necessário atualizar para uma das versões mais recentes para se beneficiar do novo Console do cliente e garantir uma transição contínua **antes de 31 de março de 2021**.

## Integração com Experience Cloud Triggers

O serviço herdado de autenticação oAuth chegou ao fim da vida útil e será descontinuado em 30 de junho de 2021. [Saiba mais](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411).

**Você é afetado?**

Se você estiver usando uma versão mais antiga da integração de acionadores por meio da autenticação oAuth, **será necessário mover para o Adobe I/O**.

**Como atualizar?**

[Saiba como migrar para o Adobe I/O](../integrations/using/configuring-adobe-io.md).

## API do provedor APNs com base em HTTP/2

O serviço de notificação por push da Apple (APNs) não oferecerá mais suporte ao protocolo binário herdado a partir de 31 de março de 2021. [Leia mais](https://developer.apple.com/news/?id=c88acm2b).

**Você é afetado?**

Se suas instâncias estiverem em execução em uma versão anterior ao Campaign 21.1 e enviarem notificações por push com o protocolo binário herdado da Apple, será necessário atualizar para a API do provedor APNs baseada em HTTP/2.

**Como atualizar?**

Como cliente hospedado, nenhuma ação é necessária: O Adobe já atualizou suas instâncias para a API baseada em HTTP/2.

Como cliente local/hospedado, é necessário atualizar sua configuração. [Saiba como migrar para HTTP/2](https://helpx.adobe.com/campaign/kb/migrate-to-apns-http2.html)

## Atualizações de certificado raiz APNs

Em 29 de março de 2021, uma atualização de infraestrutura do serviço de notificação por push (APNs) da Apple afetará o canal do Adobe Campaign Classic iOS. Uma alteração na configuração do sistema operacional é **mandatory** para evitar a interrupção do canal de push do iOS.

Saiba mais sobre as alterações de APNs [nesta página](https://developer.apple.com/news/?id=7gx0a2lp).

**Você é afetado?**

Se estiver usando o Campaign para enviar notificações por push em dispositivos iOS, você será afetado.

**Como atualizar?**

Como cliente hospedado, nenhuma ação é necessária: O Adobe já incorporou o novo certificado raiz ao seu ambiente.

Como cliente local/híbrido, você precisa atualizar sua configuração para garantir uma transição contínua **antes de 29 de março de 2021**.

[Saiba como incorporar o novo certificado](ios-certificate-update.md)
