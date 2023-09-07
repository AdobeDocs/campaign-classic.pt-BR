---
product: campaign
title: Versão mais recente
description: Notas de versão mais recentes do Campaign Classic v7
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 155fbcd2846cfc5a8db25194bd8d7007356db24e
workflow-type: tm+mt
source-wordcount: '1869'
ht-degree: 58%

---

# Versão mais recente{#latest-release}

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign v7**. Cada nova build vem com um status que é materializado por uma cor. Saiba mais sobre os status de build do Campaign Classic v7 [nesta página](rn-overview.md).

## Versão 7.3.4 - Build 9364 {#release-7-3-4}

[!BADGE Disponibilidade geral]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade geral"}

>[!CAUTION]
>
>A atualização do Console do Cliente é obrigatória. Saiba como atualizar seu console do cliente nesta [página](../../installation/using/installing-the-client-console.md).
>
> Se você estiver usando [Campaign - Conector do Microsoft Dynamics CRM](../../platform/using/crm-connectors.md), você deve atualizar seus servidores de marketing e mid-sourcing com essa nova build.

_7 de setembro de 2023_

**Aprimoramento de segurança**

* A segurança foi aprimorada nas APIs do IMS. As informações confidenciais do cliente (ou seja, tokens de acesso) foram removidas dos parâmetros de URL. Essas credenciais agora são enviadas nos dados de publicação ou no cabeçalho de autorização, garantindo um processo de comunicação mais seguro. (NEO-63045)
* A segurança foi aprimorada em aplicativos da Web para evitar ataques de DDOS. (NEO-50757)
* A segurança foi aprimorada para evitar que os dados de PII sejam expostos nos erros de logs da Web. (NEO-46827)
* A segurança foi otimizada para impedir que o token de segurança seja incluído no URL da página inicial do Campaign. (NEO-38519)

**Atualizações de compatibilidade**

* O Tomcat foi atualizado para a versão 8.5.91
* A biblioteca libexpat foi atualizada para 2.5.0 para melhorar a segurança. (NEO-51023)

**Aprimoramentos**

