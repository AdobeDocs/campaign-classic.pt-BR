---
product: campaign
title: Versões de 2020
description: Saiba mais sobre as atualizações do Campaign Classic 2020
feature: Overview
role: User
level: Beginner
exl-id: e2eb7e04-faaa-4df0-913d-471c291eeb03
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '6601'
ht-degree: 94%

---

# Versões de 2020{#release-2020}

![](../../assets/v7-only.svg)


## Versão 20.3{#release-20-3}

### ![](assets/do-not-localize/red_2.png) Versão 20.3.3 - Build 9234 {#release-20-3-3-build-9234}

_11 de janeiro de 2021_

* Correção de um problema de segurança para reforçar a proteção contra situações de SSRF (Server Side Request Forgery). (NEO-27777)



* Correção de um problema de regressão relacionado ao processo de geração de banda larga que pode causar o travamento do processo de MTA.

### ![](assets/do-not-localize/red_2.png) Versão 20.3.1 - Build 9228 {#release-20-3-1-build-9228}

_27 de outubro de 2020_

>[!CAUTION]
>
> * Esta versão é fornecida com um novo protocolo de conexão: se você estiver se conectando ao Campaign pelo Serviço de identidade da Adobe (IMS), a atualização será obrigatória para o servidor do Campaign e o console do cliente poderem se conectar ao Campaign após **30 de junho de 2021**. [Saiba mais](../../technotes/using/ims-updates.md)
> * Esta versão vem com uma [correção de segurança](https://helpx.adobe.com/br/security/products/campaign/apsb21-04.html): a atualização é obrigatória para reforçar a segurança do ambiente.
> * Se você estiver usando a integração dos acionadores da Experience Cloud por meio da autenticação oAuth, será necessário migrar para o Adobe I/O conforme descrito [nesta página](../../integrations/using/configuring-adobe-io.md). O modo de autenticação oAuth herdado do Campaign [foi removido](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) em **setembro de 2021**. Os ambientes hospedados se beneficiarão de uma extensão até **23 de fevereiro de 2022**. Como cliente local ou híbrido, entre em contato com o Atendimento ao cliente do Adobe para estender o suporte até fevereiro de 2022. Você deve fornecer [o AppID do aplicativo OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) para a Adobe.


**Novidades**

<table> 
<thead>
<tr> 
<th> <strong>Melhorias na notificação por push do iOS</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Ao integrar seu aplicativo móvel ao Campaign, é necessário proteger sua comunicação com o serviço de notificação por push (APNs) da Apple. Você pode usar autenticação por certificado ou por token.
</p>
<p>Esses dois modos de autenticação agora estão disponíveis para aplicativos móveis iOS no Campaign Classic:
</p>
<ul> 
<li><p>Autenticação por token (recomendada): este modo de autenticação se baseia em um arquivo .p8. Esse modo de autenticação é mais rápido, pois cada solicitação para APNs contém o token. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Saiba mais</a></p></li>
<li><p>Autenticação por certificado: este modo de autenticação tem por base um arquivo .p12. Para cada aplicativo, é necessário um certificado separado. Este certificado é entregue pela Apple por meio de sua conta de desenvolvedor. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Saiba mais</a></p></li> 
</ul>
<p>Saiba como selecionar o modo de autenticação no Campaign na <a href="../../delivery/using/configuring-the-mobile-application.md">documentação detalhada</a>.</p>
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
<td> <p><a href="../../delivery/using/configuring-the-mobile-application-android.md#creating-notification-message">As notificações por push do Android foram aprimoradas para aceitar a API HTTP v1 do FCM para autenticação de canal por push do Android.</a> </p>
<p>Com a nova versão da API compatível, agora é possível enviar mensagens de notificação do FCM que fornecem recursos avançados de mensagens de push. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Saiba mais</a></p> 
<p>Saiba como configurar a API HTTP v1 do FCM para Android no Adobe Campaign <a href="../../delivery/using/configuring-the-mobile-application-android.md">nesta seção</a> .</p>
</td> 
</tr> 
</tbody> 
</table>

**Aprimoramentos de segurança**

* Carregamento seguro de bibliotecas: a fim de proteger de ataques de pré-carregamento de DLL, o Campaign agora carrega as DLLs do Windows somente do caminho padrão de DLL do sistema do Windows ao carregar o Cliente do Campaign (nlclient). [Saiba mais](https://support.microsoft.com/pt-BR/topic/secure-loading-of-libraries-to-prevent-dll-preloading-attacks-d41303ec-0748-9211-f317-2edc819682e1) (NEO-24147)
* Correção de um problema de segurança para reforçar a proteção contra ataques SSRF (Server Side Request Forgery). (NEO-25661)



* Correção de um problema que ocorria ao manipular solicitações de privacidade do RGPD que impedia que registros fossem excluídos de tabelas personalizadas com uma relação de segundo nível com a tabela do recipient. (NEO-25967)



* Correção de um problema de segurança usando chamadas de API feitas por usuários não administradores ao tentar sincronizar modelos do Adobe Experience Manager. (NEO-23487)




**Atualizações de compatibilidade**

Os seguintes sistemas agora são compatíveis com o Campaign:
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Saiba mais na [matriz de compatibilidade do Campaign](../../rn/using/compatibility-matrix.md).

**Recursos obsoletos**

Os seguintes recursos estão obsoletos na versão 20.3:

* O domínio demdex usado para importar e exportar públicos para a Adobe Experience Cloud está obsoleto. Se você estiver usando o domínio demdex para suas contas externas de importação/exportação, será necessário adaptar sua implementação de forma apropriada. [Saiba mais](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* A autenticação da integração dos acionadores originalmente baseada na configuração da autenticação oAUTH para acessar o pipeline agora foi alterada e movida para o Adobe I/O. [Saiba mais](../../integrations/using/configuring-adobe-io.md)

Saiba mais na [página sobre recursos obsoletos e removidos](../../rn/using/deprecated-features.md).

**Aprimoramentos**

* Vários aprimoramentos foram feitos no **console do cliente**:
   * O protocolo de conexão foi atualizado para seguir o novo mecanismo de autenticação IMS. A atualização do console do servidor e do cliente é obrigatória para se conectar após 30 de junho de 2021.
   * Para evitar incompatibilidade com algumas restrições de regras de GPO de segurança da Internet, a tela de logon do console do cliente do Campaign foi substituída por um formulário Windows padrão integrado.
   * Correção de um problema ao copiar/colar atividades em um workflow usando o console do cliente de 64 bits. (NEO-27635)



   * No menu **Sobre** , foram adicionadas informações para distinguir os consoles de 64 e 32 bits.
* O identificador de workflow agora é exibido nos logs ao retomar um workflow, o que permite identificar melhor qual workflow foi retomado.
* Um novo cookie permanente foi introduzido: nllastdelid. Este cookie (diferente de UUID230) armazenará deliveryId. Quando o cookie da sessão não está presente, as informações de broadlog serão obtidas a partir da deliveryId presente neste cookie.
Essa alteração corrige um problema que ocorria quando a sessão do navegador terminava: o cookie de sessão que contém deliveryId e broadlogId foi excluído. Sem o deliveryId, não foi possível encontrar informações de broadlog, e as informações da tabela de rastreamento estariam ausentes no caso de rastreamento permanente (último delivery).
Saiba mais sobre cookies [nesta seção](../../platform/using/privacy-and-recommendations.md#cookies).
* Desempenho de produtividade de delivery de alto volume aprimorado com o servidor de entrega reiniciando o processo MTA antes do envio do delivery.

**Outras alterações**

* Ao usar o caminho relativo para SFTP, os caracteres `~/` não são mais adicionados automaticamente. Se necessário, é possível adicionar caracteres `~/` manualmente ao caminho, mas a Adobe recomenda o uso de um **caminho absoluto**.
* A autenticação do Windows NT foi removida dos métodos de autenticação disponíveis ao configurar um novo banco de dados com um Microsoft SQL Server. [Leia mais](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* O workflow de limpeza do banco de dados foi otimizado para Teradata para melhorar o desempenho. (NEO-19959)



* A mensagem de erro exibida ao inserir uma imagem do Adobe Target foi aprimorada e o nome do locatário estava vazio na conta externa.
* Nas propriedades do delivery, a opção **[!UICONTROL Archive emails]** foi renomeada **[!UICONTROL Email BCC]**.
* Para melhorar a robustez, selectAll queries com nós inválidos agora são rejeitados. Se precisar desativar a verificação e voltar ao comportamento anterior, você pode definir XtkSecurity_Disable_QueryCheck como 0.
* O suporte ao intervalo de ID negativo foi adicionado para a sequência nmsBroadlogId . Esta compilação ajusta o min_value da sequência nmsBroadlogId para incluir o intervalo negativo. Caso tenha um caso de uso estrito que não permita IDs negativas, reverta o min_value da sequência para 1.

**Evoluções técnicas**

O Tomcat foi atualizado da versão 7 (7.0.103) para a versão 8 (8.5.57).

O diretório `tomcat-7` é substituído por um diretório `tomcat-8`.

No Windows, _iis_neolane_setup.vbs_ e _apache_neolane.conf_ agora estão instalados no diretório `conf` (em vez do `tomcat-7/conf` anterior).

No linux, _apache_neolane.conf_ agora está instalado no diretório `conf`.

**Correções**

* Correção de um problema que impedia que estatísticas de delivery fossem recomputadas.
* Correção de um problema que exibia uma mensagem de erro ao fazer upload de um arquivo CSV ao usar a build do Campaign Classic 9080 conectada a um servidor usando uma build mais antiga. (NEO-23218)



* Correção de um problema que poderia exibir uma mensagem de erro ao configurar o assistente do Microsoft Dynamics CRM para uma conta externa. Isso se deve a um problema de compatibilidade com a versão mais recente da API do MS Dynamics CRM. (NEO-24528)
* Correção de um problema que impedia a exportação de registros de tipo de pesquisa (ou seja, dados compostos de registros de chave estrangeira conectados a outras tabelas) do Campaign Classic para o Microsoft Dynamics usando o conector do CRM. (NEO-23864)



* Correção de um problema que impedia a busca de dados do Microsoft Dynamics se a opção **Automatic index** estivesse ativada no conector do CRM. (NEO-25981)



* Correção de um problema com a autenticação IMS que podia deixar as conexões abertas mesmo se tivessem sido encerradas. As conexões terminadas serão automaticamente fechadas assim que terminarem, a fim de evitar o acúmulo de conexões e o consumo de recursos do sistema. (NEO-25996)



* Correção de um problema que não exibia nenhuma mensagem de erro quando a sincronização do conteúdo do Adobe Experience Manager falhava em um delivery devido a uma configuração incorreta da conta externa (conta ou senha incorreta). Uma mensagem agora é exibida em caso de falha, permitindo que você identifique o problema com mais facilidade. (NEO-25586)



* Correção de um problema que ocorria ao selecionar o tipo de operação **Atualizar** na atividade **Atualizar dados**. Se os dados que seriam atualizados estivessem incorretos, o workflow estaria com erro e falharia. Em caso de dados incorretos, o workflow não falhará e os registros serão armazenados em uma transição de saída **Rejeitos**. (NEO-23794)



* Correção de um problema que impedia o funcionamento de workflows contendo subworkflows. (NEO-24036)



* Correção de um problema ao editar uma descrição de template de campanha que impedia a exibição do botão **Salvar** ao copiar símbolos de colagem, como por exemplo, caracteres japoneses. (NEO-27071)



* Correção de um problema que impedia a alteração do servidor de rastreamento no assistente de configuração de instância.
* Correção de um problema que impedia que a descrição de uma campanha ou template de campanha fosse salva ao clicar fora da janela antes de clicar no botão **Salvar**. (NEO-27449)



* Correção de um problema que impedia que o workflow técnico **Número de perfis de faturamento ativos** (billingActiveContactCount) funcionasse. Isso pode acontecer se um link tiver sido executado em um campo calculado em uma extensão de esquema. Uma grande quantidade de dados foi criada, o que pode fazer com que o banco de dados fique temporariamente sem espaço. (NEO-24062)



* Correção de um problema com a **atividade de carregamento de dados (arquivo)**, que poderia impedir a importação de caracteres japoneses a partir de arquivos txt e csv se eles estivessem posicionados no final do arquivo. (NEO-24957)



* Correção de um problema com deliveries contínuos que impedia que os campos **Análise iniciada** e **Análise concluída** fossem preenchidos corretamente. (NEO-20755)



* Correção de um problema que exibia uma mensagem de erro ao tentar a pré-visualização de mensagens SMS após um query em outro esquema que não **Recipient** (nms:recipient). (NEO-27517)



* Correção de um problema ao usar o conector Snowflake FDA. Um usuário com direitos de nome de acesso de Snowflake não pôde executar um query em um esquema Snowflake. Um erro do tipo “Senha não encontrada” foi exibido nos registros. (NEO-23851)



* Correção de um problema ao usar um conector FDA que ocorria quando o nome do esquema FDA vinculado era uma substring do nome de um elemento do esquema atual. Isso ocorria, por exemplo, se o schema FDA fosse “cust” e um dos elementos no esquema do Recipient fosse “customer”. Ao buscar a coluna dentro do elemento “customer” e adicionar uma coluna do esquema”cust” FDA, o valor da coluna local estava ausente. (NEO-20193)



* Correção de um problema em workflows ao buscar registros de um banco de dados externo e inseri-los no banco de dados do Campaign. (NEO-26359)



* Correção de um problema no workflow técnico **Atualizar status do evento**: para corresponder ao dimensionamento dos campos correspondentes recebidos na atividade de **estatísticas de Delivery**, o dimensionamento de três campos de destino na atividade **Atualizar estatísticas de delivery** foi alterado de 32 para 64 bits. (NEO-11557) Saiba mais sobre o workflow **Atualização de status do evento** [nesta seção](../../workflow/using/about-technical-workflows.md).
* Correção de um problema no relatório **Centro de mensagens da história do evento** que causava erros de script ao tentar aplicar filtros e tornava o filtro impossível em um intervalo de datas. (NEO-23365)



* Correção de uma interferência entre os workflows técnicos **trabalhos do Campaign** (operationMgt) e **Pré-visualização** (previsão). Isso ocorria quando os deliveries programados ficavam no status “Pronto para o público alvo” ou “Pronto para ser entregue”. (NEO-20819)



* Correção de um problema de análise XML quando o identificador XML não estava presente no campo mdata em xtkOperator. Estava causando falha após a atualização. (NEO-26113)



* Correção de um problema ao usar a atividade **Transferência de arquivo** vinculada a uma conta externa do Azure criptografada no SSL, onde a conexão era feita com HTTP em vez de HTTPS. (NEO-26720)



* Correção de um problema no banco de dados MSSQL em que um erro ocorria com o procedimento up_updatstats durante o workflow de limpeza.
* Correção de uma falha que ocorria durante o encerramento do processo da web se as solicitações de interação ainda estivessem sendo processadas. (NEO-26447)



* Correção de um problema em que a função **NoNull** no Oracle DB não funcionava mais após a atualização 9032. (NEO-26488)



* Correção de um problema em que o workflow de rastreamento falhava após a atualização 9171 se o pacote LINEV2 fosse instalado sem o pacote do Centro de mensagens.
* Correção de um problema de escalabilidade que impedia que o pool de conexões fosse aumentado para o número desejado de conexões, pois a cadeia de conexão do banco de dados para o atributo “APP” acabava recebendo um valor inválido. (NEO-25105)



* Correção de um problema no nível de configuração de proxy que impedia o logon no Adobe Campaign após a atualização mais recente do Windows 10. (NEO-27813)



* Correção de um problema que tornava os URLs indesejados visíveis nos emails entregues após a importação de modelos HTML contendo links de rastreamento. (NEO-25909)



* Correção de um problema que causava a falha do servidor ao exibir os dados do público alvo do restante de uma atividade **dividida** em um workflow.
* Correção de um problema de falha do servidor, impedindo assim a corrupção da memória ao limpar o analisador de expressão. (NEO-26856)



* Correção de um problema na atividade de enriquecimentos em que usuários não administradores definiam variáveis de instância. (NEO-25653)



* Correção de uma regressão que poderia bloquear a exportação de dados do workflow para um banco de dados FDA (Teradata, Snowflake).

## Versão 20.2{#release-20-2}

### ![](assets/do-not-localize/limited_2.png) Versão 20.2.5 - Build 9188 {#release-20-2-5-build-9188}

_15 de abril de 2021_

* Correção de uma regressão do console do cliente que causava mensagens de erro persistentes na tela de conexão IMS. (NEO-34821)

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!NOTE]
>
> Conecte-se à [Distribuição de software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html) para baixar a nova versão. Saiba como propor a atualização do console para todos os usuários finais [nesta página](../../installation/using/client-console-availability-for-windows.md).

_31 de março de 2021_

**Aprimoramentos**

* Foi feito um aprimoramento para evitar falhas em chamadas soap inválidas. Isso pode fazer com que a instância pare de funcionar ao tentar executar consultas complexas específicas. (NEO-28796, NEO-30553)
* Correção de uma regressão que impedia o envio de deliveries de SMS com TLS devido à verificação do nome de host. (NEO-29581)
* Correção de um problema que impedia que links de rastreamento assinados funcionassem em alguns clientes de email. (NEO-28414, NEO-29615)
* Correção de uma sequência de ID de rastreamento ao usar tags de rastreamento do webApp que poderia causar conflitos com IDs duplicadas. (NEO-27931)
* Correção de um problema que fazia com que workflows em execução fossem interrompidos pela reinicialização diária do wfserver. (NEO-30047)
* Correção de um problema de segurança usando chamadas de API feitas por usuários não administradores ao tentar sincronizar modelos do Adobe Experience Manager. (NEO-32389, NEO-23487)
* Correção de um problema que resultava em falha do console ao fechar uma caixa de diálogo de delivery em um delivery criado com de um template. (NEO-31547)
* Correção de um problema que ocorria ao criar e salvar um delivery no **Direcionamento e fluxo de trabalho** de uma campanha: a pré-visualização falharia com o seguinte erro. (NEO29440)
* Correção de um problema em que o Tomcat 8.5 enviava respostas inválidas que causavam erros nos logs de mensagens transacionais. (NEO-30858)
* Correção de um problema de regressão que causava corrupção da memória no gerenciamento de encadeamento externo e afetava o desempenho.
* Correção de um problema que poderia causar falha no workflow Faturamento ao usar um target mapping personalizado. A chave primária do esquema personalizado é armazenada na coluna &quot;sourceId&quot; que permitia apenas valores inteiros. Agora permite números inteiros e valores de sequências. (NEO-25914, NEO-28146)
* Correção de uma regressão que impedia o uso de alguns componentes do console, como o seletor de datas e o gerenciamento de imagens nos deliveries. (NEO-31453)

### ![](assets/do-not-localize/red_2.png) Versão 20.2.4 - Build 9187 {#release-20-2-4-build-9187}

_15 de abril de 2021_

* Correção de uma regressão do console do cliente que causava mensagens de erro persistentes na tela de conexão IMS. (NEO34821)
* Correção de uma regressão que impedia o uso de alguns componentes do console, como o seletor de datas e o gerenciamento de imagens nos deliveries. (NEO-31453, NEO-31454)

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!NOTE]
>
> Conecte-se à [Distribuição de software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) para baixar a nova versão. Saiba como propor a atualização do console para todos os usuários finais [nesta página](../../installation/using/client-console-availability-for-windows.md).

_22 de dezembro de 2020_

>[!CAUTION]
>
> * Esta versão é fornecida com um novo protocolo de conexão: se você estiver se conectando ao Campaign pelo Serviço de identidade da Adobe (IMS), a atualização será obrigatória para o servidor do Campaign e o console do cliente poderem se conectar ao Campaign após **30 de junho de 2021**.  [Saiba mais](../../technotes/using/ims-updates.md)
> * Esta versão vem com uma [correção de segurança](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): a atualização é obrigatória para reforçar a segurança do ambiente.
> * Se você estiver usando a integração dos acionadores da Experience Cloud por meio da autenticação oAuth, será necessário migrar para o Adobe I/O conforme descrito [nesta página](../../integrations/using/configuring-adobe-io.md). O modo de autenticação oAuth herdado do Campaign [foi removido](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) em **setembro de 2021**. Os ambientes hospedados se beneficiarão de uma extensão até **23 de fevereiro de 2022**. Como cliente local ou híbrido, entre em contato com o Atendimento ao cliente do Adobe para estender o suporte até fevereiro de 2022. Você deve fornecer [o AppID do aplicativo OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) para a Adobe.


**Aprimoramentos**

* O protocolo de conexão foi atualizado para seguir o novo mecanismo de autenticação IMS.
* A autenticação da integração dos acionadores originalmente baseada na configuração da autenticação oAUTH para acessar o pipeline agora foi alterada e movida para o Adobe I/O. [Saiba mais](../../integrations/using/configuring-adobe-io.md)
* Após o [fim do suporte para o protocolo binário herdado APNs do iOS](https://developer.apple.com/news/?id=c88acm2b), todas as instâncias que usam esse protocolo são atualizadas para o protocolo HTTP/2 após a atualização.
* Correção de um problema de segurança para reforçar a proteção contra situações de SSRF (Server Side Request Forgery). (NEO-27777)



* Correção de um problema que resultava na desativação do conector SMPP após um erro de conexão, impedindo o envio de outros deliveries SMS e causando problemas de desempenho. (NEO-28609)



* Correção de um problema de falha do servidor, impedindo assim a corrupção da memória ao limpar o analisador de expressão. (NEO-26856)



* Correção de um problema que causava a falha do servidor ao exibir os dados do público alvo do restante de uma atividade **dividida** em um workflow.
* Correção de um problema que exibia uma mensagem de erro ao tentar a pré-visualização de mensagens SMS após um query em outro esquema que não **Recipient** (nms:recipient). (NEO-27517)



* Correção de um problema ao fazer uma solicitação de conexão HTTPS com o número da porta explicitamente definido no nome do host. A chamada falhou com um erro de certificado. (NEO-29146)



* Correção de um problema no gerenciamento de processos POSIX que gerava arquivos de despejo principais na instância de marketing. (NEO-28117, NEO-29281)
* Correção de problemas que resultavam em falha do processo da web ao preparar deliveries ou com pré-visualizações recorrentes de delivery. (NEO-27790, NEO-27517)
* Correção de um problema que causava a falha de envio de deliveries ou provas quando acionados por um operador não administrador. (NEO-28597)




![](assets/do-not-localize/cp-icon.png) **Nova versão de outubro do Painel de controle do Campaign** com configuração de domínio usando CNAMEs e novos recursos de monitoramento de banco de dados. [Saiba mais](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=pt-BR).

### ![](assets/do-not-localize/red_2.png) Versão 20.2.3 - Build 9182 {#release-20-2-3-build-9182}

_11 de setembro de 2020_

* Correção de uma regressão que causava o bloqueio da preparação do delivery devido a uma única função incorreta na parte do delivery, resultando em sobrecarga da memória. (NEO-27346)



* Correção de um problema de pós-atualização que desativava o Apache e o servidor da web antes da republicação do aplicativo web. (NEO-27155)



* Correção de uma regressão no gerenciamento de template de HTML que resultava na visibilidade de URLs de rastreamento devido a uma interpretação incorreta de guias. (NEO-25909)



* Correção de um problema com o workflow de limpeza do banco de dados que poderia falhar devido à fonte de dados não gerenciada. (NEO-23160, NEO-23364)
* O workflow de limpeza agora limpa listas expiradas por lotes de 100 em vez de uma a uma.
* Correção de uma regressão que impedia a modificação do nome interno de uma conta externa. (NEO-27323)



* Correção de uma regressão durante a pós-atualização, causando um início incorreto do nlserver (logs de erros).
* O gerenciamento de atualizações da memória compartilhada foi aprimorado. As etapas adicionais necessárias na versão 20.2 não são mais necessárias.

### ![](assets/do-not-localize/red_2.png) Versão 20.2.2 - Build 9180 {#release-20-2-2-build-9180}

_22 de julho de 2020_

* Correção de um problema que impedia o funcionamento do rastreamento quando o recurso de assinatura era desativado. (NEO-26411)
* Correção de um problema que resultava no bloqueio de links não assinados de domínios personalizados quando deveriam ser permitidos. (NEO-25210)
* Correção de um problema que poderia impedir a abertura/clique de URLs de rastreamento ao usar determinadas versões herdadas do Outlook. (NEO-25688)
* Correção de um problema que resultava na definição incorreta de URLs de mirror page em delivery de email (devido ao controle de caracteres ASCII incorreto). (NEO-26084)
* Correção de um problema com a codificação do gerenciamento de URL no serviço anti-phishing. (NEO-25283)
* Correção de um problema que impedia o funcionamento do rastreamento de URLs usando fragmentos em parâmetros de personalização (tags de âncora com sinal de hashtag). (NEO-25774)
* Correção de um problema de rastreamento ao usar fórmulas de rastreamento personalizadas específicas. (NEO-25277)




* Correção de um problema que impedia o funcionamento do rastreamento de &quot;cliques de notificação&quot; (notificações por push de iOS e Android). (NEO-25965)
* Correção de uma regressão que afetava os campos calculados em um workflow, causando falha no workflow. (NEO-25194)
* Correção de uma regressão que impedia o funcionamento da criação instantânea de URLs de rastreamento da web. (NEO-20999)
* Correção de um problema de regressão com relatórios do delivery de utilização imediata que apareciam cortados quando exportados para PDF. (NEO-25757)
* Correção de uma falha no assistente de implantação.
* Correção de um problema que impedia que o workflow de notificação de oferta funcionasse corretamente após uma pós-atualização.
* O conector HTTP2 para iOS foi aprimorado (atualizações de terceiros e gerenciamento de erros). (NEO-25904, NEO-25903)
* A lista jarsToSkip em catalina.properties foi atualizada para remover a referência a um arquivo jar que não é mais utilizado (notificações do iOS).
* Correção de um problema que bloqueava a preparação do delivery após a atualização.
* Após a mudança para o novo mecanismo de ID de sequência, todos os aplicativos da web que estão atualizando a tabela do recipient são republicados durante a pós-atualização.
* Correção de uma possível vulnerabilidade XSS no conteúdo do delivery. (NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) **Nova versão de junho do Painel de controle do Campaign** com monitoramento de perfis ativos, auditoria de entregabilidade de subdomínio e gerenciamento de chaves GPG. [Saiba mais](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html).

### ![](assets/do-not-localize/red_2.png) Versão 20.2.1 - Build 9178 {#release-20-2-1-build-9178}

_8 de junho de 2020_

**Novidades**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Suporte a emoticons</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Ao projetar uma mensagem no Campaign, agora é possível inserir emoticons facilmente no corpo da mensagem, usando um botão dedicado. Eles também podem ser adicionados na linha de assunto do email. Você pode personalizar a lista de emoticons disponíveis na interface.</p>
    <p>Para obter mais informações sobre como adicionar emoticons, consulte a <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">documentação detalhada</a>. Saiba como personalizar a lista de emoticons <a href="../../delivery/using/customizing-emoticon-list.md">nesta seção</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Conector do Azure Synapse FDA</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Agora você pode conectar sua instância do Campaign ao banco de dados externo do Azure Synapse. Essa conexão é gerenciada por meio de uma nova conta externa.</p>
    <p>O Azure Synapse só está disponível para ambientes híbridos e no local. Para obter mais informações, consulte a <a href="../../installation/using/configure-fda-synapse.md">documentação detalhada</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Leis de privacidade da Tailândia e do Brasil</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>A PDPA (Personal Data Protection Act, Lei de Proteção de Dados Pessoais) da Tailândia é a nova lei de privacidade que harmoniza e moderniza os requisitos de proteção de dados da Tailândia. </p>
   <p>A Lei Geral de Proteção de Dados (LGPD) do Brasil entrará em vigor a partir do início de 2021 para todas as empresas que coletam ou processam dados pessoais no Brasil.</p>
   <p>Esses regulamentos aplicam-se aos clientes do Adobe Campaign que coletam dados de residentes nesses países. Além dos recursos de privacidade já disponíveis no Campaign (incluindo o gerenciamento de consentimento, as configurações de retenção de dados e as funções de usuários), aproveitamos a oportunidade para incluir recursos adicionais que ajudam a estar de acordo com a PDPA e a LGPD:</p>
   <ul> 
     <li><p>Direito de acesso e direito de exclusão: estamos nos beneficiando dos recursos que foram adicionadas para o GDPR e a CCPA. <a href="https://helpx.adobe.com/br/campaign/kb/acc-privacy.html">Leia mais</a></p></li> 
     <li> <p>Ao criar uma solicitação de privacidade usando a interface ou a API do Adobe Campaign, agora você seleciona o tipo de <strong>regulamento</strong>: PDPA, LGPD, GDPR, CCPA. <a href="https://helpx.adobe.com/br/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">Leia mais</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Aprimoramentos de segurança**

* A segurança aprimorada no rastreamento de links no email é ativada por padrão para todos os clientes. Um recurso de segurança adicional e aprimorado está disponível e pode ser ativado ao acessar o Atendimento ao cliente. Mais detalhes sobre o recurso e as etapas para clientes não hospedados para habilitá-lo podem ser encontrados na [lista de verificação de Segurança e Privacidade](https://helpx.adobe.com/br/campaign/kb/acc-security.html). (NEO-24232)

* Para otimizar a segurança, o algoritmo de hash MD5 usado para gerar nomes de arquivos foi reforçado com sha256 para upload de arquivos públicos. (NEO-17044)

* Para reforçar a segurança contra ataques XSS, os scripts do lado do cliente são desativados ao executar uma mirror page. (NEO-17987)

* Correção de um problema que impedia que o workflow técnico de **Limpeza de solicitação de privacidade** excluísse os dados de reconciliação. (NEO-25168, NEO-21004)

* Correção de um problema com a atividade **Transferência de Arquivo**, que impedia que a autenticação com a chave SFTP funcionasse no Debian 9. (NEO-23183)

**Aprimoramentos de compatibilidade**

Os seguintes sistemas agora são compatíveis com o Campaign:
* Sistemas operacionais: Debian 10
* RDBMS: Oracle 18c e Oracle 19c
* FDA: Azure Synapse Analytics

Saiba mais na [matriz de compatibilidade do Campaign](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html).

**Aprimoramentos**

* As mensagens transacionais foram aprimoradas para melhorar a experiência do usuário. Agora é possível desfazer a publicação de um template de mensagem transacional, o que o exclui das instâncias de execução. [Saiba mais](../../message-center/using/publishing-message-templates.md#template-unpublication).

* Há novas opções disponíveis para definir limitações ao enviar emails com imagens ou anexos. Essas grades de proteção podem evitar problemas de desempenho, o que é particularmente útil com mensagens transacionais. [Leia mais](../../installation/using/configuring-campaign-options.md#delivery)

* A nova opção **Preparar as partes do delivery no banco de dados** possibilita executar a preparação do delivery diretamente no banco de dados, o que pode acelerar bastante a análise. Essa opção só está disponível para configurações específicas. [Saiba mais](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* O desempenho da [Atividade do conector de CRM](../../workflow/using/crm-connector.md) para Microsoft Dynamics foi aprimorado. (NEO-13303, NEO-12710)

* A versão da memória compartilhada foi aumentada.

   >[!WARNING]
   >
   >Essa melhoria requer uma etapa adicional após a execução da atualização. Consulte a seção **Evoluções técnicas** abaixo.

* O fluxo de trabalho de limpeza foi aprimorado. As tabelas de trabalho órfãs de todos os workflows excluídos agora também são excluídas automaticamente pelo fluxo de trabalho de limpeza. [Saiba mais](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Certificados para aplicativos móveis iOS com o conector HTTP2 do iOS agora são validados antes do envio de notificações por push, evitando que os deliveries falhem devido a certificados expirados.

* O gerenciamento de conexões proxy HTTP foi aprimorado. [Saiba mais](../../installation/using/file-res-management.md).

* Nova opção nas atividade de workflow **[!UICONTROL Javascript Code]** e **[!UICONTROL Advanced Javascript Code]** para interromper a execução após um limite. O valor padrão é 1 hora. [Saiba mais](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

**Outras alterações**

* Conectores SMS herdados agora estão obsoletos. Consulte a [página de recursos obsoletos](../../rn/using/deprecated-features.md).

* Você não pode mais usar sua própria conta Litmus para provisionar e usar a renderização da caixa de entrada no Adobe Campaign. [Saiba mais](../../delivery/using/inbox-rendering.md).

* Para distinguir melhor as visualizações das pastas, a cor dos nomes das visualizações foi alterada de azul escuro para ciano escuro. [Leia mais](../../platform/using/access-management-folders.md)

* O Campaign Classic agora pode ser conectado a contas do Microsoft Dynamics CRM hospedadas nas regiões do Reino Unido, Índia e Canadá. Isso se aplica aos tipos de implantação do Office 365 e no local (Dynamics 2015).

* O Campaign agora executa uma verificação TLS para verificar se o nome do host do servidor corresponde ao nome do host no certificado fornecido.

* A tabela de estatísticas de delivery e rastreamento agora exibe uma entrada por delivery para o canal SMS, em vez de uma entrada por recipient de delivery.

* Adição de uma mensagem de erro no arquivo de log para avisar os usuários quando o arquivo baixado for maior que o espaço em disco.

* As seguintes funções estão disponíveis para o conector Snowflake: MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**Evoluções técnicas**

Esta nova build atualiza a memória compartilhada e requer etapas adicionais para executar a atualização. Como administrador do Campaign, é necessário remover segmentos de memória. Essas etapas são obrigatórias, pois os segmentos antigos impedirão que nlserver/nlsrvmod seja iniciado.

No Windows, é necessário reiniciar o sistema.

No Debian/CentOs, é preciso excluir a memória compartilhada. Estas são as etapas:

Antes da atualização, você precisa seguir estas etapas:

1. Pare o serviço apache2 (http2 no CentOS) se ele estiver em execução.
1. Pare o serviço nlserver (nlserver6 para builds mais antigas) se ele estiver em execução.

Após a atualização:

1. Remova a memória compartilhada usando o comando **ipcrm**, se a versão for anterior à versão atual.
1. Inicie o serviço nlserver se ele estava em execução.
1. Inicie o serviço apache2 se ele estava em execução.

Estas são as linhas de comando para Debian:

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Um exemplo para Linux está disponível nesta [página](../../configuration/using/additional-parameters.md#redirection-server-configuration).

**Correções**

* Correção de uma regressão menor nos logs de workflow de limpeza.
* Correção de um problema na atividade **Loading (SOAP)** do fluxo de trabalho ao analisar arquivos WSDL.
* Correção de um problema que causava um erro ao atualizar vários fluxos de trabalho usando uma atividade de **Pesquisa** para processar com eficiência um número alto de fluxos de trabalho.
* Correção de um problema intermitente de conectividade durante o processamento de mensagens do InMail do MTA aprimorado. (NEO-20380)
* Correção de um problema que impedia que as porcentagens de cliques ativos fossem exibidas corretamente quando as imagens eram exibidas com 100% de largura no HTML. (NEO-23203)
* Correção de um problema que impedia que o conteúdo condicional do delivery fosse totalmente exibido no relatório de cliques ativos. (NEO-18729)
* Correção de um problema que ignorava a etapa de aprovação do público-alvo ao retomar um fluxo de trabalho para enviar um delivery recorrente. (NEO-18166)
* Correção de um problema que impedia que o botão **Reiniciar a preparação da mensagem** retomasse o delivery após corrigir um erro no fluxo de trabalho. (NEO-13488)
* Correção de um problema que resultava em falha de delivery no modo mid-sourcing durante a fase de inicialização, onde o público-alvo incluía recipients com formatos de email japoneses. (NEO-23846)
* Correção de um problema de conversão de fuso horário com o Snowflake Connector (NEO-20105)
* Correção de um problema com a conta externa que usa o FTP sobre SSL. (NEO-20498)
* Correção de um problema que impedia a exibição de imagens na entrega de linha. (NEO-23207)
* Correção de um problema que causava um erro ao publicar uma oferta. (NEO-23312)
* Correção de um problema com notificações por push que permitiam que conexões de teste funcionassem em aplicativos móveis, mesmo quando o certificado expirava. (NEO-22991)
* Correção de um problema que poderia afetar a notificação por push quando enviada em alta frequência. (NEO-20516)
* Correção de um problema que fazia com que os dados de rastreamento incluíssem duplicidades, mesmo se os logs de rastreamento não incluíssem. (NEO-20040)
* Correção de um problema que fazia com que emails transacionais duplicados fossem enviados após uma falha de comunicação do servidor de rastreamento ser corrigida. (NEO-23640)
* Correção de um problema que excluía o valor do parâmetro de codificação ao redirecionar a partir de um URL de rastreamento (impacto nos caracteres japoneses). (NEO-25637)
* Correção de um problema que impedia que uma consulta funcionasse ao comparar números flutuantes. (NEO-23243)
* Correção de um problema que impedia a exibição do conteúdo da coluna **Modificado por** após reiniciar um fluxo de trabalho. (NEO-23035)
* Correção de um problema que causava falha do fluxo de trabalho técnico de rastreamento ao baixar registros de um segundo container. (NEO-23159)
* Correção de um problema que resultava em falha em fluxos de trabalho ao executar uma atividade de **Enriquecimento**. (NEO-17338)
* Uma verificação foi adicionada ao campo **Duplos a manter** na atividade de fluxo de trabalho **Desduplicação** para evitar a inserção de valores nulos ou negativos.
* Remoção do **Assistente de scheduler** das campanhas recorrentes para evitar mencionar horas e minutos. Somente datas são consideradas.
* Correção de um problema com campos de armazenamento adicionais ao criar deliveries por meio da opção **Calculado por um script** na atividade do fluxo de trabalho **Script**. (NEO-20609)
* Correção de um problema que impedia que fluxos de trabalho fantasmas fossem excluídos nas tarefas de limpeza do banco de dados.
* Correção de um problema que causava a falha do fluxo de trabalho técnico **Faturamento (perfis ativos)**. (NEO-19777)
* Correção de um problema de regressão ao usar o recurso Conector de ACS que impedia a conexão com uma instância do Campaign Standard (gerenciamento incorreto da conexão FOH/FOH2). (NEO-23433)
* Correção de um problema que impedia a criação de uma extensão de schema em uma chave primária com várias colunas com uma tabela Hadoop. (NEO-17390)
* Correção de um problema na atividade **Loading (SOAP)** que poderia impedir que arquivos WSDL fossem carregados de um URL. (NEO-16924)
* Correção de um problema que impedia a execução de uma **parada incondicional** pelo console quando vários servidores de fluxo de trabalho ativos eram balanceados de carga. (NEO-19556)
* Correção de uma regressão que resulta em falha do workflow de limpeza.
* Correção de um problema que poderia ocorrer ao publicar um template em uma instância de execução.
* Correção de um problema que poderia impedir a execução do workflow técnico collectPrivacyRequests. (NEO-20513, NEO-25169)
* Correção de problemas que poderiam ocorrer ao tentar se conectar ao Audience Manager após a atualização para a build 9080. (NEO-20511, NEO-25167)
* Correção de problemas que poderiam ocorrer ao exportar relatórios nos formatos PDF ou XLS. (20982, NEO-, NEO-23493, NEO-23348)
* Correção de um problema que poderia exibir um delivery duas vezes na lista de delivery após ele ser enviado.
* Correção de um problema com a preparação do delivery que poderia ocorrer quando a configuração do roteamento estava definida para enviar o delivery via mid-sourcing.
* Correção de um problema que poderia exibir uma mensagem de erro ao clicar em um link de aplicativo da Web em uma mensagem do LINE.
* Correção de um problema que excluía o histórico de atividades de **Query incremental** após a execução do fluxo de trabalho de limpeza.
* Correção de um problema ao criar uma conta externa de mid-sourcing em que a opção NmsMidSourcing_LastBroadLog_&lt;InternalName> estava ausente.
* Correção de um problema de regressão na conexão do banco de dados, provocando a reinicialização constante do servidor da web devido a um problema de codificação do banco de dados. As reinicializações poderiam causar um consumo excessivo. (NEO-23264)





## Versão 20.1{#release-20-1}

### ![](assets/do-not-localize/limited_2.png) Versão 20.1.4 - Build 9126 {#release-20-1-4-build-9126}

_15 de abril de 2021_

* Correção de uma regressão do console do cliente que causava mensagens de erro persistentes na tela de conexão IMS. (NEO34821)

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!NOTE]
>
> Conecte-se à [Distribuição de software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) para baixar a nova versão. Saiba como propor a atualização do console para todos os usuários finais [nesta página](../../installation/using/client-console-availability-for-windows.md).

_22 de março de 2021_

* Correção de uma regressão que impedia o uso de alguns componentes do console, como o seletor de datas e o gerenciamento de imagens nos deliveries. (NEO31453, NEO31454)

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!NOTE]
>
> Conecte-se à [Distribuição de software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) para baixar a nova versão. Saiba como propor a atualização do console para todos os usuários finais [nesta página](../../installation/using/client-console-availability-for-windows.md).

_23 de dezembro de 2020_

>[!CAUTION]
>
> * Esta versão é fornecida com um novo protocolo de conexão: se você estiver se conectando ao Campaign pelo Serviço de identidade da Adobe (IMS), a atualização será obrigatória para o servidor do Campaign e o console do cliente poderem se conectar ao Campaign após **30 de junho de 2021**. [Saiba mais](../../technotes/using/ims-updates.md)
>
> * Esta versão vem com uma [correção de segurança](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): a atualização é obrigatória para reforçar a segurança do ambiente.


* O protocolo de conexão foi atualizado para seguir o novo mecanismo de autenticação IMS.
* Correção de um problema de segurança para reforçar a proteção contra situações de SSRF (Server Side Request Forgery). (NEO-27777)




### ![](assets/do-not-localize/red_2.png) Versão 20.1.3 - Build 9124{#release-20-1-3-build-9124}

_6 de maio de 2020_

* Correção de um problema com a atividade **Transferência de Arquivo**, que impedia que a autenticação com a chave SFTP funcionasse no Debian 9. (NEO23183)

### ![](assets/do-not-localize/red_2.png) Versão 20.1.2 - Build 9123{#release-20-1-2-build-9123}

_13 de março de 2020_

* Correção de um problema que impedia a implantação da versão em servidores Red Hat 7. (NEO-23332)

### ![](assets/do-not-localize/red_2.png) Versão 20.1 - Build 9122{#release-20-1-build-9122}

_17 de fevereiro de 2020_

**Novidades**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Conector Snowflake FDA</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>O Snowflake é um data warehouse de nuvem totalmente gerenciado, criado para dimensionar tanto no nível de armazenamento quanto no nível de computação. Com esse novo conector, o Adobe Campaign agora pode aproveitar o potencial do Snowflake para executar a Segmentação de Big Data. Esse conector está disponível para todos os clientes, inclusive hospedado pela Adobe.</p>
    <p>Para obter mais informações, consulte a <a href="../../installation/using/configure-fda-snowflake.md">documentação detalhada</a> e o <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">vídeo tutorial</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Aprimoramentos do conector FDA Hadoop</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>O conector FDA Hadoop foi aprimorado para oferecer suporte ao Hadoop 3.0 e à Cloudera.</p>
    <p>Para obter mais informações, consulte a <a href="../../installation/using/configure-fda-hadoop.md">documentação detalhada</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Aprimoramentos de segurança**

* Segurança aprimorada na configuração do relatório para proteger contra clickjacking. Isso se aplica aos novos relatórios. Para relatórios antigos, é necessário republicá-los para aplicar as alterações. (NEO-13282)

* Correção de um pequeno problema de memória no cryptString. (NEO-20071)

* JSP do monitor aprimorado para corrigir uma divulgação interna de IP. (NEO-16821)

* Correção de um problema em que as informações de rastreamento de pilha podiam ser exibidas para usuários não administradores. (NEO-12388)

* Gerenciamento de dados em cache aprimorado de sessões anteriores. (NEO-17039)

* Correção de um problema que impedia o arquivo logins.log de registrar tentativas de login bem-sucedidas por meio do IMS. (NEO-11004)

**Aprimoramentos**

* O iOS 13 agora é compatível com o conector HTTP2.

* Gerenciamento de quarentena e limpeza aprimorados das tabelas usadas pelo recurso de notificação por push (nms:address e nms:appSubscriptionRcp). No iOS (somente conector HTTP2), os tokens desativados agora são manipulados da mesma forma que no Android. O sinalizador disable agora está definido na tabela NmsAppSubscriptionRcp. [Leia mais](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Uma nova opção foi adicionada ao **código JavaScript** e às atividades de workflow do **código JavaScript avançado** para definir um período de tempo limite. Isso impede que a fase de execução do JavaScript seja executada por muito tempo. Se o período limite expirar, o workflow será interrompido. O tempo limite padrão é de 1 hora. [Leia mais](../../workflow/using/sql-code-and-javascript-code.md)

* A análise do delivery agora é interrompida quando nenhuma afinidade correspondente é encontrada no servidor mid-sourcing, com a mensagem de erro correspondente sendo exibida.

* Agora há suporte para failover de banco de dados para Postgres: quando o servidor de banco de dados trava e reinicia, o Campaign agora se reconecta automaticamente a ele.

* A visualização **Start Pending** foi adicionada ao nó Administration > Audit > Workflows Status. Isso permite que você monitore todos os workflows na sua instância que estão aguardando para serem iniciados pelo processo **operationMgt**. Esta visualização vem com o pacote de campanhas de marketing. [Leia mais](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Outras alterações**

* No Linux, a inicialização do serviço nlserver agora usa uma unidade sistêmica em vez do script /etc/init.d/nlserver6. A migração para o novo schema de inicialização é executada automaticamente ao instalar o pacote 20.1. O /etc/init.d/nlserver6 ainda é fornecido, mas para interagir com o serviço nlserver (start, reinicialização, interrupção etc.), recomendamos que você use o comando systemctl diretamente.

* As tabelas personalizadas mais trabalhosas foram movidas da sequência **xtkNewId** para sequências dedicadas.

* Melhora do desempenho do query que pode ser afetado por conexões desnecessárias ao banco de dados.

* O desempenho do assistente de atualização de banco de dados foi aprimorado para realizar menos declarações SQL a fim de otimizar o tempo de resposta.

* O gerenciamento dos registros do banco de dados foi aprimorado.

* A robustez do pool de conexões foi aprimorada, o que pode impedir que falhas inesperadas de conexão ocorram com muita frequência.

* As regras de validação de endereço de email para enviar um endereço para a quarentena em caso de erro de software foram aprimoradas. [Leia mais](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Para Debian, o Campaign agora usa bibliotecas PCRE do sistema quando elas estão disponíveis.

* O Campaign agora permite o uso de uma biblioteca ODBC do sistema mais recente.

* Adicionamos um tempo limite ao servlet LINE quando uma conexão para carregar uma imagem avançada é aberta. Se a imagem estiver demorando muito para carregar, o servlet interrompe a conexão para evitar um gargalo.

**Correções**

* Correção de um problema de criptografia de chave da conta ao usar o conector do Hadoop.

* Correção de um problema de regressão devido à implementação da certificação SSL que causava a falha da conexão do usuário no servidor Windows. (NEO-20629)

* Correção de um problema com a atividade de query incremental no caso de IDs de workflow negativas. (NEO-19779)

* Correção de um problema de codificação ao executar os queries por meio do conector FDA Netezza. (NEO-19594)

* Correção de um problema que resulta em erro ao usar o método POST na atividade de evento do workflow **Download da Web**

* Correção de um problema com a criação da apresentação da oferta. (NEO-18176)

* Correção de um problema de exibição do rodapé ao usar o modelo de formulário da Web de aquisição.

* Correção de um problema ao analisar os URLs no conteúdo de deliveries contínuos que causa falhas. (NEO-16910)

* Correção de um problema onde os campos **Start** e **End** não são computados ao criar uma nova campanha.

* Correção de um problema com a atividade de workflow **Download de arquivo** ao usar um URL.

* Correção de um problema ao visualizar uma lista importada em uma atividade de consulta de um relatório. (NEO-13119)

* Correção de um problema que exibia uma imagem desatualizada ao selecionar o bloco de personalização **Powered by Campaign** no editor de email.

* A comunicação de rede entre o cliente e o servidor foi aprimorada.

* Correção de um problema em que muitos workflows eram criados na mesma campanha. Agora, você não pode criar mais de 28 workflows. Um aviso é exibido.

* Correção de um problema ao usar a opção **Uma seleção de reconciliação de colunas** em uma atividade de workflow **Union**.

* Correção de um problema de travamento do console que ocorria ao usar uma lista de enriquecimento corrompida em um workflow. (NEO-18096)

* Correção de vários problemas de travamento do console que podem ocorrer em workflows (NEO-18010, NEO-18032)

* Correção de um problema que permite a execução de uma atividade de workflow **External Signal** mesmo quando ela está desativada. (NEO-17524)

* Correção de um problema ao criar um novo schema.

* Correção de um problema de rastreamento ao enviar mensagens SMS. (NEO-19595)

* Correção de um problema que exibe números incorretos do público direcionado em indicadores de entrega.

* Correção de um problema que exibe porcentagens incorretas ao gerar um relatório descritivo por meio de uma atividade de workflow. (NEO-14314)

* Correção de um problema que faz com que o relatório de taxa de transferência do delivery apresente números diferentes quando o parâmetro de visualização de tempo é utilizado. (NEO-11783)

* Correção de um problema que impede a atualização dos indicadores de rastreamento de mensagens transacionais pelo workflow Tracking. (NEO-17770)

* Correção de um problema de regressão que resulta na falha e reinicialização do processo da Web ao solicitar uma oferta por meio do SOAP. (NEO-19482)

* Correção de um problema que impede o upload de dados para recursos públicos se o diretório estiver em um local compartilhado remoto. (NEO-19361)

* Correção de um problema que causa a falha constante do workflow técnico **Import audiences from the Adobe Experience Cloud**. (NEO-18463)

* Correção de um problema que impede o envio do delivery ao usar os modelos importados do Experience Manager. (NEO-17540)

* Correção de um problema que ocorre após a atualização para a build 9032 e impede a instância de se conectar ao servidor FTP pelo protocolo SSL. (NEO20498)

* Correção de um problema que ocorre ao excluir, inserir ou atualizar uma grande quantidade de dados com a atividade **Update data** em um workflow que usa um schema FDA como dimensão de direcionamento. (NEO-13280)

* Correção de um problema que impedia o envio de emails quando um código Javascript estivesse fora da tag de conteúdo HTML. (NEO-18628)

* Correção de um problema que ocorre ao tentar exibir a mirror page dos logs do delivery de uma mensagem enviada. (NEO-17976)

* Correção de um problema que impede que o bloco de personalização **Link to mirror page** seja exibido na guia **Text content** depois de clicar em **Import HTML** de uma delivery. (NEO-17568)

* A mensagem de erro que é exibida ao clicar em um link para uma mirror page que expirou foi esclarecida. (NEO-17340)

* Correção de um problema que impede que alguns botões sejam usados na tela de criação **Data distribution**.

* Correção de um problema que ocorre ao agendar uma atividade de delivery em uma instância com Ásia/Calcutá como fuso horário. (NEO-20001)

* Um erro agora é exibido quando um delivery tem um problema de configuração de afinidade.

* Correção de um problema que exibia um número de tag de versão incorreto no menu **About**.

* Correção de um problema que ocorre ao tentar atualizar a conta do roteamento a partir de propriedades de delivery que são recorrentes em um workflow. (NEO-18684)

* Correção de um problema que ocorre ao conectar-se à instância por meio do módulo de redirecionamento, que impedia que a conexão fosse limpa corretamente depois de fechada.
