---
solution: Campaign Classic
product: campaign
title: Conectores CRM
description: Introdução aos Conectores CRM no Campaign
audience: platform
content-type: reference
topic-tags: connectors
translation-type: ht
source-git-commit: 2838ced5f5d562914c0791e6a0b8f02dd61006b4
workflow-type: ht
source-wordcount: '356'
ht-degree: 100%

---


# Conectores CRM{#crm-connectors}

## Introdução aos conectores CRM {#about-crm-connectors}

O Adobe Campaign fornece vários conectores de CRM para vincular sua plataforma a sistemas de terceiros. Esses conectores de CRM permitem sincronizar contatos, contas, compras, etc. Eles facilitam a integração de seu aplicativo com vários aplicativos de terceiros e corporativos.

Esses conectores permitem uma integração de dados rápida e fácil: o Adobe Campaign fornece um assistente dedicado para coletar e selecionar entre as tabelas disponíveis no CRM. Isso garante a sincronização bidirecional para assegurar que os dados estejam sempre atualizados em todos os sistemas.

>[!NOTE]
>
>Esse recurso está disponível no Adobe Campaign através dos **conectores dedicados do CRM**.


### Sistemas compatíveis {#compatible-crm-systems-and-limitations}

O CRM e as versões compatíveis estão detalhados na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md) do Campaign.

>[!NOTE]
>
>Os conectores CRM funcionam somente com uma URL segura (https).

### Etapas de implementação {#crm-implementation-steps}

Saiba mais sobre o procedimento passo a passo para conectar o Campaign e o Microsoft Dynamics [nesta seção](../../platform/using/crm-ms-dynamics.md)

Em geral, para usar conectores CRM no Adobe Campaign, siga estas etapas:

1. Crie uma nova conta externa através do nó **[!UICONTROL Administration > Platform > External accounts]** da árvore do Adobe Campaign.
1. Selecione o sistema CRM ao qual você precisa conectar o Campaign.
1. Digite as configurações para habilitar a conexão.
1. Execute o assistente de configuração para gerar a tabela CRM disponível: o assistente de configuração permite que você colete tabelas e crie o esquema correspondente.

   Exemplo do assistente de configuração do **Salesforce**:

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Para aprovar a configuração, você precisa fazer logoff e voltar ao console do Adobe Campaign.

1. Verifique o schema gerado no Adobe Campaign no nó **[!UICONTROL Administration > Configuration > Data schemas]**.

   Exemplo do esquema do **Salesforce**:

   ![](assets/crm_connectors_sfdc_table.png)

1. Após a criação do schema, você pode sincronizar enumerações automaticamente usando o CRM para o Adobe Campaign.

   Para fazer isso, clique no link **[!UICONTROL Synchronizing enumerations...]** e selecione a lista discriminada do Adobe Campaign que corresponde à lista discriminada do CRM.

   >[!NOTE]
   >
   >É possível substituir todos os valores de uma lista discriminada do Adobe Campaign pelos valores do CRM: para fazer isso, selecione **[!UICONTROL Yes]** na coluna **[!UICONTROL Replace]**.

   Exemplo das listas discriminadas do **Salesforce**:

   ![](assets/crm_connectors_sfdc_enum.png)

   Clique em **[!UICONTROL Next]** e depois em **[!UICONTROL Start]** para começar a importar a lista.

1. Verifique os valores importados no menu **[!UICONTROL Administration > Platform > Enumerations]**.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Não há suporte para várias listas discriminadas de seleção no Salesforce.

1. Para sincronizar dados entre os dados da Adobe Campaign e o sistema CRM, é necessário criar um fluxo de trabalho e usar a atividade **[!UICONTROL CRM connector]**.

   ![](assets/crm_connectors_sfdc_wf.png)

   Saiba mais sobre a sincronização de dados [nesta página](../../platform/using/crm-data-sync.md).
