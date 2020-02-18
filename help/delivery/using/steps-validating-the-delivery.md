---
title: Validando o dleivery
seo-title: Validando o dleivery
description: Validando o dleivery
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# Validando o dleivery {#validating-the-delivery}

Quando um delivery for criado e configurado, você deverá validá-lo antes de enviá-lo para o target principal.

Para fazer isso:

1. **Analise a entrega**: essa etapa permite que você prepare as mensagens a serem entregues. Consulte [Análise da entrega](#analyzing-the-delivery).

   Os modos de validação disponíveis estão detalhados em [Alterar o modo](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode)de aprovação.

1. **Enviar provas**: essa etapa permite que você aprove conteúdo, URLs, campos de personalização etc. Consulte [Envio de uma prova](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) e [Definição de uma meta](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)de prova específica.

>[!CAUTION]
>
>Essas duas etapas devem ser executadas necessariamente após cada modificação no conteúdo da mensagem.

## Análise do delivery {#analyzing-the-delivery}

A análise é a fase na qual a população do target é calculada e o conteúdo de delivery é preparado. Quando estiver concluído, a entrega estará pronta para ser enviada. Para iniciar a análise de entrega, clique em **[!UICONTROL Send]** e selecione **[!UICONTROL Deliver as soon as possible]**.

![](assets/s_ncs_user_email_del_send.png)

The **[!UICONTROL Analyze]** button lets you launch the analysis manually. A barra de progresso mostra o progresso da análise. A seção inferior da janela exibe o resultado da análise. Ícones especiais exibem avisos.

![](assets/s_ncs_user_interface_delivery04b.png)

>[!NOTE]
>
>As regras de validação são descritas no processo [de validação com tipologias](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

You can stop this job at any time by clicking **[!UICONTROL Stop]**.

![](assets/s_ncs_user_wizard_email01_16.png)

Nenhuma mensagem será enviada durante a fase de análise. Portanto, você poderá iniciar ou cancelar esse trabalho sem riscos.

>[!CAUTION]
>
>A análise congela o delivery (ou a prova) no momento da análise. Qualquer modificação no delivery (ou na prova) deverá ser seguida de outra análise antes de se tornar aplicável.

A última mensagem de log exibe mensagens de erro e o número de erros. Um ícone especial mostra o tipo de erro: o ícone amarelo indica um erro de processamento não crítico, o ícone vermelho indica um erro crítico que impede o início do delivery.

![](assets/s_ncs_user_email_del_analyze_error.png)

Clique em **[!UICONTROL Close]** para corrigir os erros. Após fazer as alterações, você deverá reiniciar a análise.

Check the result of the analysis before clicking **[!UICONTROL Confirm delivery]** to send the message to the specified target. Uma mensagem de confirmação permite iniciar o delivery.

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>Click the **[!UICONTROL Change the main delivery target]** link if the number of messages to send does not match your configuration. Isso permite que você altere a definição da população do target e reinicie a análise.

The delivery parameters **[!UICONTROL Analysis]** tab lets you define a set of information concerning the preparation of messages during the analysis phase.

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

Essa guia fornece acesso às seguintes opções:

* **[!UICONTROL Label and code of the delivery]** : as opções referentes a esta seção do ecrã são utilizadas para calcular os valores destes campos durante a fase de análise de entrega. The **[!UICONTROL Calculate the execution folder during the delivery analysis]** field computes the name of the folder that will contain this delivery action during the analysis phase.
* **[!UICONTROL Approval mode]** : esse campo permite selecionar o tipo de aprovação de entrega. Os modos de aprovação são apresentados no processo de [validação com tipologias](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).
* **[!UICONTROL Prepare the personalization data with a workflow]** : essa opção permite preparar os dados de personalização contidos na entrega em um fluxo de trabalho automático. Ele permite melhorar o desempenho da análise de delivery quando muitos dados estão sendo processados, especialmente se os dados de personalização vêm de uma tabela externa por meio da FDA. Consulte a seção [Acessando um banco de dados externo (FDA)](../../platform/using/additional-options.md#optimizing-email-personalization-with-external-data).
* **[!UICONTROL Start job in a detached process]** : Essa opção permite iniciar a análise de delivery em um processo separado. A função de análise usa o processo do servidor de aplicativos Adobe Campaign (Web nlserver) por padrão. Ao selecionar essa opção, você garante que a análise será concluída mesmo no caso de falha do servidor de aplicativos.
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** : essa opção adiciona os logs de consulta SQL ao diário de entrega durante a fase de análise.
* **[!UICONTROL Ignore personalization scripts during sending]** : essa opção permite que você ignore a interpretação das diretivas JavaScript encontradas no conteúdo HTML. Eles serão exibidos como nos conteúdos entregues. These directives are introduced with the **&lt;%=** tag).

### Configurar a prioridade da análise {#analysis-priority-}

When the delivery is part of a campaign, the **[!UICONTROL Advanced]** tab offers an additional option. Isso permite organizar a ordem de processamento dos deliveries na mesma campanha.

Antes de enviar, cada delivery é analisado. A duração da análise depende do arquivo de extração de delivery. Quanto mais significativo for o tamanho do arquivo, mais tempo levará a análise, fazendo com que os deliveries aguardem.

The options for the **[!UICONTROL Message preparation by the scheduler]** let you prioritize the delivery analysis in a campaign workflow.

![](assets/delivery_analysis_priority.png)

Se um delivery for muito grande, é melhor atribuir uma prioridade baixa a ele para evitar o atraso na análise de outros deliveries do workflow.

>[!NOTE]
>
>To ensure that the larger delivery analyses do not slow down the progress of your workflows, you can schedule their executions by ticking the **[!UICONTROL Schedule execution for a time of low activity]**.

## Envio de uma prova {#sending-a-proof}

Para detectar possíveis erros na configuração da mensagem, a Adobe recomenda configurar um ciclo de validação de entrega. Verifique se o conteúdo é aprovado com a frequência necessária enviando provas para testar os destinatários. Uma prova deve ser enviada toda vez que uma alteração for feita, para aprovar o conteúdo.

>[!NOTE]
>
>* Os modos de validação disponíveis estão detalhados em [Alterar o modo](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode)de aprovação.
>* A configuração da meta de prova é explicada em [Definição de uma meta](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)de prova específica.
>



Para enviar uma prova, siga as etapas abaixo:

1. Verifique se o destino da prova foi configurado conforme descrito em [Definição de um destino](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)de prova específico.
1. Click **[!UICONTROL Send a proof]** on the top bar of the delivery wizard.

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. Iniciar análise de mensagem. Consulte [Análise da entrega](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).
1. Agora você pode enviar a entrega (consulte [Envio da entrega](../../delivery/using/steps-sending-the-delivery.md)).

   Quando a entrega for enviada, a prova será exibida na lista de entrega e será automaticamente criada e numerada. Ela poderá ser editada se você quiser acessar seu conteúdo e propriedades. Para obter mais informações, consulte esta [página](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >Se vários formatos forem criados para o delivery (HTML e Texto), você poderá escolher o formato das mensagens a serem enviadas aos recipients da prova na seção inferior da janela.

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

Talvez você queira modificar o conteúdo do delivery como resultado de qualquer comentário feito pelo grupo de validação que recebe a prova. Depois de fazer suas alterações, você deverá reiniciar a análise e enviar outra prova. Cada nova prova é numerada e registrada no journal de delivery.

Once the delivery has been analyzed, you can view the various proofs sent via the **[!UICONTROL Proofs]** sub-tab of the log (**[!UICONTROL Audit]** tab).

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

Você deverá enviar quantas provas forem necessárias até que o conteúdo do delivery esteja finalizado. Depois disso, você poderá enviar o delivery para o target principal e fechar o ciclo de validação.

The **[!UICONTROL Advanced]** tab of delivery properties lets you define the properties of the proof. Quando necessário, você poderá substituir as regras de exclusão de recipient.

![](assets/s_ncs_user_wizard_email01_145.png)

As seguintes opções estão disponíveis:

* A primeira opção permite que você mantenha as duplicatas da prova.
* As opções a seguir permitem que você mantenha os recipients e endereços incluídos na blacklist em quarentena. See the description of these options for the main target in [Customizing exclusion settings](../../delivery/using/steps-defining-the-target-population.md#customizing-exclusion-settings). Diferentemente do target de um delivery, onde esses endereços são excluídos por padrão, eles serão mantidos por padrão para o target de uma prova.
* The **[!UICONTROL Keep the delivery code for the proof]** option lets you give the proof the same delivery code as the one defined for the delivery to which it relates. Este código é especificado na primeira etapa do assistente de delivery.
* Por padrão, o assunto da prova tem o prefixo &#39;Proof #&#39;, onde # é o número da prova. You can change this prefix in the **[!UICONTROL Label prefix]** field.

## Processo de validação com tipologias {#validation-process-with-typologies}

Antes de enviar qualquer mensagem, você deverá analisar a campanha para aprovar seu conteúdo e configuração. As regras de verificação aplicadas durante a fase de análise são definidas em uma **tipologia**. Por padrão, para emails, a análise cobre os seguintes pontos:

* Aprovando o objeto
* Aprovando as URLs e imagens
* Aprovação dos rótulos do URL
* Aprovando o link de cancelamento de subscrição
* Verificando o tamanho das provas
* Verificando o período de validade
* Verificando a programação de ondas

The typology to be applied for each delivery is selected in the **[!UICONTROL Typologies]** tab in the delivery parameters.

You can view and edit the approval rules, their content, their order of execution, and their full description via the **[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]** node.

Você poderá criar novas regras e definir novas tipologias a partir desse nó. No entanto, essas tarefas são reservadas para usuários expert que conhecem JavaScript.

Para editar a tipologia atual, clique no **[!UICONTROL Edit link]** ícone à direita do **[!UICONTROL Typology]** campo.

![](assets/s_ncs_user_email_del_typo_tab.png)

The **[!UICONTROL Rule]** tab gives a list of the typology rules to apply. Select a rule and click the **[!UICONTROL Detail...]** icon to view its configuration:

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** as tipologias de tipo são usadas na estrutura de gerenciamento de pressão de vendas. Para obter mais informações, consulte [esta seção](../../campaign/using/about-marketing-resource-management.md).

## Alterando o modo de aprovação {#changing-the-approval-mode}

The **[!UICONTROL Analysis]** tab for delivery properties lets you select the validation mode. Se os avisos forem gerados durante a análise (ex.: se certos caracteres estiverem acentuados no assunto da entrega etc.), você poderá configurar o delivery para definir se ele ainda deverá ou não ser executado. Por padrão, o usuário deverá confirmar o envio de mensagens no final da fase de análise: essa é a validação **manual**.

Selecione outro modo de aprovação na lista suspensa no campo apropriado.

![](assets/s_ncs_user_email_del_validation_mode.png)

Os seguintes modos de aprovação estão disponíveis:

* **[!UICONTROL Manual]**: No final da fase de análise, o usuário deverá confirmar o delivery para começar a enviar. To do this, click the **[!UICONTROL Start]** button to launch the delivery.
* **[!UICONTROL Semi-automatic]**: O envio começa automaticamente se a fase de análise não gerar mensagens de advertência.
* **[!UICONTROL Automatic]**: O envio começa automaticamente no final da fase de análise, independentemente do resultado.
