---
product: campaign
title: Matriz de recursos no local, híbridos e hospedados do Campaign
description: Saiba mais sobre as principais diferenças entre implantações hospedadas e no local
feature: Installation, Architecture
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 47%

---

# Matriz de recursos por modelo{#capability-matrix-per-model}



O Adobe Campaign Classic vem com um conjunto de módulos e opções. A disponibilidade desses módulos e sua configuração podem depender do tipo de implantação da sua instalação. Este artigo compartilha alguns detalhes sobre as principais diferenças para determinados recursos entre implantações totalmente hospedadas (Managed Services) e no local.

Esta página mostra as principais diferenças entre implantações locais e hospedadas (Managed Services). As especificidades das implantações híbridas dependem dos elementos hospedados pelo Adobe e hospedados em suas instalações.

Os diferentes modelos de hospedagem são introduzidos [nesta seção](../../installation/using/hosting-models.md).

## Disponibilidade por modelo de implantação {#capability-matrix}

| Recurso | Hospedado | Híbrido | No local | Detalhes |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configurar o servidor do Campaign | Sob demanda | Disponível | Disponível | [Saiba mais](../../installation/using/the-server-configuration-file.md) |
| CCO de email | Sob demanda | Sob demanda | Disponível | [Saiba mais](../../installation/using/email-archiving.md) |
| Gerenciar instância de execução do Centro de mensagens | Sob demanda | Sob demanda | Disponível | [Saiba mais](../../message-center/using/about-transactional-messaging.md) |
| Gerenciamento da plataforma Mid-sourcing | Sob demanda | Sob demanda | Disponível | [Saiba mais](../../installation/using/mid-sourcing-server.md) |
| Renderização da caixa de entrada via Litmus | Sob demanda | Sob demanda | Disponível | [Saiba mais](../../delivery/using/inbox-rendering.md) |
| Integração com IMS (Adobe ID) | Sob demanda | Sob demanda | Sob demanda | [Saiba mais](../../integrations/using/about-adobe-id.md) |
| Criptografar/descriptografar dados para transferências de arquivos | Sob demanda | Disponível | Disponível | [Saiba mais](../../platform/using/unzip-decrypt.md) |
| Compactação/descompactação de arquivos | Sob demanda | Disponível | Disponível | [Saiba mais](../../platform/using/unzip-decrypt.md) |
| Delegação de nome de domínio | Sob demanda | Sob demanda | Indisponível | [Saiba mais](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=pt-BR) |
| Instalação do SpamAssassin | Sob demanda | Disponível | Disponível | [Saiba mais](../../delivery/using/spamassassin.md) |
| Acesso aos relatórios de entrega | Disponível | Sob demanda | Disponível | [Saiba mais](../../delivery/using/monitoring-deliverability.md) |
| Configuração da autenticação LDAP | Não disponível | Disponível | Disponível | [Saiba mais](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

O Adobe Campaign oferece a opção **Federated Data Access** (FDA) para processar informações armazenadas em um ou mais bancos de dados externos: é possível acessá-los sem alterar a estrutura dos dados do Adobe Campaign. [Saiba mais](../../installation/using/about-fda.md)

>[!CAUTION]
>
>Sistemas de banco de dados externos compatíveis dependem do seu modelo de hospedagem. Saiba mais em [Matriz de compatibilidade do Campaign](../../rn/using/compatibility-matrix.md).
>

**Consulte também**

* [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md)
* [Notas de versão](../../rn/using/latest-release.md)
* [Atualizações de Campaign Classic](../../rn/using/rn-overview.md)
* [Recursos descontinuados e removidos](../../rn/using/deprecated-features.md)
* [Versões [!DNL Gold Standard] ](../../rn/using/gold-standard.md)
