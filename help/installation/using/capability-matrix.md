---
product: campaign
title: Matriz de recursos no local, híbrida e hospedada do Campaign
description: Saiba mais sobre as principais diferenças entre implantações locais e hospedadas
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 39%

---

# Matriz de recursos por modelo{#capability-matrix-per-model}

![](../../assets/v7-only.svg)

O Adobe Campaign Classic vem com um conjunto de módulos e opções. A disponibilidade desses módulos e sua configuração podem depender do tipo de implantação da sua instalação. Este artigo compartilha alguns detalhes sobre as principais diferenças para determinados recursos entre implantações totalmente hospedadas (Managed Services) e implantações locais.

Esta página mostra as principais diferenças entre implantações hospedadas (Managed Services) e locais. As especificidades de implantações híbridas dependem dos elementos hospedados pelo Adobe e hospedados em suas instalações.

Os diferentes modelos de hospedagem são introduzidos [nesta seção](../../installation/using/hosting-models.md).

## Disponibilidade por modelo de implantação {#capability-matrix}

| Recurso | Hospedado | Híbrido | No local | Detalhes |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configurar o servidor do Campaign | Sob demanda | Disponível | Disponível | [Saiba mais](../../installation/using/the-server-configuration-file.md) |
| CCO de email | Sob demanda | Sob demanda | Disponível | [Saiba mais](../../installation/using/email-archiving.md) |
| Gerenciar instância de execução do Centro de Mensagens | Sob demanda | Sob demanda | Disponível | [Saiba mais](../../message-center/using/about-transactional-messaging.md) |
| Gerenciamento de plataforma Mid-sourcing | Sob demanda | Sob demanda | Disponível | [Saiba mais](../../installation/using/mid-sourcing-server.md) |
| Renderização da caixa de entrada via Litmus | Sob demanda | Sob demanda | Disponível | [Saiba mais](../../delivery/using/inbox-rendering.md) |
| Integração com o IMS (Adobe ID) | Sob demanda | Sob demanda | Sob demanda | [Saiba mais](../../integrations/using/about-adobe-id.md) |
| Criptografar/descriptografar dados para transferências de arquivos | Sob demanda | Disponível | Disponível | [Saiba mais](../../platform/using/unzip-decrypt.md) |
| Compactação/descompactação de arquivos | Sob demanda | Disponível | Disponível | [Saiba mais](../../platform/using/unzip-decrypt.md) |
| Delegação de Nome de Domínio | Sob demanda | Sob demanda | Não disponível | [Saiba mais](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=pt-BR) |
| Instalação do SpamAssassin | Sob demanda | Disponível | Disponível | [Saiba mais](../../delivery/using/spamassassin.md) |
| Acesso aos relatórios de capacidade de delivery | Disponível | Sob demanda | Disponível | [Saiba mais](../../delivery/using/monitoring-deliverability.md) |
| Configuração da autenticação LDAP | Não disponível | Disponível | Disponível | [Saiba mais](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

O Adobe Campaign oferece a opção **Federated Data Access** (FDA) para processar informações armazenadas em um ou mais bancos de dados externos: é possível acessá-los sem alterar a estrutura dos dados do Adobe Campaign. [Saiba mais](../../installation/using/about-fda.md)

>[!CAUTION]
>
>O acesso a um banco de dados externo por meio do FDA só é possível para instalações locais ou híbridas, exceto com o [conector Snowflake](../../installation/using/configure-fda-snowflake.md).


**Consulte também**

* [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md)
* [Notas de versão](../../rn/using/latest-release.md)
* [Atualizações de Campaign Classic](../../rn/using/rn-overview.md)
* [Recursos descontinuados e removidos](../../rn/using/deprecated-features.md)
* [Versões do [!DNL Gold Standard] ](../../rn/using/gold-standard.md)
* [Programa do [!DNL Gold Standard]](../../rn/using/gs-overview.md)
