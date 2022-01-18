---
product: campaign
title: Perfis de operador
description: Perfis de operador
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: e11fb28c-d530-45a2-862a-ff1c20975577
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: ht
source-wordcount: '384'
ht-degree: 100%

---

# Perfis de operador{#operator-profiles}

![](../../assets/v7-only.svg)

Existem dois tipos de operadores que usam o Interaction: gerentes de oferta e gerentes de delivery. Cada um deles tem direitos específicos que só dão acesso a algumas partes da árvore e da plataforma.

* **[!UICONTROL Offer manager]** : cria e mantém ofertas. Observe que se as ofertas forem usadas no workflow, o operador precisará estar no **[!UICONTROL Administrator]** ou no grupo de operadores **[!UICONTROL Offer managers]** para executar o workflow.
* **[!UICONTROL Delivery manager]** : aprova e usa ofertas

As etapas para criar operadores específicos ao Interaction são idênticas às usadas para criar todos os outros operadores na plataforma. Para obter mais informações, consulte [esta seção](../../platform/using/access-management.md). Os direitos são configurados durante a criação do operador.

## Gerente de ofertas {#offer-manager}

1. Crie um novo operador.
1. Vá para a janela **[!UICONTROL Groups and named rights]**, clique em **[!UICONTROL Add]** e selecione o grupo **[!UICONTROL Offer manager]**.

   ![](assets/offer_operators_create_001.png)

Os direitos atribuídos ao gerente de ofertas permitem que eles executem as seguintes tarefas:

* Modificar ambientes **[!UICONTROL Design]**.
* Visualizar ambientes **[!UICONTROL Live]**.
* Configurar funções de administração (espaços e filtros predefinidos).
* Criar e alterar categorias.
* Criar ofertas.
* Configurar a qualificação para a oferta.
* Aprovar ofertas.

   >[!NOTE]
   >
   >O gerente de ofertas só pode aprovar uma oferta em dois casos específicos. O primeiro se ninguém tiver sido especificado como revisor, e o segundo se o operador encarregado de criar templates (com o direito de atribuir revisores) especificou ele/ela como revisor no template de oferta em que a oferta foi baseada.

## Gerente de delivery {#delivery-manager}

1. Crie um novo operador.
1. Vá para a janela **[!UICONTROL Groups and named rights]**, clique em **[!UICONTROL Add]** e selecione o grupo **[!UICONTROL Delivery manager]**.

   ![](assets/offer_operators_create_002.png)

Os direitos atribuídos aos gerentes de delivery os habilitam a realizar as seguintes tarefas:

* Exibir ambientes **[!UICONTROL Live]**.
* Exibir e modificar categorias de ofertas.
* Aprovar ofertas se esse gerente de delivery for especificado como um de seus revisores.

   >[!NOTE]
   >
   >Os gerentes de delivery só podem aprovar uma oferta se tiverem sido definidos como revisores durante a configuração da oferta.

## Resumo dos direitos de acordo com o operador {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Gerente de ofertas (edição)</strong><br /> </td> 
   <td> <strong>Gerente de ofertas (live)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Nível de estrutura de árvore</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Ofertas que estão sendo editadas / Ofertas ativas<br /> </td> 
   <td> Ler / Gravar<br /> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Recipiente - Ambiente<br /> </td> 
   <td> Ler / Gravar<br /> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Administração<br /> </td> 
   <td> Ler / Gravar<br /> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Espaços<br /> </td> 
   <td> Ler / Gravar<br /> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Filtros de oferta predefinidos<br /> </td> 
   <td> Ler / Gravar<br /> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Tipologia<br /> </td> 
   <td> Ler / Gravar<br /> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Regras de tipologia<br /> </td> 
   <td> Ler / Gravar<br /> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Catálogo de ofertas<br /> </td> 
   <td> Ler / Gravar<br /> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Categoria de oferta<br /> </td> 
   <td> Ler / Gravar<br /> </td> 
   <td> Ler<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Gerente de delivery (edição)</strong><br /> </td> 
   <td> <strong>Gerente de delivery (live)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Nível de estrutura de árvore</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Ofertas que estão sendo editadas / Ofertas ativas<br /> </td> 
   <td> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Recipiente - Ambiente<br /> </td> 
   <td> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Administração<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Espaços<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Filtros de oferta predefinidos<br /> </td> 
   <td> Ler<br /> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Tipologia<br /> </td> 
   <td> Ler<br /> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Regras de tipologia<br /> </td> 
   <td> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Catálogo de ofertas<br /> </td> 
   <td> Ler<br /> </td> 
   <td> Ler<br /> </td> 
  </tr> 
  <tr> 
   <td> Categoria de oferta<br /> </td> 
   <td> </td> 
   <td> Ler<br /> </td> 
  </tr> 
 </tbody> 
</table>
