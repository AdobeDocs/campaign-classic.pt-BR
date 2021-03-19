---
solution: Campaign Classic
product: campaign
title: Nota técnica
description: Nota técnica
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 587daebd8a779bb9d0917fd2dfab4144494809e3
workflow-type: tm+mt
source-wordcount: '1027'
ht-degree: 14%

---


# Atualizações de configuração do Adobe Campaign - março de 2021 {#acc-config-updates}

Você deve manter sua infraestrutura e configurações atualizadas com as builds e correções de produtos mais recentes. Essas correções são obrigatórias para garantir a continuidade e a segurança do serviço. Além disso, é necessário adaptar sua implementação para alinhar-se às alterações de terceiros.

Como cliente hospedado, o Adobe informará você sobre as atualizações de build necessárias a intervalos regulares. Você precisa atualizar de acordo com as recomendações para garantir a conformidade.

Como cliente local/híbrido, por motivos de segurança, você deve atualizar para uma das versões listadas nesta página. Além disso, algumas tarefas manuais devem ser executadas para garantir que seu ambiente esteja seguro e pronto para futuras alterações de sistemas Adobe ou de terceiros.

>[!NOTE]
>
>Para qualquer dúvida sobre essas alterações, entre em contato com o [Adobe Customer Care](https://helpx.adobe.com/br/enterprise/admin-guide.html).


## Atualizações de segurança

As versões mais recentes do Campaign são fornecidas com uma correção de segurança que reforça a proteção contra problemas de falsificação de solicitação do lado do servidor (SSRF). Saiba mais [nesta página](https://helpx.adobe.com/security/products/campaign/apsb21-04.html).

**Você é afetado?**

Se o ambiente estiver em uma build inferior à listada abaixo, você será afetado:

* Gold Standard 11. [Saiba mais](../rn/using/gold-standard.md)
* Campaign versão 21.1.1. [Saiba mais](../rn/using/latest-release.md)
* Campaign versão 20.3.3. [Saiba mais](../rn/using/release--20-3.md)
* Campaign versão 20.2.4. [Saiba mais](../rn/using/release--20-2.md)
* Campaign versão 20.1.4. [Saiba mais](../rn/using/release--20-1.md)
* Campaign versão 19.2.4. [Saiba mais](../rn/using/release--19-2.md)
* Campaign versão 19.1.8. [Saiba mais](../rn/using/release--19-1.md)

**Como atualizar?**

Você precisa atualizar para uma das builds mais recentes listadas acima.

* Como um cliente híbrido, o Adobe atualizará a instância mid-sourcing para a nova versão e você é altamente recomendado atualizar a instância de marketing também.

   A nova build é compatível com pelo menos a versão do Campaign Classic 17.9, mas para evitar qualquer lacuna de segurança, o Adobe recomenda que todas as instâncias sejam atualizadas para uma nova build. 

* Como cliente local, você deve atualizar instâncias de marketing e mid-sourcing para uma build mais recente.

>[!CAUTION]
>
>Se não for possível atualizar por enquanto, **você deve entrar em contato com a equipe de Atendimento ao Cliente do Adobe para aplicar manualmente uma correção de segurança em suas instâncias**.


## Atualização do console do cliente do Campaign

A build Gold Standard 11 mais recente corrige uma regressão que impedia o uso de alguns componentes do Console do cliente, como o seletor de datas e o gerenciamento de imagens nas entregas. A atualização do console é obrigatória.

[Saiba mais](../rn/using/gold-standard.md).

>[!NOTE]
>
>O novo Console do cliente para outras versões estará disponível em breve.

## Atualização do sistema Adobe Identity Management (IMS)

O Adobe Identity Service (IMS) interromperá o suporte a versões antigas do Internet Explorer a partir de **30 de junho de 2021**. [Saiba mais](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

O Console do cliente do Campaign foi atualizado para garantir a compatibilidade com o Adobe IMS.

**Você é afetado?**

Se você estiver se conectando ao Campaign [por meio de um Adobe ID](../integrations/using/about-adobe-id.md), por meio do Adobe Identity Management Service (IMS), a atualização para uma das novas versões listadas abaixo é obrigatória:

* Gold Standard 11. [Saiba mais](../rn/using/gold-standard.md)
* Campaign versão 21.1.1. [Saiba mais](../rn/using/latest-release.md)
* Campaign versão 20.3.3. [Saiba mais](../rn/using/release--20-3.md)
* Campaign versão 20.2.4. [Saiba mais](../rn/using/release--20-2.md)
* Campaign versão 20.1.4. [Saiba mais](../rn/using/release--20-1.md)
* Campaign versão 19.2.4. [Saiba mais](../rn/using/release--19-2.md)
* Campaign versão 19.1.8. [Saiba mais](../rn/using/release--19-1.md)

Essas versões são fornecidas com um novo protocolo de conexão: a atualização é obrigatória para o servidor do Campaign e o Console do cliente poderem se conectar ao Campaign após **30 de junho de 2021**.

**Como atualizar?**

Como cliente hospedado, nenhuma ação é necessária: O Adobe já atualizou suas instâncias para uma versão mais recente.

Como cliente local/híbrido, é necessário atualizar para uma das versões mais recentes para se beneficiar do novo Console do cliente e garantir uma transição contínua **antes de 30 de junho de 2021**.

Depois que todas as instâncias forem atualizadas, o Console do cliente também precisará ser atualizado para essa versão.

* Saiba como acessar o [Adobe Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

* [Saiba como instalar o Console](../installation/using/installing-the-client-console.md) do cliente do Campaign.

## Integração com Experience Cloud Triggers

O serviço de autenticação oAuth herdado chegou ao fim da vida útil. A autenticação da integração dos acionadores, originalmente baseada na configuração da autenticação oAUTH para acessar o pipeline, foi movida para o Adobe I/O. Ele será removido em **30 de novembro de 2021**. [Saiba mais](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email).

**Você é afetado?**

Se suas instâncias estiverem em execução em uma versão **anterior à Campanha 19.1.8, 20.2.4, Gold Standard 11**, você estará usando uma versão mais antiga da integração de acionadores por meio da autenticação oAuth: **é necessário atualizar para uma versão mais recente e ir para Adobe I/O**.

A atualização para uma das novas versões listadas abaixo é obrigatória:

* Gold Standard 11. [Saiba mais](../rn/using/gold-standard.md)
* Campaign versão 21.1.1. [Saiba mais](../rn/using/latest-release.md)
* Campaign versão 20.3.3. [Saiba mais](../rn/using/release--20-3.md)
* Campaign versão 20.2.4. [Saiba mais](../rn/using/release--20-2.md)
* Campaign versão 19.1.8. [Saiba mais](../rn/using/release--19-1.md)

**Como atualizar?**

Depois que as instâncias são atualizadas para uma versão mais nova, todos os clientes precisam seguir o [procedimento para mover para o novo modo de autenticação](../integrations/using/configuring-adobe-io.md). Isso requer gerar o novo token de Adobe I/O e usá-lo na implementação.  

Além disso, para ambientes híbridos, os clientes precisam garantir que o pipeline de assimilação esteja configurado na instância de mid-sourcing. [Saiba mais](../integrations/using/configuring-pipeline.md).

[Saiba como migrar para o Adobe I/O](../integrations/using/configuring-adobe-io.md).

## Atualizações de APNs

### API do provedor APNs com base em HTTP/2

O serviço Apple Push Notification (APNs) não oferecerá mais suporte ao protocolo binário herdado a partir de **31 de março de 2021**. [Leia mais](https://developer.apple.com/news/?id=c88acm2b).

**Você é afetado?**

Se suas instâncias estiverem em execução em uma versão **anterior ao Campaign 21.1,** e enviarem notificações por push com o protocolo binário herdado da Apple, será necessário atualizar para a API do provedor APNs baseada em HTTP/2.

**Como atualizar?**

Como cliente hospedado, nenhuma ação é necessária: O Adobe já atualizou suas instâncias para a API baseada em HTTP/2.

Como cliente local/hospedado, é necessário atualizar sua configuração. [Saiba como migrar para HTTP/2](https://helpx.adobe.com/campaign/kb/migrate-to-apns-http2.html)

### Atualizações de certificado raiz APNs

Em 29 de março de 2021, uma atualização de infraestrutura do serviço de notificação por push (APNs) da Apple afetará o canal do Adobe Campaign Classic iOS. Uma alteração na configuração do sistema operacional é **mandatory** para evitar a interrupção do canal de push do iOS.

Saiba mais sobre as alterações de APNs [nesta página](https://developer.apple.com/news/?id=7gx0a2lp).

**Você é afetado?**

Se estiver usando o Campaign para enviar notificações por push em dispositivos iOS, você será afetado.

**Como atualizar?**

Como cliente hospedado, nenhuma ação é necessária: O Adobe já incorporou o novo certificado raiz ao seu ambiente.

Como cliente local/híbrido, você precisa atualizar sua configuração para garantir uma transição contínua **antes de 29 de março de 2021**.

[Saiba como incorporar o novo certificado](ios-certificate-update.md).


## Links úteis

* [Atualizar seu ambiente](../production/using/build-upgrade.md)
* [Perguntas frequentes de atualização de build](../platform/using/faq-build-upgrade.md)
* [Baixar a build do Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html)
* [Disponibilizar o novo Console do cliente para os usuários](../installation/using/client-console-availability-for-windows.md)
