---
solution: Campaign Classic
product: campaign
title: Módulos e problemas frequentes
description: Módulos e problemas frequentes
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 5%

---


# Módulos e problemas frequentes{#modules-and-frequent-issues}

Esta é uma lista de módulos afetados por problemas frequentes:

<table> 
 <thead> 
  <tr> 
   <th> Módulo </th> 
   <th> Âmbito de execução </th> 
   <th> Solução de problemas </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportação </td> 
   <td> Execução de um processo de exportação<br /> </td> 
   <td> O operador que programou essa exportação precisa reiniciá-la. O delta ou a reinicialização completa.<br /> </td> 
  </tr> 
  <tr> 
   <td> importação </td> 
   <td> Execução de um processo de importação<br /> </td> 
   <td> O operador que programou essa exportação precisa reiniciá-la. Verifique se há duplicados no banco de dados.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Leitura da caixa de correio de rejeição<br /> </td> 
   <td> Verifique este módulo se os emails de rejeição não forem mais encaminhados.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Fornece emails<br /> </td> 
   <td> Verifique este módulo se os emails não estão mais sendo enviados.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Mantém as estatísticas de conexão MTA<br /> </td> 
   <td> Verifique este módulo se os emails não estão mais sendo enviados.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Registro<br /> </td> 
   <td> Se alguns registros estiverem ausentes nos arquivos de registro, verifique se o módulo está usando a porta 666. Consulte a <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Lista de portas</a>abertas.<br /> </td> 
  </tr> 
  <tr> 
   <td> rastreamento </td> 
   <td> Consolidação e recuperação de logs de rastreamento<br /> </td> 
   <td> Verifique este módulo se os logs de rastreamento não forem mais encaminhados.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Rastreamento de gravação e remoção de log do servidor<br /> </td> 
   <td> Verifique este módulo se os logs de rastreamento não forem mais encaminhados e se não houver rastreamentos de registros nos arquivos no servidor. Consulte os problemas com <a href="../../production/using/tracking-logs-issues.md" target="_blank">Logs de rastreamento</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> cão de guarda </td> 
   <td> Instância de inicialização e monitoramento<br /> </td> 
   <td> Verifique este módulo se nenhum start de processos for processado.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Servidor de aplicativos (HTTP e SOAP)<br /> </td> 
   <td> Verifique este módulo se o console e as conexões da Web não funcionam e dispare um erro de tipo <strong>xtk:session</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Controla a execução da instância do fluxo de trabalho.<br /> </td> 
   <td> Se encontrar algum problema, reinicie este módulo. Se necessário, aplique o procedimento para aumentar a precisão dos registros detalhados na seção de precisão <a href="../../production/using/log-precision.md" target="_blank">do</a> registro.<br /> </td> 
  </tr> 
 </tbody> 
</table>

