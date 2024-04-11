---
product: campaign
title: Importação e exportação de dados usando workflows
description: Saiba como importar e exportar dados usando workflows no Campaign
feature: Data Management, Workflows
badge-v8: label="Também se aplica à versão v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 98%

---

# Importar e exportar dados usando workflows {#import-export-workflows}



## Coleta de dados {#collecting-data-workflows}

Os workflows podem ser uma maneira útil de automatizar alguns dos processos de importação. Se você importa dados de um arquivo local ou de um SFTP, você pode usar workflows para padronizar os procedimentos de gerenciamento de dados.

### Usar dados de uma lista: Lista de leitura {#using-data-from-a-list--read-list}

Os dados enviados em um fluxo de trabalho podem vir de listas em que os dados foram preparados e estruturados antecipadamente.

Esta lista pode ter sido criada diretamente no Adobe Campaign ou importada pela opção **[!UICONTROL Import a list]**. Para obter mais informações sobre essa opção, consulte esta [página](../../platform/using/about-generic-imports-exports.md).

Para obter mais informações sobre como usar a atividade da lista de leitura em um fluxo de trabalho, consulte [esta página](../../workflow/using/read-list.md).

### Carregar dados de um arquivo {#loading-data-from-a-file}

Os dados processados em um workflow podem ser extraídos de um arquivo estruturado para serem importados para o Adobe Campaign.

Uma descrição da atividade de carregamento de dados pode ser encontrada na seção [Data loading (file)](../../workflow/using/data-loading-file.md).

Exemplo de arquivo estruturado a ser importado:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

Depois que os dados forem coletados, você poderá usá-los em seus workflows, por exemplo, para enriquecer uma entrega ou atualizar o banco de dados. Para obter mais informações, consulte [esta página](../../workflow/using/how-to-use-workflow-data.md).

## Exportar dados {#exporting-data-via-a-workflow}

Os workflows podem ser uma maneira útil de automatizar alguns dos processos de exportação ou exportar conjuntos precisos de dados após usar algumas atividades disponíveis de gerenciamento de dados disponíveis para transformar seus dados.

As operações de exportação são executadas usando uma **[!UICONTROL Data extraction (file) activity]**. Para obter mais informações sobre como configurar e usar a atividade, consulte [esta página](../../workflow/using/extraction-file.md).
