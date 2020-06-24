---
title: Versão mais recente
description: Versão mais recente
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b2cc71f8f9b7df80b1601a9fa55bfd77f9a82433
workflow-type: tm+mt
source-wordcount: '1765'
ht-degree: 15%

---


# Versão mais recente{#latest-release}

[Build upgrade](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html) | [Control Panel releases](https://docs.adobe.com/content/help/pt-BR/control-panel/using/release-notes.html) | [Documentation updates](../../rn/using/documentation-updates.md) | [Previous releases](../../rn/using/release--20-1.md) | [Deprecated features](../../rn/using/deprecated-features.md)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/do-not-localize/green3.png"/><strong>Disponibilidade geral</strong></td>
   <td><img src="assets/do-not-localize/blue3.png"/><strong>Candidato a lançamento</strong></td> 
   <td><img src="assets/do-not-localize/orange3.png"/><strong>Não está mais disponível</strong></td> 
   <td><img src="assets/do-not-localize/red3.png"/><strong>Obsoleto</strong></td> 
  </tr> 
   <tr> 
   <td>Compilação estável mais recente disponível. Compilação validada na produção.<br></td>
   <td>Compilação validada pela Adobe. Aguardando prova de produção.<br></td>
   <td>Versão mais recente disponível com correções de erros. Atualização necessária.<br></td>
   <td>Contém regressões conhecidas. A atualização é obrigatória.<br></td>
  </tr> 
 </tbody> 
</table>

A **última build estável** é a 9032 (3a9dc9c). Clique [aqui](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

![](assets/do-not-localize/cp-icon.png) **Nova versão** de junho do Painel de controle com monitoramento de perfis ativos, auditoria de entregabilidade de subdomínio e gerenciamento de chaves GPG. [Saiba mais](https://docs.adobe.com/content/help/pt-BR/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/blue_2.png) Versão 20.2.1 - Build 9178 {#release-20-2-1-build-9178}

_8 de junho de 2020_

**Novidades**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Suporte a Emoticons</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Ao projetar uma mensagem na Campanha, agora é possível inserir emoticons facilmente no corpo da mensagem, usando um botão dedicado. Eles também podem ser adicionados na linha de assunto do email. Você pode personalizar a lista de emoticons disponíveis na interface.</p>
    <p>Para obter mais informações sobre como adicionar emoticons, consulte a documentação <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons"></a>detalhada. Saiba como personalizar a lista de emoticon <a href="../../delivery/using/customizing-emoticon-list.md">nesta seção</a>.</p>
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
   <td> <p>Agora você pode conectar sua instância de Campanha ao banco de dados externo do Azure Synapse. Essa conexão é gerenciada por meio de uma nova conta externa.</p>
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
   <td> <p>O PDPA (Personal Data Protection Act) da Tailândia é a nova lei de privacidade que harmoniza e moderniza os requisitos de proteção de dados para a Tailândia. </p>
   <p>A Lei Geral de Dados (LGPD) do Brasil estará em vigor a partir de 16 de agosto para todas as empresas que coletam ou processam dados pessoais no Brasil.</p>
   <p>Esses regulamentos se aplicam a clientes Adobe Campaign que detêm dados para pessoas que residem nesses países. Além dos recursos de privacidade já disponíveis na Campanha (incluindo gerenciamento de consentimento, configurações de retenção de dados e funções de usuário), estamos aproveitando esta oportunidade para incluir recursos adicionais, para ajudar a facilitar sua prontidão para PDPA e LGPD:</p>
   <ul> 
     <li><p>Direito de acesso e direito de exclusão: estamos aproveitando as capacidades que foram adicionadas ao RGPD e CCPA. <a href="https://helpx.adobe.com/br/campaign/kb/acc-privacy.html">Leia mais</a></p></li> 
     <li> <p>Ao criar uma solicitação de privacidade usando interface de Campanha ou API, agora você seleciona o tipo de <strong>regulamento</strong> : PDPA, LGPD, GDPR, CCPA. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">Leia mais</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Aprimoramentos de segurança**

* A segurança aprimorada no rastreamento de links no email é ativada por padrão para todos os clientes. Um recurso de segurança adicional e aprimorado está disponível e pode ser ativado ao acessar o Atendimento ao cliente. Mais detalhes sobre o recurso e as etapas para clientes não hospedados para habilitá-lo podem ser encontrados na [lista de verificação de Segurança e Privacidade](https://helpx.adobe.com/br/campaign/kb/acc-security.html). (NEO-24232)

* Para otimizar a segurança, o algoritmo de hash MD5 usado para gerar nomes de arquivos foi reforçado com sha256 para upload de arquivos públicos. (NEO-17044)

* Para reforçar a segurança contra ataques XSS, os scripts do cliente são desativados ao executar um mirror page. (NEO-17987)

* Correção de um problema que impedia que o fluxo de trabalho técnico de Limpeza **de solicitação de** privacidade excluísse os dados de reconciliação. (NEO-25168, NEO-21004)

* Correção de um problema com a atividade **Transferência de Arquivo**, que impedia que a autenticação com a chave SFTP funcionasse no Debian 9. (NEO-23183)

**Aprimoramentos de compatibilidade**

Os seguintes sistemas agora são suportados com Campanha:
* Sistemas operacionais: Debian 10
* RDBMS: Oracle 18c e Oracle 19c
* FDA: Azure Synapse Analytics

Saiba mais na matriz de compatibilidade de [Campanha](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html).

**Aprimoramentos**

* As mensagens transacionais foram aprimoradas para uma melhor experiência do usuário. Agora é possível cancelar a publicação de um template de mensagem transacional, o que o exclui das instâncias de execução. [Saiba mais](../../message-center/using/template-unpublication.md).

* Novas opções estão disponíveis para definir limitações ao enviar emails que incluem imagens ou anexos. Esses painéis podem evitar problemas de desempenho, o que é particularmente útil com mensagens transacionais. [Leia mais](../../installation/using/configuring-campaign-options.md#delivery)

* A nova opção **Preparar as partes do delivery no banco de dados** permite executar a preparação do delivery diretamente no banco de dados, o que pode acelerar significativamente a análise. Essa opção só está disponível para configurações específicas. [Saiba mais](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* O desempenho da atividade [do Conector](../../workflow/using/crm-connector.md) CRM para Microsoft Dynamics foi aprimorado. (NEO-13303, NEO-12710)

* A versão da memória compartilhada foi aumentada.

   >[!WARNING]
   >
   >Essa melhoria requer uma etapa adicional após a execução da atualização. Consulte a seção **Evolução** técnica abaixo.

* O fluxo de trabalho de limpeza foi aprimorado. As tabelas de trabalho órfãs de todos os workflows excluídos agora também são excluídas automaticamente pelo fluxo de trabalho de limpeza. [Saiba mais](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Certificados para aplicativos móveis iOS com o conector HTTP2 do iOS agora são validados antes do envio de notificações por push, evitando que delivery falhem devido a certificados expirados.

* O gerenciamento de conexões proxy HTTP foi aprimorado. [Saiba mais](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**Outras alterações**

* Conectores SMS herdados agora estão obsoletos. Consulte a página [Recursos](../../rn/using/deprecated-features.md)obsoletos.

* Você não pode mais usar sua própria conta Litmus para provisionar e usar a renderização de Caixa de entrada no Adobe Campaign. [Saiba mais](../../delivery/using/inbox-rendering.md).

* Para distinguir melhor as visualizações das pastas, a cor dos nomes das visualizações foi alterada de azul escuro para ciano escuro. [Leia mais](../../platform/using/access-management.md#about-views)

* O Campaign Classic agora pode ser conectado a contas do Microsoft Dynamics CRM hospedadas nas regiões do Reino Unido, Índia e Canadá. Isso se aplica aos tipos de implantação do Office 365 e On premise (Dynamics 2015).

* A Campanha agora executa uma verificação TLS para verificar se o nome do host do servidor corresponde ao nome do host no certificado fornecido.

* A tabela de estatísticas de Delivery e rastreamento agora exibe uma entrada por delivery para o canal SMS, em vez de uma entrada por recipient de delivery.

* Adicionada uma mensagem de erro no arquivo de log para avisar os usuários quando o arquivo baixado for maior que o espaço em disco.

* As seguintes funções estão disponíveis para o conector Snowflake: Meses Atrás, Dias AgoInt, AtéDataHora, Anos Atrás.

**Evoluções técnicas**

Esta nova compilação atualiza a memória compartilhada e requer etapas adicionais para executar a atualização. Como administrador da Campanha, é necessário remover segmentos de memória. Essas etapas são obrigatórias, pois os segmentos antigos impedirão que nlserver/nlsrvmod seja iniciado.

No Windows, é necessário reiniciar o sistema.

No Debian/CentOs, a exclusão de memória compartilhada é necessária. Estas são as etapas:

Antes da atualização, você precisa seguir estas etapas:

1. Pare o serviço apache2 (http2 no CentOS) se ele estiver em execução.
1. Pare o serviço nlserver (nlserver6 para compilações mais antigas) se ele estiver em execução.

Após a atualização:

1. Remova a memória compartilhada usando o comando **ipcrm** , se a versão for anterior à versão atual.
1. Start o serviço nlserver se ele estava sendo executado.
1. Start o serviço apache2 se ele estivesse em execução.

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
* Correção de um problema que causava um erro ao atualizar vários workflows usando uma atividade de **Pesquisa** para processar com eficiência um número alto de workflows.
* Correção de um problema intermitente de conectividade durante o processamento de mensagens do InMail do MTA aprimorado. (NEO-20380)
* Correção de um problema que impedia que as porcentagens de cliques ativos fossem exibidas corretamente quando as imagens eram exibidas com 100% de largura no HTML. (NEO-23203)
* Correção de um problema que impedia que o conteúdo condicional do delivery fosse totalmente exibido no relatório de cliques em funcionamento. (NEO-18729)
* Correção de um problema que ignorava a etapa de aprovação do público alvo ao retomar um fluxo de trabalho para enviar um delivery recorrente. (NEO-18166)
* Correção de um problema que impedia que o botão de preparação **da mensagem de** Reiniciar retomasse o delivery após corrigir um erro no fluxo de trabalho. (NEO-13488)
* Correção de um problema que resultava em falha de delivery durante a fase de rampa, onde o público alvo incluía recipient com formatos do email japoneses. (NEO-23846)
* Correção de um problema de conversão de fuso horário com o Conector Snowflake (NEO-20105)
* Correção de um problema com a conta externa que usa o FTP sobre SSL. (NEO-20498)
* Correção de um problema que impedia a exibição de imagens em delivery de linha. (NEO-23207)
* Correção de um problema que causava um erro ao publicar uma oferta. (NEO-23312)
* Correção de um problema com notificações por push que permitiam que conexões de teste funcionassem em aplicativos móveis, mesmo quando o certificado expirava. (NEO-22991)
* Correção de um problema que poderia afetar as notificações por push quando enviadas com alta frequência. (NEO-20516)
* Correção de um problema que fazia com que os dados de rastreamento incluíssem duplicados, mesmo que os logs de rastreamento não incluíssem. (NEO-20040)
* Correção de um problema que fazia com que emails transacionais de duplicado fossem enviados após uma falha de comunicação do servidor de rastreamento ser corrigida. (NEO-23640)
* Correção de um problema que excluía o valor do parâmetro de codificação ao redirecionar de um URL de rastreamento. (NEO-25637)
* Correção de um problema que impedia que um query funcionasse ao comparar números flutuantes. (NEO-23243)
* Correção de um problema que impedia a exibição do conteúdo da coluna **Modificado por** pelo após reiniciar um fluxo de trabalho. (NEO-23035)
* Correção de um problema que causava a falha do fluxo de trabalho técnico de rastreamento ao baixar registros de um segundo container. (NEO-23159)
* Correção de um problema que resultava em falha de workflows ao executar uma atividade de **Enriquecimento** . (NEO-17338)
* Uma verificação foi adicionada aos **Duplos para manter** o campo na atividade de fluxo de trabalho **Desduplicação-duplicada** para evitar a inserção de valores nulos ou negativos.
* Removido o assistente **de** Scheduleres das campanhas recorrentes para evitar mencionar horas e minutos. Só são consideradas datas.
* Correção de um problema com campos de armazenamento adicionais ao criar delivery por meio da opção **Calculado por um script** na atividade do fluxo de trabalho **Script** . (NEO-20609)
* Correção de um problema que impedia que workflows fantasmas fossem excluídos nas tarefas de limpeza do banco de dados.
* Correção de um problema que causava a falha do fluxo de trabalho técnico **Faturamento (perfis ativos)** . (NEO-19777)
* Correção de um problema ao testar a conexão da conta externa acsDefaultAccount. (NEO-23433)
* Correção de um problema que impedia a criação de uma extensão de schema em uma chave primária com várias colunas com uma tabela Hadoop. (NEO-17390)
* Correção de um problema na atividade **Loading (SOAP)** que poderia impedir que arquivos WSDL fossem carregados de um URL. (NEO-16924)
* Correção de um problema que impedia a execução de uma parada **** incondicional pelo console quando vários servidores de fluxo de trabalho ativos eram balanceados de carga. (NEO-19556)
* Correção de uma regressão que resulta em falha do workflow de limpeza.
* Correção de um problema que ocorria ao publicar um modelo em uma instância de execução.
* Correção de um problema que poderia impedir a execução do fluxo de trabalho técnico collectPrivacyRequests. (NEO-20513, NEO-25169)
* Correção de problemas que ocorriam ao tentar se conectar ao Audience Manager após a atualização para a compilação 9080. (NEO-20511, NEO-25167)
* Correção de problemas que podem ocorrer ao exportar relatórios no formato PDF ou XLS. (NEO-20982, NEO-23493, NEO-23348)
* Correção de um problema que podia exibir um delivery duas vezes na lista do delivery depois de ele ser enviado.
* Correção de um problema com a preparação do delivery que ocorria quando a configuração do roteamento era definida para enviar o delivery via mid-sourcing.
* Correção de um problema que podia exibir uma mensagem de erro ao clicar em um link de aplicativo da Web em uma mensagem de Linha.
* Correção de um problema que impedia o Microsoft Dynamics CRM de recuperar todas as entidades. (NEO-24528)
* Correção de um problema que excluía o histórico de atividades de **Query incrementais** após a execução do fluxo de trabalho de limpeza.
* Correção de um problema ao criar uma conta externa de mid-sourcing em que a opção NmsMidSourcing_LastBroadLog_&lt;InternalName> estava ausente
