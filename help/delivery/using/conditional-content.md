---
product: campaign
title: Conteúdo condicional
description: Saiba como adicionar conteúdo condicional
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Personalization, Multilingual Messages
role: User
hide: true
exl-id: 12595ee4-6a52-4e06-b80d-85fe633a5a11
TQID: https://experienceleague.adobe.com/S8pQz1eOVkbkBKFzhPwzEfj50cPnBBOeYNGFg-R6EZ4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 502
ht-degree: 100%

---

# Conteúdo condicional{#conditional-content}

Ao configurar campos de conteúdo condicional, você pode criar personalização dinâmica com base no perfil do destinatário, por exemplo. Blocos de texto e/ou imagens são substituídos quando uma determinada condição é atendida.

![](assets/do-not-localize/how-to-video.png) [Conheça este recurso no vídeo](#conditionnal-content-video)


## Usar condições em um email {#using-conditions-in-an-email}

No exemplo abaixo, você aprenderá a criar uma mensagem, personalizada dinamicamente no gênero e interesses do destinatário.

* Exibição de “Sr.” ou “Sra.” de acordo com o valor do campo **[!UICONTROL Gender]** (M ou F) na fonte de dados,
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

   * Selecione o primeiro elemento da expressão, **`<field>`**, (por padrão, esse elemento é realçado durante a inserção da expressão **if** ) e clique no ícone de personalização para substitui-lo pelo campo de teste.

     ![](assets/s_ncs_user_conditional_content03.png)

   * Substitua **`<value>`** pelo valor do campo para o qual a condição será atendida. Esse valor deve estar entre aspas.
   * Especifique o conteúdo a ser inserido quando a condição for atendida. Isso pode consistir em um texto, uma imagem, um formulário, um link de hipertexto etc.

     ![](assets/s_ncs_user_conditional_content04.png)

1. Clique na guia **[!UICONTROL Preview]** para exibir o conteúdo da mensagem de acordo com o destinatário da entrega:

   * Selecionando um destinatário para o qual a condição é verdadeira:

     ![](assets/s_ncs_user_conditional_content05.png)

   * Selecionando um destinatário para o qual a condição não é verdadeira:

     ![](assets/s_ncs_user_conditional_content06.png)

Você pode adicionar outros casos e definir outro conteúdo de acordo com os valores de um ou mais campos. Para fazer isso, use **[!UICONTROL Conditional content > Else]** e **[!UICONTROL Conditional content > Else if]**. Essas expressões são configuradas da mesma maneira que a expressão **se**.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>Para respeitar a sintaxe do JavaScript, os caracteres **%> &lt;%** devem ser excluídos após adicionar as condições **Senão** e **Senão se**.

Clique em **[!UICONTROL Preview]** e selecione um destinatário para exibir o conteúdo condicional.

![](assets/s_ncs_user_conditional_content08.png)

## Criar email multilíngue {#creating-multilingual-email}

Você verá no exemplo abaixo como criar um email multilíngue. O conteúdo será exibido em um idioma ou em outro, dependendo da preferência de idioma do destinatário.

1. Crie um email e selecione a população de destino. Neste exemplo, a condição para exibir uma versão ou outra será baseada no valor **Idioma** do perfil do destinatário. Neste exemplo, esses valores são definidos como **EN**, **FR**, **ES**.
1. No conteúdo HTML de email, clique na guia **[!UICONTROL Source]** e cole o seguinte código:

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

1. Teste o conteúdo do email na guia **[!UICONTROL Preview]** selecionando os destinatários com as diferentes preferências de idioma.

   >[!NOTE]
   >
   >Como nenhuma versão alternativa foi definida no conteúdo do email, filtre a população de destino antes de enviar o email.

## Tutorial em vídeo {#conditionnal-content-video}

Saiba como adicionar conteúdo condicional a uma entrega no exemplo de um informativo multilíngue.

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)

Vídeos extras sobre procedimentos do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
