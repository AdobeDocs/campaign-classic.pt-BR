---
title: Versão 18.10
seo-title: Versão 18.10
description: Versão 18.10
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: cb2fb5a338220c54aba96b510a7371e520c2189e
workflow-type: tm+mt
source-wordcount: '2367'
ht-degree: 98%

---


# Versão 18.10{#release-18-10}

## Versão 18.10.6 - Build 8985{#release-18-10-6-build-8985}

12 de julho de 2019

**Aprimoramentos**

* Agora permitimos a exclusão de registros fictícios criados no Microsoft Dynamics durante o fluxo de trabalho de importação.
* Correção de um problema com a atividade de fluxo de trabalho File collector que poderia registrar erros em loop quando o acesso a um arquivo era negado. (NEO-12085)
* Correção de um problema que resultava em discrepâncias de relatório entre as atividades do usuário e os relatórios de rastreamento do indicador de abertura de delivery. (NEO-11742)
* Permissões aprimoradas para executar o pacote de zona de segurança ao usar a conta interna.
* Correção de um problema que poderia causar erros nos logs mtachild. (NEO-8978)

## Versão 18.10.5 - Build 8984{#release-18-10-5-build-8984}

23 de abril de 2019

**Aprimoramentos**

* Correção de um problema de impasse do SQL que resultava na falha da análise de delivery em caso de análise/envio simultâneo (quando duas deliveries são analisadas ao mesmo tempo). (NEO-13026)
* Remoção do limite de 10.000 registros no Mapa de Aquecimento do Fluxo de Trabalho para corrigir um problema de dados ausente. (NEO-12329)
* Correção de um problema ao usar a opção &quot;Manter todos os dados adicionais do conjunto principal&quot; em uma atividade de workflow de enriquecimento. (NEO-13291)

## Versão 18.10.4 - Build 8983{#release-18-10-4-build-8983}

15 de abril de 2019

**Aprimoramentos**

* Correção de um problema com o processo de computação de indicadores de rastreamento para mensagens transacionais. (NEO-12529, NEO-12581)
* Correção de um problema com API HTTPRequest que não esperou o término de todos os retornos de chamada. (NEO-12628)
* Os índices foram adicionados nas tabelas temporárias de cupom para otimizar o envio de delivery. (NEO-12437)
* Correção de um problema ao analisar uma mensagem que tinha como target recipients para domínios japoneses (.JP). (NEO-12246)
* Na integração do Analytics, a recuperação de dados de segmento de AAM com caractere % agora é permitida. (NEO-12025)
* Correção de um problema de falha do Tomcat ao enviar notificações por push usando HTTP2. (NEO-12701)

## Versão 18.10.3 - Build 8981{#release-18-10-3-build-8981}

29 de janeiro de 2019

>[!CAUTION]
>
>Esta configuração foi retomada. Atualize [para a versão](../../production/using/build-upgrade.md) mais recente ou entre em contato com o Atendimento [ao cliente da](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)Adobe.

**Aprimoramentos**

* Correção de um problema com a atividade do workflow s3 Transferência de Arquivo. (NEO-12473)
* Correção de um problema que poderia falhar o workflow de Rastreamento. (NEO-12520)
* Correção de um problema com o login de IMS.
* Correção de um problema com a pré-visualização e aprovação do conteúdo em mensagens transacionais ao usar uma ID de oferta grande.
* Correção de um problema com o workflow Mid-sourcing (contadores de delivery).
* Correção de um problema com a atualização da estrutura do banco de dados que descartava novos índices no NmsRecipient.
* Correção de uma falha do console que poderia ocorrer ao usar a opção Definido em um arquivo externo para o target principal de um delivery. (NEO-12349)
* Correção de várias falhas InMail.
* Correção de um problema ao usar uma atividade de workflow de dados da Atualização para excluir registros armazenados em um banco de dados da FDA Teradata.
* Correção de problemas de inconsistência no gerenciamento de chaves secretas.
* Correção de um problema com a atividade de Enriquecimento ao digitar um campo como: xml=true e calculated=true
* Correção de um problema de pular caracteres ao enviar notificações via push em um aplicação móvel.
* Correção de um problema que impedia a alternância do FDA para o método de sincronização SOAP em uma conta externa Mid-Sourcing.

## Versão 18.10.2 - Build 8978{#release-18-10-2-build-8978}

6 de dezembro de 2018

>[!CAUTION]
>
>Esta configuração foi retomada. Atualize [para a versão](../../production/using/build-upgrade.md) mais recente ou entre em contato com o Atendimento [ao cliente da](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)Adobe.

**Aprimoramentos**

