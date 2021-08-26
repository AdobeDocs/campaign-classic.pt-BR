---
product: campaign
title: Restrição da visualização de PII
description: Restrição da visualização de PII
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 0f32d62d-a10a-4feb-99fe-4679b98957d4
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 3%

---

# Restringir visualização de IP{#restricting-pii-view}

![](../../assets/v7-only.svg)

## Visão geral {#overview}

Alguns clientes precisam de usuários de marketing para acessar registros de dados, mas não desejam que eles vejam informações de identificação pessoal (PII), como nome, sobrenome ou endereço de email. A Adobe Campaign propõe uma maneira de proteger a privacidade e evitar que os dados sejam utilizados incorretamente pelos operadores de campanha regulares.

## Implementação {#implementation}

Um novo atributo que pode ser aplicado a qualquer elemento ou atributo foi adicionado aos schemas, complementa o atributo existente **[!UICONTROL visibleIf]** . Este atributo é: **[!UICONTROL accessibleIf]** . Ao conter uma expressão XTK relacionada ao contexto do usuário atual, ela pode aproveitar **[!UICONTROL HasNamedRight]** ou **[!UICONTROL $(login)]** , por exemplo.

Você pode encontrar uma amostra de uma extensão de schema de recipient que mostra este uso abaixo:

```
<srcSchema desc="Recipient table (profiles" entitySchema="xtk:srcSchema" extendedSchema="nms:recipient"
           img="nms:recipient.png" label="Recipients" labelSingular="Recipient"
           name="recipient" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Recipient table (profiles" img="nms:recipient.png" label="Recipients"
           labelSingular="Recipient" name="recipient">
    <attribute name="firstName" accessibleIf="$(login)=='admin'"/>
    <attribute name="lastName" visibleIf="$(login)=='admin'"/>
    <attribute name="email" accessibleIf="$(login)=='admin'"/>
  </element>
</srcSchema>
```

As principais propriedades são:

* **[!UICONTROL visibleIf]** : oculta os campos dos metadados, portanto, eles não podem ser acessados em uma visualização de esquema, ou seleção de coluna, ou em um construtor de expressões. Mas isso não oculta dados. Se o nome do campo for inserido manualmente em uma expressão, o valor será exibido.
* **[!UICONTROL accessibleIf]** : oculta os dados (substituindo-os por valores vazios) da consulta resultante. Se visibleIf estiver vazio, ele terá a mesma expressão que **[!UICONTROL accessibleIf]** .

Estas são as consequências do uso desse atributo no Campaign:

* Os dados não serão mostrados usando o editor de query genérico no console,
* Os dados não estarão visíveis nas listas de visão geral e de registro (console).
* Os dados se tornarão somente leitura na exibição detalhada.
* Os dados só serão utilizáveis em filtros (o que significa que, usando algumas estratégias de dicotomia, você ainda pode adivinhar valores).
* Qualquer expressão que é criada usando um campo restrito é restrita a: lower(@email) torna-se acessível como @email.
* Em um workflow, é possível adicionar a coluna restrita ao público alvo como uma coluna extra da transição, mas ela ainda fica inacessível aos usuários do Adobe Campaign.
* Ao armazenar a população direcionada em um grupo (lista), as características dos campos armazenados são as mesmas da fonte de dados.
* Por padrão, os dados não são acessíveis ao código JS.

## Recomendações {#recommendations}

Em cada delivery, os endereços de email são copiados nas tabelas **[!UICONTROL broadLog]** e **[!UICONTROL forecastLog]**: consequentemente, esses campos também precisam ser protegidos.

Abaixo está uma amostra da extensão da tabela de log para implementar isso:

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:broadLogRcp" img="nms:broadLog.png"
           label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema desc="Delivery messages being prepared." entitySchema="xtk:srcSchema"
           extendedSchema="nms:tmpBroadcast" img="" label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Delivery messages being prepared." label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:excludeLogRcp" img="nms:excludeLog.png"
           label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:excludeLog.png" label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
```

>[!NOTE]
>
>Esta restrição aplica-se a utilizadores não técnicos: um usuário técnico, com permissões relacionadas, poderá recuperar dados. Portanto, esse método não é 100% seguro.
