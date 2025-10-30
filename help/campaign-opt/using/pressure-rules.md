---
product: campaign
title: Regras de pressão
description: Saiba como trabalhar com regras de pressão no Adobe Campaign
role: User, Data Engineer
feature: Fatigue Management, Typology Rules, Campaigns
hide: true
hidefromtoc: true
exl-id: c23212f2-fdf8-4820-b389-546f7c84db27
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: ht
source-wordcount: '3335'
ht-degree: 100%

---

# Regras de pressão{#pressure-rules}

## Sobre fadiga de marketing {#about-marketing-fatigue}

A implementação do gerenciamento de regras de pressão permite evitar o excesso de solicitações de população no banco de dados, também conhecido como fadiga da marca. Para fazer isso, você pode definir um número máximo de mensagens por destinatário. Também permite implementar regras de arbitragem entre campanhas, para enviar a melhor mensagem para o público-alvo.

Regras de **pressão** para gerenciar a fadiga da marca, por exemplo: para restringir o número de cartas a serem enviadas a uma população, tanto para selecionar a comunicação que melhor corresponde aos interesses de um grupo de assinantes, quanto para evitar o envio de um SMS para um cliente insatisfeito etc.

As campanhas são selecionadas com base nos limites definidos e no peso da mensagem.

* Um limite é o número mais alto de entregas autorizado para um determinado destinatário dentro de um determinado período. Ele pode ser definido ou variável. Ele é definido ou calculado nas configurações da regra de tipologia. Consulte [Número máximo de mensagens](#maximum-number-of-messages).
* Os pesos das entregas permitem identificar entregas de alta prioridade dentro da estrutura do gerenciamento de pressão. As mensagens com o peso mais alto têm prioridade. Consulte [Peso da mensagem](#message-weight).

A arbitragem consiste em garantir que campanhas agendadas com peso maior do que a campanha em andamento não gerem solicitações de perfil excessivas: se esse for o caso, o perfil será excluído da entrega.

Os critérios de arbitragem (peso e/ou limite da mensagem) podem variar com base em dois tipos de informações:

* preferência de destinatário, que são informações declarativas: assinaturas de boletim informativo, status do destinatário (cliente ou cliente potencial),
* comportamento do destinatário: compras, links visitados etc.

A regra de arbitragem para definir mensagens qualificadas é aplicada durante o estágio de análise. Para cada destinatário e para o período em questão, a mensagem será enviada se a seguinte fórmula for verdadeira: **(number of messages sent) + (number of messages with a greater weight) &lt; threshold**.

Caso contrário, o destinatário será **[!UICONTROL Excluded by arbitration]**. Para obter mais informações, consulte [Exclusão após arbitragem](#exclusion-after-arbitration).

## Criação de uma regra de pressão {#creating-a-pressure-rule}

Para configurar arbitragem entre campanhas usando o Adobe Campaign, comece criando tipologias de campanha e definindo regras de tipologia vinculadas (regras de **Pressão**).

Para criar e configurar uma regra de tipologia **[!UICONTROL Pressure]**, siga estas etapas:

1. Na lista de regras de tipologia de campanha, clique no ícone **[!UICONTROL New]** acima da lista.

   ![](assets/campaign_opt_create_a_rule_01.png)

1. Na guia **[!UICONTROL General]** da nova regra, selecione uma regra de tipo **Pressure** e digite um nome e uma descrição para ela.

   ![](assets/campaign_opt_create_a_rule_02.png)

1. Altere a ordem de execução se necessário. Quando várias regras de tipologia são aplicadas como um conjunto **[!UICONTROL Typology]**, as regras de menor posição são aplicadas primeiro. Para obter mais informações, consulte [Ordem de execução](applying-rules.md#execution-order).
1. Na seção **[!UICONTROL Calculation parameters]**, defina uma frequência se quiser salvar o direcionamento para além da próxima execução diária de nova arbitragem. Para obter mais informações, consulte [Ajustar a frequência de cálculo](applying-rules.md#adjusting-calculation-frequency).
1. Clique na guia **[!UICONTROL Pressure]** e escolha o período do calendário durante o qual a regra de tipologia se aplica.

   ![](assets/campaign_opt_create_a_rule_03.png)

   A regra será aplicada a entregas cuja data de contato esteja incluída no período relacionado.

   >[!NOTE]
   >
   >As entregas agendadas só serão levadas em conta se a opção **[!UICONTROL Take the deliveries into account in the provisional calendar]** for selecionada. Para obter mais informações, consulte [Definição do período](#setting-the-period).
   >

1. Defina o método para calcular o número mais alto de mensagens.

   O limite representa o número mais alto de mensagens que podem ser enviadas para um destinatário durante o período relacionado.

   Por padrão, o limite é constante e você precisa indicar um número máximo de mensagens autorizadas pela regra.

   ![](assets/campaign_opt_create_a_rule_03b.png)

   Para definir um limite de variável, selecione o valor **[!UICONTROL Depends on the recipient]** no campo **[!UICONTROL Type of threshold]** e use o ícone à direita para abrir o editor de expressão.

   ![](assets/campaign_opt_create_a_rule_04.png)

   Para obter mais informações, consulte [Número máximo de mensagens](#maximum-number-of-messages).

1. Especifique o método para calcular o peso da entrega.

   Cada entrega tem um peso, ou seja, um valor que representa seu nível de prioridade: isso permite a arbitragem entre campanhas. Os pesos são calculados usando a fórmula definida na regra de tipologia e/ou em suas propriedades. Para obter mais informações, consulte [Peso da mensagem](#message-weight).

1. Por padrão, todas as mensagens são consideradas para o cálculo do limite. A guia **[!UICONTROL Restriction]** permite filtrar as mensagens relacionadas à regra de tipologia:

   * A seção superior desta guia permite restringir os destinatários relacionados.
   * A seção inferior desta guia permite que você filtre as mensagens a serem contadas.

     No exemplo a seguir, somente os destinatários salvos na pasta **NewContacts** são considerados, sendo relacionados as entregas que começam com **Newsletter**.

   ![](assets/campaign_opt_create_a_rule_05.png)

1. A guia **[!UICONTROL Typologies]** permite visualizar as tipologias de campanha que aplica essa regra ou vincular a regra a uma ou mais tipologias existentes. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=pt-BR){target="_blank"}.

## Definir limites e pesos {#defining-thresholds-and-weights}

### Número máximo de mensagens {#maximum-number-of-messages}

Cada regra de pressão define um limite, ou seja, o número máximo de mensagens que podem ser enviadas para um destinatário em um determinado período de tempo. Depois que esse limite for atingido, não poderá ocorrer mais entregas até que o final do período seja considerado. Esse processo permite que você exclua automaticamente um destinatário de uma entrega se uma mensagem exceder o limite definido, evitando assim um excesso de solicitações.

Os valores de limite podem ser constantes ou calculados por uma fórmula com variáveis. Isso significa que, para um determinado período, os limites podem variar de um destinatário para outro ou até mesmo para o mesmo destinatário.

![](assets/campaign_opt_create_a_rule_threshold.png)

>[!CAUTION]
>
>Inserir **0** como limite impede todas as entregas à população de destino durante o período considerado.

**Exemplo:**

Você pode indexar o número de mensagens autorizadas de acordo com o segmento ao qual pertence o destinatário. Isso significa que um destinatário pertencente ao segmento da web pode receber mais mensagens do que outros destinatários. Uma fórmula do tipo **[!UICONTROL Iif (@origin='Web', 5, 3)]** autoriza a entrega de 5 mensagens a destinatários e 3 para outros segmentos. A configuração será a seguinte:

![](assets/campaign_opt_pressure_sample.png)

Para definir o limite, você pode usar uma dimensão vinculada à dimensão de direcionamento: por exemplo, para incluir mensagens enviadas aos perfis de destinatários armazenados na tabela de visitantes (para saber mais sobre a tabela de visitantes, consulte [esta seção](../../surveys/using/use-case-creating-a-refer-a-friend-form.md)) ou para evitar o envio de mais de uma mensagem por semana para a mesma família de destinatários, (o que pode significar vários endereços de email) identificada em uma dimensão vinculada aos destinatários.

Para fazer isso, selecione a opção **[!UICONTROL Count messages on a linked dimension]** e selecione a tabela de visitantes ou de contatos.

### Peso da mensagem {#message-weight}

Cada entrega tem um peso que representa seu nível de prioridade. Por padrão, o peso de uma entrega é definido como 5. As regras de pressão permitem definir o peso das entregas às quais serão aplicadas.

Os pesos podem ser definidos ou calculados por meio de uma fórmula para se adequar aos destinatários. Por exemplo, você pode definir o peso de uma entrega com base nos interesses do destinatário.

>[!CAUTION]
>
>O peso definido em uma regra de tipologia pode ser sobrecarregado individualmente para cada entrega, na guia **[!UICONTROL Properties]**. Clique na guia **[!UICONTROL Typology]** para selecionar a tipologia de campanha e, se necessário, especifique o peso a ser aplicado.\
>No entanto, o peso declarado em uma regra de tipologia A não será usado para calcular uma regra de tipologia B: esse peso irá se referir apenas às entregas que usam a regra A.

**Exemplo:**

No exemplo a seguir, queremos vincular o peso das newsletters sobre música ao escore de propensão dos destinatários. Para fazer isso:

1. Crie um novo campo para armazenar escores de propensão do destinatário. O campo, **@Music** neste caso, será enriquecido com respostas de pesquisas e questionários on-line, dados de rastreamento coletados, etc.
1. Crie uma regra de tipologia para calcular o peso da mensagem com base nesse campo.

   ![](assets/campaign_opt_pressure_weight_sample.png)

1. Aplique esta regra a mensagens com os seguintes tópicos: newsletters, ofertas especiais etc. O peso dessas entregas e, portanto, o nível de prioridade, dependerão do escore de propensão de cada destinatário.

## Definir o período {#setting-the-period}

As regras de pressão são definidas em períodos de **n** dias consecutivos.

O período é configurado na guia **[!UICONTROL Pressure]** da regra. Você pode especificar o número de dias e, se necessário, selecionar o tipo de agrupamento a ser aplicado (dia, semana, mês, trimestre, etc.).

O tipo de agrupamento permite estender o campo **[!UICONTROL Period considered]** para todo o dia, semana, mês ou ano para datas do período.

Por exemplo, uma regra de pressão que define um limite de 2 mensagens por semana, com um agrupamento para cada mês, impedirá a entrega de mais de 2 mensagens na mesma semana E no mesmo mês. Aviso, se o período se sobrepõe dois meses, o limite de cálculo leva em consideração as entregas desses dois meses e, portanto, poderá impedir todas as novas entregas durante o segundo mês.

Observe que, por padrão, somente as entregas já enviadas são consideradas ao calcular o limite. No Campaign Classic v7, marque a opção **[!UICONTROL Take the deliveries into account in the provisional calendar]** se desejar considerar também as entregas programadas para o período em questão. Nesse caso, o período considerado é dobrado para permitir a integração de entregas futuras, bem como as anteriores.

Para restringir os envios realizados em um período de duas semanas, é possível:

1. Insira **15d** no campo **[!UICONTROL Concerned period]**: no cálculo são considerados as entregas realizadas em até duas semanas antes da data da entrega no qual a regra é aplicada,

ou

1. Insira **7d** no campo **[!UICONTROL Period considered]** E marque a opção **[!UICONTROL Take the deliveries into account in the provisional calendar]**: entregas enviadas até 7 dias antes da data de entrega e programadas para até 7 dias após a data de entrega em que a regra aplicada será levada em conta no cálculo.

A data inicial do período depende de como o banco de dados está configurado.

Por exemplo, ao aplicar uma regra de pressão de 15 dias sem agrupar a uma entrega com data 11/12, serão consideradas as entregas entre 27/11 e 12/12. Se a regra de pressão considerar os envios do calendário provisional, todas as entregas agendadas entre 27/11 e 27/12 são consideradas. Por fim, ao configurar na regra um agrupamento por mês, todas as entregas em novembro e dezembro são consideradas para calcular o limite (de 01/11 a 31/12).


**Casos frequentes**

Para garantir que as entregas da semana atual do calendário não sejam levadas em conta, assim como também não correr o risco de considerar a semana anterior no limite de cálculo, especifique o **[!UICONTROL Period considered]** como &quot;0&quot; e selecione &quot;Grouping per calendar week&quot; como o **[!UICONTROL Period type]**.

Quando um período é maior que 0 (1 por exemplo), o limite de cálculo pode considerar os envios do dia anterior. Portanto, se o dia anterior corresponde à semana do calendário anterior e o tipo de período selecionado é o &#39;Agrupamento por semana do calendário&#39;, então toda a semana anterior é considerada para o limite de cálculo.

**Exemplo:**

Para criar uma regra de pressão que restringe a solicitação de 3 mensagens por período 2 semanas, com um agrupamento por mês do calendário.

![](assets/campaign_opt_pressure_period_sample_1a.png)

São usados 6 boletins com o mesmo peso, programados para 30/05, 03/06, 08/06, 12/06, 22/06 e 30/06.

![](assets/campaign_opt_pressure_period_sample_0.png)

As entregas programadas para os dias 12 e 30 de junho não podem ser realizadas: a entrega de 12/06 excede o limite de 3 mensagens por período de 2 semanas e a entrega do dia 30 excede o limite de comunicações autorizadas por mês.

![](assets/campaign_opt_pressure_period_sample_1.png)

Todos os destinatários dessas entregas são excluídos por arbitragem durante a fase de análise:

![](assets/campaign_opt_pressure_period_sample_2.png)

Para a mesma regra, ao agrupar as entregas por trimestre, os destinatários do **newsletter no.5** também devem ser excluídos e não podem ser enviadas.

Finalmente, se nenhum agrupamento for selecionado, somente o **newsletter no.4** não pode ser enviado, já que foi programado para o mesmo período de 2 semanas que os três primeiros boletins.

>[!NOTE]
>
>Ao altera a definição de uma regra de tipologia, é possível criar uma **Simulation** para controlar o impacto sobre as entregas ao qual é aplicada e monitorar o impacto que as entregas têm umas nas outras. Para obter mais informações, consulte [Simulações de campanha](campaign-simulations.md).

## Exclusão após arbitragem {#exclusion-after-arbitration}

A arbitragem é reaplicada todas as noites através do fluxo de trabalho técnico **[!UICONTROL Forecasting]** e do fluxo de trabalho **[!UICONTROL Campaign jobs]**.

O fluxo de trabalho **[!UICONTROL Forecasting]** pré-calcula os dados do período em andamento (da data inicial para a data atual), que permite a aplicação das regras de tipologia durante a análise. Também recalcula os contadores de exclusão para arbitragem a cada noite.

Assim, para cada destinatário, o Adobe Campaign verifica se o número de mensagens que devem ser enviadas não excede o limite e assim considera todas as que já foram enviadas no período relacionado. Estas informações são um **indicador**, já que todos os cálculos são atualizados no momento da entrega.

Se esse número excede o limite, as regras de arbitragem definidas na tipologia de campanha são aplicadas e os destinatários são excluídos das campanhas com um peso menor.

![](assets/campaign_opt_pressure_exclusion.png)

>[!NOTE]
>
>Se várias entregas alcançam pontuações iguais, a campanha programada para a data mais antiga é enviada.

## Casos de uso em regras de pressão {#use-cases-on-pressure-rules}

### Adaptar o limite com base no critério {#adapting-the-threshold-based-on-criterion}

Criaremos uma regra de tipologia para evitar a entrega de mais de quatro mensagens por semana para clientes e duas mensagens por semana para clientes potenciais.

Para identificar clientes e clientes potenciais, use o campo **[!UICONTROL Status]**, que contém 0 para clientes potenciais e 1 para clientes.

Para criar a regra, aplique as seguintes etapas:

1. Crie uma nova regra de tipologia do tipo **Pressão**.
1. Edite a guia **[!UICONTROL Pressure]**: na seção **[!UICONTROL Maximum number of messages]**, queremos criar uma fórmula para calcular o limite de acordo com cada destinatário. Selecione o valor **[!UICONTROL Depends on the recipient]** no campo **[!UICONTROL Threshold type]** e clique em **[!UICONTROL Edit expression]** à direita do campo **[!UICONTROL Formula]**.

   Clique no botão **[!UICONTROL Advanced parameters]** para definir a fórmula de cálculo.

   ![](assets/campaign_opt_pressure_sample_1_1.png)

1. Selecione a opção **[!UICONTROL Edit the formula using an expression]** e clique em **[!UICONTROL Next]**.

   ![](assets/campaign_opt_pressure_sample_1_2.png)

1. Na lista de funções, clique duas vezes na função **Iif** no nó **[!UICONTROL Others]**.

   Em seguida, selecione o **Status** dos destinatários na seção **[!UICONTROL Available fields]**.

   ![](assets/campaign_opt_pressure_sample_1_3.png)

   Informe a seguinte fórmula: **Iif(@status=0,2,4)**

   ![](assets/campaign_opt_pressure_sample_1_4.png)

   Essa fórmula permite atribuir o valor 2 se o status for igual a 0, e o valor 4 para todos os outros status.

   Clique em **[!UICONTROL Finish]** para aprovar a fórmula.

1. Indicar o período durante o qual a regra será aplicada: 7 dias nesse caso, para contar o número de mensagens por semana.

   ![](assets/campaign_opt_pressure_sample_1_5.png)

1. Salve a regra para aprovar a criação.

Agora vincule a regra que acabou de criar a um tipologia para aplicá-la às entregas. Para fazer isso:

1. Crie uma tipologia de campanha.
1. Vá para a guia **[!UICONTROL Rules]**, clique no botão **[!UICONTROL Add]** e selecione a regra que você acabou de criar.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. Salve a tipologia: ela será adicionada à lista de tipologias existentes.

Para usar essa tipologia em suas entregas, selecione-a nas propriedades de entrega, na guia **[!UICONTROL Typology]**, conforme mostrado abaixo:

![](assets/campaign_opt_pressure_sample_1_7.png)

>[!NOTE]
>
>A tipologia pode ser definida no template da entrega para que seja aplicada automaticamente a todas as entregas criadas usando esse modelo.

Durante a análise de entrega, os destinatários da entrega são excluídos, se aplicável, dependendo do número de entregas já enviados para eles. Para visualizar essas informações, você poderá:

* Visualizar o resultado da análise:

  ![](assets/campaign_opt_pressure_sample_1_8.png)

* Edite a entrega e clique na guia **[!UICONTROL Delivery]** e na subguia **[!UICONTROL Exclusions]**:

  ![](assets/campaign_opt_pressure_sample_1_9.png)

* Clique na guia **[!UICONTROL Audit]** e, em seguida, na subguia **[!UICONTROL Causes of exclusions]** para exibir o número de exclusões e as regras de tipologia aplicadas:

  ![](assets/campaign_opt_pressure_sample_1_10.png)

### Calcular o peso da entrega com base no comportamento {#calculating-the-delivery-weight-based-on-behavior}

Você pode definir regras de pressão com base no comportamento do destinatário: assim, o peso de uma entrega pode se adaptar a critérios que variam de um destinatário a outro. Você pode decidir enviar uma mensagem dependendo se um destinatário visitou o seu site de Internet, clicou em uma seção específica do último boletim informativo, se inscreveu em um serviço de informação ou até mesmo com base nas respostas de uma pesquisa, um jogo online etc.

No exemplo a seguir, uma entrega com um peso de 5 é criada. Esse peso é melhorado com pontuações de propensão com base no comportamento do destinatário: os clientes que já compraram neste site tem uma pontuação de 5, enquanto os clientes que nunca compraram online terão uma pontuação de 4.

Para executar esse tipo de configuração, é necessário usar uma fórmula para definir o peso da mensagem. As informações sobre pontuações de propensão e as respostas da pesquisa devem ser acessíveis no modelo de dados. No exemplo, o campo **Propensity** foi adicionado.

Aplique as seguintes etapas de configuração:

1. Crie uma nova regra de tipologia do tipo **Pressão**.
1. Edite a guia **[!UICONTROL Pressure]**. Para criar uma fórmula de limite que será baseada em cada destinatário individual: clique no ícone **[!UICONTROL Edit expression]** à direita do campo **[!UICONTROL Weight formula]**.

   ![](assets/campaign_opt_pressure_sample_2_1.png)

1. Por padrão, o valor **5** é mostrado na seção superior do editor de expressão. Queremos adicionar a pontuação de propensão de cada destinatário a esse peso: coloque o cursor à direita do 5, insira o caractere **+** e selecione o campo **Propensity** .

   ![](assets/campaign_opt_pressure_sample_2_2.png)

1. Em seguida, adicione um valor maior para destinatários que já fizeram uma compra. Para eles, o peso da entrega deverá ser aumentado em 5, enquanto para os outros o aumento será de somente 4.

   ![](assets/campaign_opt_pressure_sample_2_3.png)

1. Clique em **[!UICONTROL Finish]** para salvar essa regra.
1. Vincule a regra a uma tipologia de campanha e faça referência a essa tipologia em uma entrega para aprová-la.

### Enviar somente as mensagens com maior peso {#sending-only-the-highest-weighted-messages}

Você deseja enviar não mais do que 2 mensagens na mesma semana, com um limite de 2 mensagens por dia a cada um dos destinatários, e você deseja que apenas as mensagens com pesos maiores sejam entregues.

Para fazer isso, é necessário agendar várias entregas com pesos diferentes para o mesmo destinatário e aplicar uma regra de pressão para excluir as entregas com pesos menores.

Primeiro, configure a regra de pressão.

1. Criar uma regra de pressão. Para obter mais informações, consulte [Criar uma regra de pressão](#creating-a-pressure-rule).
1. Na guia **[!UICONTROL General]**, selecione a opção **[!UICONTROL Re-apply the rule at the start of personalization]**. 

   ![](assets/campaign_opt_pressure_example_5.png)

   Essa opção anula o valor definido no campo **[!UICONTROL Frequency]** e aplica a regra automaticamente durante a fase de personalização. Para obter mais informações, consulte [Ajustar a frequência de cálculo](applying-rules.md#adjusting-calculation-frequency).

1. Na guia **[!UICONTROL Pressure]**, defina **[!UICONTROL 7d]** como **[!UICONTROL Period considered]**, e **[!UICONTROL Grouping per day]** como **[!UICONTROL Period type]**.
1. Selecione a opção **[!UICONTROL Take the deliveries into account in the provisional calendar]** para incluir as entregas programadas.

   ![](assets/campaign_opt_pressure_example_1.png)

   São consideradas no cálculo as entregas realizadas até 7 dias antes da data de entrega e os programados até 7 dias após a data de entrega. Para obter mais informações, consulte [Definir o período](#setting-the-period).

1. Na guia **[!UICONTROL Typologies]**, vincule a regra a uma tipologia de campanha.
1. Salve as alterações.

Agora, crie e configure um fluxo de trabalho para cada entrega em que a regra de pressão é aplicada.

1. Crie uma campanha. Para obter mais informações, consulte [esta seção](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. Na guia **[!UICONTROL Targeting and workflows]** da campanha, adicione uma atividade de **Query** ao fluxo de trabalho. Para obter mais informações sobre o uso dessa atividade, consulte [esta seção](../../workflow/using/query.md).
1. Adicione uma atividade **[!UICONTROL Email delivery]** ao fluxo de trabalho e depois a abra. Para obter mais informações sobre o uso dessa atividade, consulte [esta seção](../../workflow/using/delivery.md).
1. Acesse a guia **[!UICONTROL Approvals]** das **[!UICONTROL Delivery properties]** e desabilite todas as aprovações.

   ![](assets/campaign_opt_pressure_example_2.png)

1. Na guia **[!UICONTROL Typology]** das **[!UICONTROL Delivery properties]**, consulte a tipologia de campanha à qual aplicar a regra. Defina um peso para a entrega.

   ![](assets/campaign_opt_pressure_example_3.png)

1. Na entrega, clique em **[!UICONTROL Scheduling]** e selecione **[!UICONTROL Schedule delivery (automatic execution when the scheduled date is reached)]**. Neste exemplo, selecione a opção **[!UICONTROL Use a calculation formula]**.
1. Defina a data de extração para 10 minutos (data atual + 10 minutos).
1. Defina a data de contato para o dia seguinte (data atual + 1 dia).

   ![](assets/campaign_opt_pressure_example_4.png)

   Para implementar as exclusões da regra de pressão com êxito, certifique-se de definir a data e a hora da extração antes da data e hora do contato, assim como antes da arbitragem noturna ser reaplicada. Para obter mais informações, consulte [Exclusão após arbitragem](#exclusion-after-arbitration).

1. Desmarque a opção **[!UICONTROL Confirm the delivery before sending]** e salve as alterações.
1. Continue de forma semelhante para cada entrega que deve ser enviada. Certifique-se de definir o peso desejado para cada entrega.
1. Execute os fluxos de trabalho relevantes para preparar e realizar as entregas.

Quando a arbitragem noturna for aplicada, as entregas com os pesos menores para o mesmo destinatário serão excluídas. Somente as entregas com o peso mais alto serão consideradas para envio. Para obter mais informações, consulte [Peso da mensagem](#message-weight).

Considerando que um email já tenha sido enviado aos destinatários relacionados anteriormente durante a semana, a tabela abaixo mostra um exemplo das configurações que poderão ser aplicadas para duas entregas adicionais.

<table> 
 <thead> 
  <tr> 
   <th> Entrega<br /> </th> 
   <th> Aprovações<br /> </th> 
   <th> Peso<br /> </th> 
   <th> Data/hora de Extração<br /> </th> 
   <th> Data de contato<br /> </th> 
   <th> Data/hora de início da entrega<br /> </th> 
   <th> Data/hora de execução do fluxo de trabalho de arbitragem<br /> </th> 
   <th> Status da entrega<br /> </th> 
   <th> Entrega enviada (data/hora)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Entrega 1<br /> </td> 
   <td> Desabilitado<br /> </td> 
   <td> 5<br /> </td> 
   <td> 15h<br /> </td> 
   <td> 8h (próximo dia)<br /> </td> 
   <td> 14h<br /> </td> 
   <td> Noturno<br /> </td> 
   <td> Excluído<br /> </td> 
   <td> Excluído<br /> </td> 
  </tr> 
  <tr> 
   <td> Entrega 2<br /> </td> 
   <td> Desabilitado<br /> </td> 
   <td> 10<br /> </td> 
   <td> 16h<br /> </td> 
   <td> 9h (próximo dia)<br /> </td> 
   <td> 14h<br /> </td> 
   <td> Noturno<br /> </td> 
   <td> Sent<br /> </td> 
   <td> 9h (próximo dia)<br /> </td> 
  </tr> 
 </tbody> 
</table>

Após a data de extração haver expirado para as duas entregas, a arbitragem noturna será reaplicada antes das datas de contato de ambas as entregas. Isso permite encontrar todas as entregas já enviadas (destinatários para os quais uma entrega é processada, registrados pelos logs amplos) ou agendadas para serem enviadas (destinatários qualificados para receber uma entrega, registrados pelos logs de previsão).

Depois que todas as entregas enviadas e potenciais tiverem sido listadas para o período definido na regra de pressão, o Adobe Campaign as classificará por peso, com o maior valor em primeiro lugar. Quando o limite definido na regra de pressão for atingido (aqui, não mais do que 2 emails na mesma semana), os destinatários serão excluídos da entrega.
