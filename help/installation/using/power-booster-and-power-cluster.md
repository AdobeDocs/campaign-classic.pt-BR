---
product: campaign
title: Power Boster e Power Cluster
description: Power Boster e Power Cluster
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
TQID: https://experienceleague.adobe.com/lcr5Xfipd9cDuglWBqBsiVXJUUZqQxLEmzzZPrAEhHU
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: a7760dfc-5c44-4d77-bb68-c50b1e265c93
subfeature_v2: id: ac9c0a9c-8a76-4419-bd64-9c34c5782666id: fb2a841f-c522-491f-9901-a1b939d252df
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 412
ht-degree: 6%

---

# Power Boster e Power Cluster{#power-booster-and-power-cluster}



## Visão geral {#overview}

O Adobe Campaign fornece dois conjuntos de opções de arquitetura predefinidas para dimensionar sua implantação:

* **Power Booster**

  Essa opção oferece suporte a uma única instância de execução adicional dissociada da instância de aplicativo principal do Adobe Campaign. As instâncias de execução dedicadas podem ser hospedadas remotamente ou por terceiros. Quando implementados, a execução do email, o rastreamento, as mirror pages e as mensagens de rejeição são tratadas independentemente das funções da aplicação central.

* **Cluster de Energia**

  Essa opção oferece suporte a 2 a N instâncias de execução clusterizadas dissociadas da instância de aplicativo principal do Adobe Campaign em relação a um determinado aplicativo. Os clusters podem ser hospedados remotamente, em implantações distribuídas e por terceiros. Além dos benefícios do isolamento de processos, a opção Adobe Campaign Power Cluster permite redundância e estratégias de scale-out usando hardware comercial para uma evolução simplificada do SLA ou do desempenho.

![](assets/architectural_options_diagram.png)

## Candidaturas elegíveis {#eligible-applications}

As opções Power Boster e Power Cluster podem ser usadas pelos seguintes aplicativos:

* Campaign
* Entrega
* Centro de mensagens

## Matriz de recomendações arquitetônicas {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Arquitetura padrão</strong><br /> </td> 
   <td> <strong>Power Booster</strong><br /> </td> 
   <td> <strong>Cluster de Energia</strong><br /> </td> 
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
   <td> O do banco de dados primário<br /> </td> 
   <td> 24 horas por dia, 7 dias por semana, exceto janelas de manutenção e tempos de inatividade para a instância de execução<br /> </td> 
   <td> Serviço 24/7/365 possível<br /> </td> 
  </tr> 
  <tr> 
   <td> Segurança<br /> </td> 
   <td> O data mart é potencialmente acessível a partir da internet pública<br /> </td> 
   <td> O armazém de dados está isolado de componentes frontais voltados para a Internet<br /> </td> 
   <td> O armazém de dados está isolado de componentes frontais voltados para a Internet<br /> </td> 
  </tr> 
  <tr> 
   <td> Modelo de implantação<br /> </td> 
   <td> Tudo em um site (pode ser no local ou na nuvem)<br /> </td> 
   <td> É possível fazer marketing local com execução na nuvem<br /> </td> 
   <td> Marketing local com execução na nuvem; execução em diferentes regiões possível<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Recomendações {#recommendations}

* Uma instância de execução deve ser dedicada a um serviço. Não é possível instalar um pacote para um serviço que você não assinou. Por exemplo, se você assinar a opção **Power Booster** para o serviço **Centro de Mensagens**, poderá instalar o pacote **[!UICONTROL Execution of transactional messages]** somente na instância de execução dedicada. Verifique o contrato de licença.
* Como as instâncias dedicadas (ou clusters) são instâncias do Adobe Campaign, as recomendações são as mesmas de uma instância principal. Para obter mais informações, consulte [este documento](../../production/using/foreword.md).
* Para configurar corretamente a instância do ponto de vista de um banco de dados/componentes de hardware, entre em contato com os Adobe Campaign Professional Services.
