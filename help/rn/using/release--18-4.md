---
title: Versão 18.4
seo-title: Versão 18.4
description: Versão 18.4
seo-description: null
page-status-flag: never-activated
uuid: d132570e-20e6-4550-95bd-176701f43b19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 4dc87ff3-eb6a-40ac-97ee-00b64cd7718d
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '2263'
ht-degree: 100%

---


# Versão 18.4{#release-18-4}

## Versão 18.4.5 - Build 8937{#release-18-4-5-build-8937}

21 de novembro de 2018

**Aprimoramentos**

* Corrigidos vários problemas ao executar workflows usando MySQL na FDA. (NEO-11652)
* Correção de um problema que fazia com que uma parte da população de delivery permanecer no estado pendente, em casos específicos. (NEO-11336)
* Correção de um problema intermitente com a resposta automática do SMS. (NEO-11811)
* Correção de um problema de esgotamento de ID ao usar seed addresses em um delivery. (NEO-11842)
* Correção de um erro de sintaxe ao executar uma classificação em uma atividade do workflow de enriquecimento. (NEO-11394)
* Correção de um problema que poderia causar falha no servidor Web ao reiniciar o IIS. (NEO-10862)
* Correção de um problema que poderia causar falha no workflow de rastreamento após uma atualização de compilação (FDA - SQL). (NEO-11635)
* Correção de um problema que poderia causar perda de dados da lista de workflows. (NEO-11696)
* Correção de um problema de desempenho ao enviar notificações por push. (NEO-11787)
* Correção de um problema que impedia que o rastreamento Web funcionasse para domínios &quot;com.au&quot; (NEO-4385).
* Correção de um problema de congelamento do cliente que pode ocorrer ao usar workflows complexos. (NEO-11847)
* Correção de um erro Oracle ao salvar um novo delivery após selecionar um elemento de um schema específico (NEO-11682).
* Correção de um problema ao realizar query em um campo contendo caracteres com acentos (FDA/Teradata). A conta externa agora permite alterar a codificação utilizada para se comunicar com o driver Teradata. (NEO-11818).
* Correção de um problema de rastreamento ao transmitir URLs em variáveis adicionais em uma notificação por push que poderia resultar em dados mal formatados ou incorretos recebidos pelo aplicativo móvel. (NEO-11468, NEO-11960)
* Correção de um problema que causava um problema de exibição ao usar uma distribuição de valores com um link 1:N. (NEO-11820)
* Correção de um problema que impedia o funcionamento de carregamento em massa no Teradata 16.
* Aumento do tamanho do buffer para carimbo de data/hora no Teradata para evitar problemas de encadernação com driver 15.10.
* Melhorou o gerenciamento de índices de nomes longos que podem causar problemas após a atualização.
* Tempo de memória compartilhado aprimorado disponível durante o processamento de crianças menores (MTA).
* Correção de um possível bloqueio no Apache (rastreamento).

## Versão 18.4.4 - Build 8936{#release-18-4-4-build-8936}

1 de agosto de 2018

**Aprimoramentos**

* Os logs de arquivamento de emails foram aprimorados, o que facilita e agiliza a verificação de quais emails foram entregues com êxito ou falharam no arquivamento do Cco. (NEO-10675)
* Correção de um problema que levou à exibição dos IPs do balanceador de carga em vez dos IPs do cliente no rastreamento de broadlogs. (NEO-11295)
* Correção de um erro com codificação LATIN1 ao usar um FDA Connection para um banco de dados PostgreSQL. (NEO-11299)
* Correção de um problema que ocorria ao usar a opção de delivery **[!UICONTROL Prepare the personalization data with a workflow]**. (NEO-11047, NEO-11301)
* Correção de um problema aleatório que fazia com que as propriedades de um delivery fossem substituídas incorretamente. (NEO-11015)
* Correção de um problema ao usar campos calculados em uma atividade de workflow **[!UICONTROL Survey answers]**. (NEO-11382)
* Correção de um problema ao usar dados armazenados em XML em uma atividade de workflow de **[!UICONTROL Survey answers]**. (NEO-10816)
* Correção de um problema ao executar a atualização do servidor com o build 8935.
* Correção de um problema que exibia erros inúteis no log após a atualização quando uma atividade de workflow **[!UICONTROL Survey answers]** não estava totalmente configurada.
* FDA Teradata: correção de um problema com campos incrementados automaticamente e índices em tabelas SQL.

## Versão 18.4.3 - Build 8935{#release-18-4-3-build-8935}

22 de junho de 2018

**Aprimoramentos**

* Correção de um problema de codificação de rastreamento com o Microsoft Edge e o Internet Explorer. (NEO-11257)
* Correção de um problema com a personalização do link de imagem em remessas LINE. (NEO-11077)
* Correção de um problema que impedia o funcionamento correto do mecanismo de geração de sequência de ID. (NEO-11115)
* Correção de um problema que impedia o funcionamento das solicitações de privacidade (GDPR) ao usar um namespace personalizado com uma chave de reconciliação de tipo inteiro. (NEO-11123)
* Correção de um erro que poderia ocorrer ao usar a opção **[!UICONTROL Distribution of values]** em atividades de workflow de **[!UICONTROL Query]**. (NEO-10958)
* Correção de um problema ao sincronizar espaços de oferta da instância de marketing para a instância de interação. (NEO-11162)
* Melhoria do gerenciamento de índices de nomes longos durante a pós atualização.

## Versão 18.4.2 - Build 8932{#release-18-4-2-build-8932}

22 de maio de 2018

**Aprimoramentos**

* Correção de um problema que impedia o funcionamento da atualização do Windows Server.
* Correção de um problema na atividade **[!UICONTROL Survey Result]** ao usar dados armazenados em XML. O relatório foi exibido incorretamente. (NEO-10816)
* Correção de um problema de desempenho que poderia ocorrer com o processo inMail ao usar um servidor de email de devolução. (NEO-10641)
* Correção de um problema de atualização de banco de dados que pode ocorrer ao atualizar mais de 1000 schemas.

## Versão 18.4 - Build 8931{#release-18-4-build-8931}

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
     <li> <p>Direito de Acesso: permite que o Alvo dos Dados receba uma cópia dos seus dados pessoais capturados pelos Controladores de Dados, incluindo potencialmente dados armazenados no Adobe Campaign.</p> </li> 
     <li> <p>Direito de Exclusão: possibilita que o Assunto dos Dados apague seus dados pessoais capturados pelos Controladores de Dados, possivelmente incluindo os dados armazenados no Adobe Campaign.</p> </li> 
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
* Adição da caixa de seleção **Enable SMPP traces** na conta externa para forçar registros de rastreamentos. Para obter mais informações, consulte a [documentação detalhada](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

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
      <node expr="@id"/> <!-- implicitely added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
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
