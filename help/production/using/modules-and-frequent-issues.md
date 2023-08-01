---
product: campaign
title: Módulos e problemas frequentes
description: Módulos e problemas frequentes
feature: Monitoring, Troubleshooting
badge-v7-only: label="v7" type="Informative" tooltip="Aplicável somente ao Campaign Classic v7"
badge-v7-prem: label="no local e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 12%

---

# Módulos e problemas frequentes{#modules-and-frequent-issues}



Esta é uma lista de módulos afetados por problemas frequentes:

<table> 
 <thead> 
  <tr> 
   <th> Módulo </th> 
   <th> Escopo da execução </th> 
   <th> Solução de problemas </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportar </td> 
   <td> Execução de um processo de exportação<br /> </td> 
   <td> O operador que agendou essa exportação precisa reiniciá-la. Delta ou relançamento completo.<br /> </td> 
  </tr> 
  <tr> 
   <td> importar </td> 
   <td> Execução de um processo de importação<br /> </td> 
   <td> O operador que agendou essa exportação precisa reiniciá-la. Verifique se há duplicatas no banco de dados.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Leitura da caixa de emails de devolução<br /> </td> 
   <td> Verifique esse módulo se os emails de devolução não forem mais encaminhados.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Entregar emails<br /> </td> 
   <td> Verifique esse módulo se os emails não estiverem mais sendo enviados.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Mantém estatísticas de conexão do MTA<br /> </td> 
   <td> Verifique esse módulo se os emails não estiverem mais sendo enviados.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Gravação de log<br /> </td> 
   <td> Se alguns registros estiverem ausentes nos arquivos de registro, verifique se o módulo está usando a porta 6666. Consulte <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Lista de portas abertas</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> rastreamento </td> 
   <td> Consolidação e recuperação de logs de rastreamento<br /> </td> 
   <td> Verifique esse módulo se os logs de rastreamento não estiverem mais encaminhados.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Servidor de gravação e limpeza do log de rastreamento<br /> </td> 
   <td> Verifique esse módulo se os logs de rastreamento não forem mais encaminhados e não houver mais rastreamentos de logs nos arquivos no servidor. Consulte <a href="../../production/using/tracking-logs-issues.md" target="_blank">Problemas de logs de rastreamento</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> watchdog </td> 
   <td> Instância de inicialização e monitoramento<br /> </td> 
   <td> Verifique esse módulo se nenhum processo for iniciado.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Servidor de aplicativos (HTTP e SOAP)<br /> </td> 
   <td> Verifique esse módulo se o console e as conexões da web não funcionarem e acione um <strong>xtk:session</strong> erro de tipo<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Controla a execução da instância do fluxo de trabalho.<br /> </td> 
   <td> Se você encontrar algum problema, reinicie este módulo. Se necessário, aplique o procedimento para aumentar a precisão dos registros detalhados na <a href="../../production/using/log-precision.md" target="_blank">Log de precisão</a> seção.<br /> </td> 
  </tr> 
 </tbody> 
</table>
