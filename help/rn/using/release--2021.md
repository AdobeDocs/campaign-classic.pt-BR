---
product: campaign
title: Versões do Campaign Classic 2021
description: Saiba mais sobre as atualizações do Campaign Classic 2021
feature: Overview
role: User
level: Beginner
exl-id: 0cd6bf20-da72-4cf0-9f5d-d4e8acdd324d
source-git-commit: 1e2c20befebf2343cb0f781aa7f2bd1ed6b3f383
workflow-type: tm+mt
source-wordcount: '2540'
ht-degree: 100%

---

# Versões de 2021{#release-2021}

## Versão 7.1 (21.1)

>[!CAUTION]
>Use o menu **[!UICONTROL Help > About...]** para verificar sua [versão e número de build](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) do Adobe Campaign. No entanto, observe que para todas as builds entre 9277 e 9343 listadas nesta página, o número da versão mostra 7.0 em vez de 7.1.

### ![](assets/do-not-localize/limited_2.png) Versão 21.1.4 – Build 9343 {#release-21-1-4-build-9343}

_8 de outubro de 2021_

**Correções**

* Correção do fluxo de trabalho de faturamento disponível na build 9342, que requer uma reinicialização manual do fluxo de trabalho para que a correção seja aplicada. Agora, a pós-atualização reinicia automaticamente o fluxo de trabalho.

* Correção de um problema que podia impedir o gerenciamento adequado de ofertas ao usar o módulo **Interaction** com a opção [Power Booster](../../installation/using/power-booster-and-power-cluster.md). (NEO-39263)

* Correção do erro “A afinidade de IP xxx não foi encontrada no mid server xxx” que podia ocorrer no envio de um delivery ao usar mais de uma afinidade de IP em uma instância de multi mid-sourcing. (NEO-37514)

### ![](assets/do-not-localize/limited_2.png) Versão 21.1.4 – Build 9342 {#release-21-1-4-build-9342}

_7 de setembro de 2021_

**Aprimoramento de segurança**

* Correção de um problema de segurança para reforçar a proteção contra ataques de travessia de diretórios. (NEO-28547)

**Aprimoramentos**

* Após o fim da vida útil, o Flash foi removido de todos os recursos e componentes relacionados do Campaign e substituído pelo HTML5. O tipo de gráfico **Medição** foi removido. (NEO-30330) [Leia mais](../../reporting/using/creating-a-chart.md)
* Ao instalar o console do cliente no Windows, o instalador agora verifica se há um nó de registro pai e cria um se estiver ausente. Isso evita possíveis problemas ao iniciar o console. (NEO-34854)
* O recurso de assinatura de rastreamento foi aprimorado para evitar erros vinculados à forma como as ferramentas de terceiros (clientes de email, navegadores de Internet etc.) lidam com caracteres especiais. Os parâmetros de URL agora são codificados.

**Outras alterações**

* Correção de uma regressão introduzida na versão 21.1.3 com a nova garantia do fluxo de trabalho de faturamento. O fluxo de trabalho de faturamento foi executado em instâncias erradas e falhou ao tentar enviar o relatório de faturamento, que não foi gerado. É necessário reiniciar manualmente o fluxo de trabalho para que a correção seja aplicada.
* Os conectores do Microsoft CRM obsoletos anteriormente (implantações do Office 365 e no local) foram removidos da interface. [Leia mais](../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft)
* Após a migração para o Tomcat 8, o script de configuração do IIS foi atualizado para corrigir problemas de integração do IIS. (NEO-31019)
* A identificação da fonte de dados foi aprimorada nas guias de dados e esquema da janela **Exibir população** das transições do fluxo de trabalho.
* Os índices de banco de dados ausentes foram adicionados aos seguintes esquemas para evitar problemas de atualização do banco de dados: xtk:rights, nms:dlvExclusion, nms:seedMember, nms:trackingUrl

**Correções**

