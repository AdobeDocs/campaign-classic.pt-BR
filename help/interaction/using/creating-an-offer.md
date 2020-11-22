---
solution: Campaign Classic
product: campaign
title: Criação de uma oferta
description: Criação de uma oferta
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 100%

---


# Criação de uma oferta{#creating-an-offer}

## Criação da oferta {#creating-the-offer}

Para criar uma oferta, aplique as seguintes etapas:

1. Vá para o universo **[!UICONTROL Campaigns]** e clique no link **[!UICONTROL Offers]**.

   ![](assets/offer_create_001.png)

1. Clique no botão **[!UICONTROL Create]**.

   ![](assets/offer_create_005.png)

1. Altere o rótulo e selecione a categoria à qual a oferta deve pertencer.

   ![](assets/offer_create_002.png)

1. Clique em **[!UICONTROL Save]** para criar a oferta.

   ![](assets/offer_create_003.png)

   A oferta está disponível na plataforma e seu conteúdo pode ser configurado.

   ![](assets/offer_create_004.png)

## Configuração da qualificação para a oferta {#configuring-offer-eligibility}

Na guia **[!UICONTROL Eligibility]**, defina o período em que a oferta será válida e poderá ser apresentada, os filtros a serem aplicados no target e o peso da oferta.

### Definição do período de qualificação de uma oferta {#defining-the-eligibility-period-of-an-offer}

Para definir o período de qualificação da oferta, use as listas suspensas e selecione uma data inicial e final no calendário.

![](assets/offer_eligibility_create_002.png)

Fora dessas datas, a oferta não será selecionada pelo mecanismo do Interaction. Se também tiver configurado datas de qualificação para a categoria de oferta, o período mais restritivo será aplicado.

### Filtros no target {#filters-on-the-target}

É possível aplicar filtros ao target da oferta.

