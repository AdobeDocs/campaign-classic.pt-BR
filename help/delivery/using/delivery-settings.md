---
product: campaign
title: Sobre configurações de deliveries
description: Conheça as configurações específicas de delivery do v7
feature: Channel Configuration
role: User
hide: true
hidefromtoc: true
exl-id: 66250817-f829-4b8b-92dd-2daa92a97fe0
source-git-commit: d3d731c64cb5a430de6adac3aeb326f74134c436
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 95%

---

# Configurações de entrega {#about-delivery-settings}

As configurações a seguir são específicas do Campaign Classic. Para outras configurações de entrega, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html?lang=pt-BR){target="_blank"}.

## Análise de entrega {#delivery-analysis}

### Melhorar o desempenho da análise de entrega {#improving-delivery-analysis}

Para acelerar o preparo da entrega, é possível marcar a opção **[!UICONTROL Prepare the delivery parts in the database]** antes de iniciar a análise.

Ao ativar esta opção, o preparo da entrega é executado diretamente no banco de dados, o que pode acelerar significativamente a análise.

Atualmente, essa opção está disponível somente quando as seguintes condições são atendidas:

* A entrega deve ser um email. Por enquanto, os outros canais não são compatíveis.
* O mid-sourcing ou roteamento externo não deve ser usado, apenas o tipo de roteamento de entrega em massa. É possível verificar o roteamento usado na guia **[!UICONTROL General]** do **[!UICONTROL Delivery properties]**.
* Não é possível direcionar uma população proveniente de um arquivo externo. Para uma única entrega, clique no link **[!UICONTROL To]** do **[!UICONTROL Email parameters]** e verifique se a opção **[!UICONTROL Defined in the database]** está selecionada. Para uma entrega usada em um workflow, verifique se os destinatários estão **[!UICONTROL Specified by the inbound event(s)]** na guia **[!UICONTROL Delivery]**.
* É necessário o uso de um banco de dados PostgreSQL.

### Configurar a prioridade da análise {#analysis-priority-}

Quando a entrega é parte de uma campanha, a guia **[!UICONTROL Advanced]** oferece uma opção adicional. Isso permite organizar a ordem de processamento das entregas na mesma campanha.

Antes de enviar, cada entrega é analisada. A duração da análise depende do arquivo de extração de entrega. Quanto mais significativo for o tamanho do arquivo, mais tempo levará a análise, fazendo com que as entregas aguardem.

As opções para **[!UICONTROL Message preparation by the scheduler]** permitem priorizar a análise de entrega em um workflow da campanha.

![](assets/delivery_analysis_priority.png)

Se uma entrega for muito grande, é melhor atribuir uma prioridade baixa a ele para evitar o atraso na análise de outras entregas do workflow.

>[!NOTE]
>
>Para garantir que as análises de entrega maiores não retardem o progresso dos workflows, você poderá agendar suas execuções marcando **[!UICONTROL Schedule execution for a time of low activity]**.

## Envio de entrega {#delivery-sending}

### Configurar novas tentativas {#configuring-retries}

As mensagens temporariamente não entregues devido a um erro **Suave** ou **Ignorado** estão sujeitas a uma repetição automática. Os tipos de falha de entrega são apresentados nesta [seção](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Para instalações hospedadas ou híbridas, se você tiver atualizado para o [MTA aprimorado](sending-with-enhanced-mta.md), as configurações de nova tentativa na entrega não serão mais usadas pelo Campaign. As tentativas de rejeição temporária e o intervalo de tempo entre elas são determinados pelo MTA aprimorado com base no tipo e na gravidade das respostas de rejeição que retornam do domínio de email da mensagem.

Para instalações no local e instalações hospedadas/híbridas usando o MTA herdado do Campaign, a seção central da guia **[!UICONTROL Delivery]** para parâmetros de entrega indica quantas tentativas devem ser executadas no dia seguinte à entrega e o atraso mínimo entre as tentativas.

![](assets/s_ncs_user_wizard_retry_param.png)

Por padrão, cinco tentativas são agendadas para o primeiro dia da entrega, com um intervalo mínimo de uma hora distribuído pelas 24 horas do dia. Uma nova tentativa por dia é programada depois disso e até o prazo da entrega, que é definido na guia **[!UICONTROL Validity]**. Consulte [Definir o período de validade](#defining-validity-period).

### Definir o período de validade {#defining-validity-period}

Quando a entrega for iniciada, as mensagens (e todas as tentativas) poderão ser enviadas até o prazo da entrega. Isso é indicado nas propriedades de entrega, por meio da guia **[!UICONTROL Validity]**.

![](assets/s_ncs_user_email_del_valid_period.png)

* O campo **[!UICONTROL Delivery duration]** permite inserir o limite de novas tentativas de entrega globais. Isso significa que o Adobe Campaign envia as mensagens começando na data de início e, em seguida, para mensagens que retornam somente um erro, tentativas regulares e configuráveis são executadas até que o limite de validade seja atingido.

  Você também poderá optar por especificar datas. Para fazer isso, selecione **[!UICONTROL Explicitly set validity dates]**. Nesse caso, as datas de entrega e limite de validade também permitem especificar o tempo. O tempo atual é usado por padrão, mas você poderá modificar isso diretamente no campo de entrada.

  >[!IMPORTANT]
  >
  >Para instalações hospedadas ou híbridas, se você tiver atualizado para o [MTA aprimorado](sending-with-enhanced-mta.md), a configuração **[!UICONTROL Delivery duration]** nas entregas de email do Campaign será usada somente se definida como **3,5 dias ou menos.**. Se você definir um valor superior a 3,5 dias, ele não será levado em consideração.

* **Limite da validade de recursos**: o campo **[!UICONTROL Validity limit]** é usado para recursos carregados, principalmente para a mirror page e imagens. Os recursos desta página são válidos por um tempo limitado (para economizar espaço em disco).

  Os valores nesse campo podem ser expressos nas unidades listadas [nesta seção](../../platform/using/adobe-campaign-workspace.md#default-units).
