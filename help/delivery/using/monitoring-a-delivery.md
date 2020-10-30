---
title: Monitorar um delivery
seo-title: Monitorar um delivery
description: Monitorar um delivery
seo-description: null
page-status-flag: never-activated
uuid: 7cb409eb-a01c-4b4d-bb62-760e0bafdc8a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 3aab3d47-76fd-4c68-add4-9c14240c936e
translation-type: ht
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: ht
source-wordcount: '2562'
ht-degree: 100%

---


# Monitorar um delivery{#monitoring-a-delivery}

O **painel de delivery** é fundamental para monitorar seus deliveries e eventuais problemas encontrados durante o envio de mensagens.

**Tópicos relacionados:**

* [Noções básicas sobre falhas de delivery](../../delivery/using/understanding-delivery-failures.md)
* [Noções básicas sobre gestão de quarentena](../../delivery/using/understanding-quarantine-management.md)
* [Práticas recomendadas para delivery](../../delivery/using/delivery-best-practices.md)
* [Gerenciamento da capacidade de entrega](../../delivery/using/about-deliverability.md)

## Painel de delivery {#delivery-dashboard}

Para exibir as informações em um delivery, edite-as, exiba o painel e clique nas guias disponíveis.

O conteúdo da guia não pode mais ser alterado uma vez que o delivery foi enviado.

![](assets/s_ncs_user_del_details.png)

### Resumo do delivery {#delivery-summary}

