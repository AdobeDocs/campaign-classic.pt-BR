---
product: campaign
title: Configuração das opções do Campaign
description: Saiba como configurar as opções do Campaign
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: c095d7ddde4b4ac23467ebd0fa8ee2fb613aacdc
workflow-type: tm+mt
source-wordcount: '3941'
ht-degree: 3%

---

# Lista de opções do Campaign Classic{#configuring-campaign-options}

O nó **[!UICONTROL Administration / Platform / Options]** permite configurar as opções do Adobe Campaign. Alguns deles são incorporados ao instalar o Campaign e outros podem ser adicionados manualmente quando necessário. As opções disponíveis variam de acordo com os pacotes instalados com sua instância.

>[!CAUTION]
>
>* As opções não listadas nesta página são somente internas e **não devem ser modificadas**.
   >
   >
* A modificação ou atualização das opções do Adobe Campaign só pode ser executada por especialistas usuários.


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
   <td> Data da última broadLogMsg recuperada da instância de deliverability.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> Data do último broadLogMsg enviado à instância de deliverability.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Identificador de relatórios do delivery. Entre em contato com o suporte para obter seu identificador.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> Lista de esquemas para os quais você deseja usar endereços de teste para Renderização da Caixa de Entrada. (os nomes dos elementos são separados por vírgulas) Por exemplo: custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NMS_AtivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Permite que o operador encarregado do delivery confirme o delivery, se um operador ou grupo de operadores específico for designado para iniciar um delivery nas propriedades do delivery.</p><p> Para fazer isso, ative a opção inserindo "1" como o valor. Para desativar essa opção, digite "0".</p><p> O processo de confirmação de delivery funcionará como padrão: somente o operador ou grupo de operadores designado ao delivery nas propriedades de delivery (ou um administrador) poderá confirmar e realizar o delivery. Consulte <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">esta seção</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> O Adobe Campaign usa uma variável global "Nms_DefaultRcpSchema" para diálogo com o banco de dados do recipient padrão (nms:recipient).<br /> O valor da opção deve corresponder ao nome do schema que corresponde à tabela externa do recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Número mínimo de recipients para que um delivery seja considerado como o principal no relatório de faturamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> Provedor de serviço de roteamento padrão para os novos modelos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Número de BroadLogs criados para um delivery de uma vez.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Inserção (na tabela) de logs (broadLogs) por transações : número de linhas a processar por lote.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Tamanho do agrupamento de partes do delivery ao analisar entregas de mid-sourcing.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> Período de entrega padrão para um delivery (em segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> Expressões regulares para normalizar mensagens de delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> Inserir "1" como o valor permite excluir recipients que não desejam mais ser contatados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> Inserir "1" como o valor permite que você ignore duplas automaticamente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMask</span> <br /> </td> 
   <td> Permite definir a sintaxe do endereço de Erro usado ao responder a uma mensagem.<br /> </td> 
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
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadImageSize</span> <br /> </td> 
   <td> Permite definir o tamanho máximo (em bytes) permitido para uma imagem baixada de um URL personalizado e anexada a um email. O valor padrão é de 100.000 bytes. Ao enviar uma prova e baixar a(s) imagem(s) para processar o email, se o tamanho de uma imagem exceder esse valor ou se houver um problema de download, um erro será exibido nos Logs do delivery e o delivery da prova falhará.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> Permite definir um número máximo de anexos em um email ou modelo de email transacional. Se esse valor for excedido, um aviso será exibido nos logs de análise do delivery ou ao publicar o template de email transacional. O valor padrão é 1 anexo.<br /> </td> 
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
   <td> Desative a contagem broadLogMsg para mensagens de push.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> Exiba o peso da mensagem no assistente do delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> Endereço de email 'erro' padrão no nível da instância usado para entrega de email se deixado em branco pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Endereço de email 'de' padrão no nível da instância usado para entrega de email se deixado em branco pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Endereço de email 'reply' padrão no nível da instância usado para delivery de email se deixado em branco pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> Nome comum do cliente. Usada em algumas mensagens de aviso exibidas para os recipients.<br /> "Você está recebendo esta mensagem porque esteve em contato com ***** ou com uma empresa afiliada. Para não receber mais mensagens de ****".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> Rótulo de email 'de' padrão no nível da instância usado para entrega de email se deixado em branco pelo usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Rótulo de email 'reply' padrão no nível da instância usado para entrega de email se deixado em branco pelo usuário.<br /> </td> 
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
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> Fórmula usada para calcular a ponderação de uma mensagem para um delivery provisional.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> Lista de endereços de email de encaminhamento autorizados (do módulo de processamento de email de entrada). Os endereços devem ser separados por vírgulas (ou * para permitir tudo). Por exemplo, xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> Chave AES usada no servlet 'lineImage' para codificar os URLs (canal LINE).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> No canal "email" (use como padrão) : Número máximo de erros aceitos para erros SOFT durante o envio antes de colocar o recipient em quarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> No canal "email" (use como padrão) : Período mínimo a ser gasto desde o erro SOFT referenciado anterior, antes de considerar um novo erro SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> No canal "móvel" : Número máximo de erros aceitos para erros SOFT durante o envio antes de colocar o recipient em quarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> No canal "móvel" : Período mínimo a ser gasto desde o erro SOFT referenciado anterior, antes de considerar um novo erro SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Permite que um período máximo (expresso em horas) seja especificado como limite para o número de broadlogs recuperados toda vez que o workflow de sincronização é executado.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> Número máximo de chamadas na sessão MidSourcing, que pode ser executada em paralelo (3 por padrão).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> Atraso personalizado (em minutos) após o qual um delivery é considerado "atrasado", sendo o padrão 30 minutos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>Essa opção é usada pelo workflow técnico <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> ao contar o número de deliveries em execução.</p>Ela permite definir o número de dias acima dos quais os deliveries com status inconsistente serão excluídos da contagem de entregas em execução.</p><p>Por padrão, o valor é definido como "7", o que significa que os deliveries inconsistentes com mais de 7 dias serão excluídos.</p></td> 
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
   <td> O URL do servidor da mirror page (por padrão, deve ser idêntico a NmsTracking_ServerUrl).<br /> É o valor padrão de deliveries de email quando o URL não é especificado na definição de roteamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Parâmetros das mensagens SMS enviadas: informações transmitidas ao gateway de SMS para indicar a prioridade da mensagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Número de tentativas ao enviar mensagens SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Período durante o qual novas tentativas de mensagens SMS serão executadas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Data da última consolidação para as estatísticas <span class="uicontrol">NmsUserAgent</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Nome da opção que contém os segmentos da Web e seus estados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Ative/desative o suporte para caracteres especiais do Código128.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> Caracteres válidos para um endereço de email.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> Adicione essa opção com o valor "0" para desabilitar a edição do código XML dos deliveries (clique com o botão direito do mouse / <span class="uicontrol">Editar fonte XML</span> ou <span class="uicontrol">CTRL + F4</span> atalho).<br /> </td> 
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
   <td> Configuração do upload de imagem. Os valores podem ser none / tracking / script / list (podem ser substituídos pelas configurações opcionais do operador). </td> 
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
   <td> Pasta raiz para publicações.<br /> Para obter mais informações sobre a geração de conteúdo de HTML e texto, consulte  <a href="../../delivery/using/using-a-content-template.md">esta seção</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> Permite definir o servidor no qual as imagens usadas nos deliveries são armazenadas para permitir que o navegador as obtenha.<br /> Para versões de build  &lt;&gt;<br /> Para versões de compilação &gt; 5098, usamos o URL público do delivery ou o URL da opção  <span class="uicontrol">XtkFileRes_Public_</span> URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Permite configurar o nome da instância para o upload da imagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Permite configurar a senha para o upload de imagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> Permite configurar os URLs de mídia para o upload de imagem.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> Duração de validade padrão para recursos online de um delivery (em segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> Novo URL para arquivos de recursos públicos.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Campanha e gerenciamento de workflow {#campaign-e-workflow-management}

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
   <td> Histórico de marketing mostrado para esse número de meses.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> Período de validade padrão de uma campanha (em segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Número máximo de tarefas de delivery/workflow/hipótese/simulação que podem ser processadas por vez, iniciadas pelo workflow operationMgt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Permite monitorar a execução do workflow técnico <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a>. Quando ativadas (valor "1"), as informações de execução são registradas nos logs de auditoria do workflow.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Período de tempo para definição de alvos e condições de extração no modo agendado.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> Número de registros afetados após os quais as estatísticas de tabela são automaticamente recalculadas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> Logotipo a ser exibido no canto superior direito dos relatórios exportados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Número de dias para aguardar entre verificações de fluxos de trabalho pausados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Ativate_OwnerConfirmation</span> <br /> </td> 
   <td> Ative a validação de deliveries pelo proprietário da operação inserindo "1" como o valor. Para desativar esta opção, digite "0".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> Biblioteca JS adicional para carregar na atividade do workflow "Notificações de recurso de marketing".<br /> </td> 
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
   <td> (Instalar modo de compatibilidade: build&gt;6000) Quando ativada (valor "1"), essa opção permite o uso de senhas antigas armazenadas no banco de dados para a conexão com contas externas ou com a instância.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Essa chave é usada para criptografar a maioria das senhas no banco de dados. (contas externas, senha LDAP..).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Se 1 for selecionado, essa opção permitirá o privilegieEscalation em javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> Se 1 for selecionado, essa opção desativa os controles ACL durante um download de arquivo (via fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> Se 1 for selecionado, essa opção desativa a sandbox de arquivos no Javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> Se definido como 'true', operador não administrador autorizado para atualizar os valores de xtkOption por meio do assistente de implantação.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> Se 1 for selecionado, essa opção permitirá o uso de decryptString para descriptografar algumas senhas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> Insira o valor "1" para rastrear a exclusão de elementos com informações da Trilha de auditoria no mData, por meio da modificação do campo "modificado por" antes da exclusão do registro.<br /> </td> 
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
   <td> Biblioteca de JavaScript a ser personalizada para enriquecer eventos. Deve conter a implementação dessas duas funções:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : enriquece e salva eventos no banco de dados (onde  <span class="uicontrol"></span> aiEventIdits corresponde à tabela de eventos em tempo real processados).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : enriquece e salva eventos no banco de dados (onde  <span class="uicontrol"></span> aiEventIdentidade corresponde à tabela de ID de eventos em lote processados).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Data da última atualização do status do evento por meio de logs de delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> Biblioteca JavaScript a ser personalizada para eventos de roteamento. Deve conter a implementação dessas duas funções:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatRtEvent(iEventId);</span> : retorna o nome interno da mensagem transacional selecionada para processar o evento em tempo real (onde  <span class="uicontrol"></span> iEventIdentidade corresponde à ID do evento em tempo real processado).</p> </li> 
     <li> <p> <span class="uicontrol">dispatBatchEvent(iEventId);</span> : retorna o nome interno da mensagem transacional selecionada para processar o evento batch (onde  <span class="uicontrol"></span> iEventIdentidade corresponde à ID do evento batch processado).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Limite de alertas do tempo médio de envio de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> Limite de aviso para o tempo médio de envio de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> Limite de alertas para o tempo médio de processamento de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> Limite de aviso para o tempo médio de processamento de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> Limite de alertas para o número médio de eventos em tempo real enfileirados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Limite de alertas para o tempo médio de enfileiramento de eventos em tempo real.<br /> </td> 
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
   <td> Limite de alertas para erros de processamento de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Limite de aviso para erros de processamento de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> Limite de alertas para o número máximo de eventos em tempo real enfileirados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> Limite de aviso para o número máximo de eventos em tempo real enfileirados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> Limite de alertas para o número mínimo de eventos em tempo real enfileirados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> Limite de aviso para o número mínimo de eventos em tempo real enfileirados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> Limite antes da condição crítica para a fila de eventos em tempo real pendentes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Limite antes de avisar para a fila de eventos em tempo real pendentes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> Limite de alertas para throughput de eventos em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> Limite de aviso para throughput do evento em tempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> Tamanho do reagrupamento para o roteamento do evento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> Atualizar ponteiro do status de RtEvent (última data até quando os dados foram recuperados).<br /> </td> 
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
   <td> <p>Permite definir o atraso após o qual o broadlog é apagado do banco de dados.</p><p>Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual o histórico de eventos é apagado do banco de dados.</p><p>
   Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual os eventos são apagados do banco de dados.</p><p>Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual as estatísticas do evento são apagadas do banco de dados.</p><p>Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual as apresentações são apagadas do banco de dados.</p><p> Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual as quarentenas são apagadas do banco de dados.</p><p> Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual os deliveries reciclados são apagados do banco de dados.</p><p> Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual as rejeições são apagadas do banco de dados.</p><p>Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual os logs de rastreamento são apagados do banco de dados.</p><p>Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir o atraso após o qual as estatísticas de rastreamento são apagadas do banco de dados.</p><p> Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual os visitantes são apagados do banco de dados.</p><p> Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir o atraso após o qual os resultados do workflow são apagados do banco de dados.</p><p> Essa opção é criada automaticamente quando o atraso é modificado na interface. Se você modificar o valor na lista de opções, ele deverá ser expresso em segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Opções de conector do Azure SQL Datawarehouse.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Permite afetar o comportamento de Interrupção Incondicional em todos os workflows e queries de banco de dados PostgreSQL de acordo com os seguintes valores em potencial:<ul>
    <li><p>0 - padrão: interrompe o processo de workflow, sem impacto no banco de dados<p></li>
    <li><p>1 - pg_cancel_backend: interrompe o processo do fluxo de trabalho e cancela a consulta no banco de dados<p></li>
    <li><p>2 - pg_terminate_backend: interrompe o processo do fluxo de trabalho e encerra a consulta no banco de dados<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Nome do tablespace destinado a conter os dados das tabelas ootb do Adobe Campaign.<br />Consulte  <a href="../../installation/using/creating-and-configuring-the-database.md">Criação e configuração do banco de dados</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Nome do tablespace destinado a conter os índices das tabelas ootb do Adobe Campaign.<br />Consulte  <a href="../../installation/using/creating-and-configuring-the-database.md">Criação e configuração do banco de dados</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Nome do tablespace destinado a conter os dados das tabelas de trabalho do Adobe Campaign.<br />Consulte  <a href="../../installation/using/creating-and-configuring-the-database.md">Criação e configuração do banco de dados</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Nome do tablespace destinado a conter os índices das tabelas de trabalho do Adobe Campaign.<br />Consulte  <a href="../../installation/using/creating-and-configuring-the-database.md">Criação e configuração do banco de dados</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Permite configurar um banco de dados separado para tabelas de trabalho no Microsoft SQL Server, a fim de otimizar backups e replicação. A opção corresponde ao nome do banco de dados temporário: As tabelas de trabalho serão gravadas neste banco de dados, se especificado. Exemplo: 'tempdb.dbo.' (observe que o nome deve terminar com um ponto). <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">Leia mais</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Fuso horário da instância do Adobe Campaign. Consulte <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Configuração</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> Os campos de sequência do banco de dados estão definidos com NChar?<br /> </td> 
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
   <td> Número máximo de resultados retornados por uma consulta em xtk:schema e xtk:srcSchema.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> Todos os esquemas personalizados, criados após esse tempo, com autopk="true" e sem o atributo "pkSequence" receberão uma sequência gerada automaticamente "auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       _seq. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> Durante a migração, a estrutura em árvore é automaticamente reorganizada com base nos novos padrões de versão.<br /> Essa opção permite desativar a migração automática da árvore de navegação. Se você usá-lo, após a migração, terá que excluir pastas obsoletas, adicionar as novas pastas e executar todas as verificações necessárias.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Tipo de dados: </span> Número inteiro</p> </li> 
     <li> <p> <span class="uicontrol">Valor (texto)</span> : 1 </p> </li> 
    </ul> Essa opção só deve ser usada se a árvore de navegação predefinida tiver sofrido muitas alterações.<br /> Para obter mais informações, consulte <a href="../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure">esta seção</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Data do último processamento da limpeza da tabela <span class="uicontrol">NmsEmailErrorStat</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Informações relativas ao erro que ocorreu no Postupgrade, seguindo a sintaxe abaixo:<br /> <strong>{Build number}:{mode: pre/post/..}:{The 'lessThan'/'greaterOrEquelThan' where error was + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> Insira o valor "1" para que a atualização de estatísticas não seja executada por meio do workflow de limpeza.<br /> </td> 
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
   <td> Permite configurar Experience Cloud Triggers. O tipo de dados é "long text" e deve estar no formato JSON. Consulte <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Como usar Experience Cloud Triggers com Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> Essa opção é usada ao importar dados de um sistema de terceiros por meio de um conector CRM. Habilitar a opção  permite coletar apenas objetos modificados desde a última importação. Essa opção deve ser criada e preenchida manualmente como abaixo: 
    <ul> 
     <li> <p> <span class="uicontrol">Nome</span>  interno: LASTIMPORT_&lt;&gt;_&lt;&gt;</p> </li> 
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
   <td> Opções do conector Hive.<br /> </td> 
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
   <td> Rastreamento do fluxo de trabalho de sincronização.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> Ative/desative a gravação assíncrona de propostas ("0" para desabilitar, "1" para habilitar).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> Permite ativar cupons.<br /> </td> 
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
   <td> Identificador da instância de execução.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> Identificador do cliente usado ao enviar o relatório de faturamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> URL de base interna para acessar o servidor de aplicativos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Número de compilação da instância AC antes da última atualização.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> URL base do servidor público de aplicações Web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> Permite que você continue usando funções SQL antigas não declaradas após a migração. É altamente recomendável não usar essa opção devido aos riscos de segurança que ela introduz.<br /> </td> 
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
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> Abra o script de cálculo do URL.<br /> </td> 
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
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> Script usado para calcular tags de rastreamento Web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> Nome do delivery virtual criado para o gerenciamento de rastreamento Web.<br /> </td> 
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
   <td> Se a opção 1 estiver selecionada, será necessário confirmar manualmente a exclusão na interface em uma segunda etapa. Caso contrário, os dados serão excluídos sem confirmação.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> O atraso entre a solicitação aguarda a exclusão da confirmação e a solicitação é cancelada.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> O número máximo de erros permitidos ao processar/excluir uma solicitação de privacidade.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> O atraso entre a solicitação é criado na fila e os dados da solicitação são excluídos.<br /> </td> 
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
   <td> Habilite o servidor LDAP a ser usado para autenticar usuários e fornecer autorizações aos usuários.<br /> </td> 
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
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> Habilite a criação automática de operadores e direitos no Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> Fórmula de cálculo para DN LDAP com base no logon.<br /> </td> 
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
   <td> <span class="uicontrol">XtkLdap_Engine</span> <br /> </td> 
   <td> Tipo de autenticação usado para entrar em contato com o servidor LDAP (simples, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> Ative a sincronização de autorizações e grupos do diretório LDAP para direitos nomeados no Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> Atributo LDAP contendo o nome de autorização.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> Base de pesquisa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> Pesquise o filtro para autorizações do usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> Expressão para extrair os nomes dos direitos do Adobe Campaign das autorizações LDAP.<br /> </td> 
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
   <td> O valor definido como 1 permitirá a adição da barra de rolagem aos formulários de detalhes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> Instância a ser usada para invalidação de formulário web no modo 'outros servidores'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> Senha da instância a ser usada para invalidação de formulário web no modo 'outros servidores'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Opção que permite especificar o modo de invalidação de formulários web: local por padrão, usa servidores de rastreamento se a opção for 'tracking' e usa uma lista personalizada com a opção 'other server(s)'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> Lista de endereços personalizados de servidores a serem contatados para invalidação de formulário web (modo 'outros servidores').<br /> </td> 
  </tr> 
 </tbody> 
</table>
