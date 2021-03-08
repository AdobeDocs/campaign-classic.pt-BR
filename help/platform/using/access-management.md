---
solution: Campaign Classic
product: campaign
title: Introdução a permissões
description: Saiba como conceder acesso aos recursos do Campaign
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: f7e4f129a96e80ec169428057f661165d8b967c9
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 66%

---


# Comece com permissões{#access-management}

O Adobe Campaign permite definir e gerenciar os direitos atribuídos aos diversos operadores. Veja um conjunto de direitos e restrições que autorizam ou negam:

* Acesso a certas funcionalidades (por meio dos direitos nomeados),
* Acesso a certos registros,
* Criação, modificação e/ou exclusão de registros (ações, contatos, campanhas, grupos, etc.).

As permissões se aplicam a perfis ou grupos de operadores.

Os perfis são preenchidos por parâmetros de segurança vinculados ao modo de conexão do operador para o Adobe Campaign. Para obter mais informações sobre zonas de segurança em [esta página](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Há dois tipos de permissões que você pode conceder a um usuário:

* Você pode definir grupos de operadores para atribuir direitos e, em seguida, associar os operadores a um ou mais grupos. Isso permite que você reutilize os direitos e torne os perfis de operadores mais consistentes. Também facilita o gerenciamento e a manutenção de perfis. A criação e o gerenciamento de grupos são apresentados em [this section](access-management-groups.md).

* Você pode atribuir direitos nomeados diretamente aos usuários, em alguns casos para sobrecarregar os direitos alocados por meio de grupos. Esses direitos são apresentados em [this page](access-management-named-rights.md).

>[!NOTE]
>
>Antes de começar a definir as permissões, a Adobe recomenda que você leia a [Lista de verificação de configuração de segurança](https://helpx.adobe.com/br/campaign/kb/acc-security.html).

Saiba como conceder acesso e configurar permissões nestas seções:

* [Criar operadores](access-management-operators.md)

* [Definir grupos](access-management-groups.md)

* [Adicionar direitos nomeados](access-management-named-rights.md)

* [Gerenciar o acesso à pasta do Campaign](access-management-folders.md)

* [Matriz de direitos de acesso](access-management-named-rights.md#access-rights-matrix)


Consulte também:

* [Gerenciar permissões para fluxos de trabalho](../../workflow/using/managing-rights.md)
* [Gerenciar permissões para marketing distribuído](../../campaign/using/about-distributed-marketing.md#operators-and-entities)
* [Gerenciar permissões do módulo de interação](../../interaction/using/operator-profiles.md)
* [Filtrar o acesso a schemas](../../configuration/using/filtering-schemas.md)
* [Restrição da exibição de PI](../../configuration/using/restricting-pii-view.md)
