---
product: campaign
title: Falha ao conectar
description: Falha ao conectar
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 4%

---

# Falha ao conectar{#failure-to-connect}

![](../../assets/v7-only.svg)

Os motivos para um problema de conexão podem ser múltiplos e dependem de vários contextos.

Você pode tentar os testes a seguir e, se a falha de conexão persistir, entre em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/using/support-for-experience-cloud.html).



<table> 
<thead> 
<tr> 
<th>Controlos<br /> </th> 
<th>Solução<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>Você tem acesso à Internet em seu computador?</td> 
<td>Verifique se você pode se conectar a sites na Internet (por exemplo). Se você não conseguir se conectar, o problema estará em sua máquina. Entre em contato com o administrador do sistema.</td>
</tr>
<tr> 
<td>É possível se conectar ao servidor que hospeda a Adobe Campaign por meio de outro serviço?</td> 
<td>Conecte-se ao servidor via SSH ou qualquer outro meio. Se isso não for possível, sua empresa host tem um problema. Entre em contato com o administrador do sistema.</td>
</tr>
<tr> 
<td>O servidor Web responde?</td> 
<td>Conecte-se ao URL de acesso do servidor do Adobe Campaign usando um navegador da Web: <b>http(s):// &lt;urlserver&gt;</b>. Se não responder, o servidor da Web será interrompido no computador. Entre em contato com o administrador do sistema da empresa de host para reiniciar o serviço.</td>
</tr>
<tr> 
<td>O Adobe Campaign foi integrado corretamente?</td> 
<td>Faça logon no: <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. O servidor deve retornar o seguinte tipo de mensagem: &lt;redir status="OK" date="YYYY/MM/DD HH&lt;span id="0" translate="no"/&gt;SS" build="XXXX" host="&lt;hostname&gt;" localhost="&lt;server&gt;" /&gt;
Se não obter esse resultado, verifique na configuração do servidor da Web se a integração é levada em conta.:MM:</td>
</tr>
<tr> 
<td>Conecte-se ao seguinte URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>Se você obter um erro Tomcat Java, verifique se a integração JAVA foi executada corretamente. Ele é integrado ao arquivo [caminho do aplicativo]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Conecte-se ao seguinte URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>Se você obter uma página em branco, verifique se o módulo Web do Adobe Campaign foi iniciado. O comando nlserver pdump deve retornar o servidor de aplicativos para Adobe Campaign Classic (build 7.X YY.R XXX@SHA1) de DD/MM/AAAA. Caso contrário, reinicie o módulo com o comando nlserver start web</td>
</tr>
<tr>
<td>Verifique a configuração geral das zonas de segurança.</td>
<td>Para obter mais informações sobre a configuração de zonas de segurança, consulte <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=en#configuring-campaign-server"/>esta seção.</a></td>
</tr>
<tr>
<td>O comando nlserver pdump retorna <b>Nenhuma tarefa</b></td>
<td>Você deve reiniciar o aplicativo Adobe Campaign inteiro. Para fazer isso, use o seguinte comando: <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
