---
product: campaign
title: Notas de versão do [!DNL Gold Standard]
description: Notas de versão do Campaign Classic [!DNL Gold Standard]
feature: Overview
role: User
level: Beginner
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
source-git-commit: 2c548465a73bcd817c6d2b18853f4f074ed6adfa
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 87%

---

# Notas de versão do [!DNL Gold Standard]{#gold-standard}

![](../../assets/v7-only.svg)

Esta página lista versões do [!DNL Gold Standard]. Saiba mais sobre o Campaign [!DNL Gold Standard] [nesta página](gs-overview.md).

## ![](assets/do-not-localize/limited_2.png) [!DNL Gold Standard] versão 12{#gs-12}

_27 de agosto de 2021_

A build 9032@99a3894 inclui as seguintes correções:

* O recurso de assinatura de rastreamento foi aprimorado para evitar erros vinculados às ferramentas de terceiros (clientes de email, navegadores de Internet etc.) manipule caracteres especiais. Os parâmetros de URL agora são codificados.
* Correção de um problema com seletores de data que poderia resultar na exibição de uma mensagem de erro de bloqueador por parte de um console. (NEO-36345)

## ![](assets/do-not-localize/green_2.png) [!DNL Gold Standard] versão 11{#gs-11}

_14 de abril de 2021_

A compilação 9032@d030c36 inclui a seguinte correção:

