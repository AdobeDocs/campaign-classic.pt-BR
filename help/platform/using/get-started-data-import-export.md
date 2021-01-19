---
solution: Campaign Classic
product: campaign
title: Introdução à importação e exportação de dados
description: Saiba mais sobre importação e exportação de dados no Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 37cc6cd8b71ec82cd4e6a910d6664a51ed5c091e
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 8%

---


# Introdução à importação e exportação de dados {#get-started-data-import-export}

A Adobe Campaign Classic fornece recursos de gestão de dados que permitem importar e exportar dados. Estas operações podem ser efetuadas utilizando workflows ou importações e exportações genéricas.

>[!IMPORTANT]
>
>Lembre-se dos limites do armazenamento SFTP, do armazenamento do banco de dados e do perfil ativo conforme o contrato da Adobe Campaign ao usar essa funcionalidade.

## Fluxos de trabalho {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Os** fluxos de trabalho são uma maneira útil de automatizar seus processos de importação. Quer você importe dados de um arquivo local ou de um SFTP, eles permitem padronizar seus procedimentos de gestão de dados.

Com os workflows, as operações de importação e exportação podem ser repetidas automaticamente de acordo com uma programação, por exemplo para automatizar a troca de dados entre vários sistemas de informações.

Para obter mais informações, consulte [esta seção](../../platform/using/import-export-workflows.md).

## Importações e exportações genéricas {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

Além disso, o Campaign Classic fornece **importações e exportações genéricas** que permitem criar trabalhos ocasionais de importação ou exportação.

As importações e exportações são configuradas em modelos dedicados, que você pode configurar e usar para iniciar e monitorar trabalhos de importação e exportação.

Para obter mais informações sobre importações e exportações genéricas, consulte [esta seção](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>As importações e exportações genéricas devem ser utilizadas apenas para operações ocasionais. Para garantir a consistência dos dados e melhorar a eficiência, é recomendável executar as operações de importação e exportação usando workflows.

## Criptografia e compactação de dados {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

O Campaign Classic permite importar arquivos compactados ou criptografados e exportar arquivos compactados ou criptografados.

Essas operações são executadas em workflows, aplicando estágios de pré-processamento aos dados que você deseja aproveitar.

Para saber mais, consulte estas seções:

* [Descompactando ou descriptografando um arquivo](../../platform/using/unzip-decrypt.md)
* [Compactação ou criptografia de um arquivo](../../platform/using/zip-encrypt.md)

## Práticas recomendadas e solução de problemas {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

Diversas [práticas recomendadas](../../platform/using/import-export-best-practices.md) devem ser seguidas ao executar operações de importação e exportação para garantir a consistência dos dados no banco de dados e evitar erros comuns durante a atualização ou exportação.

Além disso, recomendações e problemas comuns relacionados ao uso de servidores SFTP estão disponíveis em [esta seção](../../platform/using/sftp-server-usage.md).
