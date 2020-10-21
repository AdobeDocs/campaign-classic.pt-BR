---
title: Versão 19.1
seo-title: Versão 19.1
description: Versão 19.1
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
source-git-commit: c2c0609619e0cc81444d089850add6dec5de93fd
workflow-type: tm+mt
source-wordcount: '2623'
ht-degree: 98%

---


# Versão 19.1{#release-19-1}

## ![](assets/do-not-localize/limited_2.png) Versão 19.1.7 - Build 9036 {#release-19-1-7-build-9036}

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
* Após a mudança para o [novo mecanismo de ID de sequência](https://helpx.adobe.com/br/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence), todos os aplicativos da web que estão atualizando a tabela do recipient são republicados durante a pós-atualização.
* Correção de um problema que impedia o envio de emails quando um código Javascript estivesse fora da tag de conteúdo HTML. (NEO-18628)
* Correção de um problema que impede a atualização dos indicadores de rastreamento de mensagens transacionais pelo workflow Tracking. (NEO-17770)
* O desempenho do assistente de atualização de banco de dados foi aprimorado para realizar menos declarações SQL a fim de otimizar o tempo de resposta.
* Correção de um problema de travamento do console que poderia ocorrer ao desmarcar URLs rastreados em um email, na guia **Conteúdo de texto** devido a uma variável não inicializada. (NEO-13545)
* Correção de um problema que impedia o upload de arquivos em uma atividade de transferência de arquivos usando uma conta externa do Armazenamento Blob do Azure devido a uma variável não inicializada (m_pCurlReader). (NEO-13717)



* Correção de um problema de pós-atualização que desativava o Apache e o servidor da web antes da republicação do aplicativo web. (NEO-27155)



* Correção de uma regressão que resultava na escolha incorreta de um fuso horário na configuração de horário em uma atividade de workflow de **Scheduler**.

## ![](assets/do-not-localize/orange_2.png) Versão 19.1.6 - Build 9035 {#release-19-1-6-build-9035}

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

## ![](assets/do-not-localize/red_2.png) Versão 19.1.5 - Build 9033{#release-19-1-5-build-9033}

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

## ![](assets/do-not-localize/green_2.png) Versão 19.1.4 - Build 9032{#release-19-1-4-build-9032}

>[!NOTE]
>
>As versões 19.1.4 Gold Standard estão listadas nesta [página](../../rn/using/gold-standard.md).


## ![](assets/do-not-localize/red_2.png) Versão 19.1.2 - Build 9029{#release-19-1-2-build-9029}

_21 de junho de 2019_

**Aprimoramentos de segurança**

* Para otimizar a segurança, a biblioteca do Java (Netty) foi atualizada para a versão mais recente (4.1.34). (NEO-12788)

**Aprimoramentos**

* Correção de uma regressão relacionada ao gerenciamento de coluna sdomain que impedia que os emails fossem enviados em determinadas configurações.
* Para aprimorar o desempenho, um atributo _operation=&quot;none&quot; foi adicionado a chamadas rtEvent SOAP para evitar solicitações &quot;SELECIONE PARA ATUALIZAR&quot;.
* Correção de um problema de exibição do workflow com transições de saída após uma atividade Test. (NEO-12727)
* Agora permitimos a exclusão de registros fictícios criados no Microsoft Dynamics durante o fluxo de trabalho de importação.
* Permissões aprimoradas para executar o pacote de zona de segurança ao usar a conta interna.

## ![](assets/do-not-localize/red_2.png) Versão 19.1 - Build 9026{#release-19-1-build-9026}

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
   <td> <p>Para aumentar a eficiência do seu trabalho como usuário administrador, gerencie as configurações dos servidores SFTP monitorando o armazenamento, adicione endereços IP à lista de permissões e instale chaves SSH para cada instância. Observe que o Painel de Controle está disponível apenas para clientes hospedados no AWS a partir de hoje (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">login através da Experience Cloud hoje</a>).</p> <p>Para obter mais informações, consulte a <a href="https://docs.adobe.com/content/help/pt-BR/control-panel/using/control-panel-home.translate.html">documentação detalhada</a> e o <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/control-panel/control-panel-overview.html">vídeo de instruções</a>. </p><p>Observação: não é necessário atualizar para a build mais recente do Campaign para acessar o Painel de Controle.</p> </td> 
  </tr> 
    <tr> 
   <td> Trilha de auditoria<br /> </td> 
   <td> <p>Como administrador, aumente a produtividade monitorando e gerenciando alterações feitas na instância do Adobe Campaign Classic. A Trilha de Auditoria registrará ações feitas nos Schemas de origem, Workflows e Opções. Você pode ver rapidamente se um elemento foi criado, modificado ou excluído.</p><p>Para obter mais informações, consulte a <a href="../../production/using/audit-trail.md">documentação detalhada</a> e o <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/monitoring/audit-trail.html">vídeo de instruções</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Grade de Proteção, Robustez e Escalabilidade<br /> </td> 
   <td> Uma série de melhorias foi adicionada ao Campaign Classic. As melhorias de grade de proteção, robustez e escalabilidade estão listadas abaixo.<br /> </td> 
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

**Aprimoramentos de grade de Proteção, robustez e escalabilidade**

* Otimização do uso da sequência Lifespan - XtkNewId: as tabelas mais antigas foram movidas da sequência xtkNewId para sequências dedicadas. [Leia mais](https://helpx.adobe.com/br/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* FDA sobre HTTP v2: FDA sobre protocolo HTTP é amplamente usado em implantações híbridas, especialmente para recuperação de broadLog e preparação de delivery. Robustez foi aprimorada para evitar problemas de rede e possíveis erros como recuperação e envio de dados. Isso requer que as builds nas duas extremidades da conexão estejam atualizados, caso contrário, o protocolo antigo ainda será usado.
* Workflow de rastreamento: a robustez do workflow de rastreamento foi aprimorada. Vários problemas relacionados a inserções/atualizações de log de rastreamento e personalização de rastreamento de URL foram corrigidos. Além disso, o workflow de rastreamento agora detecta problemas de log de rastreamento que podem levar a erros e interromper o workflow. Esses problemas agora são descartados e não processados.
* Workflow de limpeza: o workflow de limpeza foi aprimorado para evitar possíveis erros e interrupções. Isso otimiza o tamanho e o desempenho do banco de dados.
* Imagens incorporadas em mensagens transacionais: adicionamos o suporte completo de imagens incorporadas em mensagens transacionais, para evitar possíveis falhas ou ausência de imagens.
* Tamanho do banco de dados - XtkJobLog: um mecanismo de limpeza foi adicionado a essa tabela. Isso tem um impacto positivo no tamanho do banco de dados.
* Arquivamento do Cco: os parâmetros padrão para arquivamento do Cco foram alterados para aumentar a velocidade do arquivamento. [Leia mais](../../installation/using/email-archiving.md#parameters)
* Atualização da estrutura do banco de dados: as solicitações SQL geradas pelo Assistente de atualização da estrutura do banco de dados foram aprimoradas para execução mais rápida.
* Grades de proteção para ações do operador: várias grades de proteção foram implementadas para impedir que os operadores executem ações que poderiam afetar a integridade da plataforma. Os esquemas internos não podem mais ser excluídos pela interface. Além disso, o XML de origem do workflow não pode mais ser editado por usuários não administradores.
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
