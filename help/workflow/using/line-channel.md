---
product: campaign
title: Canal LINE
description: Canal LINE
hide: true
feature: Workflows
source-git-commit: 76f483dcda9f8a5ed93355d68bb1d1a589d55722
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

