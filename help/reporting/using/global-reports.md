---
title: Relatórios globais
seo-title: Relatórios globais
description: Relatórios globais
seo-description: null
page-status-flag: never-activated
uuid: 83ea834e-08f7-441b-8f15-a25ec07c4aab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
discoiquuid: cc832666-ad18-49ce-afcc-f9169b683ae8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 18309c190c351cc57f7af24f48b2a772c1840319

---


# Relatórios globais {#global-reports}

Esses relatórios dizem respeito à atividade dos dados no banco de dados inteiro. To view the reports dashboard, go to the **[!UICONTROL Reports]** tab.

![](assets/s_ncs_user_report_delivery_link.png)

Para exibir relatórios, clique em seus nomes. Os seguintes relatórios estão disponíveis por padrão:

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>Esta seção mostra apenas os relatórios vinculados aos deliveries.

* **[!UICONTROL Delivery throughput]** : consulte a [Taxa de transferência](#delivery-throughput)de entrega.
* **[!UICONTROL Browsers]** : consulte [Navegadores](#browsers).
* **[!UICONTROL Sharing to social networks]** : consulte [Compartilhamento em redes](#sharing-to-social-networks)sociais.
* **[!UICONTROL Statistics on sharing activities]** : consultar [Estatísticas sobre atividades](#statistics-on-sharing-activities)de partilha.
* **[!UICONTROL Operating systems]** : consulte os sistemas [operacionais](#operating-systems).
* **[!UICONTROL URLs and click streams]** : consulte [URLs e fluxos de cliques](../../reporting/using/delivery-reports.md#urls-and-click-streams).
* **[!UICONTROL Tracking indicators]** : consulte os indicadores [de](../../reporting/using/delivery-reports.md#tracking-indicators)rastreamento.
* **[!UICONTROL Non-deliverables and bounces]** : consulte [Produtos não entregues e rejeições](#non-deliverables-and-bounces).
* **[!UICONTROL User activities]** : consulte as atividades [do usuário](#user-activities).
* **[!UICONTROL Subscription tracking]** : consulte o rastreamento [de](#subscription-tracking)assinatura.
* **[!UICONTROL Delivery summary]** : consulte o resumo [da entrega](../../reporting/using/delivery-reports.md#delivery-summary).
* **[!UICONTROL Delivery statistics]** : consulte as estatísticas [de](#delivery-statistics)entrega.
* **[!UICONTROL Breakdown of opens]** : consulte [Detalhamento das aberturas](#breakdown-of-opens).

## Taxa de transferência da entrega {#delivery-throughput}

Este relatório contém informações sobre a taxa de transferência de delivery da plataforma inteira por um determinado período. Para medir a velocidade em que as mensagens são entregues, os critérios são o número de mensagens enviadas por hora e o tamanho das mensagens (em bits por segundo). No exemplo abaixo, o primeiro gráfico mostra as entregas bem-sucedidas em azul e o número de deliveires incorretos em laranja.

![](assets/s_ncs_user_report_toolbar.png)

Você pode configurar os valores exibidos alterando a escala de tempo: Visualização de 1 hora, 3 horas, 24 horas etc. Clique **[!UICONTROL Refresh]** para confirmar sua seleção.

## Atividades do usuário {#user-activities}

Este relatório mostra o detalhamento de aberturas, cliques e transações por meia hora, hora ou dia, no formato de um gráfico.

![](assets/s_ncs_user_user_report.png)

As seguintes opções estão disponíveis:

* **[!UICONTROL Opens]** : Número total de mensagens abertas. Os emails no formato de texto não são considerados. For more information on tracking opens, refer to [Tracking opens](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** : Número total de cliques nos links nos deliveries. Cliques em links de unsubscription e mirror pages não são considerados.
* **[!UICONTROL Transactions]** : Número total de transações depois que uma mensagem é recebida. Para que uma transação seja considerada, uma tag do tipo de transação de rastreamento Web deve ser inserida na página da Web correspondente. A configuração de rastreamento Web é apresentada [nesta seção](../../configuration/using/about-web-tracking.md).

## Não entregues e rejeitados {#non-deliverables-and-bounces}

Este relatório mostra o detalhamento de não entregues, bem como uma análise de devoluções por domínio de Internet.

The **[!UICONTROL Number of messages processed]** represents the total number of messages processed by the delivery server. Esse valor é menor do que o número de mensagens a serem entregues quando alguns deliveries tiverem sido interrompidos ou pausados (antes de serem processados pelo servidor).

![](assets/s_ncs_user_errors_report.png)

**[!UICONTROL Breakdown of errors by type]**

>[!NOTE]
>
>Os erros exibidos nesse relatório acionam o processo de quarentena. Para obter mais informações sobre a gestão de quarentena, consulte [Gestão de Quarentena](../../delivery/using/understanding-quarantine-management.md).

A primeira seção desse relatório mostra o detalhamento de não entregues no formulário de uma tabela de valores e um gráfico.

Para cada tipo de erro, temos:

* o número de mensagens de erro desse tipo,
* a porcentagem de mensagens com erros desse tipo em comparação ao número total de mensagens com erros,
* a porcentagem de mensagens com erro desse tipo em comparação ao número total de mensagens processadas.

Os seguintes indicadores são usados:

* **[!UICONTROL User unknown]** : Tipo de erro gerado durante o delivery para indicar que o endereço de email é inválido.
* **[!UICONTROL Invalid domain]** : Tipo de erro gerado ao enviar um delivery para indicar que o domínio do endereço de email está errado ou não existe.
* **[!UICONTROL Inbox full]** : Tipo de erro gerado após cinco tentativas de delivery para indicar que a caixa de entrada dos recipients contém muitas mensagens.
* **[!UICONTROL Account disabled]** : Tipo de erro gerado ao enviar um delivery para indicar que o endereço não existe mais.
* **[!UICONTROL Rejected]** : Tipo de erro gerado quando um endereço é rejeitado pelo IAP (Provedor de Acesso à Internet), por exemplo, ao seguir uma regra de segurança da aplicação (software antispam).
* **[!UICONTROL Unreachable]** : Tipo de erro que ocorre na cadeia de caracteres de distribuição de mensagens: incidente na retransmissão SMTP, domínio temporariamente inacessível, etc
* **[!UICONTROL Not connected]** : Tipo de erro para indicar que o celular do recipient está desligado ou desconectado da rede no momento do envio.

   >[!NOTE]
   >
   >Esse indicador apenas diz respeito aos canais móveis. Para obter mais informações, consulte [esta seção](../../delivery/using/sms-channel.md).

   You can open up each line of the value table by clicking the `[+]` symbol. Para cada tipo de erro, é possível exibir o detalhamento das mensagens de erro por domínio.

   ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

A segunda seção desse relatório mostra o detalhamento de erros por domínio da Internet na forma de uma tabela de valores e um gráfico.

Para cada nome de domínio, temos:

* o número de mensagens com erros para esse domínio,
* a porcentagem de mensagens com erros para esse domínio em comparação ao número total de mensagens processadas para este domínio,
* a porcentagem de mensagens de erro para esse domínio em comparação ao número total de mensagens de erro.

You can open up each line of the value table by clicking the [+] symbol. Para cada tipo de domínio, é possível exibir o detalhamento das mensagens de erro por tipo de erro.

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>Os nomes de domínio exibidos nesse relatório são definidos em nível de cubo. Para alterar esses valores, edite o **[!UICONTROL Delivery logs (broadlogrcp)]** cubo. Para obter mais informações, consulte [esta seção](../../reporting/using/about-cubes.md). The **[!UICONTROL Others]** category includes domain names that don&#39;t belong to a specific class.

## Navegadores {#browsers}

Este relatório mostra o detalhamento dos navegadores da Internet usados pelos recipients do delivery para o período relacionado.

>[!NOTE]
>
>Os valores mostrados nesse relatório são estimativas: apenas recipients que clicaram em um delivery serão considerados.

**Estatísticas globais**

As estatísticas globais no uso do navegador são apresentadas na forma de uma tabela de valores e um gráfico.

![](assets/dlv_explorers_report.png)

Os seguintes indicadores são usados:

* **[!UICONTROL Visitors]** : Número total de recipients alvos (por navegador de Internet) e que clicaram em um delivery pelo menos uma vez.
* **[!UICONTROL Pages viewed]** : Número total de cliques nos links em um delivery (por navegador de Internet) para todos os deliveries.
* **[!UICONTROL Usage rate]** : Essa taxa representa o detalhamento dos visitantes (por navegador de Internet) em relação ao número total de visitantes.

**Estatísticas por navegador**

Na tabela de valores de estatística global, você pode clicar em cada nome de navegador para exibir suas estatísticas de uso.

![](assets/s_ncs_user_explorers_report2.png)

As estatísticas são apresentadas no formato de uma curva, um gráfico e uma tabela de valores.

The **[!UICONTROL History]** curve represents the attendance rate of this browser per day. A taxa é a relação do número de visitantes por dia (nesse navegador) em comparação ao número de visitantes medidos no dia com a maior taxa de presença.

The **[!UICONTROL Breakdown per version]** chart represents the breakdown of visitors per version compared to the total number of visitors (on this browser).

A tabela de valores usa os seguintes indicadores:

* **[!UICONTROL Global rate]** : Essa taxa representa o detalhamento dos visitantes por versão em comparação ao número total de visitantes (em todos os navegadores).
* **[!UICONTROL Relative rate]** : Essa taxa representa o detalhamento dos visitantes por versão em comparação ao número total de visitantes (nesse navegador).

### Compartilhamento em redes sociais {#sharing-to-social-networks}

O marketing viral permite que os recipients do delivery compartilhem informações com sua rede de contatos: eles podem adicionar um link ao seu perfil (Facebook, Twitter, etc.) ou enviar uma mensagem para um amigo. Cada compartilhamento e cada acesso às informações compartilhadas é controlado no delivery. Para obter mais informações sobre marketing viral, consulte [esta seção](../../delivery/using/viral-and-social-marketing.md).

Esse relatório mostra o detalhamento de mensagens compartilhadas e abertas em redes sociais (Facebook, Twitter, etc.) e/ou por email.

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

Nas estatísticas de delivery de email, dois valores são exibidos:

* **[!UICONTROL Number of messages to be delivered]** : Número total de mensagens processadas durante a análise de delivery.
* **[!UICONTROL Number of successful deliveries]** : Número de mensagens processadas com êxito.

**[!UICONTROL Sharing activities and mail open statistics]**

A tabela central exibe as estatísticas de compartilhamentos de email e aberturas.

In the **[!UICONTROL Shares]** column, we have the following indicators:

* **[!UICONTROL No. of sharing activities]** : Número total de mensagens compartilhadas em cada rede social. This value equals the total number of clicks on the icon of the matching **[!UICONTROL Links for sharing to social networks]** personalization block.
* **[!UICONTROL Breakdown]** : Essa taxa representa o detalhamento de compartilhamentos por rede social, em relação ao número total de compartilhamentos.
* **[!UICONTROL Sharing rate]** : Essa taxa representa o detalhamento de compartilhamentos por rede social, em relação ao número de mensagens a serem entregues.

In the **[!UICONTROL Opens]** column, we have the following indicators:

* **[!UICONTROL No. of opens]** : O número total de mensagens abertas por pessoas às quais a mensagem foi encaminhada (por meio do bloco de **[!UICONTROL Links for sharing to social networks]** personalização). Esse valor é igual ao número de vezes de exibição da mirror page. Aberturas por recipients de delivery não são considerados.
* **[!UICONTROL Breakdown]** : Essa taxa representa o detalhamento de aberturas por rede social, em relação ao número total de aberturas.
* **[!UICONTROL Rate of opens]** : Essa taxa representa o detalhamento de aberturas por rede social, em relação ao número total de compartilhamentos.

**[!UICONTROL Breakdown of sharing activities and opens]**

Esta seção inclui dois gráficos que representam o detalhamento de atividades de compartilhamento e aberturas por rede social.

## Estatísticas de atividades de compartilhamento {#statistics-on-sharing-activities}

Esse relatório exibe a evolução dos compartilhamentos em redes sociais (Facebook, Twitter, email, etc.).

Para obter mais informações sobre marketing viral, consulte [esta seção](../../delivery/using/viral-and-social-marketing.md).

![](assets/s_ncs_user_social_report2.png)

As estatísticas são apresentadas no formato de uma tabela de valores e um gráfico.

Os seguintes indicadores são usados:

* **[!UICONTROL New contacts]** : Número de novas subscrições após o recebimento de uma mensagem compartilhada por email. This value matches the number of people who received a message shared via email, clicked the **[!UICONTROL Subscription link]** and filled in the subscription form.
* **[!UICONTROL Opens]** : O número total de mensagens abertas por pessoas para as quais a mensagem foi transferida (por meio do bloco de **[!UICONTROL Link for sharing to social networks]** personalização). Esse valor é igual ao número de vezes de exibição da mirror page. Aberturas por recipients de delivery não são considerados.
* **[!UICONTROL Sharing activities]** : Número total de mensagens compartilhadas em redes sociais. This value matches the total number of clicks on the icon of the **[!UICONTROL Links for sharing to social networks]** personalization block.

## Sistemas operacionais {#operating-systems}

Este relatório exibe o detalhamento dos sistemas operacionais usados pelos recipients de delivery do período relacionado.

>[!NOTE]
>
>Os valores mostrados nesse relatório são estimativas: apenas recipients que clicaram em um delivery serão considerados.

**Estatísticas globais**

As estatísticas de uso global dos sistemas operacionais são apresentadas no formato de uma tabela de valores e um gráfico.

![](assets/s_ncs_user_os_report.png)

Os seguintes indicadores são usados:

* **[!UICONTROL Visitors]** : Média diária do número total de recipients alvos (por sistema operacional) que clicaram em um delivery pelo menos uma vez.
* **[!UICONTROL Pages viewed]** : Média diária do número total de cliques nos links de delivery (por sistema operacional) para todos os deliveries.
* **[!UICONTROL Rate of use]** : Essa taxa representa o detalhamento dos visitantes (por sistema operacional) em relação ao número total de visitantes.

**Estatísticas por sistema operacional**

Na tabela de valores de estatística global, clique no nome de cada sistema operacional para exibir as estatísticas por sistema operacional.

![](assets/s_ncs_user_os_report2.png)

As estatísticas são apresentadas no formato de uma curva, um gráfico e uma tabela de valores.

The **[!UICONTROL History]** curve represents the rate of use of this operating system per day. Essa taxa é a relação do número de visitantes por dia (neste sistema operacional) em relação ao número de visitantes medidos no dia com a maior participação.

The **[!UICONTROL Breakdown by version]** chart represents the breakdown of visitors per version in relation to the total number of visitors on this operating system.

A tabela de valores usa os seguintes indicadores:

* **[!UICONTROL Global rate]** : Essa taxa representa o detalhamento dos visitantes (por versão) em relação ao número total de visitantes em todos os sistemas operacionais.
* **[!UICONTROL Relative rate]** : Essa taxa representa o detalhamento dos visitantes (por versão) em relação ao número total de visitantes desse sistema operacional.

## Rastreamento de subscrição {#subscription-tracking}

Este relatório permite monitorar subscrições de serviços de informação. Ele mostra subscrições e unsubscriptions.

![](assets/s_ncs_user_services_report.png)

It can be displayed for a subscription by clicking the **[!UICONTROL Profiles and targets > Services and subscriptions]** node of the home page or the explorer. Select the desired subscription, and then click the **[!UICONTROL Reports]** tab. O **[!UICONTROL Subscriptions tracking]** relatório está disponível por padrão. Ele permite ver as tendências de subscrição e unsubscription e a taxa de fidelidade por um período. Você pode configurar a representação desses dados pela lista suspensa. Click **[!UICONTROL Refresh]** to validate the selected configuration.

Para obter mais informações, consulte [esta página](../../delivery/using/managing-subscriptions.md).

The **[!UICONTROL Number subscribed to date]** represents the total number of people currently subscribed.

**[!UICONTROL Overall evolution of subscriptions]**

A tabela de valores usa os seguintes indicadores:

* **[!UICONTROL Subscribers]** : Número total de assinantes do período relacionado.
* **[!UICONTROL Subscriptions]** : Número de subscrições do período relacionado.
* **[!UICONTROL Unsubscriptions]** : Número de unsubscriptions do período relacionado.
* **[!UICONTROL Evolution]** : Número de unsubscriptions menos o número de subscrições. A taxa é calculada com base no número total de assinantes.
* **[!UICONTROL Loyalty]** : Taxa de fidelidade de assinantes do período relacionado.

**[!UICONTROL Subscription evolution curves]**

Este gráfico mostra a evolução das subscrições e unsubscriptions para o período relacionado.

## Estatísticas de delivery {#delivery-statistics}

Este relatório mostra o detalhamento por domínio de Internet, de todas as mensagens processadas e enviadas, de devoluções permanentes e temporárias, aberturas, cliques e unsubscriptions.

![](assets/s_ncs_user_broadcast_report.png)

Os seguintes indicadores são usados:

* **[!UICONTROL Emails processed]** : Número total de mensagens processadas pelo servidor de delivery.
* **[!UICONTROL Delivered]** : porcentagem do número de mensagens processadas com êxito em comparação ao número total de mensagens processadas.
* **[!UICONTROL Hard bounces]** : porcentagem do número de rejeições &quot;duras&quot; em comparação ao número total de mensagens processadas.
* **[!UICONTROL Soft bounces]** : porcentagem do número de rejeições &quot;suaves&quot; em comparação ao número total de mensagens processadas.

   >[!NOTE]
   >
   >Para obter mais informações sobre devoluções permanentes e temporárias, consulte [Gestão de Quarentena](../../delivery/using/understanding-quarantine-management.md).

* **[!UICONTROL Opens]** : porcentagem do número de recipients alvos que abriram uma mensagem pelo menos uma vez em comparação ao número de mensagens processadas com êxito.
* **[!UICONTROL Clicks]** : porcentagem do número de pessoas que clicaram em um delivery pelo menos uma vez em comparação ao número de mensagens processadas com êxito.
* **[!UICONTROL Unsubscription]** : porcentagem do número de cliques em um link de cancelamento de assinatura em comparação ao número de mensagens processadas com êxito.

## Detalhamento de aberturas {#breakdown-of-opens}

Este relatório mostra o detalhamento de aberturas por sistema operacional, dispositivo e navegador para o período relacionado. Para cada categoria, dois gráficos são usados. O primeiro exibe estatísticas referentes a aberturas em um computador e dispositivos móveis. O segundo exibe estatísticas relacionadas apenas a aberturas em dispositivos móveis.

O número de aberturas corresponde ao número total de mensagens abertas. Os emails em formato de texto não são contados. For more information on Tracking opens, refer to the [Tracking opens](../../reporting/using/indicator-calculation.md#tracking-opens-) section.

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>Os nomes do navegador e do sistema operacional fazem parte das informações enviadas pelo agente do usuário do navegador em que o email foi aberto. O Adobe Campaign deduz o tipo de dispositivo usando as informações do dispositivo.