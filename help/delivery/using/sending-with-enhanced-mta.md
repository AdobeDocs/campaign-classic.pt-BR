---
product: campaign
title: Envio com o MTA aprimorado no Adobe Campaign Classic
description: Saiba mais sobre o escopo e as especificidades do envio de emails com o MTA aprimorado do Adobe Campaign
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Email
role: User, Admin, Developer
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: ht
source-wordcount: '1352'
ht-degree: 100%

---

# Envio com o MTA aprimorado {#sending-with-enhanced-mta}

O **MTA aprimorado do Adobe Campaign** (Agente de Transferência de Correspondência) fornece uma infraestrutura de envio atualizada que permite melhor fornecimento, reputação, taxa de transferência, relatórios, tratamento de rejeição, aumento do IP e gerenciamento da configuração de conexão.

Ele é implementado para melhorar a escalabilidade, aumentar a taxa de transferência do delivery e ajudar a enviar mais emails mais rapidamente. Isso é feito com novas técnicas de delivery adaptáveis que alteram as configurações de envio de email em tempo real, com base no feedback dos Provedores de serviço da Internet.

>[!IMPORTANT]
>
>O MTA aprimorado do Adobe Campaign só está disponível para clientes do Campaign Classic hospedados ou híbridos. As instalações no local do Campaign Classic não podem ser atualizadas para usar o MTA aprimorado.

