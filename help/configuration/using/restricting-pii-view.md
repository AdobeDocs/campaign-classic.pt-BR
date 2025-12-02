---
product: campaign
title: Restringir visualização de IP
description: Saiba como restringir a visualização de IP
feature: PI
role: Developer
exl-id: 0f32d62d-a10a-4feb-99fe-4679b98957d4
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 2%

---

# Restringir visualização de IP{#restricting-pii-view}

## Visão geral {#overview}

Alguns clientes precisam que os usuários de marketing consigam acessar registros de dados, mas não desejam que eles vejam as Informações de identificação pessoal (PII), como nome, sobrenome ou endereço de email. O Adobe Campaign propõe uma maneira de proteger a privacidade e impedir que os dados sejam usados indevidamente por operadores de campanha regulares.

## Implementação {#implementation}

Um novo atributo que pode ser aplicado a qualquer elemento ou atributo foi adicionado aos esquemas, ele complementa o atributo existente **[!UICONTROL visibleIf]**. Este atributo é: **[!UICONTROL accessibleIf]** . Ao conter uma expressão XTK relacionada ao contexto de usuário atual, ela pode aproveitar **[!UICONTROL HasNamedRight]** ou **[!UICONTROL $(login)]** , por exemplo.

Você pode encontrar abaixo um exemplo de extensão de schema de recipient que mostra esse uso:

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

* **[!UICONTROL visibleIf]** : oculta os campos dos metadados, portanto, eles não podem ser acessados em uma exibição de esquema, seleção de coluna ou um construtor de expressões. Mas isso não oculta dados. Se o nome do campo for inserido manualmente em uma expressão, o valor será exibido.
* **[!UICONTROL accessibleIf]** : oculta os dados (substituindo-os por valores vazios) da consulta resultante. Se visibleIf estiver vazio, ele terá a mesma expressão que **[!UICONTROL accessibleIf]** .

Estas são as consequências do uso desse atributo no Campaign:

* Os dados não serão exibidos usando o editor de query genérico no console,
* Os dados não estarão visíveis nas listas de visão geral e de registros (console).
* Os dados se tornarão somente leitura na exibição detalhada.
* Os dados só serão utilizáveis dentro de filtros (o que significa que, usando algumas estratégias de dicotomia, ainda é possível adivinhar valores).
* Qualquer expressão criada usando um campo restrito se torna restrita a: lower(@email) se torna tão acessível quanto @email.
* Em um workflow, é possível adicionar a coluna restrita à população direcionada como uma coluna extra da transição, mas ela ainda estará inacessível aos usuários do Adobe Campaign.
* Ao armazenar a população direcionada em um grupo (lista), as características dos campos armazenados são as mesmas da fonte de dados.
* Os dados não estão acessíveis ao código JS por padrão.

>[!IMPORTANT]
>
>O uso do atributo **accessibleIf** em parâmetros críticos (como aqueles em chaves compostas) pode resultar em erros para usuários que não têm permissão para ler os dados devido a dados ocultos. Isso pode levar a falhas de consulta ou comportamento inesperado. Garantir que os parâmetros essenciais estejam acessíveis para evitar interrupções.

## Recomendações {#recommendations}

Em cada delivery, endereços de email são copiados nas tabelas **[!UICONTROL broadLog]** e **[!UICONTROL forecastLog]**: como consequência, esses campos também precisam ser protegidos.

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
>Essa restrição se aplica a usuários não técnicos: um usuário técnico, com permissões relacionadas, poderá recuperar dados. Portanto, esse método não é 100% seguro.
