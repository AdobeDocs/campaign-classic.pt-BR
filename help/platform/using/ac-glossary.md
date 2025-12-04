---
product: campaign
title: Glossário do Adobe Campaign
description: Glossário do Adobe Campaign
feature: Overview
role: User, Developer
level: Beginner
exl-id: 81f207a0-bb72-450b-abe4-0b229b6b1f3a
source-git-commit: a85d94e8ff66e8468b4fe2f071df48437393bbce
workflow-type: tm+mt
source-wordcount: '6202'
ht-degree: 99%

---

# Glossário do Adobe Campaign{#ac-glossary}

Abaixo está a definição dos termos principais e conceitos no Adobe Campaign, com links para a documentação relacionada. Clique em um termo para exibir sua definição.

## A - D{#sec-1}

+++**Teste A/B**

O teste A/B é um recurso que permite ao usuário definir duas a três variantes de email: cada variante é enviada para amostras de população para determinar qual tem o melhor resultado. Uma vez determinada, a variante vencedora é então enviada para a população restante.

Saiba mais sobre [Teste A/B](../../delivery/using/get-started-a-b-testing.md).
+++

+++**Gerenciamento de acesso**

O gerenciamento de acesso permite que administradores atribuam acesso e permissões aos usuários do Adobe Campaign. As permissões incluem a capacidade de exibir e/ou usar recursos do Adobe Campaign, como executar workflows, definir esquemas e gerenciar públicos-alvos.

Saiba mais sobre [Gerenciamento de acesso](access-management.md).
+++

<!--
+++**ACS Connector**

ACS Connector (Prime Offering) bridges Adobe Campaign v7 and Adobe Campaign Standard. It is an integrated feature in Campaign v7 that automatically replicates data to Campaign Standard, uniting the best of both applications. Campaign v7 has advanced tools to manage the primary marketing database. The data replication from Campaign v7 allows Campaign Standard to leverage the rich data in a user-friendly environment. 

Learn more about [ACS Connector](../../integrations/using/acs-connector-principles-and-data-cycle.md).
+++
-->

+++**Atividade**

Uma atividade é um item da paleta, que é adicionado a um fluxo de trabalho para definir uma funcionalidade de execução. A atividade é um container que executa uma tarefa. Em um diagrama de fluxo de trabalho, uma determinada atividade pode produzir várias tarefas, principalmente quando houver ações recorrentes (periódicas) ou em loop.

Saiba mais sobre atividades de fluxo de trabalho na [documentação do Campaign v8]&#x200B;(https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/activities
.html?lang=pt-BR){target="_blank"}.
+++

+++**Perfil ativo**

Os perfis são considerados ativos se tiverem sido direcionados ou comunicados nos últimos 12 meses por meio de qualquer canal. De acordo com o contrato, cada uma das instâncias do Campaign é provisionada com uma quantidade específica de perfis ativos que são contados para fins de faturamento.

Saiba mais sobre [Perfis ativos](../../platform/using/about-profiles.md#active-profiles).
+++

+++**Atividade de fluxo de trabalho de aprovação**

*Contexto: Marketing distribuído do Campaign*

A atividade de Aprovação Local é uma atividade de fluxo de trabalho usada para configurar um processo de aprovação de entrega antes que as mensagens sejam enviadas.

+++

+++**Público-alvo**

Um público-alvo é o conjunto de perfis que atendem aos critérios de uma definição de filtro, com base em regras e atributos.

Saiba mais sobre públicos-alvo na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=pt-BR){target="_blank"}.
+++

+++**Trilha de auditoria**

A trilha de auditoria captura em tempo real uma lista abrangente de ações e eventos que ocorrem na sua instância do Adobe Campaign. Ele inclui uma maneira de autoatendimento para acessar um histórico de dados que ajudam a responder perguntas como: o que aconteceu com seus fluxos de trabalho e quem os atualizou por último ou o que seus usuários fizeram na instância .

Saiba mais sobre [Trilha de auditoria](../../production/using/audit-trail.md).
+++

<!--
----DUPLICATE WITH THE "CAMPAIGN" ENTRY?---
+++**Automated campaigns**

Campaigns that run on a schedule, such as for targeting recipients who have a birthday or an anniversary. Can also be used to execute look-ahead and look-back logic, such as who purchased yesterday or who has a payment due tomorrow.

Learn more about [Campaigns](../../campaign/using/designing-marketing-campaigns.md).
+++
-->

+++**Modo de lote**

*Contexto: Interação do Campaign*

No contexto da Interação do Campaign, o modo de lote permite que o motor de oferta selecione a melhor oferta (ou ofertas) para um conjunto de contatos. As regras de elegibilidade/priorização são aplicadas a todos os contatos do conjunto.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Campanha**

O Campaign é uma interface para coordenar, definir e executar campanhas de marketing. Campanhas podem conter dados relacionados a fluxos de trabalho, entregas, documentos e outros em uma única interface fácil de usar.

Saiba mais sobre campanhas na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html?lang=pt-BR){target=_blank}.
+++

<!--
-----NOT USEFUL HERE?-----
+++**Changeover process**

*Context: Campaign Interaction*

In the context of Campaign Interaction, the changeover process is an activated process in an identified environment, responsible for directing the call to an anonymous environment if the contact has not been explicitly and/or implicitly identified.

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++
-->

+++**Canal**

Um canal é um meio pelo qual uma comunicação é enviada. Os canais integrados no Adobe Campaign são email, SMS, correspondência direta, notificações por push, LINE e X (anteriormente conhecido como Twitter). Os canais personalizados podem ser implementados para requisitos de canal fora do padrão.

Saiba mais sobre [Canais](../../delivery/using/communication-channels.md).
+++

+++**Console do cliente**

O console do cliente do Campaign é um cliente avançado que permite a conexão com seu(s) servidor(es) de aplicativos do Campaign. O aplicativo executável (.exe) do console do cliente é instalado em um computador com um sistema operacional Microsoft Windows. O console do Campaign Client centraliza todos os recursos e configurações.

Saiba mais sobre o [Console do Cliente](../../platform/using/adobe-campaign-workspace.md).
+++

+++**Aprovação de conteúdo**

Aprovação de conteúdo é o processo no qual um Operador ou grupo de Operadores à parte aprova o conteúdo de uma entrega antes que ela possa ser enviada.

Saiba mais sobre a aprovação de conteúdo na [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/automation/campaign-orchestration/marketing-campaign-approval){target="_blank"}.

+++

+++**Grupos de controle**

Use Grupos de controle para medir o impacto de suas campanhas excluindo parte dos públicos-alvos. Os operadores podem comparar o comportamento da população do público-alvo que recebeu a mensagem com o comportamento dos contatos que não foram direcionados. Com base nos logs de envio, os operadores também poderão direcionar um grupo de controle em campanhas futuras.

Saiba mais sobre grupos de controle na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=pt-BR#add-a-control-group){target="_blank"}.
+++

+++**Painel de controle**

