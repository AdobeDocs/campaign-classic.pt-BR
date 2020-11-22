---
solution: Campaign Classic
product: campaign
title: Restrição da visualização de PII
description: Restrição da visualização de PII
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 3%

---


# Restrição da visualização de PII{#restricting-pii-view}

## Visão geral {#overview}

Alguns clientes precisam de usuários de marketing para poderem acessar registros de dados, mas não querem que eles vejam Informações pessoais identificáveis (PII), como nome, sobrenome ou endereço de email. A Adobe Campaign propõe uma maneira de proteger a privacidade e impedir que os dados sejam usados indevidamente pelos operadores regulares de campanhas.

## Implementação {#implementation}

Um novo atributo que pode ser aplicado a qualquer elemento ou atributo foi adicionado aos schemas, complementa o atributo existente **[!UICONTROL visibleIf]** . Este atributo é: **[!UICONTROL accessibleIf]** . Ao conter uma expressão XTK relacionada ao contexto do usuário atual, ela pode aproveitar **[!UICONTROL HasNamedRight]** ou **[!UICONTROL $(login)]** , por exemplo, .

Você pode encontrar um exemplo de uma extensão de schema de recipient que mostra este uso abaixo:

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

* **[!UICONTROL visibleIf]** : oculta os campos dos metadados, portanto eles não podem ser acessados em uma visualização de schema, ou seleção de coluna, ou em um criador de expressões. Mas isso não oculta dados, se o nome do campo for inserido manualmente em uma expressão, o valor será exibido.
* **[!UICONTROL accessibleIf]** : oculta os dados (substituindo-os por valores vazios) do query resultante. Se visibleIf estiver vazio, então obterá a mesma expressão que **[!UICONTROL accessibleIf]** .

Estas são as consequências do uso desse atributo na Campanha:

* Os dados não serão exibidos usando o editor de query genérico no console,
* Os dados não estarão visíveis nas listas de visão geral e lista de registro (console).
* Os dados se tornarão somente leitura em visualizações detalhadas.
* Os dados só serão utilizáveis em filtros (o que significa que, usando algumas estratégias de dicotomia, você ainda pode adivinhar valores).
* Qualquer expressão criada usando um campo restrito se torna restrita a: lower(@email) se torna tão acessível quanto @email.
* Em um fluxo de trabalho, você pode adicionar a coluna restrita à população direcionada como uma coluna extra da transição, mas ela ainda está inacessível aos usuários do Adobe Campaign.
* Ao armazenar a população direcionada em um grupo (lista), as características dos campos armazenados são as mesmas da fonte de dados.
* Por padrão, os dados não são acessíveis ao código JS.

## Recomendações {#recommendations}

Em cada delivery, os endereços de e-mail são copiados para as **[!UICONTROL broadLog]** tabelas **[!UICONTROL forecastLog]** e para as tabelas: consequentemente, esses campos também precisam de ser protegidos.

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
>Esta restrição aplica-se a utilizadores não técnicos: um usuário técnico, com permissões relacionadas, poderá recuperar dados. Este método não é, portanto, 100% seguro.

