---
title: Versão mais recente
description: Versão mais recente do Campaign Classic Observações
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: 36fef519be93b33d55a96992c1ce234f2eaea696
workflow-type: tm+mt
source-wordcount: '1820'
ht-degree: 4%

---


# Versão mais recente{#latest-release}

Esta página lista novos recursos, melhorias e correções com a versão **mais** recente do Campaign Classic Release Candidate.

Para obter a versão do Campaign Classic Gold Standard (versão mais recente do GA), [consulte esta página](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Versão 20.3.1 - Build 9228 {#release-20-3-1-build-9228}

_27 de outubro de 2020_

**Novidades**

<table> 
<thead>
<tr> 
<th> <strong>Melhorias na notificação por push do iOS</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Ao integrar seu aplicativo móvel à Campanha, é necessário proteger sua comunicação com o serviço de notificação por push (APNs) da Apple. Você pode usar autenticação baseada em certificado ou baseada em token.
</p>
<p>Esses dois modos de autenticação agora estão disponíveis para aplicativos móveis iOS no Campaign Classic:
</p>
<ul> 
<li><p>Autenticação baseada em token (recomendada): este modo de autenticação baseia-se em um arquivo .p8. Esse modo de autenticação é mais rápido, pois cada solicitação para APNs contém o token. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Saiba mais</a></p></li>
<li><p>Autenticação baseada em certificados: este modo de autenticação tem por base um arquivo .p12. Para cada aplicativo, é necessário um certificado separado. Este certificado é entregue pela Apple por meio de sua conta de desenvolvedor. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Saiba mais</a></p></li> 
</ul>
<p>Saiba como selecionar o modo de autenticação na Campanha na documentação <a href="../../delivery/using/configuring-the-mobile-application.md"></a>detalhada.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Melhorias na notificação por push do Android</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p><a href="../../delivery/using/configuring-the-mobile-application-android.md#creating-notification-message">As notificações</a> por push do Android foram aprimoradas para suportar a API HTTP v1 do FCM para autenticação de canal por push do Android. </p>
<p>Com a nova versão da API compatível, agora é possível enviar mensagens de notificação do FCM que fornecem recursos avançados de mensagens de push. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Saiba mais</a></p> 
<p>Saiba como configurar a API HTTP v1 do FCM para Android no Adobe Campaign nesta <a href="../../delivery/using/configuring-the-mobile-application-android.md">seção</a> .</p>
</td> 
</tr> 
</tbody> 
</table>

**Aprimoramentos de segurança**

* Carregamento seguro de bibliotecas: Para proteger contra ataques de pré-carregamento de DLL, o Campaign agora carrega as DLLs do Windows somente do caminho padrão de DLL do sistema do Windows ao carregar o cliente Campaign (nlclient). [Saiba mais](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* Correção de um problema de segurança para reforçar a proteção contra ataques SSRF (Server Side Request Forgery). (NEO-25661)



* Correção de um problema que ocorria ao manipular solicitações de privacidade do RGPD que impedia que registros fossem excluídos de tabelas personalizadas com uma relação de segundo nível com a tabela do Recipient. (NEO-25967)



* Correção de um problema de segurança usando chamadas de API feitas por usuários não administradores ao tentar sincronizar modelos do Adobe Experience Manager. (NEO-23487)




**Atualizações de compatibilidade**

Os seguintes sistemas agora são compatíveis com o Campaign:
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

**Recursos obsoletos**

Os seguintes recursos estão obsoletos na versão 20.3:

* O domínio demdex usado para importar e exportar audiências para o Adobe Experience Cloud está obsoleto. Se você estiver usando o domínio demdex para suas contas externas de importação/exportação, será necessário adaptar sua implementação de acordo. [Saiba mais](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* Aciona a autenticação da integração originalmente com base na configuração da autenticação oAUTH para acessar o pipeline agora foi alterada e movida para E/S de Adobe. [Saiba mais](../../integrations/using/configuring-adobe-io.md)

Saiba mais na página [Recursos](../../rn/using/deprecated-features.md)obsoletos e removidos.

**Aprimoramentos**

* Vários aprimoramentos foram feitos no console **do** Cliente:
   * Para evitar incompatibilidade com algumas restrições de regras de GPO de segurança da Internet, a tela de logon do console do cliente da Campanha foi substituída por um formulário Windows padrão incorporado.
   * Correção de um problema ao copiar/colar atividades em um fluxo de trabalho usando o console Cliente de 64 bits. (NEO-27635)



   * No menu **Sobre** , foram adicionadas informações para distinguir os consoles de 64 e 32 bits.
* O identificador de fluxo de trabalho agora é exibido nos logs ao retomar um fluxo de trabalho, o que permite identificar melhor qual fluxo de trabalho foi retomado.
* Um novo cookie permanente foi introduzido: nllastdelid. Este cookie (diferente de UUID230) armazenará a deliveryId. Quando o cookie da sessão não está presente, as informações de catálogo serão obtidas da deliveryId presente neste cookie.
Essa alteração corrige um problema que ocorria quando a sessão do navegador terminava: o cookie de sessão que contém deliveryId e BroadlogId foi excluído. Sem o deliveryId, não foi possível encontrar informações de catálogo e as informações da tabela de rastreamento estariam ausentes no caso de rastreamento permanente (último delivery).
Learn more about cookies in [this section](../../platform/using/privacy-and-recommendations.md#cookies).
* Desempenho de throughput de delivery de alto volume aprimorado com o servidor de entrega reiniciando o processo MTA antes do envio do delivery.

**Outras alterações**

* Ao usar o caminho relativo para SFTP, `~/` os caracteres não são mais adicionados automaticamente. Se necessário, é possível adicionar `~/` caracteres manualmente ao caminho, mas o Adobe recomenda o uso de um caminho **** absoluto.
* A autenticação do Windows NT foi removida dos métodos de autenticação disponíveis ao configurar um novo banco de dados com um Microsoft SQL Server. [Leia mais](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* O fluxo de trabalho de limpeza do banco de dados foi otimizado para a Teradata para melhorar o desempenho. (NEO-19959)



* A mensagem de erro exibida ao inserir uma imagem do Adobe Target foi aprimorada e o nome do locatário estava vazio na conta externa.
* Nas propriedades do delivery, a **[!UICONTROL Archive emails]** opção foi renomeada **[!UICONTROL Email BCC]**.
* Para melhorar a robustez, selecione Todos os query com nós inválidos agora são rejeitados. Se precisar desativar a verificação e voltar ao comportamento anterior, você pode definir XtkSecurity_Disable_QueryCheck como 0.

**Evoluções técnicas**

O Tomcat foi atualizado da versão 7 (7.0.103) para a 8 (8.5.57).

O `tomcat-7` diretório é substituído por um `tomcat-8` diretório.

No Windows, _is_neolane_setup.vbs_ e _apache_neolane.conf_ agora estão instalados no `conf` diretório (em vez de `tomcat-7/conf` anteriormente).

No linux, _apache_neolane.conf_ agora está instalado no `conf` diretório.

**Correções**

* Correção de um problema que impedia que estatísticas de delivery fossem recompostas.
* Correção de um problema que exibia uma mensagem de erro ao fazer upload de um arquivo CSV ao usar o Campaign Classic 9080 build conectado a um servidor usando uma compilação mais antiga. (NEO-23218)



* Correção de um problema que poderia exibir uma mensagem de erro ao configurar o assistente do Microsoft Dynamics CRM para uma conta externa. Isso se deve a um problema de compatibilidade com a versão mais recente da API do MS Dynamics CRM. (NEO-24528)
* Correção de um problema que impedia a exportação de registros de tipo de pesquisa (ou seja, dados compostos de registros de chave estrangeira conectados a outras tabelas) de Campaign Classic para o Microsoft Dynamics usando o conector do CRM. (NEO-23864)



* Correção de um problema que impedia a busca de dados do Microsoft Dynamics se a opção de índice **** Automático estivesse ativada no conector do CRM. (NEO-25981)



* Correção de um problema com a autenticação IMS que podia deixar as conexões abertas mesmo se tivessem sido encerradas. As conexões terminadas serão automaticamente fechadas assim que terminarem, a fim de evitar a acumulação de conexões e o consumo de recursos do sistema. (NEO-25996)



* Correção de um problema que não exibia nenhuma mensagem de erro quando a sincronização do conteúdo do Adobe Experience Manager falhava em um delivery devido a uma configuração incorreta da conta externa (conta ou senha incorreta). Uma mensagem agora é exibida em caso de falha, permitindo que você identifique o problema com mais facilidade. (NEO-25586)



* Correção de um problema que ocorria ao selecionar o tipo de operação **Atualizar** na atividade de dados **** Atualizar. Se os dados a serem atualizados estivessem incorretos, o fluxo de trabalho estaria com erro e falharia. Em caso de dados incorretos, o fluxo de trabalho não falhará e os registros serão armazenados em uma transição de saída **Rejeita** . (NEO-23794)



* Correção de um problema que impedia o funcionamento de workflows contendo subworkflows. (NEO-24036)



* Correção de um problema ao editar uma descrição de template de campanha que impedia a exibição do botão **Salvar** ao copiar símbolos de colagem, como, por exemplo, caracteres japoneses. (NEO-27071)



* Correção de um problema que impedia a alteração do servidor de rastreamento no assistente de configuração de instância.
* Correção de um problema que impedia que a descrição de uma campanha ou template de campanha fosse salva ao clicar fora da janela antes de clicar no botão **Salvar** . (NEO-27449)



* Correção de um problema que impedia que o fluxo de trabalho técnico **Número de perfis** de faturamento ativos (billingActiveContactCount) funcionasse. Isso pode acontecer se um link tiver sido executado em um campo calculado em uma extensão de schema. Grande quantidade de dados foi criada, o que pode fazer com que o banco de dados fique sem espaço temporário. (NEO-24062)



* Correção de um problema com a atividade de carregamento de **dados (arquivo)** , que poderia impedir a importação de caracteres japoneses de arquivos txt e csv se eles estivessem posicionados no final do arquivo. (NEO-24957)



* Correção de um problema com delivery contínuos que impedia que os campos **Análise Iniciada** e **Análise Concluída** fossem preenchidos corretamente. (NEO-20755)



* Correção de um problema que exibia uma mensagem de erro ao tentar pré-visualização de mensagens SMS após um query em outro schema que não **Recipient** (nms:recipient). (NEO-27517)



* Corrigido um problema ao usar o conector de FDA Snowflake. Um usuário com direitos de nome de acesso de Snowflake não pôde executar um query em um schema Snowflake. Um erro do tipo &quot;Senha não encontrada&quot; foi exibido nos registros. (NEO-23851)



* Correção de um problema ao usar um conector FDA que ocorria quando o nome do schema FDA vinculado era uma substring do nome de um elemento do schema atual. Isso ocorria, por exemplo, se o schema FDA era &quot;cust&quot; e um dos elementos no schema do Recipient era &quot;customer&quot;. Ao buscar a coluna dentro do elemento &quot;cliente&quot; e adicionar uma coluna do schema &quot;cliente&quot; FDA, o valor da coluna local estava ausente. (NEO-20193)



* Correção de um problema em workflows ao buscar registros de um banco de dados externo e inseri-los no banco de dados de Campanha. (NEO-26359)



* Correção de um problema no fluxo de trabalho técnico de status **do evento** Atualizar: para corresponder ao dimensionamento dos campos correspondentes recebidos na atividade de estatísticas **de** Delivery, o dimensionamento de três campos de destino na atividade **Atualizar estatísticas** de delivery foi alterado de 32 para 64 bits. (NEO-11557) Saiba mais sobre o fluxo de trabalho de status **do evento de** atualização [nesta seção](../../workflow/using/message-center--execution-.md).
* Correção de um problema no relatório Histórico **de Eventos do Centro de** Mensagens que causava erros de script ao tentar aplicar filtros e tornava o filtro impossível em um intervalo de datas. (NEO-23365)



* Correção de um problema de interferência entre os workflows técnicos de trabalhos **de** Campanha (operationMgt) e **Pré-visualização** (previsão). Isso ocorria quando os delivery programados ficavam no status &quot;Pronto para o Público alvo&quot; ou &quot;Pronto para ser entregue&quot;. (NEO-20819)



* Correção de um problema de análise XML quando o identificador XML não estava presente no campo mdata em xtkOperador. Estava causando falha após a atualização. (NEO-26113)



* Correção de um problema ao usar a atividade **File Transfer** vinculada a uma conta externa do Azure criptografada no SSL, onde a conexão era feita com HTTP em vez de HTTPS. (NEO-26720)



* Correção de um problema no banco de dados MSSQL em que um erro ocorria com o procedimento up_updatstats durante o fluxo de trabalho de limpeza.
* Corrigida uma falha que ocorria durante o encerramento do processo da Web se as solicitações de Interação ainda estivessem sendo processadas. (NEO-26447)



* Correção de um problema em que a função **NoNull** no Oracle DB não funcionava mais após a atualização 9032. (NEO-26488)



* Correção de um problema em que o fluxo de trabalho de rastreamento falhava após a atualização 9171 se o pacote LINEV2 fosse instalado sem o pacote do Centro de mensagens.
* Correção de um problema de escalabilidade que impedia que o pool de conexões fosse aumentado para o número desejado de conexões, pois a cadeia de conexão do banco de dados para o atributo &quot;APP&quot; acabava recebendo um valor inválido. (NEO-25105)



* Correção de um problema no nível de configuração do proxy que impedia o logon no Adobe Campaign após a atualização mais recente do Windows 10. (NEO-27813)



* Correção de um problema que tornava os URLs indesejados visíveis nos e-mails entregues após a importação de modelos HTML que continham links de rastreamento. (NEO-25909)



* Correção de um problema que causava a falha do servidor ao exibir os dados do público alvo do restante de uma atividade **dividida** em um fluxo de trabalho.
* Correção de um problema de falha do servidor ao impedir a corrupção da memória ao limpar o analisador de expressão. (NEO-26856)



* Correção de um problema na atividade de enriquecimentos em que usuários não administradores definiam variáveis de instância. (NEO-25653)