O Painel de controle ajuda os administradores de produtos do Adobe Campaign a aumentar a eficiência em seu trabalho, permitindo que eles gerenciem configurações e monitorem o uso de cada uma de suas instâncias. Sua interface intuitiva permite que eles monitorem facilmente o uso dos principais ativos e realizem tarefas administrativas, como adicionar endereços IP na lista de permissões, monitorar o armazenamento SFTP, gerenciar chaves e muito mais.

Saiba mais sobre o [Painel de controle](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=pt-BR).
+++

+++**Cubos**

*Contexto: análise de marketing*

Cubo é uma ferramenta de exploração de dados intuitiva do Adobe Campaign que ajuda os usuários a criar e compartilhar relatórios dinâmicos.

Saiba mais sobre os [Cubos](../../reporting/using/ac-cubes.md).
+++

+++**Recursos personalizados**

O Adobe Campaign vem com um modelo de dados predefinido, em que os tipos de dados são definidos por meio da instalação de vários pacotes. Os operadores podem enriquecer o modelo de dados fornecido ao estender os recursos para adicionar campos personalizados ou tabelas personalizadas, como tabelas de transações ou de produtos.

Saiba mais sobre [Recursos personalizados](../../configuration/using/about-schema-edition.md).
+++

+++**Modelo de dados**

O modelo de dados do Campaign é um conjunto de esquemas que definem os tipos de dados e seus relacionamentos (links). O modelo de dados é uma definição abstrata que é implementada fisicamente com um banco de dados que contém os dados reais.

Saiba mais sobre o [Modelo de dados](../../configuration/using/about-data-model.md).
+++

+++**Fluxo de trabalho de limpeza do banco de dados**

O fluxo de trabalho de limpeza do banco de dados exclui dados obsoletos para evitar o seu crescimento exponencial. O fluxo de trabalho é acionado automaticamente sem a intervenção do usuário.

Saiba mais sobre [Fluxo de trabalho de limpeza do banco de dados](../../production/using/database-cleanup-workflow.md).
+++

<!--
----UNCLEAR----
+++**Dedicated server**

*Context: Transactional Messaging*

Dedicated execution server(s) to leverage Transactional Messaging. A server can typically process up to 50,000 Engine Calls per hour. The "Per-Dedicated Server" designation does not necessarily have a 1:1 correlation with a physical server as Adobe may utilize virtualization technologies to achieve the equivalent effect.

Learn more about [Transactional Messaging](../../message-center/using/about-transactional-messaging.md).
+++
-->

+++**Avaliação da entrega**

*Contexto: entregabilidade por email*

A capacidade de entrega permite medir o sucesso das campanhas que chegam à caixa de entrada dos destinatários sem rejeição ou sem serem marcadas como spam. Mais precisamente, a capacidade de entrega de email refere-se ao conjunto de características que determinam o potencial de uma mensagem de alcançar seu destino, por meio de um endereço de email pessoal, dentro de um curto período e com a qualidade esperada em termos de conteúdo e formato.

Saiba mais sobre [Entregabilidade](../../delivery/using/about-deliverability.md).
+++

+++**Entrega**

Uma entrega é um item específico de comunicação de marketing que é enviado para um público-alvo em um canal específico (email, SMS, notificação por push etc.). Também conhecido como &quot;contato&quot; na terminologia de marketing.

Saiba mais sobre [Entregas](../../delivery/using/communication-channels.md).
+++

+++**Análise de entrega**

A análise de entrega é a preparação da entrega. Esse processo combina o conteúdo com os dados de perfil do destinatário para produzir o email personalizado que o destinatário recebe. A lógica de análise de entrega pode excluir destinatários do público-alvo ou interromper a entrega completamente, com base na lógica definida. Esse processo também inclui a avaliação da lógica do conteúdo dinâmico e a inserção de ofertas específicas ao perfil de destinatário individual.

Saiba mais sobre a análise de entrega na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/delivery-analysis.html?lang=pt-BR){target="_blank"}.
+++

+++**Logs de entrega**

Os logs de entrega contêm informações geradas ao enviar uma mensagem. Esses logs mostram os detalhes do envio, que mensagem foi preparada, ignorada, enviada ou que está com falha. Elas podem ser acessadas diretamente no painel de entrega.

