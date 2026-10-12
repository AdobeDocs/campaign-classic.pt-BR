---
title: Migrar operadores do Campaign para o Adobe Identity Management System (IMS)
description: Saiba como migrar operadores do Campaign para o Adobe Identity Management System (IMS)
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
TQID: 'https://experienceleague.adobe.com/drpNkA9cj7Prid--GixHMQ48CO7ZC9qqX4w5fnTiD88'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 4bc1e76d129c6a6aa15b7e3915232043bd6f4286
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 4%
---
# Migrar operadores do Campaign para o Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Como parte do esforço para reforçar a segurança e o processo de autenticação, a Adobe Campaign recomenda migrar o modo de autenticação do usuário final da autenticação nativa de logon/senha para o Adobe Identity Management System (IMS). Todos os operadores devem implementar o [Adobe Identity Management System (IMS)](https://helpx.adobe.com/br/enterprise/using/identity.html){target="_blank"} para se conectar ao Campaign.

Saiba mais sobre esta migração em [esta página](ac-ims.md).

## O que mudou? {#move-to-ims-changes}

Com o Campaign Classic, todos os usuários regulares já podem se conectar ao console do cliente do Adobe Campaign usando sua Adobe ID, por meio do Adobe Identity Management System (IMS). No entanto, as conexões de usuário/senha ainda estão disponíveis. Isso não será mais permitido com o Campaign v8.

Além disso, como parte do esforço para reforçar a segurança e o processo de autenticação, o aplicativo cliente do Adobe Campaign agora chama as APIs do Campaign diretamente usando o token de conta técnica do IMS. A migração para operadores técnicos é detalhada em um artigo dedicado, disponível em [esta página](ims-migration.md).

Essa alteração já é aplicável no Campaign Classic v7 e será **obrigatória** para mover para o Campaign v8.

A Adobe apoia você nesse esforço de migração. Você pode encontrar contexto detalhado e diretrizes passo a passo no artigo abaixo.

## Você será afetado?{#migrate-ims-impacts}

Esse procedimento se aplica a todos os usuários do Campaign que ainda não estão se conectando ao Campaign com sua Adobe ID.

Se os operadores em sua organização estiverem se conectando ao console do cliente do Campaign usando seu logon/senha (também conhecido como. autenticação nativa), você será afetado e deverá migrar esses operadores para o Adobe IMS conforme detalhado abaixo.

A migração para o [Adobe Identity Management System (IMS)](https://helpx.adobe.com/br/enterprise/using/identity.html){target="_blank"} é uma obrigação de segurança para tornar seus ambientes seguros e padronizados, pois a maioria das outras soluções e aplicativos da Adobe Experience Cloud já estão no IMS.

Esta alteração é aplicável a partir do Campaign Classic v7.4.1 (e as [versões compatíveis com a migração do IMS](ac-ims.md#ims-versions) mais recentes) e é **obrigatória** para migrar para o Adobe Campaign v8.

>[!IMPORTANT]
>
>**Impacto do acesso ao Painel de Controle**
>
>Depois de migrar os usuários para o IMS, esteja ciente de que qualquer Perfil de produto no Adobe Admin Console que contenha a palavra &quot;administrador&quot; no nome (como &quot;Administradores&quot;, &quot;administrador&quot;, &quot;administradores&quot;, &quot;administrador de aprovação&quot; etc.) concederá acesso automaticamente ao Painel de controle do Campaign. O Painel de controle do Campaign é uma ferramenta de autoatendimento que permite fazer alterações significativas em instâncias do Campaign.
>
>Analise cuidadosamente suas convenções de nomenclatura de perfil de produto para garantir que somente usuários autorizados tenham acesso ao Painel de controle do Campaign. Saiba mais sobre como gerenciar permissões do Painel de Controle na [documentação do Painel de Controle](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=pt-BR){target="_blank"}.


## Como migrar ambientes híbridos e no local? {#ims-migration-procedure-on-prem}

As principais etapas dessa migração estão listadas abaixo:

1. Atualize seus ambientes para o Campaign v7.4.1 (ou uma [versão compatível com a migração IMS](#ims-versions)).
1. Após a atualização, ainda será possível criar novos usuários com ambos os métodos, como usuário nativo ou com IMS.
1. O administrador interno do Campaign deve configurar o Adobe IMS conforme detalhado em [esta seção](../../integrations/using/configuring-ims.md).
1. Em seguida, adicione emails exclusivos a todos os usuários nativos no console do cliente do Campaign. Esta etapa está detalhada em [esta seção](https://experienceleague.adobe.com/pt-br/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-id){target="_blank"} (documentação do Campaign v8).
1. Crie usuários e perfis de produto no Adobe Admin Console conforme detalhado na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html?lang=pt-BR){target="_blank"}.
1. Habilite a opção **Conectar-se com o Adobe ID** para todos os operadores.
1. Implemente o Adobe IMS para sua conexão conforme detalhado em [esta página](../../integrations/using/implementing-ims.md).

Você também pode migrar seus operadores técnicos para o Adobe Developer Console conforme detalhado em [esta nota técnica](ims-migration.md).

## Perguntas frequentes {#ims-migration-faq}

Para obter respostas a perguntas comuns sobre a migração (criar usuários após a migração, adicionar emails para usuários nativos, fazer logon via IMS, tempo de inatividade, organizações que já usam o IMS, visualizar o tipo de autenticação dos operadores), consulte a [nota técnica do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-faq){target=_blank} (documentação do Campaign v8).

>[!MORELIKETHIS]
>
>* [Migração de usuários técnicos para o console do Adobe Developer](ims-migration.md)
>* [notas de versão do Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [O que é o Adobe Identity Management System (IMS)](https://helpx.adobe.com/br/enterprise/using/identity.html){target="_blank"}
