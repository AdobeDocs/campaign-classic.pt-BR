---
product: campaign
title: Campaign - Conector CRM do Salesforce
description: Saiba como conectar o Campaign e o Salesforce
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
hide: true
TQID: https://experienceleague.adobe.com/LeUJ-F5dAECUrtkbvgwL0BN88Alofnh2rBWe7hIVGgI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
  - id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 323
ht-degree: 95%

---

# Conecte o Campaign e o Salesforce.com{#connect-to-sfdc}



Nesta página, você aprenderá a conectar o Campaign Classic ao **Salesforce**.

A sincronização de dados é realizada por meio de uma atividade de fluxo de trabalho dedicada. [Saiba mais](../../platform/using/crm-data-sync.md).


A conta externa do permite importar e exportar dados do Salesforce para o Adobe Campaign.
Para configurar o Conector CRM do Salesforce, siga as etapas abaixo:

1. Crie uma nova conta externa por meio do nó **[!UICONTROL Administration > Platform > External accounts]** da árvore do Adobe Campaign.
1. Selecione **[!UICONTROL Salesforce.com]**.
1. Digite as configurações para habilitar a conexão.

   ![](assets/ext_account_17.png)

   Para configurar a conta externa do Salesforce CRM para funcionar com o Adobe Campaign, você precisa fornecer os seguintes detalhes:

   * **[!UICONTROL Account]**
Conta usada para fazer logon no Salesforce CRM.

   * **[!UICONTROL Password]**
Senha usada para fazer logon no Salesforce CRM.

   * **[!UICONTROL Client identifier]**
Para saber onde encontrar o identificador do cliente, consulte esta [página](https://help.salesforce.com/articleView?id=000205876&type=1).

   * **[!UICONTROL Security token]**
Para saber onde encontrar o token de segurança, consulte esta [página](https://help.salesforce.com/articleView?id=000205876&type=1).

   * **[!UICONTROL API version]**
Selecione a versão da API.
1. Execute o assistente de configuração para gerar a tabela CRM disponível: o assistente de configuração permite que você colete tabelas e crie o esquema correspondente.

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Para aprovar a configuração, você precisa fazer logoff e voltar ao console do Adobe Campaign.

1. Verifique o esquema gerado no Adobe Campaign no nó **[!UICONTROL Administration > Configuration > Data schemas]**.

   Exemplo do esquema do **Salesforce**:

   ![](assets/crm_connectors_sfdc_table.png)

1. Após a criação do esquema, você pode sincronizar enumerações automaticamente do Salesforce para o Adobe Campaign.

   Para fazer isso, clique no link **[!UICONTROL Synchronizing enumerations...]** e selecione a lista discriminada do Adobe Campaign que corresponde à enumeração do Salesforce.



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >É possível substituir todos os valores de uma enumeração do Adobe Campaign pelos valores do CRM: para fazer isso, selecione **[!UICONTROL Yes]** na coluna **[!UICONTROL Replace]**.


   Clique em **[!UICONTROL Next]** e depois em **[!UICONTROL Start]** para começar a importar a lista.

1. Verifique os valores importados no menu **[!UICONTROL Administration > Platform > Enumerations]**.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Não há suporte para a seleção de várias enumerações.

O Campaign e o Salesforce.com agora estão conectados. Você pode configurar a sincronização de dados entre os dois sistemas.

Para sincronizar dados entre o Adobe Campaign e o SFDC, é necessário criar um fluxo de trabalho e usar a atividade **[!UICONTROL CRM connector]**.

![](assets/crm_connectors_sfdc_wf.png)

Saiba mais sobre a sincronização de dados [nesta página](../../platform/using/crm-data-sync.md).
