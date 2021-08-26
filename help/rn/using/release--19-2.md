---
product: campaign
title: Versão 19.2
description: Notas de versão do Campaign 19.2
exl-id: 3c529e4e-8787-41d2-b85d-3feaa5432196
source-git-commit: 84312974b9b7372c8a46fd1c7ead1148690bcd83
workflow-type: tm+mt
source-wordcount: '1542'
ht-degree: 99%

---

# Versão 19.2{#release-19-2}

![](../../assets/v7-only.svg)

## ![](assets/do-not-localize/limited_2.png) Versão 19.2.4 – Build 9082 {#release-19-2-4-build-9082}

_15 de abril de 2021_

* Correção de uma regressão do console do cliente que causava mensagens de erro persistentes na tela de conexão IMS. (NEO-34821)

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!NOTE]
>
> Conecte-se à [Distribuição de software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) para baixar a nova versão. Saiba como propor a atualização do console para todos os usuários finais [nesta página](../../installation/using/client-console-availability-for-windows.md).

_22 de março de 2021_

* Correção de uma regressão que impedia o uso de alguns componentes do console, como o seletor de datas e o gerenciamento de imagens nos deliveries. (NEO-31453, NEO-31454)

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!NOTE]
>
> Conecte-se à [Distribuição de software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) para baixar a nova versão. Saiba como propor a atualização do console para todos os usuários finais [nesta página](../../installation/using/client-console-availability-for-windows.md).

_23 de dezembro de 2020_

>[!CAUTION]
>
> * Esta versão é fornecida com um novo protocolo de conexão: se você estiver se conectando ao Campaign pelo Serviço de identidade da Adobe (IMS), a atualização será obrigatória para o servidor do Campaign e o console do cliente poderem se conectar ao Campaign após **30 de junho de 2021**. [Saiba mais](../../technotes/using/ims-updates.md)
>
> * Esta versão vem com uma [correção de segurança](https://helpx.adobe.com/br/security/products/campaign/apsb21-04.html): a atualização é obrigatória para reforçar a segurança do ambiente.



* O protocolo de conexão foi atualizado para seguir o novo mecanismo de autenticação IMS.
* Correção de um problema de segurança para reforçar a proteção contra situações de SSRF (Server Side Request Forgery). (NEO-27777)




## ![](assets/do-not-localize/red_2.png) Versão 19.2.3 – Build 9081 {#release-19-2-3-build-9081}

_7 de fevereiro de 2020_

**Aprimoramentos**

* Correção de um problema de regressão devido à implementação da certificação SSL que causava a falha da conexão do usuário no servidor Windows. (NEO-20629)
* Correção de um problema que exibia um número de tag de versão incorreto no menu **About**.

## ![](assets/do-not-localize/red_2.png) Versão 19.2 – Build 9080 {#release-19-2-build-9080}

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
* Uma garantia específica foi adicionada para verificar o espaço em disco antes de permitir o upload de recursos públicos no servidor.
* Novas [Opções de campanha](../../installation/using/configuring-campaign-options.md) foram adicionadas:
   * A opção de configuração **WdbcKillSessionPolicy** permite que você afete o comportamento de **Unconditional Stop** em todos os workflows e consultas de banco de dados PostgreSQL.
   * A opção **NmsOperation_DeliveryPreparationWindow** permite definir o número de dias nos quais os deliveries com status inconsistente serão excluídos da contagem de entregas em execução.
   * A opção **WdbcOptions_TempDbName** permite configurar um banco de dados separado para tabelas de trabalho no Microsoft SQL Server. Isso otimiza os backups e a replicação. [Leia mais](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * A opção **XtkCleanup_NoStats** foi aprimorada para PostgreSQL para controlar melhor o comportamento da etapa de otimização de armazenamento do workflow de limpeza do banco de dados. [Leia mais](../../production/using/database-cleanup-workflow.md#statistics-update)
* Um mecanismo de bloqueio de conta foi adicionado à API **logon()**. Impede novas tentativas de login após um certo número de tentativas com falha consecutivas em um período especificado.
* Uma nova opção **Maximum personalization run time** nas propriedades de delivery permite definir um período de tempo limite para o tempo de execução de personalização, a fim de evitar que a fase de personalização seja executada por muito tempo. [Leia mais](../../delivery/using/personalization-fields.md#timing-out-personalization)
* A opção **ftp protocol** foi adicionada para permitir que você use uma configuração proxy para conexões SFTP. [Leia mais](../../installation/using/file-res-management.md)
* Novo suporte de acesso proxy a um servidor externo SFTP para ambientes locais.
* Uma garantia específica foi adicionada para impedir a instalação de pacotes que não são compatíveis com a instância do Campaign. [Leia mais](../../installation/using/installing-campaign-standard-packages.md)

_Sistemas obsoletos_

Os seguintes sistemas foram [descontinuados](https://helpx.adobe.com/br/campaign/kb/deprecated-and-removed-features.html) para implementações do Campaign Classic:
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



