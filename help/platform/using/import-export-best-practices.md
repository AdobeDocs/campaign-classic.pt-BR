---
product: campaign
title: Práticas recomendadas de importação e exportação
description: Saiba mais sobre as práticas recomendadas a serem seguidas ao importar ou exportar dados.
audience: automating
content-type: reference
topic-tags: workflow-general-operation
exl-id: 03d35202-d221-4136-aad4-00704aabb356
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '511'
ht-degree: 100%

---

# Práticas recomendadas de importação e exportação {#import-export-best-practices}

![](../../assets/common.svg)

Ser cuidadoso e seguir as regras simples detalhadas abaixo ajudará a garantir a consistência dos dados dentro do banco de dados e evitar erros comuns durante a atualização ou exportação de dados.

## Utilização de modelos de fluxo de trabalho {#using-import-templates}

A maioria dos workflows destinados à importação de dados deve conter as seguintes atividades: **[!UICONTROL Load file]**, **[!UICONTROL Reconciliation]**, **[!UICONTROL Segmentation]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

É muito conveniente usar modelos de fluxo de trabalho para preparar importações semelhantes e garantir a consistência dos dados no banco de dados.

Em muitos projetos, as importações são criadas sem a atividade **[!UICONTROL Deduplication]** porque os arquivos usados no projeto não têm duplicatas. As duplicatas às vezes surgem da importação de arquivos diferentes. A eliminação de duplicatas é difícil. Portanto, a etapa de eliminação de duplicatas é uma boa precaução em todos os workflows de importação.

Não confie na suposição de que os dados de entrada são consistentes e corretos, ou que o departamento de TI ou o supervisor do Adobe Campaign irá resolver isso. Durante o projeto, mantenha a limpeza dos dados em mente. Elimine duplicatas, reconcilie e mantenha de consistência ao importar dados.

Um exemplo de modelo de fluxo de trabalho genérico projetado para importar dados está disponível na seção [Exemplo: modelo de fluxo de trabalho para importar dados](../../platform/using/creating-import-export-templates.md).

## Usar formatos de arquivo simples {#using-flat-file-formats}

O formato mais eficiente para importações é o arquivo simples. Arquivos simples podem ser importados no modo em massa no nível do banco de dados.

Por exemplo:

* Separador: tabulação ou ponto e vírgula
* Primeira linha com cabeçalhos
* Nenhum delimitador de cadeia de caracteres
* Formato de data: AAAA/MM/DD HH:mm:SS

Exemplo de arquivo a ser importado:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## Usar compactação {#using-compression}

Use arquivos compactados para importações e exportações sempre que possível. O GZIP é compatível por padrão. Você pode adicionar pré-processamento ao importar arquivos ou pós-processamento ao extrair dados, respectivamente nas atividades de fluxo de trabalho **[!UICONTROL Load file]** e **[!UICONTROL Extract file]**.

**Tópicos relacionados:**

* [Atividade de carregamento de dados (arquivo)](../../workflow/using/data-loading--file-.md)
* [Atividade de extração de dados (arquivo)](../../workflow/using/extraction--file-.md)

## Importar no modo Delta {#importing-in-delta-mode}

Importações regulares devem ser feitas no modo delta. Isso significa que somente os dados modificados ou novos são enviados ao Adobe Campaign, em vez da tabela toda sempre.

As importações completas devem ser usadas somente para carregamento inicial.

## Manter a consistência {#maintaining-consistency}

Para manter a consistência dos dados no banco de dados do Adobe Campaign, siga os princípios abaixo:

* Se os dados importados corresponderem a uma tabela de referência no Adobe Campaign, então ele deverá ser reconciliado com essa tabela no workflow. Os registros que não correspondem devem ser rejeitados.
* Certifique-se de que os dados importados sejam sempre **&quot;normalizados&quot;** (email, número de telefone, endereço de mala direta) e que essa normalização seja confiável e não será alterada ao longo dos anos. Se não for o caso, provavelmente aparecerão algumas duplicatas no banco de dados e, como o Adobe Campaign não fornece ferramentas para fazer a correspondência &quot;difusa&quot;, será muito difícil removê-las e gerencia-las.
* Os dados transacionais devem ter uma chave de reconciliação e serem reconciliados com os dados existentes para evitar a criação de duplicatas.
* **Importação de arquivos relacionados em ordem**. Se a importação for composta de vários arquivos que dependem uns dos outros, o workflow deve garantir que os arquivos sejam importados na ordem correta. Quando um arquivo falhar, os outros arquivos não serão importados.
* **Elimine duplicatas**, reconcilie e mantenha de consistência ao importar dados.
