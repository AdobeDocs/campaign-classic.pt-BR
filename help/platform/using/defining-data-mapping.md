---
title: Acesso a um banco de dados externo
seo-title: Acesso a um banco de dados externo
description: Acesso a um banco de dados externo
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 100%

---


# Definição do mapeamento de dados {#defining-data-mapping}

O Adobe Campaign permite definir o mapeamento nos dados em uma tabela externa.

Para fazer isso, após a criação do schema da tabela externa, é possível criar um novo mapeamento de delivery para usar os dados nessa tabela como um Delivery Target.

Para fazer isso, siga as etapas abaixo:

1. Crie um novo mapeamento de delivery e escolha o targeting dimension, como o schema que você acabou de criar, por exemplo.

   ![](assets/wf_new_mapping_create_fda.png)

1. Indique os campos onde as informações de delivery são armazenadas (sobrenome, nome, e-mail, endereço, etc.).

   ![](assets/wf_new_mapping_define_join.png)

1. Especifique os parâmetros para armazenamento de informações, incluindo o sufixo dos schemas de extensão para que sejam facilmente identificáveis.

   ![](assets/wf_new_mapping_define_names.png)

   Você pode escolher se deseja armazenar exclusões (**excludelog**), com mensagens (**broadlog**) ou em uma tabela separada.

   Você também pode escolher se deseja gerenciar o rastreamento para esse mapeamento de delivery (**trackinglog**).

1. Em seguida, selecione as extensões a serem consideradas. O tipo de extensão depende dos parâmetros e opções da sua plataforma (visualizar seu contrato de licença).

   ![](assets/wf_new_mapping_define_extensions.png)

   Clique no botão **[!UICONTROL Save]** para iniciar a criação de mapeamento de delivery: todas as tabelas vinculadas são criadas automaticamente com base nos parâmetros selecionados.
