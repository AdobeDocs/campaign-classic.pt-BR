---
product: campaign
title: S com o MTA aprimorado no Adobe Campaign Classic
description: Saiba mais sobre o escopo e as especificidades do envio de emails com o MTA aprimorado do Adobe Campaign
feature: Email
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '1946'
ht-degree: 99%

---

# Envio com o MTA aprimorado {#sending-with-enhanced-mta}

![](../../assets/common.svg)

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

O Adobe Campaign agora pode ser atualizado para usar um novo MTA (Mail Transfer Agent, agente de transferência de correspondência) que executa o MTA de email comercial do SparkPost chamado **Momentum**.

O Momentum representa uma tecnologia MTA inovadora e de alto desempenho, que inclui um tratamento mais inteligente de rejeição e um recurso automatizado de otimização de entrega que ajuda os remetentes a alcançarem e manterem as taxas ideais de delivery da caixa de entrada. <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

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

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
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

Qualquer delivery que tenha sido preparado antes de sua instância ter sido atualizada para usar o MTA aprimorado precisará ser preparado novamente para usar de maneira correta o novo MTA.

Para os clientes que usam a funcionalidade de mensagens transacionais do Adobe Campaign, todas as chamadas à API para acionar um email serão enfileiradas durante o curto tempo de inatividade da atualização e serão tentadas após a conclusão da atualização.

## Especificidades do MTA aprimorado {#enhanced-mta-impacts}

### Cabeçalhos do MTA aprimorado

