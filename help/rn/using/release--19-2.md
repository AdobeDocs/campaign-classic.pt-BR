---
title: Versão 19.2
seo-title: Versão 19.2
description: Versão 19.2
seo-description: null
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
source-git-commit: 410fd89cd030ac3d4644e6aa025ed5f03adb788f

---


# Versão 19.2{#release-19-2}

[Criar atualização](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) | Versões [do Painel](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) de controle| Atualizações [da documentação](../../rn/using/documentation-updates.md) | [Versões anteriores](../../rn/using/release--19-1.md) | Recursos [obsoletos](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>Disponibilidade geral</strong></td>
   <td><img src="assets/blue3.png"/><strong>Release Candidate</strong></td> 
   <td><img src="assets/orange3.png"/><strong>Não está mais disponível</strong></td> 
   <td><img src="assets/red3.png"/><strong>Obsoleto</strong></td> 
  </tr> 
   <tr> 
   <td>Compilação estável mais recente disponível. <br>Compilação validada na produção. </td>
   <td>Compilação validada pela Adobe. <br>Aguardando prova de produção. </td>
   <td>Versão mais recente disponível com correções de erros. <br>É necessário atualizar. </td>
   <td>Contém regressões conhecidas. <br>A atualização é obrigatória. </td>
  </tr> 
 </tbody> 
</table>

Clique [aqui](../../rn/using/release--19-1.md#release-19-1-4-build-9032) para exibir a **última compilação** estável (GA).

## ![](assets/blue-2.png) Versão 19.2.3 - Build 9081 {#release-19-2-3-build-9081}

_07 de fevereiro de 2020_

**Aprimoramentos**

* Corrigido um problema de regressão devido à implementação da certificação SSL que causava a falha da conexão do usuário no servidor Windows. (NEO-20629)
* Correção de um problema que exibia um número de tag de versão incorreto no menu **Sobre** .

## ![](assets/orange-2.png) Versão 19.2 - Build 9080 {#release-19-2-build-9080}

_02 de dezembro de 2019_

**Novidades**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA é a nova lei de privacidade do estado da Califórnia que harmoniza e moderniza os requisitos de proteção de dados que entram em vigor em 1° de janeiro de 2020. O CCPA se aplica aos clientes do Adobe Campaign que detêm dados para pessoas de dados residentes na Califórnia.</p>
    <p> Além dos recursos de privacidade já disponíveis (incluindo gerenciamento de consentimento, configurações de retenção de dados e funções de usuário), o Adobe Campaign ajuda a facilitar a preparação para CCPA:</p>
    <ul>
      <li>Direito de acesso e direito de exclusão: estamos aproveitando as capacidades que foram adicionadas ao RGPD. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">Leia mais</a></li>
      <li>Você pode rastrear se um consumidor optou pela venda de Informações pessoais. Para isso, é necessário estender a tabela Perfis e adicionar um campo <strong>Recusar para CCPA</strong> . <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Leia mais</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Monitoramento ao vivo do fluxo de trabalho</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Agora você pode monitorar o status de execução de todos os fluxos de trabalho na sua instância usando exibições predefinidas.</p>
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
<td> <p>O Adobe Campaign permite que você experimente o novo <a href="https://amp.dev/about/email/">AMP interativo para o formato de email</a> , que permite que os profissionais de marketing incluam componentes AMP dentro de mensagens para aprimorar a experiência de email com conteúdo avançado, dinâmico e interativo, acionável diretamente na própria mensagem.</p>
   <p> Esse recurso é lançado como um beta público.</p>
   <p>For more information, refer to the <a href="../../delivery/using/defining-interactive-content.md">detailed documentation</a> and the <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">tutorial video</a>.</p><br /></td> 
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
<td> <p>O SMS Seguro agora é suportado pelo Conector SMPP Genérico Estendido. Isto permite uma conexão codificada com o provedor.</p> <p><strong>Aviso</strong> Este recurso requer um certificado atualizado em todos os servidores. Certificados inválidos, revogados ou expirados gerarão erros que afetam os recursos gerais de envio de SMS.</p><p>Para obter mais informações, consulte a <a href="https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html">documentação detalhada</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Aprimoramentos de segurança**

* Corrigidas as vulnerabilidades de script entre sites armazenadas na interface do Campaign - validação de dados de entrada e codificação de saída. (NEO-16810)
* Correção de um problema de segurança na autorização de perfil que poderia permitir o acesso a dados não autorizados ao reforçar a política de restrição de logon. (NEO-14445)

**Aprimoramentos**

* Otimização do consumo de memória para notificações por push.
* Para otimização de desempenho e armazenamento, a manipulação do arquivo **logins.log** foi aprimorada. O arquivo agora é dividido em vários arquivos, um a cada dia com um máximo de 365 arquivos retidos. [Leia mais](../../production/using/log-files.md)
* A conta externa do Microsoft Dynamics CRM agora pode ser configurada usando credenciais de senha (senha + nome de usuário) ou certificado (chave privada). [Leia mais](../../platform/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Alguns aprimoramentos foram adicionados ao conector Hadoop FDA para melhorar a confiabilidade
* Uma garantia específica foi adicionada para verificar o espaço em disco antes de permitir o upload de recursos públicos no servidor.
* Novas opções [de](../../installation/using/configuring-campaign-options.md) campanha foram adicionadas:
   * A opção de configuração **WdbcKillSessionPolicy** permite que você afete o comportamento de Parada **** Incondicional em todos os fluxos de trabalho e consultas de banco de dados PostgreSQL.
   * A opção **NmsOperation_DeliveryPreparationWindow** permite definir o número de dias acima dos quais as entregas com status inconsistente serão excluídas da contagem de entregas em execução.
   * A opção **WdbcOptions_TempDbName** permite configurar um banco de dados separado para tabelas de trabalho no Microsoft SQL Server. Isso otimiza os backups e a replicação. [Leia mais](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * A opção **XtkCleanup_NoStats** foi aprimorada para o PostgreSQL para controlar melhor o comportamento da etapa de otimização de armazenamento do fluxo de trabalho de limpeza do banco de dados. [Leia mais](../../production/using/database-cleanup-workflow.md#statistics-update)
* Um mecanismo de bloqueio de conta foi adicionado à API **logon()** . Evita novas tentativas de login após um determinado número de tentativas consecutivas de falha de login em um período de tempo especificado.
* Uma nova opção **Máximo de tempo** de execução de personalização nas propriedades de entrega permite definir um período de tempo limite para o tempo de execução de personalização, a fim de evitar que a fase de personalização seja executada por muito tempo. [Leia mais](../../delivery/using/personalization-fields.md#timing-out-personalization)
* A opção de protocolo **** ftp foi adicionada para permitir que você use uma configuração proxy para conexões SFTP. [Leia mais](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* Novo suporte de acesso proxy a um servidor externo SFTP para ambientes locais.
* Uma garantia específica foi adicionada para impedir a instalação de pacotes que não são compatíveis com a instância da Campanha. [Leia mais](../../installation/using/installing-campaign-standard-packages.md)

_Sistemas obsoletos_

Os seguintes sistemas foram [descontinuados](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html) para implementações do Campaign Classic:
* Apache 2.2
* Centos 6

Certifique-se de que você esteja usando as versões compatíveis de qualquer sistema listadas na matriz de compatibilidade de campanha mais recente. [Leia mais](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

_SDK do Campaign Mobile_

A compilação 1.0.26 do SDK do iOS está disponível. Nesta nova compilação, adicionamos o suporte do iOS 13. Esta nova versão agora suporta prioridade de notificação e o novo processo de gerenciamento de token de registro para notificações por push do iOS 13. Se você estiver executando aplicativos em uma versão anterior do SDK, será necessário recompilar seus aplicativos com o novo SDK. Para obter o SDK, entre em contato com o Atendimento ao cliente da Adobe.

**Correções**

* Corrigida uma falha no console que ocorria ao adicionar uma tabela vinculada vazia na atividade de fluxo de trabalho **de Carregamento de dados (RDBMS)** . (NEO-12213)
* Correção de um problema que resultava no não processamento de determinadas mensagens pelo servidor de Mid-Sourcing. (NEO-12395)
* Correção de um problema no fluxo de trabalho de limpeza do banco de dados ao usar a opção de agrupamento de consulta com Teradata. (NEO-12399)
* Correção de um problema que afetava a análise de entrega com a regra de tipologia, incluindo o domínio ne.jp. (NEO-12609)
* Correção de um problema relacionado a atualizações de SMS sobre TLS que implicavam uma política de certificados mais restritiva. Essas atualizações podem levar a uma falha de conexão entre servidores de marketing e de mid-sourcing no caso de um certificado desatualizado. (NEO-17698)
* Correção de um problema ao usar o botão **Testar conexão** em uma conta externa em um ambiente de mid-sourcing com autenticação Vault. (NEO-12722)
* Correção de um problema em consultas que usavam funções de data com uma conexão FDA Hadoop. (NEO-12847)
* Correção de um problema ao substituir uma imagem no editor de email. (NEO-13098)
* Correção de um problema que resultava em erros de pós-atualização em pastas que tinham sido excluídas ou movidas para outro local. (NEO-13118)
* Correção de um problema na exibição da imagem ao usar a opção **Definir imagem por tamanho** de tela do dispositivo nas mensagens LINE. (NEO-13228)
* Correção de um problema de preparação de entrega quando a opção **Excluir endereço duplicado durante a entrega** não estava selecionada. (NEO-13240)
* Correção de um problema nos fluxos de trabalho ao usar a atividade de transferência **de** Arquivo para baixar arquivos usando a opção **Excluir os arquivos de origem após a transferência** , com um nome que contém um caractere de espaço. (NEO-13411)
* Correção de um problema com a limpeza do cache Tomcat, que pode levar a problemas de memória. (NEO-13456)
* Correção de um problema ao instalar o **Controle do mecanismo de oferta com o pacote integrado da instância** de execução em uma instância de controle existente em execução no Microsoft SQL 2017. (NEO-13539)
* Corrigida uma falha no console que ocorria ao desmarcar URLs rastreados em um email, na guia Conteúdo **de** texto. (NEO-13545)
* Correção de um problema de codificação no nome do remetente chinês. (NEO-13837)
* Correção de um erro que poderia levantar ao exibir dados de resposta da pesquisa do Explorer. (NEO-14590)
* Correção de um problema que resultava em discrepância entre a classificação do log de entrega e a tabela de quarentena. (NEO-16547)
* Correção de um problema com chaves DKIM que não eram incorporadas a emails. (NEO-16804)
* Correção de um problema que exibia o código de erro incorreto quando um token de sessão inválido era usado no contexto de chamadas de API para acionar eventos. O código de erro era &#39;HTTP 200 OK&#39; em vez de &#39;HTTP 403 Proibido&#39;. (NEO-16826)
* Correção de um problema ao exibir relatórios de entrega via acesso à Web. (NEO-17015)
* Correção de um problema de autenticação IMS ao fazer logon no Adobe Campaign. (NEO-17312)
* Correção de um problema que impedia que emails em quarentena fossem excluídos pelo processo de Gerenciamento de privacidade. (NEO-17314)
* Correção de problemas de throughput após a atualização para o 9031 com o banco de dados SQL. (NEO-17558)
* Correção de um problema que afetava o CRM Connector com Salesforce. (NEO-17712)
* Correção de um problema de tempo limite ao importar dados de um SFTP externo. (NEO-19723)
* Correção de um problema ao acessar modelos Preditivos. (NEO-19713)
* Correção de um problema que afetava a amostragem aleatória na atividade do fluxo de trabalho **Dividir** com o banco de dados FDA do Hadoop. (NEO-16636)

