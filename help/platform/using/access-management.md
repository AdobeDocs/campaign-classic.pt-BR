---
solution: Campaign Classic
product: campaign
title: Introdução a permissões
description: Saiba como conceder acesso aos recursos do Campaign
feature: Gerenciamento de acesso
role: Business Practitioner, Administrator
level: Beginner
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
translation-type: tm+mt
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 99%

---

# Introdução a permissões{#access-management}

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
>Antes de começar a definir as permissões, a Adobe recomenda que você leia a [Lista de verificação de configuração de segurança](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/security-privacy/get-started-security-privacy.html?lang=pt-BR#installing-campaign-classic).

Saiba como conceder acesso e configurar permissões nestas seções:

* [Criar operadores](access-management-operators.md)

* [Definir grupos](access-management-groups.md)

* [Adicionar direitos nomeados](access-management-named-rights.md)

* [Gerenciar o acesso à pasta do Campaign](access-management-folders.md)

* [Acessar matriz de direitos](access-management-named-rights.md#access-rights-matrix)


Consulte também:

* [Gerenciar permissões para workflows](../../workflow/using/managing-rights.md)
* [Gerenciar permissões para marketing distribuído](../../campaign/using/about-distributed-marketing.md#operators-and-entities)
* [Gerenciar permissões do módulo de interação](../../interaction/using/operator-profiles.md)
* [Filtrar o acesso a esquemas](../../configuration/using/filtering-schemas.md)
* [Restrição da visualização de PI](../../configuration/using/restricting-pii-view.md)
