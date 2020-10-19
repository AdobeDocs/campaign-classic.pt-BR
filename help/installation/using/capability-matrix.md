---
title: Matriz de recursos no local, híbrido e hospedado da campanha
description: Conheça as principais diferenças entre as implantações hospedadas e no local
page-status-flag: never-activated
uuid: d1c786a1-2691-4966-9108-059004050464
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 582f7ac6-cebe-4b47-8730-bbc16fd6b1bd
translation-type: tm+mt
source-git-commit: c2e1b4cf7051b7f1b9d5f2db0d9f51a733ca2abc
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 21%

---


# Matriz de recursos por modelo de hospedagem {#capability-matrix-per-model}

O Adobe Campaign Classic vem com um conjunto de módulos e opções. A disponibilidade desses módulos e sua configuração podem depender do tipo de implantação da sua instalação. Este artigo compartilha alguns detalhes sobre as principais diferenças para determinados recursos entre implantações totalmente hospedadas (Managed Services) e implantações locais.

Esta página mostra as principais diferenças entre as implantações hospedadas (Managed Services) e locais. As especificidades de implantações híbridas dependem dos elementos hospedados pelo Adobe e hospedados em suas instalações.

Os diferentes modelos de hospedagem são apresentados [nesta seção](../../installation/using/hosting-models.md).

## Matriz de recursos{#capability-matrix}

| Recurso | Hospedado | Híbrido | Local | Detalhes |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configurar servidor de Campanha | Sob demanda | Disponível | Disponível | O arquivo[de configuração do](../../installation/using/the-server-configuration-file.md)servidor só pode ser modificado por Adobe para clientes hospedados. |
| Cco de email | Sob demanda | Sob demanda | Disponível | Para arquiteturas hospedadas e híbridas, entre em contato com o executivo da sua conta para ativar o email CCO. Para instalações no local, siga as diretrizes da documentação. [Saiba mais](../../installation/using/email-archiving.md) |
| Gerenciar instância de execução do Centro de Mensagens | Sob demanda | Sob demanda | Disponível | Para implantações hospedadas, determinadas configurações, como a criação de usuários na instância de execução, só podem ser executadas por Adobe. [Saiba mais](../../message-center/using/about-transactional-messaging.md) |
| Gerenciamento da plataforma Mid-sourcing | Sob demanda | Sob demanda | Disponível | As plataformas mid-sourcing hospedadas pelo Adobe só podem ser configuradas por Adobe. |
| Renderização da caixa de entrada via Litmus | Sob demanda | Sob demanda | Disponível | Você precisa de uma conta de Litmus. É necessário acessar o Adobe para obter os detalhes necessários ou executar a configuração de renderização da Caixa de entrada. [Saiba mais](../../delivery/using/inbox-rendering.md) |
| Integração com o IMS (Adobe ID) | Sob demanda | Sob demanda | Sob demanda | O provisionamento de IMS é executado pelo Adobe. Essa integração é um pré-requisito para integrações Adobe Experience Cloud. [Saiba mais](../../integrations/using/about-adobe-id.md) |
| Criptografar/descriptografar dados para transferências de arquivos | Sob demanda | Disponível | Disponível | A ativação do pré ou pós-processamento de arquivos requer a instalação do utilitário necessário no servidor Adobe Campaign. Os clientes hospedados podem usar Painéis de controle do Campaign de Campanha. [Saiba mais](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Zipping/Unzipping de arquivos | Disponível sob demanda | Disponível | A ativação do pré ou pós-processamento de arquivos requer a instalação do utilitário necessário no servidor Adobe Campaign. Os clientes hospedados podem usar Painéis de controle do Campaign de Campanha. [Saiba mais](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Delegação de Nome de Domínio | Sob demanda | Sob demanda | Não disponível | [Saiba mais](https://helpx.adobe.com/br/campaign/kb/domain-name-delegation.html) |
| Instalação do SpamAssassin | Sob demanda | Disponível | Disponível | A instalação do SpamAssassin requer a edição do arquivo de configuração do servidor. [Saiba mais](../../delivery/using/spamassassin.md) |
| Acesso aos relatórios de material de entrega | Disponível | Sob demanda | Disponível | Em determinadas implantações híbridas, os relatórios de capacidade de entrega não podem ser acessados da instância de marketing. |
| Configuração da autenticação LDAP | Não disponível | Disponível | Disponível | A configuração LDAP só é possível para instalações locais ou híbridas. [Saiba mais](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

O Adobe Campaign oferece a opção **Federated Data Access** (FDA) para processar informações armazenadas em um ou mais bancos de dados externos: é possível acessá-los sem alterar a estrutura dos dados do Adobe Campaign. [Saiba mais](../../platform/using/about-fda.md)

>[!CAUTION]
>
>Accessing an external database via FDA is only possible for on-premise or hybrid installations, except with the [Snowflake connector](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).


**Consulte também**

* [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md)
* [Notas de versão](../../rn/using/latest-release.md)
* [Campaign Classic upgrades](../../rn/using/rn-overview.md)
* [Recursos descontinuados e removidos](../../rn/using/deprecated-features.md)
* [Versões Gold Standard](../../rn/using/gold-standard.md)
* [Programa](https://helpx.adobe.com/br/campaign/kb/gold-standard.html)Gold Standard.
