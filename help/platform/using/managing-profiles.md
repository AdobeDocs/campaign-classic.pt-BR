---
solution: Campaign Classic
product: campaign
title: Gerenciamento de perfis
description: Gerenciamento de perfis
audience: platform
content-type: reference
topic-tags: profile-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 100%

---


# Gerenciamento de perfis{#managing-profiles}

## Árvore do destinatário {#recipient-tree}

Para acessar as funcionalidades avançadas de gerenciamento de destinatários, é necessário editar a árvore do Adobe Campaign. Para fazer isso, clique no botão **[!UICONTROL Explorer]** na barra de ferramentas.

Por padrão, os destinatários são armazenados no nó **[!UICONTROL Profiles and targets]** da árvore do Adobe Campaign. No mesmo nó, é possível criar uma ou mais pastas e subpastas para armazenar perfis de destinatários.

Cada nó coincide com uma pasta. Os dados de cada pasta devem ser considerados particionados entre si. Isso significa que o gerenciamento de pares é mais complicado para várias pastas de destinatários.

>[!NOTE]
>
>Para exibir a lista de todos os destinatários no banco de dados, crie uma visualização. Consulte [Pastas e exibições](../../platform/using/access-management.md#folders-and-views).

## Movimentação de destinatários {#moving-recipients}

É possível selecionar um ou mais destinatários, arrastá-los da lista de destinatários e soltá-los na pasta desejada. Uma mensagem de aviso solicita que você confirme esta ação.

## Como copiar um destinatário {#copying-a-recipient}

Para copiar um destinatário na mesma pasta, clique com o botão direito do mouse no destinatário desejado e selecione **[!UICONTROL Copy]**.

## Como excluir destinatários {#deleting-recipients}

Para excluir destinatários, mova-os para uma pasta específica e, em seguida, limpe o conteúdo dessa pasta. É **altamente recomendável não usar** a opção **[!UICONTROL Delete]** neste caso.

Para limpar uma pasta, use o menu **[!UICONTROL Actions > Purge folder]**, acessível clicando com o botão direito do mouse na pasta desejada.

![](assets/s_ncs_user_purge_folder.png)

Clique em **[!UICONTROL Start]** para iniciar a operação. A seção do meio da janela exibe o status do progresso, conforme mostrado abaixo:

![](assets/s_ncs_user_purge_folder_start.png)

