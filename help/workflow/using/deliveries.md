---
product: campaign
title: Deliveries
description: Saiba mais sobre os workflows de delivery padrão
feature: Workflows
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 100%

---


# Entregas{#deliveries}

![](../../assets/common.svg)

Os fluxos de trabalho detalhados abaixo são instalados com o módulo **Deliveries** por padrão.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Relatórios de agregados</span> <br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span> <br /> </td> 
   <td> Este workflow atualiza agregados usados em relatórios. É acionado todos os dias às 2:00 AM por padrão.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Faturamento</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> Esse workflow envia o relatório de atividades do sistema para o operador 'faturamento' por email. É disparado todo dia 25 de cada mês por padrão.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Limpeza de alias</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Esse workflow padroniza os valores de enumeração. É acionado todos os dias às 3:00 AM por padrão.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Atualização para entregabilidade</span><br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Esse workflow permite criar a lista de regras de qualificação de email de devolução, bem como a lista de domínios e MXs na plataforma. Este workflow funciona somente se a porta HTTPS estiver aberta. Essas listas não são atualizadas a menos que o módulo Deliverability esteja instalado.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Limpeza do banco de dados</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Este workflow é o workflow de manutenção do banco de dados: faz diferentes cálculos das estatísticas e dos processos e exclui dados obsoletos do banco de dados de acordo com a configuração definida no assistente de implantação. É acionado todos os dias às 4:00 AM por padrão.</p> <p>Para obter mais informações, consulte esta <a href="../../production/using/database-cleanup-workflow.md">página</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Limpeza de fluxos de trabalho pausados</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>Esse workflow analisa workflows pausados que têm a severidade definida como normal e emite avisos e notificações quando ficam pausados por muito tempo. Após um mês, os workflows técnicos pausados são interrompidos definitivamente. Por padrão, é acionado toda segunda-feira às 5:00 AM.</p> <p>Para obter mais informações, consulte <a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Manuseio de fluxos de trabalho pausados</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Notificação da oferta</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> Esse workflow implanta ofertas aprovadas no ambiente online, bem como todas as categorias contidas no catálogo de oferta.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Previsão</span> <br /> </td> 
   <td> <span class="uicontrol">previsão</span> <br /> </td> 
   <td> Este workflow analisa os deliveries salvos no calendário provisional (cria logs provisionais). É acionado todos os dias às 1:00 AM por padrão.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rastreamento</span> <br /> </td> 
   <td> <span class="uicontrol">tracking</span> <br /> </td> 
   <td> Esse workflow realiza a recuperação e a consolidação de informações de rastreamento. Também garante o recálculo de rastreamento e estatísticas de delivery, principalmente aqueles usados pelos workflows de arquivamento do Centro de Mensagens. Por padrão, é acionado uma vez por hora. <br /> </td> 
  </tr> 
 </tbody> 
</table>

