---
title: Criação de uma oferta
seo-title: Criação de uma oferta
description: Criação de uma oferta
seo-description: null
page-status-flag: never-activated
uuid: 9e8b0351-e2a5-4043-be86-e275d2f849ea
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: 010c88f4-9444-448f-bb7b-7191517d2e23
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Criação de uma oferta{#creating-an-offer}

## Criação da oferta {#creating-the-offer}

Para criar uma simulação, aplique as seguintes etapas:

1. Vá para o **[!UICONTROL Campaigns]** universo e clique no **[!UICONTROL Offers]** link.

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

In the **[!UICONTROL Eligibility]** tab, define the period the offer will be valid for and can be presented, the filters to apply to the target and the offer weight.

### Definição do período de qualificação de uma oferta {#defining-the-eligibility-period-of-an-offer}

Para definir o período de qualificação da oferta, use as listas suspensas e selecione uma data inicial e final no calendário.

![](assets/offer_eligibility_create_002.png)

Fora dessas datas, a oferta não será selecionada pelo mecanismo do Interaction. Se também tiver configurado datas de qualificação para a categoria de oferta, o período mais restritivo será aplicado.

### Filtros no target {#filters-on-the-target}

É possível aplicar filtros ao target da oferta.

To do this, click the **[!UICONTROL Edit query]** link and select the filter you want to apply. (Consulte [esta seção](../../platform/using/steps-to-create-a-query.md#step-4---filter-data)).

![](assets/offer_eligibility_create_003.png)

Se os filtros predefinidos já tiverem sido criados, é possível selecioná-los na lista de filtros de usuário. Para obter mais informações, consulte [Criação de filtros](../../interaction/using/creating-predefined-filters.md)predefinidos.

![](assets/offer_eligibility_create_004.png)

### Peso da oferta {#offer-weight}

Para permitir que o mecanismo decida entre várias ofertas que o target está qualificado, é necessário atribuir um ou mais pesos à oferta. Também é possível aplicar filtros ao target se necessário ou restringir o espaço de oferta ao qual o peso será aplicado. Uma oferta com um peso mais significativo será preferível sobre uma oferta com menos peso.

É possível configurar vários pesos para a mesma oferta, por exemplo, para distinguir sub-períodos, alvos específicos ou até mesmo um espaço de oferta.

Por exemplo, uma oferta pode ter um peso de A para contatos com idade entre 18 e 25 e um peso de B para contatos acima desse intervalo. Se uma oferta estiver qualificada para o verão todo, ela também poderá ter um peso de A em julho e um peso de B em agosto.

>[!NOTE]
>
>O peso atribuído pode ser modificado temporariamente de acordo com os parâmetros da categoria à qual a oferta pertence. Para obter mais informações, consulte [Criar categorias](../../interaction/using/creating-offer-categories.md)de ofertas.

Para criar uma simulação, aplique as seguintes etapas:

1. Clique em **[!UICONTROL Add]**.

   ![](assets/offer_weight_create_001.png)

1. Altere o rótulo e atribua um peso. Por padrão, é definido como 1.

   ![](assets/offer_weight_create_006.png)

   >[!CAUTION]
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

### Um resumo das regras de qualificação de oferta {#a-summary-of-offer-eligibility-rules}

Quando a configuração for concluída, um resumo das regras de eligibilidade estará disponível no painel de ofertas.

Para exibi-la, clique no **[!UICONTROL Schedule and eligibility rules]** link.

![](assets/offer_eligibility_create_005.png)

## Criação do conteúdo da oferta {#creating-the-offer-content}

1. Clique na **[!UICONTROL Edit]** guia e, em seguida, clique na **[!UICONTROL Content]** guia.

   ![](assets/offer_content_create_001.png)

1. Preencha os vários campos do conteúdo da oferta.

   * **[!UICONTROL Title]** : Especifique o título que deseja fazer aparecer em sua oferta. Warning: this is not referring to the offer&#39;s label, which is defined in the **[!UICONTROL General]** tab.
   * **[!UICONTROL Destination URL]** : especifique o URL da oferta. Para ser processado corretamente, ele deve começar com &quot;http://&quot; ou &quot;https://&quot;.
   * **[!UICONTROL Image URL]** : especifique um URL ou um caminho de acesso para a imagem de sua oferta.
   * **[!UICONTROL HTML content]** / **[!UICONTROL Text content]** : digite o corpo da sua oferta na guia desejada. To generate tracking, the **[!UICONTROL HTML content]** must be composed of HTML elements that can be enclosed in a `<div>` type element. For example, the result of a `<table>` element in the HTML page will be as followed:

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

   To find the required fields as they were defined during offer space configuration, click the **[!UICONTROL Content definitions]** link to display the list. Para obter mais informações, consulte [Criação de espaços](../../interaction/using/creating-offer-spaces.md)de oferta.

   ![](assets/offer_content_create_003.png)

   Neste exemplo, a oferta deve incluir um título, uma imagem, conteúdo HTML e uma URL de destino.

## Pré-visualização da oferta {#previewing-the-offer}

Assim que o conteúdo da oferta for configurado, é possível pré-visualizar a oferta como ela aparecerá para o recipient. Para fazer isso:

1.  Clique na **[!UICONTROL Preview]** guia.

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

Hypotheses carried out on an offer proposition are referenced in their **[!UICONTROL Measure]** tab.

A criação de hipóteses é detalhada [nesta página](../../campaign/using/about-response-manager.md).

![](assets/offer_hypothesis_001.png)

