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
translation-type: ht
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# Validando o dleivery {#validating-the-delivery}

Quando um delivery for criado e configurado, você deverá validá-lo antes de enviá-lo para o target principal.

Para fazer isso:

1. **Analyze the delivery**: esta etapa permite preparar as mensagens para entregar. Consulte [Análise do delivery](#analyzing-the-delivery).

   Os modos de validação disponíveis estão detalhados em [Alterar o modo de aprovação](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode).

1. **Send proofs**: esta etapa permite aprovar conteúdo, URLs, campos de personalização, etc. Consulte [Envio de uma prova](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) e [Definição de um target de prova](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target).

>[!CAUTION]
>
>Essas duas etapas devem ser executadas necessariamente após cada modificação no conteúdo da mensagem.

## Análise do delivery {#analyzing-the-delivery}

A análise é a fase na qual a população do target é calculada e o conteúdo de delivery é preparado. Uma vez concluído, o delivery estará pronto para ser enviado. Para iniciar a análise de delivery, clique em **[!UICONTROL Send]** e selecione **[!UICONTROL Deliver as soon as possible]**.

![](assets/s_ncs_user_email_del_send.png)

O botão **[!UICONTROL Analyze]** permite iniciar a análise manualmente. A barra de progresso mostra o progresso da análise. A seção inferior da janela exibe o resultado da análise. Ícones especiais exibem avisos.

![](assets/s_ncs_user_interface_delivery04b.png)

>[!NOTE]
>
>As regras de validação são descritas em [Processo de validação com tipologias](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

Você pode interromper esse trabalho a qualquer momento clicando em **[!UICONTROL Stop]**.

![](assets/s_ncs_user_wizard_email01_16.png)

Nenhuma mensagem será enviada durante a fase de análise. Portanto, você poderá iniciar ou cancelar esse trabalho sem riscos.

>[!CAUTION]
>
>A análise congela o delivery (ou a prova) no momento da análise. Qualquer modificação no delivery (ou na prova) deverá ser seguida de outra análise antes de se tornar aplicável.

A última mensagem de log exibe mensagens de erro e o número de erros. Um ícone especial mostra o tipo de erro: o ícone amarelo indica um erro de processamento não crítico, o ícone vermelho indica um erro crítico que impede o início do delivery.

![](assets/s_ncs_user_email_del_analyze_error.png)

Clique em **[!UICONTROL Close]** para corrigir os erros. Após fazer as alterações, você deverá reiniciar a análise.

Verifique o resultado da análise antes de clicar em **[!UICONTROL Confirm delivery]** para enviar a mensagem para o target especificado. Uma mensagem de confirmação permite iniciar o delivery.

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>Clique no link **[!UICONTROL Change the main delivery target]** se o número de mensagens para enviar não corresponder à sua configuração. Isso permite que você altere a definição da população do target e reinicie a análise.

A guia **[!UICONTROL Analysis]** de parâmetros de delivery permite definir um conjunto de informações relacionadas à preparação das mensagens durante a fase de análise.

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

Essa guia fornece acesso às seguintes opções:

* **[!UICONTROL Label and code of the delivery]**: as opções referentes a esta seção da tela são usadas para calcular os valores desses campos durante a fase de análise de delivery. O campo **[!UICONTROL Calculate the execution folder during the delivery analysis]** calcula o nome da pasta que conterá essa ação de delivery durante a fase de análise.
* **[!UICONTROL Approval mode]**: este campo permite selecionar o tipo de aprovação de delivery. Os modos de aprovação são apresentados em [Processo de validação com tipologias](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).
* **[!UICONTROL Prepare the personalization data with a workflow]**: essa opção permite preparar os dados de personalização contidos no delivery em um workflow automático. Ele permite melhorar o desempenho da análise de delivery quando muitos dados estão sendo processados, especialmente se os dados de personalização vêm de uma tabela externa por meio da FDA. Consulte a seção [Acessando um banco de dados externo (FDA)](../../platform/using/additional-options.md#optimizing-email-personalization-with-external-data).
* **[!UICONTROL Start job in a detached process]** : essa opção permite iniciar a análise de delivery em um processo separado. A função de análise usa o processo do servidor de aplicativos Adobe Campaign (Web nlserver) por padrão. Ao selecionar essa opção, você garante que a análise será concluída mesmo no caso de falha do servidor de aplicativos.
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]**: essa opção adiciona os logs de consulta SQL ao journal de delivery durante a fase de análise.
* **[!UICONTROL Ignore personalization scripts during sending]**: essa opção permite ignorar a interpretação das diretivas JavaScript encontradas no conteúdo HTML. Eles serão exibidos como nos conteúdos entregues. Essas diretivas são introduzidas com a tag **&lt;%=**.

### Configurar a prioridade da análise {#analysis-priority-}

Quando o delivery é parte de uma campanha, a guia **[!UICONTROL Advanced]** oferece uma opção adicional. Isso permite organizar a ordem de processamento dos deliveries na mesma campanha.

Antes de enviar, cada delivery é analisado. A duração da análise depende do arquivo de extração de delivery. Quanto mais significativo for o tamanho do arquivo, mais tempo levará a análise, fazendo com que os deliveries aguardem.

As opções para **[!UICONTROL Message preparation by the scheduler]** permitem priorizar a análise de delivery em um workflow da campanha.

![](assets/delivery_analysis_priority.png)

Se um delivery for muito grande, é melhor atribuir uma prioridade baixa a ele para evitar o atraso na análise de outros deliveries do workflow.

>[!NOTE]
>
>Para garantir que as análises de delivery maiores não retardem o progresso dos workflows, você poderá agendar suas execuções marcando **[!UICONTROL Schedule execution for a time of low activity]**.

## Envio de uma prova {#sending-a-proof}

Para detectar possíveis erros na configuração da mensagem, a Adobe recomenda configurar um ciclo de validação de entrega. Verifique se o conteúdo é aprovado com a frequência necessária enviando provas para testar os destinatários. Uma prova deve ser enviada toda vez que uma alteração for feita, para aprovar o conteúdo.

>[!NOTE]
>
>* Os modos de validação disponíveis estão detalhados em [Alterar o modo de aprovação](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode).
>* A configuração do target de prova é explicada em [Definição de um target de prova específico](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target).
>



Para enviar uma prova, siga as etapas abaixo:

1. Verifique se o target de prova foi configurado conforme descrito em [Definição de um target de prova específico](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target).
1. Clique em **[!UICONTROL Send a proof]** na barra superior do assistente do delivery.

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. Iniciar análise de mensagem. Consulte [Análise de delivery](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).
1. Agora você pode enviar o delivery (consulte [Envio do delivery](../../delivery/using/steps-sending-the-delivery.md)).

   Quando o delivery for enviado, a prova será exibida na lista de delivery e será automaticamente criada e numerada. Ela poderá ser editada se você quiser acessar seu conteúdo e propriedades. Para obter mais informações, consulte esta [página](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >Se vários formatos forem criados para o delivery (HTML e Texto), você poderá escolher o formato das mensagens a serem enviadas aos recipients da prova na seção inferior da janela.

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

Talvez você queira modificar o conteúdo do delivery como resultado de qualquer comentário feito pelo grupo de validação que recebe a prova. Depois de fazer suas alterações, você deverá reiniciar a análise e enviar outra prova. Cada nova prova é numerada e registrada no journal de delivery.

Depois que o delivery for analisado, você poderá ver as várias provas enviadas por meio da subguia **[!UICONTROL Proofs]** do log (guia **[!UICONTROL Audit]**).

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

Você deverá enviar quantas provas forem necessárias até que o conteúdo do delivery esteja finalizado. Depois disso, você poderá enviar o delivery para o target principal e fechar o ciclo de validação.

A guia **[!UICONTROL Advanced]** das propriedades de delivery permite definir as propriedades da prova. Quando necessário, você poderá substituir as regras de exclusão de recipient.

![](assets/s_ncs_user_wizard_email01_145.png)

As seguintes opções estão disponíveis:

* A primeira opção permite que você mantenha as duplicatas da prova.
* As opções a seguir permitem que você mantenha os recipients e endereços incluídos na blacklist em quarentena. Consulte a descrição dessas opções para o target principal em [Personalizar configurações de exclusão](../../delivery/using/steps-defining-the-target-population.md#customizing-exclusion-settings). Diferentemente do target de um delivery, onde esses endereços são excluídos por padrão, eles serão mantidos por padrão para o target de uma prova.
* A opção **[!UICONTROL Keep the delivery code for the proof]** permite que você forneça o mesmo código de delivery que o definido para o delivery com o qual ele está relacionado. Este código é especificado na primeira etapa do assistente de delivery.
* Por padrão, o assunto da prova tem o prefixo &#39;Proof #&#39;, onde # é o número da prova. É possível alterar esse prefixo no campo **[!UICONTROL Label prefix]**.

## Processo de validação com tipologias {#validation-process-with-typologies}

Antes de enviar qualquer mensagem, você deverá analisar a campanha para aprovar seu conteúdo e configuração. As regras de verificação aplicadas durante a fase de análise são definidas em uma **tipologia**. Por padrão, para emails, a análise cobre os seguintes pontos:

* Aprovando o objeto
* Aprovando as URLs e imagens
* Aprovação dos rótulos do URL
* Aprovando o link de cancelamento de subscrição
* Verificando o tamanho das provas
* Verificando o período de validade
* Verificando a programação de ondas

A tipologia a ser aplicada para cada delivery é selecionada na guia **[!UICONTROL Typologies]** nos parâmetros de delivery.

Você pode exibir e editar as regras de aprovação, o conteúdo, a ordem de execução e a descrição completa através do nó **[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]**.

Você poderá criar novas regras e definir novas tipologias a partir desse nó. No entanto, essas tarefas são reservadas para usuários expert que conhecem JavaScript.

Para editar a tipologia atual, clique no ícone **[!UICONTROL Edit link]** à direita do campo **[!UICONTROL Typology]**.

![](assets/s_ncs_user_email_del_typo_tab.png)

A guia **[!UICONTROL Rule]** fornece uma lista das regras de tipologia para serem aplicadas. Selecione uma regra e clique no ícone **[!UICONTROL Detail...]** para exibir sua configuração:

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>As tipologias do tipo **[!UICONTROL Arbitration]** são usadas dentro da estrutura de gerenciamento de regras de pressão. Para obter mais informações, consulte [esta seção](../../campaign/using/about-marketing-resource-management.md).

## Alterando o modo de aprovação {#changing-the-approval-mode}

A guia **[!UICONTROL Analysis]** das propriedades de delivery permite selecionar o modo de validação. Se os avisos forem gerados durante a análise (ex.: se certos caracteres estiverem acentuados no assunto da entrega etc.), você poderá configurar o delivery para definir se ele ainda deverá ou não ser executado. Por padrão, o usuário deverá confirmar o envio de mensagens no final da fase de análise: essa é a validação **manual**.

Selecione outro modo de aprovação na lista suspensa no campo apropriado.

![](assets/s_ncs_user_email_del_validation_mode.png)

Os seguintes modos de aprovação estão disponíveis:

* **[!UICONTROL Manual]**: no final da fase de análise, o usuário deverá confirmar o delivery para começar a enviar. Para fazer isso, clique no botão **[!UICONTROL Start]** para iniciar o delivery.
* **[!UICONTROL Semi-automatic]**: o envio começa automaticamente se a fase de análise não gerar mensagens de advertência.
* **[!UICONTROL Automatic]**: o envio começa automaticamente no fim da fase de análise, independentemente do resultado.
