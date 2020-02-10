---
title: Tradução de uma aplicação web
seo-title: Tradução de uma aplicação web
description: Tradução de uma aplicação web
seo-description: null
page-status-flag: never-activated
uuid: 7b24a872-d3d1-4473-a6f9-96ba2a0eee8b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 328e5b2f-8596-4eda-8ac5-57cb29bfb691
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Tradução de uma aplicação web{#translating-a-web-application}

Você pode traduzir páginas de aplicativos da Web criadas com o editor de conteúdo digital do Adobe Campaign (DCE).

If you select at least one additional language via the **[!UICONTROL Localization]** tab in the **[!UICONTROL Properties]** of a Web application, a new option becomes available when adding an HTML content block in a page edited with DCE.

Essa opção permite indicar se o conteúdo do bloco deve ser traduzido ou não.

Strings to be translated are collected the same way as the other strings of the Web application, via the **[!UICONTROL Translations]** tab of the application. Para obter mais informações, consulte [esta página](../../web/using/translating-a-web-form.md).

Para sinalizar as cadeias de caracteres a ser traduzidas:

1. Abra uma página de conteúdo editada com DCE em uma aplicação web.

   ![](assets/dce_translation_3.png)

1. Selecione um bloco HTML.
1. In the parameters block on the right, the **[!UICONTROL Localization]** option lets you flag the content of the selected block. Por padrão, somente o título da página será traduzido.

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

1. Once you have finished flagging the strings, go back to the Web application and select the **[!UICONTROL Translations]** tab.
1. Select **[!UICONTROL Collect the strings to translate]**. As cadeias de caracteres sinalizadas no DCE são adicionadas às cadeias de caracteres da aplicação web.

   >[!NOTE]
   >
   >Depois que as cadeias de caracteres forem coletadas, elas não serão removidas da lista se você remover o sinalizador de tradução no DCE. Isso permite mantê-las na memória de tradução.

1. Traduza e aprove as cadeias de caracteres.

   You can then preview the translations by selecting the desired language from the **[!UICONTROL Preview]** tab in the Web application.

