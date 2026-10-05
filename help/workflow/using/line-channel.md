---
product: campaign
title: Canal LINE
description: Canal LINE
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 100%
---

# Canal LINE{#line-channel}



Os fluxos de trabalho detalhados abaixo são instalados com o módulo do **canal LINE** por padrão. Para obter mais informações sobre esse módulo, consulte esta[seção](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Atualização do token de acesso LINE V2</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> Este fluxo de trabalho atualiza o token de acesso para LINE V2.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Excluir usuários bloqueados do LINE</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> Esse fluxo de trabalho garante que os dados dos usuários LINE V2 sejam excluídos após bloquearem a conta oficial LINE por 180 dias.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Migração do MID para LineUserID</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> Esse fluxo de trabalho gera a ID de usuários LINE V2 para migração de LINE V1 para LINE V2.<br /> </td> 
  </tr> 
 </tbody> 
</table>

