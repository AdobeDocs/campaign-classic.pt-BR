---
product: campaign
title: Introdução às permissões
description: Saiba como conceder acesso aos recursos do Campaign
badge: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: a5bbd2e6c102a8afa4cd5931b77b0c83705a7bfa
workflow-type: ht
source-wordcount: '256'
ht-degree: 100%

---

# Introdução às permissões{#access-management}


>[!CAUTION]
>
>A partir do Campaign Classic v7.3.1, todos os operadores deverão usar o [Sistema de gerenciamento de identidades (IMS)](https://helpx.adobe.com/br/enterprise/using/identity.html){target="_blank"} para se conectar ao Campaign.
>
>Como parte do trabalho para reforçar o processo de segurança e autenticação, o Adobe Campaign recomenda enfaticamente migrar todos os modos de autenticação de operadores da autenticação nativa de logon/senha para o Adobe Identity Management System (IMS). Saiba como migrar operadores [nesta página](../../technotes/using/migrate-users-to-ims.md).
> 
>Após essa migração, observe que a seção a seguir não se aplica mais.  Aprenda como configurar permissões com o Adobe IMS na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=pt-BR){target="_blank"}.


O Adobe Campaign permite definir e gerenciar os direitos atribuídos aos diversos operadores. Veja um conjunto de direitos e restrições que autorizam ou negam:

* Acesso a certas funcionalidades (por meio dos direitos nomeados),
* Acesso a certos registros,
* Criação, modificação e/ou exclusão de registros (ações, contatos, campanhas, grupos, etc.).

>[!BEGINTABS]

>[!TAB Documentação das permissões]

Para saber mais sobre **permissões no Adobe Campaign**, consulte a **[documentação do Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=pt-BR#_blank){target=_blank}**.

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=pt-BR#_blank){target=_blank}


>[!TAB Gerenciar permissões em pastas]

Para saber como definir **permissões em pastas**, consulte a **[documentação do Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}**.

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}


>[!TAB Autenticação nativa]

A autenticação nativa com logon/senha ainda está disponível no Campaign v7, mas para reforçar a segurança e o processo de autenticação, o Adobe Campaign recomenda [migrar o modo de autenticação do usuário final](../../technotes/using/ac-ims.md) da autenticação nativa para o Adobe Identity Management System (IMS). Observe que, no Campaign v8, a conexão com autenticação nativa não é permitida.

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](../../technotes/using/ac-ims.md)


>[!ENDTABS]



<!--
The permissions apply to operator profiles or operator groups.

They are completed by safety parameters linked to the operator's connection mode to Adobe Campaign. For more about security zones in [this page](../../installation/using/security-zones.md).

There are two types of permissions you can grant to a user:

* You can define groups of operators to which you attribute rights, then associate the operators with one or more groups. This enables you to reuse rights and make operator profiles more consistent. It also facilitates the management and maintenance of profiles. Group creation and management are presented in [this section](access-management-groups.md).

* You can attribute named rights directly to users, in some cases to overload the rights allocated via groups. These rights are presented in [this page](access-management-named-rights.md).

>[!NOTE]
>
> * Before starting defining permissions, Adobe recommends you to read the [Security configuration checklist](https://helpx.adobe.com/br/campaign/kb/acc-security.html).
> * To learn more about permissions, please refer to the detailed explanation on the [Campaign v8 documentation](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

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