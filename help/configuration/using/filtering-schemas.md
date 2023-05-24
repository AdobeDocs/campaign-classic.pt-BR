---
product: campaign
title: Esquemas de filtragem
description: Esquemas de filtragem
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# Esquemas de filtro{#filtering-schemas}

## Filtros do sistema {#system-filters}

Você pode filtrar o acesso ao esquema para usuários específicos, dependendo de suas permissões. Os filtros de sistema permitem gerenciar as permissões de leitura e gravação de entidades detalhadas em esquemas, usando **readAccess** e **writeAccess** parâmetros.

>[!NOTE]
>
>Essa restrição se aplica somente a usuários não técnicos: um usuário técnico, com permissões relacionadas ou usando um fluxo de trabalho, poderá recuperar e atualizar dados.

* **readAccess**: fornece acesso somente leitura aos dados do esquema.

   **Aviso** - Todas as tabelas vinculadas devem ser definidas com a mesma restrição. Essa configuração pode afetar o desempenho.

* **writeAccess**: fornece acesso de gravação aos dados do esquema.

Esses filtros são inseridos no local principal **element** dos esquemas e, conforme mostrado nos exemplos a seguir, podem ser formados para restringir o acesso.

* Restringir permissões de GRAVAÇÃO

   Aqui, o filtro é usado para não permitir permissões WRITE no schema para operadores sem a permissão ADMINISTRATION. Isso significa que somente administradores terão permissões de gravação nas entidades descritas por esse esquema.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* Restringir permissões de LEITURA e GRAVAÇÃO:

   Aqui, o filtro é usado para não permitir permissões de LEITURA e GRAVAÇÃO no esquema para todos os operadores. Somente o **interno** conta, representada pela expressão &quot;$(loginId)!=0&quot;, tem essas permissões.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   Possível **expr** os valores de atributo usados para definir a condição são TRUE ou FALSE.

>[!NOTE]
>
>Se nenhum filtro for especificado, todos os operadores terão permissões de leitura e gravação no esquema.

## Esquemas integrados do Protect {#protecting-built-in-schemas}

Por padrão, os esquemas integrados só podem ser acessados com permissões WRITE para operadores com direitos ADMINISTRATION:

* ncm:publicação
* nl:monitoring
* nms:calendar
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
* xtk:operatorGroup
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
>Permissões de LEITURA e GRAVAÇÃO para o **xtk:sessionInfo** são acessíveis somente pela conta interna de uma instância do Adobe Campaign.

## Modificar filtros de sistema de esquemas internos {#modifying-system-filters-of-built-in-schemas}

Você ainda pode modificar os filtros de sistema dos esquemas prontos para uso que são protegidos por padrão devido a problemas de compatibilidade com versões mais antigas.

>[!NOTE]
>
>No entanto, o Adobe recomenda que você não modifique os parâmetros padrão para garantir a segurança ideal.

1. Crie uma extensão para o esquema relacionado ou abra uma extensão existente.
1. Adicionar um elemento filho **`<sysfilter name="<filter name>" _operation="delete"/>`** no elemento principal para excluir a aplicação do filtro em same no schema origin.
1. Se desejar, você poderá adicionar um novo filtro, conforme detalhado em [Filtros do sistema](#system-filters).