* Corrigidos vários problemas ao executar workflows usando MySQL na FDA. (NEO-11652)
* Correção de um problema de desempenho ao enviar notificações por push. (NEO-11787)
* Correção de um problema de esgotamento de ID ao usar seed addresses em um delivery. (NEO-11842)
* Correção de um problema de congelamento do cliente que pode ocorrer ao usar workflows complexos. (NEO-11847)
* Correção de um problema de exibição ao usar uma distribuição de valores com um link 1:N. (NEO-11820)
* Corrigido um erro Oracle em Heatmap do workflow.
* Correção de um problema certo ao adicionar uma apresentação de oferta em uma atividade de enriquecimento.
* Correção de um problema de conexão de gestão de dados SQL.
* Correção de um problema com a geração de nomes de tabela de workflow temporários em caso de IDs negativas.
* Correção de um problema com o cálculo das durações do workflow no Workflow HeatMap.


## Versão 18.10 - Build 8977{#release-18-10-build-8977}

5 de nov de 2018

>[!CAUTION]
>
>Esta configuração foi retomada. Atualize [para a versão](../../production/using/build-upgrade.md) mais recente ou entre em contato com o Atendimento [ao cliente da](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)Adobe.

**Novidades**

<table> 
 <thead> 
  <tr> 
   <th> Funcionalidade<br /> </th> 
   <th> Descrição<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Melhorias da notificação por push<br /> </td> 
   <td> Várias melhorias foram implementadas para notificação por push no Adobe Campaign:<br /> 
    <ul> 
     <li> <p>Rastrear notificações silenciosas no iOS </p> </li> 
     <li> <p>Implementar feedback sobre chamadas de registro no iOS</p> </li> 
     <li> <p>Melhorar a velocidade da preparação de delivery no iOS</p> </li> 
    </ul> <p>Como parte da depreciação do GCM pelo Google, o conector Android V2 agora permite conexões somente ao servidor FCM.</p><p>Para obter mais informações, consulte a <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">documentação detalhada</a>. A atualização manual para o FCM é detalhado neste <a href="https://helpx.adobe.com/br/campaign/kb/migrate-to-fcm.html">artigo</a>. </p> </td> 
  </tr> 
  <tr> 
   <td> Gestão de Dados SQL<br /> </td> 
   <td> <p>Foi adicionada uma nova atividade de workflow de gestão de dados. A atividade de <strong>Gestão de Dados SQL</strong> permite escrever ou copiar e colar seus próprios scripts SQL para criar e preencher tabelas de trabalho (apenas FDA). </p> <p>Para obter mais informações, consulte a <a href="../../workflow/using/sql-data-management.md">documentação detalhada</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Monitoramento de workflow<br /> </td> 
   <td> <p>Com o novo Adobe Campaign Workflow HeatMap, os administradores da plataforma têm uma representação gráfica rápida de todos os workflows simultâneos, o que permite monitorar a carga na instância e planejar os workflows de acordo.</p> <p>Para obter mais informações, consulte a <a href="../../workflow/using/heatmap.md">documentação detalhada</a>.</p> <p>O pacote Workflow HeatMap também está disponível sob demanda para builds anteriores ao 8977 (a partir do build 8700). Para obter mais informações sobre a solicitação e a instalação, consulte <a href="https://helpx.adobe.com/br/campaign/kb/install-workflow-heatmap-package.html">esta página</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Aprimoramentos de segurança**

* Correção de um problema de segurança que poderia resultar em vulnerabilidades para ataques Server Side Request Forgery (SSRF) attacks and denial of service (DoS). (NEO-11453)
* O conteúdo (redirecionamento de rastreamento, mirror pages, pesquisas etc.) agora será distribuído pelo Campaign com o cabeçalho X-Robots-Tag: nocache. Isso impede o indexação deste conteúdo por mecanismos de pesquisa da Internet. (NEO-11101)
* Correção de um problema de injeção de XTK na API de subscrição (nms:subscription:Unsubscribe e nms:subscription:Subscribe).
* Correção de um problema de injeção de XTK em unsubscription da aplicação Web.
* Senhas removidas que foram exibidas sem segurança em alguns logs SMS.

**Aprimoramentos**