Saiba mais sobre [Logs de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"}.
+++

<!--
----STRANGE IN DOCS?----
+++**Delivery fundamentals**

*Context: Email Deliverability*

Adobe Campaign Deliverability Fundamentals Consulting Service provides email deliverability consultation and reputation management to support customers using Adobe Campaign deliveries.

Learn more about [Deliverability](../../delivery/using/about-deliverability.md).
+++
-->

+++**Outline de entrega**

*Contexto: correspondência direta*

A descrição de entrega indica um conjunto estruturado de elementos (documentos, lojas, cupons promocionais, etc.) criados pela empresa para uma campanha específica. Ela é usada no contexto de entregas de correspondência direta.

Saiba mais sobre [Correspondência direta](../../delivery/using/about-direct-mail-channel.md).
+++

+++**assistente de implantação**

O assistente de implantação define os parâmetros da instância do Campaign, como o namespace padrão, o agendamento de limpeza do banco de dados, os períodos de retenção de dados e outras configurações técnicas.

Saiba mais sobre o [assistente de implantação](../../installation/using/deploying-an-instance.md#deployment-assistant).
+++

+++**Análise descritiva**

A Análise descritiva é uma ferramenta de relatórios com reconhecimento de contexto que pode ser usada para examinar os dados na tabela de trabalho de um fluxo de trabalho, os dados selecionados em uma pasta ou para aprofundar os públicos-alvo e as exclusões de entregas selecionadas.

Saiba mais sobre [Análise descritiva](../../reporting/using/about-descriptive-analysis.md)
+++

+++**Marketing distribuído**

*Contexto: marketing distribuído*

O complemento Marketing Distribuído oferece aos operadores do Campaign um espaço de trabalho colaborativo para implementar campanhas entre entidades centrais (sedes, departamentos de marketing, etc.) e entidades locais (pontos de venda, agências regionais, etc.). Essa cooperação é baseada em um espaço de trabalho compartilhado conhecido como **lista de pacotes de campanha**, em que modelos de campanha e instâncias criadas centralmente são oferecidos a entidades locais.

Saiba mais sobre Marketing distribuído na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/distributed-marketing/about-distributed-marketing.html?lang=pt-BR){target="_blank"}.
+++

+++**Distribuição de valores**

A Distribuição de valores é uma ferramenta que mostra a distribuição dos valores de um atributo de esquema que existe atualmente no banco de dados. Isso ajuda a determinar quais valores estão disponíveis, suas contagens e porcentagens e evitar problemas com capitalização e ortografia de valores ao criar uma consulta ou expressão.

Saiba mais sobre a [Distribuição de valores](../../platform/using/about-queries-in-campaign.md)
+++

+++**Delegação de domínio**

A configuração de subdomínios permite definir uma subseção do domínio (tecnicamente, uma “zona DNS”) para uso com o Adobe Campaign. A delegação de domínio permite que a Adobe controle e mantenha todos os aspectos do DNS necessários para entregar, renderizar e rastrear campanhas de email.

Saiba mais sobre [Delegação de domínio](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=pt-BR)
+++

## E - H {#sec-2}

<!--
----DEPRECATED------>
+++**E4X**

E4X é a versão do Javascript usada no Adobe Campaign Classic. Algumas vezes chamado de ECMAScript, essa é uma extensão do Javascript que permite a combinação de Javascript e elementos primitivos de XML no mesmo código. Observe que o E4X é classificado como uma linguagem obsoleta.
+++


+++**Regras de elegibilidade**

*Contexto: interação de campanha*

Regras de elegibilidade são restrições aplicadas a um ambiente, categoria ou oferta sobre o período de validade, público-alvo e peso. Eles permitem que os operadores garantam que uma oferta esteja alinhada com o contato direcionado. No ambiente da oferta, as regras de elegibilidade incluem regras de apresentação aplicadas às ofertas e aos destinatários do público-alvo. Nas categorias, as regras de elegibilidade permitem que os operadores limitem a validade da categoria no tempo, definam temas de aplicativo e determinem os destinatários do público-alvo. Eles também podem receber um peso multiplicador por determinado período. Isso permite que os operadores compartilhem as regras para ofertas em outras categorias e simplifiquem a administração. Nas ofertas, as regras de elegibilidade permitem que os operadores limitem a validade de ofertas no tempo e determinem os destinatários do público-alvo.

Saiba mais sobre [Regras de elegibilidade](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Oferta elegível**

*Contexto: interação de campanha*

Uma oferta elegível é uma oferta que atende às restrições definidas upstream que podem ser oferecidas de forma consistente a um público-alvo.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**CCO de email**

O recurso Cco de email envia uma cópia exata no formato EML de um email entregue correspondente, que é salvo em um endereço de email CCO dedicado, onde os emails podem ser processados e arquivados pelo remetente em um sistema externo.

Saiba mais sobre CCO do email na [Documentação do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/emails/email-bcc.html?lang=pt-BR){target="_blank"}.
+++

<!--
-----STRANGE FOR DOCS?----
+++**Email volume commitment**

The anticipated emails sent per year as set forth in the Sales Order. This is the total annual email volume commitment, including emails sent but not delivered due to delivery errors such as: non-delivery of a message including but not limited to email address errors, hard bounces, soft bounces, email filters of mail clients, and email blacklists. 
+++
-->

<!--
-----USEFUL FOR DOCS?----
+++**Engine call**

An engine call is a server call that starts real-time processing on server side for the extraction of data, such as data relating to surveys, WebApps, JSSP, APIs, mobile app registrations, etc. Engine calls must be licensed in packs of 5,000 Engine Calls per day.
+++
-->

+++**Atividade de enriquecimento**

A Atividade de enriquecimento é uma atividade avançada de fluxo de trabalho que permite aos Operadores enriquecer os dados gerados da tabela de trabalho que serão processados no fluxo de trabalho. Esta atividade é geralmente usada após atividades de direcionamento ou após a importação de um arquivo e antes de atividades que permitem o uso de dados direcionados. Os enriquecimentos podem transformar os dados de transição de entrada e configurar a atividade para concluir a transição de saída com dados aprimorados. Com ela, o operador pode combinar dados provenientes de vários conjuntos ou criar links para um recurso temporário.

Saiba mais sobre a atividade de enriquecimento na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html?lang=pt-BR){target="_blank"}.
+++

+++**Enumerações**

Uma enumeração é um tipo de dados definido em esquemas ou no nível da Platform que define os valores de entrada válidos para um campo. Enumerações aparecem na interface e nos construtores de consultas como uma lista de opções.

Saiba como **trabalhar com enumerações** na [documentação do Adobe Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.
+++

+++**Visualização do Explorer**

A visualização do Explorer é uma exibição hierárquica das pastas que contêm artefatos e dados do Adobe Campaign. Observe que o sistema de pastas no Adobe Campaign não funciona como uma visualização de árvore típica, em que cada pasta retém dados de um tipo específico, como Entregas, Fluxos de trabalho ou Ofertas.


Saiba mais sobre a interface do usuário do Campaign na [documentação do Adobe Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

+++

+++**Contas externas**

Contas externas são pontos de entrada e saída para que o produto se conecte a outros ambientes e tecnologias. As contas externas definem os parâmetros de conexão que o produto usa para enviar dados para ou receber dados de outras fontes. Tipos típicos de conta externa são conexões para sites SFTP, telecoms para dar respaldo ao envio de SMS, caixas de correio para as rejeições de processamento ou conexões a bancos de dados externos.

Saiba mais sobre [Contas externas](../../installation/using/external-accounts.md).
+++

+++**Gerenciamento de fadiga**

*Contexto: otimização de campanha*

O gerenciamento de fadiga controla a frequência e a quantidade de mensagens para evitar a solicitação excessiva de destinatários e é aplicado com frequência usando uma regra de tipologia.

Saiba mais sobre o gerenciamento de fadiga na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/pressure-rules.html?lang=pt-BR){target="_blank"}.
+++

+++**Federated Data Access (FDA)**

O Federated Data Access oferece suporte à extensão do modelo de dados do cliente para incluir um banco de dados de terceiros. Ele detectará automaticamente a estrutura das tabelas direcionadas e usará os dados das fontes SQL. Você pode acessar dados externos sem alterar a estrutura de dados do Adobe Campaign.

Saiba mais sobre [Federated Data Access](../../installation/using/about-fda.md).
+++

+++**Aprovação de extração de arquivo**

*Contexto: correspondência direta*

A aprovação de extração de arquivo é o processo no qual um Operador ou grupo de Operadores à parte aprova o conteúdo e a configuração de um arquivo extraído antes de ele ser enviado a um fornecedor externo, como para uma entrega de correspondência direta.

Saiba mais sobre a aprovação de extração de arquivo na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/direct-mail.html?lang=pt-BR#validating){target="_blank"}.
+++

+++**Dimensão do filtro**

A dimensão do filtro é o esquema que contém os dados ou atributos usados por uma consulta para filtrar as linhas desejadas. O esquema Dimensão do filtro deve ser vinculado diretamente à dimensão de direcionamento definida para permitir que o Adobe Campaign cruze a associação do banco de dados e retorne as linhas do entrevistado.

Saiba mais sobre a dimensão do filtro na [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows#targeting-and-filtering-dimensions){target="_blank"}.
+++

+++**Pasta**

Uma pasta é um item de visualização do Explorer que mantém registros de banco de dados de um tipo de dados específico. A exceção é o tipo Pasta genérica usado como um elemento organizador que não contém dados propriamente dito, apenas outras pastas.

Saiba mais sobre a interface do usuário do Campaign na [documentação do Adobe Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

+++

+++**Exibição de pasta**

A Exibição de pastas é um tipo de pasta especial do Explorer usada para exibir todos os registros de um tipo de dados selecionado, independentemente da pasta à qual pertence. As Exibições de pastas são usadas como uma ferramenta administrativa para gerenciar dados particionados ou que são distribuídos entre muitas pastas.

Saiba mais sobre a interface do usuário do Campaign na [documentação do Adobe Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.
+++

+++**Formulários**

Formulários definem a representação da interface para um tipo de esquema específico. Formulários são o meio usado para criar e editar facilmente elementos de dados no produto, como Destinatários, Entregas e Campanhas. Todos os elementos de interface no Adobe Campaign são criados no próprio produto usando formulários. Observe que os formulários são opcionais e nem todos os esquemas têm formulários.

Saiba mais sobre [Formulários](../../configuration/using/identifying-a-form.md).
+++

<!--
-----USEFUL HERE?-----
+++**Generated SQL query**

The SQL code generated for the underlying database when an operator manipulates a schema. Schemas define the data types that are then implemented using database tables and columns. The SQL generated for schema manipulation (such as in a query) is based on the installed database type. Thus, the database can be swapped to a different type and the queries in Campaign remain unchanged. Adobe refers to this functionality as being database-agnostic.

Learn more about [Generated SQL queries](../../platform/using/steps-to-create-a-query.md#step-6---preview-data).
+++
-->

+++**Heatmap**

Campaign Heatmap é uma tabela que mostra informações de execução do fluxo de trabalho para um período de 24 horas. Ele exibe a distribuição de fluxos de trabalho entre o período por hora e intervalos de 5 minutos. O Heatmap é usado para avaliar a carga do servidor e determinar as atividades do fluxo de trabalho que estão consumindo mais recursos.

Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/automation/workflows/monitoring-workflows/heatmap){target="_blank"}.
+++

+++**Implantação híbrida**

A implantação híbrida é uma combinação de serviços sob demanda e software local implantada para funcionar em conjunto.

Saiba mais sobre [Implantação híbrida](../../installation/using/hosting-models.md#hybrid).

+++

## I - L {#sec-3}

<!-- added more details but maybe still not clear/useful here? -->
+++**Modo de identificação**

*Contexto: interação de campanha*

O modo de identificação refere-se ao status de um contato. Pode ser explícito, implícito ou anônimo.

* **explícito**: o contato é identificado após fazer logon na interface do canal.
* **implicit**: o contato foi identificado por um cookie (permanente ou de sessão). Ele pode ser processado como um contato anônimo ou identificado.
* **anonymous**: o contato não pode ser identificado.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

<!--
----NOT USEFUL HERE?----
+++**Image serving**

The functionality that supplies the images embedded in emails to the delivery's recipients. The insertion of the images based on an emails system's "download images" functionality is what generates an "open" entry in Campaign's tracking logs.

Learn more about [Image serving](../../delivery/using/defining-the-email-content.md#adding-images).
+++
-->

+++**Interação de entrada**

*Contexto: interação de campanha*

Uma interação de entrada é uma interação que segue uma chamada recebida gerada pela ação de um contato em um canal, como Web, central de atendimento ou dispositivo móvel. Esse tipo de interação geralmente é processado no modo unitário (ou seja, por destinatário).

Saiba mais sobre [Interação de entrada](../../interaction/using/about-inbound-channels.md).
+++

+++**Renderização da caixa de entrada**

A renderização da caixa de entrada é a geração de visualizações de email, o que garante que a mensagem será exibida aos destinatários de forma ideal em uma variedade de clientes Web, Webmails e dispositivos. O Adobe Campaign aproveita o Litmus, que permite que os criadores de conteúdo de email visualizem o conteúdo de suas mensagens em mais de 70 renderizadores de email, como a caixa de entrada do Gmail ou o cliente Apple Mail.

Saiba mais sobre [Renderização da caixa de entrada](../../delivery/using/delivery-dashboard.md#delivery-rendering).
+++

+++**Configurações de instância**

As configurações de instância são detalhes de configuração de uma instância do Adobe Campaign. Essas configurações são definidas no assistente de implantação (Ferramentas>Avançado>assistente de implantação) ou nos arquivos de configuração do servidor e/ou da instância.

Saiba mais sobre [Configurações de instância](../../installation/using/about-initial-configuration.md).

+++

+++**Processos (importação e exportação)**

Os processos são gerenciados por um sistema assistente que simplifica a importação e exportação de dados para dentro e para fora do produto. Os processos usam o sistema de modelos para simplicidade e consistência e podem ser definidos para execução de acordo com um cronograma.

Saiba mais sobre [processos de importação e exportação](../../platform/using/get-started-data-import-export.md).
+++

+++**Listas**

Uma lista é um conjunto de dados estático. Listas são públicos ou segmentos importados para o Campaign de outras fontes (Audience Manager, Experience Platform, banco de dados etc.) e são vistos na interface como Listas importadas.

Saiba mais sobre [Listas](../../platform/using/creating-and-managing-lists.md).
+++

+++**Cache local**

O cache local são as informações armazenadas localmente no computador do operador. As informações em cache são usadas pelo console para reduzir o tráfego necessário para o servidor e melhorar o desempenho. A limpeza periódica do cache local (no menu Arquivo) atualiza as informações armazenadas e melhora o desempenho e a estabilidade.

Saiba mais sobre [Cache local](../../platform/using/faq-campaign-classic-v7.md#how-do-i-clear-console-cache).
+++

## M - P {#sec-4}

+++**Gerenciamento dos recursos de marketing (MRM)**

*Contexto: Gerenciamento dos recursos de marketing (MRM)*

O módulo **Gerenciamento dos recursos de marketing (MRM)** no Adobe Campaign permite controlar ações de marketing em um modo colaborativo, fornecendo gerenciamento completo e rastreamento em tempo real das tarefas, orçamentos e recursos de marketing envolvidos. Os operadores do Adobe Campaign podem coordenar as ações e aprovar seu progresso em todos os estágios por meio de processos de validação completos e ferramentas de rastreamento apropriadas: relatórios, rastreamento de aprovações, notificações, fóruns de discussão etc.

Saiba mais sobre o MRM na [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/automation/mrm/about-marketing-resource-management){target="_blank"}.
+++

<!--
----ACS?----
+++**Localization**

This template type is used to manage multilingual messages.  It is available for Email and SMS messages and useable in standalone mode, within a workflow or in a recurring delivery. In the multilingual feature templates, the language management is based on variants. Each variant represents one language.  This functionality is available only in Adobe Campaign Standard.  
+++
-->

+++**Direitos nomeados**

Os direitos de acesso granular ao banco de dados usados para definir o acesso e os privilégios do Grupo de operadores (funções). Direitos nomeados são preenchidos durante a instalação do produto, importando vários pacotes que definem a funcionalidade específica da ferramenta. É possível criar direitos nomeados personalizados para dar suporte aos requisitos de negócios do cliente.

Saiba mais sobre [Direitos nomeados](../../platform/using/access-management-named-rights.md).
+++

+++**Namespace**

O namespace é uma partição que separa os tipos de dados do cliente dos tipos de dados nativos do Adobe Campaign no modelo de dados. Também é usado para facilitar a migração das definições de uma instância para outra, como mover um esquema ou modelo da instância de desenvolvimento para a instância de produção.

Saiba mais sobre os [Namespaces](../../configuration/using/about-schema-reference.md#identification-of-a-schema).
+++

<!--
----generic, not specific to campaign----
+++**Navigation bar**

The navigation bar is the navigation element running across the top of the interface. The navigation bar regroups the various core capabilities of the platform. Click a navigation bar link to display the set of functionalities related to this capability. The list of core capabilities you can access depends on the packages and add-ons you have installed and on your access rights. The purpose of the Navigation bar is to simplify screen management and increase productivity.

Learn more about [Navigation Bar](../../platform/using/adobe-campaign-workspace.md#browsing-pages).
+++
-->

+++**Árvore de navegação**

A árvore de navegação é a navegação principal no modo de exibição Explorer do Adobe Campaign. A árvore de navegação funciona como um navegador de arquivos (por exemplo, Windows Explorer). As pastas podem conter subpastas. Selecionar um nó exibe a visualização correspondente ao nó. A visualização exibida é uma lista associada a um esquema e um formulário de entrada para editar a linha selecionada. É possível personalizar a árvore de navegação e definir permissões em pastas.

Saiba mais sobre a interface do usuário do Campaign na [documentação do Adobe Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

+++

+++**Objetivos**

*Contexto: Gerenciamento de recursos de marketing (MRM)*

Dentro da campanha, do programa ou do plano, os Operadores podem definir uma lista de objetivos. Esses valores são quantificados para serem alcançados. No final da campanha, do programa ou do plano, o módulo MRM permite ao Operador comparar os objetivos e os resultados em relatórios dedicados.

Saiba mais sobre objetivos na [documentação do Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/mrm/creating-and-managing-tasks.html?lang=pt-BR#expenses-and-revenues){target=_blank}.
+++

+++**Catálogo de ofertas**

*Contexto: Interação com o Campaign*

Um catálogo de ofertas é um conjunto de ofertas definido no Adobe Campaign que podem ser selecionadas durante uma interação. O catálogo é organizado hierarquicamente com cada nó correspondente a uma categoria.

Saiba mais sobre o [Catálogo de ofertas](../../interaction/using/offer-catalog-overview.md).
+++

+++**Contato da oferta**

*Contexto: Interação com o Campaign*

Um contato de oferta é um contato de uma interação de entrada. Durante o processamento de chamadas do motor, o contato é associado a uma dimensão de direcionamento. Contatos anônimos e não identificados são atribuídos à dimensão de direcionamento de visitantes. Há dois tipos de contatos, identificados e anônimos:

* **Identified contact**: um contato que foi identificado voluntariamente no canal. Em interações de saída, o contato é identificado automaticamente.
* **Anonymous contact**: um contato que não tenha assinado voluntariamente por meio do canal, mas pode ser identificado implicitamente por meio de um cookie. Essa terminologia é usada apenas para interações de entrada.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Ambiente de design de oferta**

*Contexto: Interação do Campaign*

O **Ambiente de design** de oferta é o ambiente no qual os operadores criam ofertas, definem regras de tipologia e selecionam o esquema que será direcionado pelas ofertas. A tabela para armazenar propostas de oferta geradas também é definida pelo ambiente. Por padrão, o complemento Interaction vem com um ambiente de **Design** e um ambiente **Live** vinculado. Ambos os ambientes são pré-configurados para ter como público-alvo a tabela de destinatários integrada.

Saiba mais sobre [Ambientes de criação de ofertas](../../interaction/using/fundamental-principles.md).
+++

+++**Arbitragem do motor de oferta**

*Contexto: interação de campanha*

O mecanismo de oferta seleciona as ofertas que serão exibidas em um ambiente (ofertas elegíveis). O princípio de arbitragem classifica as ofertas por prioridade de acordo com os critérios definidos nas categorias e ofertas.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Remoção do mecanismo de oferta**

*Contexto: interação de campanha*

A remoção do mecanismo de ofertas é o processo de exclusão de ofertas que não são elegíveis para seleção. Executado antes da etapa de arbitragem do mecanismo de oferta.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Ambiente de oferta**

*Contexto: interação de campanha*

O ambiente de oferta é a pasta raiz que define um catálogo de ofertas, seus espaços disponíveis e os filtros predefinidos do ambiente. Os operadores precisam criar um ambiente para cada dimensão de direcionamento. Há dois tipos de ambientes de oferta: Design e Em tempo real.

Saiba mais sobre [Ambientes de oferta](../../interaction/using/fundamental-principles.md).
+++

+++**Ambiente de oferta em tempo real**

*Contexto: interação de campanha*

O ambiente Oferta em tempo real está vinculado ao **Ambiente de design** de uma campanha. Ele contém ofertas de somente leitura cujo conteúdo e elegibilidade foram aprovados por meio do **Design environment**. Eles podem ser selecionados para apresentação em um site ou para serem inseridos em uma mensagem de saída.

Saiba mais sobre [Ambientes de oferta em tempo real](../../interaction/using/fundamental-principles.md).
+++

+++**Regras de apresentação da oferta**

*Contexto: interação de campanha*

As regras de apresentação de ofertas são regras de tipologia referenciadas no ambiente de ofertas que permitem aos operadores excluir ofertas específicas, tendo em conta o histórico de apresentações do destinatário.

Saiba mais sobre [Regras de apresentação da oferta](../../interaction/using/managing-offer-presentation.md#presentation-rules-overview).
+++

+++**Visualização da oferta**

*Contexto: interação de campanha*

Esta é a visualização da oferta conforme ela é exibida em sua pasta. Pode ser acessada na guia de visualização da oferta ou no perfil de contato.

Saiba mais sobre [Visualização da oferta](../../interaction/using/creating-an-offer.md#previewing-the-offer).
+++

+++**Apresentação da oferta**

*Contexto: interação de campanha*

Uma apresentação da oferta é o resultado da ação que consiste em apresentar uma oferta a um contato em um determinado espaço de ofertas, por exemplo, o banner em um site, um conteúdo de email ou SMS. Esse resultado é armazenado na tabela de apresentações da oferta que define a oferta, o destinatário e o carimbo de data e hora, fornecendo um registro de todas as ofertas que um destinatário recebeu.

Saiba mais sobre [Apresentações da oferta](../../interaction/using/creating-offer-spaces.md#offer-proposition-statuses).
+++

+++**Representação da oferta**

*Contexto: interação de campanha*

A representação da oferta é a informação usada pelo canal para exibir a oferta. A representação da oferta pode ser construída a partir da função de renderização do espaço em que a oferta é representada ou inserida diretamente na interface (por exemplo, no bloco HTML). Uma oferta pode ser representada por um espaço.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Simulação de oferta**

*Contexto: interação de campanha*

Uma simulação de oferta permite que operadores testem a distribuição de ofertas em um escopo definido (data de entrega, segmento de público-alvo, número de ofertas, tema, etc.) antes de enviá-las. Pode ser usada para ajustar as prioridades da oferta e as regras de elegibilidade para maximizar a eficiência da oferta.

Saiba mais sobre [Simulações de oferta](../../interaction/using/about-offers-simulation.md).
+++

+++**Espaço de oferta**

*Contexto: interação de campanha*

Um espaço de ofertas é uma pasta que define o local onde a oferta é exposta. A definição de um espaço permite especificar o canal usado, criar o conteúdo da oferta e especificar as ofertas apresentadas. Um espaço de ofertas é uma interface entre o canal e o mecanismo de oferta.

Saiba mais sobre o [Espaço de ofertas](../../interaction/using/creating-offer-spaces.md).
+++

+++**Temas da oferta**

*Contexto: interação de campanha*

Os temas de oferta são palavras-chave definidas em uma categoria, que permite aos operadores filtrar as ofertas quando são apresentadas. Os temas permitem a seleção não hierárquica de ofertas da estrutura do catálogo.

Saiba mais sobre [Temas da oferta](../../interaction/using/integrating-an-offer-via-the-wizard.md).
+++

+++**Peso da oferta**

*Contexto: interação de campanha*

O peso da oferta é baseado em fórmulas que definem precisamente a relevância de uma oferta para permitir que o mecanismo selecione a oferta mais relevante. Os pesos são definidos nas ofertas e os multiplicadores são definidos nas categorias. Ofertas elegíveis são consideradas em ordem decrescente de peso.

Saiba mais sobre [Peso da oferta](../../interaction/using/creating-an-offer.md#offer-weight).
+++

+++**Operador**

Um operador é um usuário do Adobe Campaign que tem permissões para fazer logon e executar ações. Os operadores são associados a grupos de operadores e herdam os direitos e privilégios desses grupos. Também é possível atribuir direitos nomeados diretamente aos operadores.

Saiba mais sobre [Operadores](../../platform/using/access-management-operators.md).
+++

+++**Grupos de operadores**

Os grupos de operadores permitem gerenciar funções para operadores do Campaign. Você pode definir grupos de operadores para atribuir direitos e, em seguida, associar os operadores a um ou mais grupos. Isso permite que você reutilize os direitos e torne os perfis de operadores mais consistentes. Também facilita o gerenciamento e a manutenção de perfis.

Saiba mais sobre [Grupos de operadores](../../platform/using/access-management-groups.md).
+++

+++**Options**

As opções são variáveis de nível da Platform usadas para definir configurações da instância do Campaign. As opções podem definir cronogramas (como para fluxo de trabalho de limpeza de banco de dados) ou outras definições globais no nível da plataforma.

Saiba mais sobre [Opções](../../installation/using/configuring-campaign-options.md).
+++

+++**Interação de saída**

*Contexto: interação de campanha*

Interação de saída é uma chamada para o mecanismo de interação de uma lista de contatos (usada para entrega de emails, correspondência direta etc.). As mesmas regras e processos são aplicados a cada contato. Esse tipo de interação geralmente é processado em modo de lote.

Saiba mais sobre [Interação de saída](../../interaction/using/about-outbound-channels.md).
+++

+++**Exportação/importação de pacotes**

Uma exportação de pacote é uma operação que consiste na geração de um arquivo XML que contém definições de objetos. Os pacotes são usados para migrar a funcionalidade e as definições de uma instância para outra. Eles também são usados para adicionar definições essenciais de produtos aos sistemas de backup e controle de origem.

Saiba mais sobre [Exportação/importação de pacotes](../../platform/using/working-with-data-packages.md).
+++

+++**Paleta**

A paleta fluxo de trabalho exibe as atividades disponíveis que podem ser adicionadas a um fluxo de trabalho. Esse componente é mostrado em um formato de tabulação com atividades de fluxo de trabalho agrupadas logicamente pelo uso. As atividades disponíveis na paleta são determinadas pelos complementos que foram instalados na instância do Campaign e pelo contexto que exibe o fluxo de trabalho.

Saiba mais sobre a paleta na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=pt-BR#add-and-link-activities){target="_blank"}.
+++

+++**Monitoramento de desempenho**

As informações de monitoramento de desempenho são exibidas na guia Monitoramento. Ela mostra métricas para o sistema subjacente, como uso de memória e CPU, estatísticas do servidor SMTP, processos do servidor e outras informações relevantes.

Saiba mais sobre o [Monitoramento de desempenho](../../production/using/monitoring-processes.md).
+++

+++**Blocos de personalização**

O Adobe Campaign oferece blocos de personalização integrados que podem ser inseridos nas entregas. Eles são dinâmicos, personalizados e contêm uma renderização específica. Por exemplo, você pode adicionar um logotipo, uma mensagem de saudação ou um link para uma mirror page. Vários blocos de personalização estão disponíveis por padrão. Você também pode definir blocos de personalização personalizados que permitirão otimizar a personalização da entrega. Os dados reais são inseridos em cada mensagem gerada durante a fase de análise da entrega.

Saiba mais sobre blocos de personalização na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html?lang=pt-BR){target="_blank"}.
+++

+++**Campo de personalização**

Um campo de personalização é uma única referência de campo de dados usada ao personalizar uma entrega para um destinatário específico. O valor de dados real é inserido durante a fase de análise da entrega.

Saiba mais sobre campos de personalização na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-fields.html?lang=pt-BR){target="_blank"}.
+++

+++**Variáveis de personalização**

As variáveis de personalização são partes do código em uma entrega que podem exibir textos diferentes a destinatários distintos com base em suas informações. Esses campos podem ser implementados como um campo ou bloco de personalização.

Saiba mais sobre [Variáveis de personalização](../../delivery/using/about-personalization.md).
+++

+++**Plano**

Um plano é um tipo de pasta usado para organizar atividades de marketing com base no calendário. As pastas de plano na visualização do Explorer definem unidades baseadas em tempo, como um ano, trimestre ou mês. As pastas de plano podem ser aninhadas e podem conter outras pastas de plano, pastas de programa ou campanhas.

Saiba mais sobre planos na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=pt-BR){target=_blank}.
+++

+++**Filtros predefinidos**

Filtros predefinidos são consultas que foram salvas para reutilização. O uso de filtros predefinidos aumenta a produtividade (porque são criados apenas uma vez), ajuda a criar consistência (porque todos os profissionais de marketing podem usá-los) e diminui as habilidades necessárias para o profissional de marketing, pois podem usar código ou lógica que talvez não consigam criar sozinhos.

Para mais informações sobre filtros, consulte a [documentação do Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.
+++

<!--
----DEPRECATED----
+++**Predictive Engagement Scoring**

Predictive engagement scoring predicts the probability of a recipient engaging with a message and the probability of opting out (unsubscribing) within the next seven days after the next email send. The probabilities are further divided into buckets according to the specific risk of disengagement, medium, or low. The model also provides the risk percentile rank for the customers to understand where the rank of a certain customer in relation to others. 

Learn more about [Predictive Engagement Scoring](../../platform/using/creating-filters.md).
+++
-->

+++**Chave primária**

A chave primária é o identificador exclusivo para cada registro em uma tabela de banco de dados. Uma tabela deve ter pelo menos uma chave. Como regra, as chaves são declaradas após o elemento principal do esquema e os índices. As chaves primárias não podem ser compostas (incluir vários campos).

Saiba mais sobre [Chave primária](../../configuration/using/schema/key.md).
+++

+++**Perfil**

Um perfil é um registro de informações que representam um cliente final, um cliente potencial ou lead. Cada perfil corresponde a um registro na tabela nmsRecipient ou em uma tabela externa contendo a ID do cookie, a ID do cliente, o identificador móvel ou outras informações relevantes para um canal específico.

Saiba mais sobre [Perfis](../../platform/using/about-profiles.md).
+++

+++**Programa**

Programas e pastas de subprogramas organizam atividades de marketing em torno de um objetivo comercial, como fidelidade, atração ou venda cruzada. Eles também podem representar períodos fiscais ou táticas de campanha, como eventos ou boletins informativos. Cada programa contém campanhas vinculadas a um calendário, que fornece uma visualização geral.

Saiba mais sobre programas na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=pt-BR){target=_blank}.
+++

+++**Recursos públicos**

A pasta Recursos públicos, no Adobe Campaign, armazena imagens hospedadas pelo servidor de aplicativos. As imagens nas entregas devem ser publicadas no servidor de aplicativos (ou em um servidor de hospedagem de imagem, se o Campaign estiver configurado dessa forma) para serem exibidas nas entregas, como emails.

Saiba mais sobre [Recursos públicos](../../installation/using/deploying-an-instance.md#managing-public-resources).
+++

+++**Push**

*Contexto: canal de aplicativo móvel*

As notificações por push são mensagens recebidas por aplicativos móveis. As notificações por push são configuradas para funcionar com o Adobe Campaign, incluindo o código SDK da Experience Platform no aplicativo móvel. Para push, dois canais de entrega estão disponíveis: iOS e Android.

Saiba mais sobre [Push](../../delivery/using/about-mobile-app-channel.md).
+++

## Q - T {#sec-5}

+++**Destinatário**

No Adobe Campaign, os destinatários são os perfis padrão direcionados para envio de entregas (emails, SMS, etc.) a clientes. Os dados do destinatário armazenados no banco de dados permitem filtrar o público-alvo e adicionar dados de personalização. Normalmente, são informações pessoais, de contato, demográficas e transacionais, mas podem ser qualquer tipo de informação que seja compatível com marketing e análise.

Saiba mais sobre [Destinatário](../../configuration/using/about-data-model.md).
+++

+++**Função de renderização**

*Contexto: interação de campanha*

A função de renderização é definida em um espaço de ofertas. É usada para construir sua representação da oferta com base nos atributos definidos na oferta. Há três modos diferentes de função de renderização: HTML, XML e texto.

Saiba mais sobre [Função de renderização](../../interaction/using/creating-offer-spaces.md).
+++

<!--
-----DID NOT FIND IN ACC DOCS, ACS?----
+++**Retargeting campaigns**

Campaigns that re-target the recipients of a previous delivery or deliveries.
+++
-->

+++**Schema**

Um esquema é um documento XML associado a uma tabela de banco de dados. Ele define a estrutura de dados e descreve a definição SQL da tabela. Os operadores manipulam esquemas no Campaign e o produto traduz suas ações no SQL necessário, que é executado no banco de dados.

Saiba mais sobre [Esquemas](../../configuration/using/about-schema-reference.md).
+++

+++**Extensão de esquema**

A extensão de esquema permite personalizar os esquemas prontos para uso para melhor atender aos casos de uso da empresa. Por exemplo, é possível adicionar o campo &quot;Fidelidade&quot; à tabela Destinatário.

Saiba mais sobre a [Extensão de esquema](../../configuration/using/extending-a-schema.md).
+++

+++**Seed addresses**

Seed addresses são usados para direcionar destinatários que não correspondem aos critérios de destino definidos. Dessa forma, os destinatários que estiverem fora do escopo de entrega podem recebê-lo, como qualquer outro destinatário do público-alvo receberia. Eles são adicionados ao público-alvo de uma mensagem para detectar qualquer uso fraudulento do seu banco de dados de destinatários ou para garantir a entrega.

Saiba mais sobre [Seed addresses](../../delivery/using/about-seed-addresses.md).
+++

<!--
-------ACS?-----
+++**Send-time optimization**

To improve the open rate of your messages, you can manually define a sending time per recipient. Each profile will receive the message at the specified date and time, whenever possible. Defining a sending time can be done at the delivery level or using a workflow.

Learn more about [Send-time optimization](../../delivery/using/about-seed-addresses.md:).
+++
-->

+++**Serviço**

O Adobe Campaign permite que você crie e administre serviços de informações, como boletins informativos ou atualizações de produto e gerencie as assinaturas a esses serviços. Vários serviços podem ser definidos em paralelo.

Saiba mais sobre [Serviços](../../delivery/using/about-services-and-subscriptions.md).
+++

+++**Gerenciamento de SFTP**

No Painel de controle, é possível interagir com todos os servidores SFTP conectados às instâncias do Campaign às quais você tem acesso. O Painel de controle permite executar ações em seus servidores SFTP, como Monitorar a capacidade de armazenamento, Gerenciar endereços IP para permitir listagens e gerenciar chaves SSH públicas.

Saiba mais sobre [Gerenciamento de SFTP](https://experienceleague.adobe.com/pt-br/docs/control-panel/using/sftp-management/about-sftp-management).
+++

+++**Atividade de subscrição no serviço**

Uma atividade de fluxo de trabalho de serviços de Subscrição permite criar ou excluir uma subscrição para um serviço de informações para população especificada na transição.

Saiba mais sobre a atividade Serviços de assinatura na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/subscription-services.html?lang=pt-BR){target="_blank"}.
+++

+++**Aprovação de público-alvo**

*Contexto: Marketing distribuído do Campaign*

Aprovação de público-alvo é o processo no qual o direcionamento final de uma entrega é aprovado por um Operador ou grupo de Operadores separado (após a fase de análise ter gerado o público-alvo) antes que a entrega possa ser enviada.

Saiba mais sobre a atividade Aprovação de público-alvo na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/approval.html?lang=pt-BR){target="_blank"}.
+++

+++**Dados do público-alvo**

Os dados do público-alvo são os dados armazenados na tabela de trabalho (transição) de um fluxo de trabalho. Esses dados estão disponíveis na entrega para personalização do conteúdo da entrega ou para definir a lógica de elementos dinâmicos da entrega.

Saiba mais sobre dados de público-alvo na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/use-workflow-data.html?lang=pt-BR#target-data){target="_blank"}.
+++

+++**Target mapping**

Target mapping é o mapeamento de canais de entrega para um tipo de dados específico. Os target mappings definem como diferentes canais de entrega se vinculam aos campos de dados de um esquema. Ele define como o Campaign envia para esse tipo de dados usando um campo ou expressão específica.

Saiba mais sobre o target mapping na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/audience/add-profiles/target-mappings.html?lang=pt-BR){target="_blank"}.
+++

+++**Atividades de direcionamento**

As atividades de direcionamento são atividades de fluxo de trabalho específicas para direcionamento, manipulação de dados de população e atividades de filtragem. Essas atividades permitem construir um ou mais públicos-alvos definindo conjuntos e dividindo ou combinando-os usando operações de intersecção, união ou exclusão.

Saiba mais sobre atividades de direcionamento na [documentação do Campaign v8]&#x200B;(https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/targeting-activities
.html?lang=pt-BR){target="_blank"}.
+++

+++**Dimensão de direcionamento**

Dimensão de direcionamento é o tipo de dados produzido (retornado) por uma consulta ou outras atividades de fluxos de trabalho. Observe que o Adobe Campaign retorna somente a chave primária das linhas de banco de dados do entrevistado, independentemente da consulta usada para obtê-las.

Saiba mais sobre a dimensão de direcionamento na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html?lang=pt-BR){target="_blank"}.
+++

+++**Atividade de tarefa**

*Contexto: Gestão dos Recursos de Marketing (MRM)*

A atividade de fluxo de trabalho Tarefa incorpora a ação humana à lógica de um fluxo de trabalho. Você pode especificar dois cenários: o primeiro se a tarefa estiver concluída e um segundo se a tarefa não estiver concluída. Casos de uso típicos são para incorporação de ações offline em uma campanha ou para ações personalizadas, como aprovações.

Saiba mais sobre a atividade perguntar na [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/automation/mrm/creating-and-managing-tasks){target="_blank"}.
+++

<!--
-----NOT USEFUL, detail-----
+++**Task**

One iteration of the defined functionality of a workflow activity. Each execution of a task has a unique task identifier.   

Learn more about [Tasks](../../workflow/using/about-workflows.md).
+++
-->

+++**Modelo**

Um modelo é um elemento de design usado para criar um objeto. Ele contém configurações do objeto e, opcionalmente, o conteúdo do objeto. O sistema de modelos é usado para criar entregas, campanhas, fluxos de trabalho e muitos outros elementos do Adobe Campaign. Os modelos de fábrica disponíveis são definidos pelos pacotes instalados. Os modelos podem ser duplicados e personalizados, conforme necessário pelos Operadores do Campaign.
+++

<!--
-----ACS -> SEEDS IN ACC-----
+++**Test profiles**

Allows targeting of additional recipients who do not match the defined targeting criteria. They are added to a message's audience to detect any fraudulent use of your recipient database or to ensure delivery. Seen as the Seed type in the Campaign interface.

Learn more about [Test profiles](../../workflow/using/about-workflows.md).
+++
-->

<!--
-----NOT FOR DOCS?-----
+++**Total database storage**

The aggregate size of the production and non-production instance(s) database storage managed by Adobe. 

Learn more about [Total database storage](../../workflow/using/about-workflows.md).
+++
-->

+++**Logs de rastreamento**

O fluxo de trabalho técnico de rastreamento recupera os dados de rastreamento depois que a entrega é enviada e o rastreamento ativado. Esses dados podem ser encontrados na guia Rastreamento da entrega. Você pode encontrar informações para aberturas e cliques em um email ou outras interações com uma mensagem recebida pelo destinatário.

Saiba mais sobre [Logs de rastreamento no Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/tracking-logs){target="_blank"}.
+++

+++**Mensagens transacionais**

As mensagens transacionais são um módulo do Campaign criado para gerenciar notificações de acionador personalizadas geradas por eventos enviados por um sistema de informações externo. Uma mensagem transacional é uma comunicação individual e única enviada em tempo real a um usuário por um provedor, como um site. É particularmente esperado, pois contém informações importantes que o destinatário deseja verificar ou confirmar.

Saiba mais sobre [Mensagens transacionais](../../message-center/using/about-transactional-messaging.md).
+++

&lt;!------- ÚTIL AQUI??----->
+++**Campanhas acionadas**

As campanhas acionadas são campanhas que são executadas quando uma solicitação de API é recebida em um fluxo de trabalho. As chamadas de API são consumidas por uma atividade de Sinal no fluxo de trabalho, cuja execução é iniciada.

Saiba mais sobre campanhas acionadas na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/external-signal.html?lang=pt-BR){target="_blank"}.
+++

<!--
-----NOT USEFUL-----
+++**Triggers**

Signals that initiate execution of a workflow, delivery or other action. Typically an API call. 

Learn more about [Triggers](../../workflow/using/about-workflows.md).
+++
-->

+++**Tipologia**

*Contexto: Otimização de campanha*

Uma tipologia é um agrupamento de regras de tipologia aplicadas à fase de análise de uma entrega. Uma tipologia de campanha pode conter várias regras de tipologia, mas uma entrega só pode fazer referência a uma tipologia.

Saiba mais sobre tipologias na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=pt-BR){target="_blank"}.
+++

+++**Regra de tipologia**

*Contexto: Otimização de campanha*

As regras de tipologia são regras de negócios que são implementadas como parte da fase de análise da entrega. As regras de tipologia são verificações sobre o conteúdo da entrega (regras de controle) ou do público-alvo da entrega (regras de filtragem) ou de outra lógica (regras de pressão) que impõem requisitos comerciais. As regras são elementos granulares que podem ser incluídos em uma ou mais tipologias.

Saiba mais sobre regras de tipologia na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=pt-BR){target="_blank"}.
+++

## U - Z {#sec-6}

+++**Modo Unitário**

*Contexto: Interação de campanha, mensagens transacionais*

No modo unitário, um único contato é processado pelo mecanismo de oferta no tempo de execução. Esse modo geralmente é usado para interações de entrada e mensagens transacionais.

Saiba mais sobre [Modo unitário](../../interaction/using/about-inbound-channels.md).
+++

+++**Aplicativos web**

Os aplicativos da Web são páginas de aplicativos dinâmicos e interativos hospedadas pela instância do Campaign. Eles contêm dados do banco de dados e conteúdo adaptado aos direitos do usuário conectado. Por exemplo, você pode criar um formulário de edição em uma extranet ou formulários de notificação, incluindo dados do banco de dados com tabelas, gráficos, formulários de entrada etc. Essa funcionalidade permite criar e publicar páginas da Web em que os usuários podem pesquisar ou inserir informações.

Saiba mais sobre [Aplicativos da Web](../../web/using/about-web-applications.md).
+++

+++**Fluxo de trabalho**

Um fluxo de trabalho é uma representação visual do fluxo de execução da campanha. Permite que você organize a gama completa de processos e tarefas em diferentes módulos do servidor de aplicativos. Esse ambiente gráfico abrangente permite criar processos, inclusive segmentação, execução de campanha, processamento de arquivos, participação humana etc. O mecanismo de fluxo de trabalho executa e rastreia esses processos.

Saiba mais sobre [Fluxos de trabalho](../../workflow/using/about-workflows.md)
+++

+++**Diário de fluxo de trabalho**

O diário de fluxo de trabalho é o log de execução passo a passo de um fluxo de trabalho. Ele contém o histórico ou a trilha de auditoria do fluxo de trabalho. Ele é usado para fins de desenvolvimento, solução de problemas ou depuração.

Saiba mais sobre o diário de fluxo de trabalho na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=pt-BR){target="_blank"}.
+++

+++**Tabela de trabalho**

A tabela de trabalho contém todas as informações transportadas pelas transições de fluxo de trabalho. Cada fluxo de trabalho usa várias tabelas de trabalho. A tabela de trabalho contém os resultados de sua atividade de origem e seu conteúdo é usado como entrada para a próxima atividade (conectada) no fluxo de trabalho.  A manipulação (extensão, personalização) da tabela de trabalho é uma das principais habilidades de um operador do Adobe Campaign.

Saiba mais sobre [Tabelas de trabalho](../../workflow/using/about-workflows.md).
+++
