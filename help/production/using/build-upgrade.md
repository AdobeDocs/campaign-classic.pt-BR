---
product: campaign
title: Introdução a atualizações de build
description: Saiba mais sobre as principais etapas para atualizar para uma nova build
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '2355'
ht-degree: 4%

---

# Atualização de uma build{#performing-a-build-upgrade}



Esta seção fornecerá uma apresentação detalhada do processo de atualização e das etapas para identificar e resolver conflitos.

A atualização da build deve ser realizada com cautela, seus impactos devem ser totalmente considerados com antecedência e o procedimento deve ser concluído com um alto nível de disciplina. Para garantir uma atualização bem-sucedida, verifique se apenas usuários especialistas executam as etapas descritas abaixo. Além disso, recomendamos entrar em contato com [Atendimento ao cliente Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) antes de iniciar qualquer atualização.

Os seguintes pré-requisitos são necessários:

* Noções básicas sobre a arquitetura do Campaign
* Conhecimento sobre sistemas e servidor
* Direitos e permissões administrativas

Você pode encontrar mais informações nestas seções: [Atualização do Adobe Campaign](../../production/using/upgrading.md), [Migração para uma nova versão](../../migration/using/about-migration.md).

Para instâncias hospedadas e híbridas, você deve solicitar a atualização de build para a equipe de operações técnicas do Adobe. Para obter mais informações, consulte a seção Perguntas frequentes na parte inferior desta página. Consulte também o [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md).

## Preparar a atualização

![](assets/do-not-localize/icon_planification.png)

Antes de iniciar a atualização de build, você deve executar uma preparação completa conforme descrito abaixo.
Quando o sistema estiver pronto para ser atualizado, uma atualização de build levará **pelo menos** 2 horas.

O processo de atualização de build requer os seguintes recursos:

* um arquiteto de Adobe - para entender as estruturas do banco de dados (esquemas prontos para uso e qualquer esquema adicional que tenha sido adicionado, designs de campanha e qualquer funcionalidade de caminho crítica que deve ser iniciada e testada em uma ordem específica).
* um gerente de projeto - Nos casos em que a atualização de build envolve várias instâncias diferentes (produção, preparo, teste) e outros servidores e aplicativos de terceiros (bancos de dados, sites SFTP, provedores de serviços de mensagens), ter um gerente de projeto para coordenar todos os testes é considerado uma prática recomendada.
* um administrador do Adobe Campaign - o administrador conhece a configuração do servidor, incluindo, entre outros: segurança, layout da pasta, relatórios e requisitos de importação/exportação. Não execute uma atualização de build sem o administrador.
* um operador do Adobe Campaign (usuário de marketing) - uma atualização bem-sucedida depende da capacidade do usuário de executar suas tarefas diárias com êxito. Por isso, sempre inclua pelo menos um de seus operadores diários no teste dos servidores atualizados.

### Planejamento

Estes são os pontos principais sobre como planejar uma atualização de build:

1. Reserve pelo menos 2 horas para a atualização.
1. Distribuir detalhes de contato para o Adobe e a equipe do cliente.
1. Para instâncias hospedadas: o Adobe e a equipe do cliente coordenarão o tempo da atualização e quem executará.
1. Para instâncias no local: a equipe do cliente gerencia todo o processo - se a assistência no teste de fluxos de trabalho personalizados e lógica de entrega for necessária, os serviços de consultoria deverão ser oferecidos.
1. Determine e confirme para qual versão do Adobe Campaign você deseja atualizar. Consulte o [Notas de versão do Adobe Campaign Classic](../../rn/using/rn-overview.md).
1. Confirme posse de executáveis de atualização.

### Principais pessoas

O processo de atualização de build requer que as seguintes pessoas estejam envolvidas:

* arquiteto de Adobe: para arquiteturas hospedadas ou híbridas, o arquiteto deve entrar em contato com o Atendimento ao cliente da Adobe Campaign.

* Gerente de projetos:
   * para instalações no local: o líder de projeto interno do cliente lidera a atualização e gerencia testes de ciclo de vida.

   * para instalação hospedada: a equipe de hospedagem fará uma parceria com a equipe de Atendimento ao cliente da Adobe Campaign e o cliente para coordenar a linha do tempo de atualização para todas as instâncias.

* Administrador do Adobe Campaign:
   * para instalações no local: o administrador executa a atualização.

   * para instalações hospedadas: a equipe de hospedagem realiza a atualização.

* Operador do Adobe Campaign\usuário de marketing: o operador executa testes em instâncias de desenvolvimento, teste e produção.

### Preparar a atualização da build

Antes de iniciar a atualização de build, os clientes locais precisam executar a seguinte preparação:

