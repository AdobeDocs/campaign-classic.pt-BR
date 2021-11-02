---
product: campaign
title: Introdução à importação e exportação de dados
description: Saiba mais sobre importação e exportação de dados no Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d6055d97-75fc-4ed7-89bd-8336157454eb
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: ht
source-wordcount: '326'
ht-degree: 100%

---

# Introdução à importação e exportação de dados {#get-started-data-import-export}

![](../../assets/common.svg)

O Adobe Campaign Classic fornece recursos de gerenciamento de dados que permitem importar e exportar dados. Essas operações podem ser efetuadas utilizando workflows ou importações e exportações genéricas.

>[!IMPORTANT]
>
>Lembre-se dos limites de armazenamento SFTP, armazenamento do banco de dados e perfil ativo conforme o contrato do Adobe Campaign ao usar essa funcionalidade.

## Workflows {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Os Workflows** são uma maneira útil de automatizar os processos de importação. Ao importar dados de um arquivo local ou de um SFTP, você pode padronizar os procedimentos de gerenciamento de dados.

Com os workflows, as operações de importação e exportação de dados podem ser repetidas automaticamente de acordo com uma programação, por exemplo, para automatizar a troca de dados entre vários sistemas de informações.

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

O Campaign Classic permite importar e exportar arquivos compactados ou criptografados.

Essas operações são executadas em workflows, aplicando estágios de pré-processamento aos dados que você deseja usar.

Para saber mais, consulte estas seções:

* [Descompactar ou descriptografar um arquivo](../../platform/using/unzip-decrypt.md)
* [Compactar ou criptografar um arquivo](../../platform/using/zip-encrypt.md)

## Práticas recomendadas e solução de problemas {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

Você deve seguir várias [práticas recomendadas](../../platform/using/import-export-best-practices.md) ao executar operações de importação e exportação para garantir a consistência dos dados no banco de dados e evitar erros comuns durante as operações de atualização ou exportação.

Além disso, recomendações e problemas comuns relacionados ao uso de servidores SFTP estão disponíveis [nesta seção](../../platform/using/sftp-server-usage.md).