A guia **[!UICONTROL Summary]** contém as características do delivery: status do delivery, canal usado, informações sobre o remetente, assunto, informações relacionadas à execução. Para obter mais informações, consulte [Número de mensagens enviadas](#number-of-messages-sent).

O link **[!UICONTROL reports]** permite que você veja um conjunto de relatórios referentes à ação do delivery: relatório geral do delivery, relatório detalhado, relatório do delivery, distribuição de mensagens com falha, taxa de abertura, cliques e transações etc. O conteúdo dessa guia pode ser configurado de acordo com os requisitos. Para obter mais informações, consulte [esta seção](../../reporting/using/delivery-reports.md).

### Histórico e logs do delivery {#delivery-logs-and-history}

A guia **[!UICONTROL Delivery]** fornece um histórico das ocorrências neste delivery. Ela contém os logs de delivery, ou seja, a lista de mensagens enviadas e seus status, e as mensagens associadas.

Para um delivery, você pode exibir (por exemplo) apenas os recipients com um delivery com falha ou um endereço em quarentena. Para fazer isso, clique no botão **[!UICONTROL Filters]** e selecione **[!UICONTROL By state]**. Em seguida, selecione o estado na lista suspensa.

![](assets/s_ncs_user_delivery_delivery_tab.png)

Vários status são listados [nesta página](#delivery-statuses).

>[!NOTE]
>
>O link **[!UICONTROL Display the mirror page for this message...]** permite exibir a mirror page do conteúdo do delivery selecionado na lista em uma nova janela. A mirror page só está disponível para os deliveries para as quais o conteúdo HTML foi definido. Para obter mais informações, consulte [Geração da mirror page](../../delivery/using/sending-messages.md#generating-the-mirror-page).

### Logs de rastreamento {#tracking-logs}

A guia **[!UICONTROL Tracking]** lista o histórico de rastreamento desse delivery. Esta guia exibe os dados de rastreamento das mensagens enviadas, ou seja, todas as URLs sujeitas ao rastreamento por meio do Adobe Campaign. Os dados de rastreamento são atualizados de hora em hora.

>[!NOTE]
>
>Se o rastreamento não estiver habilitado para um delivery, essa guia não será exibida.

A configuração de rastreamento é realizada no estágio apropriado do assistente do delivery. Consulte [Como configurar links rastreados](../../delivery/using/how-to-configure-tracked-links.md).

Os dados de **[!UICONTROL Tracking]** são interpretados nos relatórios de delivery. Consulte [esta seção](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

### Auditoria de delivery {#delivery-audit-}

A guia **[!UICONTROL Audit]** contém o log de delivery e todas as mensagens relacionadas às provas. O botão **[!UICONTROL Refresh]** permite atualizar os dados. Use o botão **[!UICONTROL Filters]** para definir um filtro nos dados.

Ícones especiais permitem identificar erros ou avisos. Consulte [Análise de delivery](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

A subguia **[!UICONTROL Proofs]** permite visualizar a lista de provas que foram enviadas.

![](assets/s_ncs_user_delivery_log_tab.png)

Você pode modificar as informações exibidas nessa janela (e das guias **[!UICONTROL Delivery]** e **[!UICONTROL Tracking]**) selecionando as colunas a serem exibidas. Para fazer isso, clique no ícone **[!UICONTROL Configure list]** localizado no canto inferior direito. Para obter mais informações sobre a configuração de exibição de listas, consulte [esta seção](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

### Sincronização do painel de delivery {#delivery-dashboard-synchronization}

No painel de delivery, convêm verificar as mensagens processadas e os logs de deliveries para garantir que seu delivery foi enviado com êxito.

Alguns indicadores ou status podem estar incorretos ou não atualizados, isso pode ser resolvido com as seguintes soluções:

* Se o status do delivery estiver incorreto, verifique se todas as aprovações necessárias foram feitas para esse delivery ou se os workflows **[!UICONTROL operationMgt]** e **[!UICONTROL deliveryMgt]** estão sendo executados sem erros. Isso também pode ser porque o delivery está usando uma afinidade não configurada na instância de envio.
* Se os indicadores de delivery ainda forem zero e se você estiver em uma configuração mid-sourcing, verifique o workflow técnico **[!UICONTROL Mid-sourcing (delivery counters)]**. Inicie-o se o status não for **[!UICONTROL Started]**. Você pode tentar recalcular os indicadores clicando com o botão direito do mouse no delivery relevante no gerenciador do Adobe Campaign e selecionando **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. Para obter mais informações sobre indicadores de rastreamento, consulte esta [seção](../../reporting/using/delivery-reports.md#tracking-indicators).
* Se o contador de delivery não corresponder ao seu delivery, tente recalcular os indicadores clicando com o botão direito do mouse no delivery relevante no explorador do Adobe Campaign e selecionando **[!UICONTROL Recompute delivery and tracking indicators]** > **[!UICONTROL Actions]** para sincronizar novamente. Para obter mais informações sobre indicadores de rastreamento, consulte esta [seção](../../reporting/using/delivery-reports.md#tracking-indicators).
* Se o seu contador de delivery não estiver atualizado para implantações de mid-sourcing, verifique se o workflow técnico **[!UICONTROL Mid-Sourcing (Delivery counters)]** está em execução. Para obter mais informações, consulte esta [página](../../installation/using/mid-sourcing-deployment.md).

Você também pode rastrear seus deliveries com relatórios diferentes através do painel de delivery. Para obter mais informações, consulte esta [seção](../../reporting/using/delivery-reports.md).

## Problemas de desempenho {#performance-issues}

### Lista de verificação {#checklist-}

Se os desempenhos de delivery forem ruins, você poderá verificar:

* **O tamanho do delivery**: deliveries grandes podem levar mais tempo para serem concluídos. Os MTA filho estão configurados para lidar com um tamanho de lote padrão, que funciona para a maioria das instâncias, mas precisam ser verificados quando os deliveries estiverem constantemente lentos.
* **O target do delivery**: os desempenhos de delivery são afetados por erros de devolução temporária, que são manipulados de acordo com a configuração de repetição. Quanto maior o número de erros, mais tentativas são necessárias.
* **O carregamento da plataforma geral**: quando vários deliveries grandes estão sendo enviados, a plataforma geral pode ser afetada. Você também pode verificar problemas de reputação de IP e capacidade de delivery. Para obter mais informações, consulte o [Guia de práticas recomendadas de capacidade de delivery](../../delivery/using/deliverability-key-points.md) do Adobe Campaign e [esta página](../../delivery/using/about-deliverability.md).

A manutenção da plataforma e do banco de dados também pode afetar os desempenhos de envio de delivery. Para obter mais informações, consulte [esta página](../../production/using/database-performances.md).

### Deliveries lentos {#slow-deliveries}

Depois de clicar no botão **[!UICONTROL Send]**, seu delivery parece demorar mais do que o normal. Isso pode ser causado por elementos diferentes:

* Alguns provedores de email podem ter adicionado seus endereços IP a uma lista de bloqueios. Neste caso, verifique seus broadlogs e consulte [esta seção](../../delivery/using/about-deliverability.md).
* Seu delivery pode ser muito grande para ser processado rapidamente, isso pode ocorrer com alta personalização do JavaScript ou se o seu delivery pesa mais do que 60 kbytes. Consulte as [Práticas recomendadas de delivery](../../delivery/using/delivery-best-practices.md) do Adobe Campaign para saber mais sobre as diretrizes de conteúdo.
* Pode ter ocorrido limitação dentro do MTA do Adobe Campaign. Isso é causado por:

   * Mensagens pendentes (**[!UICONTROL quotas met]** message): as cotas declaradas pelas regras MX declarativas definidas no Campaign foram atendidas. Para obter mais informações sobre esse tipo de mensagem, consulte [esta página](../../delivery/using/deliverability-faq.md). Para saber mais sobre as regras MX, consulte [esta página](../../delivery/using/technical-recommendations.md#mx-rules).
   * Mensagens pendentes (mensagem **[!UICONTROL dynamic flow control]**): o MTA do Campaign encontrou erros ao tentar entregar mensagens para um determinado ISP, o que faz com que um atraso evite uma densidade de erros muito grande e, portanto, enfrente uma possível inclusão na lista de bloqueios.

* Um problema do sistema pode impedir que os servidores interajam: isso pode desacelerar todo o processo de envio. Verifique os servidores para garantir que não haja problemas de memória ou recursos que possam afetar o Campaign no processo de obter os dados de personalização, por exemplo.

### Práticas recomendadas para desempenho {#best-practices-performance}

* Não mantenha os deliveries em estado de falha na instância, pois tabelas temporárias serão mantidas e o desempenho será afetado.

* Remova os deliveries que não são mais necessários.

* Recipients inativos nos últimos 12 meses a serem removidos do banco de dados para manter a qualidade do endereço.

* Não tente programar deliveries grandes juntos. Há um intervalo de 5 a 10 minutos para espalhar a carga uniformemente sobre o sistema. Coordene a programação de deliveries com os outros membros da equipe para garantir o melhor desempenho. Quando o servidor de marketing estiver lidando com várias tarefas diferentes ao mesmo tempo, ele poderá retardar o desempenho.

* Mantenha o tamanho do seus emails o menor possível. O tamanho máximo recomendado de um email é de aproximadamente 35 KB. O tamanho de um delivery de email gera uma certa quantidade de volume nos servidores de envio.

* Deliveries grandes, como para mais de um milhão de recipients, precisam de espaço nas filas de envio. Isso por si só não é um problema para o servidor, mas quando combinado com dezenas de outros grandes deliveries, sendo todos enviados ao mesmo tempo, pode gerar um atraso no envio.

* A personalização em emails extrai dados do banco de dados para cada recipient. Se houver muitos elementos de personalização, isso aumentará a quantidade de dados necessários para preparar o delivery.

* Endereços de índice. Para otimizar o desempenho das consultas SQL usadas no aplicativo, um índice pode ser declarado a partir do elemento principal do esquema de dados.

>[!NOTE]
>
>Os ISPs desativariam endereços após um período de inatividade. As mensagens com rejeição são enviadas aos remetentes para informá-los sobre esse novo status.

## Status de delivery {#delivery-statuses}

Ao enviar um delivery, você pode encontrar o seguinte status no seu painel de delivery:

<table> 
 <thead> 
  <tr> 
   <th> Status<br /> </th> 
   <th> Definições e soluções<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Not applicable<br /> </td> 
   <td> O delivery foi levado em conta pelo servidor (MTA), mas não foi processado.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignored<br /> </td> 
   <td> O delivery não foi enviado ao recipient devido a um erro no endereço. Ele foi incluído na lista de bloqueios, colocado em quarentena, não fornecido ou duplicado. <br /> </td> 
  </tr> 
  <tr> 
   <td> Sent<br /> </td> 
   <td> O delivery foi enviado corretamente ao provedor de mensagens (mas o recipient não o recebeu necessariamente).<br /> </td> 
  </tr> 
  <tr> 
   <td> Failed<br /> </td> 
   <td> O delivery não conseguiu alcançar o recipient devido a um endereço inválido ou a uma caixa de entrada cheia, por exemplo. Ele também pode ser vinculado a um problema com blocos de personalização, pois esses blocos podem gerar erros quando os schemas não correspondem ao mapeamento do delivery. Consulte <a href="#failed-status" target="_blank">Status com falha</a><br /> </td> 
  </tr> 
  <tr> 
   <td> Taken into account by the service provider<br /> </td> 
   <td> O provedor de serviços SMS recebeu o delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> Received on mobile<br /> </td> 
   <td> O recipient recebeu o SMS em seu dispositivo móvel.<br /> </td> 
  </tr> 
  <tr> 
   <td> Pending<br /> </td> 
   <td> O delivery está pronto para ser enviado e será processado pelo servidor de delivery (MTA). Consulte <a href="#pending-status" target="_blank">Status pendente</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Delivery canceled<br /> </td> 
   <td> O delivery foi cancelado por um operador.<br /> </td> 
  </tr> 
  <tr> 
   <td> Prepared<br /> </td> 
   <td> Status intermediário usado somente para conectores externos como o canal móvel. Ele segue o status "Pendente" e é o conector externo que determinará o status seguinte.<br /> </td> 
  </tr> 
  <tr> 
   <td> Sent to the service provider<br /> </td> 
   <td> O delivery foi enviado para o provedor de serviços SMS, mas ainda não foi recebido.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Para saber como otimizar a capacidade de entrega dos emails do Adobe Campaign, consulte o [Guia de práticas recomendadas de capacidade de entrega](../../delivery/using/deliverability-key-points.md) do Adobe Campaign e [esta página](../../delivery/using/about-deliverability.md).

### Status pendente {#pending-status}

Após confirmar o delivery, você pode ver que o status do delivery é **[!UICONTROL Pending]**. Esse status significa que o processo de execução está aguardando a disponibilidade de alguns recursos.

O status **[!UICONTROL Pending]** pode significar que o seu delivery foi agendado e está pendente até a data especificada. Para obter mais informações, consulte a seção [Agendamento de delivery](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

Se o delivery não estiver sendo enviado e o status permanecer **[!UICONTROL Pending]**, poderá ser devido a:

* O MTA (Message Transfert Agent), que executa módulos e processos no servidor de delivery e que gerencia o envio de email, pode não ter sido iniciado ou precisa ser reiniciado. Para verificar isso e iniciar o módulo se necessário, siga as seguintes etapas:

   * Verifique se os `mta@<instance>` módulos são iniciados nos servidores MTA.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
   [...]
   mta@<INSTANCENAME> (9268) - 23.0 Mb
   [...]
   ```

   * Se o MTA não estiver listado, comece com o seguinte comando:

   ```
   nlserver start mta@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Substitua `<INSTANCENAME>` pelo nome da sua instância (produção, desenvolvimento, etc.). O nome da instância é identificado por meio dos arquivos de configuração: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* Pode ser que o delivery esteja usando uma afinidade não configurada no locatário emissor. Nesse caso, verifique a configuração do gerenciamento de tráfego (afinidade IP) e use o campo **[!UICONTROL Managing affinities with IP addresses]** para vincular deliveries ao MTA que gerencia a afinidade. Para obter mais informações sobre afinidades, consulte [esta seção](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).
* Quando a preparação do delivery está pendente, pode haver muitas campanhas sendo executadas, bloqueando a atualização de status do delivery. Para resolver isso, vá para **[!UICONTROL Options]** e aumente o valor de **[!UICONTROL NmsOperation_LimitConcurrency]** (o padrão é 10). Não execute mais campanhas do que o valor atribuído a essa opção específica.

### Falha no status {#failed-status}

Se o status de um delivery de email for **[!UICONTROL Failed]**, ele poderá ser vinculado a um problema com blocos de personalização. Os blocos de personalização em um delivery podem gerar erros quando os schemas não correspondem ao mapeamento do delivery, por exemplo.

Os logs do delivery são fundamentais para saber por que um delivery falhou. Aqui estão possíveis erros que você pode detectar nos logs de delivery:

* Se as mensagens do recipient estiverem falhando com um erro &quot;Unreachable&quot; informando: **Error while compiling script &#39;content htmlContent&#39; line X: `[table]` is not defined. JavaScript: erro ao avaliar o script &quot;content htmlContent&quot;**, a causa desse problema é quase sempre uma personalização dentro da tentativa do HTML chamar em uma tabela ou campo que não foi definido ou mapeado na construção do target de upstream ou no target mapping do delivery.

   Para corrigir isso, o workflow e o conteúdo do delivery precisam ser revisados para determinar especificamente qual personalização está tentando chamar a tabela em questão e se a tabela pode ou não ser mapeada. A partir daí, ao remover a chamada para esta tabela no HTML ou ao corrigir o mapping para o delivery pode ser o caminho para a resolução.

* No modelo de implantação de mid-sourcing, a seguinte mensagem pode aparecer nos logs do delivery: **Error during the call of method &#39;AppendDeliveryPart&#39; on the mid sourcing server: &#39;Communication error with the server: please check this one is correctly configured. HTTP código 408 &#39;Serviço temporariamente indisponível&#39;**.

   A causa está vinculada aos problemas de desempenho. Significa que a instância de marketing gasta muito tempo criando dados antes de enviá-los ao servidor mid-sourcing.

   Para resolver isso, recomendamos executar um vácuo e reindexação no banco de dados. Para obter mais informações sobre manutenção de banco de dados, consulte [esta seção](../../production/using/recommendations.md).

   Você também deve reiniciar todos os workflows com uma atividade agendada e todos os workflows com o status de falha. Consulte [esta seção](../../workflow/using/scheduler.md).

* Quando um delivery falha, o seguinte erro pode aparecer nos logs do delivery: **DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Entre em contato com o suporte.**

   Normalmente, esse erro significa que há um campo ou bloco de personalização no email com mais de um valor para o recipient. Um bloco de personalização está sendo usado e está buscando mais de um registro para um determinado recipient.

   Para resolver isso, verifique os dados de personalização usados e verifique o target para os recipients que têm mais de uma entrada para qualquer um desses campos. Você também pode usar uma atividade **[!UICONTROL Deduplication]** no workflow para construção do target antes da atividade de delivery para verificar se há apenas um campo de personalização por vez. Para obter mais informações sobre desduplicação, consulte [esta página](../../workflow/using/deduplication.md).

* Alguns deliveries podem falhar com um erro &quot;Unreachable&quot; informando: &quot;Inbound email bounce (rule &#39;Auto_replies&#39; has matched this bounce). Isso significa que o delivery teve êxito, mas o Adobe Campaign recebeu uma resposta automática do recipient (por exemplo, uma &quot;ausência temporária&quot;) que corresponde às regras de email de entrada &quot;Respostas_automáticas&quot;. O email de resposta automática é ignorado pelo Adobe Campaign e o endereço do recipient não será enviado para a quarentena.

**Tópicos relacionados:**

* [Histórico e logs do delivery](#delivery-logs-and-history)
* [Noções básicas sobre falhas de delivery](../../delivery/using/understanding-delivery-failures.md)
* [Tipos e motivos de falha de delivery](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)

## Número de mensagens enviadas {#number-of-messages-sent}

Você pode acessar deliveries a partir da lista de delivery, por meio do nó **[!UICONTROL Campaign Management > Deliveries]** da árvore.

Por padrão, a lista de deliveries contém os nomes e os status dos deliveries criados no nó selecionado. Ele também mostra o número de mensagens a serem enviadas, processadas e enviadas com sucesso.

* O número de **[!UICONTROL Messages to send]** corresponde ao número de recipients target após a análise e antes do delivery.
* O número de mensagens na coluna **[!UICONTROL Success]** corresponde ao número de mensagens enviadas pelo servidor e recebidas pelos recipients.
* O número de mensagens **[!UICONTROL Processed]** corresponde ao número de mensagens recebidas mais o número de mensagens com erros.

O painel de delivery permite que você rastreie o número de mensagens enviadas.

>[!NOTE]
>
>Para deliveries grandes, convém atualizar esses valores. Para fazer isso, selecione o delivery em questão e clique com o botão direito nele. Selecione **[!UICONTROL Action > Recompute delivery and tracking indicators...]** e depois use o assistente para atualizar essas informações.

## Deliveries agendados {#scheduled-deliveries-}

Se os deliveries não forem executados em uma data agendada específica, ela poderá estar relacionada a uma diferença entre o fuso horário dos servidores. A instância mid-sourcing e a instância de produção podem estar em fusos horários diferentes.

Como exemplo, se a ocorrência de mid-sourcing estiver no fuso horário de Brisbane e a instância de produção estiver no fuso horário de Darwin, os fusos horários têm meia hora de diferença um do outro e, no log de auditoria, é possível ver claramente que se o delivery estiver agendado para a produção às 11h56, o mesmo delivery agendado para mid deveria ser às 12h26, com uma diferença de meia hora.
