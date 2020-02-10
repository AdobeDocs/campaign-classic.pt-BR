---
title: Criação de uma landing page
seo-title: Criação de uma landing page
description: Criação de uma landing page
seo-description: null
page-status-flag: never-activated
uuid: fc0e9749-f44e-4aa0-bdfa-6f44ba570bea
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 5f1e5886-628f-4c9e-80c1-d82feec23e8c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# Criação de uma landing page{#creating-a-landing-page}

## Sobre a criação de páginas iniciais {#about-landing-pages-creation}

Este caso de uso mostra o uso do Editor digital para criar uma Landing page no console do Adobe Campaign.

Antes de começar a configurar a Landing page no Adobe Campaign, verifique se você tem **um ou mais templates** para representar a(s) página(s) HTML.

O principal objetivo desse caso de uso é fazer com que os campos de formulário da Landing page correspondam aos campos internos no Adobe Campaign usando as funções no DCE.

## Criação da landing page {#creating-the-landing-page}

Para criar uma nova aplicação web tipo Landing page, use as seguintes etapas:

1. Vá para a guia **[!UICONTROL Campaigns]** , clique no **[!UICONTROL Web application]** link e, em seguida, clique no **[!UICONTROL Create]** botão.
1. Selecione o **[!UICONTROL New landing page]** modelo e insira um rótulo e clique em **[!UICONTROL Save]**.

   ![](assets/dce_uc1_newlandingpage.png)

1.  Clique na **[!UICONTROL Edit]** guia.
1. Exclua a atividade **Final**.
1. Adicione uma **[!UICONTROL Page]** atividade após a **[!UICONTROL Storage]** atividade.
1. Edite a atividade **Página 2** e desmarque a **[!UICONTROL Activate outbound transitions]** opção na **[!UICONTROL Properties]** guia.

   ![](assets/dce_uc1_transition.png)

1. Salve as alterações.

Você obterá a seguinte sequência:

![](assets/dce_uc1_edition_activity.png)

>[!NOTE]
>
>Para obter mais informações sobre criação de aplicação web, consulte [esta seção](../../web/using/creating-a-new-web-application.md).

## Etapa 1 - Seleção e carregamento de templates {#step-1---selecting-and-loading-templates}

Nesta seção, vamos examinar como **importar conteúdo HTML** para cada página da aplicação Web.

Um template deve conter:

* um arquivo **HTML** (obrigatório)
* um ou mais arquivos **CSS** (opcional)
* uma ou mais **imagens** (opcional)

Para carregar o template na primeira página, siga as etapas abaixo:

1. Open the first **[!UICONTROL Page]** activity of the Web application.
1. Selecione **[!UICONTROL From a file]** para buscar o modelo de conteúdo.

   ![](assets/dce_uc1_selectmodel.png)

1. Selecione o arquivo HTML a ser usado.
1. Clique em **Abrir** para iniciar a importação.

   Durante o carregamento, a lista de arquivos compartilhados é exibida. O sistema de importação verifica se todos os arquivos vinculados ao HTML selecionado estão no lugar (CSS, imagens, etc.).

   Click the **[!UICONTROL Close]** button once the import has finished.

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >Aguarde até obter a seguinte mensagem antes de fechar: **[!UICONTROL The external resources have been successfully published]** .

1.  Clique na **[!UICONTROL Properties]** guia.
1. Digite um **rótulo** para cada página (por exemplo: Página 1= Coleta, Página 2=Obrigado).

   ![](assets/dce_uc1_pagelabel.png)

Aplique essas etapas para cada página inserida na aplicação web.

>[!CAUTION]
>
>**O DCE executa o código JavaScript para a página HTML carregada.** Erros JavaScript no template HTML que podem aparecer na interface do Adobe Campaign. Esses erros não estão relacionados ao editor. Para verificar se não há erros nos arquivos importados, recomenda-se testar em um navegador (Internet Explorer / Firefox / Chrome) antes de importar os arquivos no DCE.

## Etapa 2 - Configuração do conteúdo {#step-2---configuring-the-content}

Nesta seção, vamos ajustar o conteúdo importado e vincular os campos do banco de dados ao formulário da página da Web. A aplicação web criada anteriormente é:

![](assets/dce_uc1_lp_enchainement.png)

### Modificação de conteúdo {#modifying-content}

Vamos começar alterando as cores da página. Para fazer isso:

1. Abra a **[!UICONTROL Collection]** página.
1. Clique no plano de fundo.
1. Clique em **Cor do plano de fundo** no lado direito.
1. Selecione uma nova cor de plano de fundo.
1. Clique em **OK** para confirmar a alteração.

   ![](assets/dce_uc1_changecolor.png)

1. Aplique esses mesmos processos para alterar a cor do botão

   ![](assets/dce_uc1_finalcolor.png)

### Vinculação de campos de formulário {#linking-form-fields}

Vamos vincular os campos na página aos campos no banco de dados, para salvar as informações fornecidas.

1. Selecione um campo de formulário.
1. Edit the **[!UICONTROL Field]** section on right-hand side of the editor.
1. Selecione o campo de banco de dados que deseja vincular ao campo selecionado.

   ![](assets/dce_uc1_mapping.png)

1. Repita esse processo para cada campo na página.

You can make a field mandatory: for example, click the **[!UICONTROL Email]** field then enable the **Mandatory** option.

![](assets/dce_uc1_fieldmandatory.png)

### Criação de um link para a próxima página {#creating-a-link-to-the-next-page}

Esta etapa é obrigatória porque permitirá que o aplicativo da Web determine a sequência das próximas etapas: Salvar os dados coletados no banco de dados e exibir a próxima página (página de **agradecimentos** ).

1. Selecione o **[!UICONTROL Send it!]** botão da **[!UICONTROL Collection]** página.
1. Clique no menu **[!UICONTROL Action]** suspenso.
1. Selecione a **[!UICONTROL Next page]** ação.

   ![](assets/dce_uc1_actionbouton.png)

### Inserção de um campo de personalização {#inserting-a-personalization-field}

Esta etapa permite personalizar a página de agradecimento. Para fazer isso:

1. Abra a **[!UICONTROL Thank you]** página.
1. Coloque o cursor em uma área de texto, onde você deseja inserir o nome do recipient.
1. Selecione **[!UICONTROL Personalization field]** no **[!UICONTROL Insert]** menu da barra de ferramentas.
1. Selecione o nome.

   ![](assets/dce_uc1_persochamp.png)

O campo de personalização tem um plano de fundo amarelo no editor.

![](assets/dce_uc1_edit_champperso.png)

## Etapa 3 - Publicação de conteúdo {#step-3---publishing-content}

O conteúdo é publicado pelo painel da aplicação web. Click the **[!UICONTROL Publish]** button to run it.

![](assets/dce_uc1_pub_dashboard.png)

Durante a publicação, é exibido um log. O sistema de publicação analisa todo o conteúdo encontrado na aplicação Web

![](assets/dce_uc1_pub_dashboard_journal.png)

>[!NOTE]
>
>No log de publicação, os avisos e erros são classificados por atividade.

Agora o formulário está disponível: sua URL está acessível no painel do aplicativo e pode ser enviada para os recipients.
