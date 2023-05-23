---
product: campaign
title: Versões do Campaign Classic 2019
description: Saiba mais sobre as atualizações do Campaign Classic 2019
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hidefromtoc: true
exl-id: 8a36a542-e095-4208-b624-e59845592863
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '4825'
ht-degree: 98%

---

# Versões de 2019{#release-2019}



## Versão 19.2{#release-19-2}

### ![](assets/do-not-localize/limited_2.png) Versão 19.2.4 - Build 9082 {#release-19-2-4-build-9082}

_15 de abril de 2021_

* Correção de uma regressão do console do cliente que causava mensagens de erro persistentes na tela de conexão IMS. (NEO-34821)

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!NOTE]
>
> Conecte-se à [Distribuição de software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html) para baixar a nova versão. Saiba como propor a atualização do console para todos os usuários finais [nesta página](../../installation/using/client-console-availability-for-windows.md).

_22 de março de 2021_

* Correção de uma regressão que impedia o uso de alguns componentes do console, como o seletor de datas e o gerenciamento de imagens nos deliveries. (NEO-31453, NEO-31454)

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!NOTE]
>
> Conecte-se à [Distribuição de software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html) para baixar a nova versão. Saiba como propor a atualização do console para todos os usuários finais [nesta página](../../installation/using/client-console-availability-for-windows.md).

_23 de dezembro de 2020_

