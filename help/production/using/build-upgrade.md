---
product: campaign
title: Introdução às atualizações de build
description: Saiba mais sobre as principais etapas para atualizar para uma nova build
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2353'
ht-degree: 4%

---

# Atualização de uma build{#performing-a-build-upgrade}

![](../../assets/v7-only.svg)

Esta seção fornecerá uma apresentação detalhada sobre o processo de atualização e as etapas para identificar e resolver conflitos.

A atualização da build deve ser realizada com cuidado, seus impactos devem ser totalmente considerados previamente e o procedimento deve ser concluído com um alto nível de disciplina. Para garantir uma atualização bem-sucedida, verifique se apenas usuários especialistas executam as etapas descritas abaixo. Além disso, é altamente recomendável entrar em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/using/support-for-experience-cloud.html) antes de iniciar qualquer atualização.

Os seguintes pré-requisitos são necessários:

* Noções básicas da arquitetura do Campaign
* Conhecimento dos sistemas e do servidor
* Direitos e permissões administrativas

Você pode encontrar mais informações nestas seções: [Atualização do Adobe Campaign](../../production/using/upgrading.md), [Migração para uma nova versão](../../migration/using/about-migration.md).

Para instâncias hospedadas e híbridas, você deve solicitar a atualização de compilação para a equipe de Operações Técnicas do Adobe. Para obter mais informações, consulte a seção Perguntas frequentes na parte inferior desta página. Consulte também a [perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md).

## Preparar a atualização

![](assets/do-not-localize/icon_planification.png)

Antes de iniciar a atualização da build, você deve executar uma preparação completa conforme descrito abaixo.
Quando o sistema estiver pronto para ser atualizado, uma atualização de build será necessária **pelo menos** 2 horas.

O processo de atualização de build requer os seguintes recursos:

* um arquiteto do Adobe - para entender as estruturas do banco de dados (esquemas prontos para uso e quaisquer esquemas adicionais que foram adicionados, designs de campanha e qualquer funcionalidade de caminho crítico que deve ser iniciada e testada em uma ordem específica).
* um gerente de projeto - Caso a atualização de build envolva várias instâncias diferentes (produção, armazenamento temporário, testes) e outros servidores e aplicativos de terceiros (bancos de dados, sites SFTP, provedores de serviços de mensagens), a prática recomendada é ter um gerente de projeto para coordenar todos os testes.
* um administrador do Adobe Campaign - seu administrador conhece a configuração do servidor, incluindo, entre outros: requisitos de segurança, layout de pastas, relatórios e importação/exportação. Não execute uma atualização de build sem o administrador.
* um operador do Adobe Campaign (usuário de marketing) - uma atualização bem-sucedida depende da capacidade do usuário de executar suas tarefas diárias com êxito. Por isso, sempre inclua pelo menos um dos operadores diários nos testes dos servidores atualizados.

### Planejamento

Estes são os principais pontos sobre como planejar uma atualização de build:

1. Reserve pelo menos 2 horas para a atualização.
1. Distribua os detalhes de contato para a Adobe e a equipe do cliente.
1. Para instâncias hospedadas: A equipe do Adobe e do cliente coordenará o tempo da atualização e quem será executado.
1. Para instâncias locais: a equipe do cliente gerencia todo o processo - se for necessária assistência em testes de workflows personalizados e lógica de delivery, os serviços de consultoria devem ser incluídos.
1. Determine e confirme para qual versão do Adobe Campaign você deseja atualizar - consulte o [Notas de versão do Adobe Campaign Classic](../../rn/using/rn-overview.md).
1. Confirme a posse dos executáveis de atualização.

### Pessoas-chave

O processo de atualização de build requer as seguintes pessoas envolvidas:

* Adobe architecture: para arquiteturas hospedadas ou híbridas, o arquiteto deve coordenar com o Adobe Campaign Client Care.

* Gerente de projeto:
   * para instalações no local: o Líder do Projeto interno do cliente lidera a atualização e gerencia os testes do ciclo de vida.

   * para instalação hospedada: a equipe de hospedagem fará parceria com a equipe de Atendimento ao cliente da Adobe Campaign e com o cliente para coordenar o cronograma de atualização de todas as instâncias.

* Administrador do Adobe Campaign:
   * para instalações no local: o administrador executa a atualização.

   * para instalações hospedadas: a equipe de hospedagem realiza a atualização.

