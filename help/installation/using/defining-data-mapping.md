---
product: campaign
title: Definir mapeamento de dados externos
description: Saiba como mapear dados em um banco de dados externo
feature: Installation, Instance Settings
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
TQID: https://experienceleague.adobe.com/9mE5BjrDg-E4FDyFFL0GVAVPof0rlSSOlzyj2zk21ag
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 91%

---

# Definir mapeamento de dados externos {#defining-data-mapping}



O Adobe Campaign permite definir o mapeamento nos dados em uma tabela externa.

Para fazer isso, após a criação do esquema da tabela externa, é possível criar um novo mapeamento de entrega para usar os dados nessa tabela como um Delivery Target.

Para fazer isso, siga as etapas abaixo:

1. Crie um novo mapeamento de entrega e escolha a dimensão de direcionamento, como o esquema que você acabou de criar, por exemplo.

   ![](assets/wf_new_mapping_create_fda.png)

1. Indique os campos onde as informações de entrega são armazenadas (sobrenome, nome, e-mail, endereço, etc.).

   ![](assets/wf_new_mapping_define_join.png)

1. Especifique os parâmetros para armazenamento de informações, incluindo o sufixo dos esquemas de extensão para que sejam facilmente identificáveis.

   ![](assets/wf_new_mapping_define_names.png)

   Você pode escolher se deseja armazenar exclusões (**excludelog**), com mensagens (**broadlog**) ou em uma tabela separada.

   Você também pode escolher se deseja gerenciar o rastreamento para esse mapeamento de entrega (**trackinglog**).

1. Em seguida, selecione as extensões a serem consideradas. O tipo de extensão depende dos parâmetros e opções da sua plataforma (visualizar seu contrato de licença).

   ![](assets/wf_new_mapping_define_extensions.png)

   Clique no botão **[!UICONTROL Save]** para iniciar a criação de mapeamento de entrega: todas as tabelas vinculadas são criadas automaticamente com base nos parâmetros selecionados.