* As APIs do Campaign Classic agora estão disponíveis em uma [página dedicada](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html). Se estiver usando o arquivo jsapi.chm, agora deverá fazer referência a nova versão online.
* PostgreSQL 10, Debian 9 e Teradata 16.20 agora são suportados. Consulte a [Matriz de Compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html).
* Ao criar uma conexão SFTP, agora você pode usar a autenticação de proxy. Para obter mais informações, consulte a [documentação detalhada](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration) (NEO-9868).
* A opção **Fórmula de cálculo de data** está agora disponível nas propriedades de delivery ao criar um delivery único usando o template de delivery de mala direta. (NEO-9792)
* A gestão de nomes de domínio foi aprimorado para rastreamento de cookies e aplicações Web. Consulte a seção &quot;Evoluções técnicas&quot; abaixo para obter mais informações.
* A importação de ativos compartilhados da Adobe Experience Cloud em um delivery ou landing page foi aprimorada em termos de segurança e desempenho.
* Uma nova caixa de seleção está disponível na conta externa do canal móvel para habilitar rastreamentos SMPP detalhados no arquivo de log, o que torna esse output diretamente acessível da interface do Adobe Campaign.
* Há agora uma distinção nos broadlogs entre o número máximo de conexões e o número máximo de mensagens por hora. Quando os limites são atingidos, é possível saber o motivo da taxa de transferência ser limitada. Anteriormente, a mesma mensagem (‘cota atingida’) se aplicava a ambos os casos.
* Agora você pode especificar um script SQL a ser executado ao adquirir uma conexão do pool. Esse script pode ser usado para definir o schema padrão. Este script será aplicado após faixas de query. (NEO-11256)
* O SDK do Campaign não armazena mais o ID de usuário para estar em conformidade com as normas de PII. Agora os dados são armazenados como um hash.
* Ao importar um arquivo XML de exportação de pacote, o Campaign agora dá suporte à presença de BOM no arquivo, mesmo que a codificação seja explicitamente declarada.

**Evoluções técnicas**

Atualização de cliente e servidor

>[!CAUTION]
>
>Se você tiver um servidor atualizado para 18.10, precisará usar um cliente 18.10 para acessar o servidor. O cliente 18.10 poderá se conectar a uma versão de servidor mais antiga.

Gestão de nome de domínio

A gestão de nomes de domínio foi aprimorado para rastreamento de cookies e aplicações Web.

Agora, todos os nomes de domínio de segundo nível de duas letras são suportados por padrão (por exemplo, .aa.com). Para nomes de domínio mais complexos (por exemplo, domínios de segundo nível de três letras, como .com.au), é necessário adicioná-los na opção **cookieDomains** do serverConf (na tag de redirecionamento). Aqui está um exemplo:

```
<redirection cookiedomain="http://toureiffel.paris">
```

Melhorias de índice

Os índices no NmsRecipient foram retrabalhados. Isso deve melhorar o desempenho em queries que usam essa tabela. Se tiver feito uma extensão de NmsRecipient, talvez você queira verificar se não possui índices duplicados (para minimizar o uso de espaço no servidor de banco de dados). (NEO-8228)

No PostgreSql ao usar um agrupamento UTF-8, agora é possível criar índices que otimizará as operações &quot;LIKE &#39;string%&#39;&quot; (ou &quot;inicia com&quot;). Se você executar outras operações na mesma coluna (por exemplo, ordenar ou unir), outro índice padrão será necessário. No lado do schema, isso será realizado adicionando indexOption=&quot;searchFromStart&quot; na definição do índice (criará um índice varchar_pattern_ops em vez de um índice btree padrão). Por exemplo (em NmsRecipient):

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

Novos índices foram adicionados ao NmsRtEvent e NmsEventHisto (na coluna &quot;Agendado&quot;), isso deve melhorar o tempo de exibição no formulário correspondente (NEO-11738).

Essas alterações de índice podem levar a um aumento do tempo necessário para executar a pós-atualização.

**Correções**

