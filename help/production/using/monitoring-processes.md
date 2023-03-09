---
product: campaign
title: Processos de monitoramento
description: Saiba como monitorar processos do Campaign
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1f5d8c7e-6f9b-46cd-a9b4-a3b48afb1794
source-git-commit: f2ec24a122eff94f62bd79e656e771fecd803659
workflow-type: tm+mt
source-wordcount: '3610'
ht-degree: 1%

---

# Processos de monitoramento{#monitoring-processes}

![](../../assets/v7-only.svg)

O servidor de aplicativos e o servidor de redirecionamento (**rastreamento**) podem ser monitorados manual ou automaticamente.

## Monitoramento manual {#manual-monitoring}

Ir para **[!UICONTROL Monitoring]** e clique no link **[!UICONTROL Overview]** link para exibir a página monitoramento do processo do Adobe Campaign.

![](assets/d_ncs_monitoring.png)

A página exibida permite visualizar o estado da instância conectada, ou seja:

* informações sobre a instância: versão, nome, mecanismo de banco de dados, pacotes instalados, indicadores do sistema do servidor,
* a lista de processos e informações de execução ausentes (data de início, PID etc.),
* uma exibição de workflows e deliveries.

Outras maneiras de monitorar os diferentes processos do Campaign são apresentadas [nesta página](../../production/using/monitoring-guidelines.md).

### Diário de log {#log-journal}

É possível exibir o diário de log relacionado a um processo. Para fazer isso, clique no processo, **mta** por exemplo, e clique em **[!UICONTROL Open the log journal]** .

![](assets/d_ncs_monitoring2.png)

### Indicadores do sistema {#system-indicators}

A lista de indicadores do sistema permite exibir informações relacionadas à máquina, como memória física e virtual, processos ativos e espaço em disco disponível. Os indicadores são diferentes para os sistemas operacionais Linux e Windows. Vá para a **[!UICONTROL Instance Monitoring]** e clique no link **[!UICONTROL Display]** link para abrir a lista de indicadores

#### Windows {#in-windows}

