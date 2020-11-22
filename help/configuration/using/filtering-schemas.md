---
solution: Campaign Classic
product: campaign
title: Schemas de filtragem
description: Schemas de filtragem
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---


# Schemas de filtragem{#filtering-schemas}

## Filtros do sistema {#system-filters}

Você pode filtrar o acesso do schema a usuários específicos, dependendo de suas permissões. Os filtros do sistema permitem gerenciar as permissões de leitura e gravação de entidades detalhadas em schemas, usando os parâmetros **readAccess** e **writeAccess** .

>[!NOTE]
>
>Esta restrição aplica-se apenas a utilizadores não técnicos: um usuário técnico, com permissões relacionadas ou usando um fluxo de trabalho, poderá recuperar e atualizar dados.

* **readAccess**: fornece acesso somente leitura aos dados do schema.

   **Aviso** - Todas as tabelas vinculadas devem ser definidas com a mesma restrição. Essa configuração pode afetar o desempenho.

* **writeAccess**: fornece acesso de gravação aos dados do schema.

Esses filtros são inseridos no nível do **elemento** principal dos schemas e, como mostrado nos exemplos a seguir, podem ser formados para restringir o acesso.

* Restringir permissões de GRAVAÇÃO

   Aqui, o filtro é usado para proibir permissões de GRAVAÇÃO no schema para operadores sem a permissão ADMINISTRAÇÃO. Isso significa que somente os administradores terão permissões de gravação em entidades descritas por esse schema.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* Restringir permissões de LEITURA e GRAVAÇÃO:

   Aqui, o filtro é usado para proibir permissões de LEITURA e GRAVAÇÃO no schema para todos os operadores. Somente a conta **interna** , representada pela expressão &quot;$(loginId)!=0&quot;, tem essas permissões.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   Os possíveis valores de atributo **expr** usados para definir a condição são VERDADEIRO ou FALSO.

>[!NOTE]
>
>Se nenhum filtro for especificado, todos os operadores terão permissões de leitura e gravação no schema.

## Proteger schemas integrados {#protecting-built-in-schemas}

Por padrão, os schemas incorporados só podem ser acessados com permissões de GRAVAÇÃO para operadores com direitos de ADMINISTRAÇÃO:

* ncm:publicação
* nl:monitoramento
* nms:calendário
* xtk:builder
* xtk:conexões
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusion
* xtk:image
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operadorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:strings
* xtk:xslt

>[!IMPORTANT]
>
>As permissões de LEITURA e GRAVAÇÃO do schema **xtk:sessionInfo** só podem ser acessadas pela conta interna de uma instância do Adobe Campaign.

## Modificação de filtros do sistema de schemas integrados {#modifying-system-filters-of-built-in-schemas}

Você ainda pode modificar os filtros do sistema dos schemas prontos para uso que são protegidos por padrão devido a problemas de compatibilidade com versões anteriores.

>[!NOTE]
>
>No entanto, o Adobe recomenda que você não modifique os parâmetros padrão para garantir a segurança ideal.

1. Crie uma extensão para o schema em questão ou abra uma extensão existente.
1. Adicione um elemento filho **`<sysfilter name="<filter name>" _operation="delete"/>`** no elemento principal para excluir a aplicação do filtro abaixo do mesmo no schema da origem.
1. Se desejar, adicione um novo filtro, conforme detalhado em filtros [](#system-filters)do sistema.

