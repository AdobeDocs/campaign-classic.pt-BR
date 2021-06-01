---
product: campaign
title: Falha ao conectar
description: Falha ao conectar
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 4%

---

# Falha ao conectar{#failure-to-connect}

Os motivos para um problema de conexão podem ser múltiplos e dependem de vários contextos.

Você pode tentar os testes a seguir e, se a falha de conexão persistir, entre em contato com o [Adobe Customer Care](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



<table> 
<thead> 
<tr> 
<th>Verifica<br /> </th> 
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
<td>Faça logon no: <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. O servidor deve retornar o seguinte tipo de mensagem: &lt;redir status='OK' date='AAA/MM/DD HH:MM:SS' build='XXXX' host='&lt;hostname&gt;' localHost='&lt;server&gt;'/&gt;
Se não obter esse resultado, verifique na configuração do servidor da Web se a integração é levada em conta.</td>
</tr>
<tr> 
<td>Conecte-se ao seguinte URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Se você obter um erro Tomcat Java, verifique se a integração JAVA foi executada corretamente. Ele é integrado ao arquivo [caminho do aplicativo]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Conecte-se ao seguinte URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Se você obter uma página em branco, verifique se o módulo Web do Adobe Campaign foi iniciado. O comando nlserver pdump deve retornar o servidor de aplicativos para Adobe Campaign Classic (build 7.X YY.R XXX@SHA1) de DD/MM/AAAA. Caso contrário, reinicie o módulo com o comando nlserver start web</td>
</tr>
<tr>
<td>Verifique a configuração geral das zonas de segurança.</td>
<td>Para obter mais informações sobre como configurar zonas de segurança, consulte <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=en#configuring-campaign-server"/>esta seção.</a></td>
</tr>
<tr>
<td>O comando nlserver pdump retorna <b>No tasks</b></td>
<td>Você deve reiniciar o aplicativo Adobe Campaign inteiro. Para fazer isso, use o seguinte comando: <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
