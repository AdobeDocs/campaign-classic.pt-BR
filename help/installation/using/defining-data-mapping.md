---
product: campaign
title: Definir mapeamento de dados externos
description: Saiba como mapear dados em um banco de dados externo
feature: Installation, Instance Settings
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 91%

---

# Definir mapeamento de dados externos {#defining-data-mapping}



O Adobe Campaign permite definir o mapeamento nos dados em uma tabela externa.

Para fazer isso, após a criação do schema da tabela externa, é possível criar um novo mapeamento de entrega para usar os dados nessa tabela como um Delivery Target.

Para fazer isso, siga as etapas abaixo:

1. Crie um novo mapeamento de entrega e escolha o targeting dimension, como o schema que você acabou de criar, por exemplo.

   ![](assets/wf_new_mapping_create_fda.png)

1. Indique os campos onde as informações de entrega são armazenadas (sobrenome, nome, e-mail, endereço, etc.).

   ![](assets/wf_new_mapping_define_join.png)

1. Especifique os parâmetros para armazenamento de informações, incluindo o sufixo dos schemas de extensão para que sejam facilmente identificáveis.

   ![](assets/wf_new_mapping_define_names.png)

   Você pode escolher se deseja armazenar exclusões (**excludelog**), com mensagens (**broadlog**) ou em uma tabela separada.

   Você também pode escolher se deseja gerenciar o rastreamento para esse mapeamento de entrega (**trackinglog**).

1. Em seguida, selecione as extensões a serem consideradas. O tipo de extensão depende dos parâmetros e opções da sua plataforma (visualizar seu contrato de licença).

   ![](assets/wf_new_mapping_define_extensions.png)

   Clique no botão **[!UICONTROL Save]** para iniciar a criação de mapeamento de entrega: todas as tabelas vinculadas são criadas automaticamente com base nos parâmetros selecionados.
