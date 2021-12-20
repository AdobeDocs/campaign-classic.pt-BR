---
product: campaign
title: Versões de Campaign Classic 2018
description: Saiba mais sobre as versões do Campaign Classic 2018
source-git-commit: eb0e572f0bb6196a58a7dab4999df784d5c4851f
workflow-type: tm+mt
source-wordcount: '5414'
ht-degree: 97%

---

# Versões de 2018{#release-2018}

![](../../assets/v7-only.svg)

## Versão 18.10

### Versão 18.10.6 – Build 8985{#release-18-10-6-build-8985}

12 de julho de 2019

**Aprimoramentos**

* Agora permitimos a exclusão de registros fictícios criados no Microsoft Dynamics durante o fluxo de trabalho de importação.
* Correção de um problema com a atividade de fluxo de trabalho File collector que poderia registrar erros em loop quando o acesso a um arquivo era negado. (NEO-12085)
* Correção de um problema que resultava em discrepâncias de relatório entre as atividades do usuário e os relatórios de rastreamento do indicador de abertura de delivery. (NEO-11742)
* Permissões aprimoradas para executar o pacote de zona de segurança ao usar a conta interna.
* Correção de um problema que poderia causar erros nos logs mtachild. (NEO-8978)

### Versão 18.10.5 – Build 8984{#release-18-10-5-build-8984}

23 de abril de 2019

**Aprimoramentos**

* Correção de um problema de impasse do SQL que resultava na falha da análise de delivery em caso de análise/envio simultâneo (quando duas deliveries são analisadas ao mesmo tempo). (NEO-13026)
* Remoção do limite de 10.000 registros no Mapa de Aquecimento do Fluxo de Trabalho para corrigir um problema de dados ausente. (NEO-12329)
* Correção de um problema ao usar a opção &quot;Manter todos os dados adicionais do conjunto principal&quot; em uma atividade de workflow de enriquecimento. (NEO-13291)

### Versão 18.10.4 – Build 8983{#release-18-10-4-build-8983}

15 de abril de 2019

**Aprimoramentos**

* Correção de um problema com o processo de cálculo de indicadores de rastreamento para mensagens transacionais. (NEO-12529, NEO-12581)
* Correção de um problema com API HTTPRequest que não esperou o término de todos os retornos de chamada. (NEO-12628)
* Os índices foram adicionados nas tabelas temporárias de cupom para otimizar o envio de delivery. (NEO-12437)
* Correção de um problema ao analisar uma mensagem que tinha como target recipients para domínios japoneses (.JP). (NEO-12246)
* Na integração do Analytics, a recuperação de dados de segmento de AAM com caractere % agora é permitida. (NEO-12025)
* Correção de um problema de falha do Tomcat ao enviar notificações por push usando HTTP2. (NEO-12701)

### Versão 18.10.3 – Build 8981{#release-18-10-3-build-8981}

29 de janeiro de 2019

