---
product: campaign
title: Solução de problemas do rastreamento
description: Esta seção fornece perguntas comuns relacionadas à configuração e à implementação do rastreamento no Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 62e67a39-1e5c-4716-a3f3-b0ca69693cd0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '759'
ht-degree: 100%

---

# Solução de problemas de rastreamento {#tracking-troubleshooting}

![](../../assets/common.svg)

Nesta seção, você encontrará perguntas comuns relacionadas à configuração e à implementação de rastreamento no Adobe Campaign Classic.

## O fluxo de trabalho de rastreamento está falhando {#tracking-workflow-failing}

Meu fluxo de trabalho de rastreamento está falhando. Como posso detectar as linhas corrompidas no arquivo de rastreamento?

>[!NOTE]
>
>Disponível somente para Windows

O arquivo de log de rastreamento corrompido .../nl6/var/&lt;instance_name>/redir/log/0x0000 log pode interromper o fluxo de trabalho de rastreamento. Para detectar facilmente linhas corrompidas e removê-las para retomar o fluxo de trabalho de rastreamento, você pode usar os comandos abaixo.

### Sei em qual arquivo está a linha corrompida

Nesse caso, linhas corrompidas podem ser encontradas no arquivo de log 0x00000000000A0000.log, mas o mesmo processo pode ser aplicado a um conjunto de arquivos, um por um.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

Em seguida, você pode interromper o fluxo de trabalho de rastreamento, excluir as linhas corrompidas e reiniciar o fluxo de trabalho.

### Não sei em qual arquivo está a linha corrompida

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

## Os links de rastreamento falham intermitentemente {#tracking-links-fail-intermittently}

Quando você tenta acessar os links de rastreamento, a seguinte mensagem é exibida:

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

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

1. Verifique manualmente se o arquivo &lt;deliveryID>.xml existe no computador no diretório .../nl6/var/&lt;instance_name>/redir/url/&lt;YYYY> (YYYY representa o ano do delivery).

1. Verifique manualmente se &lt;trackingUrlId> pode ser encontrado no arquivo &lt;deliveryID>.xml.

1. Verifique manualmente a existência de broadlogID no delivery deliveryID relacionado.

1. Verifique as permissões dos arquivos &lt;deliveryID>.xml no diretório .../nl6/var/&lt;instance_name>/redir/url/year.

   Deve haver pelo menos 644 permissões para que o Apache possa ler urls de rastreamento a fim de redirecionar o link solicitado.

## Atualizando a opção NmsTracking_Pointer? {#updating-option}

Siga estas etapas ao atualizar a opção NmsTracking_Pointer:

1. Interrompa o fluxo de trabalho de rastreamento.

1. Interrompa o serviço trackinglogd.

1. Atualize a opção NmsTracking_Pointer para o valor desejado.

1. Reinicie o serviço trackinglogd.

1. Reinicie o fluxo de trabalho de rastreamento.

## O rastreamento não parece funcionar com algum WebMail {#webmail}

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

Para entender onde está o avanço de linha extra, é possível substituir a expressão JavaScript por uma STRING de string fixa.

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

Para entender onde está o avanço de linha extra, é possível substituir a expressão JavaScript por uma STRING de string fixa.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

## A recuperação de logs de rastreamento é muito lenta {#slow-retrieval}

Quando a instância não recupera logs de rastreamento diretamente, mas de um servidor Adobe Campaign Classic distante, os logs são recuperados por meio da chamada SOAP GetTrackingLogs definida no esquema remoteTracking.

Uma opção no arquivo serverConf.xml permite que você defina o número de logs recuperados simultaneamente por meio deste método: logCountPerRequest.

O valor padrão de logCountPerRequest igual a 1000 pode ser muito pequeno em alguns casos. Os valores aceitos devem estar entre 0 e 10.000.

## Não foi possível vincular logs de rastreamento a recipients {#link-recipients}

No Adobe Campaign Classic, um target mapping deve ser único em termos de esquema de recipient versus esquemas broadlog/trackinglog.

![](assets/tracking-troubleshooting.png)

Não é possível usar vários esquemas de direcionamento com o mesmo esquema trackinglog, pois o fluxo de trabalho de rastreamento não conseguirá reconciliar os dados com a id de direcionamento.

Se você não quiser usar o target mapping pronto para uso com nms:recipient, recomendamos as seguintes abordagens:

* Se quiser usar o targeting dimension personalizado, será necessário criar o esquema broadLog/trackingLog personalizado usando nms:broadlog como modelo (por exemplo, nms:broadLogRcp, nms:broadLogSvc etc.).

* Se você quiser usar OOB trackingLogRcp/broadLogRcp, o targeting dimension precisará ser nms:recipient e a dimensão de filtragem poderá ser um esquema personalizado.
