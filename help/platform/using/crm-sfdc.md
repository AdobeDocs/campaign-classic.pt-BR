---
product: campaign
title: Campaign - Conector CRM do Salesforce
description: Saiba como conectar o Campaign e o Salesforce
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
source-git-commit: fdb840a9e6349f074378899e07f794b62fb5b054
workflow-type: ht
source-wordcount: '329'
ht-degree: 100%

---

# Conecte o Campaign e o Salesforce.com{#connect-to-sfdc}

![](../../assets/v7-only.svg)

Nesta página, você aprenderá a conectar o Campaign Classic ao **Salesforce**.

A sincronização de dados é realizada por meio de uma atividade de fluxo de trabalho dedicada. [Saiba mais](../../platform/using/crm-data-sync.md).


A conta externa permite importar e exportar dados do Salesforce para o Adobe Campaign.
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
Para saber onde encontrar o identificador do cliente, consulte esta [página](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL Security token]**
Para saber onde encontrar o token de segurança, consulte esta [página](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL API version]**
Selecione a versão da API.
1. Execute o assistente de configuração para gerar a tabela CRM disponível: o assistente de configuração permite coletar tabelas e criar o esquema correspondente.

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Para aprovar a configuração, você precisa fazer logoff e voltar ao console do Adobe Campaign.

1. Verifique o schema gerado no Adobe Campaign no nó **[!UICONTROL Administration > Configuration > Data schemas]**.

   Exemplo do esquema do **Salesforce**:

   ![](assets/crm_connectors_sfdc_table.png)

1. Após a criação do esquema, você pode sincronizar enumerações automaticamente do Salesforce para o Adobe Campaign.

   Para fazer isso, clique no link **[!UICONTROL Synchronizing enumerations...]** e selecione a lista discriminada do Adobe Campaign que corresponde à lista discriminada do Salesforce.



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >É possível substituir todos os valores de uma lista discriminada do Adobe Campaign pelos valores do CRM: para fazer isso, selecione **[!UICONTROL Yes]** na coluna **[!UICONTROL Replace]**.


   Clique em **[!UICONTROL Next]** e depois em **[!UICONTROL Start]** para começar a importar a lista.

1. Verifique os valores importados no menu **[!UICONTROL Administration > Platform > Enumerations]**.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Não há suporte para a seleção de várias listas discriminadas.

O Campaign e o Salesforce.com agora estão conectados. Você pode configurar a sincronização de dados entre os dois sistemas.

Para sincronizar dados entre o Adobe Campaign e o SFDC, é necessário criar um fluxo de trabalho e usar a atividade **[!UICONTROL CRM connector]**.

![](assets/crm_connectors_sfdc_wf.png)

Saiba mais sobre a sincronização de dados [nesta página](../../platform/using/crm-data-sync.md).