* Operador\usuário de marketing do Adobe Campaign: o operador executa testes em instâncias de desenvolvimento, teste e produção.

### Preparar a atualização de build

Antes de iniciar a atualização da build, os clientes locais precisam executar a seguinte preparação:

1. Certifique-se de que qualquer trabalho de desenvolvimento possa ser exportado antes da atualização, exporte como pacotes.

1. Faça um backup completo dos bancos de dados para todas as instâncias dos ambientes de origem e de destino.

1. Obtenha a versão mais recente de seu [arquivo de configuração do servidor](../../installation/using/the-server-configuration-file.md).

1. [Baixe a build mais recente](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html). [Saiba mais](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=pt-BR).

Você também precisa saber todas as [linhas de comando úteis](../../installation/using/command-lines.md) antes de iniciar uma atualização de compilação:

* **pdump nlserver**: listas executando processos
* **nlserver pdump -who**: lista sessões ativas do cliente
* **nlserver monitor -missing**: lista propriedades ausentes
* **nlserver start process@instanceName**: inicia um processo
* **nlserver stop process@instanceName**: interrompe um processo
* **nlserver restart process@instanceName**: reinicia um processo
* **desligamento do nlserver**: interrompe todos os processos do Campaign
* **nlserver watchdog -svc**: inicia o watchdog (somente UNIX)

## Executar a atualização

![](assets/do-not-localize/icon_process.png)

Os procedimentos abaixo são executados somente por **no local** clientes. Para clientes hospedados, é atendido pela equipe de hospedagem. Para atualizar o Adobe Campaign para uma nova build, o procedimento detalhado é descrito abaixo.

### Duplicação do ambiente

Veja como duplicar um ambiente do Adobe Campaign para restaurar um ambiente de origem para um ambiente de destino, resultando em dois ambientes de trabalho idênticos.

Para fazer isso, siga as etapas abaixo:

1. Crie uma cópia dos bancos de dados em todas as instâncias no ambiente de origem.

1. Restaure essas cópias em todas as instâncias do ambiente de destino.

1. Execute o **nms:freezeInstance.js** script de cauterização no ambiente de destino antes de iniciá-lo. Isso interromperá a interação de todos os processos com o exterior: logs, rastreamento, deliveries, workflows da campanha etc.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Verifique a cauterização, da seguinte maneira:

   * Verifique se a única parte do delivery é aquela cuja ID está definida como **0**:

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

### Serviços de desligamento

Para substituir todos os arquivos pela nova versão, é necessário que todas as instâncias do nlserverservice sejam encerradas.

1. Desligue os seguintes serviços:

   * Serviços Web (IIS): **iisreset /stop**
   * Serviço Adobe Campaign: **net stop nlserver6**

   >[!NOTE]
   >
   >Certifique-se de que o servidor de redirecionamento (webmdl) esteja parado, para que o arquivo nlsrvmod.dll usado pelo IIS possa ser substituído pela nova versão.

1. Valide se nenhuma tarefa está ativa executando o **pdump nlserver** comando. Se não houver tarefas, a saída deverá ser semelhante ao seguinte:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Verifique o Gerenciador de Tarefas do Windows para confirmar que todos os processos foram interrompidos.

### Atualizar o aplicativo do servidor do Adobe Campaign

1. Execute o **Setup.exe** arquivo. Se precisar baixar esse arquivo, acesse [Centro de download](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html).

1. Selecione o modo de instalação: **Atualizar** ou **Reparar**.

1. Clique em **Next**.

1. Clique em **Concluir**: o programa de instalação copia os novos arquivos.

1. Quando a operação estiver concluída, clique em **Concluir**.

### Sincronizar recursos

1. Abra a linha de comando.

1. Executar **nlserver config -postupgrade -allinStatus** para executar o seguinte:

   * Sincronizar recursos
   * Atualizar schemas
   * Atualizar o banco de dados

   >[!NOTE]
   >
   >Essa operação só deve ser executada uma vez e somente em um servidor de aplicativos nlserverweb.

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

Na próxima vez que os consoles do cliente estiverem conectados, uma janela informará os usuários sobre a disponibilidade de uma nova atualização e oferecerá a possibilidade de baixá-la e instalá-la.

### Tarefas adicionais específicas

Algumas configurações exigem tarefas adicionais específicas para serem atualizadas para uma nova build.

#### Mensagens transacionais

Quando o Transactional Messaging (Message Center) é ativado na instância do Campaign, é necessário executar essas etapas adicionais para atualizar:

