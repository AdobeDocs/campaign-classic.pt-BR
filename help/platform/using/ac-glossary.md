---
product: campaign
title: Glossário do Adobe Campaign
description: Glossário do Adobe Campaign
role: User, Data Architect
level: Beginner
hide: true
hidefromtoc: true
source-git-commit: 891418c4120793cf296a65f7aed86e71925a0d66
workflow-type: tm+mt
source-wordcount: '6454'
ht-degree: 12%

---

# Glossário do Adobe Campaign{#ac-glossary}

Abaixo está a definição dos termos e conceitos principais no Adobe Campaign, com links para a documentação relacionada. Clique em um termo para exibir sua definição.

## A - D{#sec-1}

+++**Teste A/B**

O teste A/B é um recurso que permite ao usuário definir duas a três variantes de email: cada variante é enviada para amostras de população para determinar qual tem o melhor resultado. Uma vez determinada, a variante vencedora é então enviada para a população restante.

Saiba mais sobre [Teste A/B](../../delivery/using/get-started-a-b-testing.md).
+++

+++**Gerenciamento de acesso**

O gerenciamento de acesso permite que administradores atribuam acesso e permissões a usuários do Adobe Campaign. As permissões incluem a capacidade de exibir e/ou usar recursos do Adobe Campaign, como executar fluxos de trabalho, definir esquemas e gerenciar públicos-alvo.

Saiba mais sobre [Gerenciamento de acesso](access-management.md).
+++

+++**Conector ACS**

O ACS Connector (Prime Offering) faz a ponte entre o Adobe Campaign v7 e o Adobe Campaign Standard. É um recurso integrado no Campaign v7 que replica automaticamente os dados no Campaign Standard, unindo o melhor das duas aplicações. O Campaign v7 tem ferramentas avançadas para gerenciar o banco de dados de marketing principal. A replicação de dados do Campaign v7 permite que o Campaign Standard potencialize os dados avançados em um ambiente simples.

Saiba mais sobre [ACS Connector](../../integrations/using/acs-connector-principles-and-data-cycle.md).
+++

+++**Atividade**

Uma atividade é um item da paleta adicionado a um fluxo de trabalho para definir uma funcionalidade de execução. A atividade é um container que executa uma tarefa. Em um workflow, uma determinada atividade pode produzir várias tarefas, principalmente quando há ações de loop ou recorrentes (periódicas).

Saiba mais sobre [Atividades de workflow](../../workflow/using/about-activities.md).
+++

+++**Perfil ativo**

Os perfis são considerados ativos se tiverem sido direcionados ou comunicados nos últimos 12 meses por meio de qualquer canal. De acordo com seu contrato, cada uma das instâncias do Campaign é provisionada com um número específico de perfis ativos que são contados para fins de faturamento.

