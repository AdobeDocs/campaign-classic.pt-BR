---
title: Recursos avançados
description: Recursos avançados
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
translation-type: tm+mt
source-git-commit: 2a82493deada11cb22ef37d215b6eae8274ce890
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 53%

---


# Recursos avançados{#advanced-functionalities}

Como usuário técnico, além das propriedades [](../../reporting/using/properties-of-the-report.md)gerais, você pode aproveitar recursos avançados para configurar seus relatórios, como:

* Crie query complexos para processar dados em uma atividade **Script** . [Saiba mais](#script-activity)

* Adicione um script externo para ser executado no servidor ou no cliente. [Saiba mais](#external-script)

* Chame um relatório com uma atividade **de salto** . [Saiba mais](#calling-up-another-report)

* Adicione um parâmetro de URL a um relatório para torná-lo mais acessível. [Saiba mais](#calling-up-another-report)

* Adicione variáveis a serem usadas no contexto do relatório. [Saiba mais](#adding-variables)

## Trabalhar com scripts {#adding-a-script}

### Scripts externos de referência {#external-script}

Você pode fazer referência a códigos JavaScript que serão executados no lado do cliente e/ou do servidor quando a página do relatório for chamada.

Para fazer isso:

1. Edit the [report properties](../../reporting/using/properties-of-the-report.md) and click the **[!UICONTROL Scripts]**.
1. Clique em **[!UICONTROL Add]** e selecione o script que será referenciado.
1. Em seguida, selecione o modo de execução.

   Se adicionar vários scripts, use as setas da barra de ferramentas para definir sua sequência de execução.

   ![](assets/reporting_custom_js.png)

Para execução normal no lado do cliente, os scripts referenciados devem ser gravados em JavaScript e devem ser compatíveis com navegadores comuns. Para obter mais informações, consulte [esta seção](../../web/using/web-forms-answers.md).

### Adding a Script activity {#script-activity}

Ao [projetar seu relatório](../../reporting/using/creating-a-new-report.md#modelizing-the-chart), use a **[!UICONTROL Script]** atividade para processar dados e criar facilmente query complexos que não habilitam o idioma SQL. Você pode inserir seu query diretamente na janela de script.

A guia **[!UICONTROL Texts]** permite definir cadeias de texto. Elas podem ser usadas com a seguinte sintaxe: **$(Identifier)**. Para obter mais informações sobre como usar textos, consulte [Adicionar um cabeçalho e um rodapé](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>NÃO recomendamos o uso do código JavaScript para criar agregações.

Para criar um histórico do relatório, adicione a seguinte linha à sua query JavaScript para salvar os dados arquivados:

```
if( ctx.@_historyId.toString().length == 0 )
```

Caso contrário, somente os dados atuais serão exibidos.

## Adicionar um parâmetro de URL {#defining-additional-settings}

The **[!UICONTROL Parameters]** tab of the [report properties](../../reporting/using/properties-of-the-report.md) lets you define additional settings for the report: these settings will be passed into the URL during the call up.

>[!CAUTION]
>
>Por motivos de segurança, esses parâmetros devem ser usados com muito cuidado.

Para criar uma nova configuração:

1. Clique no botão **[!UICONTROL Add]** e digite o nome da configuração.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Se necessário, especifique se a configuração será obrigatória ou não.

1. Selecione o tipo de configuração que deseja criar: **[!UICONTROL Filter]** ou **[!UICONTROL Variable]**.

   A opção **[!UICONTROL Filter entities]** permite usar um campo do banco de dados como parâmetro.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   Os dados são recuperados diretamente no nível da entidade: **ctx/receipt/@account**.

   A opção **[!UICONTROL Variable]** permite criar ou selecionar uma variável que será passada como parâmetro do URL e pode ser usada nos filtros.

O **[!UICONTROL Response HTTP headers]** permite que você evite o recurso de clickjacking ao incluir a página do seu relatório em uma página HTML usando o iframe. Para evitar o clickjacking, você pode escolher o comportamento **[!UICONTROL X-Frame-options header]**:

* **[!UICONTROL None]**: O relatório não terá **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**: Definido por padrão para novos relatórios e relatórios republicados. O nome do host será igual ao URL do relatório.
* **[!UICONTROL Deny]**: O relatório não pode ser incluído em uma página HTML usando iframe.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Adição de variáveis {#adding-variables}

A guia **[!UICONTROL Variables]** contém a lista de variáveis configuradas no relatório. Essas variáveis são expostas no contexto do relatório e podem ser utilizadas em cálculos.

Clique no botão **[!UICONTROL Add]** para criar uma nova variável.

Para exibir a definição de uma variável, selecione-a e clique no botão **[!UICONTROL Detail...]**.

![](assets/s_ncs_advuser_report_properties_10.png)

## Caso de uso: usar variáveis e parâmetros em um relatório

No exemplo de vídeo abaixo, você aprenderá a adicionar um parâmetro &quot;_type&quot; para criar visualizações diferentes de um relatório, com base no valor desse atributo.

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com)


## Chamado de outro relatório {#calling-up-another-report}

A **Jump** activity is like a transition without an arrow: it lets you go from one activity to another or access another report.
