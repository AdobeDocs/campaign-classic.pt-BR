---
product: campaign
title: Versão mais recente
description: Notas de versão mais recentes do Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: cdbcfc5aa0614e41ce76cb777fec58fbd01797d2
workflow-type: ht
source-wordcount: '903'
ht-degree: 100%

---

# Versão mais recente {#latest-release}

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign Classic v7**. Cada nova build vem com um status que é materializado por uma cor. Saiba mais sobre os status de build do Campaign Classic v7 [nesta página](rn-overview.md).

## Versão 7.4.2  {#release-7-4-2}

### Build 9391 {#build-9391}

[!BADGE Disponibilidade limitada]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade limitada"}

_12 de maio de 2025_

Esta build inclui as seguintes correções:

* Correção de um problema após a atualização encontrado em configurações alternativas à Oracle. (NEO-87012)
* Correção de um problema de back-end TLS/HTTPS que afetava o console do cliente e o servidor. (NEO-87432)

### Build 9390 {#build-9390}

[!BADGE Disponibilidade geral]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade geral"}

_2 de abril de 2025_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

**Melhorias de segurança**

Esta versão inclui várias correções de segurança.

A conexão com soluções e aplicativos da Adobe por meio da conta externa da **[!UICONTROL Adobe Experience Cloud]** foi atualizada para reforçar a segurança.

**Principais correções**

Esta versão inclui as seguintes correções principais:

* Conexão TLS/SMPP: correção de problemas de estabilidade do SMPP

* Correções do Google BigQuery:

   * Correção de regressões em tipos de dados BOOLEAN
   * Correção de problemas de configurações de proxy
   * Correção de regressões em tipos de dados DATETIME
   * Correção da estabilidade do carregamento em massa
   * Testes internos aprimorados nas versões ODBC
   * Correção de um problema com caracteres especiais na string de conexão
   * Remoção do tempo-limite padrão (5 min.) de consultas do Google BigQuery

* Agente de transferência de correspondência (MTA): correção do MTA filho órfão, que ficava preso no status **[!UICONTROL Start pending]**.


**Outras correções**

Os seguintes problemas também foram corrigidos nesta versão:

* Correção de um problema em que a atividade **Carregamento de dados (arquivo)** falhava ao enviar arquivos ao servidor<!--after an upgrade to version 8.3.8-->. Agora, usuários podem fazer upload de arquivos com êxito, sem paralisações ou erros no console. (NEO-47269)

* Correção de erros de falha de segmentação no Apache <!--following an upgrade to Adobe Campaign Classic 7.2.2 build 9349-->. Essa correção impede a geração de arquivo principal e garante a operação estável do servidor. (NEO-59059)

* Resolução de um problema de conectividade com o banco de dados do Google BigQuery <!--after upgrading to version 7.3.3 build 9359-->. Agora, usuários podem testar conexões com êxito usando a conta externa GCP. (NEO-62455)

* Compatibilidade aprimorada para atualizações de colunas Booleanas e Data/hora em tabelas do Google BigQuery usando Federated Data Access (FDA). Essa correção garante o tratamento adequado dos tipos de dados durante as operações Inserir/Atualizar. (NEO-65774)

* Correção de uma vulnerabilidade de injeção de recurso que permitia que invasores injetassem elementos de HTML em pontos de acesso de email. Esse aprimoramento de segurança impede tentativas de acesso não autorizado e de phishing. (NEO-66462)

* Correção de erros intermitentes ao inserir dados nas tabelas do Google BigQuery devido a problemas de codificação de transferência ou conteúdo HTTP.  Essa correção garante fluxos de trabalho estáveis de carregamento de dados. (NEO-66989)

* Resolução de uma vulnerabilidade de travessia de caminho no método `File.list()` em fluxos de trabalho. Esse aprimoramento de segurança impede o acesso não autorizado ao diretório e protege arquivos confidenciais. (NEO-77898)

* Correção de um problema em que os logs de entrega de SMS não eram atualizados corretamente para o status &quot;recebido no dispositivo móvel&quot;. Esse aprimoramento garante relatórios de entrega precisos. (NEO-78843)

* Correção de erros de logon no Adobe Campaign Classic ao usar o Azure Federated Data Access (FDA). Agora, usuários podem fazer logon com êxito por meio do console do cliente. (NEO-79373)

