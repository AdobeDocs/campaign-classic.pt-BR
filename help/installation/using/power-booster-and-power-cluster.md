---
title: Power Boster e Power Cluster
seo-title: Power Boster e Power Cluster
description: Power Boster e Power Cluster
seo-description: null
page-status-flag: never-activated
uuid: 4d23ed42-a368-4bd6-afaf-48452e253d19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 715d2b69-5b47-4890-8b7d-1dc0a0d4ead8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c25e2a4f2280cdcc61e0522f8235149410b5dacf

---


# Power Boster e Power Cluster{#power-booster-and-power-cluster}

## Visão geral {#overview}

O Adobe Campaign oferece dois conjuntos de opções de arquitetura pré-embaladas para dimensionar sua implantação:

* **Power Boster**

   Esta opção oferece suporte para uma única instância de execução adicional dissociada da instância principal do aplicativo Adobe Campaign. As instâncias de execução dedicadas podem ser hospedadas remotamente ou por terceiros. Quando implementado, a execução de email, o rastreamento, as páginas espelhadas e as mensagens de rejeição são manipuladas independentemente das funções centrais do aplicativo.

* **Cluster de energia**

   Esta opção oferece suporte para 2 a N instâncias de execução clusterizadas dissociadas da instância principal do aplicativo Adobe Campaign em relação a um determinado aplicativo. Os clusters podem ser hospedados remotamente, em implantações distribuídas e por terceiros. Além dos benefícios do isolamento do processo, a opção Adobe Campaign Power Cluster permite redundância e estratégias de expansão usando hardware básico para uma evolução simplificada do SLA ou do desempenho.

![](assets/architectural_options_diagram.png)

## Pedidos elegíveis {#eligible-applications}

As opções de Power Booster e Power Cluster podem ser usadas pelos seguintes aplicativos:

* Campanha
* Delivery
* Centro de mensagens

## Matriz de recomendações arquitetônicas {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Arquitetura padrão</strong><br /> </td> 
   <td> <strong>Power Boster</strong><br /> </td> 
   <td> <strong>Cluster de energia</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Campanhas de email e interações de saída<br /> </td> 
   <td> Até aproximadamente 30 milhões de emails por mês<br /> </td> 
   <td> 30 a 100 milhões de emails por mês<br /> </td> 
   <td> Mais de 100 milhões de emails por mês<br /> </td> 
  </tr> 
  <tr> 
   <td> Mensagens transacionais<br /> </td> 
   <td> 50.000 por hora por servidor de execução<br /> </td> 
   <td> 50.000 por hora por servidor de execução<br /> </td> 
   <td> 50.000 por hora por servidor de execução<br /> </td> 
  </tr> 
  <tr> 
   <td> Disponibilidade<br /> </td> 
   <td> A da base de dados primária<br /> </td> 
   <td> 24 horas por dia, 7 dias por semana, exceto janelas de manutenção e tempos ociosos para a instância de execução<br /> </td> 
   <td> Serviço 24/7/365 possível<br /> </td> 
  </tr> 
  <tr> 
   <td> Segurança<br /> </td> 
   <td> O data mart é potencialmente acessível através da Internet pública<br /> </td> 
   <td> O Data mart é isolado de componentes frontais e voltados para a Internet<br /> </td> 
   <td> O Data mart é isolado de componentes frontais e voltados para a Internet<br /> </td> 
  </tr> 
  <tr> 
   <td> Modelo de implantação<br /> </td> 
   <td> Todos em um site (podem estar no local ou na nuvem)<br /> </td> 
   <td> Marketing no local com execução na nuvem possível<br /> </td> 
   <td> Marketing no local com execução na nuvem; execução em diferentes regiões possíveis<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Recomendações {#recommendations}

* Uma instância de execução deve ser dedicada a um serviço. Não é possível instalar um pacote para um serviço ao qual você não se inscreveu. Por exemplo, se você assinar a opção **Power Booster** para o serviço **Message Center** **[!UICONTROL Execution of transactional messages]** , poderá instalar apenas o pacote na instância de execução dedicada. Verifique o contrato de licença.
* Como as instâncias dedicadas (ou clusters) são instâncias do Adobe Campaign, as recomendações são as mesmas de uma instância principal. For more on this, refer to [this document](../../production/using/foreword.md).
* Para configurar adequadamente a instância de um ponto de vista de componentes de banco de dados/hardware, entre em contato com o Adobe Campaign Professional Services.