* Correção de um problema que impedia o funcionamento do relatório Hot clicks quando as ofertas eram vinculadas à entrega. (NEO-26295)
* Correção de um problema com a atividade **Sub-workflow** quando sua execução não gerava uma tabela de saída. (NEO-36242)
* Correção de vários problemas ao exportar o relatório de **Análise descritiva** para PDF. (NEO-25847)
* Correção de um problema que poderia resultar em falha de entrega ao usar uma entrega de email externa. (NEO-37435)
* Correção de um erro ao se conectar ao Microsoft CRM usando a API da Web. A mensagem de erro foi removida, pois as funcionalidades não foram afetadas.
* Correção de um problema de desduplicação de log de rastreamento quando o servidor mid era definido como uma retransmissão entre servidores de rastreamento e de marketing. (NEO-36285)
* Correção de uma regressão que impedia o Cofre de ser usado como um armazenamento de código específico.
* Correção de um problema que impedia o uso de variáveis em uma atividade de fluxo de trabalho de **Enriquecimento** quando a transição recebida era de uma fonte de dados FDA.
* Correção de um problema que poderia resultar em URLs inválidos em mensagens de email.

### ![](assets/do-not-localize/limited_2.png) Versão 21.1.3 – Build 9330 {#release-21-1-3-build-9330}

_5 de junho de 2021_

**Novidades**


<table>
<thead>
<tr>
<th><strong>Nova atividade de fluxo de trabalho: Alterar fonte de dados</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>A nova atividade de fluxo de trabalho <b>Alterar fonte de dados</b> permite alterar a fonte de dados de uma tabela de trabalho do fluxo de trabalho. Isso proporciona mais flexibilidade no gerenciamento de dados em diferentes fontes de dados (FDA e banco de dados local).</p>
<p>Nos workflows do Adobe Campaign, os dados são gerenciados usando tabelas de trabalho (ou temporárias). Conforme o fluxo de trabalho é executado, as tabelas de trabalho compartilham dados entre atividades de fluxo de trabalho. Por padrão, as tabelas de trabalho são criadas no mesmo banco de dados da fonte de dados que consultamos.</p>
<p>Para obter mais informações, consulte a <a href="../../workflow/using/change-data-source.md">documentação detalhada</a>.</p>
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th><strong>Integração com o Adobe Journey Orchestration</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>A integração entre o Journey Orchestration e o Adobe Campaign Classic agora está disponível. Ela permite que o Journey Orchestration envie emails, notificações por push e SMS usando recursos de mensagens transacionais do Adobe Campaign Classic.</p>
<p>A conexão entre as instâncias do Journey Orchestration e do Campaign Classic é configurada pela Adobe no momento do provisionamento.</p>
<p>Para obter mais informações, consulte a <a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=pt-BR">documentação do Journey Orchestration</a>. Um caso de uso passo a passo é apresentado nesta <a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=pt-BR">seção</a></p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>Melhorias do canal LINE</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>As seguintes melhorias foram adicionadas ao canal LINE:
</p>
<ul> 
<li><p>Suporte para tipo de mensagem de vídeo LINE</p></li>
<li><p>Suporte para API de registro de parceiro LINE</p></li>
<li><p>Suporte para nova tentativa de envio de mensagem em caso de erro do lado do servidor LINE ou tempo limite da rede</p></li>
</ul>
<p>Para obter mais informações consulte a <a href="../../delivery/using/line-channel.md">documentação detalhada</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Conector Vertica FDA</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Agora é possível conectar a instância do Adobe Campaign Classic ao banco de dados externo da Vertica. Essa conexão é gerenciada por meio de uma nova conta externa.</p>
<p>Para obter mais informações consulte a <a href="../../installation/using/configure-fda-vertica.md">documentação detalhada</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Conector FDA do Google BigQuery</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Agora é possível conectar sua instância do Adobe Campaign Classic ao banco de dados externo do Google Big Query. Essa conexão é gerenciada por meio de uma nova conta externa.
</p>
<p>Para obter mais informações consulte a <a href="../../installation/using/configure-fda-google-big-query.md">documentação detalhada</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Melhorias de segurança**

* O acesso ao método da API **xtk:session#GetCnxInfo** que retorna os detalhes completos da conexão do banco de dados agora é restrito somente a usuários administradores. (NEO-27779)
* A função decryptString obsoleta foi substituída por decryptPassword nos arquivos JavaScript relacionados ao CRM.
* O recurso de assinatura de rastreamento foi aprimorado para reduzir o risco de rastreamento de erros de redirecionamento quando ferramentas de terceiros (clientes de email, navegadores da Internet, ferramentas de segurança de link seguro) modificam o link rastreado.
* Correção de um problema que impedia que URLs rastreados funcionassem quando contivessem caracteres em maiúsculas. O mecanismo de assinatura de URLs rastreados agora diferencia maiúsculas de minúsculas. (NEO-28414)

