---
product: campaign
title: Esquemas de filtragem
description: Esquemas de filtragem
feature: Custom Resources
role: Developer
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
TQID: https://experienceleague.adobe.com/-EcD9suVVxnqRIgsLdaADQ7T0CIMw1CzSnoqJqNe8xs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2:
  - id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 387
ht-degree: 1%

---

# Esquemas de filtro{#filtering-schemas}

## Filtros do sistema {#system-filters}

Você pode filtrar o acesso ao esquema para usuários específicos, dependendo de suas permissões. Os filtros de sistema permitem gerenciar as permissões de leitura e gravação de entidades detalhadas em esquemas, usando os parâmetros **readAccess** e **writeAccess**.

>[!NOTE]
>
>Essa restrição se aplica somente a usuários não técnicos: um usuário técnico, com permissões relacionadas ou usando um fluxo de trabalho, poderá recuperar e atualizar dados.

* **readAccess**: fornece acesso somente leitura a dados de esquema.

  **Aviso** - Todas as tabelas vinculadas devem ser definidas com a mesma restrição. Essa configuração pode afetar o desempenho.

* **writeAccess**: fornece acesso de gravação a dados de esquema.

Esses filtros são inseridos no nível **element** principal dos esquemas e, como mostrado nos exemplos a seguir, podem ser formados para restringir o acesso.

* Restringir permissões de GRAVAÇÃO

  Aqui, o filtro é usado para não permitir permissões WRITE no schema para operadores sem a permissão ADMINISTRATION. Isso significa que somente administradores terão permissões de gravação nas entidades descritas por esse esquema.

  ```
  <sysFilter name="writeAccess">      
   <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
  </sysFilter>
  ```

* Restringir permissões de LEITURA e GRAVAÇÃO:

  Aqui, o filtro é usado para não permitir permissões de LEITURA e GRAVAÇÃO no esquema para todos os operadores. Somente a conta **interna**, representada pela expressão &quot;$(loginId)!=0&quot;, tem essas permissões.

  ```
  <sysFilter name="readAccess"> 
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  
  <sysFilter name="writeAccess">  
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  ```

  Possíveis valores de atributo **expr** usados para definir a condição são TRUE ou FALSE.

>[!NOTE]
>
>Se nenhum filtro for especificado, todos os operadores terão permissões de leitura e gravação no esquema.

## Proteger esquemas integrados {#protecting-built-in-schemas}

Por padrão, os esquemas integrados só podem ser acessados com permissões WRITE para operadores com direitos ADMINISTRATION:

* ncm:publishing
* nl:monitoring
* nms:calendar
* xtk:builder
* xtk:connections
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
>As permissões de LEITURA e GRAVAÇÃO para o esquema **xtk:sessionInfo** só podem ser acessadas pela conta interna de uma instância do Adobe Campaign.

## Modificar filtros de sistema de esquemas internos {#modifying-system-filters-of-built-in-schemas}

Você ainda pode modificar os filtros de sistema dos esquemas prontos para uso que são protegidos por padrão devido a problemas de compatibilidade com versões mais antigas.

>[!NOTE]
>
>No entanto, a Adobe recomenda que você não modifique os parâmetros padrão para garantir a segurança ideal.

1. Crie uma extensão para o esquema relacionado ou abra uma extensão existente.
1. Adicione um elemento filho **`<sysfilter name="<filter name>" _operation="delete"/>`** no elemento principal para excluir a aplicação do filtro sob o mesmo no esquema de origem.
1. Se desejar, você poderá adicionar um novo filtro, conforme detalhado em [Filtros de sistema](#system-filters).
