---
product: campaign
title: Power Boster e Power Cluster
description: Power Boster e Power Cluster
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 7%

---

# Power Boster e Power Cluster{#power-booster-and-power-cluster}



## Visão geral {#overview}

O Adobe Campaign fornece dois conjuntos de opções de arquitetura predefinidas para dimensionar sua implantação:

* **Power Booster**

   Essa opção oferece suporte a uma única instância de execução adicional dissociada da instância de aplicativo principal do Adobe Campaign. As instâncias de execução dedicadas podem ser hospedadas remotamente ou por terceiros. Quando implementados, a execução do email, o rastreamento, as mirror pages e as mensagens de rejeição são tratadas independentemente das funções da aplicação central.

* **Cluster de energia**

   Essa opção oferece suporte a 2 a N instâncias de execução clusterizadas dissociadas da instância de aplicativo principal do Adobe Campaign em relação a um determinado aplicativo. Os clusters podem ser hospedados remotamente, em implantações distribuídas e por terceiros. Além dos benefícios do isolamento de processos, a opção Adobe Campaign Power Cluster permite redundância e estratégias de scale-out usando hardware comercial para uma evolução simplificada de SLA ou desempenho.

![](assets/architectural_options_diagram.png)

## Candidaturas elegíveis {#eligible-applications}

As opções Power Boster e Power Cluster podem ser usadas pelos seguintes aplicativos:

* Campaign
* Entrega
* Central de mensagens

## Matriz de recomendações arquitetônicas {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Arquitetura padrão</strong><br /> </td> 
   <td> <strong>Power Booster</strong><br /> </td> 
   <td> <strong>Cluster de energia</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Campanhas de email e interações de saída<br /> </td> 
   <td> Até aproximadamente 30 milhões de e-mails por mês<br /> </td> 
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
   <td> O do banco de dados principal<br /> </td> 
   <td> 24 horas por dia, 7 dias por semana, exceto janelas de manutenção e tempos de inatividade da instância de execução<br /> </td> 
   <td> Serviço 24/7/365 possível<br /> </td> 
  </tr> 
  <tr> 
   <td> Segurança<br /> </td> 
   <td> O armazém de dados pode ser acessado na internet pública<br /> </td> 
   <td> O armazém de dados está isolado de componentes frontais voltados para a Internet<br /> </td> 
   <td> O armazém de dados está isolado de componentes frontais voltados para a Internet<br /> </td> 
  </tr> 
  <tr> 
   <td> Modelo de implantação<br /> </td> 
   <td> Tudo em um site (pode ser no local ou na nuvem)<br /> </td> 
   <td> Marketing no local com execução na nuvem possível<br /> </td> 
   <td> Marketing local com execução na nuvem; execução em diferentes regiões possíveis<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Recomendações {#recommendations}

* Uma instância de execução deve ser dedicada a um serviço. Não é possível instalar um pacote para um serviço que você não assinou. Por exemplo, se você assinar o **Power Booster** opção para a variável **Centro de mensagens** serviço, você só pode instalar o **[!UICONTROL Execution of transactional messages]** na instância de execução dedicada. Verifique o contrato de licença.
* Como as instâncias dedicadas (ou clusters) são instâncias do Adobe Campaign, as recomendações são as mesmas de uma instância principal. Para obter mais informações, consulte [este documento](../../production/using/foreword.md).
* Para configurar corretamente a instância do ponto de vista de um banco de dados/componentes de hardware, entre em contato com os Adobe Campaign Professional Services.