* O parâmetro MaxWorkingSetMb no arquivo de configuração do servidor (serverConf.xml) foi modificado para otimizar a alocação de memória para deliveries. (NEO-49204)
* A conta externa do BigQuery foi aprimorada com novas opções usadas para configurar o SDK do GCloud. (NEO-63879) [Leia mais](../../installation/using/configure-fda-google-big-query.md#google-external)
* Um novo `cusHeader` foi adicionada uma seção no arquivo de configuração do servidor (serverConf.xml). Ele permite adicionar cabeçalhos personalizados ao fazer upload de um arquivo de um servidor externo. (NEO-58339) [Leia mais](../../installation/using/the-server-configuration-file.md#cusheaders).
* O gerenciamento de log de rastreamento foi aprimorado para evitar IDs negativas para lastMsgId. Foi alterado de int32 para int64. (NEO-52290)
* O workflow Mid-sourcing (estatísticas de delivery) foi adicionado pronto para uso. Esse novo workflow sincroniza os dados estatísticos do delivery (nms:deliveryStat) do meio à instância de marketing. (NEO-36802)

**Correções**

* Correção de um problema que ocorria quando uma solicitação de serviço era feita antes do logon do IMS, se a autenticação de chamada de solicitação de serviço estivesse usando um token de serviço. (NEO-64903)
* Correção de um problema de regressão que poderia levar a problemas de rolagem ao usar o Editor de conteúdo digital. (NEO-64671, NEO-59256)
* Correção de um problema de regressão ao colar conteúdo do Excel no Editor de conteúdo digital. (NEO-63287)
* Correção de um problema que impedia a exibição correta de aplicativos da Web no modo de compatibilidade v5. (NEO-63174)
* Correção de um problema que impedia que operadores não administradores enviassem deliveries do webAnalytics. (NEO-62750)
* Correção de um problema para impedir que os navegadores adicionassem espaços extras ao usar conteúdo condicional em uma entrega. (NEO-62132)
* Correção de um problema de regressão que impedia o funcionamento correto do cálculo de contatos ativos no fluxo de trabalho Faturamento ao usar esquemas de público alvo associados a vários esquemas de log. (NEO-61468)
* Correção de um problema que poderia resultar em erro e impedir a rolagem ao editar o conteúdo de um delivery. (NEO-61364)
* Correção de um problema que fazia com que uma janela pop-up fosse aberta ao clicar em uma imagem no editor de conteúdo de email. (NEO-60752)
* Correção de um problema que poderia resultar na codificação incorreta de caracteres especiais no conteúdo HTML de um delivery em vários navegadores. (NEO-60081)
* Correção de um problema de sincronização que poderia ocorrer ao usar a atividade de workflow do inSMS. (NEO-59544)
* Correção de um problema ao usar o conector Big Query com campos de carimbo de data e hora ou data e hora. (NEO-59502, NEO-49768)
* Correção de um problema que impedia o uso de relatórios cumulativos do delivery. (NEO-59211)
* Correção de um problema que poderia resultar em erros ao compartilhar públicos-alvo com o Serviço principal de pessoas. (NEO-58637)
* Correção de um problema ao exibir a mirror page de um delivery. (NEO-58325)
* Correção de um problema que impedia o funcionamento da expressão xtk XtkLibrary.Right(). (NEO-57870)
* Correção de um problema que fazia com que o atributo de estilo da tag body fosse alterado ao ser carregada uma imagem no Editor de conteúdo digital. (NEO-57697)
* Correção de um problema com caracteres especiais ao executar exportações em lote com a atividade do conector CRM. (NEO-54300)
* Correção de um problema que impedia que o carregamento em massa funcionasse com tipos de dados de &quot;sequência&quot; ao usar uma atividade de carregamento de dados e o conector Big Query. (NEO-53748)
* Correção de um problema de chave de cache que poderia levar a problemas de renderização. (NEO-51516, NEO-49995)
* Correção de um problema que poderia resultar em erro de validação ao enviar um delivery de correspondência direta usando targetMapping com aprovações. (NEO-50758)
* Correção de um problema de gerenciamento de query que poderia afetar o desempenho do delivery. (NEO-49991)
* Correção de um problema, ao usar contas externas em atividades de delivery de workflow da campanha, que poderia levar a problemas de configuração de conta externa. (NEO-49959)
* Correção de um problema de desempenho ao enviar notificações por push. (NEO49953) Corrigido um problema que fazia com que caracteres japoneses fossem exibidos incorretamente ao exportar relatórios (NEO49308).
* Correção de um problema que fazia com que o relatório de erros do Tomcat exibisse muitos detalhes de erro. (NEO-49029)
* Correção de um problema que poderia resultar em erro de entrega ao usar um grande número de ofertas. (NEO-48807)
* Correção de um problema que poderia impedir a **Atualizar dados** de fluxo de trabalho funcionarem corretamente. (NEO-48140)
* Correção de um problema que poderia impedir que os dados de rastreamento de cliques fossem sincronizados para deliveries usando uma conta externa diferente do email.(NEO-47277)
* Correção de um problema que poderia impedir que logs de rastreamento em tempo real fossem sincronizados na instância de marketing do Centro de mensagens. (NEO-42540)
* Correção de um problema que impedia a exibição do prefixo do espaço de trabalho na janela de descoberta de um esquema para tabelas de banco de dados do Snowflake. (NEO-40297)
* Correção de um problema que impedia `<img-amp>` para impedir que as tags funcionem no conteúdo de email. (NEO-38685)
* Correção de um problema que causava a falha do fluxo de trabalho de arquivamento do Centro de mensagens ao usar uma retransmissão HTTP. (NEO-33783)
* Correção de um problema que poderia causar erros de nome e tamanho de fonte no editor de conteúdo de email. (NEO-61342)

## Versão 7.3.3 - Build 9359 {#release-7-3-3}

[!BADGE Disponibilidade limitada]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade limitada"}

>[!CAUTION]
>
>A atualização do Console do Cliente é obrigatória. Saiba como atualizar seu console do cliente nesta [página](../../installation/using/installing-the-client-console.md).

_20 de março de 2023_

**Aprimoramento de segurança**

* Para melhorar a segurança, o Tomcat foi atualizado da versão 8.5.81 para a 8.5.85. (NEO-56936)

**Aprimoramentos**

* O fluxo de trabalho de faturamento foi aprimorado para otimizar o desempenho. (NEO-47658)
* O fluxo de trabalho de rastreamento foi aprimorado para otimizar o desempenho no caso de uma entrega grande. (NEO-45064)
* O gerenciamento de rastreamento foi aprimorado para corrigir possíveis problemas com parâmetros dinâmicos em URLs. O gerenciamento de rastreamento v3 agora aceita URLs do tipo ajax (com parâmetros após um “#”) e impede que ferramentas de terceiros modifiquem URLs de rastreamento. Para aplicar essa alteração, você precisa entrar em contato com a Adobe. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

**Correções**

* Correção de um problema que poderia impedir o envio de notificações por push de prova do iOS da instância de controle (contexto de Mensagens transacionais). (NEO-54713)
* Correção de um problema que impedia a rolagem na guia **Editar** do editor de conteúdo digital (DCE). (NEO-54474)
* Correção de um problema em que, se duas atividades de enriquecimento usassem o mesmo identificador de nome em sua vinculação, a segunda atividade usaria os links da primeira. (NEO-48851)

## Versão 7.3.2 - Build 9356 {#release-7-3-2}

[!BADGE Disponibilidade limitada]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade limitada"}

_21 de novembro de 2022_

>[!CAUTION]
>
>A atualização do Console do Cliente é obrigatória. Saiba como atualizar seu console do cliente nesta [página](../../installation/using/installing-the-client-console.md).

**Atualizações de compatibilidade**

* O Adobe Campaign agora é compatível com o PostgreSQL 14. Para obter mais informações, consulte esta [technote](../../technotes/using/tech-stack-upgrade.md).

* Após o fim da vida útil do Microsoft Internet Explorer 11, o mecanismo de renderização HTML para painéis no console do cliente começou a utilizar o Edge Chromium. (NEO-20741)

Saiba mais na [matriz de compatibilidade do Campaign](../../rn/using/compatibility-matrix.md#RDBMSservers).

**Aprimoramentos**

* O conector Google BigQuery agora oferece suporte total a campos booleanos. (NEO-49181)
* Agora você pode configurar a duração da validade dos cookies IMS na seção `Configuration for the redirection service` do arquivo serverConf.xml. Isso se aplica aos seguintes cookies: `uuid230`, `nllastdelid` e `AMCV_` (NEO-42541)
* O IP agora pode ser oculto na solicitação “/r/test” ao configurar `showSourceIP` como falso no nó de redirecionamento do arquivo serverConf.xml. [Leia mais](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

**Recursos obsoletos**

* O marketing social do Facebook agora está obsoleto. Você pode usar a integração do Twitter para publicar em redes sociais ou trabalhar com a Adobe para criar um canal personalizado.
* O conector ACS (oferta do Prime) agora está obsoleto. Você pode usar os recursos de exportação/importação do Campaign para extrair e inserir dados em ambos os produtos.

Saiba mais na [página sobre recursos obsoletos e removidos](deprecated-features.md).

**Outras alterações**

* Os logs da Web foram aprimorados: os avisos `logonEscalation` agora são exibidos somente para usuários com privilégios de administrador. (NEO-47167)
* Para evitar erros, o fluxo de trabalho **Coletar dados para o serviço do Heatmap** (collectDataHeatMapService) agora é interrompido por padrão. (NEO-33959)
* Várias melhorias foram implementadas para otimizar o uso da CPU no painel de campanhas. (NEO-46417)
* Para evitar falhas, o método JS loadLibraryDebug foi removido. (NEO-46968)
* As referências restantes à biblioteca log4j foram removidas da instalação do Campaign no Windows. (NEO-44851)

**Correções**

* Corrigido um problema que impedia a utilização da opção de fluxo de trabalho **Mesclar linhas selecionadas**. (NEO-48488)
* Corrigido um problema que impedia que o indicador de **sucesso** de entrega fosse atualizado corretamente ao usar o MTA aprimorado do Adobe Campaign. (NEO-50462)
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