* Correção de um erro que impedia que os arquivos da atividade do workflow de **download da Web** fossem baixados. (NEO-11105)
* Correção de um erro que ocasionalmente deixava o workflow **de envio de indicadores e atributos de campanha** em um estado de falha (NEO-10820).
* Correção de um problema que excluiu a lista de recipient criada após a execução da atividade de atualização da lista em um workflow. (NEO-11696)
* Correção de um problema que exibia incorretamente as campanhas com um mês de antecedência no calendário do Campaign (em uma instância japonesa). (NEO-11445)
* Correção de um problema que impedia que a configuração do Analytics fosse exibida na guia do Web Analytics das propriedades de delivery. (NEO-11619)
* Correção de um erro exibido ao tentar editar e salvar o formulário de entrada nms:delivery. (NEO-10973)
* Correção de um problema de configuração da conta externa que ocorria ao executar um workflow contendo uma atividade de transferência de arquivos. (NEO-11012)
* Correção de um problema que retornava linhas em branco ao usar a função zcat para carregar arquivos na atividade de carregamento de dados. (NEO-11273)
* Correção de um problema que gerava vários logs duplicados durante a análise do delivery. (NEO-11360)
* Correção de um problema que resultava a falha no delivery devido à falta de chave de link estrangeira após a execução da atividade de Enriquecimento em um workflow. (NEO-11537)
* Correção de um problema que impedia a desinstalação correta ou reparo do Adobe Campaign quando o caminho de instalação incluía caracteres chineses GB18030 específicos.
* Correção de um problema que vinculava alguns logs de rastreamento ao delivery errado. (NEO-11412)
* Correção de um problema que poderia resultar em algumas partes dos logs de delivery restantes com status pendente por mais tempo que o esperado. (NEO-11336)
* Correção de um erro que ocorria ao editar um query para adicionar um cupom a um delivery. (NEO-11037)
* Correção de um problema nos relatórios que resultava sempre na soma dos valores, não importando qual operador agregado era selecionado. (NEO-10913)
* Como a função &quot;request.scheme&quot; foi preterida, ela foi removida da documentação JSAPI. (NEO-10828)
* Correção de um problema que impedia que alguns usuários com configurações específicas de fuso horário a fazerem logon no Adobe Campaign. (NEO-10712)
* Correção de um problema que ocorria ao configurar uma conta externa do canal móvel usando o conector SMPP genérico estendido: se você especificou usando parâmetros diferentes para o receptor, o transmissor usaria esses parâmetros incorretamente em vez de seus próprios parâmetros.
* Correção de um problema que resultava em falha nos deliveries programados ao definir uma frequência para a regra de pressão, porque os deliveries eram constantemente recalculados após a primeira arbitragem. (NEO-10016)
* Correção de um problema que resultava em falha no servidor Web IIS durante o processo de reciclagem do Pool de Aplicativos (na biblioteca nlsrvmod.dll). (NEO-10862)
* Correção de um problema que poderia impedir a pesquisa de um recipient na tela **Perfis e Target.** (NEO-8228)
* Correção de um problema que poderia resultar em erro de tempo limite ao acessar a pasta Histórico de Eventos no caso de um número alto de registros. (NEO-11738)
* Correção de um problema que poderia resultar em recipients de delivery LINE retornados incorretamente como &quot;Inacessível&quot;. (NEO-10833)
* Correção de um problema ao executar um query de workflow com uma coluna adicional no Oracle. (NEO-11615)
* Uma melhoria foi implementada para garantir que as conexões fechadas não sejam mantidas no pool de conexões por muito tempo. (NEO-11392)
* Correção de um problema ao usar uma atividade de workflow para construção do target (query, carregamento de dados (RDBMS), etc.) conectado via FDA a uma tabela externa Oracle que continha caracteres UTF8 (no nome da tabela, nome do campo, etc.) e que também contém uma restrição de chave primária com um nome de restrição padrão gerado pelo sistema. (NEO-10714)
* Correção de um problema que poderia impedir a exclusão do conteúdo HTML de um delivery. (NEO-11327)
* Correção de um problema com a pré-visualização de arquivos XML e CSV em uma mala direta após a execução de uma campanha. (NEO-11290)
* Correção de um problema ao classificar dados em uma atividade de workflow de enriquecimento. (NEO-11394)
* Correção de um problema ao classificar dados em um relatório personalizado. (NEO-10896)
* Correção de um problema que resultava em erros ao usar a configuração useVault com Teradata. (NEO-11399)
* Correção de um problema que resultava em falha no console do cliente Adobe Campaign ao excluir várias linhas de query. (NEO-10744)
* Correção de um problema que impedia que as regras de pressão fossem aplicadas em alguns casos ao enviar um delivery de mala direta. (NEO-9004)
* Correção de um problema que ocorria ao usar a atividade de carregamento de dados para importar uma coluna com o tipo de dados ‘tempo’: o separador de tempo seria redefinido mesmo após sua remoção. (NEO-10743)
* Correção de um problema que impedia que a pasta Deliveries fosse exibida da lista Pasta de execução nas propriedades de Delivery ao editar um delivery recorrente. (NEO-11094)
* Correção de um problema que impedia que a janela Exibir público exibisse mais de 200 registros como o target resultante de uma atividade de Query em um workflow. (NEO-11195)
* Correção de um problema no Oracle que impedia que um query DELETE fosse executado com mais de 1000 elementos selecionados. (NEO-11171)
* Correção de um problema que levou a codificar URLs como URLs rastreadas nos parâmetros adicionais de um delivery de notificação por push no Android. (NEO-11468)
* Corrigido um erro de script que ocorria no relatório de atividades do usuário ao definir os parâmetros como ‘intervalos de um dia’ e ‘Aberturas’. (NEO-11655)
* Correção de um problema que ocorreu ao se conectar ao servidor mid-sourcing ou ao Centro de Mensagens por um proxy da Web autenticado. (NEO-11309)
* Correção de um erro no Oracle que ocorria quando uma nova composição de delivery era salva após selecionar um elemento de um schema específico **baseado em um modo de exibição SQL**. (NEO-11682)
* Correção de um problema que resultou em arquivos de rejeição gerados que continha falsos positivos ao processar um arquivo zip contendo um arquivo .csv por uma atividade de carregar arquivo usando a opção de Descompactação.
* xtkjoblog agora foi removido pela atividade de limpeza.

