---
product: campaign
title: Versão mais recente
description: Notas de versão mais recentes do Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: ht
source-wordcount: '2312'
ht-degree: 100%

---

# Versão mais recente{#latest-release}

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign v7**. Cada nova build vem com um status que é materializado por uma cor. Saiba mais sobre os status de build do Campaign Classic v7 [nesta página](rn-overview.md).

## Versão 7.3.5 - Build 9368 {#release-7-3-5}

[!BADGE Disponibilidade geral]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade geral"}


_5 de dezembro de 2023_


### Aprimoramentos de segurança {#release-7-3-5-security}


* Com o Campaign Classic v7.3.5, o processo de autenticação foi aprimorado e protegido. Os operadores técnicos agora devem usar o Adobe Identity Management System (IMS) para se conectarem ao Campaign. Saiba como migrar as contas técnicas já existentes nesta [nota técnica](../../technotes/using/ims-migration.md).

* Além disso, como parte do esforço para aprimorar a segurança e o processo de autenticação, o Adobe Campaign recomenda migrar o modo de autenticação do usuário final da autenticação nativa de logon/senha para o Adobe Identity Management System (IMS). Saiba como migrar operadores [nesta nota técnica](../../technotes/using/migrate-users-to-ims.md).

* Agora, quando um formulário web tem o status **Publicação pendente**, ele não é publicado automaticamente. Para evitar problemas de segurança, é necessário publicá-lo antes de ele se tornar **Online** e ficar acessível por meio do URL do formulário web em um navegador da web. [Leia mais](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### Correções {#release-7-3-5-patches}

* Correção de um problema com o uso de dados de um banco de dados do Google Big Query ao atualizar dados em um banco de dados da Oracle: todas as chaves foram definidas como `0` na tabela temporária do workflow. (NEO-65091)
* Correção de um problema que causava a falha de execução de um workflow quando duas consultas em um banco de dados do Google Big Query eram combinadas em uma atividade de workflow de **União**. (NEO-63705)
* Correção de um problema que causava a solicitação de uma nova autenticação ao clicar no botão `Back` em um relatório do Campaign. (NEO-65087)
* Correção de um erro no workflow de Limpeza de banco de dados que acontecia quando uma entrega era excluída antes de suas provas de entrega. (NEO-48114)
* Correção de um problema de conexão com o Console do cliente: atualizações recentes na verificação TLS estavam causando um erro de conexão. (NEO-50488)
* Correção de um problema com a autenticação de Proxy HTTP depois da pós-atualização do Campaign para a versão 7.3.1. As solicitações HTTP em workflows do Campaign estavam falhando com `error 407 – proxy auth required is returned`. (NEO-49624)
* Correção de uma falha intermitente com descriptografia GPG nas atividades de workflow de **Script**. A mensagem de erro associada era: `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

## Versão 7.3.4 — Build 9364 {#release-7-3-4}

[!BADGE Disponibilidade limitada]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade limitada"}


>[!CAUTION]
>
>A atualização do Console do Cliente é obrigatória. Saiba como atualizar seu console do cliente nesta [página](../../installation/using/installing-the-client-console.md).
>
>Se você estiver usando o [Campaign - Conector do Microsoft Dynamics CRM](../../platform/using/crm-connectors.md), será necessário atualizar seus servidores de marketing e mid-sourcing com essa nova build.

_7 de setembro de 2023_

### Aprimoramentos de segurança {#release-7-3-4-security}

* A segurança foi aprimorada nas APIs do IMS. As informações confidenciais do cliente (ou seja, tokens de acesso) foram removidas dos parâmetros de URL. Essas credenciais agora são enviadas nos dados de publicação ou no cabeçalho de autorização, garantindo um processo de comunicação mais seguro. (NEO-63045)
* A segurança foi aprimorada em aplicativos da web para evitar ataques de DDOS. (NEO-50757)
* A segurança foi aprimorada para evitar que os dados de PII sejam expostos nos erros de logs da web. (NEO-46827)
* A segurança foi otimizada para impedir que o token de segurança seja incluído no URL da página inicial do Campaign. (NEO-38519)

### Atualizações de compatibilidade  {#release-7-3-4-compat}

* O Tomcat foi atualizado para a versão 8.5.91
* A biblioteca libexpat foi atualizada para 2.5.0 para melhorar a segurança. (NEO-51023)

### Aprimoramentos {#release-7-3-4-improvements}

* O parâmetro MaxWorkingSetMb no arquivo de configuração do servidor (serverConf.xml) foi modificado para otimizar a alocação de memória para entregas. (NEO-49204)
* A conta externa do BigQuery foi aprimorada com novas opções para configurar o SDK do GCloud. (NEO-63879) [Leia mais](../../installation/using/configure-fda-google-big-query.md#google-external)
* Uma nova seção `cusHeader` foi adicionada ao arquivo de configuração do servidor (serverConf.xml). Ela permite adicionar cabeçalhos personalizados ao fazer upload de um arquivo de um servidor externo. (NEO-58339) [Leia mais](../../installation/using/the-server-configuration-file.md#cusheaders).
* O gerenciamento de log de rastreamento foi aprimorado para evitar IDs negativas para lastMsgId. Foi alterado de int32 para int64. (NEO-52290)
* O workflow de mid-sourcing (estatísticas de entrega) foi adicionado pronto para uso. Esse novo workflow sincroniza os dados estatísticos da entrega (nms:deliveryStat) do mid à instância de marketing. (NEO-36802)

### Correções {#release-7-3-4-patches}

* Correção de um problema que poderia ocorrer quando uma solicitação de serviço era feita antes do logon do IMS, se a autenticação de chamada de solicitação de serviço estivesse usando um token de serviço. (NEO-64903)
* Correção de um problema de regressão que poderia levar a problemas de rolagem ao usar o Editor de conteúdo digital. (NEO-64671, NEO-59256)
* Correção de um problema de regressão ao colar conteúdo do Excel no Editor de conteúdo digital. (NEO-63287)
* Correção de um problema que poderia impedir a exibição correta de aplicativos da Web no modo de compatibilidade v5. (NEO-63174)
* Correção de um problema que impedia que operadores não administradores enviassem entregas do webAnalytics. (NEO-62750)
* Correção de um problema para impedir que os navegadores adicionem espaços extras ao usar conteúdo condicional em uma entrega. (NEO-62132)
* Correção de um problema de regressão que impedia o funcionamento correto do cálculo de contatos ativos no workflow de faturamento ao usar esquemas de público-alvo associados a vários esquemas de log. (NEO-61468)
* Correção de um problema que poderia resultar em um erro e impedir a rolagem da tela ao editar o conteúdo de uma entrega. (NEO-61364)
* Correção de um problema que fazia com que uma janela pop-up fosse aberta ao clicar em uma imagem no editor de conteúdo de email. (NEO-60752)
* Correção de um problema que poderia resultar na codificação incorreta de caracteres especiais no conteúdo HTML de uma entrega em vários navegadores. (NEO-60081)
* Correção de um problema de sincronização que poderia ocorrer ao usar a atividade de workflow inSMS. (NEO-59544)
* Correção de um problema ao usar o conector do Big Query com campos de data e hora ou de carimbo de data e hora. (NEO-59502, NEO-49768)
* Correção de um problema que impedia o uso de relatórios de entrega cumulativos. (NEO-59211)
* Correção de um problema que poderia resultar em erros ao compartilhar públicos-alvo com o Serviço principal de pessoas. (NEO-58637)
* Correção de um problema ao exibir a mirror page de uma entrega. (NEO-58325)
* Correção de um problema que impedia o funcionamento da expressão xtk XtkLibrary.Right(). (NEO-57870)
* Correção de um problema que fazia com que o atributo de estilo da tag do corpo fosse alterado ao fazer upload de uma imagem no Editor de conteúdo digital. (NEO-57697)
* Correção de um problema com caracteres especiais ao executar exportações em lote com a atividade do conector do CRM. (NEO-54300)
* Correção de um problema que impedia o funcionamento do carregamento em massa com tipos de dados de “string” ao usar uma atividade de carregamento de dados e o conector o Big Query. (NEO-53748)
* Correção de um problema da chave de cache que poderia gerar problemas de renderização. (NEO-51516, NEO-49995)
* Correção de um problema que poderia resultar em um erro de validação ao enviar uma entrega de correspondência direta usando targetMapping com aprovações. (NEO-50758)
* Correção de um problema no gerenciamento de consultas que poderia afetar o desempenho da entrega. (NEO-49991)
* Correção de um problema ao usar contas externas em atividades de entrega de workflow da campanha que poderia levar a problemas de configuração da conta externa. (NEO-49959)
* Correção de um problema de desempenho ao enviar notificações por push. (NEO-49953)
Correção de um problema que poderia fazer com que caracteres japoneses fossem exibidos incorretamente ao exportar relatórios (NEO-49308).
* Correção de um problema que fazia com que o relatório de erros do Tomcat exibisse mais detalhes de erros do que deveria. (NEO-49029)
* Correção de um problema que poderia resultar em erro de entrega ao usar um grande número de ofertas. (NEO-48807)
* Correção de um problema que poderia impedir o funcionamento adequado da atividade de workflow **Atualizar dados**. (NEO-48140)
* Correção de um problema que poderia impedir a sincronização dos dados de rastreamento de cliques para entregas usando uma conta externa diferente do email.(NEO-47277)
* Correção de um problema que poderia impedir a sincronização de logs de rastreamento em tempo real na instância de marketing do Centro de mensagens. (NEO-42540)
* Correção de um problema que impedia a exibição do prefixo do espaço de trabalho na janela de descoberta de um esquema para tabelas de banco de dados do Snowflake. (NEO-40297)
* Correção de um problema que impedia que tags de `<img-amp>` funcionassem no conteúdo de email. (NEO-38685)
* Correção de um problema que poderia causar uma falha do workflow de arquivamento do Centro de mensagens ao usar uma retransmissão HTTP. (NEO-33783)
* Correção de um problema que poderia causar erros de nome e tamanho de fonte no editor de conteúdo de email. (NEO-61342)

## Versão 7.3.3 - Build 9359 {#release-7-3-3}

[!BADGE Disponibilidade limitada]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade limitada"}

>[!AVAILABILITY]
>
>Uma atualização de patch específica do Campaign v7.3.3.IMS está disponível para esta versão, se nenhum outro patch tiver sido aplicado ao seu ambiente. Ele traz [Atualizações de segurança do Adobe Identity Management System (IMS) fornecidas com a v7.3.5](#release-7-3-5-security) aos ambientes v7.3.3 já existentes.


_20 de março de 2023_


### Aprimoramento de segurança {#release-7-3-3-security}

* Para melhorar a segurança, o Tomcat foi atualizado da versão 8.5.81 para a 8.5.85. (NEO-56936)



### Aprimoramentos {#release-7-3-3-improvements}

* O fluxo de trabalho de faturamento foi aprimorado para otimizar o desempenho. (NEO-47658)
* O fluxo de trabalho de rastreamento foi aprimorado para otimizar o desempenho no caso de uma entrega grande. (NEO-45064)
* O gerenciamento de rastreamento foi aprimorado para corrigir possíveis problemas com parâmetros dinâmicos em URLs. O gerenciamento de rastreamento v3 agora aceita URLs do tipo ajax (com parâmetros após um “#”) e impede que ferramentas de terceiros modifiquem URLs de rastreamento. Para aplicar essa alteração, você precisa entrar em contato com a Adobe. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

>[!CAUTION]
>
>A atualização do Console do Cliente é obrigatória. Saiba como atualizar seu console do cliente nesta [página](../../installation/using/installing-the-client-console.md).

### Patches {#release-7-3-3-patches}

* Correção de um problema que poderia impedir o envio de notificações por push de prova do iOS da instância de controle (contexto de Mensagens transacionais). (NEO-54713)
* Correção de um problema que impedia a rolagem na guia **Editar** do editor de conteúdo digital (DCE). (NEO-54474)
* Correção de um problema em que, se duas atividades de enriquecimento usassem o mesmo identificador de nome em sua vinculação, a segunda atividade usaria os links da primeira. (NEO-48851)

## Versão 7.3.2 - Build 9356 {#release-7-3-2}

[!BADGE Disponibilidade limitada]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade limitada"}


>[!AVAILABILITY]
>
>Um upgrade de patch específico do Campaign v7.3.2.IMS está disponível para esta versão, se nenhum outro patch tiver sido aplicado ao seu ambiente. Ele traz [Atualizações de segurança do Adobe Identity Management System (IMS) fornecidas com a v7.3.5](#release-7-3-5-security) aos ambientes v7.3.3 já existentes.

_21 de novembro de 2022_

### Atualizações de compatibilidade {#release-7-3-2-compat}

* O Adobe Campaign agora é compatível com o PostgreSQL 14. Para obter mais informações, consulte esta [technote](../../technotes/using/tech-stack-upgrade.md).

* Após o fim da vida útil do Microsoft Internet Explorer 11, o mecanismo de renderização HTML para painéis no console do cliente começou a utilizar o Edge Chromium. (NEO-20741)

Saiba mais na [matriz de compatibilidade do Campaign](../../rn/using/compatibility-matrix.md#RDBMSservers).

>[!CAUTION]
>
>A atualização do Console do Cliente é obrigatória. Saiba como atualizar seu console do cliente nesta [página](../../installation/using/installing-the-client-console.md).

### Aprimoramentos {#release-7-3-2-improvements}

* O conector Google BigQuery agora oferece suporte total a campos booleanos. (NEO-49181)
* Agora você pode configurar a duração da validade dos cookies IMS na seção `Configuration for the redirection service` do arquivo serverConf.xml. Isso se aplica aos seguintes cookies: `uuid230`, `nllastdelid` e `AMCV_` (NEO-42541)
* O IP agora pode ser oculto na solicitação “/r/test” ao configurar `showSourceIP` como falso no nó de redirecionamento do arquivo serverConf.xml. [Leia mais](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

### Recursos obsoletos  {#release-7-3-2-deprecated}

* O marketing social do Facebook agora está obsoleto. É possível usar a integração com o X (anteriormente conhecido como Twitter) para publicar em redes sociais ou colaborar com a Adobe para criar um canal personalizado.
* O conector ACS (oferta do Prime) agora está obsoleto. Você pode usar os recursos de exportação/importação do Campaign para extrair e inserir dados em ambos os produtos.

Saiba mais na [página sobre recursos obsoletos e removidos](deprecated-features.md).

### Outras alterações  {#release-7-3-2-other}

<!--* Web logs have been improved: `logonEscalation` warnings are now only displayed for users with admin privileges. (NEO-47167)-->
* Para evitar erros, o fluxo de trabalho **Coletar dados para o serviço do Heatmap** (collectDataHeatMapService) agora é interrompido por padrão. (NEO-33959)
* Várias melhorias foram implementadas para otimizar o uso da CPU no painel de campanhas. (NEO-46417)
* Para evitar falhas, o método JS loadLibraryDebug foi removido. (NEO-46968)
* As referências restantes à biblioteca log4j foram removidas da instalação do Campaign no Windows. (NEO-44851)

### Patches {#release-7-3-2-patches}

* Corrigido um problema que impedia a utilização da opção de fluxo de trabalho **Mesclar linhas selecionadas**. (NEO-48488)
* Corrigido um problema que impedia que o indicador de entrega **Sucesso** fosse atualizado corretamente ao usar o MTA aprimorado do Adobe Campaign. (NEO-50462)
* Corrigido um problema ao redefinir a aprovação do conteúdo em uma entrega de email, que impedia a reaprovação. (NEO-44259)
* Corrigido um problema que poderia impedir a exibição do botão **Aprovação de entrega**. (NEO-47547)
* Corrigido um problema de desempenho na guia HTML de uma entrega que poderia ocorrer ao usar um código HTML grande. (NEO-47440)
* Corrigido um problema que afetava as atualizações de status do log de entrega na instância MID quando a opção `FeatureFlag_GZIP_Compression` estava habilitada. (NEO-49183)
* Corrigido um problema que impedia o envio de notificações do aplicativo móvel para iOS a partir de uma instância de execução ao usar a autenticação baseada em token. (NEO-45961)
* Corrigido um problema com o fluxo de trabalho **Atualizar para a capacidade de entrega** (deliverabilityUpdate) que travava por conter muitos broadlogs pendentes para sincronização. (NEO-48287)
* Corrigido um problema de tipo de evento que bloqueava o fluxo de trabalho **Sincronização do centro de mensagens** (mcSynch).
* Corrigido um problema que poderia resultar em erro ao adicionar o indicador **Destinatários que abriram** (estimatedRecipientOpen) nos dados adicionais de uma atividade de fluxo de trabalho de **Consulta**. (NEO-46665)
* Corrigido um problema com o fluxo de trabalho de **Faturamento** que falhava por conter pacotes de Execução e do Centro de controle de mensagens instalados na mesma instância. (NEO-47674)
* Corrigido um problema com o fluxo de trabalho de **Faturamento** que falhava ao conter tabelas com a chave principal definida como uma string em vez de um inteiro. (NEO-46254)
* Corrigido um problema que ocorria em filtros do Heatmap quando o nome do fluxo de trabalho era muito longo. (NEO-46301)
* Corrigido um problema introduzido na versão 7.3.1 do conector Snowflake FDA que resultava no descarte de registros ao usar a opção “Junção simples de cardinalidade 0 ou 1” durante o enriquecimento. (NEO-48737)
* Corrigido um problema com o Snowflake FFDA ao usar o parâmetro de classificação em uma atividade de fluxo de trabalho de **Divisão**. (NEO-45899)
* Corrigido um problema que impedia o usuário de salvar a configuração da conta externa. A conta externa agora é salva automaticamente após o teste de conexão para conectores com um recurso de análise (Snowflake e Google BigQuery). (NEO-47636)
* Corrigido um problema que impedia a inserção de um tipo de dados de Tempo em uma atividade de fluxo de trabalho de **Atualização de dados** no MSSQL. (NEO-47763)
* Corrigido um problema que resultava na falha do processo do MTA quando o fuso horário do mecanismo não era definido (específico para MSSQL). (NEO-46619)
* Corrigido um problema com a importação de arquivos HTML no qual os nós de imagem (img) continham URLs com campos de personalização. (NEO-48396)
* Corrigido um erro HTTP 500 ao tentar se conectar a uma instância em que o nó `limit` não estava configurado no arquivo serverConf.xml.
* Corrigido um problema que poderia resultar em um erro de “Incompatibilidade do conjunto de caracteres” ao usar determinadas funções, como a `to_nclob` em um banco de dados unicode do Oracle no qual o NChar não estava habilitado. (NEO-49361)
* Corrigido um problema que resultava em erro quando um usuário com direitos de acesso de leitura para a pasta nmsDeliveryMapping tentava executar uma campanha ou fluxo de trabalho. (NEO-48230)
* Corrigido um problema que impedia o funcionamento da função `JSPContext.sqlExecWithOneParam`. (NEO-50066)
* Correção de vários erros de redirecionamento. (NEO-50030)
