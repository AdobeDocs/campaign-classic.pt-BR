---
title: Regras de controle
seo-title: Regras de controle
description: Regras de controle
seo-description: null
page-status-flag: never-activated
uuid: a83e56d0-573a-4592-b2b1-0d3b3e52b03f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: be037a80-3f94-465c-ba7d-ae7d50f70e36
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Regras de controle{#control-rules}

## Regras de controle de análise e arbitragem {#analysis-and-arbitration-control-rules}

Regras de controle permitem que você garanta a validade e a qualidade das mensagens antes do delivery: exibição de caracteres, tamanho do SMS, formato de endereço etc.

Um conjunto de regras prontas permite que você faça as verificações normais. Essas verificações (mostradas em negrito na interface) são:

* **[!UICONTROL Object approval]** (email): verifica se o objeto e o endereço do remetente não contêm caracteres especiais que podem causar problemas em determinados agentes de email.
* **[!UICONTROL URL label approval]** (email): verifica se cada URL de rastreamento tem um rótulo.
* **[!UICONTROL URL approval]** (email): verifica os URLs de rastreamento (presença do caractere &quot;&amp;&quot;).
* **[!UICONTROL Message size approval]** (móvel): verifica o tamanho das mensagens SMS.
* **[!UICONTROL Validity period check]** (email): verifica se o período de validade da entrega é longo o suficiente para enviar todas as mensagens.
* **[!UICONTROL Proof size check]** (todos os canais): gera uma mensagem de erro se o público-alvo da prova exceder 100 destinatários.
* **[!UICONTROL Wave scheduling check]** (email): verifica se a última vaga de entregas está programada para começar antes do final do período de validade, se a entrega for dividida em várias ondas.
* **[!UICONTROL Unsubscription link approval]** (email): verifica se há pelo menos um URL de cancelamento de assinatura (opção de não participação) em cada conteúdo (HTML e Texto).

## Criando uma regra de controle {#creating-a-control-rule}

É possível criar novas regras de controle para atender às suas necessidades. To do this, create a **[!UICONTROL Control]** typology rule and enter the control formula in SQL in the **[!UICONTROL Code]** tab.

**Exemplo:**

No exemplo a seguir, vamos criar uma regra para impedir que uma oferta em SMS seja enviada para mais de 100 recipients. Essa regra será vinculada a uma tipologia de campanha, em seguida aos deliveries de SMS para os quais a oferta relacionada estiver disponível.

Siga as etapas abaixo:

1. Crie uma regra de **[!UICONTROL Control]** tipologia. Selecione um nível de **[!UICONTROL Warning]** alerta.

   ![](assets/campaign_opt_create_control_01.png)

1. In the **[!UICONTROL Code]** tab, enter the script to apply the desired threshold, as shown below:

   ![](assets/campaign_opt_create_control_02.png)

   Este script acionará um aviso se o target do delivery exceder 100 contatos:

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. Vincule esta regra a uma tipologia de campanha e faça referência à tipologia no delivery do SMS em questão.

   ![](assets/campaign_opt_create_control_03.png)

1. Durante a análise do delivery, a regra é aplicada e um aviso é criado se aplicável.

   ![](assets/campaign_opt_create_control_04.png)

   No entanto, o delivery ainda estará pronto para ser enviado.

   Se você aumentar o nível de alerta, isso impedirá que o delivery seja iniciado.

   ![](assets/campaign_opt_create_control_05.png)

   At the end of the analysis, the **[!UICONTROL Confirm delivery]** button will not be available.

   ![](assets/campaign_opt_create_control_06.png)