* Correção de uma regressão do console do cliente que causava mensagens de erro persistentes na tela de conexão IMS. (NEO-34821)
* Esta build de console é necessária para manter [IMS access](../../technotes/using/ims-updates.md).

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!CAUTION]
>
> * Se você estiver se conectando ao Campaign com sua Adobe ID, por meio do Adobe Identity Management Service (IMS), a atualização é obrigatória para o servidor do Campaign e o console do cliente poderem se conectar ao Campaign depois de **30 de junho de 2021**. [Saiba mais](../../technotes/using/ims-updates.md)
> * Esta versão vem com uma [correção de segurança](https://helpx.adobe.com/br/security/products/campaign/apsb21-04.html): a atualização é obrigatória para reforçar a segurança do ambiente.
> * Se você estiver usando a integração dos acionadores da Experience Cloud por meio da autenticação oAuth, será necessário migrar para o Adobe I/O conforme descrito [nesta página](../../integrations/using/configuring-adobe-io.md). O modo de autenticação oAuth herdado com o Campaign [foi removido](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) em **18 de agosto de 2021**. Os ambientes hospedados se beneficiam de uma extensão até **30 de novembro de 2021**. Como cliente local ou híbrido, entre em contato com o Atendimento ao cliente da Adobe para estender o suporte até 30 de novembro de 2021. Você deve fornecer [o AppID do aplicativo OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) para o Adobe.

>
>Saiba mais nas perguntas [[!DNL Gold Standard] frequentes de atualização do 11](https://helpx.adobe.com/br/campaign/kb/gold-standard-upgrade.html)

_2 de março de 2021_

A compilação 9032@10c2709 inclui a seguinte correção:

* Correção de uma regressão que impedia o uso de alguns componentes do console, como o seletor de datas e o gerenciamento de imagens nos deliveries. (NEO-31453, NEO-31454)

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!NOTE]
>
> Conecte-se à [Distribuição de software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) para baixar a nova versão. Saiba como propor a atualização do console para todos os usuários finais [nesta página](../../installation/using/client-console-availability-for-windows.md).

_22 de dezembro de 2020_

<!--
>[!CAUTION]
>
> * This release comes with a new connection protocol: if you are connecting to Campaign through Adobe Identity Service (IMS), upgrade is mandatory for both Campaign server and client console to be able to connect to Campaign after **June 30, 2021**. [Learn more](../../technotes/using/ims-updates.md)
> * This release comes with a [security fix](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): upgrade is mandatory to reinforce your environment security. 
> * If you are using the Experience Cloud Triggers integration through oAuth authentication, you need to move to Adobe I/O as described [in this page](../../integrations/using/configuring-adobe-io.md). Legacy oAuth authentication mode with Campaign will be retired on **November 30, 2021**.
>
>Learn more in the [[!DNL Gold Standard] 11 upgrade FAQ](https://helpx.adobe.com/campaign/kb/gold-standard-upgrade.html).
-->
O build 9032@d3b452f inclui os seguintes aprimoramentos e correções:

* O protocolo de conexão foi atualizado para seguir o novo mecanismo de autenticação IMS.

* A autenticação da integração dos acionadores originalmente baseada na configuração da autenticação oAUTH para acessar o pipeline agora foi alterada e movida para o Adobe I/O. [Saiba mais](../../integrations/using/configuring-adobe-io.md)

* Após o [fim do suporte para o protocolo binário herdado APNs do iOS](https://developer.apple.com/news/?id=c88acm2b), todas as instâncias que usam esse protocolo serão atualizadas para o protocolo HTTP/2 após a atualização.

* Correção de um problema de segurança para reforçar a proteção contra situações de SSRF (Server Side Request Forgery). (NEO-27777)




* Correção de um problema que resultava em falha em fluxos de trabalho ao executar uma atividade de **Enriquecimento**. (NEO-17338)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versão 10{#gs-10}

_7 de julho de 2020_

A compilação 9032@efd8a94 inclui a seguinte correção:

Correção de um problema que impedia o funcionamento do rastreamento quando o recurso de assinatura era desativado. (NEO-26411)

>[!CAUTION]
>
>Recomendamos que você atualize o console do cliente com o disponível nesta versão. Consulte [esta página](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versão 9{#gs-9}

_22 de junho de 2020_

A build 9032@800be2e inclui as seguintes correções:

* O conector HTTP2 para iOS foi aprimorado (atualizações de terceiros e gerenciamento de erros). (25904, NEO-, NEO-25903, NEO-25799)

As seguintes correções estão relacionadas ao mecanismo de segurança do link de rastreamento (consulte a [lista de verificação de segurança e privacidade](https://helpx.adobe.com/br/campaign/kb/acc-security.html#signature-mechanism)):

* Correção de um problema que impedia o funcionamento do rastreamento de &quot;cliques de notificação&quot; (notificações por push de iOS e Android). (NEO-25965)
* Correção de um problema que poderia impedir a abertura/clique de URLs de rastreamento ao usar determinadas versões herdadas do Outlook.  (NEO-25688)
* Correção de um problema que impedia o funcionamento do rastreamento de URLs usando fragmentos em parâmetros de personalização (tags de âncora com sinal de hashtag). (NEO-25774)
* Correção de um problema com o serviço anti-phishing. (NEO-25283)
* Correção de um problema de rastreamento ao usar fórmulas de rastreamento personalizadas específicas. (NEO-25277)





## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versão 8{#gs-8}

_29 de abril de 2020_

A build 9032@3a9dc9c inclui as seguintes correções:

* A segurança no rastreamento de links no email foi aprimorada. Ela é ativada por padrão para todos os clientes. Um recurso de segurança adicional e aprimorado está disponível e pode ser ativado ao acessar o Atendimento ao cliente. Mais detalhes sobre o recurso e as etapas para clientes não hospedados para habilitá-lo podem ser encontrados na [lista de verificação de Segurança e Privacidade](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Se tiver problemas com notificações por push usando links de rastreamento ou delivery usando tags de âncora, recomendamos desativar o novo mecanismo de assinatura para links de rastreamento. O procedimento está detalhado [nesta página](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)

* Correção de um problema que impedia a exibição de imagens na entrega de linha. (NEO-23207)
* Correção de um problema com a atividade **Transferência de Arquivo**, que impedia que a autenticação com a chave SFTP funcionasse no Debian 9. (NEO-23183)
* Correção de um problema que poderia afetar a notificação via push quando enviada em alta frequência. (NEO-20516)
* Correção de um problema no gerenciamento de respostas de oferta que resulta em falhas no servidor da Web. (NEO-19482)
* Correção de um erro no gerenciamento do LibreOffice que impede a exportação de relatórios. (NEO-20982)
* Correção de um problema que causa um erro ao atualizar vários workflows por meio do uso de uma atividade de pesquisa.
* Melhora do gerenciamento do LibreOffice para evitar falhas na pré-visualização de email com arquivos .odt.
* Melhora no gerenciamento da conexão do Apache para evitar latência no serviço da Web.
* Melhora na exibição da tag da versão (7 dígitos) no menu **Sobre**.
* Correção de uma prevenção no gerenciamento de listas que impede a publicação de ofertas.
* Correção de uma regressão que resulta em falha do workflow de limpeza.
* Correção de uma regressão menor nos logs de workflow de limpeza.

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versão 6{#gs-6}

_9 de março de 2020_

A build 9032@19f73c5 inclui a seguinte correção:

* Correção de um problema com a conta externa que usa o FTP sobre SSL. (NEO-20498)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versão 5{#gs-5}

_17 de dezembro de 2019_

A build 9032@d6b8062 inclui a seguinte correção:

* Correção de um problema de rastreamento nos seguintes canais de comunicação: dispositivos móveis (SMS, MMS), push (iOS, Android) e redes sociais (Facebook, Twitter). (NEO-19595)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versão 4{#gs-4}

_11 de dezembro de 2019_

A build 9032@bc4a935 inclui a seguinte correção:

* Correção de um problema de desempenho ao enviar mensagens com um banco de dados MSSQL. (NEO-17558)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versão 3{#gs-3}

_20 de novembro de 2019_

A build 9032@3468c7b inclui as seguintes correções:

* Correção de um problema de logon por autenticação IMS. (NEO-17312)
* Correção de um problema ao exibir relatórios cumulativos em várias entregas. (NEO-18165)
* Correção de um problema que poderia bloquear ou fazer o servidor web travar.

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versão 2{#gs-2}

_19 de setembro de 2019_

A build 9032@cee805c inclui as seguintes correções:

* Correção de um problema ao usar o Conector CRM para Salesforce. (NEO-17712)
* Correção de um problema de índice que causava problemas de desempenho ao enviar mensagens transacionais.

## ![](assets/do-not-localize/red_2.png) Versão 19.1.4 – Build 9032{#release-19-1-4-build-9032}

_13 de agosto de 2019_

A build inicial 19.1.4 inclui as seguintes correções:

* Correção de um problema em que a atividade do programador gerasse mensagens de erro indesejáveis durante a configuração do assistente. Reversão de atualização do NEO-11662. (NEO-17097)
* Correção de uma regressão causada pelo NEO-12727, que podia interromper os fluxos de trabalho quando uma atividade de teste era executada duas vezes. (NEO-16835)
* Correção de um problema que resultava em um código HTTP incorreto ser retornado (HTTP 200 OK em vez de HTTP 403 Forbidden) quando um token de sessão inválido ou expirado era usado em chamadas API. (NEO-16826)
* Correção de um problema com a chave DKIM, que não era inserida em emails, causando problemas de entrega. (NEO-16804)
* Correção de vários problemas com o agendamento de fluxos de trabalho. Os fluxos de trabalho eram agendados para serem executados uma vez por dia sem levar em consideração a configuração do programador. (NEO-16619, NEO-16426)