Saiba mais sobre [Perfis ativos](../../platform/using/about-profiles.md#active-profiles).
+++

+++**Atividade de workflow de aprovação**

*Contexto: Marketing distribuído da campanha*

A atividade Local Approval é uma atividade de workflow usada para configurar um processo de aprovação de delivery antes que as mensagens sejam enviadas.

Saiba mais sobre o [Atividade de aprovação local](../../workflow/using/local-approval.md).
+++

+++**Audience**

Um público-alvo é o conjunto resultante de perfis que atendem aos critérios de uma definição de filtro, com base em regras e atributos.

Saiba mais sobre [Públicos-alvo](../../campaign/using/marketing-campaign-target.md).
+++

+++**Trilha de auditoria**

A trilha de auditoria captura, em tempo real, uma lista abrangente de ações e eventos que ocorrem em sua instância do Adobe Campaign. Ele inclui uma maneira de autoatendimento para acessar um histórico de dados que ajudam a responder perguntas como: o que aconteceu com seus fluxos de trabalho e quem os atualizou pela última vez ou o que seus usuários fizeram na instância .

Saiba mais sobre [Trilha de auditoria](../../production/using/audit-trail.md).
+++

+++**Campanhas automatizadas**

Campanhas executadas de acordo com uma programação, como para direcionar recipients que fazem aniversário ou aniversário. Também pode ser usado para executar a lógica de olhar para frente e de olhar para trás, como quem comprou ontem ou quem tem um pagamento devido amanhã.

Saiba mais sobre [Campanhas](../../campaign/using/designing-marketing-campaigns.md).
+++

+++**Modo de lote**

*Contexto: Interação de campanha*

No contexto de Interação de campanha, o modo de lote permite que o Mecanismo de oferta selecione a melhor oferta (ou ofertas) para um conjunto de contatos. As regras de elegibilidade/priorização são aplicadas a todos os contatos do conjunto.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Campanha**

O Campaign é uma interface para coordenar, definir e executar campanhas de marketing. As campanhas podem conter um ou mais workflows, deliveries, documentos e outros pontos de dados relacionados em uma única interface fácil de usar.

Saiba mais sobre [Campanhas](../../campaign/using/designing-marketing-campaigns.md).
+++

+++**Processo de transição**

*Contexto: Interação de campanha*

No contexto da interação do Campaign, o processo de transição é um processo ativado em um ambiente identificado, responsável por direcionar a chamada a um ambiente anônimo se o contato não tiver sido identificado explicitamente e/ou implicitamente.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Canal**

Um canal é um meio pelo qual uma comunicação é enviada. Os canais incorporados no Adobe Campaign são email, SMS, correspondência direta, notificações por push, LINE e Twitter. Os canais personalizados podem ser implementados para requisitos de canal não padrão.

Saiba mais sobre [Canais](../../delivery/using/communication-channels.md).
+++

+++**Console do cliente**

O console do cliente do Campaign é um cliente avançado que permite a conexão com o(s) servidor(es) de aplicativos do Campaign. O aplicativo executável (.exe) do console do cliente é instalado em um computador com um sistema operacional Microsoft Windows. O console do Campaign Client centraliza todos os recursos e configurações.

Saiba mais sobre [Console do cliente](../../platform/using/adobe-campaign-workspace.md).
+++

+++**Aprovação de conteúdo**

A aprovação de conteúdo é o processo de ter um Operador ou grupo de Operadores separado aprovar o conteúdo de um delivery antes que ele possa ser enviado.

Saiba mais sobre [Aprovação de conteúdo](../../campaign/using/marketing-campaign-approval.md).
+++

+++**Grupos de controle**

Use grupos de controle para medir o impacto de suas campanhas excluindo parte de seus públicos. Os operadores podem comparar o comportamento da população do target que recebeu a mensagem com o comportamento dos contatos que não foram direcionados. Com base nos logs de envio, os Operadores também podem direcionar um grupo de controle em campanhas futuras.

Saiba mais sobre [Aprovação de conteúdo](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).
+++

+++**Painel de controle do Campaign**

O Painel de controle do Campaign ajuda a aumentar a eficiência do seu trabalho como administrador de produtos do Adobe Campaign, permitindo gerenciar configurações e rastrear o uso de cada uma de suas instâncias. Sua interface intuitiva permite monitorar facilmente o uso dos principais ativos, além de realizar tarefas administrativas, como adicionar lista de permissão de endereços IP, monitoramento de armazenamentos SFTP, gerenciamento de chaves e muito mais.

Saiba mais sobre [Aprovação de conteúdo](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=pt-BR).
+++

+++**Cubos**

*Contexto: Análise de marketing*

Cubo é uma ferramenta de exploração de dados intuitiva da Adobe Campaign que ajuda os usuários a criar e compartilhar relatórios dinâmicos.

Saiba mais sobre [Cubos](../../reporting/using/about-cubes.md).
+++

+++**Recursos personalizados**

O Adobe Campaign vem com um modelo de dados predefinido, onde os tipos de dados são definidos por meio da instalação de vários pacotes. Os operadores podem enriquecer o modelo de dados fornecido ao estender os recursos para adicionar campos personalizados ou tabelas personalizadas, como tabelas de transações ou de produtos.

Saiba mais sobre [Recursos personalizados](../../configuration/using/about-schema-edition.md).
+++

+++**Modelo de dados**

O modelo de dados da campanha é um conjunto de schemas que definem os tipos de dados e seus relacionamentos (links). O modelo de dados é uma definição abstrata que é implementada fisicamente com um banco de dados que contém os dados reais.

Saiba mais sobre [Recursos personalizados](../../configuration/using/about-data-model.md).
+++

+++**Workflow de limpeza do banco de dados**

O fluxo de trabalho de limpeza do banco de dados exclui dados obsoletos para evitar o crescimento exponencial do banco de dados. O workflow é acionado automaticamente sem a intervenção do usuário.

Saiba mais sobre [Workflow de limpeza do banco de dados](../../production/using/database-cleanup-workflow.md).
+++

+++**Servidor dedicado**

*Contexto: Mensagens transacionais*

Servidores de execução dedicados para aproveitar as Mensagens transacionais. Um servidor geralmente pode processar até 50.000 chamadas de mecanismo por hora. A designação &quot;Servidor por dedicado&quot; não tem necessariamente uma correlação 1:1 com um servidor físico, pois o Adobe pode utilizar tecnologias de virtualização para alcançar o efeito equivalente.

Saiba mais sobre [Mensagens transacionais](../../message-center/using/about-transactional-messaging.md).
+++

+++**Avaliação do delivery**

*Contexto: Entregabilidade por email*

Uma métrica que permite que os Operadores meçam o sucesso de uma campanha ao alcançar a caixa de entrada dos recipients sem rejeição ou serem marcados como spam.

Saiba mais sobre [Capacidade de entrega](../../delivery/using/about-deliverability.md).
+++

+++**Delivery**

Um delivery é um item específico de comunicação de marketing que é enviado para um público em um canal específico (email, SMS, notificação por push etc.). Também conhecido como &quot;toque&quot; na terminologia de marketing.

Saiba mais sobre [Deliveries](../../delivery/using/communication-channels.md).
+++

+++**Análise de delivery**

A análise de delivery é a preparação do delivery. Esse processo combina o conteúdo com os dados de perfil do recipient para produzir o email personalizado que o recipient recebe. A lógica de análise de delivery pode excluir recipients do target ou interromper o delivery completamente, com base na lógica definida. Esse processo também inclui a avaliação da lógica do conteúdo dinâmico e a inserção de ofertas específicas ao perfil de recipient individual.

Saiba mais sobre [Análise de delivery](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).
+++

+++**Logs do delivery**

Os logs do delivery contêm informações geradas ao enviar uma mensagem. Esses logs mostram os detalhes do envio, que mensagem foi preparada, ignorada, enviada ou com falha. Elas podem ser acessadas diretamente do painel de delivery.

Saiba mais sobre [Logs do delivery](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).
+++

+++**Fundamentos da entrega**

*Contexto: Entregabilidade por email*

O Serviço de consultoria de princípios básicos de capacidade de entrega de e-mails da Adobe Campaign fornece consultoria de capacidade de fornecimento de e-mails e gerenciamento de reputação para oferecer suporte aos clientes que usam os deliveries do Adobe Campaign.

Saiba mais sobre [Capacidade de entrega](../../delivery/using/about-deliverability.md).
+++

+++**Delivery outline**

*Contexto: Correspondência direta*

Um delivery outline é um conjunto estruturado de elementos (documentos, lojas, cupons promocionais etc.) criado pela empresa e para uma campanha específica. Ele é usado no contexto de deliveries de correspondência direta.

Saiba mais sobre [Correspondência direta](../../delivery/using/about-direct-mail-channel.md).
+++

+++**Assistente de implantação**

O assistente de implantação define os parâmetros da instância do Campaign, como o namespace padrão, o agendamento de limpeza do banco de dados, os períodos de retenção de dados e outras configurações técnicas.

Saiba mais sobre [Assistente de implantação](../../installation/using/deploying-an-instance.md#deployment-wizard).
+++

+++**Análise descritiva**

A Análise Descritiva é uma ferramenta de relatório sensível ao contexto que pode ser usada para examinar os dados na tabela de trabalho de um workflow, os dados selecionados em uma pasta ou para aprofundar os destinos e exclusões de deliveries selecionados.

Saiba mais sobre [Análise descritiva](../../reporting/using/about-descriptive-analysis.md)
+++

+++**Marketing distribuído**

*Contexto: Marketing distribuído*

O complemento Marketing distribuído oferece aos operadores do Campaign um espaço de trabalho colaborativo para implementar campanhas entre entidades centrais (sede, departamentos de marketing etc.) e entidades locais (pontos de vendas, agências regionais etc.). Essa cooperação é baseada em um espaço de trabalho compartilhado conhecido como **lista de pacotes do Campaign**, em que templates de campanha e instâncias criadas centralmente são oferecidos a entidades locais.

Saiba mais sobre [Marketing distribuído](../../distributed/using/about-distributed-marketing.md)
+++

+++**Distribuição de valores**

A Distribution of values é uma ferramenta que mostra a distribuição dos valores de um atributo de schema que existe atualmente no banco de dados. Isso ajuda a determinar quais valores estão disponíveis, suas contagens e porcentagens e evitar problemas com capitalização e ortografia de valores ao criar uma consulta ou expressão.

Saiba mais sobre [Marketing distribuído](../../platform/using/defining-filter-conditions.md#selecting-data-to-extract)
+++

+++**Delegação de domínio**

A configuração de subdomínio permite configurar uma subseção do seu domínio (tecnicamente uma &quot;zona DNS&quot;) para usar com o Adobe Campaign.
A delegação de domínio permite que o Adobe controle e mantenha todos os aspectos do DNS necessários para fornecer, renderizar e rastrear campanhas de email.

Saiba mais sobre [Delegação de domínio](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=pt-BR)
+++

## E - H {#sec-2}

<!--
+++**E4X**

The version of Javascript that is used in Adobe Campaign Classic. Sometimes called ECMAScript, it is an extension of Javascript that allows the mixing of Javascript and XML primitives in the same code. Note that E4X is classified as a deprecated language. 
+++
-->

+++**Regras de elegibilidade**

*Contexto: Interação de campanha*

As regras de elegibilidade são restrições aplicadas a um ambiente, categoria ou oferta sobre o período de validade, target e peso. Eles permitem que os Operadores garantam que uma oferta esteja alinhada com o contato direcionado. No ambiente de oferta, as regras de qualificação incluem regras de apresentação aplicadas às ofertas e aos recipients a serem alvos. Na categoria , as regras de elegibilidade permitem que os Operadores limitem a validade da categoria no tempo, definam temas de aplicação e determinem os recipients a serem alvos. Eles também podem definir um peso multiplicador para um determinado período. Isso permite que os Operadores compartilhem as regras para ofertas em outras categorias e simplifica seu gerenciamento. Em uma oferta, as regras de elegibilidade permitem que os Operadores limitem a validade de ofertas no tempo e determinem os recipients a serem alvos.

Saiba mais sobre [Regras de elegibilidade](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Oferta elegível**

*Contexto: Interação de campanha*

Uma oferta elegível é uma oferta que se encontra com as restrições definidas upstream que podem ser oferecidas de forma consistente a um target.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**CCO de email**

O recurso Cco de email envia uma cópia exata no formato EML de um email entregue correspondente, que é salvo em um endereço de email CCO dedicado, onde os emails podem ser processados e arquivados pelo remetente em um sistema externo.

Saiba mais sobre [Email Cco](../../delivery/using/email-parameters.md#email-bcc).
+++

+++**Compromisso de volume de email**

Os emails antecipados enviados por ano conforme estabelecido na Ordem de Venda. Esse é o compromisso total anual de volume de email, incluindo emails enviados, mas não entregues, devido a erros de delivery, como: não entrega de uma mensagem incluindo, mas não limitado a, erros de endereço de email, devoluções permanentes, devoluções temporárias, filtros de email de clientes de email e listas negras de email.
+++

+++**Chamada do mecanismo**

Uma chamada de mecanismo é uma chamada de servidor que inicia o processamento em tempo real no lado do servidor para a extração de dados, como dados relacionados a pesquisas, WebApps, JSSP, APIs, registros de aplicativos móveis etc. As chamadas do mecanismo devem ser licenciadas em pacotes de 5.000 chamadas do mecanismo por dia.
+++

+++**Atividade de enriquecimento**

A atividade Enrichment é uma atividade avançada de workflow que permite aos Operadores enriquecer os dados gerados da tabela de trabalho que serão processados no workflow. Essa atividade geralmente é usada após atividades de direcionamento ou após a importação de um arquivo e antes de atividades que usam dados direcionados. Os enriquecimentos podem transformar os dados de transição de entrada e configurar a atividade para concluir a transição de saída com dados aprimorados. Ela permite que o Operador combine dados de vários conjuntos de dados ou crie links para um recurso temporário.

Saiba mais sobre [Atividade de enriquecimento](../../workflow/using/enrichment.md).
+++

+++**Enumerações**

Uma enumeração é um tipo de dados definido em schemas ou no nível da plataforma que define os valores de entrada válidos para um campo. Enumerações aparecem na interface do usuário e nos construtores de consultas como uma lista de opções.

Saiba mais sobre [Enumerações](../../platform/using/managing-enumerations.md).
+++

+++**Visualização do Explorer**

A visualização do Explorer é uma exibição hierárquica das pastas que contêm artefatos e dados do Adobe Campaign. Observe que o sistema de pastas no Adobe Campaign não funciona como uma visualização de árvore típica, na medida em que cada pasta retém dados de um tipo específico, como Deliveries, Workflows ou Offers.

Saiba mais sobre [Visualização do Explorer](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Contas externas**

Contas externas são pontos de entrada e saída para que o produto se conecte a outros ambientes e tecnologias. As contas externas definem os parâmetros de conexão que o produto usa para enviar dados para ou receber dados de outras fontes. Tipos típicos de conta externa são conexões para sites SFTP, telecoms para suportar o envio de SMS, caixas de correio para as rejeições de processamento ou conexões com bancos de dados externos.

Saiba mais sobre [Contas externas](../../installation/using/external-accounts.md).
+++

+++**Gerenciamento de fadiga**

*Contexto: Otimização de campanha*

O gerenciamento de fadiga ajuda a controlar a frequência e a quantidade de mensagens para evitar a solicitação excessiva de recipients e é aplicado com frequência usando uma regra de tipologia.

Saiba mais sobre [Gerenciamento de fadiga](../../campaign-opt/using/pressure-rules.md).
+++

+++**Federated Data Access (FDA)**

O Federated Data Access oferece suporte à extensão do modelo de dados do cliente para incluir um banco de dados de terceiros. Ele detectará automaticamente a estrutura das tabelas direcionadas e usará os dados das fontes SQL. Você pode acessar dados externos sem alterar a estrutura dos dados do Adobe Campaign.

Saiba mais sobre [Federated Data Access](../../installation/using/about-fda.md).
+++

+++**Aprovação de extração de arquivo**

*Contexto: Correspondência direta*

A aprovação de extração de arquivo é o processo de ter um Operador ou grupo de Operadores separado aprovando o conteúdo e a configuração de um arquivo extraído antes de ele ser enviado a um fornecedor externo, como para um delivery de mala direta.

Saiba mais sobre [Aprovação de extração de arquivo](../../delivery/using/validating.md).
+++

+++**Dimensão do filtro**

A dimensão do filtro é o schema que contém os dados ou atributos usados por uma query para filtrar as linhas desejadas. O schema de dimensão Filtering deve ser vinculado diretamente à dimensão Targeting definida para permitir que o Adobe Campaign cruze a associação do banco de dados e retorne as linhas do entrevistado.

Saiba mais sobre [Dimensão de filtro](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).
+++

+++**Pasta**

Uma pasta é um item de visualização do Explorer que mantém registros de banco de dados de um tipo de dados específico. A exceção é o tipo Generic folder usado como um elemento organizador e não contém dados propriamente dito, apenas outras pastas.

Saiba mais sobre [Pastas](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Exibição de pasta**

A Exibição de pasta é um tipo de pasta especial do Explorer usada para exibir todos os registros de um tipo de dados selecionado, independentemente da pasta à qual pertence. As exibições de pastas são usadas como uma ferramenta administrativa para gerenciar dados particionados ou que são distribuídos entre muitas pastas.

Saiba mais sobre [Exibição de pasta](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Forms**

A Forms define a representação da interface para um tipo de schema específico. Forms são o meio usado para criar e editar facilmente elementos de dados no produto, como Recipients, Deliveries e Campanhas. Todos os elementos de interface no Adobe Campaign são criados no próprio produto usando o Forms. Observe que os formulários são opcionais e nem todos os esquemas têm formulários.

Saiba mais sobre [Forms](../../configuration/using/identifying-a-form.md).
+++

+++**Consulta SQL gerada**

O código SQL gerado para o banco de dados subjacente quando um operador manipula um esquema. Os esquemas definem os tipos de dados que são implementados usando tabelas e colunas do banco de dados. O SQL gerado para manipulação de esquema (como em uma query) é baseado no tipo de banco de dados instalado. Assim, o banco de dados pode ser trocado para um tipo diferente e as consultas no Campaign permanecem inalteradas. O Adobe refere-se a essa funcionalidade como sendo independente de banco de dados.

Saiba mais sobre [Consultas SQL geradas](../../platform/using/steps-to-create-a-query.md#step-6---preview-data).
+++

+++**Heatmap**

Campaign Heatmap é uma tabela que mostra informações de execução do workflow para um período de 24 horas. Ele exibe a distribuição de workflows entre o período por hora e intervalos de 5 minutos. O Heatmap é usado para avaliar a carga do servidor e determinar as atividades do workflow que estão consumindo mais recursos.

Saiba mais sobre [HeatMap](../../workflow/using/heatmap.md).
+++

+++**Implantação híbrida**

A implantação híbrida é uma combinação de serviços sob demanda e software local implantado para funcionar em conjunto.

Saiba mais sobre [Implantação híbrida](../../installation/using/hosting-models.md#hybrid).

+++

## I - L {#sec-3}

+++**Modo de identificação**

*Contexto: Interação de campanha*

Refere-se ao status de um Contato. Pode ser explícito, implícito ou anônimo.

* **explicit**: o contato é identificado após entrar na interface do canal.
* **implicit**: o contato foi identificado por um cookie (permanente ou de sessão). Ele pode ser processado como um contato anônimo ou identificado.
* **anonymous**: o contato não pode ser identificado.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Serviço de imagem**

A funcionalidade que fornece as imagens incorporadas em emails para os recipients do delivery. A inserção das imagens com base na funcionalidade &quot;baixar imagens&quot; de um sistema de emails é o que gera uma entrada &quot;aberta&quot; nos logs de rastreamento do Campaign.

Saiba mais sobre [Serviço de imagem](../../delivery/using/defining-the-email-content.md#adding-images).
+++

+++**Interação de entrada**

*Contexto: Interação de campanha*

Uma interação de entrada é uma interação que segue uma chamada recebida gerada pela ação de um contato em um canal, como Web, call center ou dispositivo móvel. Esse tipo de interação geralmente é processado no modo unitário (ou seja, por recipient).

Saiba mais sobre [Interação de entrada](../../interaction/using/about-inbound-channels.md).
+++

+++**Renderização da caixa de entrada**

A renderização da caixa de entrada é a geração de visualizações de email, o que garante que a mensagem será exibida aos recipients de forma ideal em uma variedade de clientes Web, Webmails e dispositivos. O Adobe Campaign aproveita o Litmus, que permite que criadores de conteúdo de email visualizem o conteúdo de sua mensagem em mais de 70 renderizadores de email, como a caixa de entrada do Gmail ou o cliente Apple Mail.

Saiba mais sobre [Renderização da caixa de entrada](../../delivery/using/delivery-dashboard.md#delivery-rendering).
+++

+++**Configurações de instância**

As configurações de instância são detalhes de configuração de uma instância do Adobe Campaign. Essas configurações são definidas no Assistente de implantação (Ferramentas>Avançado>Assistente de implantação) ou nos arquivos de configuração do servidor e/ou da instância.

Saiba mais sobre [Configurações de instância](../../installation/using/about-initial-configuration.md).

+++

+++**Trabalhos (importar e exportar)**

Os trabalhos são gerenciados por um sistema de assistente que simplifica a importação e exportação de dados para dentro e para fora do produto. As tarefas usam o sistema de modelos para simplicidade e consistência e podem ser definidas para execução de acordo com uma programação.

Saiba mais sobre [Importar e exportar trabalhos](../../platform/using/get-started-data-import-export.md).
+++

+++**Listas**

Uma lista é um conjunto de dados estático. Listas são públicos ou segmentos importados para o Campaign de outras fontes (Audience Manager, Experience Platform, banco de dados etc.) e são vistos na interface como Listas importadas.

Saiba mais sobre [Listas](../../platform/using/creating-and-managing-lists.md).
+++

+++**Cache local**

Informações armazenadas localmente no computador do operador. As informações em cache são usadas pelo console para reduzir o tráfego necessário para o servidor e melhorar o desempenho. A limpeza periódica do cache local (no menu Arquivo ) atualiza as informações armazenadas e melhora o desempenho e a estabilidade.

Saiba mais sobre [Cache local](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).
+++

## M - P {#sec-4}

+++**Gestão dos Recursos de Marketing (MRM)**

*Contexto: Gestão dos Recursos de Marketing (MRM)*

O **Gestão dos Recursos de Marketing (MRM)** no Adobe Campaign permite controlar ações de marketing em um modo colaborativo fornecendo gerenciamento completo e rastreamento em tempo real das tarefas, orçamentos e recursos de marketing envolvidos. Os operadores do Adobe Campaign podem coordenar suas ações e aprovar seu progresso em todos os estágios por meio de processos de validação completos e ferramentas de rastreamento apropriadas: relatórios, rastreamento de aprovações, notificações, fóruns de discussão etc.

Saiba mais sobre [MRM](../../mrm/using/about-marketing-resource-management.md).
+++

<!--
+++**Localization**

This template type is used to manage multilingual messages.  It is available for Email and SMS messages and useable in standalone mode, within a workflow or in a recurring delivery. In the multilingual feature templates, the language management is based on variants. Each variant represents one language.  This functionality is available only in Adobe Campaign Standard.  
+++
-->

+++**Direitos nomeados**

Os direitos granulares de acesso ao banco de dados usados para definir o acesso e os privilégios do Grupo de Operadores (funções). Direitos nomeados são preenchidos durante a instalação do produto e importando vários pacotes que definem a funcionalidade específica da ferramenta. É possível criar direitos nomeados personalizados para dar suporte aos requisitos de negócios do cliente.

Saiba mais sobre [Direitos nomeados](../../platform/using/access-management-named-rights.md).
+++

+++**Namespace**

Uma partição que separa os tipos de dados do cliente dos tipos de dados nativos da Adobe Campaign no modelo de dados. Também é usado para facilitar a migração das definições de uma instância para outra, como mover um schema ou template da instância de desenvolvimento para a instância de produção.

Saiba mais sobre [Namespace](../../configuration/using/about-schema-reference.md#identification-of-a-schema).
+++

+++**Barra de navegação**

O elemento de navegação que está sendo executado na parte superior da interface. A barra de navegação reagrupa os vários recursos principais da plataforma. Clique em um link da barra de navegação para exibir o conjunto de funcionalidades relacionadas a esse recurso. A lista de recursos principais que você pode acessar depende dos pacotes e dos complementos instalados e dos seus direitos de acesso. O objetivo da barra de navegação é simplificar o gerenciamento de tela e aumentar a produtividade.

Saiba mais sobre [Barra de navegação](../../platform/using/adobe-campaign-workspace.md#browsing-pages).
+++

+++**Árvore de navegação**

A navegação principal na visualização do Explorer do Adobe Campaign. A árvore de navegação funciona como um navegador de arquivos (por exemplo, Windows Explorer). As pastas podem conter subpastas. Selecionar um nó exibe a visualização correspondente ao nó. A visualização exibida é uma lista associada a um esquema e um formulário de entrada para editar a linha selecionada. Você pode personalizar a árvore de navegação e definir permissões em pastas.

Saiba mais sobre [Árvore de navegação](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarch).
+++

+++**Objetivos**

*Contexto: Gestão dos Recursos de Marketing (MRM)*

Na campanha, programa ou plano, os Operadores podem declarar uma lista de objetivos. Esses valores são quantificados para serem alcançados. No final da campanha, do programa ou do plano, o módulo MRM permite que os Operadores comparem os objetivos e os resultados em relatórios dedicados.

Saiba mais sobre [Objetivos](../../mrm/using/creating-and-managing-tasks.md#expenses-and-revenues).
+++

+++**Catálogo de ofertas**

*Contexto: Interação de campanha*

Conjunto de ofertas definido no Adobe Campaign que pode ser selecionado durante uma interação. O catálogo é organizado hierarquicamente com cada nó correspondente a uma categoria.

Saiba mais sobre [Catálogo de ofertas](../../interaction/using/offer-catalog-overview.md).
+++

+++**Contato da oferta**

*Contexto: Interação de campanha*

Um contato de uma interação de entrada. Durante o processamento de chamadas do mecanismo, o contato é associado a um targeting dimension. Contatos anônimos e não identificados são atribuídos ao targeting dimension do visitante. Há dois tipos de contatos, identificados e anônimos:

* **Identified contact**: um contato que foi identificado voluntariamente no canal. Em interações de saída, o contato é identificado automaticamente.
* **Anonymous contact**: um contato que não tenha assinado voluntariamente por meio do canal, mas pode ser identificado implicitamente por meio de um cookie. Essa terminologia é usada apenas para interações de entrada.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Ambiente de design de oferta**

*Contexto: Interação de campanha*

A oferta **Ambiente de design** é o ambiente no qual os operadores criam ofertas, definem regras de tipologia e selecionam o schema que será direcionado pelas ofertas. A tabela para armazenar apresentações de oferta geradas também é definida pelo ambiente . Por padrão, o complemento Interaction vem com uma **Design** ambiente e **Ao vivo** ambiente vinculado a ele. Ambos os ambientes são pré-configurados para ter como alvo a tabela de recipients integrada.

Saiba mais sobre [Ambientes de design](../../interaction/using/fundamental-principles.md).
+++

+++**Arbitragem do mecanismo de oferta**

*Contexto: Interação de campanha*

Selecionar ofertas que serão exibidas em um ambiente (ofertas elegíveis). O princípio de arbitragem classifica as ofertas por prioridade de acordo com os critérios definidos nas categorias e ofertas.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Depuração do mecanismo de oferta**

*Contexto: Interação de campanha*

O processo de exclusão de ofertas que não estão qualificadas para seleção. Executado antes da etapa de arbitragem do mecanismo de oferta.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Ambiente de oferta**

*Contexto: Interação de campanha*

A pasta raiz que define um catálogo de ofertas, seus espaços disponíveis e os filtros predefinidos do ambiente. Os operadores precisam criar um ambiente para cada targeting dimension. Há dois tipos de ambientes Offer : Design e Live.

Saiba mais sobre [Ambientes](../../interaction/using/fundamental-principles.md).
+++

+++**Ambiente Offer Live**

*Contexto: Interação de campanha*

Ambiente vinculado a uma campanha **Ambiente de design**. Ele contém ofertas de somente leitura cujo conteúdo e elegibilidade foram aprovados por meio do **Design environment**. Eles podem ser selecionados para apresentação em um site ou para serem inseridos em uma mensagem de saída.

Saiba mais sobre [Ambientes Live](../../interaction/using/fundamental-principles.md).
+++

+++**Visualização da oferta**

*Contexto: Interação de campanha*

Pré-visualização da oferta como ela é exibida em sua pasta. Também é acessível a partir da guia de pré-visualização da oferta ou do perfil de contato.

Saiba mais sobre [Visualização da oferta](../../interaction/using/creating-an-offer.md#previewing-the-offer).
+++

+++**Regras de apresentação da oferta**

*Contexto: Interação de campanha*

Regras de tipologia mencionadas no ambiente de oferta, que permitem aos Operadores excluir ofertas específicas levando em conta o histórico de apresentações do recipient.

Saiba mais sobre [Regras de apresentação da oferta](../../interaction/using/managing-offer-presentation.md#presentation-rules-overview).
+++

+++**Apresentação da oferta**

*Contexto: Interação de campanha*

Uma apresentação de oferta é o resultado da ação que consiste em apresentar uma oferta a um contato em um determinado espaço de oferta, por exemplo, o banner em um site, um conteúdo de email ou SMS. Esse resultado é armazenado na tabela de propostas de oferta que define a oferta, o recipient e o carimbo de data e hora, fornecendo um registro de todas as ofertas que um recipient recebeu.

Saiba mais sobre [Apresentações da oferta](../../interaction/using/creating-offer-spaces.md#offer-proposition-statuses).
+++

+++**Representação da oferta**

*Contexto: Interação de campanha*

Uma apresentação de oferta é o resultado da ação que consiste em apresentar uma oferta a um contato em um determinado espaço de oferta, por exemplo, o banner em um site, um conteúdo de email ou SMS. Esse resultado é armazenado na tabela de propostas de oferta que define a oferta, o recipient e o carimbo de data e hora, fornecendo um registro de todas as ofertas que um recipient recebeu.

Saiba mais sobre [Interação](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Simulação de oferta**

*Contexto: Interação de campanha*

Uma simulação de oferta permite que os Operadores testem a distribuição de ofertas em um escopo definido (data de delivery, segmento de target, número de ofertas, tema etc.) antes de realmente enviar as ofertas. Ele pode ser usado para ajustar as prioridades da oferta e as regras de qualificação para maximizar a eficácia da oferta.

Saiba mais sobre [Simulações de oferta](../../interaction/using/about-offers-simulation.md).
+++

+++**Espaço de oferta**

*Contexto: Interação de campanha*

Um espaço de oferta é uma pasta que define o local onde a oferta é exposta. A definição de um espaço permite especificar o canal usado, criar o conteúdo da oferta e especificar as ofertas apresentadas. O espaço de oferta é a interface entre o canal e o mecanismo de oferta.

Saiba mais sobre [Simulações de oferta](../../interaction/using/creating-offer-spaces.md).
+++

+++**Temas da oferta**

*Contexto: Interação de campanha*

Os temas de oferta são palavras-chave definidas em uma categoria, que permite que os Operadores filtrem ofertas quando são apresentadas. Os temas permitem a seleção não hierárquica de ofertas da estrutura do catálogo.

Saiba mais sobre [Temas da oferta](../../interaction/using/integrating-an-offer-via-the-wizard.md).
+++

+++**Peso da oferta**

*Contexto: Interação de campanha*

O peso da oferta é baseado em fórmulas que definem precisamente a relevância de uma oferta para permitir que o mecanismo selecione a oferta mais relevante. Os pesos são definidos nas ofertas e os multiplicadores são definidos nas categorias. Ofertas elegíveis são consideradas em ordem decrescente de peso.

Saiba mais sobre [Peso da oferta](../../interaction/using/creating-an-offer.md#offer-weight).
+++

+++**Grupos de operadores**

Os grupos de operadores permitem gerenciar funções para operadores do Campaign. Você define grupos de operadores aos quais atribui direitos e associa os operadores a um ou mais grupos. Isso permite que você reutilize os direitos e torne os perfis de operadores mais consistentes. Também facilita o gerenciamento e a manutenção de perfis.

Saiba mais sobre [Grupos de operadores](../../platform/using/access-management-groups.md).
+++

+++**Operador**

Um operador é um usuário do Adobe Campaign que tem permissões para fazer o login e executar ações. Os operadores são associados a grupos de operadores e herdam os direitos e privilégios desses grupos. Também é possível atribuir direitos nomeados diretamente aos operadores.

Saiba mais sobre [Operadores](../../platform/using/access-management-operators.md).
+++

+++**Options**

As opções são variáveis de nível de plataforma usadas para definir configurações da instância do Campaign. As opções podem definir cronogramas (como para workflow de limpeza de banco de dados) ou outras definições globais no nível da plataforma.

Saiba mais sobre [Opções](../../installation/using/configuring-campaign-options.md).
+++

+++**Interação de saída**

*Contexto: Interação de campanha*

Uma interação de saída é uma chamada para o motor de interação de uma lista de contatos (usada para delivery de emails, mala direta etc.). As mesmas regras e processos são aplicados a cada contato. Esse tipo de interação geralmente é processado em modo de lote.

Saiba mais sobre [Interação de saída](../../interaction/using/about-outbound-channels.md).
+++

+++**Exportação/importação de pacotes**

Uma exportação de pacote é uma operação que consiste na geração de um arquivo XML que contém definições de objetos. Os pacotes são usados para migrar a funcionalidade e as definições de uma instância para outra. Eles também são usados para adicionar definições essenciais de produtos aos sistemas de backup e controle de origem.

Saiba mais sobre [Exportação/importação de pacotes](../../platform/using/working-with-data-packages.md).
+++

+++**Paleta**

A paleta fluxo de trabalho exibe as atividades disponíveis que podem ser adicionadas a um fluxo de trabalho. Esse componente é mostrado em um formato de tabulação com atividades de workflow agrupadas logicamente pelo seu uso. As atividades disponíveis na paleta são determinadas pelos complementos que foram instalados na instância do Campaign e pelo contexto que exibe o workflow.

Saiba mais sobre [Paleta](../../workflow/using/building-a-workflow.md#adding-and-linking-activities).
+++

+++**Monitoramento de desempenho**

As informações de monitoramento de desempenho são exibidas na guia Monitoramento. Ele mostra métricas para o sistema subjacente, como uso de memória e CPU, estatísticas do servidor SMTP, processos do servidor e outras informações relevantes.

Saiba mais sobre [Monitoramento de desempenho](../../production/using/monitoring-processes.md).
+++

+++**Blocos de personalização**

O Adobe Campaign oferece blocos de personalização integrados que podem ser inseridos nos seus deliveries. Eles são dinâmicos, personalizados e contêm uma renderização específica. Por exemplo, você pode adicionar um logotipo, uma mensagem de saudação ou um link para uma mirror page. Vários blocos de personalização estão disponíveis por padrão. Você também pode definir blocos de personalização personalizados que permitirão otimizar a personalização do delivery. Os dados reais são inseridos em cada mensagem gerada durante a fase de análise do delivery.

Saiba mais sobre [Blocos de personalização](../../delivery/using/personalization-blocks.md).
+++

+++**Campo de personalização**

Um campo de personalização é uma única referência de campo de dados usada ao personalizar um delivery para um recipient específico. O valor de dados real é inserido durante a fase de análise de delivery.

Saiba mais sobre [Campos de personalização](../../delivery/using/personalization-fields.md).
+++

+++**Variáveis de personalização**

As variáveis de personalização são pedaços de código em um delivery que podem exibir texto diferente para recipients diferentes com base nas informações do recipient. Esses campos podem ser implementados como um campo ou bloco de personalização.

Saiba mais sobre [Variáveis de personalização](../../delivery/using/about-personalization.md).
+++

+++**Plano**

Um plano é um tipo de pasta usado para organizar atividades de marketing com base no calendário. As pastas de plano na visualização do Explorer definem unidades baseadas em tempo, como um ano, trimestre ou mês. As pastas de plano podem ser aninhadas e podem conter outras pastas de Plano, pastas de programa ou Campanhas.

Saiba mais sobre [Planos](../../campaign/using/setting-up-marketing-campaigns.md).
+++

+++**Filtros predefinidos**

Filtros predefinidos são queries que foram salvas para reutilização. O uso de filtros predefinidos aumenta a produtividade (porque são criados apenas uma vez), ajuda a criar consistência (porque todos os profissionais de marketing podem usá-los) e diminui as habilidades necessárias para o profissional de marketing, pois eles podem usar código ou lógica que talvez não consigam criar a si mesmos.

Saiba mais sobre [Filtros predefinidos](../../configuration/using/creating-filters.md).
+++

<!--
+++**Predictive Engagement Scoring**

Predictive engagement scoring predicts the probability of a recipient engaging with a message and the probability of opting out (unsubscribing) within the next seven days after the next email send. The probabilities are further divided into buckets according to the specific risk of disengagement, medium, or low. The model also provides the risk percentile rank for the customers to understand where the rank of a certain customer in relation to others. 

Learn more about [Predictive Engagement Scoring](../../platforrm/using/creating-filters.md).
+++
-->

+++**Chave primária**

A chave primária é o identificador exclusivo para cada registro em uma tabela de banco de dados. Uma tabela deve ter pelo menos uma chave. Como regra, as chaves são declaradas após o elemento principal do schema e os índices. As chaves primárias não podem ser compostas (incluir vários campos).

Saiba mais sobre [Chave primária](../../configuration/using/schema/key.md).
+++

+++**Perfil**

Um perfil é um registro de informações que representam um cliente final, um prospecto ou um cliente potencial. Cada perfil corresponde a um registro na tabela nmsRecipient ou uma tabela externa contendo a ID do cookie, a ID do cliente, o identificador móvel ou outras informações relevantes para um canal específico.

Saiba mais sobre [Perfis](../../platforrm/using/about-profiles.md).
+++

+++**Programa**

Programas e pastas de subprogramas organizam atividades de marketing em torno de um objetivo comercial, como fidelidade, aquisição ou venda cruzada. Eles também podem representar períodos fiscais ou táticas de campanha, como eventos ou boletins informativos. Cada programa contém campanhas vinculadas a um calendário, que fornece uma visualização geral.

Saiba mais sobre [Programas](../../campaign/using/setting-up-marketing-campaigns.md).
+++

+++**Recursos públicos**

A pasta Public resources, no Adobe Campaign, armazena imagens hospedadas pelo servidor de aplicativos. As imagens nos deliveries devem ser publicadas no servidor de aplicativos (ou em um servidor de hospedagem de imagem, se o Campaign estiver configurado dessa forma) para serem exibidas nos deliveries, como emails.

Saiba mais sobre [Recursos públicos](../../installation/using/deploying-an-instance.md#managing-public-resources).
+++

+++**Push**

As notificações por push são mensagens recebidas pelos aplicativos móveis. As notificações por push são configuradas para funcionar com o Adobe Campaign, incluindo o código SDK do Experience Platform no aplicativo móvel. Para Push, dois canais de delivery estão disponíveis: iOS e Android.

Saiba mais sobre [Empurrar](../../delivery/using/about-mobile-app-channel.md).
+++

## Q - T {#sec-5}

+++**Recipient**

No Adobe Campaign, os recipients são os perfis padrão direcionados para envio de deliveries (emails, SMS etc.) aos seus clientes. Os dados do destinatário armazenados no banco de dados permitem filtrar o target e adicionar dados de personalização. Normalmente, são informações pessoais, de contato, demográficas e transacionais, mas podem ser qualquer tipo de informação que seja compatível com marketing e análise.

Saiba mais sobre [Recipient](../../configuration/using/about-data-model.md).
+++

+++**Função de renderização**

*Contexto: Interação de campanha*

A função de renderização é definida em um espaço de oferta. É usado para construir sua representação de oferta com base nos atributos definidos na oferta. Há três modos diferentes de função de renderização: HTML, XML e texto.

Saiba mais sobre [Função de renderização](../../interaction/using/creating-offer-spaces.md).
+++

+++**Campanhas de redirecionamento**

Campanhas que direcionam novamente os recipients de um delivery ou deliveries anteriores.
+++

+++**Extensão de esquema**

A extensão de esquema permite personalizar os esquemas prontos para uso para melhor adequar seus casos de uso da empresa. Por exemplo, é possível adicionar o campo &quot;Fidelidade&quot; à tabela Recipient .

Saiba mais sobre [Extensão de esquema](../../configuration/using/extending-a-schema.md).
+++

+++**Schema**

Um esquema é um documento XML que define um tipo de dados específico. Os esquemas são implementados como tabelas de banco de dados no banco de dados do produto.  Os operadores manipulam esquemas no Campaign e o produto traduz suas ações no SQL necessário, que é executado no banco de dados. Observe que esses termos (Esquema/Tabela) são frequentemente usados alternadamente pelos Operadores, mas são elementos diferentes da arquitetura do produto.

Saiba mais sobre [Esquemas](../../configuration/using/about-schema-reference.md).
+++

+++**Seed addresses**

Seed addresses são usados para direcionar destinatários que não correspondem aos critérios de destino definidos. Dessa forma, os recipients que estiverem fora do escopo de delivery podem recebê-lo, como qualquer outro recipient target receberia.

Saiba mais sobre [Seed addresses](../../delivery/using/about-seed-addresses.md).
+++

<!--
+++**Send-time optimization**

To improve the open rate of your messages, you can manually define a sending time per recipient. Each profile will receive the message at the specified date and time, whenever possible. Defining a sending time can be done at the delivery level or using a workflow.

Learn more about [Send-time optimization](../../delivery/using/about-seed-addresses.md:).
+++
-->

+++**Serviço**

O Adobe Campaign permite criar e administrar serviços de informações, como boletins informativos ou atualizações de produtos, e gerenciar as assinaturas desses serviços. Vários serviços podem ser definidos em paralelo.

Saiba mais sobre [Serviços](../../delivery/using/about-services-and-subscriptions.md).
+++

+++**Gerenciamento SFTP**

No Painel de controle do Campaign, é possível interagir com todos os servidores SFTP conectados às instâncias do Campaign às quais você tem acesso. O Painel de controle do Campaign permite executar ações em seus servidores SFTP, como Monitorar a capacidade de armazenamento, Gerenciar endereços IP para permitir listagens e gerenciar chaves SSH públicas.

Saiba mais sobre [Gerenciamento SFTP](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/about-sftp-management.html?lang=en).
+++

+++**Atividade dos serviços de assinatura**

Essa atividade de workflow permite criar ou excluir uma subscrição de um serviço de informações para a população especificada na transição.

Saiba mais sobre [Atividade dos serviços de assinatura](../../workflow/using/subscription-services.md).
+++

+++**Aprovação do target**

*Contexto: Marketing distribuído da campanha*

Target approval é o processo de ter um Operador ou grupo de Operadores separado que aprova o target final de um delivery (após a fase de análise ter gerado o target) antes que o delivery possa ser enviado.

Saiba mais sobre [Aprovação do target](../../workflow/using/local-approval.md).
+++

+++**Dados do Target**

Os dados do Target são os dados armazenados na tabela de trabalho (transição) de um workflow. Esses dados estão disponíveis no delivery para personalização do conteúdo do delivery ou para definir a lógica de elementos dinâmicos do delivery.

Saiba mais sobre [Dados do Target](../../workflow/using/data-life-cycle.md#target-data).
+++

+++**Mapa do Target**

Esse é o mapeamento de canais de delivery para um tipo de dados específico. O Adobe Campaign não envia para endereços de email ou números de telefone propriamente ditos, mas para tipos de dados. Os mapas do Target (às vezes chamados de Mapas de entrega) definem como diferentes canais de entrega se vinculam aos campos de dados de um esquema. Ele define como o Campaign envia para esse tipo de dados usando um campo ou expressão específica.

Saiba mais sobre [Dados do Target](../../delivery/using/define-the-right-audience.md#target-mappings).
+++

+++**Atividades de direcionamento**

Essas são atividades de workflow específicas para direcionar, manipular dados de população e filtrar atividades. Eles permitem que os Operadores criem um ou mais targets definindo conjuntos e dividindo ou combinando esses conjuntos usando operações de interseção, união ou exclusão.

Saiba mais sobre [Atividades de direcionamento](../../workflow/using/about-targeting-activities.md).
+++

+++**Dimensão de direcionamento**

O tipo de dados produzido (retornado) por um query ou outras atividades de workflow. Observe que o Adobe Campaign retorna somente a Chave primária das linhas de banco de dados do entrevistado, independentemente da consulta usada para obtê-las.

Saiba mais sobre [Dimensão de direcionamento](../../workflow/using/targeting-data.md).
+++

+++**Atividade da tarefa**

*Contexto: Gestão dos Recursos de Marketing (MRM)*

A atividade de workflow Tarefa incorpora a ação humana à lógica de um workflow. Você pode especificar dois cenários: o primeiro se a tarefa for concluída e um segundo se a tarefa não for concluída (se estiver marcada manualmente como incompleta ou se ela expirar).

Casos de uso típicos são para incorporação de ações offline em uma campanha ou para ações personalizadas, como aprovações.

Em um workflow de campanha, a atividade Task



Saiba mais sobre [Atividade da tarefa](../../workflow/using/task.md).
+++

<!--
+++**Task**

One iteration of the defined functionality of a workflow activity. Each execution of a task has a unique task identifier.   

Learn more about [Tasks](../../workflow/using/about-workflows.md).
+++
-->

+++**Template**

Um modelo é um elemento de design usado para criar um objeto. Ele contém configurações de objeto e, opcionalmente, o conteúdo do objeto. O sistema de templates é usado para criar deliveries, campanhas, workflows e muitos outros elementos do Adobe Campaign. Os templates de fábrica disponíveis são definidos pelos pacotes instalados. Os modelos podem ser duplicados e personalizados, conforme necessário, pelos Operadores de campanha.
+++

<!--
+++**Test profiles**

Allows targeting of additional recipients who do not match the defined targeting criteria. They are added to a message’s audience to detect any fraudulent use of your recipient database or to ensure delivery. Seen as the Seed type in the Campaign interface.

Learn more about [Test profiles](../../workflow/using/about-workflows.md).
+++
-->

<!--
+++**Total database storage**

The aggregate size of the production and non-production instance(s) database storage managed by Adobe. 

Learn more about [Total database storage](../../workflow/using/about-workflows.md).
+++
-->

+++**Logs de rastreamento**

O fluxo de trabalho técnico de rastreamento recupera os dados de rastreamento depois que o delivery é enviado e o rastreamento ativado. Esses dados podem ser encontrados na guia Rastreamento do seu delivery. Você pode encontrar informações para aberturas e cliques em um email ou outras interações com uma mensagem recebida pelo recipient.

Saiba mais sobre [Logs de rastreamento](../../delivery/using/accessing-the-tracking-logs.md).
+++

+++**Mensagens transacionais**

As mensagens transacionais são um módulo do Campaign projetado para gerenciar notificações de acionador personalizadas geradas por eventos enviados por um sistema de informações externo. Uma mensagem transacional é uma comunicação individual e única enviada em tempo real a um usuário por um provedor, como um site. É particularmente esperado, pois contém informações importantes que o recipient deseja verificar ou confirmar.

Saiba mais sobre [Mensagens transacionais](../../message-center/using/about-transactional-messaging.md).
+++

+++**Campanhas acionadas**

Campanhas acionadas são campanhas que são executadas quando uma solicitação de API é recebida em um workflow. As chamadas de API são consumidas por uma atividade Signal no workflow que inicia a execução do workflow.

Saiba mais sobre [Campanhas acionadas](../../workflow/using/external-signal.md).
+++

<!--
+++**Triggers**

Signals that initiate execution of a workflow, delivery or other action. Typically an API call. 

Learn more about [Triggers](../../workflow/using/about-workflows.md).
+++
-->

+++**Regra de tipologia**

*Contexto: Otimização de campanha*

As regras de tipologia são regras de negócios que são implementadas como parte da fase de análise do delivery. As regras de tipologia são verificações do conteúdo do delivery (Regras de controle) ou do target do delivery (Regras de filtragem) ou de outra lógica (Regras de pressão) que impõem requisitos comerciais. As regras são elementos granulares que podem ser incluídos em uma ou mais Tipologias.

Saiba mais sobre [Tipologias](../../campaign-opt/using/about-campaign-typologies.md#typology-rules).
+++

+++**Tipologia**

*Contexto: Otimização de campanha*

Uma tipologia é um agrupamento das Regras de tipologia aplicadas à fase de análise de um delivery. Uma tipologia de campanha pode conter várias regras de tipologia, mas uma entrega só pode fazer referência a uma tipologia.

Saiba mais sobre [Tipologias](../../campaign-opt/using/about-campaign-typologies.md#typologies).
+++

## U - Z {#sec-6}

+++**Modo Unitário**

*Contexto: Interação de campanha, mensagens transacionais*

No modo unitário são, um único contato é processado pelo mecanismo de oferta no tempo de execução. Esse modo geralmente é usado para interações de entrada e mensagens transacionais.

Saiba mais sobre [Modo Unitário](../../interaction/using/about-inbound-channels.md).
+++

<!--
+++**Universes**

Application pages hosted by the Campaign instance. Used for approval forms, landing pages, opt-out forms, preference pages or to implement other business requirements.  

Learn more about [Universes](../../workflow/using/about-workflows.md).
+++
-->

+++**Aplicativos web**

Os aplicativos web são páginas de aplicativos dinâmicos e interativos hospedadas pela instância do Campaign. Ele contém dados do banco de dados e conteúdo adaptado aos direitos do usuário conectado. Por exemplo, é possível criar um formulário de edição em uma extranet ou formulários de notificação, incluindo dados do banco de dados com tabelas, gráficos, formulários de entrada etc. Essa funcionalidade permite criar e publicar páginas da Web em que os usuários podem pesquisar ou inserir informações.

Saiba mais sobre [Aplicações web](../../web/using/about-web-applications.md).
+++

+++**Diário de Fluxo de Trabalho**

O journal de workflow é o log de execução passo a passo de um workflow. Ele contém todo o histórico ou trilha de auditoria do workflow. Ele é usado para fins de desenvolvimento, solução de problemas ou depuração.

Saiba mais sobre [Diário de Fluxo de Trabalho](../../workflow/using/monitoring-workflow-execution.md).
+++

+++**Workflow**

Um workflow é uma representação visual do fluxo de execução da campanha. Ele permite orquestrar a gama completa de processos e tarefas em diferentes módulos do servidor de aplicativos. Esse ambiente gráfico abrangente permite criar processos, inclusive segmentação, execução de campanha, processamento de arquivos, participação humana, etc. O mecanismo de workflow executa e rastreia esses processos.

Saiba mais sobre [Fluxos de trabalho](../../workflow/using/about-workflows.md).
+++

+++**Worktable**

A tabela de trabalho contém todas as informações transportadas por transições de workflow. Cada workflow usa várias tabelas de trabalho. Os dados transmitidos nessas tabelas podem ser acelerados e usados no ciclo de vida do workflow, desde que não sejam apagados. De fato, tabelas desnecessárias são removidas toda vez que o workflow se torna passivo e possivelmente durante a execução dos maiores workflows para evitar sobrecarga no servidor.

Saiba mais sobre [Worktables](../../workflow/using/about-workflows.md).
+++