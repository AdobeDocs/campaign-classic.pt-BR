---
product: campaign
title: Traduzir um aplicativo web
description: Traduzir um aplicativo web
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Web Apps
exl-id: 82c5c610-8161-4686-aa79-1b690e763765
TQID: https://experienceleague.adobe.com/AVV-TybR3s6d68N7DS0TSKBN46-etor1Ezhlaah-MJs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
subfeature_v2:
  - id: f391046b-0cf3-4e76-bd3b-97fe06654506
  - id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
  - id: d7be2b01-dc9c-40f7-aace-a151707504ed
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 373
ht-degree: 100%

---

# Traduzir um aplicativo web{#translating-a-web-application}



É possível traduzir páginas de aplicativos Web criados com o editor de conteúdo digital (DCE) do Adobe Campaign.

Se você selecionar pelo menos um idioma adicional pela guia **[!UICONTROL Localization]** nas **[!UICONTROL Properties]** de uma aplicação web, uma nova opção ficará disponível ao adicionar um bloco de conteúdo HTML em uma página editada com o DCE.

Essa opção permite indicar se o conteúdo do bloco deve ser traduzido ou não.

As strings a serem traduzidas são coletadas da mesma forma que as outras strings da aplicação web, através da guia **[!UICONTROL Translations]** da aplicação. Para obter mais informações, consulte [esta página](translating-a-web-form.md).

Para sinalizar as strings a ser traduzidas:

1. Abra uma página de conteúdo editada com DCE em uma aplicação web.

   ![](assets/dce_translation_3.png)

1. Selecione um bloco HTML.
1. No bloco de parâmetros à direita, a opção **[!UICONTROL Localization]** permite sinalizar o conteúdo do bloco selecionado. Por padrão, somente o título da página será traduzido.

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >As strings não devem exceder 1023 caracteres.

   Há três casos específicos:

   * Quando o bloco selecionado contiver várias strings/blocos, ele será sinalizado como uma única string a ser traduzida. A string contém então o código HTML dos elementos dentro desse bloco.
   * Quando você deseja sinalizar um bloco que contém várias strings e, se pelo menos uma dessas cadeias já estiver sinalizada, um aviso será exibido. Você pode então remover o sinalizador da string isolada e adicionar todo o bloco.

     ![](assets/dce_translation_4.png)

   * Quando você deseja remover o sinalizador de uma string contida em um bloco que já está sinalizado, não é possível modificar diretamente a opção de conversão de string. No entanto, você pode acessar o bloco contendo a string para alterá-lo.

     ![](assets/dce_translation_2.png)

1. Depois de concluir a sinalização das strings, volte para a aplicação web e selecione a guia **[!UICONTROL Translations]**.
1. Selecione **[!UICONTROL Collect the strings to translate]**. As strings sinalizadas no DCE são adicionadas às strings da aplicação web.

   >[!NOTE]
   >
   >Depois que as strings forem coletadas, elas não serão removidas da lista se você remover o sinalizador de tradução no DCE. Isso permite mantê-las na memória de tradução.

1. Traduza e aprove as strings.

   Você pode pré-visualizar as traduções selecionando o idioma desejado na guia **[!UICONTROL Preview]** na aplicação web.
