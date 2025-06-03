---
product: campaign
title: Introdução a permissões
description: Saiba como conceder acesso aos recursos do Campaign
badge: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 85%

---

# Introdução a permissões{#access-management}


>[!CAUTION]
>
>A partir do Campaign Classic v7.3.1, todos os operadores devem usar o [Adobe Identity Management System (IMS)](https://helpx.adobe.com/br/enterprise/using/identity.html){target="_blank"} para se conectarem ao Campaign.
>
>Como parte do trabalho para reforçar o processo de segurança e autenticação, o Adobe Campaign recomenda enfaticamente migrar todos os modos de autenticação de operadores da autenticação nativa de logon/senha para o Adobe Identity Management System (IMS). Saiba como migrar operadores [nesta página](../../technotes/using/migrate-users-to-ims.md).
> 
>Após essa migração, observe que a seção a seguir não se aplica mais.  Saiba como configurar permissões com o Adobe IMS na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=pt-BR){target="_blank"}.


O Adobe Campaign permite definir e gerenciar os direitos atribuídos aos diversos operadores. Veja um conjunto de direitos e restrições que autorizam ou negam:

* Acesso a certas funcionalidades (por meio dos direitos nomeados),
* Acesso a certos registros,
* Criação, modificação e/ou exclusão de registros (ações, contatos, campanhas, grupos, etc.).

As permissões se aplicam a perfis ou grupos de operadores.

Os perfis são preenchidos por parâmetros de segurança vinculados ao modo de conexão do operador para o Adobe Campaign. Para obter mais informações sobre zonas de segurança consulte [esta página](../../installation/using/security-zones.md).

Há dois tipos de permissões que você pode conceder a um usuário:

* Você pode definir grupos de operadores para atribuir direitos e, em seguida, associar os operadores a um ou mais grupos. Isso permite que você reutilize os direitos e torne os perfis de operadores mais consistentes. Também facilita o gerenciamento e a manutenção de perfis. A criação e o gerenciamento de grupos são apresentados [nesta seção](access-management-groups.md).

* Você pode atribuir direitos nomeados diretamente aos usuários, em alguns casos para aumentar os direitos alocados por meio de grupos. Esses direitos são apresentados [nesta página](access-management-named-rights.md).

>[!NOTE]
>
> * Antes de começar a definir as permissões, a Adobe recomenda que você leia a [Lista de verificação de configuração de segurança](https://helpx.adobe.com/br/campaign/kb/acc-security.html).
> * Para saber mais sobre permissões, consulte a explicação detalhada na [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

<!--

Learn how to grant access and set up permissions in these sections:

* [Create operators](access-management-operators.md)

* [Define groups](access-management-groups.md)

* [Add Named rights](access-management-named-rights.md)

* [Manage Campaign folder access](access-management-folders.md)

* [Access rights matrix](access-management-named-rights.md#access-rights-matrix)


See also:

* [Manage permissions for workflows](../../workflow/using/managing-rights.md)
* [Manage permissions for distributed marketing](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Manage permissions for the interaction module](../../interaction/using/operator-profiles.md)
* [Filter access to schemas](../../configuration/using/filtering-schemas.md)
* [Restricting PI view](../../configuration/using/restricting-pii-view.md)
-->