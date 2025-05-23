---
product: campaign
title: Falha ao conectar
description: Falha ao conectar
feature: Monitoring
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 5%

---

# Falha ao conectar{#failure-to-connect}



Os motivos para um problema de conexão podem ser múltiplos e dependem de vários contextos.

Você pode tentar os seguintes testes e, se a falha de conexão persistir, entre em contato com o [Adobe Customer Care](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



<table> 
<thead> 
<tr> 
<th>Verificações<br /> </th> 
<th>Resolução<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>Você tem acesso à Internet no seu computador?</td> 
<td>Verifique se você pode se conectar a sites da Internet (por exemplo). Se você não conseguir se conectar, o problema está na sua máquina. Entre em contato com o administrador do sistema.</td>
</tr>
<tr> 
<td>Você pode se conectar ao servidor que hospeda o Adobe Campaign por meio de outro serviço?</td> 
<td>Conecte-se ao servidor via SSH ou qualquer outro meio. Se isso não for possível, a empresa host terá um problema. Entre em contato com o administrador do sistema.</td>
</tr>
<tr> 
<td>O servidor Web responde?</td> 
<td>Conecte-se à URL de acesso do servidor do Adobe Campaign usando um navegador da Web: <b>http(s):// &lt;urlserver&gt;</b>. Se não responder, o servidor Web é interrompido na máquina. Entre em contato com o administrador do sistema da empresa host para reiniciar o serviço.</td>
</tr>
<tr> 
<td>O Adobe Campaign foi integrado corretamente?</td> 
<td>Faça logon na URL: <b>http(s)://&lt;urlserver&gt;/r/test</b>. O servidor deve retornar o seguinte tipo de mensagem: &lt;redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='&lt;nome do host&gt;' localHost='&lt;servidor&gt;'/&gt;
Se você não obter esse resultado, verifique na configuração do servidor Web se a integração é levada em conta.</td>
</tr>
<tr> 
<td>Conecte-se à seguinte URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Se você obter um erro de Java do Tomcat, verifique se a integração JAVA foi executada corretamente. Ele está integrado ao arquivo [caminho do aplicativo]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Conecte-se à seguinte URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Se você obter uma página em branco, verifique se o módulo Web do Adobe Campaign foi iniciado. O comando nlserver dump deve retornar Application server for Adobe Campaign Classic (build 7.X YY.R XXX@SHA1) de DD/MM/YYYY. Caso contrário, reinicie o módulo com o comando nlserver start web</td>
</tr>
<tr>
<td>Verifique a configuração geral das zonas de segurança.</td>
<td>Para saber mais sobre como configurar zonas de segurança, consulte <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=pt-BR#configuring-campaign-server"/>esta seção.</a></td>
</tr>
<tr>
<td>O comando nlserver pdump retorna <b>Nenhuma tarefa</b></td>
<td>Você deve reiniciar todo o aplicativo do Adobe Campaign. Para fazer isso, use o seguinte comando: <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
