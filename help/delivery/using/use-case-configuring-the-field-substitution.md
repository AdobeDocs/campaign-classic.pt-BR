---
product: campaign
title: "Caso de uso: configurar a substituição de campo"
description: "Caso de uso: configurar a substituição de campo"
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Seed Address
exl-id: 3f567b2d-6f98-4831-af84-7db17fd12c6e
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 100%

---

# Caso de uso: configurar a substituição de campo{#use-case-configuring-the-field-substitution}



A substituição de campo aleatório permite atribuir um valor a partir da lista de destinatário para os seed addresses que estão vazios quando o usuário usa esse valor em uma entrega (exemplo: nome, cidade, etc.).

Essa substituição permite economizar tempo ao criar a entrega: em vez de adicionar manualmente o valor desejado aos seed addresses, a substituição recupera aleatoriamente esse valor na lista de destinatários targets da entrega e o aplica aos seed addresses.

## Contexto {#context}

Nesse caso de uso, o site **Minha biblioteca online** gostaria de enviar um desconto aos seus clientes, com base no gênero literário favorito deles.

O gerente de entrega integrou um campo de personalização vinculado ao gênero favorito no email. O objetivo é usar alguns seed addresses: esses seed addresses têm o campo de personalização em sua tabela, mas sem nenhum valor salvo nele.

Para usar a substituição de campo aleatório, você deve ter:

* uma entrega com um ou vários campos de personalização,
* seed addresses cujo **schema de dados** é modificado de acordo com os campos de personalização usados na entrega.

## Criar uma entrega {#step-1---creating-a-delivery}

As etapas para criar uma entrega estão detalhadas na seção [Criar uma entrega por email](creating-an-email-delivery.md).

Neste exemplo, o gerenciador de entrega criou o boletim informativo.

![](assets/dlv_seeds_usecase_24.png)

## Editar o esquema de dados dos seed addresses {#editing-the-seed-addresses-data-schema}

As instruções sobre como modificar um schema de dados são detalhadas na seção .

Neste exemplo, o schema de dados dos seed addresses pega um valor criado pelo schema de dados dos destinatários:

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

Essa enumeração permite especificar o gênero literário favorito de seus clientes.

Para que essa modificação do schema de dados possa ser visualizada no **Formulário de entrada** dos seed addresses, você deve atualizá-lo. Consulte a seção [Atualizar o formulário de entrada](use-case-selecting-seed-addresses-on-criteria.md#updating-the-input-form).

## Configuração da personalização {#configuring-personalization}

1. Abra uma entrega.

   Neste exemplo, a entrega tem dois campos de personalização: o **nome** do destinatário e o **gênero literary favorito** do destinatário.

   ![](assets/dlv_seeds_usecase_25.png)

1. Configure sua lista de entrega e seus seed addresses. Consulte [Identificar as populações alvo](steps-defining-the-target-population.md).

   Neste exemplo, o usuário seleciona usuários cujo **gênero literário favorito** é ficção científica como o principal público alvo.

   ![](assets/dlv_seeds_usecase_26.png)

   O usuário adiciona seed addresses à entrega.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >Para obter mais informações sobre o link **[!UICONTROL Edit the dynamic condition...]**, consulte o [Caso de uso: selecionar seed addresses de acordo com os critérios](use-case-selecting-seed-addresses-on-criteria.md)

1. Clique na guia **[!UICONTROL Preview]** e selecione um seed address para testar a personalização.

   ![](assets/dlv_seeds_usecase_28.png)

   Você pode ver que um dos campos de personalização está vazio. Como o seed address não tem dados para este campo, a visualização de conteúdo HTML não pode exibir um valor.

   A substituição aleatória de campos é realizada **no momento da entrega**.

1. Clique no botão **[!UICONTROL Send]**.
1. Analise e depois **confirme a entrega**.

   Os seed addresses recebem a entrega na caixa de entrada.

   A personalização de campos é eficaz.

   ![](assets/dlv_seeds_usecase_08.png)
