---
product: campaign
title: Introdução ao rastreamento
description: Saiba mais sobre as diretrizes gerais para rastreamento no Adobe Campaign
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: ba53107ce06c0484070cbe0943ba439d33d5f710
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 64%

---

# Introdução ao rastreamento de mensagens {#get-started-tracking}

>[!IMPORTANT]
>
>Para obter a **orientação geral de rastreamento** que se aplica ao Campaign Classic v7 e ao Campaign v8, consulte a [documentação de rastreamento de mensagens do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"}:
>
>* [Configurar links rastreados](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"}
>* [Configurar opções de rastreamento de URL](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/tracking/url-tracking){target="_blank"}
>* [Rastrear links personalizados](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/tracking/personalized-links){target="_blank"}
>* [Acessar logs de rastreamento](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"}
>* [Rastreamento de teste](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/testing-tracking){target="_blank"}
>* [Rastreamento de relatórios](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/reporting/delivery-reports#tracking-indicators){target="_blank"}
>
>**Esta página documenta apenas os recursos de rastreamento específicos do Campaign Classic v7**, principalmente para implantações híbridas e locais.

## Recursos de rastreamento

### Configuração de rastreamento {#configure-tracking}

Para o Campaign Classic v7 **implantações híbridas/no local**, é necessário configurar o rastreamento no nível da instância antes de usá-lo.

>[!NOTE]
>
>Para o Campaign v8 Managed Cloud Services, a configuração de rastreamento é executada pela Adobe.

**Princípio operacional**

Antes de usar o rastreamento, é necessário configurá-lo para a sua instância. A configuração precisa ser executada no(s) servidor(es) de aplicativos e no(s) servidor(es) da Web do Adobe Campaign.

No Campaign, há dois tipos de rastreamento:

* **Rastreamento web**: este modo permite rastrear visitas às páginas do seu site
* **Rastreamento de mensagens**: esse modo permite rastrear as entregas de mensagens e o comportamento do destinatário

O modo de rastreamento é selecionado durante a instalação. Para instalações no local, a configuração de rastreamento deve ser definida no nível da instância. [Saiba mais](../../installation/using/deploying-an-instance.md#operating-principle)

**Servidor de rastreamento**

Para configurar o rastreamento, sua instância deve ser declarada e registrada nos servidores de rastreamento. O servidor de rastreamento é usado para registrar e recuperar informações sobre URLs clicados pelos recipients.

Para instalações no local, o servidor de rastreamento geralmente é um servidor Web que executa o aplicativo Web do Adobe Campaign. O URL do servidor de rastreamento deve ser definido na configuração da instância. [Saiba mais](../../installation/using/deploying-an-instance.md#tracking-server)

**Salvar o rastreamento**

Depois que o rastreamento é configurado e os URLs são preenchidos, o servidor de rastreamento deve ser registrado. O registro permite que o Adobe Campaign salve informações de rastreamento e forneça relatórios e estatísticas sobre atividades rastreadas.

Para instalações locais, as informações de rastreamento são armazenadas no banco de dados e recuperadas por meio de workflows técnicos. O fluxo de trabalho técnico **Rastreamento** processa e armazena os dados de rastreamento coletados do servidor de redirecionamento. [Saiba mais](../../installation/using/deploying-an-instance.md#saving-tracking)

### Rastreamento de aplicativo web {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

>[!NOTE]
>
>**O rastreamento de aplicativos web é específico do Campaign Classic v7** e não está disponível no Campaign v8.

**Rastreamento de uma aplicação web**

Também é possível rastrear e medir visitas em páginas de aplicação web com tags de rastreamento. Essa funcionalidade pode ser usada para todos os tipos de aplicativo Web, como formulários e landing pages. [Saiba mais](../../web/using/tracking-a-web-application.md)

**Recusar rastreamento da aplicação web**

A opção de recusar o rastreamento de aplicações web permite que você interrompa o rastreamento dos comportamentos da Web de usuários finais que recusam o rastreamento comportamental. Você pode incluir a capacidade de exibir um banner em aplicações web ou landing pages para permitir que os usuários recusem. [Saiba mais](../../web/using/web-application-tracking-opt-out.md)

## Solução de problemas de rastreamento {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

As seguintes dicas de solução de problemas se aplicam a **implantações híbridas/no local do Campaign Classic v7**. Algumas informações também podem se aplicar às implantações locais do Campaign v8. Para obter ajuda com o Managed Cloud Services do Campaign v8, entre em contato com o representante da Adobe.

Para obter as etapas básicas de solução de problemas de rastreamento no Campaign v8, consulte a [Documentação sobre solução de problemas de rastreamento no Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/tracking/tracking-logs#troubleshooting){target="_blank"}.

### Verificações básicas {#basic-checks}

**Verifique se o processo trackinglogd está em execução**

Esse processo lê a memória compartilhada do IIS/Servidor Web e grava os logs de redirecionamento.

Você pode acessá-la na Página inicial selecionando a guia Monitoramento na sua instância. Você também pode executar o seguinte comando na instância: `<user>@<instance>:~$ nlserver pdump`

Se o processo trackinglogd não aparecer na lista, inicie-o com o seguinte comando na instância: `<user>@<instance>:~$ nlserver start trackinglogd`

**Verifique se o fluxo de trabalho técnico de Acompanhamento foi executado recentemente**

Você pode localizar o fluxo de trabalho técnico de Rastreamento nas pastas de workflows técnicos da > Produção > de Administração.

### Solução avançada de problemas {#advanced-troubleshooting}

+++O fluxo de trabalho de rastreamento está falhando

>[!NOTE]
>
>Disponível somente para Windows

O arquivo de log de rastreamento corrompido .../nl6/var/&lt;instance_name>/redir/log/0x0000 log pode interromper o fluxo de trabalho de rastreamento. Para detectar facilmente linhas corrompidas e removê-las para retomar o fluxo de trabalho de rastreamento, você pode usar os comandos abaixo.

**Sei em qual arquivo a linha corrompida está**

Nesse caso, linhas corrompidas podem ser encontradas no arquivo de log 0x00000000000A0000.log, mas o mesmo processo pode ser aplicado a um conjunto de arquivos, um por um.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

Em seguida, você pode interromper o fluxo de trabalho de rastreamento, excluir as linhas corrompidas e reiniciar o fluxo de trabalho.

**Não sei em qual arquivo está a linha corrompida**

1. use a seguinte linha de comando para fazer verificar em todos os arquivos de rastreamento.

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. O comando lista todas as linhas corrompidas. Por exemplo:

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Um retorno de carro foi adicionado antes do Agente do Usuário para permitir melhor leitura e não reflete a renderização real.

1. Execute um comando grep para localizar o arquivo correspondente.

   ```
   $ grep -Rn <Log Id>
   # for example:
   $ grep -Rn 50x000000000FD7EC86
   ```

1. Localize o log com falha com o nome do arquivo e o número da linha. Por exemplo:

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Um retorno de carro foi adicionado antes do Agente do Usuário para permitir melhor leitura e não reflete a renderização real.

Em seguida, você pode interromper o fluxo de trabalho de rastreamento, excluir as linhas corrompidas e reiniciar o fluxo de trabalho.

+++

+++Os links de rastreamento falham intermitentemente

Quando você tenta acessar os links de rastreamento, a seguinte mensagem é exibida:

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&p1=1' cannot be found`

1. Acesse a URL &lt;redirection_server>/r/test e verifique se o número da compilação e o host local foram retornados pela solicitação.

1. Verifique a configuração spareServer no arquivo serverConf.xml do servidor de rastreamento. Essa configuração deve estar no modo de redirecionamento.

   ```
   <redirection>
      <spareServer _operation="update" enabledIf="$(hostname)!='test-rt1'" id="1"
      url="http://test-rt1:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt4'" id="4"
      url="http://test-rt4:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt3'" id="3"
      url="http://test-rt3:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!=test-rt2'" id="2"
      url="http://test-rt2:8080"/>
   </redirection>
   ```

1. Verifique manualmente se o arquivo &lt;deliveryID>.xml existe no computador no diretório .../nl6/var/&lt;instance_name>/redir/url/&lt;YYYY> (YYYY representa o ano da entrega).

1. Verifique manualmente se &lt;trackingUrlId> pode ser encontrado no arquivo &lt;deliveryID>.xml.

1. Verifique manualmente a existência de broadlogID na entrega deliveryID relacionado.

1. Verifique as permissões dos arquivos &lt;deliveryID>.xml no diretório .../nl6/var/&lt;instance_name>/redir/url/year.

   Deve haver pelo menos 644 permissões para que o Apache possa ler urls de rastreamento a fim de redirecionar o link solicitado.

+++

+++Atualização da opção NmsTracking_Pointer

Siga estas etapas ao atualizar a opção NmsTracking_Pointer:

1. Interrompa o fluxo de trabalho de rastreamento.

1. Interrompa o serviço trackinglogd.

1. Atualize a opção NmsTracking_Pointer para o valor desejado.

1. Reinicie o serviço trackinglogd.

1. Reinicie o fluxo de trabalho de rastreamento.

+++

+++O rastreamento não funciona com algum WebMail

Você pode personalizar a fórmula de rastreamento de cliques e especificar uma fórmula de rastreamento do Adobe Analytics personalizada.

Esse tipo de personalização precisa ser feito com cautela para evitar a adição de caracteres de avanço de linha. Todos os caracteres de avanço de linha presentes fora da expressão JavaScript estarão presentes na fórmula final.

Esse tipo de caractere extra de avanço de linha no URL de rastreamento levará a problemas em algum WebMail (AOL, GMail etc.).

**Primeiro exemplo:**

* Sintaxe incorreta

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>
  &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

* Sintaxe correta

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

Para entender onde está o avanço de linha extra, é possível substituir a expressão JavaScript por uma STRING fixa.

```
// Incorrect
STRING1
&cid=STRING2&bid=STRING3

// Correct
STRING1&cid=STRING2&bid=STRING3
```

**Segundo exemplo**

* Sintaxe incorreta

  ```
  <%@ include option='NmsTracking_ClickFormula' %>
  <% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

* Sintaxe correta

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

Para entender onde está o avanço de linha extra, é possível substituir a expressão JavaScript por uma STRING fixa.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

+++

+++A recuperação de logs de rastreamento é muito lenta

Quando a instância não recupera logs de rastreamento diretamente, mas de um servidor Adobe Campaign Classic distante, os logs são recuperados por meio da chamada SOAP GetTrackingLogs definida no esquema remoteTracking.

Uma opção no arquivo serverConf.xml permite que você defina o número de logs recuperados simultaneamente por meio deste método: logCountPerRequest.

O valor padrão de logCountPerRequest igual a 1000 pode ser muito pequeno em alguns casos. Os valores aceitos devem estar entre 0 e 10.000.

+++

+++Não foi possível vincular logs de rastreamento a destinatários

No Adobe Campaign Classic, um target mapping deve ser único em termos de esquema de destinatário versus esquemas broadlog/trackinglog.

![](assets/tracking-troubleshooting.png)

Não é possível usar vários esquemas de direcionamento com o mesmo esquema trackinglog, pois o fluxo de trabalho de rastreamento não conseguirá reconciliar os dados com a id de direcionamento.

Se você não quiser usar o target mapping pronto para uso com nms:recipient, recomendamos as seguintes abordagens:

* Se você quiser usar o targeting dimension personalizado, será necessário criar o esquema broadLog/trackingLog personalizado usando nms:broadlog como modelo (por exemplo, nms:broadLogRcp, nms:broadLogSvc etc.).

* Se você quiser usar OOB trackingLogRcp/broadLogRcp, o targeting dimension precisará ser nms:recipient e a dimensão de filtragem poderá ser um esquema personalizado.

+++