As instâncias mais recentes do Campaign Classic incluem código que adiciona os cabeçalhos do MTA aprimorado necessários a cada mensagem. Se estiver usando o Adobe Campaign 19.1 (compilação 9032) ou superior e se esse não for o caso, você deverá solicitar ao [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) que adicione o parâmetro &quot;useMomentum=true&quot; à configuração da instância de execução (no arquivo [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)), que pode ser a instância de marketing, [a instância de mid-sourcing](../../installation/using/mid-sourcing-server.md) ou a [instância de execução de mensagens transacionais](../../message-center/using/configuring-instances.md#execution-instance), dependendo da sua configuração.

No entanto, se você estiver usando uma instância mais antiga que não inclui esse código, uma nova regra de tipologia chamada **[!UICONTROL Typology Rule for Enhanced MTAs]** deverá ser adicionada a todas as tipologias existentes na instância do Campaign.
Essa regra é adicionada por um pacote **[!UICONTROL Typology]** instalado como parte da atualização para o MTA aprimorado.

>[!IMPORTANT]
>
>Se você vir essa regra de tipologia em suas tipologias, não a exclua nem modifique de forma alguma. Caso contrário, seus deliveries de email poderão ser prejudicados.

Este pacote de **[!UICONTROL Typology]** precisa ser instalado na instância de marketing do Adobe Campaign.

Se você for um cliente híbrido, a equipe do Adobe Campaign fornecerá instruções sobre como instalar o pacote de **[!UICONTROL Typology]** em sua instância de marketing como parte da atualização para o MTA aprimorado. Entre em contato com o executivo de sua conta para obter as instruções completas.

>[!IMPORTANT]
>
>As instruções fornecidas pela equipe do Adobe Campaign sobre como instalar o pacote de **[!UICONTROL Typology]** devem ser cuidadosamente seguidas. Caso contrário, você poderá encontrar sérios problemas em seus IPs usados para enviar emails.

Para obter mais informações sobre topologias, consulte[esta seção](../../campaign-opt/using/about-campaign-typologies.md).

### Novas regras de MX

As regras de taxa de transferência de delivery de gerenciamento de MX não são mais usadas. O MTA aprimorado tem suas próprias regras de MX, que permitem personalizar a taxa de transferência por domínio com base em sua própria reputação de email histórica e no feedback em tempo real proveniente dos domínios para os quais você está enviando emails.

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

>[!NOTE]
>
>Com o recurso [Serviço de feedback de email](#email-feedback-service) (EFS) (atualmente disponível na versão beta), o gráfico da taxa de transferência de delivery do Campaign ainda mostra a taxa de transferência para seus destinatários de email.

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

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### Serviço de feedback por email (beta) {#email-feedback-service}

Com o recurso Serviço de feedback por email (EFS), o status de cada email é relatado com precisão, pois o feedback é capturado diretamente do MTA aprimorado (Agente de transferência de mensagem).

>[!IMPORTANT]
>
>O Serviço de feedback por email está disponível no momento como um recurso beta.
>
>Se você estiver interessado em participar desse programa beta, preencha [este formulário](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) e entraremos em contato com você.

Depois que o delivery é iniciado, não há alteração na porcentagem de **[!UICONTROL Success]** quando a mensagem é transmitida com êxito do Campaign para o MTA aprimorado.

<!--![](assets/efs-sending.png)-->

Os logs do delivery mostram o status **[!UICONTROL Taken into account by the service provider]** para cada endereço direcionado.

<!--![](assets/efs-pending.png)-->

Quando a mensagem é realmente entregue aos perfis direcionados e uma vez que essas informações são relatadas em tempo real do MTA aprimorado, os logs do delivery mostram o status **[!UICONTROL Sent]** para cada endereço que recebeu a mensagem com êxito. A porcentagem de **[!UICONTROL Success]** aumenta de acordo com cada delivery bem-sucedido.

Quando mensagens com rejeição permanente são relatadas do MTA aprimorado, o status do log muda de **[!UICONTROL Taken into account by the service provider]** para **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

Quando mensagens com rejeição temporária são relatadas do MTA aprimorado, o status do log permanece inalterado (**[!UICONTROL Taken into account by the service provider]**): somente o [motivo do erro](understanding-delivery-failures.md#delivery-failure-types-and-reasons) é atualizado<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. A porcentagem de **[!UICONTROL Success]** permanece inalterada. As mensagens com rejeição temporária são então repetidas durante todo o [período de validade do delivery](steps-sending-the-delivery.md#defining-validity-period)

* Se uma nova tentativa for bem-sucedida antes do fim do período de validade, o status da mensagem mudará para **[!UICONTROL Sent]** e a porcentagem **[!UICONTROL Success]** será aumentada de maneira apropriada.

* Caso contrário, o status mudará para **[!UICONTROL Failed]**. A porcentagem de **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->permanece inalterada.

>[!NOTE]
>
>Para obter mais informações sobre rejeições permanentes e temporárias, consulte [esta seção](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Para obter mais informações sobre tentativas após uma falha temporária de delivery, consulte [esta seção](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


As tabelas abaixo mostram as alterações nos KPIs e no envio de status de logs introduzidos pelo recurso EFS.

**Com o serviço de feedback por email**

| Etapa do processo de envio | Resumo do KPI | Envio de status de logs |
|--- |--- |--- |
| A mensagem foi transmitida com êxito do Campaign para o MTA aprimorado | A porcentagem de **[!UICONTROL Success]** não é exibida (começa em 0%) | Levado em consideração pelo provedor de serviço |
| Mensagens com rejeição permanente são relatadas de volta do MTA aprimorado | Nenhuma alteração na porcentagem de **[!UICONTROL Success]** | Com falha |
| Mensagens com rejeição temporária são relatadas de volta do MTA aprimorado | Nenhuma alteração na porcentagem de **[!UICONTROL Success]** | Levado em consideração pelo provedor de serviço |
| Tentativas de mensagens com rejeição temporária são bem-sucedidas | A porcentagem de **[!UICONTROL Success]** é aumentada de maneira apropriada | Enviada |
| Falha nas tentativas de mensagens com rejeição temporária | Nenhuma alteração na porcentagem de **[!UICONTROL Success]** | Com falha |

**Sem Serviço de feedback por email**

| Etapa do processo de envio | Resumo do KPI | Envio de status de logs |
|--- |--- |--- |
| A mensagem foi transmitida com êxito do Campaign para o MTA aprimorado | A porcentagem de **[!UICONTROL Success]** começa em 100% | Enviada |
| Mensagens com rejeição permanente são relatadas de volta do MTA aprimorado | A porcentagem de **[!UICONTROL Success]** é reduzida de maneira apropriada | Com falha |
| Mensagens com rejeição temporária são relatadas de volta do MTA aprimorado | Nenhuma alteração na porcentagem de **[!UICONTROL Success]** | Enviada |
| Tentativas de mensagens com rejeição temporária são bem-sucedidas | Nenhuma alteração na porcentagem de **[!UICONTROL Success]** | Enviada | A porcentagem de **[!UICONTROL Success]** é aumentada de maneira apropriada | Enviada |
| Falha nas tentativas de mensagens com rejeição temporária | A porcentagem de **[!UICONTROL Success]** é reduzida de maneira apropriada | Com falha |
