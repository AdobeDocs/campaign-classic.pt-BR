---
product: campaign
title: Cálculo do indicador
description: Cálculo do indicador
badge: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
feature: Reporting, Monitoring
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '2979'
ht-degree: 100%

---

# Cálculo do indicador {#indicator-calculation}



## Atividades do usuário {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Aberturas<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Soma de todos os @totalClicks com uma chave primária de URL igual a 1.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Cliques<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> Soma de todos os @totalClicks com um tipo de URL igual a "Clique de email".<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transações<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> Soma de todos os @totalClicks com um tipo de URL igual a "Transação".<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

Este relatório é baseado na tabela **[!UICONTROL Consolidated tracking]** (nms:trackingStats). Essa tabela de agregação é usada por motivos de desempenho ao exibir relatórios em vez da tabela **[!UICONTROL Recipient tracking logs]** (nms:trackingLogRcp), e não é calculada em tempo real. A tabela é gerada alguns minutos após os logs de rastreamento serem recuperados. Se os indicadores estiverem atualizados, os resultados serão iguais aos indicadores do relatório **Indicadores de rastreamento.** O indicador @totalclicks expressa o número total de cliques em um período de 5 minutos.

## Não entregues e devolvidos {#non-deliverables-and-bounces-1}

**Detalhamento por tipo de erro**

