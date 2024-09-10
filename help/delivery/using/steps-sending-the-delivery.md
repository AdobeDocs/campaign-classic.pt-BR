---
product: campaign
title: Configurar e enviar a entrega
description: Saiba como configurar e enviar a entrega
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Channel Configuration
role: User
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1526'
ht-degree: 98%

---

# Configurar e enviar a entrega {#configuring-and-sending-the-delivery}

## Permissões{#delivery-permissions}

Somente o proprietário da entrega pode iniciar uma entrega. Para que outros operadores (ou grupo de operadores) possam iniciar uma entrega, é necessário adicioná-los como revisores no campo **[!UICONTROL Delivery start:]**. [Saiba mais](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

## Parâmetros adicionais de entrega {#delivery-additiona-parameters}

Antes de enviar a entrega, você poderá definir os parâmetros de envio nas propriedades da entrega, por meio da guia **[!UICONTROL Delivery]**.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: use essa opção para alterar a ordem de envio das entregas, definindo o nível de prioridade (normal, alto ou baixo).

* **[!UICONTROL Message batch quantity]**: use essa opção para definir o número de mensagens agrupadas no mesmo pacote de entrega XML. Se o parâmetro for definido como 0, as mensagens serão automaticamente agrupadas. O tamanho do pacote é definido pelo cálculo `<delivery size>/1024`, com no mínimo 8 e no máximo 256 mensagens por pacote.

  >[!IMPORTANT]
  >
  >Quando a entrega é criada duplicando uma existente, esse parâmetro é redefinido.

* **[!UICONTROL Send using multiple waves]**: use essa opção para enviar suas mensagens em lotes, em vez de enviá-las para todo o público-alvo de uma só vez. [Saiba mais](#sending-using-multiple-waves).

* **[!UICONTROL Test SMTP delivery]**: use essa opção para testar o envio via SMTP. A entrega é processada até a conexão com o servidor SMTP, mas não é enviada: para cada destinatário do delivery, o Campaign se conecta ao servidor do provedor SMTP, executa o comando SMTP RCPT TO e encerra a conexão antes do comando SMTP DATA.

  >[!NOTE]
  >
  >* Essa opção não deve ser definida no mid-sourcing.
  >
  >* Saiba mais sobre a configuração do servidor SMTP [nesta seção](../../installation/using/configure-delivery-settings.md).

* **[!UICONTROL Email BCC]**: essa opção permite armazenar emails em um sistema externo por meio do CCO. Para isso, basta adicionar um endereço de email de CCO ao destinatário da mensagem. [Saiba mais](sending-messages.md#archiving-emails).

## Confirmar a entrega {#confirming-delivery}

Quando a entrega estiver configurada e pronta para ser enviada, execute a análise de entrega.

Para fazer isso, clique em **[!UICONTROL Send]**, selecione a ação desejada e clique em **[!UICONTROL Analyze]**. [Saiba mais](steps-validating-the-delivery.md#analyzing-the-delivery).

![](assets/s_ncs_user_email_del_send.png)

Depois de concluído, clique em **[!UICONTROL Confirm delivery]** para iniciar a entrega de mensagens.

Você poderá fechar o assistente de entrega e controlar a execução da entrega a partir da guia **[!UICONTROL Delivery]**, acessível por meio do detalhe desta entrega ou pela lista de entregas.

Após enviar as mensagens, você pode monitorar e rastrear suas entregas. Para obter mais informações, consulte essas seções.

* [Monitorar uma entrega](about-delivery-monitoring.md)
* [Entender as falhas de entrega](understanding-delivery-failures.md)
* [Sobre o rastreamento de mensagens](about-message-tracking.md)

## Agendar o envio da entrega {#scheduling-the-delivery-sending}

Você pode adiar o envio da mensagem agendando a entrega.

1. Clique no botão **[!UICONTROL Send]** e selecione a opção **[!UICONTROL Postpone delivery]**.

1. Especifique uma data de início no campo **[!UICONTROL Contact date]**.

![](assets/dlv_email_del_plan.png)

1. Você pode iniciar a análise da entrega e confirmar o envio da entrega. No entanto, o envio da entrega não será iniciado até a data indicada no campo **[!UICONTROL Contact date]**.

>[!IMPORTANT]
>
>Depois de iniciar a análise, a data de contato que você definiu será corrigida. Se você modificar essa data, será necessário reiniciar a análise para que suas modificações sejam consideradas.

![](assets/s_ncs_user_email_del_start_delayed.png)

Na lista do delivery, a entrega será exibida com o status **[!UICONTROL Pending]**.

![](assets/s_ncs_user_email_del_waiting.png)

O agendamento pode ser configurado de forma ascendente através do botão **[!UICONTROL Scheduling]** da entrega.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

Isso permite adiar a entrega para uma data posterior ou salvar a entrega no calendário provisional.

* A opção **[!UICONTROL Schedule delivery (no automatic execution)]** permite agendar uma análise provisional da entrega.

  Quando essa configuração é salva, a entrega muda para o status **[!UICONTROL Targeting pending]**. A análise será iniciada na data especificada.

* A opção **[!UICONTROL Schedule delivery (automatic execution on planned date)]** permite especificar a data da entrega.

  Clique em **[!UICONTROL Send]** e selecione **[!UICONTROL Postpone delivery]**, depois inicie a análise e confirme a entrega. Quando a análise for concluída, o destinatário da entrega estará pronto e as mensagens serão automaticamente enviadas na data especificada.

Datas e horas são expressas no fuso horário do operador atual. A lista suspensa **[!UICONTROL Time zone]** localizada abaixo do campo de entrada de data do contato permite converter automaticamente a data e a hora inseridas para o fuso horário selecionado.

Por exemplo, se você agendar uma entrega para que ela seja executada automaticamente às 8h, horário de Londres, a hora será convertida automaticamente para o fuso horário selecionado:

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## Enviar usando várias ondas {#sending-using-multiple-waves}

Para balancear a carga, você pode dividir entregas em vários lotes. Configure o número de lotes e sua proporção com relação à entrega inteira.

>[!NOTE]
>
>Você só poderá definir o tamanho e o atraso entre duas ondas consecutivas. Os critérios de seleção de destinatário para cada onda não podem ser configurados.

1. Abra a janela de propriedades do e clique na guia **[!UICONTROL Delivery]** Entrega.
1. Selecione a opção **[!UICONTROL Send using multiple waves]** e clique no link **[!UICONTROL Define waves...]**.

   ![](assets/s_ncs_user_wizard_waves.png)

1. Para configurar ondas, você pode:

   * Definir o tamanho de cada onda. Por exemplo, se você inserir **[!UICONTROL 30%]** no campo correspondente, cada onda representará 30% das mensagens incluídas na entrega, exceto a última, que representará 10% das mensagens.

     No campo **[!UICONTROL Period]**, especifique o atraso entre o início de duas ondas consecutivas. Por exemplo, se você inserir **[!UICONTROL 2d]**, a primeira onda começará imediatamente, a segunda onda começará em dois dias, a terceira onda em quatro dias e assim por diante.

     ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Defina um calendário para enviar cada onda.

     Na coluna **[!UICONTROL Start]**, especifique o atraso entre o início de duas ondas consecutivas. Na coluna **[!UICONTROL Size]**, insira um número fixo ou uma porcentagem.

     No exemplo abaixo, a primeira onda representa 25% do número total de mensagens incluídas na entrega e iniciará imediatamente. As próximas duas ondas completam a entrega e são definidas para começar em intervalos de seis horas.

     ![](assets/s_ncs_user_wizard_waves_create.png)

   Uma regra de tipologia específica, **[!UICONTROL Wave scheduling check]**, garante que a última onda seja planejada antes do limite da validade da entrega. As tipologias de campanha e suas regras, configuradas na guia **[!UICONTROL Typology]** das propriedades de entrega, são apresentadas em [Processo de validação com tipologias](steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!IMPORTANT]
   >
   >Certifique-se de que as últimas ondas não excedam o prazo da entrega, que é definido na guia **[!UICONTROL Validity]**. Caso contrário, algumas mensagens podem não ser enviadas.
   >
   >Você também deverá permitir tempo suficiente para novas tentativas ao configurar as últimas ondas. Consulte [esta seção](steps-sending-the-delivery.md#configuring-retries).

1. Para monitorar seus envios, vá para os logs de entrega. Consulte [esta página](delivery-dashboard.md#delivery-logs-and-history).

   Você pode ver as entregas que já foram enviadas nas ondas processadas (status **[!UICONTROL Sent]**) e as entregas a serem enviadas nas ondas restantes (status **[!UICONTROL Pending]**).

Os dois exemplos abaixo são os casos de uso mais comuns para usar várias ondas.

* **Durante o processo de aumento**

  Quando os emails são enviados usando uma nova plataforma, os provedores de serviços de Internet (ISPs) suspeitam de endereços IP que não são reconhecidos. Se grandes volumes de emails forem enviados repentinamente, os ISPs freqüentemente os marcam como spam.

  Para evitar ser marcado como spam, você poderá aumentar progressivamente o volume enviado usando ondas. Isso deve garantir o desenvolvimento suave da fase de inicialização e permitir que você reduza a taxa geral de endereços inválidos.

  Para fazer isso, use a opção **[!UICONTROL Schedule waves according to a calendar]**. Por exemplo, defina a primeira onda para 10%, a segunda para 15% e assim por diante.

  ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Campanhas envolvendo uma central de atendimento**

  Ao gerenciar uma campanha de fidelidade por telefone, sua organização tem uma capacidade limitada de processamento do número de chamadas para contatar assinantes.

  Usando ondas, você poderá restringir o número de mensagens a 20 por dia, por exemplo, considerando a capacidade diária de processamento de uma central de atendimento.

  Para fazer isso, selecione a opção **[!UICONTROL Schedule multiple waves of the same size]**. Insira **[!UICONTROL 20]** como o tamanho da onda e **[!UICONTROL 1d]** no campo **[!UICONTROL Period]**.

  ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Configurar novas tentativas {#configuring-retries}

As mensagens temporariamente não entregues devido a um erro **Suave** ou **Ignorado** estão sujeitas a uma repetição automática. Os tipos de falha de entrega são apresentados nesta [seção](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Para instalações hospedadas ou híbridas, se você tiver atualizado para o [MTA aprimorado](sending-with-enhanced-mta.md), as configurações de nova tentativa na entrega não serão mais usadas pelo Campaign. As tentativas de rejeição temporária e o intervalo de tempo entre elas são determinados pelo MTA aprimorado com base no tipo e na gravidade das respostas de rejeição que retornam do domínio de email da mensagem.

Para instalações no local e instalações hospedadas/híbridas usando o MTA herdado do Campaign, a seção central da guia **[!UICONTROL Delivery]** para parâmetros de entrega indica quantas tentativas devem ser executadas no dia seguinte à entrega e o atraso mínimo entre as tentativas.

![](assets/s_ncs_user_wizard_retry_param.png)

Por padrão, cinco tentativas são agendadas para o primeiro dia da entrega, com um intervalo mínimo de uma hora distribuído pelas 24 horas do dia. Uma nova tentativa por dia é programada depois disso e até o prazo da entrega, que é definido na guia **[!UICONTROL Validity]**. Consulte [Definir o período de validade](#defining-validity-period).

## Definir o período de validade {#defining-validity-period}

Quando a entrega for iniciada, as mensagens (e todas as tentativas) poderão ser enviadas até o prazo da entrega. Isso é indicado nas propriedades de entrega, por meio da guia **[!UICONTROL Validity]**.

![](assets/s_ncs_user_email_del_valid_period.png)

* O campo **[!UICONTROL Delivery duration]** permite inserir o limite de novas tentativas de entrega globais. Isso significa que o Adobe Campaign envia as mensagens começando na data de início e, em seguida, para mensagens que retornam somente um erro, tentativas regulares e configuráveis são executadas até que o limite de validade seja atingido.

  Você também poderá optar por especificar datas. Para fazer isso, selecione **[!UICONTROL Explicitly set validity dates]**. Nesse caso, as datas de entrega e limite de validade também permitem especificar o tempo. O tempo atual é usado por padrão, mas você poderá modificar isso diretamente no campo de entrada.

  >[!IMPORTANT]
  >
  >Para instalações hospedadas ou híbridas, se você tiver atualizado para o [MTA aprimorado](sending-with-enhanced-mta.md), a configuração **[!UICONTROL Delivery duration]** nas entregas de email do Campaign será usada somente se definida como **3,5 dias ou menos.**. Se você definir um valor superior a 3,5 dias, ele não será levado em consideração.

* **Limite da validade de recursos**: o campo **[!UICONTROL Validity limit]** é usado para recursos carregados, principalmente para a mirror page e imagens. Os recursos desta página são válidos por um tempo limitado (para economizar espaço em disco).

  Os valores nesse campo podem ser expressos nas unidades listadas [nesta seção](../../platform/using/adobe-campaign-workspace.md#default-units).
