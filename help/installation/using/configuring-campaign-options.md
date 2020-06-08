---
title: Configuração das opções de Campanha
seo-title: Configuração das opções de Campanha
description: Configuração das opções de Campanha
seo-description: null
page-status-flag: never-activated
uuid: 32e85e41-6898-4fb3-90c8-2201ceea2e91
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 9c1884f6-1dd8-41ab-b8dc-604c8cc2dc89
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de1173786c94c2a526153e7e6948f71c9523fa7b
workflow-type: tm+mt
source-wordcount: '3903'
ht-degree: 3%

---


# Lista de opções do Campaign Classic{#configuring-campaign-options}

O **[!UICONTROL Administration / Platform / Options]** nó permite configurar opções de Adobe Campaign.

>[!NOTE]
>
>A modificação ou atualização das opções de Adobe Campaign pode ser executada somente por usuários especialistas.

Alguns deles são incorporados ao instalar a Campanha e outros podem ser adicionados manualmente quando necessário. As opções disponíveis variam de acordo com os pacotes instalados com sua instância.

## Delivery {#delivery}

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
   <td> Data da última wideLogMsg recuperada da instância de entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> A data do último wideLogMsg enviado para a instância de entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Identificador de Relatórios do delivery. Entre em contato com o suporte para obter seu identificador.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> Lista de schemas para os quais você deseja usar endereços de teste para Renderização da Caixa de entrada. (os nomes dos elementos são separados por vírgulas) Por exemplo: custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NMS_AtivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Permite que o operador responsável pelo delivery confirme o envio, se um operador ou grupo de operadores específico for designado para iniciar um delivery nas propriedades do delivery.</p><p> Para fazer isso, ative a opção digitando "1" como valor. Para desativar essa opção, digite "0".</p><p> O processo de confirmação de delivery funcionará como padrão: somente o operador ou grupo de operadores designado ao delivery nas propriedades de delivery (ou um administrador) poderá confirmar e realizar o delivery. Consulte <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">esta seção</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> O Adobe Campaign usa uma variável global "Nms_DefaultRcpSchema" para dialogar com o banco de dados do recipient padrão (nms:recipient).<br /> O valor da opção deve corresponder ao nome do schema que corresponde à tabela do recipient externo.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Número mínimo de recipient para que um delivery seja considerado o principal no relatório de cobrança.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> provedor de serviço de roteamento padrão para os novos modelos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Número de BroadLogs criados para um delivery ao mesmo tempo.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Inserção (na tabela) de registros (wideLogs) por transações: número de linhas a serem processadas por lote.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Tamanho de agrupamento de partes do delivery ao analisar delivery mid-sourcing.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> Período de delivery padrão para um delivery (em segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> expressões regulares para normalizar mensagens de delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> Digitar "1" como valor permite excluir recipient que não desejam mais ser contatados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> Digitar "1" como valor permite ignorar automaticamente duplos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMask</span> <br /> </td> 
   <td> Permite que você defina a sintaxe do endereço Erro usado ao responder a uma mensagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMask</span> <br /> </td> 
   <td> Permite definir a sintaxe do endereço De usado ao enviar uma mensagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> Permite definir um limite de tempo limite (em segundos) para obter uma resposta do servidor ao recuperar uma imagem baixada de um URL personalizado e anexada a um email. Se esse valor for excedido, a mensagem não poderá ser enviada. O valor padrão é de 60 segundos.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> Permite definir o tamanho máximo (em bytes) permitido para uma imagem baixada de um URL personalizado e anexada a um email. O valor padrão é 100.000 bytes. Ao enviar uma prova e baixar as imagens para processar o e-mail, se o tamanho de uma imagem exceder esse valor ou se houver um problema de download, um erro será exibido nos Logs do delivery e o delivery da prova falhará.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> Permite definir um número máximo de anexos em um modelo de email ou de email transacional. Se esse valor for excedido, um aviso será exibido nos registros de análises do delivery ou ao publicar o modelo de email transacional. The default value is 1 attachment.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> Número máximo de tentativas durante a análise.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> Script de publicação.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> Desative a contagem de wideLogMsg para mensagens de push.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> Exiba o peso da mensagem no assistente do delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> O endereço de e-mail 'error' padrão no nível da instância usado para delivery de e-mail se deixado em branco pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Endereço de email padrão "de" no nível da instância usado para delivery de email se deixado em branco pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> O endereço de e-mail 'reply' padrão no nível da instância usado para delivery de e-mail se deixado em branco pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> Nome comum do cliente. Usado em algumas mensagens de aviso exibidas aos recipient.<br /> "Você está recebendo esta mensagem porque entrou em contato com ****** ou uma empresa afiliada. Para não receber mais mensagens de ****".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> Rótulo de email padrão "de" no nível da instância usado para delivery de email se deixado em branco pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Rótulo de email 'reply' padrão no nível da instância usado para delivery de email se deixado em branco pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> Período entre duas tentativas de uma mensagem de email (em segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> Período de tentativas para mensagens de email.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">FórmulaPrevisãoNms_MsgWeight</span> <br /> </td> 
   <td> Fórmula usada para calcular a ponderação de uma mensagem para um delivery provisório.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_WhitelistEmails</span> <br /> </td> 
   <td> Lista de endereços de email de encaminhamento autorizados (do módulo de processamento de email de entrada). Os endereços devem ser separados por vírgulas (ou * para permitir tudo). Por exemplo, xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> Chave AES usada no servlet 'lineImage' para codificar os URLs (canal LINE).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> No canal "email" (use como padrão): Número máximo de erros aceitos para erros SOFT durante o envio antes de colocar o recipient em quarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> No canal "email" (use como padrão): Período mínimo a ser gasto desde o erro SOFT referenciado anteriormente, antes de levar em conta um novo erro SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> No canal "mobile" : Número máximo de erros aceitos para erros SOFT durante o envio antes de colocar o recipient em quarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> No canal "mobile" : Período mínimo a ser gasto desde o erro SOFT referenciado anteriormente, antes de levar em conta um novo erro SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Permite especificar um período máximo (expresso em horas) para limitar o número de logs recuperados sempre que o fluxo de trabalho de sincronização for executado.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> Número máximo de chamadas na sessão MidSourcing, que pode ser executada em paralelo (3 por padrão).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> Atraso personalizado (em minutos) após o qual um delivery é considerado como "atrasado", o padrão é 30 minutos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryProcessingWindow</span> <br /> </td> 
   <td><p>Essa opção é usada pelo fluxo de trabalho técnico <span class="uicontrol"><a href="../../workflow/using/campaign.md">operation</a></span> ao contar o número de delivery em execução.</p>Permite definir o número de dias acima dos quais os delivery com status inconsistente serão excluídos da contagem de delivery em execução.</p><p>Por padrão, o valor é definido como "7", o que significa que delivery inconsistentes com mais de 7 dias serão excluídos.</p></td> 
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
   <td> O URL do servidor de mirrores page (por padrão, deve ser idêntico a NmsTracking_ServerUrl).<br /> É o valor padrão de delivery de email quando o URL não é especificado na definição do roteamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Parâmetros das mensagens SMS enviadas: informações transmitidas ao gateway SMS para indicar a prioridade da mensagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Número de tentativas ao enviar mensagens SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Período durante o qual serão efetuadas tentativas de mensagens SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Data da última consolidação para estatísticas <span class="uicontrol">NmsUserAgent</span> .<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Nome da opção que contém os segmentos da Web e seus estados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Ative/desative o suporte para caracteres especiais do Code128.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> Caracteres válidos para um endereço de email.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> Adicione essa opção com o valor "0" para desativar a edição do código XML dos delivery (clique com o botão direito do mouse / <span class="uicontrol">Editar fonte</span> XML ou atalho <span class="uicontrol">CTRL + F4</span> ).<br /> </td> 
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
   <td> Localização dos recursos para publicação no console do cliente Adobe Campaign. Consulte <a href="../../delivery/using/formatting.md#image-referencing">esta seção</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> Localização dos recursos para visualização no console do cliente Adobe Campaign. Consulte <a href="../../delivery/using/formatting.md#image-referencing">esta seção</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> Lista de máscaras de URL para as imagens ignoradas durante o upload.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Configuração do carregamento de imagem. Os valores podem ser none / tracking / script / lista (podem ser substituídos pelas configurações opcionais do operador). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> Pasta na qual as imagens no servidor devem ser armazenadas.<br /> </td> 
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
   <td> Permite definir o servidor no qual as imagens usadas nos delivery são armazenadas para permitir que o navegador as obtenha.<br /> Para versões de compilação &lt;= 5098, usamos o URL das imagens que foram carregadas na instância.<br /> Para versões de compilação &gt; 5098, usamos o URL público do delivery ou o URL da opção <span class="uicontrol">XtkFileRes_Public_URL</span> .<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Permite configurar o nome da instância para o upload de imagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Permite configurar a senha para o upload de imagens.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> Permite configurar os URLs de mídia para upload de imagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> Duração de validade padrão para recursos online de um delivery (em segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> Novo URL para arquivos de recurso público.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Gerenciamento de Campanhas e fluxos de trabalho {#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> Nome da opção </th> 
   <th> Descrição </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span> <br /> </td> 
   <td> Histórico de marketing exibido para esse número de meses.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> Período de validade padrão de uma campanha (em segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Número máximo de trabalhos de delivery/fluxo de trabalho/hipótese/simulação que podem ser processados por vez, iniciados pelo fluxo de trabalho operationMgt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Permite monitorar a execução do fluxo de trabalho técnico <a href="../../workflow/using/campaign.md">operationMgt</a> . Quando ativadas (valor "1"), as informações de execução são registradas nos logs de auditoria do fluxo de trabalho.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Período para definição de metas e condições de extração no modo agendado.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> Número de registros afetados após os quais as estatísticas de tabela são automaticamente recompostas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> Logotipo a ser exibido no canto superior direito dos relatórios exportados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Número de dias de espera entre verificações de workflows pausados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Ativate_OwnerConfirmation</span> <br /> </td> 
   <td> Ative a validação dos delivery pelo proprietário da operação digitando "1" como valor. Para desativar essa opção, digite "0".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> Biblioteca JS adicional para carregar na atividade do fluxo de trabalho "Notificações de Recurso de marketing".<br /> </td> 
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
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (Instalar modo de compatibilidade: build&gt;6000) Quando ativada (valor "1"), essa opção permite o uso de senhas antigas armazenadas no banco de dados para a conexão com o conta externa ou com a instância.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Essa chave é usada para criptografar a maioria das senhas no banco de dados. (conta externa, senha LDAP...).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Se 1 for selecionado, essa opção permitirá o PrivilegeEscalation no javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> Se 1 for selecionado, essa opção desativa os controles ACL durante um download de arquivo (via fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> Se 1 for selecionado, essa opção desativará a caixa de proteção do arquivo no Javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> Se definido como 'true', o operador não administrativo autorizado para atualizar os valores xtkOption por meio do assistente de implantação.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> Se 1 for selecionado, esta opção permite usar decryptString para descriptografar algumas senhas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> Insira o valor "1" para rastrear a exclusão de elementos com informações de trilha de auditoria no mData, por meio da modificação do campo "modificado por" antes da exclusão do registro.<br /> </td> 
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
   <td> Biblioteca JavaScript a ser personalizada para eventos enriquecedores. Deve conter a implementação destas duas funções:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : enriquece e salva eventos no banco de dados (onde <span class="uicontrol">aiEventId</span> corresponde à tabela de eventos em tempo real processados).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : enriquece e salva eventos no banco de dados (onde <span class="uicontrol">aiEventId</span> corresponde à tabela de ID dos eventos batch processados).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> A data da última atualização de status do evento por meio de logs do delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> Biblioteca JavaScript a ser personalizada para eventos de roteamentos. Deve conter a implementação destas duas funções:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatRtEvent(iEventId);</span> : retorna o nome interno do mensagen transacional selecionado para processar o evento em tempo real (onde <span class="uicontrol">iEventId</span> corresponde à ID do evento em tempo real processado).</p> </li> 
     <li> <p> <span class="uicontrol">dispatBatchEvent(iEventId);</span> : retorna o nome interno do mensagen transacional selecionado para processar o evento batch (onde <span class="uicontrol">iEventId</span> corresponde à ID do evento batch processado).</p> </li> 
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
   <td> Limite de alerta para o número médio de eventos em tempo real em fila.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Limite de alerta para tempo médio de enfileiramento de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> Limite de aviso para o tempo médio de enfileiramento de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> Limite de aviso para o número médio de eventos em tempo real em fila.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> Limite de alerta para erros de processamento de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Limite de aviso para erros de processamento de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> Limite de alerta para o número máximo de eventos em tempo real na fila.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> Limite de aviso para o número máximo de eventos em tempo real na fila.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> Limite de alerta para o número mínimo de eventos em tempo real na fila.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> Limite de aviso para o número mínimo de eventos em tempo real na fila.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> Limite antes da condição crítica para a fila de eventos em tempo real pendentes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Limite antes do aviso para a fila de eventos em tempo real pendentes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> Limite de alerta para throughput de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> Limite de aviso para throughput de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> Tamanho do agrupamento do roteamento do evento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> Atualize o ponteiro do status RtEvent (última data até a data em que os dados foram recuperados).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> URL do servidor do Centro de Mensagens usado para enviar mensagens de boas-vindas (canal LINE).<br /> </td> 
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
   <td> <p>Permite que você defina o atraso após o qual a transmissão é apagada do banco de dados.</p><p>Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor da lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual o histórico de eventos é apagado do banco de dados.</p><p>
   Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor da lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual os eventos são apagados do banco de dados.</p><p>Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor da lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual as estatísticas de eventos são apagadas do banco de dados.</p><p>Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor da lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual as proposições são apagadas do banco de dados.</p><p> Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor da lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual as quarentenas são apagadas do banco de dados.</p><p> Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor da lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual os delivery reciclados são apagados do banco de dados.</p><p> Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor da lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual os rejeitos são apagados do banco de dados.</p><p>Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor da lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual os logs de rastreamento são apagados do banco de dados.</p><p>Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor da lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual as estatísticas de rastreamento são apagadas do banco de dados.</p><p> Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor da lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual os visitantes são apagados do banco de dados.</p><p> Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor da lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual os resultados do fluxo de trabalho são apagados do banco de dados.</p><p> Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor da lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Opções do conector do SQL Datawarehouse do Azure.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Permite que você afete o comportamento Parar incondicional em todos os workflows e query de banco de dados PostgreSQL de acordo com os seguintes valores potenciais:<ul>
    <li><p>0 - padrão: para o processo de fluxo de trabalho, sem impacto no banco de dados<p></li>
    <li><p>1 - pg_cancel_backend: interrompe o processo de fluxo de trabalho e cancela o query no banco de dados<p></li>
    <li><p>2 - pg_cancel_backend: interrompe o processo de fluxo de trabalho e encerra o query no banco de dados<p></li></ul></td> 
  </tr>  
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Nome do tablespace destinado a conter os índices das tabelas padrão Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Nome do tablespace destinado a conter os dados das tabelas Adobe Campaign padrão.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Nome do tablespace destinado a conter os dados das tabelas de trabalho do Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Nome do tablespace destinado a conter os índices das tabelas de trabalho Adobe Campaign.<br /> </td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Permite configurar um banco de dados separado para tabelas de trabalho no Microsoft SQL Server, a fim de otimizar backups e replicação. A opção corresponde ao nome do banco de dados temporário: As tabelas de trabalho serão gravadas neste banco de dados, se especificado. Exemplo: 'tempdb.dbo.' (observe que o nome deve terminar com um ponto).</desc> <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">Leia mais</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Fuso horário da instância de Adobe Campaign. Consulte <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Configuração</a>.<br /> </td> 
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
   <td> ID do banco de dados. Começa por 'u' para Unicode DataBase.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> Prefixo adicionado aos nomes internos gerados automaticamente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> Número máximo de resultados retornados por um query em xtk:schema e xtk:srcSchema.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> Todos os schemas personalizados, criados depois desse tempo, com autopk="true" e sem o atributo "pkSequence" receberão uma sequência gerada automaticamente "auto_ &lt;schemanamespace&gt; &lt;schemaname&gt; _seq. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> Durante a migração, a estrutura em árvore é automaticamente reorganizada com base nos novos padrões de versão.<br /> Essa opção permite desativar a migração automática da árvore de navegação. Se você usá-lo, após a migração, será necessário excluir pastas obsoletas, adicionar as novas pastas e executar todas as verificações necessárias.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Tipo de dados:</span> Número inteiro</p> </li> 
     <li> <p> <span class="uicontrol">Valor (texto)</span> : 1 </p> </li> 
    </ul> Essa opção só deve ser usada se a árvore de navegação predefinida tiver sofrido muitas alterações.<br /> Para obter mais informações, consulte <a href="../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure">esta seção</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Data do último processamento da limpeza da tabela <span class="uicontrol">NmsEmailErrorStat</span> .<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Informações sobre o erro que ocorreu no Pós-atualização, seguindo a sintaxe abaixo:<br /> <strong>{Número da compilação}:{modo: pre/post/...}:{The 'lessThan'/'moreOrEquelThan' where error occurred + sub-Step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> Insira o valor "1" para que a atualização das estatísticas não seja realizada por meio do fluxo de trabalho de limpeza.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integration {#integration}

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
   <td> Tipos de recursos do AEM que podem ser usados no Adobe Campaign. Os valores devem ser separados por vírgulas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Permite configurar os Acionadores da Experience Cloud. O tipo de dados é "texto longo" e deve estar no formato JSON. Consulte <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Como usar os Acionadores da Experience Cloud com o Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> Essa opção é usada ao importar dados de um sistema de terceiros por meio de um conector CRM. Habilitar a opção   permite coletar apenas objetos modificados desde a última importação. Essa opção deve ser criada manualmente e preenchida como a seguir: 
    <ul> 
     <li> <p> <span class="uicontrol">Nome</span> interno: LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Valor (campo)</span> : data da última importação, com o formato aaaa/MM/dd hh:mm:ss. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> O servidor Adobe Target usado para a integração. Essa opção é selecionada por padrão. Esse valor corresponde ao Domain Server do Adobe Target, seguido pelo valor /m2. Por exemplo: tt.omtrdc.net/m2.<br /> Consulte <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">esta seção</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Nome da organização do Adobe Target. Esse valor corresponde ao nome do Client do Adobe Target.<br /> Consulte <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">esta seção</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> Opção usada para a integração com o Adobe Audiência Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> Opção usada para a integração com o Adobe Audiência Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Opções do conector Teradata.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> Opções de conector de gravação.<br /> </td> 
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
   <td> '+ [schema da proposta] + "_" + extAccountSource.@runningInstanceId + [schema da proposta] + "_" + vars.executeInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [ schema da proposta] + "_" + extAccountSource.@runningInstanceId + "_" + extAccountTarget.@runningInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> Rastreamento do fluxo de trabalho de sincronização.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> Ative/desative a gravação assíncrona de proposição ("0" para desativar, "1" para ativar).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> Permite ativar cupons.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Server {#server}

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
   <td> Identificador de Instância de execução.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> Identificador do cliente usado ao enviar o relatório de cobrança.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> URL de base interna para acessar o servidor de aplicativos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Número de compilação da instância CA antes da última atualização.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> URL base do servidor público de aplicativos da Web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> Permite que você continue usando funções SQL antigas não declaradas após a migração. Recomendamos vivamente que esta opção não seja utilizada devido aos riscos de segurança que apresenta.<br /> </td> 
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
   <td> <span class="uicontrol">FórmulaNmsTracking_Click</span> <br /> </td> 
   <td> Script de cálculo de URL rastreado.<br /> </td> 
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
   <td> A última vez que as informações de rastreamento foram consolidadas com novos dados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFórmula</span> <br /> </td> 
   <td> Abra o script de cálculo de URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> Senha do servidor de rastreamento<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> O ponteiro mantém o controle dos últimos eventos de mensagem que foram processados por meio de suas IDs e data.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> URL seguro do servidor de rastreamento frontal.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> URL do servidor de rastreamento frontal.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> Lista dos URLs usados para entrar em contato com os servidores de rastreamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> Conjunto de regras de identificação do navegador.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFórmula</span> <br /> </td> 
   <td> Script usado para calcular Tag de rastreamento web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> Nome do delivery virtual projetado para o gerenciamento de rastreamento da Web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> Permite definir o modo de rastreamento da Web.<br /> </td> 
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
   <td> <span class="uicontrol">Privacidade_Solicitação_ConfirmarExcluirPendente</span> <br /> </td> 
   <td> Se a opção 1 estiver selecionada, você deverá confirmar manualmente a exclusão na interface em uma segunda etapa. Caso contrário, os dados serão excluídos sem confirmação.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeleteCurrentDelay</span> <br /> </td> 
   <td> O atraso entre as solicitações aguarda a exclusão da confirmação e a solicitação é cancelada.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> O número máximo de erros permitidos ao processar/excluir uma solicitação de privacidade.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> O atraso entre solicitações é criado na fila e os dados da solicitação são excluídos.<br /> </td> 
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
   <td> <span class="uicontrol">XtkLdap_Active</span> <br /> </td> 
   <td> Ative o servidor LDAP para autenticar usuários e fornecer autorizações aos usuários.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> Logon do aplicativo para entrar em contato com o servidor para várias pesquisas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> Senha criptografada para o logon do aplicativo.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperador</span> <br /> </td> 
   <td> Ative a criação automática de operadores e direitos no Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> Fórmula de computação para DN LDAP com base no logon.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> Ative a pesquisa de DN no diretório.<br /> </td> 
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
   <td> Escopo de pesquisa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Mechanism</span> <br /> </td> 
   <td> Tipo de autenticação usado para entrar em contato com o servidor LDAP (simples, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> Ative a sincronização de autorizações e grupos do diretório LDAP para direitos nomeados no Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> Atributo LDAP contendo o nome da autorização.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> Base de pesquisa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> Procure no filtro autorizações do usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> Expressão para extrair os nomes dos direitos de Adobe Campaign das autorizações LDAP.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> Escopo de pesquisa.<br /> </td> 
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
   <td> O valor definido como 1 permitirá a adição da barra de rolagem aos formulários detalhados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> Instância a ser usada para invalidação de formulário da Web no modo 'outros servidores'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> Senha da instância a ser usada para invalidação de formulário da Web no modo 'outros servidores'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Opção que permite especificar o modo de invalidação de formulários da Web: local por padrão, usa servidores de rastreamento se a opção for 'tracking' e usa uma lista personalizada com a opção 'other server(s)'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> lista de endereço personalizado dos servidores a serem contatados para invalidação de formulário da Web (modo 'outros servidores').<br /> </td> 
  </tr> 
 </tbody> 
</table>