Este relatório é baseado na tabela **[!UICONTROL Delivery and tracking statistics]**(nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Número total de mensagens processadas<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> Soma de mensagens com status igual a "Pronta", "Enviada" ou "Falha".<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Usuário desconhecido<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> Contagem de todas as mensagens com status igual a "Falha" e uma razão igual a "Usuário desconhecido". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> Inacessível <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> Contagem de todas as mensagens com status igual a "Falha" e uma razão igual a "Inacessível". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejeitada<br /> </td> 
   <td> @refused<br /> </td> 
   <td> Contagem de todas as mensagens com status igual a "Falha" e uma razão igual a "Rejeitada". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Domínio inválido<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> Contagem de todas as mensagens com status igual a "Falha" e uma razão igual a "Domínio Inválido". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> Conta desabilitada<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> Contagem de todas as mensagens com status igual a "Falha" e uma razão igual a "Conta desabilitada".<br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> Caixa de entrada cheia<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> Contagem de todas as mensagens com status igual a "Falha" e uma razão igual a "Caixa de entrada cheia". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Erros<br /> </td> 
   <td> @value<br /> </td> 
   <td> Número de mensagens com falha desse tipo de erro.<br /> </td> 
   <td> Count(@status=2 e msg/@failureReason="Valor do tipo de erro")<br /> </td> 
  </tr> 
  <tr> 
   <td> Contribuição<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentagem de erros desse tipo em comparação ao número total de mensagens de erro.<br /> </td> 
   <td> percent(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Detalhamento<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentagem de erros desse tipo em comparação ao número total de mensagens processadas.<br /> </td> 
   <td> percent(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Detalhamento por domínio**

A segunda parte do relatório detalha a análise de mensagens com falha por domínio da Internet, ao contrário do tipo de erro. A fórmula vinculada ao indicador **Error** (@value) neste caso é: Count(@status=2 e @domain=&quot;Valor do nome de domínio&quot;), isto é, uma contagem de todas as mensagens com um status de falha para este domínio.

## Navegadores {#browsers-1}

Este relatório é baseado na tabela **[!UICONTROL Internet Browser Statistics]** (nms:userAgentsStats).

**Estatísticas globais**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Visitantes<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> Número total de recipients alvos para esse navegador que clicaram em um delivery pelo menos uma vez.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Exibições de página<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> Número total de cliques nos links de delivery usando esse navegador, para todos os deliveries.<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa de uso<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentagem de visitantes desse navegador em comparação ao número total de visitantes.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**Estatísticas por navegador**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Taxa de uso<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> Porcentagem do número de visitantes por dia usando esse navegador em comparação ao número de visitantes medidos no dia com mais visitas.<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa global<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentagem de visitantes dessa versão em comparação ao número total de visitantes que usam todos os navegadores.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Peso relativo<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentagem de visitantes dessa versão em comparação ao número total de visitantes que usam esse navegador.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Compartilhamento em redes sociais {#sharing-to-social-networks-1}

Este relatório é baseado nas tabelas **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) e **[!UICONTROL Web tracking]** (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Número de mensagens a serem enviadas<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Número total de mensagens processadas durante a análise de delivery.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Número de deliveries bem-sucedidos<br /> </td> 
   <td> @success<br /> </td> 
   <td> Número de mensagens processadas com êxito <br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Email<br /> </td> 
   <td> @email<br /> </td> 
   <td> Soma de todos os @totalClicks para os quais a categoria de URL é igual a "email".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Soma de todos os @totalClicks para os quais a categoria de URL é igual a "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Soma de todos os @totalClicks para os quais a categoria de URL é igual a "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Soma de todos os @totalClicks para os quais a categoria de URL é igual a "delicious".<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Soma de todos os @totalClicks para os quais a categoria de URL é igual a "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Soma de todos os @totalClicks para os quais a categoria de URL é igual a "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Soma de todos os @totalClicks para os quais a categoria de URL é igual a "linkedin".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Compartilhamentos**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Número de compartilhamentos<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Número total de mensagens compartilhadas nessa rede social.<br /> </td> 
   <td> Sum(iIf([url/@category]="Valor do tipo de rede social",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Detalhamento<br /> </td> 
   <td> @percent<br /> </td> 
   <td> Porcentagem do número de compartilhamentos nessa rede social em comparação ao número total de compartilhamentos.<br /> </td> 
   <td> percent(@forward, sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa de compartilhamento<br /> </td> 
   <td> @rate<br /> </td> 
   <td> Número de compartilhamentos nessa rede em comparação ao número de mensagens a serem entregues.<br /> </td> 
   <td> @forward / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Aberturas**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Número de aberturas <br /> </td> 
   <td> @open<br /> </td> 
   <td> Número total de linhas de rastreamento na tabela de rastreamento Web.<br /> </td> 
   <td> Contagem<br /> </td> 
  </tr> 
  <tr> 
   <td> Detalhamento<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> Porcentagem do número de aberturas nessa rede social em comparação ao número total de aberturas.<br /> </td> 
   <td> percent(@open, sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa de aberturas<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> O número de aberturas nessa rede social em comparação ao número total de mensagens a serem entregues.<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Estatísticas de atividades de compartilhamento {#statistics-on-sharing-activities-1}

Este relatório é baseado nas tabelas **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) e **[!UICONTROL Web tracking]** (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Novos contatos<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> Contagem do número de visitantes vinculados a um recipient.<br /> </td> 
   <td> Fórmula: count(@id)<br /> Filtro: @recipient-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> Aberturas<br /> </td> 
   <td> @opened<br /> </td> 
   <td> Contagem de @ids com um tipo de URL igual a "Abrir".<br /> </td> 
   <td> count(Iif([url/@type]=2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Compartilhamentos<br /> </td> 
   <td> @shared<br /> </td> 
   <td> A categoria de URL incluída em 'email' , 'facebook' , 'twitter' , 'delicious' , 'digg' , 'google' , 'linkedin'<br /> Contagem de todos os @totalClicks com uma categoria de URL que equivalha a "email", "facebook", "twitter", "delicious", "digg", "google" ou "linkedin".<br /> </td> 
   <td> contagem (Iif([url/@category] IN ("email" , "facebook" , "twitter" , "delicious" , "digg" , "google" , "linkedin"), @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Sistemas operacionais {#operating-systems-1}

Este relatório é baseado na tabela **[!UICONTROL Internet Browser Statistics]** (nms:userAgentsStats).

**Estatísticas globais**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Visitantes<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> Média diária do número total de recipients alvos por sistema operacional que clicaram em um delivery pelo menos uma vez.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Páginas exibidas<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> Média diária do número total de cliques nos links de delivery por sistemas operacionais para todos os deliveries.<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa de uso<br /> </td> 
   <td> -<br /> </td> 
   <td> Detalhamento de visitantes por sistema operacional em comparação ao número total de visitantes.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Estatísticas por sistema operacional**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Taxa de uso<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> Porcentagem do número de visitantes por dia nesse sistema operacional em comparação ao número de visitantes medidos no dia com mais visitas.<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa global<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentagem de visitantes por versão em comparação ao número total de visitantes em todos os sistemas operacionais.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa relativa<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentagem de visitantes por versão em comparação ao número total de visitantes que usam esse sistema operacional.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rastreamento de assinatura {#subscription-tracking-1}

Este relatório é baseado na tabela **[!UICONTROL Services]** (nms:service).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Registrado<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> Contagem de pessoas registradas no dia anterior.<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Subscrições<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> contagem de subscrições (@action = 1) no dia anterior.<br /> </td> 
   <td> sum(Iif(@action = 1 e @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Cancelamentos de assinatura<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> contagem de unsubscriptions (ação = 0) no dia anterior.<br /> </td> 
   <td> sum(Iif(@action = 0 e @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Evolução<br /> </td> 
   <td> -<br /> </td> 
   <td> Número de subscrições menos o número de unsubscriptions. A taxa é calculada em relação ao número total de assinantes.<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription), '+', '')+format(@_subscription - @_unsubscription, 'number', '# ##0')+ Iif(@_subscriber&gt;0,' (' + format(100*percent(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.00')+ '%)','')<br /> </td> 
  </tr> 
  <tr> 
   <td> Fidelidade<br /> </td> 
   <td> -<br /> </td> 
   <td> Taxa de fidelidade do assinante para o período relacionado.<br /> </td> 
   <td> 1-percent(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Indicadores de rastreamento {#tracking-indicators-1}

Este relatório é baseado nas tabelas **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats) e **[!UICONTROL Consolidated tracking]** (nms:trackingStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Mensagens a entregar<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Contagem do número de broadLogs após a análise de target.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Êxito<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Contagem de mensagens para as quais o campo "seed address" é igual a "Não" e com um status igual a "Considerado pelo provedor de serviços" ou "Enviado" ou "Recebido no celular".<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Aberturas distintas no público alcançado<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> Extrapolação do número de aberturas distintas para todos os emails com base no número de aberturas distintas para emails em formato html.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@recipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Soma de aberturas no público alcançado<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> Extrapolação do número total de aberturas para todos os emails com base no número total de emails em formato html.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Cliques no link de unsubscription<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Contagem de @ids com uma categoria de URL igual a "Opt out".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Cliques no link para a mirror page<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> Contagem de @ids com uma categoria de URL igual a "Mirror page".<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Estimativa de encaminhamentos<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Diferença entre o número de pessoas distintas e o número de recipients distintos que clicaram no email pelo menos uma vez.<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> Envios<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Contagem das mensagens para as quais o campo "seed address" é igual a "Não" e com um status igual a "considerado pelo recipient" ou "Enviado" ou "Recebido em celular".<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Reclamações<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> Contagem de mensagens com status igual a "Falha" e uma razão igual a "endereço incluído na lista de bloqueios".<br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> Aberturas<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Contagem de todos os @broadLog-ids em todos os logs de rastreamento.<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Cliques<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Contagem distinta de @broadLog-ids com um tipo de URL igual a "clique de email". <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Reatividade bruta<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentagem do número de recipients que clicaram em um delivery pelo menos uma vez em comparação ao número de recipients que abriram um delivery pelo menos uma vez.<br /> </td> 
   <td> percent(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> Cliques distintos no público alcançado<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Contagem de @source-ids com uma categoria de URL igual a "clique de email".<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Cliques acumulados<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> Contagem de @ids com uma categoria de URL que é igual a "clique de mail".<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Cliques do recipient<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Contagem distinta de @broadLog-ids com um tipo de URL que é igual a "clique de mail".<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Reatividade estimada<br /> </td> 
   <td> -<br /> </td> 
   <td> Taxa do número de recipients que clicaram em um delivery pelo menos uma vez em comparação à estimativa de recipients que abriram o delivery pelo menos uma vez.<br /> </td> 
   <td> percent(@recipientClick, @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> Páginas visitadas<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> Contagem de @ids com um tipo de URL igual a "Web" ou "Transação".<br /> </td> 
   <td> count(Iif([url/@type]=4 or [url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transações<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> Contagem de @ids com um tipo de URL igual a "Transação".<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Valor total<br /> </td> 
   <td> @amount<br /> </td> 
   <td> Soma de webTrackingLog/@amounts com um tipo de URL igual a "Transação". <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Valor médio da transação<br /> </td> 
   <td> -<br /> </td> 
   <td> Taxa do valor total em comparação ao número de transações.<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Itens<br /> </td> 
   <td> @article<br /> </td> 
   <td> Soma de webTrackingLog/@articles com um tipo de URL que é igual a "Transação".<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Número médio de itens por transação<br /> </td> 
   <td> -<br /> </td> 
   <td> Taxa do número de itens em comparação ao número de transações.<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Valor médio por mensagem<br /> </td> 
   <td> -<br /> </td> 
   <td> Taxa do valor total em comparação ao número de mensagens a serem entregues.<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> Email<br /> </td> 
   <td> @email<br /> </td> 
   <td> Soma de todos os @totalClicks com uma categoria de URL que é igual a "email".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Soma de todos os @totalClicks com uma categoria de URL que é igual a "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Soma de todos os @totalClicks com uma categoria de URL que é igual a "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Soma de todos os @totalClicks com uma categoria de URL que é igual a "delicious".<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Soma de todos os @totalClicks com uma categoria de URL que é igual a "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Soma de todos os @totalClicks com uma categoria de URL que é igual a "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Soma de todos os @totalClicks com uma categoria de URL que é igual a "linkedin".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Fluxos de clique e URLs {#urls-and-click-streams-1}

Este relatório é baseado na tabela **[!UICONTROL Delivery]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Reatividade<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> Taxa do número de recipients alvos que clicaram em um delivery pelo menos uma vez em comparação ao número estimado de recipients alvos que abriram um delivery pelo menos uma vez.<br /> </td> 
   <td> percent([indicators/@recipientClick], [indicators/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> Cliques distintos<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> Taxa do número de pessoas distintas que clicaram em um delivery pelo menos uma vez em comparação ao número de mensagens entregues com êxito.<br /> </td> 
   <td> percent([indicators/@personClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Cliques acumulados<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> Taxa do número total de cliques por recipients alvos em comparação ao número de mensagens entregues com êxito.<br /> </td> 
   <td> percent([indicators/@totalRecipientClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Cliques<br /> </td> 
   <td> @_click<br /> </td> 
   <td> Contagem de @totalClicks com uma chave primária de URL diferente de 1<br /> </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Cliques (%)<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentagem do número de cliques em comparação ao número total de cliques acumulados.<br /> </td> 
   <td> percent(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Resumo da entrega {#delivery-summary-1}

Este relatório é baseado na tabela **[!UICONTROL Delivery]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Público inicial<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Número total de recipients alvos do delivery.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Mensagens rejeitadas pela regra<br /> </td> 
   <td> @reject<br /> </td> 
   <td> Número de endereços ignorados durante a análise ao manter as regras de tipologia: endereço não especificado, em quarentena, incluído na lista de bloqueios, etc.<br /> </td> 
   <td> sum([properties/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> Mensagens a entregar<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Número total de mensagens a serem entregues após a análise de delivery.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Êxito<br /> </td> 
   <td> @success<br /> </td> 
   <td> Número de mensagens processadas com êxito.<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Erros<br /> </td> 
   <td> @error<br /> </td> 
   <td> Número total de erros acumulados durante os deliveries e processamento automático de devolução.<br /> </td> 
   <td> sum([indicators/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> Novos em quarentena<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> Número de endereços em quarentena após uma falha de delivery (usuário desconhecido, domínio inválido).<br /> </td> 
   <td> sum([indicators/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Hot clicks {#hot-clicks-1}

Este relatório é baseado nas tabelas Delivery(nms:delivery) e **[!UICONTROL Consolidated tracking]** (nms:trackingStats).

Este relatório mostra o conteúdo da mensagem (HTML e/ou texto) com a porcentagem de cliques nos links, em cada link. Os links de unsubscription de blocos de personalização e links de mirror pages são considerados no total de cliques, mas não são exibidos no relatório.

## Estatísticas de rastreamento {#tracking-statistics-1}

Este relatório é baseado na tabela **[!UICONTROL Delivery]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Transações<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> Soma de todos os @totalClicks com um tipo de URL que é igual a "Transação".<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Cliques<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> Soma de todos os @totalClicks com um tipo de URL que é igual a "Clique de email".<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Abertura<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Soma de todos os @totalClicks com uma chave primária de URL que é igual a 1.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Estatísticas de entrega {#delivery-statistics-1}

Este relatório é baseado na tabela **[!UICONTROL Delivery and tracking statistics]**(nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Emails processados<br /> </td> 
   <td> @processed<br /> </td> 
   <td> Número total de mensagens com status "Pronta", "Enviada" ou "Falha".<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Entregue<br /> </td> 
   <td> @success<br /> </td> 
   <td> Número de mensagens processadas com êxito.<br /> </td> 
   <td> indicators/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> Devoluções permanentes<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> Número total de mensagens com um status que é igual a "Falha" e uma razão que é igual a "Usuário desconhecido".<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> Devoluções temporárias<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> Total de todas as mensagens com status que é igual a "Falha" e uma razão que é igual a "inacessível", "caixa de entrada cheia", "domínio inválido", "conta desabilitada", "não conectado" ou "rejeitada"<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> Aberturas<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Número total de @broadLog-ids nos logs de rastreamento.<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Cliques<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Número total de @source-ids para os quais a categoria de URL é igual a "Clique de email". <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> Cancelamentos de assinatura<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Número total de @ids para as quais a categoria de URL é igual a "Opt out".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Detalhamento de aberturas {#breakdown-of-opens-1}

Este relatório baseia-se nas tabelas de **Deliveries** (nms:delivery) e **Logs de rastreamento** (nms:trackingLogRcp)

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Nome do campo</strong> <br /> </th> 
   <th> <strong>Descrição do indicador</strong> <br /> </th> 
   <th> <strong>Fórmula do cálculo de indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Aberturas<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> Soma de todos os @id com uma chave primária de URL igual a 1 (abertura). <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Outros indicadores {#other-indicators}

O indicador **Enviado** (@sent), acessado pelo nó **Deliveries (nms:delivery) > Indicators** corresponde ao número total de SMS enviado ao provedor de serviços. Esse indicador é usado apenas para deliveries de SMS e não deve ser usado para outros tipos de deliveries (não deve ser confundido com os indicadores **@success** e **@processed**).

## Sincronização de indicadores {#indicator-synchronization}

Se você enfrentar dessincronização ou inconsistência de determinados indicadores, selecione o delivery correspondente no navegador do Adobe Campaign, clique com o botão direito do mouse e escolha **[!UICONTROL Action>Recompute delivery and tracking indicators]**. Clique em **[!UICONTROL Next]** e depois em **[!UICONTROL Finish]**.

![](assets/s_ncs_user_recalculate_indicators.png)

## Rastreamento de aberturas {#tracking-opens-}

Para que o Adobe Campaign detecte aberturas de mensagem, o recipient deve baixar as imagens no email. Os emails em HTML e Multipart/alternative incluem uma imagem de 0 pixel, que permite detectar mensagens que foram abertas. Como as mensagens em formato de texto não incluem imagens, é impossível detectar se foram abertas ou não. Os valores calculados com base na abertura de mensagem são sempre estimativas, devido à margem de erro vinculada à exibição de imagem.

## Pessoas/recipients direcionados {#targeted-persons---recipients}

Em alguns relatórios, o Adobe Campaign diferencia pessoas alvos e recipients alvos.

Os recipients alvos são todos os recipients aos quais o delivery foi enviado.

O número de pessoas inclui recipients alvos, além de todas as pessoas aos quais o email foi encaminhado. Cada vez que há um clique ou uma abertura em um novo navegador (que a mensagem ainda não foi aberta), outra pessoa é adicionada à estatística.

Por exemplo, se você receber um email (enviado pelo Adobe Campaign) no trabalho e abrir ou clicar nele, você será contado como recipient alvo (ou seja, recipient=1, pessoa=1). Se você encaminhar esse email para dois amigos, o número de recipients ainda será igual a um, enquanto o número de pessoas será igual a três. O valor 3 coincide com cada abertura/clique em um novo navegador.
