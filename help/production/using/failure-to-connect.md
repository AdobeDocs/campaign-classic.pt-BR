---
solution: Campaign Classic
product: campaign
title: Falha ao conectar
description: Falha ao conectar
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: fc5a44fe7bf4c88eca4634a67eaae48c722d8e5e
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 2%

---


# Falha ao conectar{#failure-to-connect}

Os motivos para um problema de conexão podem ser múltiplos e dependem de vários contextos.

Você pode tentar os testes a seguir e, se a falha na conexão persistir, entre em contato com o suporte **da** Adobe Campaign.



<table> 
<thead> 
<tr> 
<th>Verificações<br /> </th> 
<th>Solução<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>Você tem acesso à Internet em seu computador?</td> 
<td>Verifique se você pode se conectar a sites na Internet (por exemplo). Se você não conseguir se conectar, o problema está em sua máquina. Entre em contato com o administrador do sistema.</td>
</tr>
<tr> 
<td>Você pode se conectar ao servidor que hospeda a Adobe Campaign por meio de outro serviço?</td> 
<td>Conecte-se ao servidor via SSH ou qualquer outro meio. Se isso não for possível, a empresa do host apresenta um problema. Entre em contato com o administrador do sistema.</td>
</tr>
<tr> 
<td>O servidor Web responde?</td> 
<td>Conecte-se ao URL de acesso do servidor Adobe Campaign usando um navegador da Web: <b>http(s):// &lt;urlserver&gt;</b>. Se não responder, o servidor Web será interrompido no computador. Entre em contato com o administrador do sistema da empresa do host para reiniciar o serviço.</td>
</tr>
<tr> 
<td>A Adobe Campaign foi integrada corretamente?</td> 
<td>Faça logon no: <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. O servidor deve retornar o seguinte tipo de mensagem: &lt;redir status='OK' date='AAAA/MM/DD HH:MM:SS' build='XXXX' host='&lt;nome do host&gt;' localHost='&lt;servidor&gt;'/&gt;Se você não obtiver esse resultado, verifique na configuração do servidor Web se a integração é considerada.</td>
</tr>
<tr> 
<td>Conecte-se ao seguinte URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Se você obter um erro Java Tomcat, verifique se a integração JAVA foi realizada corretamente. Ele é integrado ao arquivo [caminho do aplicativo]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Conecte-se ao seguinte URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Se você obter uma página em branco, verifique se o módulo da Web da Adobe Campaign foi iniciado. O comando nlserver pdump deve retornar o servidor de aplicativos para Adobe Campaign Classic (compilação 7.X YY.R XXX@SHA1) de DD/MM/AAAA. Caso contrário, reinicie o módulo com o comando nlserver start web</td>
</tr>
<tr>
<td>Verifique a configuração geral das zonas de segurança.</td>
<td>Para obter mais informações sobre a configuração de zonas de segurança, consulte [esta seção](../../installation/using/configuring-campaign-server.md#definindo-zonas-de-segurança)</td>
</tr>
</tbody> 
</table>
