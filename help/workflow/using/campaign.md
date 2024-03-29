---
product: campaign
title: Campanha
description: Campanha
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
feature: Workflows
topic-tags: technical-workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 100%

---


# Campanha{#campaign}



Os workflows detalhados abaixo são instalados com o módulo **Campaign** por padrão. Para obter mais informações sobre esse módulo, consulte esta[seção](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>Esses workflows DEVEM ser iniciados para que os processos de campanha sejam executados em um nível de campanha.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Cost calculation</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span><br /> </td> 
   <td> Esse workflow inicia o cálculo das linhas de despesas e custos nos orçamentos, planos, programas, campanhas, entregas e tarefas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Stock: Orders and alerts</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span><br /> </td> 
   <td> Este workflow inicia o cálculo de estoque nas linhas de pedido e gerencia os limites de aviso.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Empregos em deliveries em campanhas</span><br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span><br /> </td> 
   <td> Esse fluxo de trabalho aciona as entregas aprovadas e inicia o pós-processamento no provedor de serviços para uma entrega externa. Também envia notificações e lembretes de aprovação.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Campaign jobs</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span><br /> </td> 
   <td> Esse workflow gerencia as tarefas para campanhas de marketing (inicia o target, extrai arquivos etc.). Ele também cria workflows relacionados a campanhas recorrentes e periódicas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Empregos em prestadores de serviços</span> <br /> </td> 
   <td> <span class="uicontrol">vendorMgt</span><br /> </td> 
   <td> Esse workflow inicia processos do provedor de serviços (email para o roteador e o pós-processamento) após a aprovação de entregas. <br /> </td> 
  </tr> 
 </tbody> 
</table>

