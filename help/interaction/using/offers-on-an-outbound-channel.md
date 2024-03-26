---
product: campaign
title: Ofertas em um canal de saída
description: Ofertas em um canal de saída
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: 77fee343-09d1-4d60-be43-efe02953a70c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 100%

---

# Ofertas em um canal de saída{#offers-on-an-outbound-channel}



## Entrega da oferta de email {#email-offer-delivery}

Em nosso banco de dados, há uma categoria de ofertas de viagem para a África. A qualificação, os contextos e as representações de cada oferta foram configurados. Agora, queremos criar uma campanha para apresentar nossas ofertas por e-mail.

1. Crie uma campanha de marketing e o workflow para construção do target.

   ![](assets/offer_delivery_example_001.png)

1. Edite a entrega do email e clique no ícone **[!UICONTROL Offers]**.

   ![](assets/offer_delivery_example_002.png)

1. Escolha o espaço de e-mail do ambiente de oferta que corresponda aos feriados.

   ![](assets/offer_delivery_example_003.png)

1. Escolha a categoria que contém as ofertas de viagem da África.

   ![](assets/offer_delivery_example_004.png)

1. Defina o número de ofertas na entrega para dois.

   ![](assets/offer_delivery_example_005.png)

1. Feche a janela de gerenciamento de ofertas e crie o conteúdo de sua entrega.

   ![](assets/offer_delivery_example_006.png)

1. Use os menus para inserir uma apresentação de oferta e escolha a função de renderização HTML.

   ![](assets/offer_delivery_example_007.png)

1. Insira a segunda apresentação de oferta.

   ![](assets/offer_delivery_example_008.png)

1. Clique em **[!UICONTROL Preview]** para visualizar as ofertas na entrega e, em seguida, selecione um destinatário para visualizar as ofertas que eles receberão.

   ![](assets/offer_delivery_example_009.png)

1. Salve a entrega e inicie o workflow para construção do target.
1. Abra a entrega e clique na guia **[!UICONTROL Audit]** dele: é possível ver que o mecanismo de oferta selecionou as propostas a serem feitas dentre as várias ofertas do catálogo.

   ![](assets/offer_delivery_example_010.png)

## Executar uma simulação de oferta {#perform-an-offer-simulation}

1. Na guia **[!UICONTROL Profiles and Targets]**, clique no link **[!UICONTROL Simulations]** e depois clique no botão **[!UICONTROL Create]**.

   ![](assets/offer_simulation_001.png)

1. Escolha um rótulo e especifique as configurações de execução, se necessário.

   ![](assets/offer_simulation_example_002.png)

1. Salve a simulação. Isso abrirá em uma nova guia.

   ![](assets/offer_simulation_example_003.png)

1. Clique na guia **[!UICONTROL Edit]** e depois em **[!UICONTROL Scope]**.

   ![](assets/offer_simulation_example_004.png)

1. Escolha a categoria que deseja simular ofertas.

   ![](assets/offer_simulation_example_005.png)

1. Escolha o espaço de oferta a ser usado para a simulação.

   ![](assets/offer_simulation_example_006.png)

1. Insira as datas de validade. É necessário inserir pelo menos uma data de início. Isso permite que o mecanismo de oferta ofereça e escolha aqueles que são válidos em uma determinada data.
1. Se necessário, especifique um ou vários temas para restringir o número de ofertas que contêm essa palavra-chave em suas configurações.

   No nosso exemplo, a categoria **Viagem** contém duas subcategorias com dois temas separados. Queremos executar uma simulação para ofertas com o tema **Customers>1 ano** .

   ![](assets/offer_simulation_example_007.png)

1. Escolha os destinatários que deseja direcionar.

   ![](assets/offer_simulation_example_008.png)

1. Configure o número de ofertas a serem enviadas para cada destinatário.

   No nosso exemplo, o mecanismo de oferta escolherá as 3 ofertas com o peso mais alto para cada destinatário.

   ![](assets/offer_simulation_example_009.png)

1. Salve as configurações e clique em **[!UICONTROL Start]**, na guia **[!UICONTROL Dashboard]**, para executar a simulação.

   ![](assets/offer_simulation_example_010.png)

1. Uma vez concluída a simulação, consulte os **[!UICONTROL Results]** para obter uma análise detalhada das propostas por oferta.

   No nosso exemplo, o mecanismo de oferta baseou o detalhamento da oferta em 3 propostas.

   ![](assets/offer_simulation_example_011.png)

1. Exiba **[!UICONTROL Breakdown of offers by rank]** para visualizar a lista de ofertas selecionadas pelo mecanismo de oferta.

   ![](assets/offer_simulation_example_012.png)

1. Se necessário, é possível alterar as configurações do escopo e executar a simulação novamente clicando em **[!UICONTROL Start simulation]**.

   ![](assets/offer_simulation_example_010.png)

1. Para salvar os dados da simulação, use o histórico ou as funções de exportação disponíveis no relatório.

   ![](assets/offer_simulation_example_013.png)