1. Certifique-se de que qualquer trabalho de desenvolvimento possa ser exportado antes da atualização, exporte como pacotes.

1. Executar um backup completo dos bancos de dados para todas as instâncias dos ambientes de origem e de destino.

1. Obtenha a versão mais recente do seu [arquivo de configuração do servidor](../../installation/using/the-server-configuration-file.md).

1. [Baixar a build mais recente](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html). [Saiba mais](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=pt-BR).

Você também precisa saber todas as [linhas de comando úteis](../../installation/using/command-lines.md) antes de iniciar uma atualização de build:

* **despejo nlserver**: lista processos em execução
* **nlserver dump - quem**: lista as sessões ativas do cliente
* **monitor nlserver - ausente**: lista propriedades ausentes
* **nlserver start process@instance-name**: inicia um processo
* **nlserver stop process@instance-name**: interrompe um processo
* **nlserver restart process@instance-name**: reinicia um processo
* **desligamento do nlserver**: interrompe todos os processos do Campaign
* **nlserver watchdog -svc**: inicia o watchdog (somente UNIX)

## Executar a atualização

![](assets/do-not-localize/icon_process.png)

Os procedimentos abaixo são executados somente por **no local** clientes. Para clientes hospedados, a equipe de hospedagem cuida disso. Para atualizar o Adobe Campaign para um novo build, o procedimento detalhado é descrito abaixo.

### Duplicação do ambiente

Esta é a forma como você duplica um ambiente Adobe Campaign para restaurar um ambiente de origem para um ambiente de destino, resultando em dois ambientes de trabalho idênticos.

Para fazer isso, siga as etapas abaixo:

1. Crie uma cópia dos bancos de dados em todas as instâncias no ambiente de origem.

1. Restaurar essas cópias em todas as instâncias do ambiente de destino.

1. Execute o **nms:freezeInstance.js** script de cauterização no ambiente do target antes de iniciá-lo. Isso interromperá a interação de todos os processos com o exterior: logs, rastreamento, deliveries, workflows da campanha etc.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Verifique a cauterização, como se segue:

   * Verifique se a única parte do delivery é aquela com a qual a ID está definida **0**:

      ```
      SELECT * FROM neolane.nmsdeliverypart;
      ```

   * Verifique se a atualização do status do delivery está correta:

      ```
      SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
      ```

   * Verifique se a atualização do status do workflow está correta:

      ```
      SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
      SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
      ```

### Desligar serviços

Para substituir todos os arquivos pela nova versão, é necessário que todas as instâncias do nlserverservice sejam encerradas.

1. Encerre os seguintes serviços:

   * Serviços Web (IIS): **iisreset /stop**
   * Serviço Adobe Campaign: **net stop nlserver6**

   >[!NOTE]
   >
   >Verifique se o servidor de redirecionamento (webmdl) está parado, para que o arquivo nlsrvmod.dll usado pelo IIS possa ser substituído pela nova versão.

1. Valide se nenhuma tarefa está ativa executando o **despejo nlserver** comando. Se não houver tarefas, a saída será semelhante ao seguinte:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Verifique o Gerenciador de tarefas do Windows para confirmar se todos os processos foram interrompidos.

### Atualizar o aplicativo do servidor do Adobe Campaign

1. Execute o **Setup.exe** arquivo. Se precisar baixar este arquivo, acesse [o Centro de download](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html).

1. Selecione o modo de instalação: **Atualizar** ou **Reparar**.

1. Clique em **Next**.

1. Clique em **Concluir**: o programa de instalação copia os novos arquivos.

1. Quando a operação estiver concluída, clique em **Concluir**.

### Sincronizar recursos

1. Abra a linha de comando.

1. Executar **nlserver config -postupgrade -allinstances** para executar o seguinte:

   * Sincronizar recursos
   * Atualizar esquemas
   * Atualizar o banco de dados

   >[!NOTE]
   >
   >Esta operação só deve ser executada uma vez e somente em um servidor de aplicativos nlserverweb.

   Para sincronizar apenas um banco de dados, execute o seguinte comando:

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Verifique se a sincronização gerou erros ou avisos.

### Reiniciar serviços

Os seguintes serviços precisam ser reiniciados:

* Serviços Web (IIS): **issreset /start**
* Serviço Adobe Campaign: **net start nlserver6**

### Atualização dos consoles do cliente

O console do cliente deve estar na mesma build da instância do servidor.

Na máquina em que o servidor de aplicativos do Adobe Campaign está instalado (nlserverweb), baixe e copie o arquivo:

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

Na próxima vez que os consoles do cliente estiverem conectados, uma janela informará os usuários sobre a disponibilidade de uma nova atualização e oferecerá a eles a possibilidade de baixá-la e instalá-la.

