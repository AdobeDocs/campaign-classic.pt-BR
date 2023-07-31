---
product: campaign
title: Gerenciamento de perfis
description: Gerenciamento de perfis
feature: Profiles
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '236'
ht-degree: 100%

---

# Gerenciar perfis{#managing-profiles}



## Árvore do destinatário {#recipient-tree}

Para acessar as funcionalidades avançadas de gerenciamento de destinatários, é necessário editar a árvore do Adobe Campaign. Para fazer isso, clique no botão **[!UICONTROL Explorer]** na barra de ferramentas.

Por padrão, os destinatários são armazenados no nó **[!UICONTROL Profiles and targets]** da árvore do Adobe Campaign. No mesmo nó, é possível criar uma ou mais pastas e subpastas para armazenar perfis de destinatários.

Cada nó coincide com uma pasta. Os dados de cada pasta devem ser considerados particionados entre si. Isso significa que o gerenciamento de pares é mais complicado para várias pastas de destinatários.

>[!NOTE]
>
>Para exibir a lista de todos os destinatários no banco de dados, crie uma visualização. Saiba mais em [Pastas e exibições](../../platform/using/access-management-folders.md).

## Mover destinatários {#moving-recipients}

É possível selecionar um ou mais destinatários, arrastá-los da lista de destinatários e soltá-los na pasta desejada. Uma mensagem de aviso solicita que você confirme esta ação.

## Copiar um destinatário {#copying-a-recipient}

Para copiar um destinatário na mesma pasta, clique com o botão direito do mouse no destinatário desejado e selecione **[!UICONTROL Copy]**.

## Excluir destinatários {#deleting-recipients}

Para excluir recipients, mova-os para uma pasta específica e, em seguida, limpe o conteúdo dessa pasta. É **altamente recomendável não usar** a opção **[!UICONTROL Delete]** neste caso.

Para limpar uma pasta, use o menu **[!UICONTROL Actions > Purge folder]**, acessível clicando com o botão direito do mouse na pasta desejada.

![](assets/s_ncs_user_purge_folder.png)

Clique em **[!UICONTROL Start]** para iniciar a operação. A seção do meio da janela exibe o status do progresso, conforme mostrado abaixo:

![](assets/s_ncs_user_purge_folder_start.png)
