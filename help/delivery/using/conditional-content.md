---
title: Conteúdo condicional
seo-title: Conteúdo condicional
description: Conteúdo condicional
seo-description: null
page-status-flag: never-activated
uuid: d1c38263-a163-448c-8822-8b3e776e45cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 167cc61a-fbc7-48cb-89ff-fbdbf9321c01
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# Conteúdo condicional{#conditional-content}

Ao configurar campos de conteúdo condicional, você pode criar personalização dinâmica com base no perfil do recipient, por exemplo. Blocos de texto e/ou imagens são substituídos quando uma determinada condição é atendida.

## Uso das condições em um email {#using-conditions-in-an-email}

No exemplo abaixo, você aprenderá a criar uma mensagem, personalizada dinamicamente no sexo e interesses do recipient.

* Exibição mostrando &quot;Sr.&quot; ou &quot;Sra.&quot; de acordo com o valor do **[!UICONTROL Gender]** campo (M ou F) da fonte de dados,
* Assembly personalizado de um boletim informativo ou ofertas promocionais de acordo com os interesses indicados ou detectados:

   * Interesse 1 -- > Bloco 1
   * Interesse 2 -- > Bloco 2
   * Interesse 3 -- > Bloco 3
   * Interesse 4 -- > Bloco 4

Para criar conteúdo condicional de acordo com o valor de um campo, siga as seguintes etapas:

1. Clique no ícone de personalização e selecione **[!UICONTROL Conditional content > If]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   Os elementos de personalização são inseridos no corpo da mensagem. Devem ser configurados agora.

1. Em seguida, preencha os parâmetros da expressão **Se**.

   Para fazer isso:

   * Select the first element of the expression, **`<field>`**, (by default, this element is highlighted during insertion of the **if** expression) and click the personalization icon to replace it with the test field.

      ![](assets/s_ncs_user_conditional_content03.png)

   * Replace **`<value>`** with the value of the field for which the condition will be satisfied. Esse valor deve estar entre aspas.
   * Especifique o conteúdo a ser inserido quando a condição for atendida. Isso pode consistir em um texto, uma imagem, um formulário, um link de hipertexto etc.

      ![](assets/s_ncs_user_conditional_content04.png)

1. Click the **[!UICONTROL Preview]** tab to view the content of the message according to the delivery recipient:

   * Selecionando um recipient para o qual a condição é verdadeira:

      ![](assets/s_ncs_user_conditional_content05.png)

   * Selecionando um recipient para o qual a condição não é verdadeira:

      ![](assets/s_ncs_user_conditional_content06.png)

Você pode adicionar outros casos e definir outro conteúdo de acordo com os valores de um ou mais campos. Para fazer isso, use **[!UICONTROL Conditional content > Else]** e **[!UICONTROL Conditional content > Else if]**. Essas expressões são configuradas da mesma maneira que a expressão **se**.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>Para respeitar a sintaxe do JavaScript, os caracteres **%> &lt;%** devem ser excluídos após adicionar as condições **Senão** e **Senão se**.

Click **[!UICONTROL Preview]** and select a recipient to view the conditional content.

![](assets/s_ncs_user_conditional_content08.png)

## Criação de email multilíngue {#creating-multilingual-email}

Você verá no exemplo abaixo como criar um email multilíngue. O conteúdo será exibido em um idioma ou no outro, dependendo do idioma preferencial do destinatário.

1. Crie um email e selecione o público alvo. Neste exemplo, a condição para exibir uma versão ou outra será baseada no valor **Idioma** do perfil do recipient. Neste exemplo, esses valores são definidos como **EN**, **FR**, **ES**.
1. In the email HTML content, click the **[!UICONTROL Source]** tab and paste the following code:

   ```
   <% if (language == "EN" ) { %>
   <DIV id=en-version>Hello <%= recipient.firstName %>,</DIV>
   <DIV>Discover your new offers!</DIV>
   <DIV><a href="https://www.adobe.com/products/en">www.adobe.com/products/en</A></FONT></DIV><%
    } %>
   <% if (language == "FR" ) { %>
   <DIV id=fr-version>Bonjour <%= recipient.firstName %>,</DIV>
   <DIV>Découvrez nos nouvelles offres !</DIV>
   <DIV><a href="https://www.adobe.com/products/fr">www.adobe.com/products/fr</A></DIV><%
    } %>
    <% if (language == "ES" ) { %>
   <DIV id=es-version><FONT face=Arial>
   <DIV>Olà <%= recipient.firstName %>,</DIV>
   <DIV>Descubra nuestros nuevas ofertas !</DIV>
   <DIV><a href="https://www.adobe.com/products/es">www.adobe.com/products/es</A></DIV>
   <% } %>
   ```

1. Test email content in the **[!UICONTROL Preview]** tab by selecting recipients with different preferred languages.

   >[!NOTE]
   >
   >Como nenhuma versão alternativa foi definida no conteúdo do email, certifique-se de filtrar o público alvo antes de enviar o email.