### Tarefas adicionais específicas

Algumas configurações exigem tarefas adicionais específicas para atualizar para uma nova build.

#### Mensagens transacionais

Quando as mensagens transacionais (Centro de mensagens) estão ativadas na instância do Campaign, é necessário executar as seguintes etapas adicionais para atualizar:

1. Atualize o servidor de produção do Centro de mensagens para a versão escolhida.
1. Execute os scripts de pós-atualização.
1. Execute testes e verifique se os emails foram recebidos com êxito por meio da instância de produção do Centro de mensagens.
1. Atualizar clientes e limpar o cache.
1. Exportar pacotes:
   * Exportar pacotes usando a ferramenta de exportação de pacotes do cliente
   * Importar pacote de esquema
   * Desconectar e reconectar o cliente
   * Atualizar banco de dados
   * Desconectar e reconectar
   * Importar pacote de administração
   * Importar pacote de conteúdo
   * Importar pacote de gerenciamento de conteúdo
   * Desconectar e reconectar
   * Executar uma verificação rápida de integridade dos fluxos de trabalho

1. Publique modelos do Centro de mensagens para garantir que a interface entre os servidores e a instância do Centro de mensagens esteja funcionando.
1. Execute testes para garantir que os emails sejam recebidos com êxito por meio da instância de produção do Centro de mensagens.
1. Execute testes de workflow na produção para garantir que os deliveries sejam recebidos.

#### Mid-sourcing

No contexto de um ambiente mid-sourcing, é necessário executar estas etapas adicionais para atualizar:

