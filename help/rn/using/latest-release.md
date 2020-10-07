---
title: Versão mais recente
description: Versão mais recente do Campaign Classic
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '2163'
ht-degree: 99%

---


# Versão mais recente{#latest-release}

![](assets/do-not-localize/cp-icon.png) **Nova versão de junho do Painel de controle do Campaign** com monitoramento de perfis ativos, auditoria de entregabilidade de subdomínio e gerenciamento de chaves GPG. [Saiba mais](https://docs.adobe.com/content/help/pt-BR/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/blue_2.png) Versão 20.2.3 - Build 9182 {#release-20-2-3-build-9182}

_11 de setembro de 2020_

* Correção de uma regressão que causava o bloqueio da preparação do delivery devido a uma única função incorreta na parte do delivery, resultando em sobrecarga da memória. (NEO-27346)



* Correção de um problema de pós-atualização que desativava o Apache e o servidor da web antes da republicação do aplicativo web. (NEO-27155)



* Correção de uma regressão no gerenciamento de modelos HTML que permitia a visibilidade de URLs de rastreamento devido a uma interpretação incorreta de guias. (NEO-25909)



* Correção de um problema com o workflow de limpeza do banco de dados que poderia falhar devido à fonte de dados não gerenciada. (NEO-23160, NEO-23364)
* O workflow de limpeza agora limpa listas expiradas por lotes de 100 em vez de uma a uma.
* Correção de uma regressão que impedia a modificação do nome interno de uma conta externa. (NEO-27323)



* Correção de uma regressão durante a pós-atualização, causando um início incorreto do nlserver (logs de erros).
* O gerenciamento de atualizações da memória compartilhada foi aprimorado. As etapas adicionais necessárias na versão 20.2 não são mais necessárias.

## ![](assets/do-not-localize/orange_2.png) Versão 20.2.2 - Build 9180 {#release-20-2-2-build-9180}

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
* Após a mudança para o [novo mecanismo de ID de sequência](https://helpx.adobe.com/br/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence), todos os aplicativos da web que estão atualizando a tabela do recipient são republicados durante a pós-atualização.
* Correção de uma possível vulnerabilidade XSS no conteúdo do delivery. (NEO-17987, NEO-26073)

## ![](assets/do-not-localize/orange_2.png) Versão 20.2.1 - Build 9178 {#release-20-2-1-build-9178}

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
    <p>O Azure Synapse só está disponível para ambientes híbridos e no local. Para obter mais informações, consulte a <a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">documentação detalhada</a>.</p>
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

* As mensagens transacionais foram aprimoradas para melhorar a experiência do usuário. Agora é possível desfazer a publicação de um template de mensagem transacional, o que o exclui das instâncias de execução. [Saiba mais](../../message-center/using/template-unpublication.md).

* Há novas opções disponíveis para definir limitações ao enviar emails com imagens ou anexos. Essas grades de proteção podem evitar problemas de desempenho, o que é particularmente útil com mensagens transacionais. [Leia mais](../../installation/using/configuring-campaign-options.md#delivery)

* A nova opção **Preparar as partes do delivery no banco de dados** possibilita executar a preparação do delivery diretamente no banco de dados, o que pode acelerar bastante a análise. Essa opção só está disponível para configurações específicas. [Saiba mais](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* O desempenho da [Atividade do conector de CRM](../../workflow/using/crm-connector.md) para Microsoft Dynamics foi aprimorado. (NEO-13303, NEO-12710)

* A versão da memória compartilhada foi aumentada.

   >[!WARNING]
   >
   >Essa melhoria requer uma etapa adicional após a execução da atualização. Consulte a seção **Evoluções técnicas** abaixo.

* O fluxo de trabalho de limpeza foi aprimorado. As tabelas de trabalho órfãs de todos os workflows excluídos agora também são excluídas automaticamente pelo fluxo de trabalho de limpeza. [Saiba mais](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Certificados para aplicativos móveis iOS com o conector HTTP2 do iOS agora são validados antes do envio de notificações por push, evitando que os deliveries falhem devido a certificados expirados.

* O gerenciamento de conexões proxy HTTP foi aprimorado. [Saiba mais](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**Outras alterações**

* Conectores SMS herdados agora estão obsoletos. Consulte a [página de recursos obsoletos](../../rn/using/deprecated-features.md).

* Você não pode mais usar sua própria conta Litmus para provisionar e usar a renderização da caixa de entrada no Adobe Campaign. [Saiba mais](../../delivery/using/inbox-rendering.md).

* Para distinguir melhor as visualizações das pastas, a cor dos nomes das visualizações foi alterada de azul escuro para ciano escuro. [Leia mais](../../platform/using/access-management.md#about-views)

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