1. Atualize o servidor de produção do Centro de Mensagens para a versão escolhida.
1. Execute os scripts postupgrade.
1. Execute testes e garanta que os emails sejam recebidos com êxito por meio da instância de produção do Centro de Mensagens.
1. Atualize clientes e limpe o cache.
1. Exportar pacotes:
   * Exportar pacotes usando a ferramenta de exportação de pacotes do cliente
   * Importar pacote de esquema
   * Desconectar e reconectar o cliente
   * Atualizar banco de dados
   * Desconectar e reconectar
   * Importar pacote de administrador
   * Importar pacote de conteúdo
   * Importar pacote de Gestão de Conteúdo
   * Desconectar e reconectar
   * Execute uma verificação rápida dos workflows

1. Publique modelos do Centro de Mensagens para garantir que a interface entre servidores e a instância do Centro de Mensagens esteja funcionando.
1. Execute testes para garantir que os emails sejam recebidos com êxito pela instância de produção do Centro de Mensagens.
1. Execute testes de workflow em produção para garantir que os deliveries sejam recebidos.

#### Mid-sourcing

No contexto de um ambiente de mid-sourcing, é necessário executar essas etapas adicionais para atualizar:

1. Contato [Atendimento ao cliente do Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) coordenar a atualização do servidor Mid-sourcing.
1. Valide se a versão foi atualizada executando um link de teste. Por exemplo:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>O servidor Mid-sourcing deve sempre executar a mesma versão (ou mais recente) dos servidores de marketing.

## Em caso de conflitos

### Identificar conflitos

Você precisa verificar o resultado da sincronização. Esse procedimento só é executado por clientes locais. Para clientes hospedados, é atendido pela equipe de hospedagem. Há duas maneiras de visualizar o resultado da sincronização:

Na interface da linha de comando, os erros são materializados por uma divisa tripla &#39;>>>&#39; e a sincronização é interrompida automaticamente. Os avisos são materializados por uma divisa dupla &#39;>>&#39; e devem ser resolvidos assim que a sincronização for concluída. No final do postupgrade, um resumo é exibido no prompt de comando. Pode ser assim:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Se o aviso se referir a um conflito de recursos, é necessário prestar atenção ao usuário para resolvê-lo.

O **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** O arquivo contém o resultado da sincronização. Está disponível por padrão no seguinte diretório: **installationDirectory/var/instanceName/postupgrade**. Erros e avisos são indicados pelos atributos de erro e aviso.

### Analisar conflitos

**Como se encontra um conflito?**

Os conflitos podem ser encontrados no postupgrade.log no servidor em questão ou na interface do cliente Campaign (Administration > Configuration > Package management > Edit conflicts).

O documento com o identificador &quot;stockOverview&quot; e o tipo &quot;nms:webApp&quot; estão em conflito com a nova versão.

Se um conflito for encontrado, verifique se as seguintes condições correspondem:

* O objeto foi modificado ou personalizado pelo cliente?
* O objeto foi alterado no produto?

Se nenhuma dessas condições se aplicar, isso é um falso positivo. Se ambas as condições se aplicarem, foi encontrado um verdadeiro conflito.

**O objeto foi modificado pelo cliente?**

1. Identifique o objeto conflitante.
1. Pergunte ao cliente se ele modificou o objeto.
1. Existe algo incomum com o objeto?
1. A data da última modificação está definida no código do objeto?
1. Examine o código XML do conflito para os atributos &quot;_conflict&quot; . Parece uma personalização?

**O objeto foi alterado na nova build?**

