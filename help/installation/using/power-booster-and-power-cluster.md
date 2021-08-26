---
product: campaign
title: Power Boster e Power Cluster
description: Power Boster e Power Cluster
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 6%

---

# Power Boster e Power Cluster{#power-booster-and-power-cluster}

![](../../assets/v7-only.svg)

## Visão geral {#overview}

O Adobe Campaign fornece dois conjuntos de opções de arquitetura pré-embaladas para dimensionar sua implantação:

* **Power Boster**

   Essa opção fornece suporte para uma única instância de execução adicional dissociada da instância de aplicativo principal do Adobe Campaign. As instâncias de execução dedicadas podem ser hospedadas remotamente ou por terceiros. Quando implementados, a execução de email, o rastreamento, as mirror pages e as mensagens de devolução são manipuladas independentemente das funções centrais do aplicativo.

* **Cluster de energia**

   Essa opção oferece suporte para 2 a N instâncias de execução em cluster dissociadas da instância principal do aplicativo Adobe Campaign em relação a um determinado aplicativo. Os clusters podem ser hospedados remotamente, em implantações distribuídas e por terceiros. Além dos benefícios do isolamento do processo, a opção Adobe Campaign Power Cluster permite redundância e estratégias de escalabilidade usando hardware de mercadoria para uma evolução simplificada do SLA ou do desempenho.

![](assets/architectural_options_diagram.png)

## Candidaturas elegíveis {#eligible-applications}

As opções Power Booster e Power Cluster podem ser usadas pelos seguintes aplicativos:

* Campaign
* Entrega
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
   <td> A do banco de dados principal<br /> </td> 
   <td> 24/7 exceto janelas de manutenção e tempos de inatividade para a instância de execução<br /> </td> 
   <td> Serviço 24/7/365 possível<br /> </td> 
  </tr> 
  <tr> 
   <td> Segurança<br /> </td> 
   <td> O Data mart é potencialmente acessível a partir da Internet pública<br /> </td> 
   <td> O Data Smart é isolado de componentes frontais e voltados para a Internet<br /> </td> 
   <td> O Data Smart é isolado de componentes frontais e voltados para a Internet<br /> </td> 
  </tr> 
  <tr> 
   <td> Modelo de implantação<br /> </td> 
   <td> Tudo em um site (pode estar no local ou na nuvem)<br /> </td> 
   <td> Marketing no local com execução na nuvem possível<br /> </td> 
   <td> Marketing no local com execução na nuvem; execução em regiões diferentes possível<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Recomendações {#recommendations}

* Uma instância de execução deve ser dedicada a um serviço. Não é possível instalar um pacote para um serviço ao qual você não se inscreveu. Por exemplo, se assinar a opção **Power Boster** para o serviço **Message Center**, você só poderá instalar o pacote **[!UICONTROL Execution of transactional messages]** na instância de execução dedicada. Verifique o contrato de licença.
* Como as instâncias dedicadas (ou clusters) são instâncias do Adobe Campaign, as recomendações são as mesmas de uma instância principal. Para obter mais informações, consulte [este documento](../../production/using/foreword.md).
* Para configurar adequadamente a instância do ponto de vista de um banco de dados/componentes de hardware, entre em contato com o Adobe Campaign Professional Services.
