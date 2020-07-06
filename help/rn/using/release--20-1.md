---
title: Versão 20.1
description: Versão 20.1
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
translation-type: ht
source-git-commit: 6ce00d34ecbdfa6a13593772ffa1850768ad6e45
workflow-type: ht
source-wordcount: '1408'
ht-degree: 100%

---


# Versão 20.1{#release-20-1}

[Build upgrade](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html) | [Control Panel releases](https://docs.adobe.com/content/help/pt-BR/control-panel/using/release-notes.html) | [Documentation updates](../../rn/using/documentation-updates.md) | [Previous releases](../../rn/using/release--19-2.md) | [Deprecated features](https://helpx.adobe.com/br/campaign/kb/deprecated-and-removed-features.html)

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

## ![](assets/do-not-localize/orange_2.png) Versão 20.1.3 - Build 9124 {#release-20-1-3-build-9124}

_6 de maio de 2020_

* Correção de um problema com a atividade **Transferência de Arquivo**, que impedia que a autenticação com a chave SFTP funcionasse no Debian 9. (NEO-23183)

## ![](assets/do-not-localize/orange_2.png) Versão 20.1.2 - Build 9123 {#release-20-1-2-build-9123}

_13 de março de 2020_

* Correção de um problema que impedia a implantação da versão em servidores Red Hat 7. (NEO-23332)

## ![](assets/do-not-localize/orange_2.png) Versão 20.1 - Build 9122 {#release-20-1-build-9122}

_17 de fevereiro de 2020_

**Novidades**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Conector Snowflake FDA</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>O Snowflake é um data warehouse de nuvem totalmente gerenciado, criado para dimensionar tanto no nível de armazenamento quanto no nível de computação. Com esse novo conector, o Adobe Campaign agora pode aproveitar o potencial do Snowflake para executar a Segmentação de Big Data. Esse conector está disponível para todos os clientes, inclusive hospedado pela Adobe.</p>
    <p>Para obter mais informações, consulte a <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake">documentação detalhada</a> e o <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">vídeo tutorial</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Aprimoramentos do conector FDA Hadoop</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>O conector FDA Hadoop foi aprimorado para oferecer suporte ao Hadoop 3.0 e à Cloudera.</p>
    <p>Para obter mais informações, consulte a <a href="../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3">documentação detalhada</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Aprimoramentos de segurança**

* Segurança aprimorada na configuração do relatório para proteger contra clickjacking. Isso se aplica aos novos relatórios. Para relatórios antigos, é necessário republicá-los para aplicar as alterações. (NEO-13282)

* Correção de um pequeno problema de memória no cryptString. (NEO-20071)

* JSP do monitor aprimorado para corrigir uma divulgação interna de IP. (NEO-16821)

* Correção de um problema em que as informações de rastreamento de pilha podiam ser exibidas para usuários não administradores. (NEO-12388)

* Gerenciamento de dados em cache aprimorado de sessões anteriores. (NEO-17039)

* Correção de um problema que impedia o arquivo logins.log de registrar tentativas de login bem-sucedidas por meio do IMS. (NEO-11004)

**Aprimoramentos**

* O iOS 13 agora é compatível com o conector HTTP2.

* Gerenciamento de quarentena e limpeza aprimorados das tabelas usadas pelo recurso de notificação por push (nms:address e nms:appSubscriptionRcp). No iOS (somente conector HTTP2), os tokens desativados agora são manipulados da mesma forma que no Android. O sinalizador disable agora está definido na tabela NmsAppSubscriptionRcp. [Leia mais](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Uma nova opção foi adicionada ao **código JavaScript** e às atividades de workflow do **código JavaScript avançado** para definir um período de tempo limite. Isso impede que a fase de execução do javascript seja executada por muito tempo. Se o período limite expirar, o workflow será interrompido. O tempo limite padrão é de 1 hora. [Leia mais](../../workflow/using/sql-code-and-javascript-code.md)

* A análise do delivery agora é interrompida quando nenhuma afinidade correspondente é encontrada no servidor mid-sourcing, com a mensagem de erro correspondente sendo exibida.

* Agora há suporte para failover de banco de dados para Postgres: quando o servidor de banco de dados trava e reinicia, o Campaign agora se reconecta automaticamente a ele.

* A visualização **Start Pending** foi adicionada ao nó Administration > Audit > Workflows Status. Isso permite que você monitore todos os workflows na sua instância que estão aguardando para serem iniciados pelo processo **operationMgt**. Esta visualização vem com o pacote de campanhas de marketing. [Leia mais](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Outras alterações**

* No Linux, a inicialização do serviço nlserver agora usa uma unidade sistêmica em vez do script /etc/init.d/nlserver6. A migração para o novo schema de inicialização é executada automaticamente ao instalar o pacote 20.1. O /etc/init.d/nlserver6 ainda é fornecido, mas para interagir com o serviço nlserver (start, reinicialização, interrupção etc.), recomendamos que você use o comando systemctl diretamente.

* As tabelas personalizadas mais trabalhosas foram movidas da sequência **xtkNewId** para sequências dedicadas. [Leia mais](https://helpx.adobe.com/br/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Melhora do desempenho do query que pode ser afetado por conexões desnecessárias ao banco de dados.

* Melhora do desempenho do assistente de atualização do banco de dados.

* O gerenciamento dos registros do banco de dados foi aprimorado.

* A robustez do pool de conexões foi aprimorada, o que pode impedir que falhas inesperadas de conexão ocorram com muita frequência.

* As regras de validação de endereço de email para enviar um endereço para a quarentena em caso de erro de software foram aprimoradas. [Leia mais](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Para Debian, o Campaign agora usa bibliotecas PCRE do sistema quando elas estão disponíveis.

* O Campaign agora permite o uso de uma biblioteca ODBC do sistema mais recente.

* Adicionamos um tempo limite ao servlet LINE quando uma conexão para carregar uma imagem avançada é aberta. Se a imagem estiver demorando muito para carregar, o servlet interrompe a conexão para evitar um gargalo.

**Correções**

* Correção de um problema de criptografia de chave da conta ao usar o conector do Hadoop.

* Correção de um problema de regressão devido à implementação da certificação SSL que causava a falha da conexão do usuário no servidor Windows. (NEO-20629)

* Correção de um problema com a atividade de query incremental no caso de IDs de workflow negativas. (NEO-19779)

* Correção de um problema de codificação ao executar os queries por meio do conector FDA Netezza. (NEO-19594)

* Correção de um problema que resulta em erro ao usar o método POST na atividade de evento do workflow **Download da Web**

* Correção de um problema com a criação da apresentação da oferta. (NEO-18176)

* Correção de um problema de exibição do rodapé ao usar o modelo de formulário da Web de aquisição.

* Correção de um problema ao analisar os URLs no conteúdo de deliveries contínuos que causa falhas. (NEO-16910)

* Correção de um problema onde os campos **Start** e **End** não são computados ao criar uma nova campanha.

* Correção de um problema com a atividade de workflow **Download de arquivo** ao usar um URL.

* Correção de um problema ao visualizar uma lista importada em uma atividade de consulta de um relatório. (NEO-13119)

* Correção de um problema que exibia uma imagem desatualizada ao selecionar o bloco de personalização **Powered by Campaign** no editor de email.

* A comunicação de rede entre o cliente e o servidor foi aprimorada.

* Correção de um problema em que muitos workflows eram criados na mesma campanha. Agora, você não pode criar mais de 28 workflows. Um aviso é exibido.

* Correção de um problema ao usar a opção **Uma seleção de reconciliação de colunas** em uma atividade de workflow **Union**.

* Correção de um problema de travamento do console que ocorria ao usar uma lista de enriquecimento corrompida em um workflow. (NEO-18096)

* Correção de vários problemas de travamento do console que podem ocorrer em workflows (NEO-18010, NEO-18032)

* Correção de um problema que permite a execução de uma atividade de workflow **External Signal** mesmo quando ela está desativada. (NEO-17524)

* Correção de um problema ao criar um novo schema.

* Correção de um problema de rastreamento ao enviar mensagens SMS. (NEO-19595)

* Correção de um problema que exibe números incorretos do público direcionado em indicadores de entrega.

* Correção de um problema que exibe porcentagens incorretas ao gerar um relatório descritivo por meio de uma atividade de workflow. (NEO-14314)

* Correção de um problema que faz com que o relatório de taxa de transferência do delivery apresente números diferentes quando o parâmetro de visualização de tempo é utilizado. (NEO-11783)

* Correção de um problema que impede a atualização dos indicadores de rastreamento de mensagens transacionais pelo workflow Tracking. (NEO-17770)

* Correção de um problema de regressão que resulta na falha e reinicialização do processo da Web ao solicitar uma oferta por meio do SOAP. (NEO-19482)

* Correção de um problema que impede o upload de dados para recursos públicos se o diretório estiver em um local compartilhado remoto. (NEO-19361)

* Correção de um problema que causa a falha constante do workflow técnico **Import audiences from the Adobe Experience Cloud**. (NEO-18463)

* Correção de um problema que impede o envio do delivery ao usar os modelos importados do Experience Manager. (NEO-17540)

* Correção de um problema que ocorre após a atualização para a build 9032 e impede a instância de se conectar ao servidor FTP pelo protocolo SSL. (NEO-20498)

* Correção de um problema que ocorre ao excluir, inserir ou atualizar uma grande quantidade de dados com a atividade **Update data** em um workflow que usa um schema FDA como dimensão de direcionamento. (NEO-13280)

* Correção de um problema que impede o envio de emails ao usar a declaração &quot;se&quot; fora da tag `body`.

* Correção de um problema que ocorre ao tentar exibir a mirror page dos logs do delivery de uma mensagem enviada. (NEO-17976)

* Correção de um problema que impede que o bloco de personalização **Link to mirror page** seja exibido na guia **Text content** depois de clicar em **Import HTML** de uma delivery. (NEO-17568)

* A mensagem de erro que é exibida ao clicar em um link para uma mirror page que expirou foi esclarecida. (NEO-17340)

* Correção de um problema que impede que alguns botões sejam usados na tela de criação **Data distribution**.

* Correção de um problema que ocorre ao agendar uma atividade de delivery em uma instância com Ásia/Calcutá como fuso horário. (NEO-20001)

* Um erro agora é exibido quando um delivery tem um problema de configuração de afinidade.

* Correção de um problema que exibia um número de tag de versão incorreto no menu **About**.

* Correção de um problema que ocorre ao tentar atualizar a conta do roteamento a partir de propriedades de delivery que são recorrentes em um workflow. (NEO-18684)

* Correção de um problema que ocorre ao conectar-se à instância por meio do módulo de redirecionamento, que impedia que a conexão fosse limpa corretamente depois de fechada.
