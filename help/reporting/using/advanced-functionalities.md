---
title: Funcionalidades avançadas
seo-title: Funcionalidades avançadas
description: Funcionalidades avançadas
seo-description: null
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: af768da6ee8cc0ca2ea1f24f297239b974c113a5

---


# Funcionalidades avançadas{#advanced-functionalities}

## Adição de um script {#adding-a-script}

### Atividade script {#script-activity}

Essa atividade permite processar dados e criar queries complexas facilmente que não permitem a linguagem SQL.

Basta inserir sua query na janela do script.

A guia **[!UICONTROL Texts]** permite definir cadeias de texto. Elas podem ser usadas com a seguinte sintaxe: **$(Identifier)**. Para obter mais informações sobre como usar textos, consulte [Adicionar um cabeçalho e um rodapé](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>NÃO recomendamos o uso do código JavaScript para criar agregações.

Para criar um histórico do relatório, adicione a seguinte linha à sua query JavaScript para salvar os dados arquivados:

```
if( ctx.@_historyId.toString().length == 0 )
```

Caso contrário, os dados atuais serão exibidos.

### Script externo {#external-script}

É possível usar um script externo que será executado no servidor e/ou no lado do cliente. Para fazer isso:

1. Edite as propriedades do relatório e clique em **[!UICONTROL Scripts]**.
1. Clique em **[!UICONTROL Add]** e selecione o script que será referenciado.
1. Em seguida, selecione o modo de execução.

   Se adicionar vários scripts, use as setas da barra de ferramentas para definir sua sequência de execução.

   ![](assets/reporting_custom_js.png)

## Chamado de outro relatório {#calling-up-another-report}

### Atividade de jump {#jump-activity}

Um jump é como uma transição sem uma seta: permite ir de uma atividade para outra ou acessar outro relatório.
