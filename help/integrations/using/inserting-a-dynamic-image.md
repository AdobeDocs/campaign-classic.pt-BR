---
product: campaign
title: Inserir uma imagem dinâmica
description: Inserir uma imagem dinâmica
feature: Target Integration
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 6177f57b-534c-4d86-8f73-d96980c48a77
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 100%

---

# Inserir conteúdo dinâmico do Target {#inserting-a-dynamic-image}



Nesta página, aprenda a integrar uma oferta dinâmica do Adobe Target em um email no Adobe Campaign.

O objetivo é criar um delivery com um bloco de imagem que muda dinamicamente de acordo com o país do recipient: os dados são enviados a cada solicitação de mbox e dependem do endereço IP do recipient.

Nesta mensagem, as imagens podem variar dinamicamente de acordo com as seguintes experiências do usuário:

* O e-mail é aberto na França.
* O e-mail é aberto nos Estados Unidos.
* Se nenhuma dessas condições se aplicar, uma imagem padrão será exibida.

![](assets/target_4.png)

Para fazer isso, siga as etapas abaixo:

1. [Inserir a oferta dinâmica em um email](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [Criar ofertas de redirecionamento](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [Criar públicos](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [Criar uma atividade de direcionamento de experiência](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [Pré-visualizar e enviar o email](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## Inserir a oferta dinâmica em um email {#inserting-dynamic-offer}

No Adobe Campaign, depois de definir o destino e o conteúdo do seu e-mail, você pode inserir uma imagem dinâmica do Target.

Para fazer isso, especifique o URL da imagem padrão, o nome do local e os campos que você deseja transferir para o Target.

No Adobe Campaign, há duas maneiras de inserir uma imagem dinâmica do Target em um email:

* Se o editor de conteúdo digital estiver em uso, escolha uma imagem existente e selecione **[!UICONTROL Insert]** > **[!UICONTROL Dynamic image served by Adobe Target]** na barra de ferramentas.

  ![](assets/target_5.png)

* Se o editor padrão estiver em uso, coloque o cursor onde deseja inserir a imagem e selecione **[!UICONTROL Include]** > **[!UICONTROL Dynamic image served by Adobe Target...]** no menu suspenso de personalização.

  ![](assets/target_12.png)

### Definir os parâmetros de imagem {#defining-image-parameters}

* O URL de **[!UICONTROL Default image]**: a imagem que será exibida quando nenhuma das condições for satisfeita. Você também pode selecionar uma imagem da biblioteca de recursos.
* O **[!UICONTROL Target location]**: digite um nome para a localização da oferta dinâmica. Você terá que selecionar este local na atividade do público-alvo.
* O **[!UICONTROL Landing Page]**: se desejar que a imagem padrão seja redirecionada para uma landing page padrão. Esse URL é somente para os casos que a imagem padrão é exibida no email final e é opcional.
* O **[!UICONTROL Additional decision parameters]**: especifique o mapeamento entre os campos definidos nos segmentos do Adobe Target e os campos do Adobe Campaign. Os campos do Adobe Campaign usados devem ter sido especificados no rawbox. No nosso exemplo, adicionamos o campo País.

Se você usar permissões do Enterprise em suas configurações no Adobe Target, adicione a propriedade correspondente nesse campo. Saiba mais sobre as permissões do Target Enterprise [nesta página](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html?lang=pt-BR).

![](assets/target_13.png)

## Criar ofertas de redirecionamento {#create-redirect-offers}

No Target , é possível criar diferentes versões da oferta. Dependendo da experiência de cada usuário, uma oferta de redirecionamento pode ser criada e você pode especificar a imagem que será exibida.

Em nosso caso, precisamos de duas ofertas de redirecionamento, a terceira (a padrão) deve ser definida no Adobe Campaign.

1. Para criar uma nova oferta de redirecionamento no Target Standard, na guia **[!UICONTROL Content]**, clique em **[!UICONTROL Code offers]**.

1. Clique em **[!UICONTROL Create]** e em **[!UICONTROL Redirect Offer]**.

   ![](assets/target_9.png)

1. Insira um nome para a oferta e o URL da imagem.

   ![](assets/target_6.png)

1. Siga o mesmo procedimento para a oferta de redirecionamento restante. Para obter mais informações, consulte esta [página](https://experienceleague.adobe.com/docs/target/using/experiences/offers/offer-redirect.html?lang=pt-BR).

## Criar públicos {#audiences-target}

No Target , é necessário criar os dois públicos nos quais as pessoas que visitam a oferta são categorizadas para os diferentes conteúdos a serem entregues. Para cada público, adicione uma regra para definir quem poderá ver a oferta.

1. Para criar um novo público no Target, na guia **[!UICONTROL Audiences]**, clique em **[!UICONTROL Create Audience]**.

   ![](assets/audiences_1.png)

1. Adicione um nome ao público.

   ![](assets/audiences_2.png)

1. Clique **[!UICONTROL Add a rule]** e selecione uma categoria. A regra usa critérios específicos para direcionar os visitantes. É possível refinar as regras adicionando condições ou criando novas regras em outras categorias.

1. Siga o mesmo procedimento para os públicos restantes.

## Criar uma atividade de direcionamento de experiência {#creating-targeting-activity}

No Target, é necessário criar uma atividade de direcionamento de experiência, definir as diferentes experiências e associá-las às ofertas correspondentes.

### Definir o público {#defining-the-audience}

1. Para criar uma atividade de Direcionamento de Experiência, na guia **[!UICONTROL Activities]**, clique em **[!UICONTROL Create Activity]** e em **[!UICONTROL Experience Targeting]**

   ![](assets/target_10.png)

1. Selecione **[!UICONTROL Form]** como **[!UICONTROL Experience Composer]**.

1. Escolha um público ao clicar no botão **[!UICONTROL Change audience]**.

   ![](assets/target_10_2.png)

1. Selecione o público criado nas etapas anteriores.

   ![](assets/target_10_3.png)

1. Crie outra experiência ao clicar em **[!UICONTROL Add Experience Targeting]**.

### Definir a localização e o conteúdo {#defining-location-content}

Adicione um conteúdo para cada público:

1. Selecione o nome do local escolhido ao inserir a oferta dinâmica no Adobe Campaign.

   ![](assets/target_15.png)

1. Clique no botão suspenso e selecione **[!UICONTROL Change Redirect Offer]**.

   ![](assets/target_content.png)

1. Selecione a oferta de redirecionamento que você criou anteriormente.

   ![](assets/target_content_2.png)

1. Siga o mesmo procedimento para a segunda experiência.

### Definir a atividade {#defining-activity}

A janela **[!UICONTROL Target]** resume a atividade. Se necessário, você pode adicionar outras experiências.

![](assets/target_experience.png)

A janela **[!UICONTROL Goal & Settings]** permite a personalização da atividade ao definir uma prioridade, um objetivo ou uma duração.

A seção **[!UICONTROL Reporting Settings]** permite selecionar uma ação e editar os parâmetros que devem determinar quando sua meta será atingida.

![](assets/target_experience_2.png)

## Pré-visualizar e enviar o email {#preview-send-email}

No Adobe Campaign, agora você pode visualizar seu e-mail e testar sua renderização em diferentes recipients. Você notará que a imagem muda de acordo com as diferentes experiências criadas. Para saber mais sobre a criação de email, consulte esta [página](../../delivery/using/defining-the-email-content.md).

Agora você está pronto para enviar seu email, incluindo uma oferta dinâmica do Target.

![](assets/target_20.png)
