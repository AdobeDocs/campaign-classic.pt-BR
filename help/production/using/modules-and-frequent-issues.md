---
product: campaign
title: Módulos e problemas frequentes
description: Módulos e problemas frequentes
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
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
   <th> Escopo de execução </th> 
   <th> Solução de problemas </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportar </td> 
   <td> Execução de um processo de exportação<br /> </td> 
   <td> O operador que programou essa exportação precisa reiniciá-la. Delta ou reinicialização completa.<br /> </td> 
  </tr> 
  <tr> 
   <td> importar </td> 
   <td> Execução de um processo de importação<br /> </td> 
   <td> O operador que programou essa exportação precisa reiniciá-la. Verifique se há duplicatas no banco de dados.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Leitura da caixa de email de devolução<br /> </td> 
   <td> Verifique este módulo se os emails de devolução não forem mais encaminhados.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Envia emails<br /> </td> 
   <td> Verifique este módulo se os emails não estiverem mais sendo enviados.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Mantém estatísticas de conexão MTA<br /> </td> 
   <td> Verifique este módulo se os emails não estiverem mais sendo enviados.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Gravação de log<br /> </td> 
   <td> Se alguns logs estiverem ausentes nos arquivos de log, verifique se o módulo está usando a porta 666. Consulte <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Lista de portas abertas</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> tracking </td> 
   <td> Consolidação e recuperação de logs de rastreamento<br /> </td> 
   <td> Verifique este módulo se os logs de rastreamento não forem mais encaminhados.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Rastreamento da gravação e limpeza do servidor de log<br /> </td> 
   <td> Verifique esse módulo se os logs de rastreamento não forem mais encaminhados e se não houver rastreamentos de logs nos arquivos no servidor. Consulte <a href="../../production/using/tracking-logs-issues.md" target="_blank">Problemas de logs de rastreamento</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> vigia </td> 
   <td> Inicialização e monitoramento da instância<br /> </td> 
   <td> Verifique este módulo se nenhum processo for iniciado.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Servidor de aplicativos (HTTP e SOAP)<br /> </td> 
   <td> Verifique este módulo se o console e as conexões da Web não funcionarem e acionarem um erro de tipo <strong>xtk:session</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Controla a execução da instância do fluxo de trabalho.<br /> </td> 
   <td> Se encontrar problemas, reinicie este módulo. Se necessário, aplique o procedimento para aumentar a precisão dos logs detalhados na seção <a href="../../production/using/log-precision.md" target="_blank">Precisão do log</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>
