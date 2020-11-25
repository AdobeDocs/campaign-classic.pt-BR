---
solution: Campaign Classic
product: campaign
title: Falha ao conectar
description: Falha ao conectar
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: cb6a2247e3b7617511aecf3d2d19985af0216494
workflow-type: tm+mt
source-wordcount: '340'
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
   <td>Conecte-se ao URL de acesso do servidor Adobe Campaign usando um navegador da Web: **`http(s):// <urlserver>`**. Se não responder, o servidor Web será interrompido no computador. Entre em contato com o administrador do sistema da empresa do host para reiniciar o serviço.</td>
  </tr>
  <tr> 
   <td>A Adobe Campaign foi integrada corretamente?</td> 
   <td>Faça logon no: **`http(s)://<urlserver>/r/test`** URL. O servidor deve retornar o seguinte tipo de mensagem

    &quot;
    &lt;redir status=&#39;OK&#39; date=&#39;AAAA/MM/DD HH:MM:SS&#39; build=&#39;XXXX&#39; host=&#39;&lt;nome do host>&#39; localHost=&#39;&lt;servidor>&#39;/>
    &quot;
    
    Se você não obter esse resultado, verifique na configuração do servidor Web se a integração é considerada.&lt;/td>
</tr>
  <tr> 
   <td>O módulo Adobe Campaign Web foi iniciado?</td> 
   <td>
   Conecte-se ao seguinte URL: **`http(s)://<URLSERVER>/nl/jsp/logon.jsp`** * Se você receber um erro Java do Tomcat:

    A integração do JAVA é realizada corretamente? A Adobe Campaign requer um SUN JDK.
    
    Ele é integrado ao arquivo **`[caminho do aplicativo]`/nl6/customer.sh**
    
    * Se você obter uma página em branco:
    
    O módulo da Web Adobe Campaign foi iniciado? Você deve obter:
    
    &quot;
    nlserver
    pdumpHH:MM:SS > Servidor de aplicativos para Adobe Campaign Classic (build XXX@SHA1 7.X YY.R) de DD/MM/AAAA
    [...]
    web@default (27515) - 55.2 Mb
    [..]
    &quot;
    
    * Caso contrário, reinicie usando o seguinte comando:
    
    &quot;Web de start
    
    nlserver&quot;&lt;/td>
</tr>
  <tr>
  	<td>Verifique a configuração geral das zonas de segurança.</td>
  	<td>Para obter mais informações sobre a configuração de zonas de segurança, consulte [esta seção](../../installation/using/configuring-campaign-server.md#definindo-zonas-de-segurança)</td>
  </tr>
 </tbody> 
</table>