* **[!UICONTROL Pending events queued]** : indicador específico do **Centro de mensagens**. Consulte [esta seção](../../message-center/using/additional-configurations.md#monitoring-thresholds) para obter mais informações.

* **[!UICONTROL Memory]** : informações sobre a memória física (RAM).

   **[!UICONTROL Current value]** : consumo real de memória.

   **[!UICONTROL Max Value]** : quantidade total de memória instalada.

   **[!UICONTROL Available]** : quantidade de memória disponível.

   **[!UICONTROL Warning]** : esse indicador é exibido quando o consumo de memória atinge 80% da quantidade total.

   **[!UICONTROL Alert]** : esse indicador é exibido quando o consumo de memória atinge 90% da quantidade total.

   Quando a variável **[!UICONTROL Warning]** e **[!UICONTROL Alert]** forem exibidos indicadores, você poderá resolver o problema adicionando RAM à máquina em que o servidor do Adobe Campaign está instalado. Você também pode decidir instalar o servidor do Adobe Campaign em uma máquina dedicada.

* **[!UICONTROL Swap Memory]** : informações relacionadas à memória virtual que corresponde a um arquivo de paginação: uma área no disco rígido que o Windows usa como se fosse a RAM.

   **[!UICONTROL Current value]** : consumo real de memória.

   **[!UICONTROL Max Value]** : quantidade total de memória.

   **[!UICONTROL Available]** : quantidade de memória disponível.

   **[!UICONTROL Warning]** : esse indicador é exibido quando o consumo de memória atinge 80% da quantidade total.

   **[!UICONTROL Alert]** : esse indicador é exibido quando o consumo de memória atinge 90% da quantidade total.

   Quando a variável **[!UICONTROL Warning]** e **[!UICONTROL Alert]** forem exibidos indicadores, você poderá resolver o problema aumentando o tamanho do arquivo do Exchange nas configurações avançadas do Windows.

* **[!UICONTROL Disk XXX]** : informações sobre leitores de máquina.

   **[!UICONTROL Current value]** : espaço em disco realmente usado.

   **[!UICONTROL Max Value]** : capacidade total do disco.

   **[!UICONTROL Available]** : espaço em disco disponível

   **[!UICONTROL Used]** : porcentagem de disco usada.

   **[!UICONTROL Warning]** : esse indicador é exibido quando o espaço disponível em disco atinge 80% da capacidade total.

   **[!UICONTROL Alert]** : esse indicador é exibido quando o espaço disponível em disco atinge 90% da capacidade total.

* **[!UICONTROL Number of processes too old]** : informações sobre processos do Adobe Campaign que estão ativos por mais de um dia.

   **[!UICONTROL Current value]** : número de processos atualmente ativos.

   **[!UICONTROL Max Value]** : número máximo de processos autorizados (1).

   **[!UICONTROL Alert]** : esse indicador será exibido se o número de processos for igual a 1.

   Quando a variável **[!UICONTROL Alert]** for exibido, pode ser que o processo relacionado esteja bloqueado pelo mecanismo de banco de dados SQL ou que esteja preso em um loop infinito. A variável **watchdog** O processo fornecido pelo Adobe Campaign reinicia automaticamente todos os processos todos os dias e permite que você resolva esse problema. No entanto, você também pode interromper o processo relacionado sozinho para forçar a reinicialização.

#### Linux {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Pending events queued]** : indicador específico do **Centro de mensagens**. Consulte [esta seção](../../message-center/using/additional-configurations.md#monitoring-thresholds) para obter mais informações.

* **[!UICONTROL Load average (1/5/15 minutes)]** : informações sobre a carga, ou seja, a taxa de uso do processador pelos processos em execução na máquina durante o último minuto, cinco minutos ou quinze minutos

   **[!UICONTROL Current value]** : carga real da máquina.

   **[!UICONTROL Max value]** : carga máxima de uso dos processos na máquina

   **[!UICONTROL Warning]** : esse indicador é exibido quando a carga atinge 80% do valor máximo autorizado no último minuto, cinco minutos ou quinze minutos.

   **[!UICONTROL Alert]** : esse indicador é exibido quando a carga atinge 90% do valor máximo autorizado do último minuto, cinco minutos ou quinze minutos.

* **[!UICONTROL Memory]** : informações sobre a memória física (RAM).

   **[!UICONTROL Current value]** : consumo real de memória.

   **[!UICONTROL Max Value]** : quantidade total de memória instalada.

   **[!UICONTROL Available]** : quantidade de memória disponível.

   **[!UICONTROL Warning]** : esse indicador é exibido quando o consumo de memória atinge 80% da quantidade total.

   **[!UICONTROL Alert]** : esse indicador é exibido quando o consumo de memória atinge 90% da quantidade total.

   Quando a variável **[!UICONTROL Warning]** e **[!UICONTROL Alert]** forem exibidos indicadores, você poderá resolver o problema adicionando RAM à máquina em que o servidor do Adobe Campaign está instalado. Você também pode decidir instalar o servidor do Adobe Campaign em uma máquina dedicada.

* **[!UICONTROL Swap Memory]** : informações relacionadas à memória virtual que corresponde a um arquivo de paginação: uma área no disco rígido que o Windows usa como se fosse a RAM.

   **[!UICONTROL Current value]** : consumo real de memória.

   **[!UICONTROL Max Value]** : quantidade total de memória.

   **[!UICONTROL Available]** : quantidade de memória disponível.

   **[!UICONTROL Warning]** : esse indicador é exibido quando o consumo de memória atinge 80% da quantidade total.

   **[!UICONTROL Alert]** : esse indicador é exibido quando o consumo de memória atinge 90% da quantidade total.

   Quando a variável **[!UICONTROL Warning]** e **[!UICONTROL Alert]** forem exibidos indicadores, você poderá resolver o problema aumentando o tamanho do arquivo do exchange.

* **[!UICONTROL Core Files]** : informações sobre os arquivos gerados após a falha de um processo do Adobe Campaign. Esses arquivos permitem diagnosticar os motivos da falha.

   **[!UICONTROL Current Value]** : número de arquivos existentes.

   **[!UICONTROL Max Value]** : número máximo de ficheiros autorizados (1).

   **[!UICONTROL Warning]** : esse indicador é exibido quando o número de arquivos se aproxima de 1.

   **[!UICONTROL Alert]** : esse indicador é exibido quando o número de arquivos é igual a 1.

   Quando um processo não aparece devido a uma falha, ele é mostrado em vermelho na lista de processos e é reiniciado automaticamente pelo **watchdog** processo fornecido pela Adobe Campaign.

* **[!UICONTROL Number of shared memory segments]** : informações relacionadas aos segmentos de memória compartilhados por todos os processos do Adobe Campaign.

   **[!UICONTROL Current value]** : número de segmentos de memória em uso no momento.

   **[!UICONTROL Max Value]** : número máximo de segmentos de memória autorizados (2).

   **[!UICONTROL Warning]** : este indicador é exibido quando o número de segmentos de memória atinge 1.

   **[!UICONTROL Alert]** : este indicador é exibido quando o número de segmentos de memória atinge 2.

* **[!UICONTROL Number of processes too old]** : informações sobre processos que estiveram ativos por mais de um dia.

   **[!UICONTROL Current value]** : número de processos atualmente ativos.

   **[!UICONTROL Max Value]** : número máximo de processos autorizados.

   **[!UICONTROL Warning]** : esse indicador é exibido quando o número de processos atinge 80% do limite autorizado.

   **[!UICONTROL Alert]** : esse indicador é exibido quando o número de processos atinge 90% do limite autorizado.

* **[!UICONTROL File Handles]** : informações sobre os descritores de arquivo, ou seja, o número de arquivos abertos por processo.

   **[!UICONTROL Current value]** : número atual de descritores de arquivo.

   **[!UICONTROL Max Value]** : número máximo de descritores de arquivo autorizados pelo sistema operacional.

   **[!UICONTROL Warning]** : esse indicador é exibido quando o número de descritores de arquivo autorizados atinge o limite de 80%.

   **[!UICONTROL Alert]** : esse indicador é exibido quando o número de descritores de arquivo autorizados atinge o limite de 90%.

* **[!UICONTROL Processes]** : informações relativas aos processos da máquina.

   **[!UICONTROL Current value]** : número de processos atualmente ativos.

   **[!UICONTROL Max Value]** : número máximo de processos autorizados.

   **[!UICONTROL Active Processes]** : número de processos ativos.

   **[!UICONTROL Inactive Processes]** : número de processos inativos.

   **[!UICONTROL Warning]** : esse indicador é exibido quando o número de processos autorizados atinge o limite de 80%.

   **[!UICONTROL Alert]** : esse indicador é exibido quando o número de processos autorizados atinge o limite de 90%.

* **[!UICONTROL Zombie Processes]** : informações sobre os processos que foram interrompidos, mas ainda têm um identificador de processo (PID) e permanecem visíveis na tabela de processos.

   **[!UICONTROL Current value]** : número de processos zumbis ativos no momento.

   **[!UICONTROL Max Value]** : número máximo de processos de autorização zumbis (2).

   **[!UICONTROL Warning]** : esse indicador é exibido quando o número de processos zumbis se aproxima de 2.

   **[!UICONTROL Alert]** este indicador é exibido quando o número de processos zumbis atinge 2.

#### Indicadores personalizados {#customized-indicators}

O Adobe Campaign permite personalizar indicadores. Para fazer isso:

1. Criar um **.sh** arquivo e nomeie-o **[!UICONTROL cust_indicators.sh]** .
1. Adicione seus indicadores personalizados a esse arquivo. Por exemplo:

   ```
   #!/bin/bash 
   echo "<indicator name='Zombie Processes'>  
   <current label='Current Value' value='0' display=''/>  
   <warning value='2'/>  <alert value='2'/>  
   <max label='Max Value' value='2'/>
   </indicator>"
   ```

   ou

   ```
   #!/bin/bash 
   echo "<indicator name='Availability'>  
   <current label='Last update of data' display='2012-09-03 10:00'/>  
   <current label='Availability last month' display='100.00%'/>  
   <current label='Availability this month' display='100.00%'/> 
   <current label='Recent downtime periods' display='2012-07-04 11:10:00 - 11:19:59'/>
   </indicator>"
   ```

1. Coloque o arquivo no **[!UICONTROL usr/local/neolane/nl6]** pasta.

Este arquivo será chamado pelo Adobe Campaign.

## Relatórios SMTP {#smtp-reports}

Os relatórios de monitoramento de delivery SMTP são integrados à plataforma do Adobe Campaign. Eles podem ser acessados por meio do console ou usando o acesso à Web.

Esses relatórios exibem estatísticas de delivery SMTP e erros SMTP por domínio.

Para acessá-las, o operador deve ter direitos de Administration.

Eles estão agrupados em **Monitoramento** > &#39;Monitoramento SMTP&#39;.

![](assets/smtp_reports_access.png)

>[!IMPORTANT]
>
>* As informações relacionadas ao monitoramento SMTP só estarão disponíveis se o canal de email tiver sido ativado.
>* A variável **[!UICONTROL SMTP sending statistics]** são oferecidos somente se o servidor de estatísticas for iniciado na instância.
>


### Estatísticas de envio SMTP {#smtp-sending-statistics}

A variável **[!UICONTROL SMTP sending statistics]** permite controlar a atividade do servidor. Ele exibe uma síntese de cada um dos mtachilds.

![](assets/smtp_stats_report.png)

A lista de indicadores desse relatório é mostrada abaixo do gráfico.

1. Número total de mensagens enviadas.
1. Representa mensagens de entrada/saída:

   * Linha azul: mensagens prontas para envio que chegaram no Shaper, ou seja, a última etapa antes de enviar SMTP (coincide com os dados de entrada).

   * Linha verde: mensagens enviadas com êxito (coincide com os dados de saída).

   * Linha vermelha: mensagens abandonadas pelo Shaper, retornadas à **mta** (coincide com os dados rejeitados nesta recuperação).

   Esses valores são expressos em número de mensagens por hora.

1. Representa duas filas do Shaper:

   * Curva azul: fila de mensagens ativas. Essas mensagens serão enviadas assim que possível.

   * Curva de Kaki: a fila &#39;deferida&#39;. Essas mensagens não podem ser retornadas no momento devido à limitação ou porque nenhuma conexão com o destino está disponível. As tentativas ocorrerão a cada 5, 10, 20, 40, 2 min, etc. para o definido **MaxAgeSec** antes de ser abandonada.

1. Este gráfico mostra um detalhe de mensagens abandonadas (curva vermelha no segundo gráfico): ele mostra a proporção de mensagens abandonadas sem tentativas (mauve) em comparação com mensagens cujo envio falhou (vermelho). Isso permite exibir a proporção de mensagens não processadas no período concedido devido a limitações do servidor de estatísticas (limitação) ou devido à indisponibilidade do servidor remoto.
1. As conexões SMTP estão abertas ou sendo abertas.
1. Estimativa do número de **mtachild**.

>[!NOTE]
>
>Este relatório está relacionado ao status do componente de Modelador de tráfego de email.

### Erros de SMTP por domínio {#smtp-errors-per-domain}

Esse relatório permite visualizar os erros de delivery, durante um período definido, divididos por domínio.

>[!NOTE]
>
>A variável **minConnectionsToLog**, **minErrorsToLog** e **minMessagesToLog** opções do **serverConf.xml** arquivo define os limites acima dos quais as estatísticas de conexão são consideradas.

![](assets/smtp_error_report.png)

A lista de indicadores para esse relatório é mostrada abaixo da tabela.

* A variável **Domínio** contém o nome do domínio para o qual as mensagens são enviadas (ou o nome do domínio real, yahoo.com para yahoo.fr por exemplo),
* A variável **Cnx** exibe o número de conexões SMTP abertas para este domínio,
* A variável **Enviado** corresponde ao número de mensagens enviadas para esse domínio,
* A variável **Volume** exibe o volume de mensagens que tentaram ser enviadas para esse domínio (valor aproximado),
* A variável **Erros** exibe um indicador de volume de erros neste domínio durante o período,
* A variável **Última resposta** exibe a última mensagem de resposta SMTP recebida para este domínio,
* A variável **Data** exibe a data da última resposta SMTP recebida para este domínio.

>[!NOTE]
>
>Os valores exibidos na variável **Cnx**, **Enviado**, e **Volume** são calculadas em relação ao período selecionado na variável **[!UICONTROL Period]** campo.

Clique em um nome de domínio para exibir os erros.

Eles são categorizados por PublicId: esse identificador corresponde a um endereço IP compartilhado por vários mtas do Adobe Campaign atrás de um roteador. O servidor de estatísticas usa esse identificador para memorizar a conexão e as estatísticas de entrega entre esse ponto de partida e o servidor de destino.

![](assets/smtp_error_report_details.png)

A variável **[!UICONTROL Owner of domain]** permite agrupar vários nomes de domínio no mesmo rótulo. Na exibição inicial do relatório, todos os nomes de domínio MX serão associados a esse proprietário.

Clique em um identificador PublicId para exibir mais detalhes.

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>A porcentagem de erros é representada por dois gráficos. A primeira é uma barra de progresso horizontal em um plano de fundo preto. O segundo gráfico é cronológico. O período selecionado é dividido em doze intervalos de tempo, cada um representado por uma barra de progresso vertical. Em ambas as representações, se nenhum erro for detectado, a barra ficará preta. A cor da barra depende da porcentagem de erros encontrados (amarelo, laranja e, por último, vermelho). A cor cinza significa que nenhum volume de dados significativo foi encontrado. É possível exibir a porcentagem exata de erros, colocando o cursor no gráfico.

>[!NOTE]
>
>Para obter mais informações sobre erros SMTP e gerenciá-los no Adobe Campaign, consulte [nesta seção](../../installation/using/email-deliverability.md).

## Relatório de faturamento {#billing-report}

A variável **[!UICONTROL Billing]** o workflow técnico envia o relatório de atividades do sistema para o operador &#39;faturamento&#39; por email. É acionado por padrão todo dia 25 de cada mês na instância de marketing.

O workflow técnico pode ser encontrado em uma subpasta do seguinte nó: **Administração** > **Produção** > **Fluxos de trabalho técnicos**.

![](assets/billing.png)

Assim que o fluxo de trabalho for iniciado, a cada 25 dias do mês, sua operadora de cobrança receberá o relatório a seguir em sua caixa de entrada.

![](assets/billing_2.png)

As seguintes métricas estão disponíveis para rastrear seus deliveries:

* **[!UICONTROL Start date]** : data de início da entrega. Observe que pode ser anterior à data &quot;de&quot; do relatório.
* **[!UICONTROL Label]** : Rótulo da entrega. Deliveries que têm menos de 100 mensagens para enviar são considerados muito pequenos e, portanto, agregados por data de início, nesse caso, o rótulo exibe o número de agregados, por exemplo, [Agregação de 3 deliveries pequenos].
* **[!UICONTROL Total volume]** : Volume total de bytes transferidos para o delivery.
* **[!UICONTROL Avg volume]** : Volume médio de bytes transferidos. Este é o resultado da seguinte fórmula **(volume total/mensagens)**, que é a base de cálculo do **[!UICONTROL Multiplier]** métrica.
* **[!UICONTROL Messages]** : Número de mensagens enviadas. Isso inclui mensagens enviadas com êxito e tentativas (após o recebimento de uma mensagem de devolução do servidor contatado).
* **[!UICONTROL Multiplier (x)]** : O valor do multiplicador é deduzido do volume médio das mensagens.
* **[!UICONTROL Count]** : Resultado da multiplicação das mensagens e do multiplicador.

## Monitoramento automático {#automatic-monitoring}

O Adobe Campaign oferece vários métodos de monitoramento automático, que são apresentados abaixo.

### Linha de comando {#command-line}

Comando

**monitor nlserver**

Permite listar um conjunto de indicadores nos módulos Adobe Campaign e no sistema.

Ele gera saída em um formato XML facilmente processado.

Esse comando também pode ser executado com a variável **-ausente** parâmetro, que lista os processos que estão faltando nessa instância quando os arquivos de configuração dizem que devem ser executados.

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### Informações publicadas pelo servidor {#information-published-by-the-server}

#### /r/test {#r-test}

A variável **http(s)://`<application>`/r/test** página é usada para testar o servidor de redirecionamento. Recomendamos usar esse mesmo método para testar os servidores frontais usados para rastreamento. Esta página também pode ser usada para testar um dispatcher de carga.

Ele exibe uma linha como esta no formato XML:

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**Frequência**: esse teste não usa carga e, portanto, pode ser executado com muita frequência (por exemplo, uma vez a cada segundo).

#### /nl/jsp/ping.jsp {#nl-jsp-ping-jsp}

Este **http(s)://`<Application server url>`/nl/jsp/ping.jsp**  A página opera da mesma forma que sua contraparte de rede: ela testa uma consulta completa passando pelo apache/tomcat/web module/database e fazendo upload para o cliente. Se tudo estiver funcionando corretamente, retornará um &quot;OK&quot;. Recomendamos executar esse teste em computadores com acesso aos bancos de dados (mtas e pesquisas, por exemplo).

**Uso**: um token de sessão associado a um logon de operador deve ser passado como argumento para fazer logon remotamente (consulte a dica em [Monitoramento automático via scripts do Adobe Campaign](#automatic-monitoring-via-adobe-campaign-scripts)).

Por exemplo:

![](assets/ncs_monitoring_ping.png)

O nome e o logon do operador precisam ser configurados anteriormente no console do cliente do Adobe Campaign com direitos de banco de dados.

![](assets/ncs_operators_rights_01.png)

**Frequência**: este é um teste que usa muito pouca largura de banda. Portanto, pode ser executado com bastante frequência, embora não mais do que uma vez por minuto.

#### /nl/jsp/monitor.jsp {#nl-jsp-monitor-jsp}

Este é um teste para verificar se um operador pode acessar o servidor do Adobe Campaign por meio de uma página da Web; a mesma página da Web acessada pelos menus do console do cliente. Você pode chamar esta página de suas ferramentas de vigilância (Tivoli, Nagios, etc.).

![](assets/ncs_monitoring_web.png)

**Uso**: um token de sessão associado a um logon de operador que permite a conexão com a instância precisa ser usado como argumento (consulte a dica em [Monitoramento automático via scripts do Adobe Campaign](#automatic-monitoring-via-adobe-campaign-scripts)).

O operador e seu logon precisam ser configurados anteriormente no console do cliente do Adobe Campaign com os direitos e restrições apropriados do banco de dados.

**Frequência**: este é um teste de servidor completo e não precisa ser executado com frequência (pode ser executado uma vez a cada dez minutos, por exemplo).

#### /nl/jsp/soaprouter.jsp {#nl-jsp-soaprouter-jsp}

Este **jsp** representa o ponto de entrada das APIs de aplicativo do Adobe Campaign. Por conseguinte, pode proporcionar uma monitorização pormenorizada da aplicação. Ele também pode ser usado para monitorar os serviços Web do Adobe Campaign. Ela é usada em nossos scripts de monitoramento, mas observe que é somente para usuários avançados.

### Monitoramento com base nos tipos de implantação {#monitoring-based-on-deployment-types}

O Adobe Campaign habilita várias configurações de implantação (para obter mais informações, consulte [nesta seção](../../installation/using/hosting-models.md)). Esta seção detalha as várias técnicas de monitoramento automático a serem aplicadas dependendo do tipo de instalação.

<table> 
 <thead> 
  <tr> 
   <th> Tipo de implantação </th> 
   <th> Monitoramento </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Autônomo </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> e <span class="uicontrol">/nl/jsp/monitor.jsp</span> no servidor do Adobe Campaign</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Padrão </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> e <span class="uicontrol">/nl/jsp/ping.jsp</span> nos servidores frontais</p> </li> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> no servidor de aplicativos</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Enterprise </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> e <span class="uicontrol">/nl/jsp/ping.jsp</span> nos servidores frontais</p> </li> 
     <li><p> <span class="uicontrol">/r/test</span> e <span class="uicontrol">/nl/jsp/monitor.jsp</span> no servidor de aplicativos</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Mid-sourcing </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> no servidor de aplicativos</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Monitoramento automático via scripts do Adobe Campaign {#automatic-monitoring-via-adobe-campaign-scripts}

O Adobe Campaign pode fornecer uma ferramenta de monitoramento de instância (netreport) que permite enviar um relatório por email sobre as anomalias detectadas.

![](assets/pro_netreport.png)

>[!IMPORTANT]
>
>Essa ferramenta pode ser usada para monitorar suas instâncias, mas não é compatível com o Adobe Campaign. Entre em contato com o administrador do Campaign para obter mais informações.

### Elementos obrigatórios {#required-elements}

As seguintes precauções de pré-instalação são necessárias para a monitoração automática:

* Você deve ter o **netreport.tgz** (Instalação do Linux) ou **netreport.zip** arquivos (instalação do Windows),
* Recomendamos que você não instale o monitoramento na máquina a ser monitorada,
* deve ser instalado em uma máquina com um JRE ou JDK,
* no Linux, a máquina a ser monitorada deve ter o **bc** pacote. Para obter mais informações, consulte [esta seção](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages).

### Procedimento de instalação {#installation-procedure}

O procedimento de instalação é o seguinte:

1. No console, crie um novo operador, se necessário (o usuário &quot;monitoramento&quot; já existe), mas não atribua direitos.
1. Execute a extração de arquivos.
1. Leia o **readme** arquivo.
1. Atualize o **netconf.xml** arquivo de configuração.
1. Atualize o **netreport.bat** (Windows) ou **netreport.sh** (Linux).

### Configurar o arquivo netconf.xml {#configuring-the-netconf-xml-file}

O arquivo de configuração XML contém os seguintes elementos:

* [Elemento &quot;Propriedades&quot;](#properties--element)
* [Elemento &quot;Instance&quot;](#instance--element)
* [Elemento &quot;Host&quot;](#host--element)
* [Subelementos](#sub-elements)

Veja um exemplo de configuração:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<netconf>
  <properties mailServer="mail.adobe.net" mailFrom="mail@adobe.com" recipientList="recipient@adobe.com">
    <nightMode start="00:00 am" end="07:00 am"/>
    <buildRange minimum="7829" maximum="8180"/>
    <buildRange minimum="8300" maximum="8400"/>
    <sla/>
  </properties>

  <instance name="dev" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devrd.domain.com" alias="devrd" sessiontoken="monitoring" criticalLevel="1" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="false" isSecure="false"/>
                                <redir url="/r/test"/>
                                <http url="/nl/jsp/ping.jsp"/>
                </host>
                <host name="devtrk.domain.com" alias="devtrk" sessiontoken="monitoring" criticalLevel="0" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="true" isSecure="false"/>
                </host>
  </instance>
  <host name="dev-test" alias="dev-test" sessiontoken="monitoring" criticalLevel="2">
                <ncs instance="dev" url="/nl/jsp/soaprouter.jsp" includeDead="false"/>
  </host>
</netconf>
```

>[!NOTE]
>
>Você pode especificar várias configurações adicionando um sufixo à variável **netconf.xml** arquivo, por exemplo, **netconf-dev.xml**, **netconf-prod.xml**, etc. Em seguida, especifique a configuração a ser usada para executar o netreport no **netreport.bat** ou **netreport.sh** arquivos adicionando **$JAVA_HOME/bin/java netreport dev** ou **@%JAVA_HOME%binjava netreport prod** por exemplo.

>[!IMPORTANT]
>
>Para o **monitoramento** operador para funcionar, a máquina na qual o netreport é executado deve estar em uma zona de segurança que esteja **sessionTokenOnly** modo. Se nenhuma máscara IP confiável tiver sido especificada para este operador, a zona de segurança também deverá estar em **allowEmptyPassword** e **allowUserPassword** modo.

#### Elemento &quot;Propriedades&quot; {#properties--element}

Esse elemento é usado para preencher a configuração de emails, ou seja,

* **mailServer**: servidor SMTP usado para enviar emails (por exemplo: smtp.domain.net).
* **mailFrom**: endereço de email do remetente do relatório (por exemplo: monitoring@domain.net).
* **recipientList**: a lista de endereços de email dos recipients do monitoramento. Os endereços devem ser separados por vírgulas (sem espaços).
* &#39;**noite** O modo &quot; (opcional) é usado para evitar o envio de emails entre o período de tempo especificado. Em vez disso, os dados são consolidados e um email sobre a atividade da noite é enviado após o horário de término (7:00 por padrão).
* A variável **buildRange** o subelemento (opcional) permite especificar um número de build mínimo e máximo. Um erro será gerado para todos os computadores cujo número de build não se enquadra nesse intervalo

   ```
   <buildRange minimum="0000" maximum="9999"/>
   ```

* Você pode adicionar um **`<sla>`** (opcional) subelemento na variável **propriedades** elemento. Um arquivo de log será gerado sempre que o netreport for executado. O nome do arquivo contém o nome da configuração e a data e hora, por exemplo **dev_06_12_13_16_47_05.tmp**. O arquivo contém as seguintes informações: nome da instância, nome da máquina, nível de gravidade, (0 a 3, de menos crítico para mais crítico), data (formato de carimbo de data e hora), tempo decorrido (em milissegundos) entre a consulta e a resposta, serviço usado (http, ncs, ncsex, redir). Essas informações são separadas por marcas de tabulação e quebras de linha no final de cada serviço.

>[!NOTE]
>
>A variável **persistHtmlFile** atributo com o valor &quot;true&quot; na variável **`<property>`** elemento é usado para registrar o status de monitoramento mais recente no arquivo **netreport.md**. Esse arquivo é salvo no diretório de instalação.

#### Elemento &quot;Instance&quot; {#instance--element}

Esse elemento permite reagrupar vários computadores (hosts) na mesma instância. Os nomes de instância aparecem na primeira parte do email de monitoramento. Você pode clicar no nome de uma instância para acessar os detalhes sobre cada máquina.

```
instance name="instanceName" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devcamp.domain.com" ...>
                       ...
                </host>
                <host name="devtrack.domain.com" ...>
                       ...
                </host>
</instance
```

* **name**: nome da instância que aparecerá na primeira parte do email.
* **recipientList** (opcional): permite enviar um relatório de monitoramento sobre uma instância específica por email.

#### Elemento &quot;Host&quot; {#host--element}

Esse elemento configura o monitoramento de um determinado servidor no host, ou seja,

* **name**: nome da máquina a ser monitorada.
* **alias** (opcional): nome da máquina monitorada como ele aparecerá no relatório.
* **sessionToken**: fornece autenticação de logon por meio de um token de sessão autorizado.

   Para configurar o token de sessão, selecione o **monitoramento** operador no console do Adobe Campaign. No **Direitos de acesso** especifique os endereços IP das máquinas autorizadas a monitorar essa instância. Você poderá se conectar à página de monitoramento dessas máquinas usando o **monitoramento** e sem precisar especificar uma senha.

   ![](assets/ncs_operators_rights_02.png)

* **criticalLevel** (opcional): permite que você classifique os erros para serem exibidos por nível de gravidade. Os valores possíveis são &#39;0&#39; (todos os níveis exibidos), &#39;1&#39; (somente erros altos e críticos exibidos) e &#39;2&#39; (somente erros críticos exibidos). Se este atributo não for fornecido, todos os níveis de erro serão exibidos.
* **filtro** (opcional): permite excluir determinados erros de workflow, por exemplo **filter=&quot;wkf;wkf1&quot;**. Os rótulos do fluxo de trabalho devem ser separados por ponto e vírgula.

#### Subelementos {#sub-elements}

* **tcp**: verifica se o servidor está ativo ou inativo. Você deve digitar um número de porta.
* **http**: verifica se o servidor Web existe (o servidor de aplicativos está operacional).
* **ncs**: verifica os processos na instância inserida no atributo &quot;instance&quot; (erros de workflow, uso de memória, etc.). A variável **incluído** (obrigatório) o atributo oferece a opção de exibir processos inativos (valores &quot;true&quot; ou &quot;false&quot;).
* **redirecionar**: verifica o rastreamento.

Na maioria dos casos, apenas a **ncs** e **redirecionar** subelementos podem ser mantidos.

Em qualquer caso, determinados nós podem ser sobrecarregados nos subelementos (por exemplo, o nó **port=75** para sobrecarregar a porta usada para a conexão http, ncs ou redirecionamento):

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

No **ncs**, **redirecionar** e **http** subelementos, é possível adicionar a variável **isSecure** attribute (opcional) para escolher se usa ou não o protocolo https (valores &quot;true&quot; ou &quot;false&quot;). Se esse atributo não for fornecido, o protocolo http será usado.

### Configurar o arquivo netreport.bat ou netreport.sh {#configuring-the-netreport-bat-or-netreport-sh--file}

Para configurá-lo, edite esse arquivo e indique em qual diretório o JRE ou JDK está instalado.

### Iniciando monitoramento {#launching-monitoring}

Para iniciar o monitoramento, execute o **netreport.bat** ou **netreport.sh** em intervalos regulares por meio de um script. Um relatório é enviado após a primeira execução e somente no caso de uma mudança de status.

### Monitoramento de testes {#testing-monitoring}

Para testar o monitoramento, execute o **netreport.bat** ou **netreport.sh** arquivo.

Um email é enviado aos recipients especificados no **recipientList** do **netconf.xml** arquivo.
