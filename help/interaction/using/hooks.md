---
product: campaign
title: Ganchos
description: 'Ganchos '
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: e1d7d7c2-61e7-40d6-a8ce-69bc976f8c73
source-git-commit: 7728826eea199d2367fcbf556c01ec9d6cae466f
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 100%

---

# Modificar o comportamento padrão do mecanismo{#hooks}

![](../../assets/v7-only.svg)

Ganchos em Interações permitem modificar o **comportamento do mecanismo padrão**.

Os ganchos **[!UICONTROL Target loading]** e **[!UICONTROL Proposition post-processing]** são configurados no espaço de ofertas do Adobe Campaign:

![](assets/interaction_hooks_1.png)

O gancho **[!UICONTROL Dynamic offer]** é configurado com o peso da oferta no Adobe Campaign:

![](assets/interaction_hooks_2.png)

## Carregamento de target {#target-loading}

Este gancho permite enriquecer o perfil do contato (que foi carregado pela query pronta para uso) com dados adicionais de um sistema externo.

Os dados coletados devem ser inseridos no nó de dados da chamada (nó Interaction). O integrador deve ter estendido o schema de dados de chamada antecipadamente para definir a estrutura dos dados coletados. O usuário pode acessar esses dados da mesma forma que os dados de chamada padrão (em regras de qualificação e nível de personalização).

**Parâmetros de entrada:**

* xmlInteraction (tipo xml): nó de interação
* aTargetId (tipo de tabela): identificador do target
* sUuid230 (tipo string): valor do cookie permanente uuid230
* sNlid (tipo string): valor do cookie da sessão nlid

**Parâmetros de retorno:**

* nó Interaction enriquecido (primeiro parâmetro deste gancho)

>[!NOTE]
>
>O parâmetro **xmlInteraction** contém os dados de chamada e o perfil do contato que foi carregado pela query pronta para uso.

**Exemplo:**

```
// Call an external system to get additional data for the target
  var additionalData  = getUrl("https://EXTERNAL_SYSTEM?target=" + encodeURIComponent(aTargetId.join("|")));
  // Enrich the context with this data
  interaction.@additionalData = additionalData;
```

## Pós-processamento de propostas {#proposition-post-processing-}

Este gancho permite verificar a consistência e a compatibilidade de propostas qualificadas em uma determinada interação. Também permite definir uma nova funcionalidade de cálculo de pontuação ou probabilidade.

Exemplo de uso de regras de consistência:

* Limitar o número de propositions na mesma chamada, vinculado ao mesmo produto ou a mesma categoria.
* Apresentar apenas ofertas relacionadas a um produto na mesma interação.

O pós-processamento é executado depois do aplicativo de regras de tipologia e da classificação de proposta qualificada e antes da etapa de priorização.

**Parâmetros de entrada:**

* aProposition: tabela de propostas qualificadas. Veja aqui um exemplo da estrutura de um elemento nesta tabela.

   ```
   { offer_id:1234,
     weight:2}
   ```

* dicOffer (tipo xml): dicionário de todos os atributos de ofertas qualificadas (código de oferta, id da categoria, nome completo da categoria, data inicial, data final, rótulo, nome interno, ID da oferta, campos de oferta adicionais). Por exemplo:

   ```
   { "1242": <offer category-id="61242" categoryFullName="/FULL/PATH/TO/CATEGORY/" code="CODE" endDate="" id="62473" label="LABEL" name="OFR38_OE4" product-id="43" startDate=""/>,
     "1243": ...}
   ```

* xmlTarget (tipo xml): nó de dados de perfil
* xmlInteraction (tipo xml): nó de dados de chamada
* iPropNumber (tipo inteiro): número de ofertas esperadas

**Parâmetros de retorno:**

* lista de propostas modificadas (primeiro parâmetro do gancho)
* nó Interaction modificado

**Exemplo:**

```
var aReturnedProps = [];

if( aProposition.length > 0 )
{
  var iReturnedProps = 0;
  for( var iPropIdx = 0; iPropIdx < aProposition.length && iReturnedProps < iPropNumber; iPropIdx ++ )
  {
    // Check a consistency rule for instance
    if( true )
    {
      aReturnedProps.push(aProposition[iPropIdx]);
      iReturnedProps++;
    }
  }
}

return aReturnedProps;
```

## Oferta dinâmica {#dynamic-offer}

Este gancho permite fazer uma chamada para um mecanismo externo para selecionar uma lista de produtos vinculados a uma oferta. Ele é configurado na oferta após as regras de qualificação e antes do aplicativo de regras de tipologia.

O integrador deve estender o schema **PropositionRcp** anteriormente com as informações adicionais sobre o produto. Para especificar onde esses dados serão armazenados, um link **[!UICONTROL Proposition being processed]** está disponível na guia **[!UICONTROL Storage]** do espaço.

![](assets/interaction_hooks_3.png)

**Parâmetros de entrada:**

* xmlOffer (tipo xml): oferta (código de oferta, id da categoria, nome completo da categoria, data inicial, data final, rótulo, nome interno, campos de oferta adicionais)
* dWeight: peso de contexto (tipo double)
* xmlTarget (tipo xml): nó de dados de perfil
* xmlInteraction (tipo xml): nó de dados de chamada

**Parâmetros de retorno:**

Uma tabela de propostas a serem geradas é retornada. Cada elemento desta tabela é composto pelas seguintes informações:

* identificador de oferta
* dados adicionais do produto (código do produto, por exemplo)
* peso

>[!NOTE]
>
>O sistema verifica se o ID da oferta é o mesmo para os parâmetros de entrada e de retorno.

**Exemplo:**

```
var product = getUrl("https://EXTERNAL_SYSTEM?offerCode=" + encodeURIComponent(xmlOffer.@code));
if( product )
  return [{offer_id: parseInt(String(xmlOffer.@id)), weight: dWeight, productId: product}];
```
