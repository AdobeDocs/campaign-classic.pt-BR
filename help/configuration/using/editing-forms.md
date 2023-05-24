---
product: campaign
title: Editar formulários
description: Editar formulários
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1698'
ht-degree: 2%

---


# Editar formulários{#editing-forms}



## Visão geral

Profissionais de marketing e operadores usam formulários de entrada para criar, modificar e visualizar registros. O Forms mostra uma representação visual das informações.

É possível criar e modificar formulários de entrada:

* Você pode modificar os formulários de entrada de fábrica fornecidos por padrão. Os formulários de entrada de fábrica são baseados nos schemas de dados de fábrica.
* Você pode criar formulários de entrada personalizados, com base em esquemas de dados definidos por você.

Forms são entidades de `xtk:form` tipo. É possível exibir a estrutura do formulário de entrada na `xtk:form` esquema. Para exibir esse esquema, escolha **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** no menu. Leia mais sobre [estrutura do formulário](form-structure.md).

Para acessar formulários de entrada, escolha **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** no menu:

![](assets/d_ncs_integration_form_arbo.png)

Para criar formulários, edite o conteúdo XML no editor XML:

![](assets/d_ncs_integration_form_edit.png)

[Leia mais](form-structure.md#formatting).

Para visualizar um formulário, clique no link **[!UICONTROL Preview]** guia:

![](assets/d_ncs_integration_form_preview.png)

## Tipos de formulário

É possível criar diferentes tipos de formulários de entrada. O tipo de formulário determina como os usuários navegam pelo formulário:

* Tela do console

   Este é o tipo de formulário padrão. O formulário é composto por uma única página.

   ![](assets/console_screen_form.png)

* Gerenciamento de conteúdo

   Use este tipo de formulário para gerenciamento de conteúdo. Veja isto [caso de uso](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Assistente

   Este formulário inclui várias telas flutuantes ordenadas em sequências específicas. Os usuários navegam de uma tela para outra. [Leia mais](form-structure.md#wizards).

* Caixa de ícones

   Este formulário inclui várias páginas. Para navegar no formulário, os usuários selecionam ícones à esquerda do formulário.

   ![](assets/iconbox_form_preview.png)

* Notebook

   Este formulário inclui várias páginas. Para navegar pelo formulário, os usuários selecionam guias na parte superior do formulário.

   ![](assets/notebook_form_preview.png)

* Painel vertical

   Este formulário mostra uma árvore de navegação.

* Painel horizontal

   Este formulário mostra uma lista de itens.

## Containers

Nos formulários, você pode usar contêineres para várias finalidades:

* Organizar conteúdo em formulários
* Definir acesso a campos de entrada
* Aninhar formulários em outros formulários

[Leia mais](form-structure.md#containers).

### Organizar conteúdo

Usar contêineres para organizar o conteúdo em formulários:

* Você pode agrupar campos em seções.
* É possível adicionar páginas a formulários de várias páginas.

Para inserir um container, use o `<container>` elemento. [Leia mais](form-structure.md#containers).

#### Agrupar campos

Use containers para agrupar campos de entrada em seções organizadas.

Para inserir uma seção em um formulário, use este elemento: `<container type="frame">`. Como opção, para adicionar um título de seção, use o `label` atributo.

Sintaxe: `<container type="frame" label="`*section_title*`"> […] </container>`

Neste exemplo, um container define o **Criação** seção, que inclui a **[!UICONTROL Created by]** e **[!UICONTROL Name]** campos de entrada:

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### Adicionar páginas a formulários de várias páginas

Para formulários de várias páginas, use um container para criar uma página de formulário.

Este exemplo mostra contêineres para o **Geral** e **Detalhes** páginas de um formulário:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Definir acesso a campos

Use containers para definir o que está visível e para definir o acesso a campos. Você pode ativar ou desativar grupos de campos.

### Aninhar formas

Use contêineres para aninhar formulários em outros formulários. [Leia mais](#add-pages-to-multipage-forms).

## Referências a imagens

Para localizar imagens, escolha **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** no menu.

Para associar uma imagem a um elemento no formulário, por exemplo, um ícone, é possível adicionar uma referência a uma imagem. Use o `img` atributo, por exemplo, no campo `<container>` elemento.

Sintaxe: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

Este exemplo mostra referências à variável `book.png` e `detail.png` imagens do `ncm` namespace:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

Essas imagens são usadas para ícones nos quais os usuários clicam para navegar em um formulário de várias páginas:

![](assets/nested_forms_preview.png)


## Criar um formulário simples {#create-simple-form}

Para criar um formulário, siga estas etapas:

1. No menu, escolha **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**.
1. Clique em **[!UICONTROL New]** no canto superior direito da lista.

   ![](assets/input-form-create-1.png)

1. Especifique as propriedades do formulário:

   * Especifique o nome do formulário e o namespace.

      O nome do formulário e o namespace podem corresponder ao esquema de dados relacionado.  Este exemplo mostra um formulário para o `cus:order` esquema de dados:

      ```xml
      <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
        […]
      </form>
      ```

      Como alternativa, você pode especificar explicitamente o schema de dados na `entity-schema` atributo.

      ```xml
      <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
        […]
      </form>
      ```

   * Especifique o rótulo a ser exibido no formulário.
   * Opcionalmente, especifique o tipo de formulário. Se você não especificar um tipo de formulário, o tipo de tela do console será usado por padrão.

      ![](assets/input-form-create-2.png)

      Se estiver criando um formulário multipáginas, você poderá omitir o tipo de formulário no `<form>` e especifique o tipo em um contêiner.

1. Clique em **[!UICONTROL Save]**.

1. Insira os elementos de formulário.

   Por exemplo, para inserir um campo de entrada, use o `<input>` elemento. Defina o `xpath` atributo para a referência de campo como uma expressão XPath. [Leia mais](schema-structure.md#referencing-with-xpath).

   Este exemplo mostra campos de entrada com base na variável `nms:recipient` esquema.

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. Se o formulário for baseado em um tipo de esquema específico, você poderá pesquisar os campos deste esquema:

   1. Clique em **[!UICONTROL Insert]** > **[!UICONTROL Document fields]**.

      ![](assets/input-form-create-4.png)

   1. Selecione o campo e clique em **[!UICONTROL OK]**.

      ![](assets/input-form-create-5.png)

1. Opcionalmente, especifique o editor de campos.

   Um editor de campo padrão está associado a cada tipo de dados:
   * Para um campo do tipo data, o formulário mostra um calendário de entrada.
   * Para um campo do tipo lista discriminada, o formulário mostra uma lista de seleção.

   Você pode usar estes tipos de editor de campo:

   | Editor de campo | Atributo de formulário |
   | --- | --- |
   | Botão de opção | `type="radiobutton"` |
   | Caixa de seleção | `type="checkbox"` |
   | Editar árvore | `type="tree"` |

   Leia mais sobre [controles da lista de memória](form-structure.md#memory-list-controls).

1. Opcionalmente, defina o acesso aos campos:

   | Elemento | Atributo | Descrição |
   | --- | --- | --- |
   | `<input>` | `read-only="true"` | Fornece acesso somente leitura a um campo |
   | `<container>` | `type="visibleGroup" visibleIf="`*edit-expr*`"` | Exibe condicionalmente um grupo de campos |
   | `<container>` | `type="enabledGroup" enabledIf="`*edit-expr*`"` | Habilita condicionalmente um grupo de campos |

   Exemplo:

   ```xml
   <container type="enabledGroup" enabledIf="@gender=1">
     […]
   </container>
   <container type="enabledGroup" enabledIf="@gender=2">
     […]
   </container>
   ```

1. Opcionalmente, use containers para agrupar campos em seções.

   ```xml
   <container type="frame" label="Name">
      <input xpath="@firstName"/>
      <input xpath="@lastName"/>
   </container>
   <container type="frame" label="Contact details">
      <input xpath="@email"/>
      <input xpath="@phone"/>
   </container>
   ```

   ![](assets/input-form-create-3.png)

## Criar um formulário multipáginas {#create-multipage-form}

É possível criar formulários de várias páginas. Também é possível aninhar formulários em outros formulários.

### Criar um `iconbox` formulário

Use o `iconbox` tipo de formulário para mostrar ícones à esquerda do formulário, que levam os usuários a páginas diferentes no formulário.

![](assets/iconbox_form_preview.png)

Para alterar o tipo de um formulário existente para `iconbox`, siga estas etapas:

1. Altere o `type` atributo de `<form>` elemento para `iconbox`:

   ```xml
   <form […] type="iconbox">
   ```

1. Defina um container para cada página de formulário:

   1. Adicionar um `<container>` elemento como filho de `<form>` elemento.
   1. Para definir um rótulo e uma imagem para o ícone, use o `label` e `img` atributos.

      ```xml
      <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="iconbox" xtkschema="xtk:form">
          <container img="xtk:properties.png" label="General">
              <input xpath="@label"/>
              <input xpath="@name"/>
              […]
          </container>
          <container img="nms:msgfolder.png" label="Details">
              <input xpath="@address"/>
              […]
          </container>
          <container img="nms:supplier.png" label="Services">
              […]
          </container>
      </form>
      ```
   Como alternativa, remova a variável `type="frame"` atributo do existente `<container>` elementos.

### Criar um formulário de bloco de anotações

Use o `notebook` tipo de formulário para mostrar guias na parte superior do formulário, que levam os usuários a páginas diferentes.

![](assets/notebook_form_preview.png)

Para alterar o tipo de um formulário existente para `notebook`, siga estas etapas:

1. Altere o `type` atributo de `<form>` elemento para `notebook`:

   ```xml
   <form […] type="notebook">
   ```

1. Adicione um container para cada página de formulário:

   1. Adicionar um `<container>` elemento como filho de `<form>` elemento.
   1. Para definir o rótulo e a imagem do ícone, use o `label` e `img` atributos.

   ```xml
     <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="notebook" xtkschema="xtk:form">
         <container label="General">
             <input xpath="@label"/>
             <input xpath="@name"/>
             […]
         </container>
         <container label="Details">
             <input xpath="@address"/>
             […]
         </container>
         <container label="Services">
             […]
         </container>
     </form>
   ```

   Como alternativa, remova a variável `type="frame"` atributo do existente `<container>` elementos.

### Aninhar formas

É possível aninhar formulários em outros formulários. Por exemplo, você pode aninhar formulários de bloco de anotações em formulários de caixa de ícones.

O nível de aninhamento controla a navegação. Os usuários podem detalhar os subformulários.

Para aninhar um formulário em outro formulário, insira um `<container>` elemento e defina o `type` ao tipo de formulário. Para o formulário de nível superior, é possível definir o tipo de formulário em um contêiner externo ou no `<form>` elemento.

### Exemplo

Este exemplo mostra um formulário complexo:

* O formulário de nível superior é um formulário de caixa de ícones. Este formulário inclui dois contêineres rotulados **Geral** e **Detalhes**.

   Como resultado, o formulário externo mostra a **Geral** e **Detalhes** páginas no nível superior. Para acessar essas páginas, os usuários clicam nos ícones à esquerda do formulário.

* O subformulário é um formulário de bloco de anotações aninhado dentro do **Geral** recipiente. O subformulário inclui dois contêineres rotulados **Nome** e **Contato**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

Como resultado, a **Geral** mostra a página do formulário externo **Nome** e **Contato** guias.

![](assets/nested_forms_preview.png)

Para aninhar um formulário em outro formulário, insira um `<container>` elemento e defina o `type` ao tipo de formulário. Para o formulário de nível superior, é possível definir o tipo de formulário em um contêiner externo ou no `<form>` elemento.

### Exemplo

Este exemplo mostra um formulário complexo:

* O formulário de nível superior é um formulário de caixa de ícones. Este formulário inclui dois contêineres rotulados **Geral** e **Detalhes**.

   Como resultado, o formulário externo mostra a **Geral** e **Detalhes** páginas no nível superior. Para acessar essas páginas, os usuários clicam nos ícones à esquerda do formulário.

* O subformulário é um formulário de bloco de anotações aninhado dentro do **Geral** recipiente. O subformulário inclui dois contêineres rotulados **Nome** e **Contato**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

Como resultado, a **Geral** mostra a página do formulário externo **Nome** e **Contato** guias.

![](assets/nested_forms_preview.png)



## Modificar um formulário de entrada de fábrica {#modify-factory-form}

Para modificar um formulário de fábrica, siga estas etapas:

1. Modifique o formulário de entrada de fábrica:

   1. No menu, escolha **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**.
   1. Selecione e modifique um formulário de entrada.

   Você pode estender esquemas de dados de fábrica, mas não pode estender formulários de entrada de fábrica. Recomendamos que você modifique os formulários de entrada de fábrica diretamente sem recriá-los. Durante as atualizações de software, as modificações nos formulários de entrada de fábrica são mescladas com as atualizações. Se a mesclagem automática falhar, você poderá resolver os conflitos. [Leia mais](../../production/using/upgrading.md#resolving-conflicts).

   Por exemplo, se você estender um schema de fábrica com um campo adicional, poderá adicionar esse campo ao formulário de fábrica relacionado.

## Validar formulários {#validate-forms}

É possível incluir controles de validação em formulários.

### Conceder acesso somente leitura aos campos

Para conceder acesso somente leitura a um campo, use o `readOnly="true"` atributo. Por exemplo, talvez você queira mostrar a chave primária de um registro, mas com acesso somente leitura. [Leia mais](form-structure.md#non-editable-fields).

Neste exemplo, a chave primária (`iRecipientId`) do `nms:recipient` o esquema é exibido no acesso somente leitura:

```xml
<value xpath="@iRecipientId" readOnly="true"/>
```

### Verificar campos obrigatórios

Você pode verificar as informações obrigatórias:

* Use o `required="true"` atributo para os campos obrigatórios.
* Use o `<leave>` para verificar esses campos e mostrar mensagens de erro.

Neste exemplo, o endereço de email é obrigatório e uma mensagem de erro será exibida se o usuário não tiver fornecido essas informações:

```xml
<input xpath="@email" required="true"/>
<leave>
  <check expr="@email!=''">
    <error>The email address is required.</error>
  </check>
</leave>
```

Leia mais sobre [campos de expressão](form-structure.md#expression-field) e [contexto de formulário](form-structure.md#context-of-forms).

### Validar valores

Você pode usar chamadas SOAP do JavaScript para validar dados de formulário do Console. Use essas chamadas para validação complexa, por exemplo, para verificar um valor em relação a uma lista de valores autorizados. [Leia mais](form-structure.md#soap-methods).

1. Crie uma função de validação em um arquivo JS.

   Exemplo:

   ```js
   function nms_recipient_checkValue(value)
   {
     logInfo("checking value " + value)
     if (…)
     {
       logError("Value " + value + " is not valid")
     }
     return 1
   }
   ```

   Neste exemplo, a função é chamada de `checkValue`. Esta função é usada para verificar a `recipient` tipo de dados no `nms` namespace. O valor que está sendo verificado é registrado em log. Se o valor não for válido, uma mensagem de erro será registrada. Se o valor for válido, o valor 1 será retornado.

   Você pode usar o valor retornado para modificar o formulário.

1. No formulário, adicione a variável `<soapCall>` elemento para o `<leave>` elemento.

   Neste exemplo, uma chamada SOAP é usada para validar o `@valueToCheck` string:

   ```xml
   <form name="recipient" (…)>
   (…)
     <leave>
       <soapCall name="checkValue" service="nms:recipient">
         <param exprIn="@valueToCheck" type="string"/>
       </soapCall>
     </leave>
   </form>
   ```

   Neste exemplo, a variável `checkValue` e o `nms:recipient` serviço são usados:

   * O serviço é o namespace e o tipo de dados.
   * O método é o nome da função. O nome diferencia maiúsculas e minúsculas.

   A chamada é executada de forma síncrona.

   Todas as exceções são exibidas. Se você usar o `<leave>` elemento, os usuários não poderão salvar o formulário até que as informações inseridas sejam validadas.

Este exemplo mostra como você pode fazer chamadas de serviço de dentro de formulários:

```xml
<enter>
  <soapCall name="client" service="c4:ybClient">
    <param exprIn="@id" type="string"/>
    <param type="boolean" xpathOut="/tmp/@count"/>
  </soapCall>
</enter>
```

Neste exemplo, a entrada é uma ID, que é uma chave primária. Quando os usuários preenchem o formulário dessa ID, é feita uma chamada SOAP com essa ID como parâmetro de entrada. A saída é um booleano gravado neste campo: `/tmp/@count`. Você pode usar esse booleano dentro do formulário. Leia mais sobre [contexto de formulário](form-structure.md#context-of-forms).