1. Contato [Atendimento ao cliente Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para coordenar a atualização do servidor Mid-Sourcing.
1. Validar se a versão foi atualizada executando um link de teste. Por exemplo:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>O servidor Mid-Sourcing sempre deve executar a mesma versão (ou mais recente) dos servidores de marketing.

## Em caso de conflito

### Identificar conflitos

Você precisa verificar o resultado da sincronização. Esse procedimento só é executado por clientes no local. Para clientes hospedados, a equipe de hospedagem cuida disso. Há duas maneiras de exibir o resultado da sincronização:

Na interface de linha de comando, os erros são materializados por uma divisa tripla &#39;>>>&#39; e a sincronização é interrompida automaticamente. Os avisos são materializados por uma divisa dupla &#39;>>&#39; e devem ser resolvidos quando a sincronização estiver concluída. No final da pós-atualização, um resumo é exibido no prompt de comando. Ele pode ter esta aparência:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Se o aviso aborda um conflito de recursos, é necessária atenção do usuário para resolvê-lo.

A variável **postupgrade_ServerVersionNumber_TimeOfPostUpgrade.log** o arquivo contém o resultado da sincronização. Ela está disponível por padrão no seguinte diretório: **installationDirectory/var/`<instance-name>`/postupgrade**. Os erros e avisos são indicados pelos atributos de erro e aviso.

### Analisar conflitos

**Como um conflito é encontrado?**

Conflitos podem ser encontrados no postupgrade.log no servidor em questão ou na interface do cliente do Campaign (Administration > Configuration > Package management > Edit conflicts).

O documento com o identificador &quot;stockOverview&quot; e o tipo &quot;nms:webApp&quot; está em conflito com a nova versão.

Se um conflito for encontrado, verifique se as seguintes condições são compatíveis:

* O objeto foi modificado ou personalizado pelo cliente?
* O objeto foi alterado no produto?

Se nenhuma dessas condições se aplicar, isso será um falso positivo. Se ambas as condições se aplicarem, um conflito real foi encontrado.

**O objeto foi modificado pelo cliente?**

1. Identifique o objeto conflitante.
1. Pergunte ao cliente se ele modificou o objeto.
1. Há algo incomum com o objeto?
1. A data da última modificação está definida no código do objeto?
1. Examine o código XML do conflito para atributos &quot;_conflict&quot;. Parece uma personalização?

**O objeto foi alterado na nova build?**

1. Algum &quot;suspeito de sempre&quot;? Aplicativos web ou relatórios incorporados (por exemplo: &quot;deliveryValidation&quot;, &quot;deliveryOverview&quot;, &quot;budget&quot;).
1. Examine os logs de alteração para verificar se há atualizações.
1. Pergunte aos especialistas da Adobe Campaign.
1. Execute um comando &quot;diff&quot; no código.

### Resolver um conflito

Para resolver conflitos, aplique o seguinte processo:

1. No explorador do Adobe Campaign, acesse **Administração > Configuração > Gerenciamento de pacotes > Editar conflitos**.

1. Selecione o conflito que deseja resolver na lista.
Há três opções para resolver conflitos: **Aceitar a nova versão**, **Manter a versão atual**, **Mesclar o código (e declarar como resolvido)**, **Ignorar o conflito (não recomendado)**.

**Quando posso aceitar a nova versão?**

* Se quiser os recursos padrão.
* Se você não tiver personalizações (todas as personalizações serão removidas)

**Quando posso manter a versão atual?**

* Se você tiver personalizações
* Se não quiser mesclar
* Se você não precisar de correções no objeto conflitante da atualização

**Quando executar uma mesclagem?**

* Somente formulários, relatórios e aplicativos Web podem ser mesclados.
* Algumas mesclagens secundárias podem ser resolvidas sem compreender o código.
* Mesclagens mais complexas devem ser executadas por alguém com as habilidades e os conhecimentos apropriados.
* Consulte [Executar uma mesclagem](#perform-a-merge).

**E se eu ignorar os conflitos?**

* O conflito permanecerá
* O objeto não será atualizado
* Impactos a longo prazo: incompatibilidades de versão, o cliente não se beneficiará das correções de erros.

>[!IMPORTANT]
>É altamente recomendável resolver conflitos.

### Executar uma mesclagem{#perform-a-merge}

Há diferentes tipos de mesclagens:

1. Mesclagem fácil: elementos personalizados e novos são pequenos e não relacionados, e não é necessário codificar.
1. Sem alterações: aceitar a nova versão, somente a data da última atualização alterada, somente comentários, guias, espaços ou novas linhas. Exemplo: salvamento acidental.
1. Mudanças triviais: apenas uma linha mudou. Exemplo: xpathToLoad
1. Mesclagem complexa: quando a codificação é necessária. As habilidades de desenvolvimento são necessárias. Consulte [Mesclagens complexas](#complex-merges).

#### Como mesclar?

1. Obtenha todas as três versões: a versão original, a nova versão e a versão personalizada.
1. Execute um comando &quot;diff&quot; entre as versões original e nova.
1. Isole as alterações.
1. Se não houver alterações, resolva mantendo a versão atual.

#### Onde encontrar o código?

1. O código incorporado é armazenado em arquivos XML na pasta datakit. Localize o arquivo XML que corresponde ao objeto conflitante. Exemplo: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Recupere a versão original: por meio da [Centro de download](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html) instalação não atualizada do produto.
1. Recupere a nova versão: por meio da [Centro de download](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html) ou os arquivos instalados do cliente.
1. Recuperar a versão personalizada: recupere o código-fonte do objeto no cliente do Campaign.

### Como fazer a diferença?

1. Instale um editor de texto ou mesclagem, por exemplo, Notepad ++, AraxisMerge, WinMerge.
1. Abra o arquivo original e o novo arquivo no editor.
1. Execute o comando diff (compare os dois arquivos).
1. Identifique as diferenças.

### Como mesclar?

1. Comece a partir da versão personalizada.
1. Aplique as alterações.
1. Resolva o conflito declarando-o como resolvido.
1. Verifique se há não regressões.

Se você optar por resolver o conflito manualmente, proceda da seguinte maneira:

1. Na seção inferior da janela, procure pela variável **_conflict_string_** para localizar as entidades com conflitos. A entidade instalada com a nova versão contém o novo argumento, a entidade que corresponde à versão anterior contém o argumento personalizado.
1. Exclua a versão que não deseja manter. Exclua o **_argumento_de_conflito_** string da entidade que você está mantendo.
1. Vá para o conflito que você resolveu. Clique em **Ações** e selecione **Declarar como resolvido**.
1. Salve as alterações: o conflito agora está resolvido.

#### Mesclagens complexas{#complex-merges}

1. Entenda o que a alteração faz: reverter a engenharia das alterações, examinar os logs de alteração e acompanhar com especialistas da Adobe Campaign.
1. Decida o que fazer com a alteração.
1. Entenda o que as personalizações fazem: reverter a engenharia das alterações

Estas são as etapas para executar uma mesclagem complexa:

1. Copiar bits de código do conjunto de alterações
1. Colar na versão personalizada
1. Teste de não regressão da personalização
1. Teste de função das alterações
1. Realizar teste de aceitação do usuário
1. Desempenho no ambiente de teste


>[!IMPORTANT]
>Habilidades de desenvolvimento são necessárias para executar mesclagens complexas.

**Tópicos relacionados**

* [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md)
* [Notas de versão do Campaign Classic](../../rn/using/rn-overview.md)
* [Opções de ajuda e suporte para o Campaign Classic](../../support.md)
* [Programa de atualização anual do Campaign](../../rn/using/rn-overview.md)