* Correção de uma falha nos fluxos de trabalho causada pelo método `CCurlAzureBlobStorage::UploadStream()`. Essa melhoria garante uma execução estável do fluxo de trabalho. (NEO-79598)

* Dois sinalizadores de compilação críticos (`ControlFlowGuard` e `StackProtection`) foram ativados no Windows para aprimorar a segurança do produto e reduzir os riscos de exploração. (NEO-80145)

* Correção de um problema em que os status de evento eram enviados incorretamente enquanto o BroadLog estava em um estado de falha. Esse aprimoramento garante a precisão dos relatórios de eventos. (NEO-80245)

* O token de acesso e de atualização POP3 OAuth agora são salvos no banco de dados e o erro `Authentication failure: unknown user name or bad password` não aparece mais após a expiração do token de atualização.  (NEO-80683)

* Uma opção `XApiKey` agora é usada como um valor para a ID do cliente ao se conectar ao Adobe Analytics, em vez da ID do cliente da conta externa do Marketing Cloud (MAC). (NEO-80434)

* Resolvido um problema em que usuários do InMail encontravam erros de autenticação devido à expiração do token. Os usuários agora podem testar a conexão e reiniciar o servidor para resolver problemas semelhantes. (NEO-80683)

* Funcionalidade aprimorada da API de análise, garantindo que todas as chamadas de análise usem uma chave de API consistente (Campaign1) para autenticação, mesmo ao alternar para uma ID de cliente aleatória.  Isso garante um rastreamento de análise contínuo. (NEO-80434)

* O conector Federated Data Access (FDA) do BigQuery foi aprimorado, permitindo que usuários ajustem o período de tempo limite para consultas. Essa melhoria evita erros de tempo limite durante consultas de longa duração. (NEO-81222)

* O processo de atualização da versão <!--7.4.1--> do Campaign foi revisto para incluir as dependências necessárias. Esse aprimoramento simplifica o processo de atualização para usuários. (NEO-81433)

* Correção de um problema de falha do console ao usar um subfluxo de trabalho junto a um campo `enum`. Essa melhoria garante uma execução estável do fluxo de trabalho. (NEO-81864)

* Resolvido um problema em que os processos derivados do MTA ficavam paralisados, bloqueando os slots de entrega. Essa correção garante operações de entrega fluidas para comunicações por push e WhatsApp. (NEO-82351)

* Correção de um problema no qual as entregas ficavam paralisadas em personalização pendente devido a atividades de entrega pausadas. Esse aprimoramento garante a execução bem-sucedida da entrega. (NEO-82781)

* Aprimoramento da funcionalidade de logon do IMS ao aproveitar o ponto de acesso do Campaign IO para autenticação. Essa melhoria simplifica o processo de logon. (NEO-82838)

* Corrigidos novamente os erros de tempo limite do Federated Data Access (FDA) do Google BigQuery para garantir uma implementação estável pós-hotfix da execução da consulta. (NEO-82923)

* Resolvido um problema de espaço ao carregar grandes volumes de dados em tabelas do Teradata. Esse aprimoramento garante operações estáveis de carregamento de dados. (NEO-83252)

* Correção de um problema em que as consultas GCP falhavam devido a incompatibilidades de data e carimbo de data/hora <!--after upgrading to version 9383-->. Esse aprimoramento garante a compatibilidade da consulta. (NEO-83826)

* Resolução de falhas de entrega causadas pela retomada de atividades de entrega pausadas. Essa correção garante a execução bem-sucedida da entrega. (NEO-83809)

* Correção de erros de autenticação com o conector Federated Data Access (FDA) do Snowflake ao usar a autenticação de chave privada. Esse aprimoramento garante conexões de banco de dados bem-sucedidas. (NEO-84024)

* Alterações de monitoramento implementadas para resolver o bloqueio de slot derivado do MTA causado por processos paralisados. Esse aprimoramento garante operações de entrega fluidas. (NEO-84553)

* Verificações de espera do Javascript reforçadas para resolver o bloqueio de slot derivado do MTA causado por processos em um estado de funcionamento. Essa correção garante operações de entrega estáveis. (NEO-85150)

