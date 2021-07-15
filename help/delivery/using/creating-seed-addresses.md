---
product: campaign
title: Criação de seed addresses
description: Saiba como criar e usar seeds addresses
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: ht
source-wordcount: '413'
ht-degree: 100%

---

# Criação de seed addresses{#creating-seed-addresses}

Os seed addresses não são gerenciados por meio de perfis e públicos-alvo padrão, mas em um nó dedicado da hierarquia do Adobe Campaign **[!UICONTROL Resources > Campaign management > Seed addresses]**.

Você pode criar subpastas para organizar os seed addresses. Para fazer isso, clique com o botão direito do mouse no nó **[!UICONTROL Seed addresses]** e selecione **[!UICONTROL Create a new 'Seed addresses' folder]**. Nomeie a subpasta e pressione **[!UICONTROL Enter]** para validar. Agora você pode criar ou copiar seed addresses para esta subpasta. Para obter mais informações, consulte [Definindo addresses](#defining-addresses).

O Adobe Campaign também permite criar templates de seed addresses que são importados para deliveries ou campanhas e adaptados com base nas necessidades específicas dos deliveries e campanhas relacionadas. Consulte [Criação de templates de seed address](#creating-seed-address-templates).

## Definição de endereços {#defining-addresses}

Para criar seed addresses, siga as etapas abaixo:

1. Clique no botão **[!UICONTROL New]** acima da lista de seed addresses.
1. Insira os dados vinculados ao endereço nos campos correspondentes da guia **[!UICONTROL Recipient]**. Os campos disponíveis correspondem aos campos padrão nos perfis dos recipients do delivery (tabela nms:recipient): sobrenome, nome, email, etc.

   >[!NOTE]
   >
   >O rótulo do endereço é preenchido automaticamente com o sobrenome e o nome que você definiu.
   >
   >Não é necessário inserir todos os campos de cada guia ao criar um seed address. Todos os elementos de personalização ausentes são inseridos aleatoriamente durante o delivery.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. Na guia **[!UICONTROL Seed fields]**, insira os valores que serão inseridos nos logs de delivery durante a fase de análise (na tabela **[!UICONTROL nms:broadLog]**).

1. Na guia **[!UICONTROL Additional data]**, insira os dados de personalização usados para os deliveries criados nos workflows de gestão de dados, aos quais você deseja atribuir um valor específico.

   >[!NOTE]
   >
   >Verifique se os dados adicionais do público-alvo foram definidos com um pseudônimo iniciado por &#39;@&#39; na atividade **[!UICONTROL Enrichment]**. Caso contrário, você não poderá usá-los corretamente com seus seeds addresses na atividade do delivery.

## Criação de modelos de seed address {#creating-seed-address-templates}

Para criar templates de endereço que serão importados e podem ser modificados para cada delivery, o processo é o mesmo que definir um novo seed address. A única diferença é que os templates de seed address devem ser armazenados em uma pasta do tipo &#39;template&#39;.

Para definir uma pasta de template, siga o seguinte processo:

1. Crie uma nova pasta do tipo **[!UICONTROL Seed addresses]**, clique com o botão direito do mouse na pasta e selecione **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Clique na guia **[!UICONTROL Restriction]** e adicione a seguinte condição de filtragem: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Os endereços armazenados nesta pasta agora podem ser usados como templates de endereço. Você pode importá-los para deliveries ou campanhas e adaptá-los com base nas necessidades específicas de deliveries e campanhas relacionadas (consulte[Adição de seed addresses](adding-seed-addresses.md)).
