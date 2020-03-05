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
source-git-commit: fd7bc26fe12a26d8fb0dcccd2135b799e76b52bd

---


# Versão mais recente{#latest-release}

[Criar atualização](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) | Versões [do Painel](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) de controle| Atualizações [da documentação](../../rn/using/documentation-updates.md) | [Versões anteriores](../../rn/using/release--19-2.md) | Recursos [obsoletos](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>Disponibilidade geral</strong></td>
   <td><img src="assets/blue3.png"/><strong>Candidato à versão</strong></td> 
   <td><img src="assets/orange3.png"/><strong>Não está mais disponível</strong></td> 
   <td><img src="assets/red3.png"/><strong>Obsoleto</strong></td> 
  </tr> 
   <tr> 
   <td>Compilação estável mais recente disponível. Compilação validada na produção.<br> </td>
   <td>Compilação validada pela Adobe. Aguardando prova de produção.<br> </td>
   <td>Versão mais recente disponível com correções de erros. É necessário atualizar.<br> </td>
   <td>Contém regressões conhecidas. A atualização é obrigatória.<br> </td>
  </tr> 
 </tbody> 
</table>

A **última compilação** estável é 9032 (205c981c3). Clique [aqui](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/blue_2.png) Versão 20.1 - Build 9122 {#release-20-1-build-9122}

_17 de fevereiro de 2020_

**Novidades**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Conector FDA em floco de neve</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>O Floco de neve é um data warehouse em nuvem totalmente gerenciado, criado para dimensionar no nível de armazenamento e de computação. Com esse novo conector, o Adobe Campaign agora pode aproveitar o poder do Floco de neve para executar a Segmentação de grandes dados. Esse conector está disponível para todos os clientes, inclusive hospedado pela Adobe.</p>
    <p>For more information, refer to the <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake">detailed documentation</a> and <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">tutorial video</a>.</p>
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
   <td> <p>O Conector FDA do Hadoop foi aprimorado para suportar o Hadoop 3.0 e a Cloudera.</p>
    <p>Para obter mais informações, consulte a <a href="../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3">documentação detalhada</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Aprimoramentos de segurança**

* Segurança aprimorada na configuração do relatório para proteger contra clickjacking. Isso se aplica aos novos relatórios. Para relatórios antigos, é necessário republicá-los para aplicar as alterações. (NEO-13282)

* Correção de um pequeno problema de memória em cryptString. (NEO-20071)

* JSP do monitor aprimorado para corrigir uma divulgação interna de IP. (NEO-16821)

* Correção de um problema em que as informações de rastreamento de pilha podiam ser exibidas para usuários não administradores. (NEO-12388)

* Gerenciamento de dados em cache aprimorado de sessões anteriores. (NEO-17039)

* Correção de um problema que impedia o arquivo logins.log de registrar tentativas de login bem-sucedidas por meio do IMS. (NEO-11004)

**Aprimoramentos**

* O iOS 13 agora é compatível com o conector HTTP2.

* Gerenciamento de quarentena e limpeza aprimorados das tabelas usadas pelo recurso de notificação por push (nms:address e nms:appSubscriptionRcp). No iOS (somente conector HTTP2), os tokens desativados agora são manipulados da mesma forma que no Android. O sinalizador disable agora está definido na tabela NmsAppSubscriptionRcp. [Leia mais](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Uma nova opção foi adicionada ao código **JavaScript e às atividades de fluxo de trabalho do código** JavaScript **** avançado para definir um período de tempo limite. Isso impede que a fase de execução do javascript seja executada por muito tempo. Se o período limite expirar, o fluxo de trabalho será interrompido. O tempo limite padrão é de 1 hora. [Leia mais](../../workflow/using/sql-code-and-javascript-code.md)

* A análise de entrega agora é interrompida quando nenhuma afinidade correspondente é encontrada no servidor de mid-sourcing, com a mensagem de erro correspondente sendo exibida.

* Agora há suporte para failover de banco de dados para Postgres: quando o servidor de banco de dados falha e é reiniciado, o Campaign agora se conecta a ele automaticamente.

* A exibição **Iniciar pendente** foi adicionada ao nó Administração > Auditoria > Status dos fluxos de trabalho. Isso permite monitorar todos os fluxos de trabalho na sua instância que estão aguardando para serem iniciados pelo processo **operationMgt** . Esta exibição vem com o pacote de campanhas de marketing. [Leia mais](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Outras alterações**

* No Linux, a inicialização do serviço nlserver agora usa uma unidade sistêmica em vez do script /etc/init.d/nlserver6. A migração para o novo esquema de inicialização é executada automaticamente quando você instala o pacote 20.1. O /etc/init.d/nlserver6 ainda é fornecido, mas para interagir com o serviço nlserver (iniciar, reiniciar, parar etc.), recomendamos que você use o comando systemctl diretamente.

* As tabelas personalizadas mais consumentes foram movidas da sequência **xtkNewId** para sequências dedicadas. [Leia mais](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Desempenho de consulta aprimorado que pode ser afetado por conexões desnecessárias ao banco de dados.

* Aprimorado o desempenho do assistente de atualização de banco de dados.

* O gerenciamento de registros do banco de dados foi aprimorado.

* A robustez do pool de conexões foi aprimorada, o que pode impedir que falhas inesperadas de conexão ocorram com muita frequência.

* As regras de validação de endereço de email para enviar um endereço para quarentena em caso de erro de software foram aprimoradas. [Leia mais](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Para Debian, o Campaign agora usa bibliotecas PCRE do sistema quando elas estão disponíveis.

* A campanha agora permite o uso de uma biblioteca ODBC do sistema mais recente.

* Foi adicionado um tempo limite ao servlet LINE ao abrir uma conexão para carregar uma imagem avançada. Se a imagem estiver demorando muito para carregar, o servlet interrompe a conexão para evitar um gargalo.

**Correções**

* Correção de um problema de criptografia de chave de conta ao usar o conector Hadoop.

* Correção de um problema de regressão devido à implementação da certificação SSL que causava a falha da conexão do usuário no servidor Windows. (NEO-20629)

* Correção de um problema com a atividade de consulta incremental no caso de IDs de fluxo de trabalho negativas. (NEO-19779)

* Correção de um problema de codificação ao executar consultas via conector Netezza FDA. (NEO-19594)

* Correção de um problema que resultava em erro ao usar o método POST na atividade de evento de fluxo de trabalho de Download **da** Web.

* Correção de um problema com a geração de proposta de oferta. (NEO-18176)

* Correção de um problema de exibição de rodapé ao usar o modelo de formulário da Web de aquisição.

* Correção de um problema ao analisar os URLs no conteúdo de entregas contínuas, o que poderia causar falhas. (NEO-16910)

* Correção de um problema que fazia com que os campos **Início** e **Fim** não fossem calculados ao criar uma nova campanha.

* Correção de um problema com a atividade do fluxo de trabalho Download **de** arquivo ao usar um URL.

* Correção de um problema ao visualizar uma lista importada em uma atividade de consulta de um relatório. (NEO-13119)

* Correção de um problema que exibia uma imagem desatualizada ao selecionar o bloco de personalização **Powered by Campaign** no editor de email.

* A comunicação de rede entre o cliente e o servidor foi aprimorada.

* Correção de um problema em que muitos fluxos de trabalho são criados na mesma campanha. Agora, você não pode criar mais de 28 fluxos de trabalho. Um aviso é exibido.

* Correção de um problema ao usar a opção **Uma seleção de reconciliação de colunas** em uma atividade de fluxo de trabalho da **União** .

* Correção de um problema de travamento do console que poderia ocorrer ao usar uma lista de enriquecimento corrompida em um fluxo de trabalho. (NEO-18096)

* Correção de vários problemas de travamento do console que podem ocorrer em fluxos de trabalho (NEO-18010, NEO-18032)

* Correção de um problema que permitia a execução de uma atividade de fluxo de trabalho de sinal **** externo mesmo quando ela estava desativada. (NEO-17524)

* Correção de um problema ao criar um novo esquema.

* Correção de um problema de rastreamento ao enviar mensagens SMS. (NEO-19595)

* Correção de um problema que exibia um número de público-alvo direcionado incorreto nos indicadores de entrega.

* Correção de um problema que exibia porcentagens incorretas ao gerar um relatório descritivo por meio de uma atividade de fluxo de trabalho. (NEO-14314)

* Correção de um problema que fazia com que o relatório de throughput de entrega mostrasse números diferentes quando o parâmetro de visualização de tempo era exibido. (NEO-11783)

* Correção de um problema que impedia que os indicadores de rastreamento de mensagens transacionais fossem atualizados pelo fluxo de trabalho de Rastreamento. (NEO-17770)

* Correção de um problema de regressão que resultava em falha e reinicialização do processo da Web ao solicitar uma oferta por meio do SOAP. (NEO-19482)

* Correção de um problema que impedia o upload de dados para recursos públicos se o diretório de upload fosse um local compartilhado remoto. (NEO-19361)

* Correção de um problema que causava a falha constante do fluxo de trabalho técnico **Importar públicos-alvo da Adobe Experience Cloud** . (NEO-18463)

* Correção de um problema que impedia o envio de entregas ao usar modelos importados do Experience Manager. (NEO-17540)

* Correção de um problema que ocorria após a atualização para a compilação 9032 e impedia a instância de se conectar ao servidor FTP pelo protocolo SSL. (NEO-20498)

* Correção de um problema que ocorria ao excluir, inserir ou atualizar uma grande quantidade de dados com a atividade de dados **** Atualizar em um fluxo de trabalho usando um esquema FDA como dimensão de definição de metas. (NEO-13280)

* Correção de um problema que impedia o envio de emails ao usar a declaração &quot;if&quot; fora da `body` tag .

* Correção de um problema que ocorria ao tentar exibir a página espelhada dos registros de entrega de uma mensagem enviada. (NEO-17976)

* Correção de um problema que impedia que o bloco de personalização **Link para espelhar página** fosse exibido na guia Conteúdo **de** texto depois de clicar em **Importar HTML** em uma entrega. (NEO-17568)

* A mensagem de erro exibida ao clicar em um link para uma página espelhada que expirou foi esclarecida. (NEO-17340)

* Correção de um problema que impedia que alguns botões fossem usados na tela de criação da distribuição **de** dados.

* Correção de um problema que ocorria ao agendar uma atividade de entrega em uma instância com Ásia/Calcutá como fuso horário. (NEO-20001)

* Um erro agora é exibido quando uma entrega tem um problema de configuração de afinidade.

* Correção de um problema que exibia um número de tag de versão incorreto no menu **Sobre** .

* Correção de um problema que ocorria ao tentar atualizar a conta de roteamento a partir das propriedades de uma entrega recorrente em um fluxo de trabalho. (NEO-18684)

* Correção de um problema que ocorria ao conectar-se à instância por meio do módulo de redirecionamento, o que impedia que a conexão fosse limpa corretamente depois de fechada.
