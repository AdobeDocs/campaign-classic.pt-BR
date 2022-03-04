---
product: campaign
title: Regras de controle
description: Regras de controle
feature: Typology Rules
exl-id: 5a5f26f6-38da-4488-aadb-81fcb5359331
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 100%

---

# Regras de controle{#control-rules}

![](../../assets/common.svg)

## Regras de controle de análise e arbitragem {#analysis-and-arbitration-control-rules}

Regras de controle permitem que você garanta a validade e a qualidade das mensagens antes do delivery: exibição de caracteres, tamanho do SMS, formato de endereço etc.

Um conjunto de regras prontas permite que você faça as verificações normais. Essas verificações (mostradas em negrito na interface) são:

* **[!UICONTROL Object approval]** (email): verifica se o objeto e o endereço do remetente não contêm caracteres especiais que podem causar problemas em determinados agentes de email.
* **[!UICONTROL URL label approval]** (email): verifica se cada URL de rastreamento tem um rótulo.
* **[!UICONTROL URL approval]** (email): verifica as URLs de rastreamento (presença do caractere &quot;&amp;&quot;).
* **[!UICONTROL Message size approval]** (dispositivos móveis): verifica o tamanho das mensagens SMS.
* **[!UICONTROL Validity period check]** (email): verifica se o período de validade da entrega é longo o suficiente para enviar todas as mensagens.
* **[!UICONTROL Proof size check]** (todos os canais): gera uma mensagem de erro se a população do target de prova exceder 100 destinatários.
* **[!UICONTROL Wave scheduling check]** (email): verifica se a última onda de deliveries está agendada para iniciar antes do fim do período de validade, caso o delivery esteja distribuído em várias ondas.
* **[!UICONTROL Unsubscription link approval]** (email): verifica a presença de pelo menos um URL de cancelamento de subscrição (opt-out) em cada conteúdo (HTML e Text).

## Criação de uma regra de controle {#creating-a-control-rule}

É possível criar novas regras de controle para atender às suas necessidades. Para fazer isso, crie uma regra de tipologia **[!UICONTROL Control]** e insira a fórmula de controle em SQL na guia **[!UICONTROL Code]**.

**Exemplo:**

No exemplo a seguir, vamos criar uma regra para impedir que uma oferta em SMS seja enviada para mais de 100 recipients. Essa regra será vinculada a uma tipologia de campanha, em seguida aos deliveries de SMS para os quais a oferta relacionada estiver disponível.

Siga as etapas abaixo:

1. Crie uma regra de tipologia **[!UICONTROL Control]**. Selecione um nível de alerta **[!UICONTROL Warning]**.

   ![](assets/campaign_opt_create_control_01.png)

1. Na guia **[!UICONTROL Code]**, insira o script para aplicar o limite desejado, conforme mostrado abaixo:

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

   No final da análise, o botão **[!UICONTROL Confirm delivery]** não estará disponível.

   ![](assets/campaign_opt_create_control_06.png)