>[!CAUTION]
>
> * Esta versão é fornecida com um novo protocolo de conexão: se você estiver se conectando ao Campaign pelo Serviço de identidade da Adobe (IMS), a atualização será obrigatória para o servidor do Campaign e o console do cliente poderem se conectar ao Campaign após **30 de junho de 2021**. [Saiba mais](../../technotes/using/ims-updates.md)
>
> * Esta versão vem com uma [correção de segurança](https://helpx.adobe.com/br/security/products/campaign/apsb21-04.html): a atualização é obrigatória para reforçar a segurança do ambiente.



* O protocolo de conexão foi atualizado para seguir o novo mecanismo de autenticação IMS.
* Correção de um problema de segurança para reforçar a proteção contra situações de SSRF (Server Side Request Forgery). (NEO-27777)




### ![](assets/do-not-localize/red_2.png) Versão 19.2.3 - Build 9081 {#release-19-2-3-build-9081}

_7 de fevereiro de 2020_

**Aprimoramentos**

* Correção de um problema de regressão devido à implementação da certificação SSL que causava a falha da conexão do usuário no servidor Windows. (NEO-20629)
* Correção de um problema que exibia um número de tag de versão incorreto no menu **About**.


### ![](assets/do-not-localize/red_2.png) Versão 19.2 - Build 9080 {#release-19-2-build-9080}

_2 de dezembro de 2019_

**Novidades**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>O CCPA é a nova lei de privacidade do estado da Califórnia que concilia e moderniza os requisitos de proteção de dados que entrou em vigor em 01 de janeiro de 2020. O CCPA se aplica aos clientes do Adobe Campaign que coletam dados de residentes da Califórnia.</p>
    <p> Além dos recursos de privacidade já disponíveis (incluindo gerenciamento de consentimento, configurações de retenção de dados e funções de usuário), o Adobe Campaign ajuda a facilitar a preparação para o CCPA:</p>
    <ul>
      <li>Direito de acesso e direito de exclusão: estamos nos beneficiando dos recursos que foram adicionadas ao GDPR. <a href="https://helpx.adobe.com/br/campaign/kb/acc-privacy.html#righttoaccess">Leia mais</a></li>
      <li>Você pode acompanhar se um consumidor optou por não participar da venda de informações pessoais. Para isso, é necessário estender a tabela Perfis e adicionar um campo <strong>Opt-Out for CCPA</strong> . <a href="https://helpx.adobe.com/br/campaign/kb/acc-privacy.html#ccpa">Leia mais</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Monitoramento ao vivo do workflow</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Agora você pode monitorar o status de execução de todos os workflows na sua instância usando exibições predefinidas.</p>
   <p>Para obter mais informações, consulte a <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">documentação detalhada</a>.</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Conteúdo interativo com AMP</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>O Adobe Campaign permite que você experimente o novo formato do <a href="https://amp.dev/about/email/">AMP for Email</a>, que permite que os profissionais de marketing incluam componentes do AMP dentro de mensagens para aprimorar a experiência de email com conteúdo avançado, dinâmico e interativo, acionável diretamente na própria mensagem.</p>
   <p> Esse recurso foi lançado como um beta público.</p>
   <p>Para obter mais informações, consulte a <a href="../../delivery/using/defining-interactive-content.md">documentação detalhada</a> e o <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">vídeo tutorial</a>.</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Sistema de Mensagens Seguras de SMS (TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>O SMS Seguro agora é suportado pelo Conector SMPP Genérico Estendido. Isto permite uma conexão codificada com o provedor.</p> <p><strong>Aviso</strong> Este recurso requer um certificado atualizado em todos os servidores. Certificados inválidos, revogados ou expirados gerarão erros que afetam os recursos gerais de envio de SMS.</p><p>Para obter mais informações, consulte a <a href="https://helpx.adobe.com/br/campaign/kb/sms-connector-protocol-and-settings.html">documentação detalhada</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Aprimoramentos de segurança**

* Corrigidas as vulnerabilidades de script entre sites armazenadas na interface do Campaign - validação de dados de entrada e codificação de saída. (NEO-16810)
* Correção de um problema de segurança na autorização de perfil que poderia permitir o acesso a dados não autorizados, reforçando a política de restrição de login. (NEO-14445)

**Aprimoramentos**

* Otimização do consumo de memória para notificações por push.
* Para otimização de desempenho e armazenamento, a manipulação do arquivo **logins.log** foi aprimorada. O arquivo agora é dividido em vários arquivos, um a cada dia com um máximo de 365 arquivos retidos. [Leia mais](../../production/using/log-files.md)
* A conta externa do Microsoft Dynamics CRM agora pode ser configurada usando credenciais de senha (senha + nome de usuário) ou certificado (chave privada). [Leia mais](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Alguns aprimoramentos foram adicionados ao conector Hadoop FDA para melhorar a confiabilidade
* Foi adicionada uma medida de proteção específica para verificar o espaço em disco antes de permitir o upload de recursos públicos no servidor.
* Novas [Opções de campanha](../../installation/using/configuring-campaign-options.md) foram adicionadas:
   * A opção de configuração **WdbcKillSessionPolicy** permite que você afete o comportamento de **Unconditional Stop** em todos os workflows e consultas de banco de dados PostgreSQL.
   * A opção **NmsOperation_DeliveryPreparationWindow** permite definir o número de dias nos quais os deliveries com status inconsistente serão excluídos da contagem de entregas em execução.
   * A opção **WdbcOptions_TempDbName** permite configurar um banco de dados separado para tabelas de trabalho no Microsoft SQL Server. Isso otimiza os backups e a replicação. [Leia mais](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * A opção **XtkCleanup_NoStats** foi aprimorada para PostgreSQL para controlar melhor o comportamento da etapa de otimização de armazenamento do workflow de limpeza do banco de dados. [Leia mais](../../production/using/database-cleanup-workflow.md#statistics-update)
* Um mecanismo de bloqueio de conta foi adicionado à API **logon()**. Impede novas tentativas de login após um certo número de tentativas com falha consecutivas em um período especificado.
* Uma nova opção **Maximum personalization run time** nas propriedades de delivery permite definir um período de tempo limite para o tempo de execução de personalização, a fim de evitar que a fase de personalização seja executada por muito tempo. [Leia mais](../../delivery/using/personalization-fields.md#timing-out-personalization)
* A opção **ftp protocol** foi adicionada para permitir que você use uma configuração proxy para conexões SFTP. [Leia mais](../../installation/using/file-res-management.md)
* Novo suporte de acesso proxy a um servidor externo SFTP para ambientes locais.
* Foi adicionada uma medida de proteção específica para impedir a instalação de pacotes que não são compatíveis com a instância do Campaign. [Leia mais](../../installation/using/installing-campaign-standard-packages.md)

_Sistemas obsoletos_

Os seguintes sistemas foram [descontinuados](deprecated-features.md) para implementações do Campaign Classic:
* Apache 2.2
* Centos 6

Verifique se você está usando as versões compatíveis de qualquer sistema listado na matriz mais recente de compatibilidade de campanhas. [Leia mais](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

_SDK do Campaign Mobile_

A build 1.0.26 do SDK do iOS está disponível. Nesta nova build, adicionamos o suporte do iOS 13. Esta nova versão agora é compatível com a prioridade de notificação e o novo processo de gerenciamento de token de registro para notificações por push do iOS 13. Se você estiver executando aplicativos em uma versão anterior do SDK, será necessário recompilar seus aplicativos com o novo SDK. Para obter o SDK, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Correções**

* Correção de um problema de falha quando o campo **Adicionar tabela vinculada** ficava vazio na atividade de workflow **Carregamento de dados (RDBMS)**. (NEO-12213)
* Correção de um problema que resultava no não processamento de determinadas mensagens pelo servidor de Mid-Sourcing. (NEO-12395)
* Correção de um problema no workflow de limpeza do banco de dados ao usar a opção de faixas de query com Teradata. (NEO-12399)
* Correção de um problema que afetava a análise de delivery com a regra de tipologia incluindo o domínio ne.jp. (NEO-12609)
* Correção de um problema relacionado a atualizações de SMS sobre TLS que implicavam uma política de certificados mais restritiva. Essas atualizações poderiam causar uma falha de conexão entre servidores de marketing e de mid-sourcing no caso de um certificado desatualizado. (NEO-17698)
* Correção de um problema ao usar o botão **Test connection** em uma conta externa em um ambiente de mid-sourcing com autenticação Vault. (NEO-12722)
* Correção de um problema em queries que usavam funções de data com uma conexão FDA Hadoop. (NEO-12847)
* Correção de um problema ao substituir uma imagem no editor de e-mail. (NEO-13098)
* Correção de um problema que resultava em erros de pós-atualização em pastas que tinham sido excluídas ou movidas para outro local. (NEO-13118)
* Correção de um problema na exibição da imagem ao usar a opção **Define image per device screen size** nas mensagens LINE. (NEO-13228)
* Correção de um problema de preparação de delivery quando a opção **Exclude duplicate address during delivery** não está selecionada. (NEO-13240)
* Correção de um problema nos workflows ao usar a atividade **File transfer** para baixar arquivos usando a opção **Delete the source files after transfer** com um nome que contém um caractere de espaço. (NEO-13411)
* Correção de um problema com a limpeza do cache Tomcat, que poderia causar problemas de memória. (NEO-13456)
* Correção de um problema ao instalar o pacote integrado **Controle do mecanismo de oferta com o módulo de instância de execução** em uma instância de controle existente em execução no Microsoft SQL 2017. (NEO-13539)
* Correção de um problema de travamento do console que poderia ocorrer ao desmarcar URLs rastreados em um email, na guia **Conteúdo de texto** devido a uma variável não inicializada. (NEO-13545)
* Correção de um problema de codificação no nome do remetente chinês. (NEO-13837)
* Correção de um erro que poderia ocorrer ao exibir dados de resposta da pesquisa no Explorer. (NEO-14590)
* Correção de um problema que poderia causar discrepância entre a classificação do log de delivery e a tabela de quarentena. (NEO-16547)
* Correção de um problema com chaves DKIM que não eram incorporadas a emails. (NEO-16804)
* Correção de um problema que exibia o código de erro incorreto quando um token de sessão inválido era usado no contexto de chamadas API para acionar eventos. O código de erro era &#39;HTTP 200 OK&#39; em vez de &#39;HTTP 403 Forbidden&#39;. (NEO-16826)
* Correção de um problema ao exibir relatórios de delivery via acesso à Web. (NEO-17015)
* Correção de um problema de autenticação IMS ao fazer logon no Adobe Campaign. (NEO-17312)
* Correção de um problema que impedia que emails em quarentena fossem excluídos pelo processo de Gerenciamento de privacidade. (NEO-17314)
* Correção de problemas de taxa de transferência após a atualização para o 9031 com o banco de dados SQL. (NEO-17558)
* Correção de um problema que afetava o CRM Connector com Salesforce. (NEO-17712)
* Correção de um problema de tempo limite ao importar dados de um SFTP externo. (NEO-19723)
* Correção de um problema ao acessar modelos preditivos. (NEO-19713)
* Correção de um problema que afetava a amostragem aleatória na atividade **Split** do workflow com o banco de dados FDA do Hadoop. (NEO-16636)
* Correção de uma regressão no Oracle que resultava em algumas funções consideradas inválidas após a atualização. (NEO-12759)





## Versão 19.1{#release-19-1}

### ![](assets/do-not-localize/limited_2.png) Versão 19.1.8 - Build 9039 {#release-19-1-8-build-9039}

_15 de abril de 2021_

* Correção de uma regressão do console do cliente que causava mensagens de erro persistentes na tela de conexão IMS. (NEO-34821)
* Correção de uma regressão que poderia bloquear a exportação de dados do workflow para um banco de dados FDA (Teradata, Snowflake).

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!NOTE]
>
> Conecte-se à [Distribuição de software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html) para baixar a nova versão. Saiba como propor a atualização do console para todos os usuários finais [nesta página](../../installation/using/client-console-availability-for-windows.md).

_22 de março de 2021_

* Correção de uma regressão que impedia o uso de alguns componentes do console, como o seletor de datas e o gerenciamento de imagens nos deliveries. (NEO-31453, NEO-31454)

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!NOTE]
>
> Conecte-se à [Distribuição de software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html) para baixar a nova versão. Saiba como propor a atualização do console para todos os usuários finais [nesta página](../../installation/using/client-console-availability-for-windows.md).

_16 de dezembro de 2020_

>[!CAUTION]
>
> * Esta versão é fornecida com um novo protocolo de conexão: se você estiver se conectando ao Campaign pelo Serviço de identidade da Adobe (IMS), a atualização será obrigatória para o servidor do Campaign e o console do cliente poderem se conectar ao Campaign após **30 de junho de 2021**. [Saiba mais](../../technotes/using/ims-updates.md)
> * Esta versão vem com uma [correção de segurança](https://helpx.adobe.com/br/security/products/campaign/apsb21-04.html): a atualização é obrigatória para reforçar a segurança do ambiente.
> * Se você estiver usando a integração do Experience Cloud Triggers por meio da autenticação oAuth, será necessário migrar para o Adobe I/O de acordo com as instruções [nesta página](../../integrations/using/configuring-adobe-io.md). O modo de autenticação oAuth herdado do Campaign [foi removido](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) em **setembro de 2021**. Os ambientes hospedados se beneficiarão de uma extensão até **23 de fevereiro de 2022**. Como cliente no local ou híbrido, entre em contato com o Atendimento ao cliente da Adobe para estender o suporte até fevereiro de 2022. Você deve fornecer [o AppID do aplicativo OAuth](../../integrations/using/configuring-pipeline.md#step-optional) para a Adobe.



**Aprimoramentos**

* O protocolo de conexão foi atualizado para seguir o novo mecanismo de autenticação IMS.
* A autenticação da integração dos acionadores originalmente baseada na configuração da autenticação oAUTH para acessar o pipeline agora foi alterada e movida para o Adobe I/O. [Saiba mais](../../integrations/using/configuring-adobe-io.md)
* Após o fim do suporte para o protocolo binário herdado APNs do iOS, todas as instâncias que usam esse protocolo são atualizadas para o protocolo HTTP/2 durante a pós-atualização.
* Correção de um problema de segurança para reforçar a proteção contra situações de SSRF (Server Side Request Forgery). (NEO-27777)



* Correção de um problema que resultava na desativação do conector SMPP após um erro de conexão, impedindo o envio de outros deliveries SMS e causando problemas de desempenho.
* Correção de um problema que exibe porcentagens incorretas ao gerar um relatório descritivo por meio de uma atividade de workflow. (NEO-14314)
* Correção de um problema de preparação de delivery quando a opção **Excluir endereço duplicado durante delivery** não está selecionada. (NEO-13240)
* Correção de um problema que resultava em falha em fluxos de trabalho ao executar uma atividade de **Enriquecimento**. (NEO-17338)
* Correção de um problema em workflows ao buscar registros de um banco de dados externo e inseri-los no banco de dados do Campaign. (NEO-26359)



* Correção de um problema de falha do servidor, impedindo assim a corrupção da memória ao limpar o analisador de expressão.
* Correção de um problema que impedia que a função **NoNull** funcionasse em bancos de dados Oracle após a atualização para a build 9032. (NEO-26488)



* Correção de um problema ao editar uma descrição de template de campanha que impedia a exibição do botão **Salvar** ao copiar símbolos de colagem, como por exemplo, caracteres japoneses. (NEO-27071)



* Correção de um problema que impedia que a descrição de uma campanha ou template de campanha fosse salva ao clicar fora da janela antes de clicar no botão **Salvar**. (NEO-27449)



* Correção de um problema no nível de configuração de proxy que impedia o logon no Adobe Campaign após a atualização mais recente do Windows 10. (NEO-27813)



* Correção de um problema relacionado ao gerenciamento de linhas vazias em arquivos de registro, que causava falhas no comportamento do processo MTA e resultava em quedas de desempenho no envio de delivery.

**Evoluções técnicas**

O Tomcat foi atualizado da versão 7 (7.0.103) para a versão 8 (8.5.57). O diretório `tomcat-7` é substituído por um diretório `tomcat-8`. No Windows, _iis_neolane_setup.vbs_ e _apache_neolane.conf_ agora estão instalados no diretório `conf` (em vez do `tomcat-7/conf` anterior). No linux, _apache_neolane.conf_ agora está instalado no diretório `conf`.

No Linux, a inicialização do serviço nlserver agora usa uma unidade sistêmica em vez do script /etc/init.d/nlserver6. A migração para o novo esquema de inicialização é executada automaticamente ao instalar o pacote 19.1.8. O /etc/init.d/nlserver6 ainda é fornecido, mas para interagir com o serviço nlserver (start, reinicialização, interrupção etc.), recomendamos que você use o comando systemctl diretamente.


### ![](assets/do-not-localize/red_2.png) Versão 19.1.7 - Build 9036 {#release-19-1-7-build-9036}

_15 de setembro de 2020_

**Aprimoramentos**

* O uso de nlsrvmod para o thread do Apache 2.4 foi aprimorado para corrigir falhas de nlsrvmod.
* Correção de um problema ao usar a atividade de transferência de arquivos com uma conta externa do Azure e uma criptografia SSL. A conexão foi executada por HTTP em vez de HTTPS. (NEO-26720)



* Correção de um problema com o mecanismo de cache de url que não recuperava o rótulo ou a categoria.
* Correção de um problema que resultava na definição incorreta de URLs de mirror page em delivery de email (devido ao controle de caracteres ASCII incorreto). (NEO-26084)
* A lista jarsToSkip em catalina.properties foi atualizada para remover a referência a um arquivo jar que não é mais utilizado (notificações do iOS).
* Correção de um problema de regressão após a publicação após a atualização.
* Correção de um problema de regressão com relatórios do delivery de utilização imediata que apareciam cortados quando exportados para PDF. (NEO-25757)
* Correção de um problema que excluía o valor do parâmetro de codificação ao redirecionar a partir de um URL de rastreamento (impacto nos caracteres japoneses). (NEO-25637)
* Correção de um problema que resultava no bloqueio de links não assinados de domínios personalizados quando deveriam ser permitidos. (NEO-25210)
* Correção de uma regressão que afetava os campos calculados em um workflow, causando falha no workflow. (NEO-25194)
* Correção de um problema de compatibilidade com o Microsoft Dynamics (da versão 8.2) que poderia impedir a execução de algumas chamadas de API (RetrieveAllEntities). (NEO-24528)
* Correção de um problema de regressão ao usar o recurso Conector de ACS que impedia a conexão com uma instância do Campaign Standard (gerenciamento incorreto da conexão FOH/FOH2). (NEO-23433)
* Correção de um problema de regressão na conexão do banco de dados, provocando a reinicialização constante do servidor da web devido a um problema de codificação do banco de dados. As reinicializações poderiam causar um consumo excessivo. (NEO-23264)



* Correção de um problema com o workflow de limpeza do banco de dados que poderia falhar devido à fonte de dados não gerenciada. (NEO-23160, NEO-23364)
* O workflow de limpeza agora limpa listas expiradas por lotes de 100 em vez de uma a uma.
* Após a mudança para o novo mecanismo de ID de sequência, todos os aplicativos da web que estão atualizando a tabela do recipient são republicados durante a pós-atualização.
* Correção de um problema que impedia o envio de emails quando um código Javascript estivesse fora da tag de conteúdo HTML. (NEO-18628)
* Correção de um problema que impede a atualização dos indicadores de rastreamento de mensagens transacionais pelo workflow Tracking. (NEO-17770)
* O desempenho do assistente de atualização de banco de dados foi aprimorado para realizar menos declarações SQL a fim de otimizar o tempo de resposta.
* Correção de um problema de travamento do console que poderia ocorrer ao desmarcar URLs rastreados em um email, na guia **Conteúdo de texto** devido a uma variável não inicializada. (NEO-13545)
* Correção de um problema que impedia o upload de arquivos em uma atividade de transferência de arquivos usando uma conta externa do Armazenamento Blob do Azure devido a uma variável não inicializada (m_pCurlReader). (NEO-13717)



* Correção de um problema de pós-atualização que desativava o Apache e o servidor da web antes da republicação do aplicativo web. (NEO-27155)



* Correção de uma regressão que resultava na escolha incorreta de um fuso horário na configuração de horário em uma atividade de workflow de **Scheduler**.


### ![](assets/do-not-localize/red_2.png) Versão 19.1.6 - Build 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Esta build destina-se apenas a instalações locais. Para implantações híbridas, as instâncias hospedadas continuarão executando a build 9032. Não atualize a instância de marketing para a build 9035, pois ela não é compatível com a 9032.

_3 de outubro de 2019_

**Aprimoramentos**

* Correção de um problema ao usar o Conector CRM para Salesforce. (NEO-17712)
* Correção de um problema de índice que causava problemas de desempenho ao enviar mensagens transacionais.
* Correção de um problema de desempenho ao enviar mensagens. (NEO-17558)
* Correção de um problema que resultava no não processamento de determinadas mensagens pelo servidor de Mid-Sourcing. (NEO-12395)
* Correção de um problema que impedia o uso total da atividade do SQL Data Management (o direito nomeado do &quot;SQL Data Management&quot; estava ausente).

### ![](assets/do-not-localize/red_2.png) Versão 19.1.5 - Build 9033{#release-19-1-5-build-9033}

_13 de agosto de 2019_

**Aprimoramentos**

* Correção de um problema com a declaração &#39;SELECT COUNT&#39; do SQL, que foi executada no banco de dados padrão em vez de no banco de dados FDA durante a extração de dados na atividade do Gerenciamento de dados.
* Para aprimora os recursos de infraestrutura do cliente, uma declaração de proxy SFTP agora está disponível no arquivo de configuração do servidor.
* Correção de um problema de falha quando o campo **Adicionar tabela vinculada** ficava vazio na atividade de workflow **Carregamento de dados (RDBMS)**. (NEO-12213)
* Correção de um problema com a instalação do pacote midEmitter por meio da linha de comando.
* Adição de uma nova opção de autenticação para oferecer suporte às credenciais do OAuth no conector AC com o Microsoft Dynamics.(NEO-11982)
* Correção de um problema com o gerenciamento UUID (identificador universal exclusivo) que resultava em falha das atividades do workflow de carregamento de query e dados com o FDA Hive.
* Correção de uma regressão no Oracle que resultava em algumas funções consideradas inválidas após a atualização. (NEO-12759)



* Correção de uma regressão que resultava na escolha incorreta de um fuso horário na configuração de horário em uma atividade do workflow do Scheduler.

### ![](assets/do-not-localize/green_2.png) Versão 19.1.4 – Build 9032{#release-19-1-4-build-9032}


>[!NOTE]
>
>19.1.4 [!DNL Gold Standard] as versões estão listadas neste [página](../../rn/using/gold-standard.md).


### ![](assets/do-not-localize/red_2.png) Versão 19.1.2 - Build 9029{#release-19-1-2-build-9029}

_21 de junho de 2019_

**Aprimoramentos de segurança**

* Para otimizar a segurança, a biblioteca do Java (Netty) foi atualizada para a versão mais recente (4.1.34). (NEO-12788)

**Aprimoramentos**

* Correção de uma regressão relacionada ao gerenciamento de coluna sdomain que impedia que os emails fossem enviados em determinadas configurações.
* Para aprimorar o desempenho, um atributo _operation=&quot;none&quot; foi adicionado a chamadas rtEvent SOAP para evitar solicitações &quot;SELECIONE PARA ATUALIZAR&quot;.
* Correção de um problema de exibição do workflow com transições de saída após uma atividade Test. (NEO-12727)
* Agora permitimos a exclusão de registros fictícios criados no Microsoft Dynamics durante o fluxo de trabalho de importação.
* Permissões aprimoradas para executar o pacote de zona de segurança ao usar a conta interna.


### ![](assets/do-not-localize/red_2.png) Versão 19.1 - Build 9026{#release-19-1-build-9026}

_30 de maio de 2019_

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
   <td> Painel de controle<br /> </td> 
   <td> <p>Para aumentar a eficiência em seu trabalho como usuário administrador, gerencie as configurações dos servidores SFTP monitorando o armazenamento, inclua endereços IP à lista de permissões e instale chaves SSH para cada instância. Observe que o Painel de Controle está disponível apenas para clientes hospedados no AWS a partir de hoje (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">login através da Experience Cloud hoje</a>).</p> <p>Para obter mais informações, consulte a <a href="https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR">documentação detalhada</a> e o <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/control-panel-overview.html?lang=pt-BR">vídeo de instruções</a>. </p><p>Observação: não é necessário atualizar para a build mais recente do Campaign para acessar o Painel de Controle.</p> </td> 
  </tr> 
    <tr> 
   <td> Trilha de auditoria<br /> </td> 
   <td> <p>Como administrador, aumente a produtividade monitorando e gerenciando alterações feitas na instância do Adobe Campaign Classic. A Trilha de Auditoria registrará ações feitas nos Schemas de origem, Workflows e Opções. Você pode ver rapidamente se um elemento foi criado, modificado ou excluído.</p><p>Para obter mais informações, consulte a <a href="../../production/using/audit-trail.md">documentação detalhada</a> e o <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/monitoring/audit-trail.html">vídeo de instruções</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Medidas de proteção, robustez e escalabilidade<br /> </td> 
   <td> Uma série de melhorias foi adicionada ao Campaign Classic. As melhorias em medidas de proteção, robustez e escalabilidade estão listadas abaixo.<br /> </td> 
  </tr> 
  <tr> 
   <td> Atualização da Matriz de Compatibilidade<br /> </td> 
   <td> Com essa nova versão, o Adobe Campaign agora oferece suporte aos seguintes sistemas de banco de dados. Consulte a <a href="https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html">Matriz de Compatibilidade</a>.<br /> 
    <ul> 
     <li> <p>Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7 (FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16 (FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Aprimoramentos de segurança**

* Por motivos de segurança, não é mais possível inserir comandos arbitrários ao usar a opção **[!UICONTROL Pre-process the file]** em uma atividade de workflow **[!UICONTROL Data loading (file)]**. Uma lista suspensa está disponível e permite selecionar entre 3 opções: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) ou **[!UICONTROL Decrypt]** (gpg). O sinalizador de segurança XtkSecurity_Disable_Preproc foi adicionado. Para novos clientes, essa opção será definida como 0. Para clientes existentes, essa opção será definida como 1 pelo postupgrade para manter o comportamento anterior. Consulte esta [seção](../../workflow/using/data-loading--file-.md).
* Correção de um problema de visibilidade de senha que ocorria ao testar a conexão de uma conta externa FDA sem fuso horário definido.
* A biblioteca PDFBox foi removida.
* O Tomcat foi atualizado para a versão 7.0.93.
* Correção de um problema de visibilidade de token que ocorria quando o token de segurança era inválido.
* Correção de um problema potencial de injeção de XTK no WSDL JSP (schemawsdl.jsp).
* O armazenamento de credenciais e senhas no código-fonte e na memória do aplicativo foi otimizado.
* A restrição de visualização de PII foi otimizada. (NEO-12339, NEO-12396, NEO-12398, NEO-12339, NEO-12667)
* Correção de problemas de inconsistência no gerenciamento de chaves secretas.
* O mesmo erro genérico é exibido agora para tentativas falhas de logon com um nome de usuário válido ou inválido.
* A nomeação de arquivos carregados foi aprimorado.
* Uma nova opção XtkSecurity_Disable_GetSetEnv foi adicionada para bloquear o uso de funções setEnv e getEnv.
* Informações confidenciais agora estão ocultas no rastreamento da pilha do aplicativo.

**Melhorias em medidas de proteção, robustez e escalabilidade**

* Otimização do uso da sequência Lifespan - XtkNewId: as tabelas mais antigas foram movidas da sequência xtkNewId para sequências dedicadas.
* FDA sobre HTTP v2: FDA sobre protocolo HTTP é amplamente usado em implantações híbridas, especialmente para recuperação de broadLog e preparação de delivery. Robustez foi aprimorada para evitar problemas de rede e possíveis erros como recuperação e envio de dados. Isso requer que as builds nas duas extremidades da conexão estejam atualizados, caso contrário, o protocolo antigo ainda será usado.
* Workflow de rastreamento: a robustez do workflow de rastreamento foi aprimorada. Vários problemas relacionados a inserções/atualizações de log de rastreamento e personalização de rastreamento de URL foram corrigidos. Além disso, o workflow de rastreamento agora detecta problemas de log de rastreamento que podem levar a erros e interromper o workflow. Esses problemas agora são descartados e não processados.
* Workflow de limpeza: o workflow de limpeza foi aprimorado para evitar possíveis erros e interrupções. Isso otimiza o tamanho e o desempenho do banco de dados.
* Imagens incorporadas em mensagens transacionais: adicionamos o suporte completo de imagens incorporadas em mensagens transacionais, para evitar possíveis falhas ou ausência de imagens.
* Tamanho do banco de dados - XtkJobLog: um mecanismo de limpeza foi adicionado a essa tabela. Isso tem um impacto positivo no tamanho do banco de dados.
* Arquivamento do Cco: os parâmetros padrão para arquivamento do Cco foram alterados para aumentar a velocidade do arquivamento. [Leia mais](../../installation/using/email-archiving.md#parameters)
* Atualização da estrutura do banco de dados: as solicitações SQL geradas pelo Assistente de atualização da estrutura do banco de dados foram aprimoradas para execução mais rápida.
* Medidas de proteção para ações do operador: várias medidas de proteção foram implementadas para impedir que os operadores executem ações que poderiam afetar a integridade da plataforma. Os esquemas internos não podem mais ser excluídos pela interface. Além disso, o XML de origem do workflow não pode mais ser editado por usuários não administradores.
* Duas novas opções foram disponibilizadas: **XtkSecurity_Restrict_EditXML** (permite desabilitar a edição do código XML dos deliveries) e **NmsOperation_OperationMgtDebug** (permite monitorar a execução do workflow técnico operationMgt). [Leia mais](../../installation/using/configuring-campaign-options.md)

**Outras alterações**

* Notificações por push: agora oferecemos suporte à opção Thread ID para iOS por push.
* Melhorou o gerenciamento de índices de nomes longos que podem causar problemas após a atualização.
* Agora, durante a análise de um delivery desfeito, se o modo de publicação estiver definido como **[!UICONTROL None]** no assistente de implantação, um erro será registrado e a análise será interrompida: &quot;Publication mode is set to &#39;none&#39;: Cannot embed image. As imagens não serão exibidas no telefone do recurso. (NEO-12208)
* A gestão de broadlog foi aprimorada para o sistema de mensagens transacionais. Quando broadlogs são sincronizados da instância de execução para a instância de controle, o campo @lastModified é atualizado para a data atual do sistema. A opção MC_Update_BlLastModified foi adicionada para as instâncias de controle. True significa que a data atual será usada na instância de controle (comportamento padrão). False significa que usamos a data @lastModified da instância de execução do broadlog. (NEO-12579)
* Os índices foram adicionados nas tabelas temporárias de cupom para otimizar o envio de delivery. (NEO-12437)
* Na integração do Analytics, a recuperação de dados de segmento de AAM com caractere % agora é permitida. (NEO-12025)
* Remoção do limite de 10.000 registros no Mapa de Aquecimento do Fluxo de Trabalho para corrigir um problema de dados ausente. (NEO-12329)
* O Open Office não é suportado e foi totalmente removido do aplicativo. Se você ainda o usava, migre para o Libre Office como ele não funcionará mais a partir da atualização 19.1.
* Agora você pode limitar o Acesso de gravação à Atividade de atualização de dados em workflows usando atributos sysfilter. [Leia mais](../../configuration/using/filtering-schemas.md)

**Correções**

* Correção de um problema que impedia que o certificado fosse carregado para as notificações por push em dispositivos móveis iOS.
* Correção de possíveis falhas recorrentes de servidor para notificações transacionais por push. Outras falhas foram corrigidas.
* Correção de um problema que resultava em discrepâncias de relatório entre as atividades do usuário e os relatórios de rastreamento do indicador de abertura de delivery. (NEO-11742)
* Correção de um problema com o login de IMS.
* Correção de um problema que poderia resultar na ausência de imagens em um delivery ao adicionar uma imagem da biblioteca. (NEO-11900)
* Correção de um problema que poderia ocorrer ao extrair detalhes da oferta em um delivery de mala direta. (NEO-11700)
* Correção de um problema que poderia afetar o desempenho da mensagem transacional de SMS. (NEO-9812)
* Correção de uma falha do console que poderia ocorrer ao usar a opção Definido em um arquivo externo para o target principal de um delivery. (NEO-12349)
* Correção de um problema ao analisar uma mensagem que tinha como target recipients para domínios japoneses (.JP). (NEO-12246)
* Correção de um problema de exibição ao usar uma distribuição de valores com um link 1:N. (NEO-12212, NEO-11820)
* Correção de um problema que poderia causar erros de NmsMxDomain nos logs MTA após um postupgrade. (NEO-12752)
* Correção de um problema ao usar a opção &quot;Manter todos os dados adicionais do conjunto principal&quot; em uma atividade de workflow de enriquecimento. (NEO-13291)
* Correção de um problema de falha do Tomcat ao enviar notificações por push usando HTTP2. (NEO-12701)
* Correção de um problema com API HTTPRequest que não esperou o término de todos os retornos de chamada. (NEO-12628)
* Correção de um problema com o processo de cálculo de indicadores de rastreamento para mensagens transacionais. (NEO-12529)
* Correção de um problema com o uso de temas na gestão de ofertas. (NEO-11804)
* Correção de um problema de desempenho ao enviar notificações por push. (NEO-11787)
* Corrigido um problema ao pré-visualizar um arquivo XML ou CSV de saída na gestão de ofertas para um delivery de mala direta. (NEO-11290)
* Correção de um problema ao instalar o pacote de **Gestão de redes sociais** (Marketing Social). (NEO-12081)
* Correção de um problema que impedia excluir uma aplicação Web mesmo se tiver os direitos de acesso corretos. (NEO-12072)
* Correção de um problema que poderia causar a substituição de alguns valores ao exportar e importar um objeto via XML. A opção XtkExport_IncludeDefaultValues foi adicionada. Quando definido como True (comportamento padrão), todos os valores são exportados. Quando definido como False, as modificações serão substituídas pelo valor padrão. (NEO-11979)
* Correção de um problema que causava falhas da atividade do workflow **[!UICONTROL Alert]** quando uma atividade de enriquecimento era adicionada após um query. (NEO-12132)
* Correção de um problema nas configurações do Oracle em que deslocamentos de pipeline (disparadores) não eram recuperados com êxito do banco de dados, gerando duplicatas. (NEO-12121)
* Correção de um problema que poderia causar erros de exibição em tabelas dinâmicas ao usar a integração do Analytics (NEO-12103)
* Correção de um problema com o relatório de Análise Descritiva. (NEO-11414)
* Correção de um problema com conectores CRM quando a tabela remota continha um campo com um sublinhado em seu nome.
* Correção de um problema que poderia causar um problema de exibição para símbolos de moeda nos relatórios de Hipótese. (NEO-11634)
* Correção de um problema de redirecionamento e rastreamento ao usar determinados caracteres nos links de rastreamento.
* Correção de um problema que impedia a pré-visualização correta de oferta.
* Correção de um problema com devoluções temporárias que não eram removidas da tabela de endereços.
* Correção de um erro JAVA ao usar códigos de barras.
* Correção de um problema de tradução em aplicações Web (NEO-12460)
* Correção de um problema com a atividade do workflow s3 Transferência de Arquivo. (NEO-12473)
* Correção de um problema com campos de data em aplicações Web. (NEO-12496)
* Correção de um problema de esgotamento de ID ao usar seed addresses em um delivery. (NEO-11842)
* Correção de um problema de compatibilidade com phantomjs e Debian 9.
* Correção de um erro ao aprovar o conteúdo de uma prova. (NEO-12725)
* Correção de um problema com o recurso de workflow &quot;Excluir este subconjunto de público&quot;. (NEO-12441)
* Correção de um problema com a API HTTPRequest-wait que não esperava pelo término de todos os retornos de chamada. (NEO-12628)
* Correção de um problema na tarefa &quot;Atualizar Audience Compartilhado&quot; em uma atividade de Split. (NEO-11562)
* Correção de um problema de falha no servidor Web. (NEO-12904)
* Correção de um problema com o parâmetro Nature em modelos transacionais. (NEO-12334)
* Correção de problema de falha do console ao exibir as URLs rastreadas no editor de texto de email. (NEO-13122)
* Correção de um problema com a atividade de Split de Arquivo ao importar audiences do Audience Manager. (NEO-11550)
* Correção de um problema que causava erros no relatório de clique populares. (NEO-11459)
* Correção de um problema com a oferta de renderização. (NEO-11565)
* Correção de um problema com a atividade de Atualização de Lista ao importar audiences do Audience Manager. (NEO-11226)
* Correção de um problema com agendamento de atividade e configuração de fuso horário. (NEO-11662)
* Correção de um problema que resultava em falha no workflow de rastreamento em caso de URLs malformadas.
* Correção de um problema com contas externas após importar o pacote de aplicativo móvel.
* Correção de um problema ao atribuir um fuso horário a um operador. (NEO-12464)
* Correção de um problema que poderia causar erros nos logs mtachild. (NEO-11539, NEO-8978)
* Correção de um problema ao clicar no ícone Histórico em um relatório salvo. (NEO-11620)
* Correção de um problema ao editar uma tabela dinâmica em um relatório. (NEO-12068)
