---
product: campaign
title: Configuração das opções do Campaign
description: Saiba como configurar as opções do Campaign
feature: Installation, Application Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '3831'
ht-degree: 1%

---

# Lista de opções de Campaign Classic{#configuring-campaign-options}

O nó **[!UICONTROL Administration / Platform / Options]** permite configurar as opções do Adobe Campaign. Alguns deles são incorporados ao instalar o Campaign e outros podem ser adicionados manualmente quando necessário. As opções disponíveis variam de acordo com os pacotes instalados com sua instância.


>[!CAUTION]
>
>* As opções não listadas nesta página são somente internas e **não devem ser modificadas**.
>
>* A modificação ou atualização das opções do Adobe Campaign pode ser executada somente por usuários especialistas.

## Entrega {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span> <br /> </td> 
   <td> Data da última broadLogMsg recuperada da instância de entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> Data da última broadLogMsg enviada para a instância da capacidade de entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Identificador de relatórios de entrega. Contate o suporte para obter seu identificador.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> Lista de esquemas para os quais você deseja usar endereços de teste para Renderização da Caixa de Entrada. (nomes de elementos são separados por vírgulas) Por exemplo: custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">ENDEREÇO_CCO_EMTA</span> </td> 
   <td> Endereço de email de CCO para o qual o MTA aprimorado enviará uma cópia bruta dos emails enviados. <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_AtivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Permite que o operador encarregado do delivery confirme o envio, se um operador ou grupo de operadores específico for designado para iniciar um delivery nas propriedades do delivery.</p><p> Para fazer isso, ative a opção inserindo "1" como o valor. Para desativar essa opção, digite "0".</p><p> O processo de confirmação de envio funcionará como padrão: somente o operador ou grupo de operadores designado ao envio nas propriedades de delivery (ou um administrador) poderá confirmar e realizar o envio. Consulte <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">esta seção</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> O Adobe Campaign usa uma variável global "Nms_DefaultRcpSchema" para dialogar com o banco de dados do recipient padrão (nms:recipient).<br /> O valor da opção deve corresponder ao nome do esquema que corresponde à tabela do destinatário externo.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Número mínimo de destinatários para que uma entrega seja considerada como a principal no relatório de cobrança.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> Provedor de serviço de roteamento padrão para os novos modelos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Tamanho de lote mínimo (número de linhas) para a inserção de broadLogs durante a preparação da entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Limite de duração do lote (número de milissegundos) sob o qual o tamanho do lote para a inserção de broadLogs é duplicado durante uma preparação de entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Tamanho de agrupamento de partes de entrega ao analisar entregas de mid-sourcing.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> Período de entrega padrão para uma entrega (em segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> Expressões regulares para normalizar mensagens de entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> Inserir "1" como valor permite excluir destinatários que não desejam mais ser contatados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> Inserir "1" como valor permite que você ignore automaticamente duplicações.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> Permite definir a sintaxe do endereço de Erro usado ao responder a uma mensagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> Permite definir a sintaxe do endereço From usado ao enviar uma mensagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> Permite definir um tempo limite (em segundos) para obter uma resposta do servidor ao recuperar uma imagem baixada de um URL personalizado e anexada a um email. Se esse valor for excedido, a mensagem não poderá ser enviada. O valor padrão é 60 segundos.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> Permite definir o tamanho máximo (em bytes) permitido para uma imagem baixada de um URL personalizado e anexada a um email. O valor padrão é 100.000 bytes (100 KB). Ao enviar uma prova e baixar a(s) imagem(ns) para processar o email, se o tamanho de uma imagem exceder esse valor ou se houver um problema de download, um erro será exibido nos Logs de entrega e a entrega da prova falhará.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> Permite definir um número máximo de anexos em um template de email de email ou transacional. Se esse valor for excedido, um aviso será exibido nos logs de análise do delivery ou ao publicar o template de email transacional. O valor padrão é 1 anexo.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> Número máximo de novas tentativas durante a análise.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> Script de publicação.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> Desabilite a contagem broadLogMsg para mensagens de push.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> Exibir o peso da mensagem no assistente de entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> Endereço de email padrão 'erro' no nível da instância usado para entrega de email se deixado vazio pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Endereço de email 'de' padrão no nível da instância usado para entrega de email se deixado vazio pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Endereço de email padrão 'responder para' no nível da instância usado para entrega de email se deixado vazio pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> Nome comum do cliente. Usado em algumas mensagens de aviso exibidas para os destinatários.<br /> "Você está recebendo esta mensagem porque entrou em contato com a ‘Organização’ ou com uma empresa afiliada. Não receber mais mensagens de `Organization`<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> Rótulo de email 'de' padrão no nível da instância usado para entrega de email se deixado vazio pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Rótulo de email padrão 'responder para' no nível da instância usado para entrega de email, se deixado vazio pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> Período entre duas novas tentativas de uma mensagem de email (em segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> Período de novas tentativas para mensagens de email.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> Fórmula usada para calcular o peso de uma mensagem para uma entrega provisória.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> Lista de endereços de email de encaminhamento autorizado (do módulo de processamento de emails de entrada). Os endereços devem ser separados por vírgulas (ou * para permitir todos). Por exemplo, xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> Chave AES usada no servlet 'lineImage' para codificar as URLs (canal LINE).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> No canal "email" (use como padrão): Número máximo de erros aceitos, para erros SOFT durante o envio antes de colocar o destinatário em quarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> No canal "email" (use como padrão): Período mínimo a ser gasto desde o erro SOFT referenciado anteriormente, antes de considerar um novo erro SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> No canal "mobile" : Número máximo de erros aceitos, para erros SOFT durante o envio antes de colocar o recipient em quarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> No canal "mobile" : período mínimo a ser gasto desde o erro SOFT referenciado anterior, antes de considerar um novo erro SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Permite que um período máximo (expresso em horas) seja especificado como limite para o número de broadlogs recuperados toda vez que o workflow de sincronização é executado.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> Número máximo de chamadas na sessão MidSourcing, que podem ser executadas em paralelo (3 por padrão).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> Atraso personalizado (em minutos) após o qual uma entrega é considerada 'atrasada'; o padrão é 30 minutos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>Esta opção é usada pelo fluxo de trabalho técnico <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> ao contar o número de entregas em execução.</p>Ele permite definir o número de dias nos quais os deliveries com status inconsistente serão excluídos da contagem de deliveries em execução.</p><p>Por padrão, o valor é definido como "7", o que significa que os deliveries inconsistentes com mais de 7 dias serão excluídos.</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> Linha 1 do endereço do remetente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> Linha 3 do endereço do remetente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> Linha 4 do endereço do remetente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> Linha 6 do endereço do remetente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> Linha 7 do endereço do remetente.<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> A URL do servidor de mirror page (por padrão, deve ser idêntica a NmsTracking_ServerUrl).<br /> É o valor padrão de entregas de email quando a URL não está especificada na definição de roteamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Parâmetros de mensagens SMS enviadas: informações transmitidas para o gateway de SMS para indicar a prioridade da mensagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Número de tentativas ao enviar mensagens SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Período durante o qual as tentativas de mensagens SMS serão executadas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Data da última consolidação para <span class="uicontrol">NmsUserAgent</span> estatísticas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Nome da opção que contém os segmentos da Web e seus estados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Habilitar/desabilitar suporte para caracteres especiais para Code128.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> Caracteres válidos para um endereço de email.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> Adicione esta opção com o valor "0" para desabilitar a edição do código XML dos deliveries (clique com o botão direito do mouse em / <span class="uicontrol">Editar fonte XML</span> ou atalho <span class="uicontrol">CTRL + F4</span>).<br /> </td> 
  </tr>  
 </tbody> 
</table>

<!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr>
-->

## Recursos {#resources}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> Local dos recursos para publicação no console do cliente do Adobe Campaign. Consulte <a href="../../delivery/using/formatting.md#image-referencing">esta seção</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> Local dos recursos para visualização no console do cliente do Adobe Campaign. Consulte <a href="../../delivery/using/formatting.md#image-referencing">esta seção</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> Lista de máscaras de URL para as imagens ignoradas durante o carregamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Configuração do upload de imagens. Os valores podem ser none / tracking / script / list (pode ser substituído pelas configurações opcionais do operador). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> Pasta na qual as imagens do servidor devem ser armazenadas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> Espaço para exibir logotipos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> Pasta raiz para publicações.<br /> Para obter mais informações sobre a geração de conteúdo de HTML e Texto, consulte <a href="../../delivery/using/using-a-content-template.md">esta seção</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> Permite definir o servidor no qual as imagens usadas nos deliveries são armazenadas para permitir que o navegador as obtenha.<br /> Para versões de compilação &lt;= 5098, usamos a URL das imagens que foram carregadas na instância.<br /> Para versões de compilação &gt; 5098, usamos a URL pública da entrega ou a URL da opção <span class="uicontrol">XtkFileRes_Public_URL</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Permite configurar o nome da instância para carregamento de imagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Permite configurar a senha para o carregamento de imagens.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> Permite configurar a(s) URL(s) de mídia para carregamento de imagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> Duração da validade padrão dos recursos online de uma entrega (em segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> Nova URL para arquivos de recurso público.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Gerenciamento de campanhas e fluxos de trabalho {#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">JanelaAtividadeDeMarketingDoCrm</span> <br /> </td> 
   <td> Histórico de marketing mostrado para este número de meses.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> Período de validade padrão de uma campanha (em segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Número máximo de trabalhos de entrega/fluxo de trabalho/hipótese/simulação que podem ser processados por vez, iniciados pelo fluxo de trabalho operationMgt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Permite monitorar a execução do fluxo de trabalho técnico <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a>. Quando ativadas (valor "1"), as informações de execução são registradas nos logs de auditoria do fluxo de trabalho.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Período de tempo para condições de direcionamento e extração no modo agendado.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> Número de registros afetados após o qual as estatísticas da tabela são recalculadas automaticamente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> Logotipo a ser exibido no canto superior direito dos relatórios exportados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Número de dias de espera entre verificações de fluxos de trabalho pausados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Ativate_OwnerConfirmation</span> <br /> </td> 
   <td> Ative a validação de deliveries pelo proprietário da operação inserindo "1" como o valor. Para desativar esta opção, digite "0".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> Biblioteca JS adicional a ser carregada na atividade "Notificações de recurso de marketing" do fluxo de trabalho.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Segurança {#security}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBSchema</span> <br /> </td> 
   <td> (a partir da versão 21.1.3) Se 1 estiver selecionado (valor padrão), essa opção desativará a edição de esquemas internos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBJavascript</span> <br /> </td> 
   <td> (a partir da versão 21.1.3) Se 1 estiver selecionado (valor padrão), essa opção desativará a edição de códigos JavaScript incorporados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (Modo de compatibilidade de instalação: build&gt;6000) Quando ativada (valor "1"), essa opção permite o uso de senhas antigas armazenadas no banco de dados para a conexão com contas externas ou com a instância.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Essa chave é usada para criptografar a maioria das senhas no banco de dados. (contas externas, senha LDAP...).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Se 1 for selecionada, esta opção permitirá o privilégioEscalation no JavaScript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> Se 1 for selecionada, esta opção desabilitará os controles ACL durante o download de um arquivo (via fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> Se 1 for selecionada, essa opção desabilitará a sandboxing de arquivo no Javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> Se definido como 'true', o operador não administrador autorizado atualizará os valores de xtkOption por meio do assistente de implantação.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> Se 1 for selecionado, essa opção permitirá o uso de decryptString para descriptografar algumas senhas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> Insira o valor "1" para rastrear a exclusão de elementos com informações de Trilha de auditoria nos mData, por meio da modificação de seu campo "modificado por" antes da exclusão do registro.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Centro de mensagens {#message-center}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> Biblioteca do JavaScript a ser personalizada para enriquecimento de eventos. Deve conter a implementação destas duas funções:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : enriquece e salva eventos no banco de dados (onde <span class="uicontrol">aiEventId</span> corresponde à tabela de eventos em tempo real processados).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : enriquece e salva eventos no banco de dados (onde <span class="uicontrol">aiEventId</span> corresponde à tabela de ID de eventos em lote processados).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Data da última atualização de status de evento via logs de entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> Biblioteca JavaScript a ser personalizada para eventos de roteamento. Deve conter a implementação destas duas funções:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatRtEvent(iEventId);</span> : retorna o nome interno da mensagem transacional selecionada para processar o evento em tempo real (onde <span class="uicontrol">iEventId</span> corresponde à ID do evento em tempo real processado).</p> </li> 
     <li> <p> <span class="uicontrol">dispatBatchEvent(iEventId);</span> : retorna o nome interno da mensagem transacional selecionada para processar o evento em lote (em que <span class="uicontrol">iEventId</span> corresponde à ID do evento em lote processado).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Limite de alerta do tempo médio de envio de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> Limite de aviso para o tempo médio de envio de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> Limite de alerta para o tempo médio de processamento de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> Limite de aviso para o tempo médio de processamento de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> Limite de alerta para o número médio de eventos em tempo real enfileirados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Limite de alerta para o tempo médio de enfileiramento de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> Limite de aviso para o tempo médio de enfileiramento de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> Limite de aviso para o número médio de eventos em tempo real enfileirados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> Limite de alerta para o processamento de erros de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Limite de aviso para erros de processamento de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> Limite de alerta para o número máximo de eventos em tempo real enfileirados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> Limite de aviso para o número máximo de eventos em tempo real enfileirados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> Limite de alerta para o número mínimo de eventos em tempo real enfileirados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> Limite de aviso para o número mínimo de eventos em tempo real enfileirados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> Limite antes da condição crítica da fila de eventos em tempo real pendentes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Valor limite antes da exibição do aviso sobre a fila de eventos em tempo real pendentes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> Limite de alerta para a taxa de transferência de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> Limite de aviso para a taxa de transferência de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> Tamanho do reagrupamento para o roteamento de eventos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> Atualizar ponteiro de status RtEvent (última data até quando os dados foram recuperados).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> URL do servidor do Centro de Mensagens usada para enviar mensagens de boas-vindas (canal LINE).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Banco de dados {#database}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span> <br /> </td> 
   <td> Define a última vez que o processo de limpeza foi executado.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual o catálogo é apagado do banco de dados.</p><p>Essa opção é criada automaticamente assim que o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual o histórico de eventos é apagado do banco de dados.</p><p>
   Essa opção é criada automaticamente assim que o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual os eventos são apagados do banco de dados.</p><p>Essa opção é criada automaticamente assim que o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual as estatísticas de evento são apagadas do banco de dados.</p><p>Essa opção é criada automaticamente assim que o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual as apresentações são apagadas do banco de dados.</p><p> Essa opção é criada automaticamente assim que o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual as quarentenas são apagadas do banco de dados.</p><p> Essa opção é criada automaticamente assim que o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual os deliveries reciclados são apagados do banco de dados.</p><p> Essa opção é criada automaticamente assim que o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual as recusas são apagadas do banco de dados.</p><p>Essa opção é criada automaticamente assim que o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual os logs de rastreamento são apagados do banco de dados.</p><p>Essa opção é criada automaticamente assim que o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual as estatísticas de rastreamento são apagadas do banco de dados.</p><p> Essa opção é criada automaticamente assim que o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual os visitantes são apagados do banco de dados.</p><p> Essa opção é criada automaticamente assim que o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual os resultados do workflow são apagados do banco de dados.</p><p> Essa opção é criada automaticamente assim que o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Opções do conector do Azure SQL Datawarehouse.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Permite que você afete o comportamento de Unconditional Stop em todos os workflows e consultas de banco de dados PostgreSQL de acordo com os seguintes valores em potencial:<ul>
    <li><p>0 - padrão: interrompe o processo do fluxo de trabalho, sem impacto no banco de dados<p></li>
    <li><p>1 - pg_cancel_backend: interrompe o processo do workflow e cancela a consulta no banco de dados<p></li>
    <li><p>2 - pg_terminate_backend: interrompe o processo de fluxo de trabalho e encerra a consulta no banco de dados<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Nome do tablespace destinado a conter os dados das tabelas OOTB do Adobe Campaign.<br />Consulte <a href="../../installation/using/creating-and-configuring-the-database.md">Criando e configurando o banco de dados</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Nome do tablespace destinado a conter os índices das tabelas OOTB do Adobe Campaign.<br />Consulte <a href="../../installation/using/creating-and-configuring-the-database.md">Criando e configurando o banco de dados</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Nome do tablespace destinado a conter os dados das tabelas de trabalho do Adobe Campaign.<br />Consulte <a href="../../installation/using/creating-and-configuring-the-database.md">Criando e configurando o banco de dados</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Nome do tablespace destinado a conter os índices das tabelas de trabalho do Adobe Campaign.<br />Consulte <a href="../../installation/using/creating-and-configuring-the-database.md">Criando e configurando o banco de dados</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Permite configurar um banco de dados separado para tabelas de trabalho no Microsoft SQL Server, a fim de otimizar backups e replicação. A opção corresponde ao nome do banco de dados temporário: as tabelas de trabalho serão gravadas nesse banco de dados, se especificado. Exemplo: 'tempdb.dbo.' (observe que o nome deve terminar com um ponto). <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">Leia mais</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Fuso horário da instância do Adobe Campaign. Consulte <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Configuração</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> Os campos de cadeia de caracteres do banco de dados estão definidos com NChar?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> Os campos 'datetime' do banco de dados armazenam informações de fuso horário?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> ID do banco de dados. Começa por 'u' para o DataBase Unicode.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> Prefixo adicionado aos nomes internos gerados automaticamente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> Número máximo de resultados retornados por uma consulta em xtk:schema e xtk:srcSchema.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> Todos os esquemas personalizados, criados após esse tempo, com autopk="true" e sem o atributo "pkSequence" obterão uma sequência gerada automaticamente "auto_ 
    &lt;schemanamespace&gt; 
     &lt;nomedoesquema&gt;
       _seq. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> Durante a migração, a estrutura de árvore é reorganizada automaticamente com base nos novos padrões de versão.<br /> Essa opção permite desabilitar a migração automática da árvore de navegação. Se você o utilizar, após a migração, será necessário excluir pastas obsoletas, adicionar as novas pastas e executar todas as verificações necessárias.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Tipo de dados:</span> Inteiro</p> </li> 
     <li> <p> <span class="uicontrol">Valor (texto)</span> : 1 </p> </li> 
    </ul> Essa opção só deverá ser usada se a árvore de navegação pronta para uso tiver sofrido muitas alterações.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Última data de processamento da limpeza da tabela <span class="uicontrol">NmsEmailErrorStat</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Informações sobre o erro ocorrido na pós-atualização, seguindo a sintaxe abaixo:<br /> <strong>{Número da compilação}:{mode: pre/post/...}:{The 'lessThan'/'greaterOrEquelThan' onde ocorreu o erro + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> Insira o valor "1" para que a atualização de estatísticas não seja executada por meio do fluxo de trabalho de limpeza.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integração {#integration}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">AEMResourceTypeFilter</span> <br /> </td> 
   <td> Tipos de recursos de AEM que podem ser usados no Adobe Campaign. Os valores devem ser separados por vírgulas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Permite configurar Experience Cloud Triggers. O tipo de dados é "long text" e deve estar no formato JSON. Consulte <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Como usar Acionadores do Experience Cloud com o Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> Essa opção é usada ao importar dados de um sistema de terceiros por meio de um conector CRM. Habilitar a opção permite coletar apenas objetos modificados desde a última importação. Essa opção deve ser criada e preenchida manualmente conforme abaixo: 
    <ul> 
     <li> <p> <span class="uicontrol">Nome interno</span> : LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Valor (campo)</span>: data da última importação, com o formato aaaa/MM/dd hh:mm:ss. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Servidor do Adobe Target usado para a integração. Essa opção é selecionada por padrão. Esse valor corresponde ao Domain Server do Adobe Target, seguido pelo valor /m2. Por exemplo: tt.omtrdc.net/m2.<br /> Consulte <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">esta seção</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Nome da organização da Adobe Target. Esse valor corresponde ao nome do cliente do Adobe Target.<br /> Consulte <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">esta seção</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> Opção usada para a integração com o Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> Opção usada para a integração com o Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Opções de conector de teradata.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> Opções de conector de hive.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Ofertas {#offers}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span> <br /> </td> 
   <td> Número de cupons atualizados por transação SQL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchControl_</span> <br /> </td> 
   <td> '+ [esquema da proposta] + "_" + extAccountSource.@executionInstanceId + [esquema da proposta] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [ esquema da proposta] + "_" + extAccountSource.@executionInstanceId + "_" + extAccountTarget.@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> Rastreamento de fluxo de trabalho de sincronização.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> Habilitar/desabilitar gravação de apresentação assíncrona ("0" para desabilitar, "1" para habilitar).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> Permite habilitar cupons.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Servidor {#server}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsExecutionInstanceId</span> <br /> </td> 
   <td> Identificador de instância de execução.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> Identificador de cliente usado ao enviar o relatório de cobrança.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> URL base interna para acessar o servidor de aplicativos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Número da compilação da instância AC antes da última atualização.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> URL base do servidor público de aplicativos Web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> Permite continuar usando funções SQL não declaradas antigas após a migração. É altamente recomendável não usar esta opção devido aos riscos de segurança que ela apresenta.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rastreamento {#tracking}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Available</span> <br /> </td> 
   <td> Opção que permite ativar o rastreamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> Script de cálculo de URL rastreada.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> Permite definir a conta externa do servidor de rastreamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> Permite definir o nome da instância no servidor de rastreamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> Última vez que as informações de rastreamento foram consolidadas com novos dados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> Abrir script de cálculo de URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> Senha para o servidor de rastreamento <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> O ponteiro rastreia os eventos da última mensagem que foram processados por meio de suas IDs e data.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> URL segura do servidor de rastreamento frontal.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> URL do servidor de rastreamento frontal.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> Lista de URLs usadas para contatar os servidores de rastreamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> Conjunto de regras de identificação de navegador.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> Script usado para calcular marcas de rastreamento Web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> Nome da entrega virtual projetada para gerenciamento de rastreamento Web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> Permite definir o modo de rastreamento Web.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Privacidade {#privacy}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePending</span> <br /> </td> 
   <td> Se a opção 1 for selecionada, você deverá confirmar manualmente a exclusão na interface em uma segunda etapa. Caso contrário, os dados serão excluídos sem confirmação.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> O atraso entre as esperas de exclusão de confirmação e solicitação foi cancelado.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> O número máximo de erros permitidos ao processar/excluir uma solicitação de privacidade.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> Um atraso entre a solicitação é criado na fila e os dados da solicitação são excluídos.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## LDAP {#ldap}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Ative</span> <br /> </td> 
   <td> Habilite o servidor LDAP para ser usado para autenticar usuários e fornecer autorizações aos usuários.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> Logon do aplicativo para contatar o servidor para várias pesquisas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> Senha criptografada para o logon do aplicativo.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> Habilite a criação automática de operadores e direitos no Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> Fórmula de cálculo para DN LDAP baseada no logon.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> Habilitar pesquisa de DN no diretório.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> Base de pesquisa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span> <br /> </td> 
   <td> Filtro de pesquisa de DN.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span> <br /> </td> 
   <td> Escopo da pesquisa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Mechanism</span> <br /> </td> 
   <td> Tipo de autenticação usado para contatar o servidor LDAP (simples, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> Habilite a sincronização de autorizações e grupos do diretório LDAP para direitos nomeados no Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> Atributo LDAP que contém o nome da autorização.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> Base de pesquisa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> Filtro de pesquisa para autorizações de usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> Expressão para extrair os nomes dos direitos do Adobe Campaign das autorizações LDAP.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> Escopo da pesquisa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
   <td> Endereço do servidor LDAP (é possível especificar uma porta especificando ':' como separador).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Formulários web {#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkUseScrollBar</span> <br /> </td> 
   <td> O valor definido como 1 permitirá a adição da barra de rolagem a formulários de detalhes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> Instância a ser usada para invalidação de formulário web no modo "outro(s) servidor(es)".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> Senha da instância a ser usada para invalidação de formulário web no modo "outro(s) servidor(es)".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Opção que permite especificar o modo de invalidação de formulários web: local por padrão; usa servidores de rastreamento se a opção for "rastreamento"; usa uma lista personalizada se a opção for "outro(s) servidor(es)".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> Lista personalizada de endereços de servidores a serem contatados para invalidação de formulário web (modo "outro(s) servidor(es)").<br /> </td> 
  </tr> 
 </tbody> 
</table>
