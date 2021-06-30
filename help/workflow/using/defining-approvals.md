---
product: campaign
title: Definição de aprovações
description: As aprovações permitem que os operadores tomem decisões que regem um workflow ou confirmem sua execução contínua
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 4d413d51-ae5d-4e5e-bfaf-4160a6075281
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '840'
ht-degree: 100%

---

# Definição de aprovações {#defining-approvals}

As aprovações permitem que os operadores tomem decisões que regem um workflow ou confirmem sua execução contínua.

Uma mensagem é enviada a um grupo de operadores e o workflow aguarda uma resposta antes de continuar. O workflow não é interrompido e outras operações podem ocorrer. Por exemplo, pode haver várias aprovações simultâneas pendentes.

Uma aprovação pode conter várias opções para o operador escolher. No entanto, é possível restringir o número de escolhas a um para enviar uma tarefa a ser executada por um operador, como, por exemplo, a execução de target. O operador pode responder depois que a tarefa for executada (o processo então reinicia). O exemplo a seguir ilustra esses tipos de aprovações:

![](assets/validation-1.png)

Em operações, todos os estágios que exigem aprovação se baseiam no mesmo princípio.

![](assets/validation-1-in-op.png)

Exemplos de aprovação podem ser encontrados nesta [seção](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

Um operador pode responder de uma das duas formas seguintes: validação usando a página da Web vinculada na mensagem de email ou através do console.

>[!NOTE]
>
>Após salvar a resposta, ela não poderá ser modificada.

## Envio de emails {#sending-emails}

É possível receber uma mensagem de aprovação contendo um link para uma página da Web pela qual é possível responder. Para que o operador de target receba um email de aprovação, o endereço de email do operador deve ser completo. Se esse não for o caso, o operador deve usar o console para responder

A gestão de operador é apresentada nesta [seção](../../platform/using/access-management.md).

Emails de aprovação são enviados continuamente. O template do delivery padrão é **[!UICONTROL notifyAssignee]**: ele é salvo na pasta **[!UICONTROL Administration > Campaign management > Technical delivery templates]**. Esse cenário pode ser personalizado e também é recomendável fazer uma cópia e alterar templates para cada atividade.

Os deliveries criados por meio desse template são armazenados na pasta **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**.

## Aprovação através do console {#approval-via-the-console}

Em operações, os elementos a serem aprovados são exibidos no painel da campanha.

Para workflows técnicos, as tarefas que o usuário pode aprovar podem ser acessadas a partir da estrutura de árvore na pasta **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]**.

![](assets/validation-node.png)

## Grupos {#groups}

Uma aprovação é atribuída a um grupo de operadores, um único operador ou um conjunto de operadores selecionados por meio de uma condição de filtragem.

1. Para a forma mais simples de aprovação, a tarefa é concluída assim que um operador responde. Qualquer outro operador que tenta responder será notificado que outra pessoa já fez isso.
1. Para obter múltiplas aprovações, consulte [Aprovação múltipla](#multiple-approval).

Os grupos de operadores para aprovações devem ser designados como atribuições ou funções em vez de pessoas nomeadas. Por exemplo, um grupo &quot;Orçamento da campanha&quot; é preferível ao &quot;Grupo do Harry&quot;. Recomendamos ter pelo menos duas pessoas em um grupo que possam aprovar uma tarefa. Dessa forma, se uma pessoa estiver ausente, a outra poderá responder.

## Expirações {#expirations}

Expirações são transições específicas usadas em diferentes tipos de atividade e, particularmente, em aprovações. Você pode usar uma expiração para acionar uma ação após um determinado tempo sem resposta. Ela também pode ser usada para perseguir o workflow e atribuir uma aprovação a um grupo diferente.

A segunda guia nas propriedades da atividade de aprovação permite definir uma ou mais expirações. Na verdade, você pode definir vários tipos de expiração.

![](assets/expiration.png)

Para adicionar uma nova expiração, clique em **[!UICONTROL Add]**. Uma transição é adicionada a cada expiração criada. É possível:

* modificar os parâmetros típicos diretamente clicando em uma célula na lista (ou pressionando F2),
* ou edite a expressão clicando no botão **[!UICONTROL Detail...]**.

>[!NOTE]
>
>Não é necessário especificar uma ordem para as expirações, pois são processadas em ordem cronológica.

A opção **[!UICONTROL Do not terminate the task]** deixa a aprovação ativa quando o atraso é saturado. Esse modo possibilita gerenciar lembretes ao deixar a aprovação ativa: os operadores ainda podem responder. Essa opção é desabilitada por padrão, significando que a tarefa é considerada concluída na expiração e que os operadores não podem mais responder.

Você pode criar quatro tipos de expirações:

* **Delay after task start**: a expiração é calculada adicionando-se um período de tempo especificado à data em que a aprovação é ativada.
* **Delay after a given date**: a expiração é calculada adicionando um período a uma data especificada. 
* **Delay before a given date**: a expiração é calculada subtraindo-se um período de uma data especificada. 
* **Expiration calculated by script**: a expiração é calculada usando o JavaScript.

   O exemplo a seguir calcula uma expiração 24 horas antes da data em que um delivery é iniciado (identificada por **vars.deliveryId**):

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

## Aprovação múltipla {#multiple-approval}

A aprovação múltipla é um mecanismo que permite que todos os operadores de aprovação respondam. Uma transição é ativada para cada resposta.

A aprovação múltipla é útil para mecanismos de voto ou pesquisa. Você pode contar respostas e processar seu resultado após um determinado período ao adicionar um prazo.

## Direitos necessários {#required-rights}

Os operadores em um grupo devem ter pelo menos os seguintes direitos para poder responder a uma solicitação de aprovação:

* Permissões de gravação para workflow.
* Permissões de leitura e gravação para a pasta que contém as tarefas a serem aprovadas.

O grupo &#39;Execução de workflow&#39; tem esses direitos. Um operador adicionado a esse grupo tem os direitos de responder a uma solicitação de aprovação.