**Atualizações de compatibilidade**

Os seguintes sistemas agora são compatíveis com o Campaign:
* Conector FDA do Google BigQuery
* Conector Vertica FDA
* PostgreSQL 13

Saiba mais na [matriz de compatibilidade do Campaign](../../rn/using/compatibility-matrix.md).

**Recursos obsoletos**

* A partir da versão 21.1 do Campaign, o Conector de dados do Adobe Analytics não será mais utilizado. Se você estiver usando esse conector, precisará adaptar sua implementação adequadamente com o novo Adobe Analytics Connector.
Para obter mais informações consulte a [documentação detalhada](../../technotes/using/aa-connector-migration.md).
* O suporte para Debian 8 foi descontinuado.
* Após a desativação do Oracle CRM na versão 20.3, a conta externa relacionada foi removida da interface.

Saiba mais na [página sobre recursos obsoletos e removidos](../../rn/using/deprecated-features.md).

**Aprimoramentos**

* Foram adicionadas verificações adicionais ao salvar um fluxo de trabalho para garantir que os nomes das atividades sejam únicos e que as transições sejam sempre seguidas por uma atividade.
* O fluxo de trabalho técnico **Faturamento (faturamento)** agora inclui as tarefas originalmente executadas pelo fluxo de trabalho **Número de perfis de faturamento ativos** (billingActiveContactCount), que foi removido. O relatório de email enviado mensalmente pelo fluxo de trabalho agora fornecerá informações sobre o número de perfis ativos na instância. [Leia mais](../../workflow/using/about-technical-workflows.md).
* O novo atributo **_keyOnMData** foi adicionado para poder usar uma chave para operações em dados de memorando.

**Outras alterações**

