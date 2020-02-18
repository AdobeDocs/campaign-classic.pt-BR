---
title: Esquemas de filtragem
seo-title: Esquemas de filtragem
description: Esquemas de filtragem
seo-description: null
page-status-flag: never-activated
uuid: 04a90785-3084-42fd-85af-77bc28687579
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 64d4c5b8-db0b-4287-8d30-4bf09878a401
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Esquemas de filtragem{#filtering-schemas}

## Filtros do sistema {#system-filters}

Você pode filtrar o acesso ao esquema para usuários específicos, dependendo de suas permissões. Os filtros do sistema permitem gerenciar as permissões de leitura e gravação de entidades detalhadas em esquemas, usando os parâmetros **readAccess** e **writeAccess** .

>[!NOTE]
>
>Esta restrição aplica-se apenas a utilizadores não técnicos: um usuário técnico, com permissões relacionadas ou usando um fluxo de trabalho, poderá recuperar e atualizar dados.

* **readAccess**: fornece acesso somente leitura aos dados do esquema.

   **Aviso** - Todas as tabelas vinculadas devem ser definidas com a mesma restrição. Essa configuração pode afetar o desempenho.

* **writeAccess**: fornece acesso de gravação aos dados do esquema.

Esses filtros são inseridos no nível do **elemento** principal dos esquemas e, como mostrado nos exemplos a seguir, podem ser formados para restringir o acesso.

* Restringir permissões de GRAVAÇÃO

   Aqui, o filtro é usado para proibir permissões de GRAVAÇÃO no esquema para operadores sem a permissão ADMINISTRAÇÃO. Isso significa que somente os administradores terão permissões de gravação em entidades descritas por este esquema.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* Restringir permissões de LEITURA e GRAVAÇÃO:

   Aqui, o filtro é usado para proibir permissões de LEITURA e GRAVAÇÃO no esquema para todos os operadores. Somente a conta **interna** , representada pela expressão &quot;$(loginId)!=0&quot;, tem essas permissões.

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
>Se nenhum filtro for especificado, todos os operadores terão permissões de leitura e gravação no esquema.

## Proteger esquemas integrados {#protecting-built-in-schemas}

Por padrão, os esquemas incorporados só são acessíveis com permissões de GRAVAÇÃO para operadores com direitos de ADMINISTRAÇÃO:

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
>As permissões de LEITURA e GRAVAÇÃO para o esquema **xtk:sessionInfo** só podem ser acessadas pela conta interna de uma instância do Adobe Campaign.

## Modificação de filtros do sistema de esquemas incorporados {#modifying-system-filters-of-built-in-schemas}

Você ainda pode modificar os filtros do sistema dos esquemas predefinidos que são protegidos por padrão devido a problemas de compatibilidade com versões anteriores.

>[!NOTE]
>
>No entanto, a Adobe recomenda que você não modifique os parâmetros padrão para garantir a segurança ideal.

1. Crie uma extensão para o esquema em questão ou abra uma extensão existente.
1. Adicione um elemento filho **`<sysfilter name="<filter name>" _operation="delete"/>`** no elemento principal para excluir a aplicação do filtro sob o mesmo no esquema de origem.
1. Se desejar, adicione um novo filtro, conforme detalhado nos filtros [](#system-filters)do sistema.

