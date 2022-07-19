---
product: campaign
title: Workflow técnico de renderização da caixa de entrada
description: Esta seção descreve o workflow técnico instalado com o pacote de renderização da caixa de entrada
feature: Workflows, Inbox Rendering
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 70%

---


# Renderização da Caixa de entrada (IR){#inbox-rendering}

![](../../assets/v7-only.svg)

O fluxo de trabalho detalhado abaixo é instalado com o módulo **Renderização da Caixa de entrada** por padrão. Para mais informações sobre renderização da Caixa de entrada, consulte esta [seção](../../delivery/using/inbox-rendering.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Atualizar rede seed para Renderização da Caixa de entrada</strong><br /> </td> 
   <td> <span class="uicontrol">updateRenderingSeeds</span> <br /> </td> 
   <td> Esse workflow atualiza endereços de email usados para a renderização da Caixa de entrada e funciona somente se a porta HTTPS estiver aberta para <strong>https://deliverability-app.neolane.net/deliverability</strong>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

