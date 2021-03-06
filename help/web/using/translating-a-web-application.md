---
product: campaign
title: Traduzir um aplicativo web
description: Traduzir um aplicativo web
feature: Web Apps
exl-id: 82c5c610-8161-4686-aa79-1b690e763765
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: ht
source-wordcount: '363'
ht-degree: 100%

---

# Traduzir um aplicativo web{#translating-a-web-application}

![](../../assets/common.svg)

É possível traduzir páginas de aplicativos Web criados com o editor de conteúdo digital (DCE) do Adobe Campaign.

Se você selecionar pelo menos um idioma adicional pela guia **[!UICONTROL Localization]** nas **[!UICONTROL Properties]** de uma aplicação web, uma nova opção ficará disponível ao adicionar um bloco de conteúdo HTML em uma página editada com o DCE.

Essa opção permite indicar se o conteúdo do bloco deve ser traduzido ou não.

As cadeias de caracteres a serem traduzidas são coletadas da mesma forma que as outras cadeias de caracteres da aplicação web, através da guia **[!UICONTROL Translations]** da aplicação. Para obter mais informações, consulte [esta página](translating-a-web-form.md).

Para sinalizar as cadeias de caracteres a ser traduzidas:

1. Abra uma página de conteúdo editada com DCE em uma aplicação web.

   ![](assets/dce_translation_3.png)

1. Selecione um bloco HTML.
1. No bloco de parâmetros à direita, a opção **[!UICONTROL Localization]** permite sinalizar o conteúdo do bloco selecionado. Por padrão, somente o título da página será traduzido.

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >As cadeias de caracteres não devem exceder 1023 caracteres.

   Há três casos específicos:

   * Quando o bloco selecionado contiver várias cadeias de caracteres/blocos, ele será sinalizado como uma única cadeia de caracteres a ser traduzida. A cadeia de caracteres contém então o código HTML dos elementos dentro desse bloco.
   * Quando você deseja sinalizar um bloco que contém várias cadeias de caracteres e, se pelo menos uma dessas cadeias já estiver sinalizada, um aviso será exibido. Você pode então remover o sinalizador da cadeia de caracteres isolada e adicionar todo o bloco.

      ![](assets/dce_translation_4.png)

   * Quando você deseja remover o sinalizador de uma cadeia de caracteres contida em um bloco que já está sinalizado, não é possível modificar diretamente a opção de conversão de cadeia de caracteres. No entanto, você pode acessar o bloco contendo a cadeia de caracteres para alterá-lo.

      ![](assets/dce_translation_2.png)

1. Depois de concluir a sinalização das cadeias de caracteres, volte para a aplicação web e selecione a guia **[!UICONTROL Translations]**.
1. Selecione **[!UICONTROL Collect the strings to translate]**. As cadeias de caracteres sinalizadas no DCE são adicionadas às cadeias de caracteres da aplicação web.

   >[!NOTE]
   >
   >Depois que as cadeias de caracteres forem coletadas, elas não serão removidas da lista se você remover o sinalizador de tradução no DCE. Isso permite mantê-las na memória de tradução.

1. Traduza e aprove as cadeias de caracteres.

   Você pode pré-visualizar as traduções selecionando o idioma desejado na guia **[!UICONTROL Preview]** na aplicação web.