Se você provisionou uma instância do Campaign Classic após setembro de 2018, está usando o MTA aprimorado. Para todos os outros clientes do Campaign Classic, consulte as [Perguntas frequentes](#enhanced-mta-faq) abaixo.

A implementação do MTA aprimorado pode afetar algumas das funcionalidades existentes do Campaign. Para obter mais informações, consulte [Especificidades do MTA aprimorado](#enhanced-mta-impacts).

>[!NOTE]
>
>Se você for um usuário final do Adobe Campaign e quiser saber se sua instância foi atualizada para o MTA aprimorado, entre em contato com o administrador interno do Campaign.

## Perguntas frequentes {#enhanced-mta-faq}

### Uso e benefícios

**O que é o MTA aprimorado?**

O Adobe Campaign agora pode ser atualizado para usar um novo MTA (agente de transferência de email) que executa o MTA do email comercial do SparkPost, chamado **Momentum**.

O Momentum representa uma tecnologia MTA inovadora e de alto desempenho, que inclui um tratamento mais inteligente de rejeição e um recurso automatizado de otimização de entrega que ajuda os remetentes a alcançarem e manterem as taxas ideais de delivery da caixa de entrada. <!--More than 37% of the world's business email is sent using SparkPost's MTA technology.-->

**Quais são os benefícios?**

* Os clientes do Adobe Campaign que usam o MTA aprimorado observaram um <!--300%-->grande aumento na velocidade geral de taxa de transferência e uma <!--90%+-->redução significativa nas rejeições temporárias.
* O MTA aprimorado usa a mais recente tecnologia MTA para oferecer a você as velocidades de taxa de transferência ideais para seu delivery de email.
* Adaptando-se instantânea e automaticamente ao feedback que recebe, ele também garante um delivery de email mais preciso e inteligente com dados de delivery em tempo real.

**Posso usar o MTA nativo e o MTA aprimorado do Adobe Campaign ao mesmo tempo?**

Não. Somente o MTA aprimorado pode ser usado para seus deliveries de email depois que sua instância é atualizada.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Atualização para o MTA aprimorado

**O que é necessário para atualizar para o MTA aprimorado?**

Se você tiver provisionado uma instância do Campaign Classic após setembro de 2018, nenhuma ação será necessária, pois você já estará usando o MTA aprimorado.

Para todos os outros clientes hospedados ou parcialmente hospedados (híbridos), a equipe do Adobe Campaign tentará coordenar uma data para a migração e fornecerá detalhes sobre as etapas apropriadas necessárias para a migração.

>[!IMPORTANT]
>
>O MTA aprimorado não está disponível para instalações no local.

**Qual é o processo para atualizar minha instância para o MTA aprimorado?**

Todo o processo das instâncias hospedadas requer alguns minutos de inatividade. O Adobe monitorará a taxa de transferência e a avaliação do delivery de email por até 24 horas após a atualização para avaliar qualquer impacto nos deliveries de email.

Caso algum problema seja detectado, a Adobe poderá reverter rápida e temporariamente sua instância de volta para o MTA nativo do Adobe Campaign.

Atualmente, o MTA aprimorado afeta apenas o canal de email. Suas notificações por push e deliveries de SMS continuarão a usar o MTA nativo do Campaign e não serão afetadas de nenhuma forma pela atualização.

**Preciso passar pelo aumento gradual de volume de IP novamente depois de atualizar para o MTA aprimorado?**

Não. A atualização não requer a mudança para novos IPs, Portanto, você pode continuar usando seus IPs de email existentes e com aumento gradual.

**A atualização para o MTA aprimorado afetará campanhas ou deliveries em andamento?**

Para os clientes que usam a funcionalidade de mensagens transacionais do Adobe Campaign, todas as chamadas à API para acionar um email serão enfileiradas durante o curto tempo de inatividade da atualização e serão tentadas após a conclusão da atualização.

## Especificidades do MTA aprimorado {#enhanced-mta-impacts}

### Novas regras de MX

As regras de taxa de transferência de delivery de gerenciamento de MX não são mais usadas. O MTA aprimorado tem suas próprias regras de MX, que permitem personalizar a taxa de transferência por domínio com base em seu próprio histórico de reputação de email e no feedback em tempo real proveniente dos domínios para os quais você está enviando emails.

Para obter mais informações sobre configurações de MX, consulte [esta seção](../../installation/using/email-deliverability.md#mx-configuration).

### Qualificação de rejeição

As qualificações de rejeição na tabela **[!UICONTROL Delivery log qualification]** do Campaign não são mais usadas para mensagens de erro de falha de delivery **síncrona**. O MTA aprimorado determinará o tipo de rejeição e a qualificação e enviará essas informações ao Campaign.

>[!NOTE]
>
>O MTA aprimorado qualifica a rejeição de SMTP e envia essa qualificação de volta ao Campaign no formato de um código de rejeição mapeado para um motivo de rejeição e qualificação do Campaign.

Para obter mais informações sobre qualificação de rejeição, consulte [esta seção](understanding-delivery-failures.md#bounce-mail-qualification).

### Taxa de transferência de delivery

O gráfico de taxa de transferência de delivery do Campaign não exibirá mais a taxa de transferência para os recipients de email. Ele mostrará a velocidade da taxa de transferência da transmissão de suas mensagens do Campaign para o MTA aprimorado.

Para obter mais informações sobre a taxa de transferência do delivery, consulte [esta seção](../../reporting/using/global-reports.md#delivery-throughput).

### Tentativas

As configurações de nova tentativa da entrega não são mais usadas pelo Campaign. As tentativas de rejeição temporária e o intervalo de tempo entre elas são determinados pelo MTA aprimorado com base no tipo e na gravidade das respostas de rejeição que retornam do domínio de email da mensagem.

Para obter mais informações sobre tentativas, consulte [esta seção](steps-sending-the-delivery.md#configuring-retries).

### Período de validade

A configuração do período de validade em seus deliveries do Campaign só será usada pelo MTA aprimorado se for definida como **3,5 dias ou menos**. Se você definir um valor superior a 3,5 dias no Campaign, ele não será levado em consideração.

Por exemplo, se o período de validade for definido como o valor padrão de 5 dias no Campaign, as mensagens com rejeição temporária entrarão na fila de tentativas do MTA aprimorado e serão repetidas apenas por até 3,5 dias a partir do momento em que a mensagem chegar ao MTA aprimorado. Nesse caso, o valor definido no Campaign não será usado.

Quando uma mensagem estiver na fila do MTA aprimorado por 3,5 dias e não for entregue, o tempo limite expirará, e seu status será atualizado de **[!UICONTROL Sent]** para **[!UICONTROL Failed]** nos logs do delivery.

Para obter mais informações sobre o período de validade, consulte [esta seção](steps-sending-the-delivery.md#defining-validity-period).

### Assinatura DKIM

A assinatura de autenticação de email DKIM (DomainKeys Identified Mail) é feita pelo MTA aprimorado. A assinatura DKIM pelo MTA nativo do Campaign será desativada na tabela Gerenciamento de domínio como parte da atualização do MTA aprimorado.
Para obter mais informações sobre DKIM, consulte o [Manual de práticas recomendadas de capacidade de delivery da Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=pt-BR#authentication).

### Relatórios de sucesso do delivery

Na exibição **[!UICONTROL Summary]** de um painel de [delivery de email](delivery-dashboard.md), a porcentagem de **[!UICONTROL Success]** começa em 100% e diminui progressivamente por todo o [período de validade do delivery](steps-sending-the-delivery.md#defining-validity-period), conforme as rejeições temporárias e permanentes são relatadas do MTA aprimorado para o Campaign.

De fato, todas as mensagens são exibidas como **[!UICONTROL Sent]** no [enviando logs](delivery-dashboard.md#delivery-logs-and-history) assim que são transmitidas com êxito do Campaign para o MTA aprimorado. Eles permanecem com esse status, a menos que uma [rejeição](understanding-delivery-failures.md#delivery-failure-types-and-reasons) para essa mensagem seja comunicada do MTA aprimorado para o Campaign.

Quando mensagens de rejeição permanente são relatadas do MTA aprimorado, seu status muda de **[!UICONTROL Sent]** para **[!UICONTROL Failed]** e a porcentagem de **[!UICONTROL Success]** é diminuída de maneira apropriada.

Quando mensagens de rejeição temporária são relatadas do MTA aprimorado, elas ainda são exibidas como **[!UICONTROL Sent]** e a porcentagem de **[!UICONTROL Success]** ainda não é atualizada. As mensagens de rejeição temporária são então [tentadas](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) durante todo o período de validade do delivery:

* Se uma tentativa for bem-sucedida antes do fim do período de validade, o status da mensagem permanecerá como **[!UICONTROL Sent]** e a porcentagem de **[!UICONTROL Success]** permanecerá inalterada.

* Caso contrário, o status mudará para **[!UICONTROL Failed]** e a porcentagem de **[!UICONTROL Success]** será diminuída de maneira apropriada.

Consequentemente, você deve aguardar até o fim do período de validade para ver a porcentagem final de **[!UICONTROL Success]** e o número final das mensagens **[!UICONTROL Sent]** e **[!UICONTROL Failed]**.

A tabela abaixo mostra as diferentes etapas no processo de envio com os KPIs correspondentes e os status dos logs de envio.

| Etapa do processo de envio | Resumo do KPI | Envio de status de logs |
|--- |--- |--- |
| A mensagem foi transmitida com êxito do Campaign para o MTA aprimorado | A porcentagem de **[!UICONTROL Success]** começa em 100% | Enviado |
| Mensagens com rejeição permanente são relatadas de volta do MTA aprimorado | A porcentagem de **[!UICONTROL Success]** é reduzida de maneira apropriada | Com falha |
| Mensagens com rejeição temporária são relatadas de volta do MTA aprimorado | Nenhuma alteração na porcentagem de **[!UICONTROL Success]** | Enviado |
| Tentativas de mensagens com rejeição temporária são bem-sucedidas | Nenhuma alteração na porcentagem de **[!UICONTROL Success]** | Enviado | A porcentagem de **[!UICONTROL Success]** é aumentada de maneira apropriada | Enviado |
| Falha nas tentativas de mensagens com rejeição temporária | A porcentagem de **[!UICONTROL Success]** é reduzida de maneira apropriada | Com falha |