Para fazer isso, clique no link **[!UICONTROL Edit query]** e selecione o filtro que deseja aplicar. (Consulte [esta seção](../../platform/using/steps-to-create-a-query.md#step-4---filter-data)).

![](assets/offer_eligibility_create_003.png)

Se os filtros predefinidos já tiverem sido criados, é possível selecioná-los na lista de filtros de usuário. Para obter mais informações, consulte [Criação de filtros predefinidos](../../interaction/using/creating-predefined-filters.md).

![](assets/offer_eligibility_create_004.png)

### Peso da oferta {#offer-weight}

Para permitir que o mecanismo decida entre várias ofertas que o target está qualificado, é necessário atribuir um ou mais pesos à oferta. Também é possível aplicar filtros ao target se necessário ou restringir o espaço de oferta ao qual o peso será aplicado. Uma oferta com um peso mais significativo será preferível sobre uma oferta com menos peso.

É possível configurar vários pesos para a mesma oferta, por exemplo, para distinguir sub-períodos, alvos específicos ou até mesmo um espaço de oferta.

Por exemplo, uma oferta pode ter um peso de A para contatos com idade entre 18 e 25 e um peso de B para contatos acima desse intervalo. Se uma oferta estiver qualificada para o verão todo, ela também poderá ter um peso de A em julho e um peso de B em agosto.

>[!NOTE]
>
>O peso atribuído pode ser modificado temporariamente de acordo com os parâmetros da categoria à qual a oferta pertence. Para obter mais informações, consulte [Criação de categorias de oferta](../../interaction/using/creating-offer-categories.md).

Para criar um peso em uma oferta, aplique as seguintes etapas:

1. Clique em **[!UICONTROL Add]**.

   ![](assets/offer_weight_create_001.png)

1. Altere o rótulo e atribua um peso. Por padrão, é definido como 1.

   ![](assets/offer_weight_create_006.png)

   >[!IMPORTANT]
   >
   >Se nenhum peso for inserido (0), o target não será considerado qualificado para a oferta.

1. Se desejar que o peso seja aplicado por um determinado período, defina datas de qualificação.

   ![](assets/offer_weight_create_002.png)

1. Se necessário, restrinja o peso a um espaço de oferta específico.

   ![](assets/offer_weight_create_003.png)

1. Aplique um filtro a um target.

   ![](assets/offer_weight_create_004.png)

1. Clique em **[!UICONTROL OK]** para salvar o peso.

   ![](assets/offer_weight_create_005.png)

   >[!NOTE]
   >
   >Se um target for elegível para vários pesos de uma oferta selecionada, o mecanismo manterá o melhor (mais alto) peso. Ao ligar para o mecanismo de oferta, uma oferta é selecionada no máximo uma vez por contato.

### Resumo das regras de qualificação de oferta {#a-summary-of-offer-eligibility-rules}

Quando a configuração for concluída, um resumo das regras de eligibilidade estará disponível no painel de ofertas.

Para fazer isso, clique no link **[!UICONTROL Schedule and eligibility rules]**.

![](assets/offer_eligibility_create_005.png)

## Criação do conteúdo da oferta {#creating-the-offer-content}

1. Clique na guia **[!UICONTROL Edit]** e depois na guia **[!UICONTROL Content]**.

   ![](assets/offer_content_create_001.png)

1. Preencha os vários campos do conteúdo da oferta.

   * **[!UICONTROL Title]** : especifique o título que quer que apareça em sua oferta. Aviso: não se refere ao rótulo da oferta, que é definido na guia **[!UICONTROL General]**.
   * **[!UICONTROL Destination URL]**: especifique o URL da sua oferta. Para ser processado corretamente, ele deve começar com &quot;http://&quot; ou &quot;https://&quot;.
   * **[!UICONTROL Image URL]**: especifique um URL ou um caminho de acesso para a imagem da sua oferta.
   * **[!UICONTROL HTML content]** / **[!UICONTROL Text content]** : digite o corpo da oferta na guia desejada. Para gerar o rastreamento, o **[!UICONTROL HTML content]** deve ser composto de elementos HTML que podem ser colocados em um elemento de tipo `<div>`. Por exemplo, o resultado de um elemento `<table>` na página HTML será o seguinte:

   ```
      <div> 
       <table>
        <tr>
         <th>Month</th>
         <th>Savings</th>   
        </tr>   
        <tr>    
         <td>January</td>
         <td>$100</td>   
        </tr> 
       </table> 
      </div>
   ```

   A definição do URL de aceitação é apresentada na seção [Configuração do status quando a proposta é aceita](../../interaction/using/creating-offer-spaces.md#configuring-the-status-when-the-proposition-is-accepted) .

   ![](assets/offer_content_create_002.png)

   Para localizar os campos obrigatórios conforme foram definidos durante a configuração do espaço de oferta, clique no link **[!UICONTROL Content definitions]** para exibir a lista. Para obter mais informações, consulte [Criação de espaços de oferta](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_content_create_003.png)

   Neste exemplo, a oferta deve incluir um título, uma imagem, conteúdo HTML e uma URL de destino.

## Pré-visualização da oferta {#previewing-the-offer}

Assim que o conteúdo da oferta for configurado, é possível pré-visualizar a oferta como ela aparecerá para o recipient. Para fazer isso:

1. Clique na guia **[!UICONTROL Preview]**.

   ![](assets/offer_preview_create_001.png)

1. Selecione a representação da oferta que deseja visualizar.

   ![](assets/offer_preview_create_002.png)

1. Se tiver personalizado o conteúdo da oferta, selecione o target da oferta para visualizar a personalização.

   ![](assets/offer_preview_create_003.png)

## Criação de uma hipótese em uma oferta {#creating-a-hypothesis-on-an-offer}

É possível criar hipóteses nas propostas de ofertas. Isso permite determinar o impacto das ofertas nas compras realizadas do produto em questão.

>[!NOTE]
>
>Essas hipóteses são executadas via Gestor de resposta. Verifique o contrato de licença.

As hipóteses executadas em uma apresentação de oferta são referenciadas na guia **[!UICONTROL Measure]**.

A criação de hipóteses é detalhada [nesta página](../../campaign/using/about-response-manager.md).

![](assets/offer_hypothesis_001.png)