* Uma garantia foi adicionada para permitir que apenas o [fluxo de trabalho técnico de faturamento](../../production/using/monitoring-processes.md#billing-report) seja executado na instância de marketing.
* O terceiro openssl para Windows foi atualizado para a versão 1.1.1h.
* Na descrição do pacote Debian, nlserver foi alterado para servidor do Adobe Campaign Classic.

**Correções**

* Correção de um problema ao editar o tempo limite da sessão para fazer logoff de usuários após um período específico em que os usuários permaneceram conectados mesmo após o tempo definido.
* Correção de um problema em que as entregas eram exibidas somente como leitura, mas ainda podiam ser editadas nas propriedades de entregas.
* Correção de um erro que fazia com que a barra de ferramentas de edição desaparecesse ao projetar um aplicativo web.
* Correção de um erro que exibia a versão de texto de um email com cabeçalhos do Adobe Campaign Classic ao adicionar um link a um email. (NEO-29211
* Ao usar FDA em conexão HTTPs, o fluxo de trabalho **Mid-sourcing (logs do delivery)** (defaultMidSourcingLog) estava preso no período definido pela opção **NmsMidSourcing_LogsPeriodHour**. Isso evitaria que registros fossem atualizados com dados que ocorressem após esse período definido. (NEO-30833)
* Correção de um problema que ocorria após a execução do fluxo de trabalho de sincronização do centro de mensagens. Toda vez que uma pasta de objetos de entrega era movida para uma pasta personalizada, o fluxo de trabalho movia as entregas de volta para a pasta genérica **Histórico de mensagem transacional**. (NEO-27445)
* Correção de um problema que exibia uma mensagem de erro ao tentar exibir os relatórios **Estatísticas de transmissão**, **Indicadores de rastreamento** e **Estatísticas de atividades de compartilhamento**.
* A atividade de fluxo de trabalho **Oracle por demanda** foi removida da interface após a desativação do conector Oracle CRM.
* Correção de um problema que interrompia a execução de workflows de processamento após a reinicialização diária do módulo do servidor de fluxo de trabalho (wfserver). (NEO-30047)
* Correção de um problema que impedia a atualização do documento de gerenciamento MX, o que poderia afetar negativamente a reputação do IP. (NEO-29897)
* Correção de problemas que causavam falhas do processo da Web ao receber uma chamada SOAP. (NEO-28796) (NEO-29600)
* Correção de um problema que causava a falha da criação do índice SAP HANA FDA. (NEO-29664)
* Correção de um problema que poderia manter mensagens transacionais no estado **Aguardando** ao executar chamadas SOAP contendo um cabeçalho. (NEO-28737)
* Correção de um problema que ocorria ao usar o conector FDA do Teradata: todas as tabelas temporárias foram criadas em apenas um nó do cluster, o que poderia acabar consumindo todo o espaço do spool e causar falha no Teradata. As tabelas temporárias agora são geradas em muitos nós. (NEO-28230)
* Correção de um problema ao usar aplicações Web que fazia com que tags de rastreamento gerassem chaves primárias incorretas no esquema **nms:trackingURL**. (NEO-27931)
* A compatibilidade com o ODBC 3.x foi aprimorada para garantir a precisão da mensagem de erro.
* Correção de um problema que poderia resultar em falhas do console quando modelos de conteúdo personalizados eram usados em entregas de email. (NEO-31547)
* Correção de um problema que impedia o Tomcat de enviar respostas válidas devido a uma conexão lenta ou um tamanho de resposta grande.
* Correção de um problema que poderia ocorrer durante a leitura de UUID de um banco de dados PostgreSQL.
* Correção de um problema que poderia causar problemas de desempenho ao pesquisar dados de proposta vinculados a ofertas. (NEO-27554)
* Correção de um problema que resultava na não resposta do processo da Web quando o serviço IMS era ativado, mas não respondia.
* Correção de um problema que impedia o envio de uma entrega com um grupo de provas devido a um mecanismo de associação específico que falhava na personalização da entrega. (NEO-14391)
* Correção de um problema em que não era enviado um alerta com a atividade de alerta se uma consulta e uma atividade de enriquecimento tivessem como alvo a tabela de entrega. (NEO-25157)

### ![](assets/do-not-localize/red_2.png) Versão 21.1.2 – Build 9282 {#release-21-1-2-build-9282}

_15 de abril de 2021_

* O gerenciamento de senhas foi aprimorado para otimizar a memória.
* Correção de um problema que poderia causar falhas de MTA.

### ![](assets/do-not-localize/red_2.png) Versão 21.1.1 – Build 9277 {#release-21-1-1-build-9277}

_22 de fevereiro de 2021_

**Aprimoramentos de segurança**

* O mecanismo de autenticação do console foi aprimorado para otimizar a segurança. (NEO-26944)
* Correção de um problema de segurança para reforçar a proteção contra problemas de SSRF (Server Side Request Forgery). (NEO-28532)

**Atualizações de compatibilidade**

Os seguintes sistemas agora são compatíveis com o Campaign:

* A API do Salesforce versão 49 agora é compatível com a utilização da conta externa do Salesforce CRM.

**Recursos obsoletos**

O relatório de **monitoramento técnico da avaliação do delivery** agora está obsoleto.

Saiba mais na [página sobre recursos obsoletos e removidos](../../rn/using/deprecated-features.md).

**Aprimoramentos**

**O EFS (Email Feedback Service, Serviço de feedback por email)** é um serviço escalável que captura diretamente o feedback do MTA aprimorado, melhorando assim a precisão dos relatórios. Esse recurso está sendo lançado como um beta privado e estará progressivamente disponível para todos os clientes em versões futuras.

* Agora todas as categorias de feedback são capturadas, para oferecer relatórios completos e precisos.
* O cálculo do indicador Entregue agora se baseia no feedback em tempo real do MTA aprimorado para melhorar a precisão e a reatividade.
* O EFS soluciona o problema de atrasos de relatórios síncronos de rejeições temporárias.

Para obter mais informações consulte a [documentação detalhada](../../delivery/using/sending-with-enhanced-mta.md#efs).
Se você estiver interessado em participar deste beta privado, preencha este [formulário](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) e nós entraremos em contato com você.

**Outras alterações**

* A velocidade de transferência foi aprimorada para grandes logs de rastreamento usando compactação.
* O mapa de calor do fluxo de trabalho foi aprimorado para evitar tempos limite ao executar workflows com várias atividades. (NEO-27423).
* Correção de um problema que permitia que uma oferta fosse apresentada mesmo se sua data final fosse no passado. Agora, o Campaign Classic considera o carimbo de data e hora completo, em vez de somente a data. (NEO-27590)
* O link do Google+ foi removido do bloco de personalização **links de compartilhamento de rede social**.
* Correção de um problema após a implementação de uma correção de erro na última versão. Uma verificação foi adicionada ao nome do host ao conectar usando SSL/TLS, o que resultava em falha de delivery de SMS. A verificação do nome do host foi desativada para a maioria dos protocolos, como POP3, SMS e HTTP com proxy, e a verificação do certificado para a conta externa SMS foi aprimorada com três valores (NEO-29581). [Saiba mais](../../delivery/using/sms-protocol.md#skip-tls)

**Correções**

* Correção de um problema que impedia que os atalhos do teclado Tab, Enter e Escape funcionassem na nova tela de logon.
* Correção de um problema de atualização que fazia com que o nome de um fluxo de trabalho recém-criado fosse substituído pelo valor padrão após o salvamento (NEO-26106).
* Correção de um problema que ocorria ao executar workflows em que um novo campo era adicionado como parte de uma atividade **Enriquecimento** antes de uma atividade **Delivery** usando um target mapping de **Arquivo externo**: campos indesejados eram adicionados ao target mapping do **Arquivo externo**. (NEO-27687)
* Correção de um problema que fazia com que alguns caracteres no código fonte fossem alterados ao ser reaberta uma aplicação web criada e salva anteriormente. (NEO-27597)
* Correção de um problema que ocorria ao atualizar para uma compilação, incluindo o novo mecanismo de assinatura para links de rastreamento (da Compilação 19.1.4 e Campaign 20.2): quando vários modelos eram associados a um evento, a atualização podia fazer com que o modelo errado fosse selecionado ao ser enviada a mensagem transacional. (NEO-28326)
* Correção de um problema que fazia com que o MTA ficasse sem resposta e não conseguisse processar deliveries, a menos que fosse reiniciado. (NEO-27455)
* Correção de um problema no banco de dados MSSQL relacionado ao gerenciamento de data e hora durante operações de carregamento em massa para uma coluna de tipo de data e hora.
* Correção de um problema de query de fluxo de trabalho ao usar funções Redshift xtk. Os SubDays, SubSeconds, SubMinutes e SubHours agora aceitam os tipos de data e hora do Redshift (NEO-24962).
* Correção de um problema que exibia uma mensagem de erro de script ao tentar a pré-visualização de um relatório com acesso Anônimo. (NEO-27081)
* Correção de um problema que podia reduzir o uso de memória no servidor durante a execução da análise do delivery.
* Correção de um problema que impedia que a instância funcionasse durante a tentativa de executar consultas complexas específicas.
* Correção de um problema que impedia a execução do fluxo de trabalho técnico **Sincronizar páginas do Twitter**. (NEO-28634)
* Correção de um problema que podia exibir uma mensagem de erro relacionada à função decryptPassword durante a tentativa de publicar no Twitter usando o template do delivery **Tweet (twitter)**. (NEO-28216)
* Correção de um problema que ocorria ao usar uma atividade **JavaScript** para fazer uma solicitação HTTP em um fluxo de trabalho. Após a definição do número da porta no nome do Host, a chamada falhará com o seguinte erro (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Correção de um problema que impedia o envio de novos deliveries com personalização de dados de target (NEO-30323).
* Correção de um problema em que várias falhas ocorriam na instância de marketing que causava os arquivos principais.
* Correção de um problema que resultava em falha do fluxo de trabalho **Rastreamento** com o seguinte erro (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Correção de um problema que ocorria ao criar e salvar um delivery na guia **Direcionamento &amp; Fluxo de trabalho** de uma campanha: a pré-visualização falhava com o seguinte erro (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Correção de um erro que ocorria ao configurar uma conta externa entre uma instância de marketing e uma instância do Adobe Campaign Standard ou uma instância do Campaign Classic mid-sourcing e usar a opção &quot;DisableFOH2=1&quot;. Ao ser usada a opção &quot;DisableFOH2=1&quot; na conta externa, as conexões não eram fechadas corretamente e se acumulavam, resultando no seguinte erro (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Correção de um erro no SMS quando ocorriam problemas de conexão entre o servidor e o provedor. A conexão era então automaticamente desativada pelo filho do MTA. O Adobe Campaign Classic não tentava se conectar a essa conexão com falha, desde que um novo filho não tivesse sido iniciado.