>[!CAUTION]
>
>Esta configuração foi retomada. Por favor [atualizar para a build mais recente](../../production/using/build-upgrade.md)  ou contato [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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

### Versão 18.10.2 – Build 8978{#release-18-10-2-build-8978}

6 de dezembro de 2018

>[!CAUTION]
>
>Esta configuração foi retomada. Por favor [atualizar para a build mais recente](../../production/using/build-upgrade.md) ou contato [Atendimento ao cliente do Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Aprimoramentos**

* Corrigidos vários problemas ao executar workflows usando MySQL na FDA. (NEO-11652)
* Correção de um problema de desempenho ao enviar notificações por push. (NEO-11787)
* Correção de um problema de esgotamento de ID ao usar seed addresses em um delivery. (NEO-11842)
* Correção de um problema de congelamento do cliente que pode ocorrer ao usar workflows complexos. (NEO-11847)
* Correção de um problema de exibição ao usar uma distribuição de valores com um link 1:N. (NEO-11820)
* Correção de um erro de Oracle no Workflow Heatmap.
* Correção de um problema certo ao adicionar uma apresentação de oferta em uma atividade de enriquecimento.
* Correção de um problema de conexão de gestão de dados SQL.
* Correção de um problema com a geração de nomes de tabela de workflow temporários em caso de IDs negativas.
* Correção de um problema com o cálculo das durações do workflow no Workflow HeatMap.


### Versão 18.10.1 – Build 8977{#release-18-10-build-8977}

5 de nov de 2018

>[!CAUTION]
>
>Esta configuração foi retomada. Por favor [atualizar para a build mais recente](../../production/using/build-upgrade.md) ou contato [Atendimento ao cliente do Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
* Correção de um problema de injeção de XTK na API de assinatura (nms):subscription:Cancelar inscrição e nms:subscription:Assinar).
* Correção de um problema de injeção de XTK em unsubscription da aplicação Web.
* Senhas removidas que foram exibidas sem segurança em alguns logs SMS.

**Aprimoramentos**

* As APIs do Campaign Classic agora estão disponíveis em uma [página dedicada](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=pt-BR). Se estiver usando o arquivo jsapi.chm, agora deverá fazer referência a nova versão online.
* PostgreSQL 10, Debian 9 e Teradata 16.20 agora são suportados. Consulte a [Matriz de Compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html).
* Ao criar uma conexão SFTP, agora você pode usar a autenticação de proxy. Para obter mais informações, consulte a [documentação detalhada](../../installation/using/file-res-management.md) (NEO-9868).
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
* Correção de um problema que poderia impedir a pesquisa de um recipient na tela **Perfis e Target.** (NEO8228)
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

## Versão 18.6

### Versão 18.6.2 – Build 8949{#release-18-6-3-build-8949}

22 de agosto de 2018

>[!CAUTION]
>
>Esta configuração foi retomada. Por favor [atualizar para a build mais recente](../../production/using/build-upgrade.md) ou contato [Atendimento ao cliente do Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Faixas de query<br /> </td> 
   <td> <p>Quando vários usuários do Campaign se conectam à mesma conta externa FDA Teradata, agora você pode passar uma faixa de query (pares de chave-valor) específica para cada usuário. Sempre que um usuário do Campaign realizar um query no banco de dados Teradata, o Adobe Campaign agora poderá enviar metadados associados ao usuário. Esses dados, que consistem em uma lista de chaves e valores, podem ser então usados pelos administradores Teradata para fins de auditoria ou para gerenciar direitos de acesso, por exemplo.</p><p>Para obter mais informações, consulte a <a href="../../installation/using/external-accounts.md">documentação detalhada</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Aprimoramentos**

* Os logs de arquivamento de emails foram aprimorados, o que facilita e agiliza a verificação de quais emails foram entregues com êxito ou falharam no arquivamento do Cco. (NEO-10675)
* Correção de um problema que levou à exibição dos IPs do balanceador de carga em vez dos IPs do cliente no rastreamento de broadlogs. (NEO-11295)
* Correção de um problema aleatório que fazia com que as propriedades de um delivery fossem substituídas incorretamente. (NEO-11015)
* Correção de um erro de sintaxe ao classificar resultados da atividade de enriquecimento. (NEO11394)
* Correção de um problema ao usar campos calculados em uma atividade de workflow **[!UICONTROL Survey answers]**. (NEO-11382)
* O Tomcat foi atualizado para evitar a exploração de vulnerabilidades. (NEO-11503)
* Correção de um erro com codificação LATIN1 ao usar um FDA Connection para um banco de dados PostgreSQL. (NEO-11299)
* Correção de um problema que ocorria ao usar o **[!UICONTROL Prepare the personalization data with a workflow]** opção de delivery. (NEO-11047)
* Correção de um problema postupgrade que impedia o envio de SMS ao usar um conector estendido.
* Importação/exportação de pacotes aprimorada (log e região foram adicionados à interface).
* Correção de um problema que exibia erros inúteis no log após a atualização quando uma atividade de workflow **[!UICONTROL Survey answers]** não estava totalmente configurada.

**Evoluções técnicas**

Faixas de query

Uma chave específica (PROXYUSER ou PROXYROLE) é usada para associar um usuário ou função Teradata a um usuário do Campaign. Uma nova permissão foi adicionada para usar este usuário/função proxy. É necessário adicionar o acesso GRANT CONNECT THROUGH à conta do banco de dados (aquele definido na conta externa do Teradata).

Uma nova guia foi adicionada nas contas externas do Teradata. A guia **[!UICONTROL Query banding]** inclui as seguintes opções:

* **[!UICONTROL Active]**: marque esta caixa para ativar o recurso.
* **[!UICONTROL Default]**: insira uma faixa de query padrão que será usada se um usuário não tiver nenhuma faixa de query associada. Se não houver faixa de query padrão definida, os usuários que não tiverem nenhuma faixa de query associada não poderão usar o Teradata.
* **[!UICONTROL Users]**: para cada usuário, especifique uma faixa de query. Você pode adicionar quantos pares chave-valor forem necessários. Por exemplo: &quot;priority=1;workload=high;&quot;

Para obter mais informações sobre faixa de query, consulte esses artigos:

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### Versão 18.6.1 – Build 8947{#release-18-6-build-8947}

25 de junho de 2018

>[!CAUTION]
>
>Esta configuração foi retomada. [Atualize para a configuração mais recente](../../production/using/build-upgrade.md) ou entre em contato com o [suporte técnico](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Melhorias de segurança<br /> </td> 
   <td> Uma série de aprimoramentos de segurança foi adicionada ao Campaign Classic. Os aprimoramentos e correções estão listados abaixo.<br /> </td> 
  </tr> 
  <tr> 
   <td> Suporte do Windows Server 2016<br /> </td> 
   <td> O Adobe Campaign agora é compatível com o Windows Server 2016. Consulte <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Matriz de compatibilidade do Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Aprimoramentos de segurança**

decryptString

A função **decryptString** foi preterida. Consulte o artigo [Recursos Preteridos e Removidos](deprecated-features.md).

Para novos clientes, essa função agora é usada apenas para descriptografar a ID criptografada do recipient nas landing pages. Para descriptografar senhas armazenadas em uma conta externa, use a nova função **decryptPassword** .

Para clientes existentes, o comportamento dessa função não é alterado, mas recomendamos que você use **decryptPassword** em vez de **decryptString**. A opção de compatibilidade **XtkSecurity_Unsafe_DecryptString** é adicionada pelo postupgrade e ativada por padrão, permitindo que continue usando a função. Se deseja desativar o **decryptString**, desative a opção.

decryptPassword

A função **decryptPassword** foi adicionada. Permite descriptografar uma senha armazenada em uma conta externa. Consulte a documentação [JSAPI](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) para obter mais informações.

APIs de Arquivo

Para novas instalações, o acesso às pastas por meio de APIs de arquivo é limitado à **var**, **sftp** e pastas temporárias do Adobe Campaign.

Para clientes existentes, as APIs de arquivo não podem mais acessar a pasta **conf** do Adobe Campaign. A opção de compatibilidade **XtkSecurity_Disable_JSFileSandboxing** é adicionada pelo postupgrade e ativada por padrão, permitindo que continue acessando as outras pastas. Se você quiser limitar o acesso ao **var**, **sftp** e pastas temporárias do Adobe Campaign, desative a opção.

**Correção**

* Correção de um problema que poderia afetar o desempenho da mensagem transacional de SMS. (NEO-9812)

## Versão 18.4

### Versão 18.4.5 – Build 8937{#release-18-4-5-build-8937}

21 de novembro de 2018

**Aprimoramentos**

* Corrigidos vários problemas ao executar workflows usando MySQL na FDA. (NEO11652)
* Correção de um problema que fazia com que uma parte da população de delivery permanecer no estado pendente, em casos específicos. (NEO11336)
* Correção de um problema intermitente com a resposta automática do SMS. (NEO-11811)
* Correção de um problema de esgotamento de ID ao usar seed addresses em um delivery. (NEO11842)
* Correção de um erro de sintaxe ao executar uma classificação em uma atividade do workflow de enriquecimento. (NEO11394)
* Correção de um problema que poderia causar falha no servidor Web ao reiniciar o IIS. (NEO10862)
* Correção de um problema que poderia causar falha no workflow de rastreamento após uma atualização de compilação (FDA - SQL). (NEO-11635)
* Correção de um problema que poderia causar perda de dados da lista de workflows. (NEO11696)
* Correção de um problema de desempenho ao enviar notificações por push. (NEO11787)
* Correção de um problema que impedia que o rastreamento Web funcionasse para domínios &quot;com.au&quot; (NEO-4385).
* Correção de um problema de congelamento do cliente que pode ocorrer ao usar workflows complexos. (NEO11847)
* Correção de um erro Oracle ao salvar um novo delivery após selecionar um elemento de um schema específico (NEO-11682).
* Correção de um problema ao realizar query em um campo contendo caracteres com acentos (FDA/Teradata). A conta externa agora permite alterar a codificação utilizada para se comunicar com o driver Teradata. (NEO-11818).
* Correção de um problema de rastreamento ao transmitir URLs em variáveis adicionais em uma notificação por push que poderia resultar em dados mal formatados ou incorretos recebidos pelo aplicativo móvel. (NEO-11468, NEO-11960)
* Correção de um problema que causava um problema de exibição ao usar uma distribuição de valores com um link 1:N. (NEO11820)
* Correção de um problema que impedia o funcionamento de carregamento em massa no Teradata 16.
* Aumento do tamanho do buffer para carimbo de data/hora no Teradata para evitar problemas de encadernação com driver 15.10.
* Melhorou o gerenciamento de índices de nomes longos que podem causar problemas após a atualização.
* Tempo de memória compartilhado aprimorado disponível durante o processamento de crianças menores (MTA).
* Correção de um possível bloqueio no Apache (rastreamento).


### Versão 18.4.4 – Build 8936{#release-18-4-4-build-8936}

1 de agosto de 2018

**Aprimoramentos**

* Os logs de arquivamento de emails foram aprimorados, o que facilita e agiliza a verificação de quais emails foram entregues com êxito ou falharam no arquivamento do Cco. (NEO10675)
* Correção de um problema que levou à exibição dos IPs do balanceador de carga em vez dos IPs do cliente no rastreamento de broadlogs. (NEO11295)
* Correção de um erro com codificação LATIN1 ao usar um FDA Connection para um banco de dados PostgreSQL. (NEO11299)
* Correção de um problema que ocorria ao usar o **[!UICONTROL Prepare the personalization data with a workflow]** opção de delivery. (NEO-11047, NEO-11301)
* Correção de um problema aleatório que fazia com que as propriedades de um delivery fossem substituídas incorretamente. (NEO11015)
* Correção de um problema ao usar campos calculados em uma atividade de workflow **[!UICONTROL Survey answers]**. (NEO11382)
* Correção de um problema ao usar dados armazenados em XML em uma atividade de workflow de **[!UICONTROL Survey answers]**. (NEO-10816)
* Correção de um problema ao executar a atualização do servidor com o build 8935.
* Correção de um problema que exibia erros inúteis no log após a atualização quando uma atividade de workflow **[!UICONTROL Survey answers]** não estava totalmente configurada.
* FDA Teradata: correção de um problema com campos incrementados automaticamente e índices em tabelas SQL.

### Versão 18.4.3 – Build 8935{#release-18-4-3-build-8935}

22 de junho de 2018

**Aprimoramentos**

* Correção de um problema de codificação de rastreamento com o Microsoft Edge e o Internet Explorer. (NEO-11257)
* Correção de um problema com a personalização do link de imagem em remessas LINE. (NEO-11077)
* Correção de um problema que impedia o funcionamento correto do mecanismo de geração de sequência de ID. (NEO-11115)
* Correção de um problema que impedia o funcionamento das solicitações de privacidade (GDPR) ao usar um namespace personalizado com uma chave de reconciliação de tipo inteiro. (NEO-11123)
* Correção de um erro que poderia ocorrer ao usar a opção **[!UICONTROL Distribution of values]** em atividades de workflow de **[!UICONTROL Query]**. (NEO-10958)
* Correção de um problema ao sincronizar espaços de oferta da instância de marketing para a instância de interação. (NEO-11162)
* Melhoria do gerenciamento de índices de nomes longos durante a pós atualização.

### Versão 18.4.2 – Build 8932{#release-18-4-2-build-8932}

22 de maio de 2018

**Aprimoramentos**

* Correção de um problema que impedia o funcionamento da atualização do Windows Server.
* Correção de um problema na atividade **[!UICONTROL Survey Result]** ao usar dados armazenados em XML. O relatório foi exibido incorretamente. (NEO10816)
* Correção de um problema de desempenho que poderia ocorrer com o processo inMail ao usar um servidor de email de devolução. (NEO-10641)
* Correção de um problema de atualização de banco de dados que pode ocorrer ao atualizar mais de 1000 schemas.

### Versão 18.4.1 – Build 8931{#release-18-4-build-8931}

24 de abril de 2018

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
   <td> European General Data Protection Regulation (GDPR)<br /> </td> 
   <td> <p>O GDPR é a nova lei de privacidade da União Europeia que concilia e moderniza os requisitos de proteção de dados, entrando em efeito em 25 de Maio de 2018. O GDPR aplica-se aos clientes do Adobe Campaign que coletam dados de residentes da UE.</p> <p>Além dos recursos de privacidade já disponíveis no Adobe Campaign (incluindo o gerenciamento de consentimento, as configurações de retenção de dados e as funções de usuários), aproveitamos a oportunidade, em função do nosso papel como Processador de Dados, para incluir recursos adicionais que ajudam o Controlador de Dados a estar de acordo com determinadas solicitações do GDPR:</p> 
    <ul> 
     <li> <p>Direito de acesso: permite que o Titular de dados receba uma cópia de seus dados pessoais capturados pelos Controladores de dados, incluindo potencialmente dados armazenados no Adobe Campaign.</p> </li> 
     <li> <p>Direito de Exclusão: possibilita que o Titular de dados apague seus dados pessoais capturados pelos Controladores de dados, possivelmente incluindo os dados armazenados no Adobe Campaign.</p> </li> 
    </ul> Para obter mais informações, consulte a <a href="https://helpx.adobe.com/br/campaign/kb/acc-privacy.html">documentação detalhada</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Perfis ativos<br /> </td> 
   <td> <p>O Adobe Campaign agora fornece a lista de perfis ativos, atualizada mensalmente por meio de um workflow dedicado.</p> <p>Para obter mais informações, consulte a <a href="../../platform/using/about-profiles.md#active-profiles">documentação detalhada</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> Aperfeiçoamento do Android Push Connector<br /> </td> 
   <td> <p>O conector Android foi aprimorado para oferecer suporte à taxa de transferência mais alta. </p> <p>Para obter mais informações, consulte a <a href="../../delivery/using/configuring-the-mobile-application.md">documentação detalhada</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Aprimoramentos de segurança**

* A expansão de entidades externas agora está desabilitada para impedir possíveis ataques de usuários não autenticados. (NEO-10173)
* Permissões mais rígidas para impedir que usuários padrão alterem os parâmetros de configuração da instância, como URLs de acesso a aplicativos, configurações LDAP etc. (NEO-10171)
* Correção de um problema que poderia revelar informações confidenciais por meio de rastreamentos em pilha. Os detalhes de erro estão agora registrados no back-end em um local de inacessível a partir da rede externa. (NEO-10176)
* Permissões mais rígidas para impedir que usuários padrão visualizem documentos carregados de um administrador e/ou pacotes exportados. (NEO-10170)

**Aprimoramentos**

* **LINE channel - architecture enhancement**: Como acontece com todos os outros canais do Adobe Campaign, o canal LINE agora é suportado em todos os tipos de implantação: hospedada, híbrida e no local.
* **Sequence auto-generation**: O mecanismo de geração de ID foi aprimorado para aumentar a vida útil das instâncias do Campaign com grande volume de objetos. Para obter mais informações, consulte esta [technote](https://helpx.adobe.com/br/campaign/kb/sequence_auto_generation.html).

**Outras alterações**

* Está disponível um novo modo de importação de pacotes usando a linha de comando que permite dependências circulares (não recomendado para pacotes grandes). Consulte a seção &quot;Evoluções técnicas&quot; abaixo para obter mais informações. (NEO-8979)
* Melhoria no desempenho para o carregamento de grande quantidade de dados no Teradata e a correção de um problema que impedia a exibição do valor correto de dados processados no log. (NEO-10429)
* Agora a importação de audiências do Audience Manager funciona com arquivos divididos. Anteriormente, somente o último arquivo do segmento era importado pelo workflow técnico importSharedAudience. (NEO-10156)
* No Windows, o caminho de instalação padrão do servidor do Campaign foi alterado. Ao iniciar a configuração da versão de 64 bits, o caminho de instalação padrão agora é: **C:Program Files\Adobe\Adobe Campaign Classic v7** em vez de **C:Program Files (x86)\Adobe\Adobe Campaign Classic v7**.
* As regras MX padrão foram aprimoradas para incluir mais domínios e otimizar a taxa de transferência.
* Restrições de acesso impostas na chamada SOAP do assistente de implantação (xtk:serverOptions#SaveOptions).
* A biblioteca weka.jar obsoleta foi removida e a biblioteca OpenSSL foi atualizada por causa de otimizações de segurança.
* Melhor workflow técnico de faturamento para proteger as performances das instâncias.
* A capacidade de os administradores definirem ou redefinirem a senha de qualquer operador foi restaurada. Para fazer isso, clique com o botão direito do mouse em um operador, selecione **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** e defina a nova senha do operador. Recomendamos que os operadores alterem sua senha ao se reconectarem pela primeira vez. Para obter mais informações, consulte a [documentação detalhada](../../production/using/lost-password.md).
* Para dar suporte ao novo recurso de multilocação no Adobe Target, um novo parâmetro “at_property” agora pode ser adicionado às URLs ao configurar as opções e as contas externas para a integração com o Target. O valor a ser usado para esse parâmetro pode ser encontrado no Adobe Target e será usado pelo Campaign ao realizar chamadas para o Target. Para obter mais informações, consulte a [documentação detalhada](../../integrations/using/inserting-a-dynamic-image.md).
* Agora é possível especificar uma landing page padrão para abrir ao clicar em uma imagem servida pelo Adobe Target. Antes, clicar naquela imagem levava à imagem padrão ao criar o email. Para obter mais informações, consulte a [documentação detalhada](../../integrations/using/inserting-a-dynamic-image.md).
* Adição da caixa de seleção **Enable SMPP traces** na conta externa para forçar registros de rastreamentos. Para obter mais informações, consulte a [documentação detalhada](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account).

**Evoluções técnicas**

queryDef

queryDef foi modificado em relação à cláusula &quot;orderBy&quot;. Antes da alteração, a chave primária da tabela consultada seria adicionada implicitamente às cláusulas &quot;orderBy&quot;. Em alguns mecanismos de banco de dados (postgresql pelo menos), impede o uso de índices (todos os campos da cláusula orderBy devem ser cobertos pelo mesmo índice). Se dependia desse comportamento, é necessário adicionar explicitamente a chave primária na sua cláusula &quot;orderBy&quot;.

Por exemplo, se tiver a seguinte query:

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

Ela seria entregue implicitamente como (antes das alterações do 18.4):

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitly added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

Função urlEncode

A função JavaScript &quot;urlEncode&quot; não estava funcionando corretamente com caracteres não ASCII. Ela foi corrigida e agora deve funcionar com todos os caracteres Unicode (incluindo caracteres japoneses). Se dependia do comportamento &quot;urlEncode&quot; para caracteres não ASCII, será necessário adaptar o código.

Novo modo de importação de pacote

Está disponível um novo modo de importação de pacotes usando a linha de comando que permite dependências circulares (não recomendado para pacotes grandes). A funcionalidade existente está mantida. Para esses pacotes com dependências circulares, um novo sinalizador **-usejs** foi adicionado à linha de comando importar pacote. Quando executado, ele usará o JSEngine como quando a importação de pacote é executada a partir da interface.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Correções**

* Correção de um problema de sincronização ao replicar logs de delivery e rastreamento do Adobe Campaign Standard para o Adobe Campaign Classic. (NEO-10023)
* Correção de um problema com o tratamento de tabelas de Erro e Log no Teradata quando um workflow ETL era retomando após uma falha em uma operação de carregamento rápido. As tabelas Erro e Log são excluídas corretamente cada vez que o workflow é retomado. (NEO-10672)
* Correção de um problema pós-atualização para instalar automaticamente o pacote Hive (necessário para o Hadoop) se o pacote FDA estiver instalado. (NEO-10592)
* Correção de um erro que tratava domínios inválidos como um erro **Não definido.** (NEO-10248)
* Correção de um problema que duplicava logs na tabela deliveryLogStats ao enviar deliveries por push no android. (NEO-10234)
* Correção de um problema que poderia levar a determinados formatos de código de barras não serem legíveis por scanners de código de barras. (NEO-10125)
* Correção de um problema com a função JavaScript &quot;urlEncode&quot; ao usar caracteres não ASCII. Consulte a seção &quot;Evoluções técnicas&quot; abaixo para obter mais informações. (NEO-10123)
* Correção de um problema ao executar uma query incluindo funções sha256 em bancos de dados Teradata. (NEO-10119)
* Correção de erros de memória de workflow que podem ocorrer na atividade SalesForce ao usar tabelas SalesForce muito grandes. (NEO-9900)
* Correção de um problema com a opção **Generate complement** nas atividades do workflow para criação de target ao usar FDA. (NEO-9878)
* Correção de um problema que poderia levar às métricas **Processed** e **Success** não serem atualizadas na instância de marketing ao usar mid-sourcing. (NEO-9454)
* Correção da interação de regras de não reproposição quando há mais de 10.000 ofertas no total na plataforma (NEO-9352)
* Correção de um problema que poderia impedir a especificação do target de um delivery ao usar um arquivo externo XML. (NEO-9312)
* Correção de um problema que poderia levar a erros de workflow ao executar uma hipótese em uma oferta e atualizar o status da proposta. (NEO-9304)
* Correção de erros que ocorriam durante a análise de delivery ao usar regras de pressão baseadas em um atributo do mapeamento de delivery no Android. (NEO-9202)
* Correção de um problema ao classificar em colunas na lista de recipientes que pode resultar em problemas de desempenho. Para obter mais informações sobre modificações &quot;queryDef&quot;, consulte a seção &quot;Technical evolutions&quot; abaixo. (NEO-9042)
* Correção de um problema em que os links em um email de aprovação poderiam apontar para uma URL de login incorreta, especialmente ao usar um tipo de login Federated ID. (NEO-9011)
* Correção de um problema que poderia resultar na exibição incorreta de datas nos seletores de data de relatórios em determinados fusos horários. (NEO-9007)
* Correção de um problema que impedia a exibição do target de uma saída ao usar um banco de dados SQL FDA. (NEO-8924)
* Correção de um problema que fazia com que o conector do MS Dynamics CRM não enviasse dados durante os primeiros 7 dias do mês. (NEO-8803)
* Correção de um erro com a integração do Analytics que impedia que os usuários incluíssem caracteres internacionais. (NEO-8719)
* Correção de um problema que poderia permitir a edição de workflow sem os direitos adequados. (NEO-8708)
* Correção de um problema com FDA sobre HTTPs ao usar o Centro de Mensagens em uma arquitetura híbrida, levando a queda de conexão ou perda de conexão (tempo limite). (NEO-8438)
* Erros de workflows fixos que ocorrem na atividade de query incremental para IDs negativas. (NEO-8229)
* Correção de um problema que poderia resultar na exibição de barras de rolagem duplas em determinadas telas. (NEO-8208)
* Correção de um problema que resultava na exibição de uma mensagem de erro ao executar o assistente de estrutura de banco de dados de atualização. O PostUpgrade executará uma renomeação de índices com nomes com mais de 30 caracteres. Esteja ciente de que para tabelas grandes, a substituição do índice levará tempo. (NEO-7983)
* Correção de um problema com logs de rastreamento não sendo sincronizados corretamente a partir da instância de execução do Centro de Mensagens para a instância de controle. (NEO-7286)
* Correção de um problema de desempenho com a atividade de enriquecimento da oferta. (NEO-7263)
* Correção de um problema que impedia a utilização da função DaysAgo ao realizar um query no banco de dados Redshift via FDA. (NEO-7099)
* Correção de uma regressão na gestão de dados que impedia a criação de índice em atividades de workflow de enriquecimento.
* Correção de um problema que poderia ocorrer ao criar recursos externos com o título @id
* Correção de um problema que poderia ocorrer ao carregar arquivos compactados por um servidor FTP ou ao carregar arquivos com caracteres curingas no nome do arquivo.
* Correção de um problema com enumerações de base longa em recursos personalizados externos criados no Campaign Standard.
* Correção de um problema que poderia resultar no envio de SMS mesmo quando a conexão com o provedor falhava, resultando em perdas no SMS.
* Correção de um erro que permita que uma conexão SMTP ficasse paralisada indefinidamente.
* Correção de um problema com regras de tipologia de pressão durante a preparação da mensagem ao usar um mapeamento LINE ou quando a filtragem e o target de schemas eram diferentes.