1. Algum &quot;suspeito habitual?&quot; Aplicativos ou relatórios da Web incorporados (por exemplo: &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. Examine os logs de alterações para verificar se há atualizações.
1. Pergunte aos especialistas da Adobe Campaign.
1. Execute um &quot;diff&quot; no código.

### Resolver um conflito

Para resolver conflitos, aplique o seguinte processo:

1. No navegador Adobe Campaign, acesse **Administração > Configuração > Gerenciamento de pacotes > Editar conflitos**.

1. Selecione o conflito que deseja resolver na lista.
Existem três opções para resolver conflitos: **Aceite a nova versão**, **Manter a versão atual**, **Mesclar o código (e declarar como resolvido)**, **Ignorar o conflito (não recomendado)**.

**Quando posso aceitar a nova versão?**

* Se quiser os recursos padrão.
* Se você não tiver personalizações (todas as personalizações serão removidas)

**Quando posso manter a versão atual?**

* Se você tiver personalizações
* Se não quiser mesclar
* Se não precisar de correções no objeto conflitante da atualização

**Quando executar uma mesclagem?**

* Somente formulários, relatórios e aplicativos da Web podem ser mesclados.
* Algumas pequenas mesclagens podem ser resolvidas sem a compreensão do código.
* As mesclagens mais complexas devem ser realizadas por alguém com as habilidades e habilidades apropriadas.
* Consulte [Executar uma mesclagem](#perform-a-merge).

**E se eu ignorar os conflitos?**

* O conflito continuará
* O objeto não será atualizado
* Impactos a longo prazo: incompatibilidades de versão, o cliente não se beneficiará das correções de erros.

>[!IMPORTANT]
>É altamente recomendável resolver conflitos.

### Executar uma mesclagem{#perform-a-merge}

Existem diferentes tipos de mesclagens:

1. Mesclagem fácil: os elementos personalizados e novos são pequenos e não estão relacionados e não há necessidade de codificação.
1. Sem alterações: aceitar nova versão, somente a última data de atualização foi alterada, apenas comentários, guias, espaços ou novas linhas. Exemplo: salvamento acidental.
1. Alterações triviais: somente uma linha foi alterada. Exemplo: xpathToLoad
1. Mesclagem complexa: quando a codificação é necessária. São necessárias competências de desenvolvimento. Consulte [Mesclagens complexas](#complex-merges).

#### Como mesclar?

1. Obtenha todas as três versões: a versão original, a nova versão e a personalizada.
1. Execute um &quot;diff&quot; entre as versões original e nova.
1. Isole as alterações.
1. Se não houver alterações, resolva mantendo a versão atual.

#### Onde encontrar o código?

1. O código incorporado é armazenado em arquivos XML na pasta do datakit. Encontre o arquivo XML que corresponde ao objeto conflitante. Exemplo: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Recuperar a versão original: através da [Centro de download](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) ou outra instalação não atualizada do produto.
1. Recupere a nova versão: através da [Centro de download](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) ou os arquivos instalados do cliente.
1. Recuperar a versão personalizada: recupere o código-fonte do objeto no cliente do Campaign.

### Como fazer um diff?

1. Instale um editor de texto ou mesclagem, por exemplo, Notepad ++, AraxisMerge, WinMerge.
1. Abra o arquivo original e o novo no editor.
1. Execute o diff (compare os dois arquivos).
1. Identifique quaisquer diferenças.

### Como mesclar?

1. Comece a partir da versão personalizada.
1. Aplique as alterações.
1. Resolva o conflito declarando-o como resolvido.
1. Verifique se há não regressões.

Se você optar por resolver o conflito manualmente, proceda da seguinte maneira:

1. Na seção inferior da janela, procure pelo **_conflict_string_** para localizar as entidades com conflitos. A entidade instalada com a nova versão contém o novo argumento, a entidade que corresponde à versão anterior contém o argumento personalizado .
1. Exclua a versão que não deseja manter. Exclua o **_argumento_de_conflito_** da entidade que você está mantendo.
1. Vá para o conflito que você resolveu. Clique no botão **Ações** e selecione **Declarar como resolvido**.
1. Salve as alterações: o conflito está agora resolvido.

#### Mesclagens complexas{#complex-merges}

1. Entenda o que a alteração faz: faça engenharia reversa das alterações, examine os logs de alterações e acompanhe os especialistas da Adobe Campaign.
1. Decida o que fazer com a mudança.
1. Entenda o que as personalizações fazem: engenharia reversa das alterações

Estas são as etapas para executar uma mesclagem complexa:

1. Copiar bits do código do conjunto de alterações
1. Cole na versão personalizada
1. Teste para não regressões da personalização
1. Teste para função de alterações
1. Realizar teste de aceitação do usuário
1. Executar no ambiente de teste


>[!IMPORTANT]
>Habilidades de desenvolvimento são necessárias para realizar mesclagens complexas.

**Tópicos relacionados**

* [Perguntas frequentes de atualização de build](../../platform/using/faq-build-upgrade.md)
* [Notas de versão do Campaign Classic](../../rn/using/rn-overview.md)
* [Opções de ajuda e suporte para o Campaign Classic](../../support.md)
* [Programa do [!DNL Gold Standard]](../../rn/using/gs-overview.md)
