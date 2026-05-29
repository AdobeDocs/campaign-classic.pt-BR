---
product: campaign
title: Carregamento (SOAP)
description: Carregamento (SOAP)
feature: Workflows
hide: true
exl-id: 20414e73-2ba9-44f9-8e16-cb6604933ee0
TQID: https://experienceleague.adobe.com/8G5YOa4HCsSoB9veHyexQ9uFvVDTYCj4W2Cv-nsmguw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 251
ht-degree: 100%

---

# Carregamento (SOAP){#loading-soap}



>[!CAUTION]
>
>A atividade de **Carregamento (SOAP)** só estará disponível se você tiver o módulo **FDA (Federated Data Access)** instalado. Verifique o contrato de licença.

A atividade de **Carregamento (SOAP)** é usada além da atividade de **carregamento de dados (RDBMS)** quando não é possível coletar dados diretamente pelo FDA em um banco de dados externo.

A operação é como descrita a seguir:

1. Escolha usar um exemplo XML ou WSDL.

   O exemplo a seguir é de um fluxo de trabalho técnico do módulo do Centro de Mensagens.

   ![](assets/load_soap_002.png)

1. Para um exemplo XML, selecione um arquivo de exemplo. O arquivo é analisado para estabelecer um exemplo de resultado.

   Para um WSDL, insira a URL de acesso correspondente, e então gere o código estrutural. O serviço e a chamada selecionados são atualizados e exibidos automaticamente.

   ![](assets/soap_load_003.png)

1. Selecione **[!UICONTROL Click here to view and edit analysis results]** para especificar cada coluna identificada.

   ![](assets/soap_load_001.png)

   Se desejar atualizar o exemplo, selecione **[!UICONTROL Re-analyze the example]**.

   Você também pode personalizar o formato dos dados da coluna por meio do link **[!UICONTROL Advanced parameters]**. Para obter mais informações sobre a formatação de dados importados, consulte esta [seção](../../platform/using/executing-import-jobs.md).

1. Você pode usar o número de linha como um identificador e/ou especificar que a chamada SOAP retorna vários elementos.
1. Insira os seguintes scripts de guia de acordo com sua função:

   * **[!UICONTROL Initialization]**: estabelece uma conexão SOAP.
   * **[!UICONTROL Iteration]**: executa a chamada para o serviço SOAP. O retorno dessa função deve ser um objeto XML compatível com a descrição do exemplo ou do WSDL.

     O código dessa guia será chamado em um loop pelo Adobe Campaign até que um objeto XML nulo seja retornado.

   * **[!UICONTROL Finalization]**: fecha a conexão e/ou libera outros recursos criados durante o processamento.
