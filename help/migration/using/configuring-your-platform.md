---
product: campaign
title: Adapte sua configuração
description: Saiba como adaptar sua configuração antes e depois de uma migração para o Campaign v7
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 327f220d6700242308ef3738a38cc95b970e3f46
workflow-type: tm+mt
source-wordcount: '1980'
ht-degree: 4%

---

# Adapte sua configuração{#configuring-your-platform}

![](../../assets/v7-only.svg)

Determinadas alterações importantes no Adobe Campaign v7 exigem configuração específica. Essas configurações podem ser necessárias antes ou depois da migração.

A configuração detalhada a ser executada no Adobe Campaign v7 ao migrar do Campaign v5 ou v6 está disponível em [esta página](general-configurations.md).


Durante a migração, a variável **NmsRecipient** é recriada a partir da definição de schemas. Qualquer alteração feita na estrutura SQL desta tabela fora do Adobe Campaign será perdida.

Exemplo de elementos a serem verificados:

* Se você tiver adicionado uma coluna (ou um índice) ao **NmsRecipient** mas não a detalhou no schema, isso não será salvo.
* O **tablespace** O atributo retorna seus valores por padrão, em outras palavras, os definidos no assistente de implantação.
* Se você tiver adicionado uma exibição de referência ao **NmsRecipient** , você deve excluí-la antes de migrar.


## Antes da migração {#before-the-migration}

Ao migrar para o Adobe Campaign v7, os seguintes elementos devem ser configurados. Esses elementos devem ser abordados antes de iniciar a **pós-atualização**.

* Fusos horários

   Durante uma migração de uma plataforma v5.11, você deve especificar o fuso horário a ser usado durante a pós-atualização.

   Se quiser usar o modo &quot;multi timezone&quot;, consulte [esta seção](../../migration/using/general-configurations.md#time-zones).

   Se você usar o Oracle como um banco de dados, verifique se os arquivos de fuso horário do Oracle foram sincronizados corretamente entre o servidor de aplicativos e o servidor de banco de dados. [Saiba mais](../../migration/using/general-configurations.md#oracle)

* Zonas de segurança

   Por motivos de segurança, a plataforma Adobe Campaign não está mais acessível por padrão: você deve configurar as zonas de segurança, o que requer a coleta dos endereços IP do usuário antes da migração. [Saiba mais](../../migration/using/general-configurations.md#security)

* Sintaxe

   Alguns códigos Javascript podem não ser mais aceitos na versão v7, devido ao uso de um novo interpretador. [Saiba mais](../../migration/using/general-configurations.md#javascript).

   Da mesma forma, uma nova sintaxe é introduzida no Adobe Campaign v7 para substituir a sintaxe baseada em SQLData. Se você usar elementos de código com essa sintaxe, deverá adaptá-los. [Saiba mais](../../migration/using/general-configurations.md#sqldata)

* Senhas

   Você deve configurar o **Administrador** e **Interno** senhas. [Saiba mais](../../migration/using/before-starting-migration.md#user-passwords)

* Estrutura de árvore

   Ao migrar de uma plataforma v5.11, você deve reorganizar as pastas da estrutura de árvore de acordo com as normas do Adobe Campaign v6. [Saiba mais](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).

* Interação

   Se você estiver migrando do Campaign v6.02 e usando o  **Interação** , você deve excluir todas as referências de schema 6.02 que não existem mais no v7. [Saiba mais](../../migration/using/general-configurations.md#interaction)

## Após a migração {#after-the-migration}

Depois de executar **pós-atualização**, verifique e configure os seguintes elementos:

* Mirror pages

   O bloco de personalização da mirror page foi alterado com a v6.x. Essa nova versão melhora a segurança ao acessar essas páginas.

   Se você usou o bloco de personalização v5 em suas mensagens, a exibição da mirror page falhará. O Adobe recomenda usar o novo bloco de personalização ao inserir a mirror page em suas mensagens.

   No entanto, como uma solução alternativa temporária (e como as mirror pages ainda estão ativas), é possível voltar ao bloco de personalização antigo para evitar esse problema, alterando a opção **[!UICONTROL XtkAcceptOldPasswords]** e defina-o como **[!UICONTROL 1]**. Isso não afetará o uso do novo bloco de personalização v6.x.

* Sintaxe

   Se encontrar erros relacionados à sintaxe, durante a pós-atualização, é necessário ativar temporariamente o **allowSQLInjection** na **serverConf.xml** , pois isso dá tempo para reescrever o código. Depois que o código for adaptado, certifique-se de reativar a segurança. [Saiba mais](../../migration/using/general-configurations.md#sqldata)

* Conflitos

   A migração é realizada por meio de uma pós-atualização e os conflitos podem aparecer em relatórios, formulários ou aplicativos da Web. Esses conflitos podem ser resolvidos do console. [Saiba mais](../../migration/using/general-configurations.md#conflicts)

* Tomcat

   Se você personalizou a pasta de instalação, verifique se ela foi atualizada corretamente após a migração. [Saiba mais](../../migration/using/general-configurations.md#tomcat)

* Relatórios

   Todos os relatórios prontos para uso atualmente usam o mecanismo de renderização v6.x. Se você tiver adicionado o código JavaScript nos relatórios, alguns elementos podem ser afetados. [Saiba mais](../../migration/using/general-configurations.md#reports)

* Aplicações web

   Após a pós-atualização, se tiver problemas de conexão com as aplicações web identificadas, ative o **allowUserPassword** e **sessionTokenOnly** nas opções da **serverConf.xml** arquivo. Para evitar qualquer problema de segurança, essas duas opções devem ser reativadas após a resolução do problema. [Saiba mais](../../migration/using/general-configurations.md#identified-web-applications)

   Dependendo do tipo de aplicação web e de sua configuração, você deve executar manipulações adicionais para garantir que funcionem corretamente. [Saiba mais](../../migration/using/general-configurations.md#web-applications)

   Ao migrar de uma plataforma v5.11, configurações adicionais devem ser realizadas. [Saiba mais](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* Zonas de segurança

   Antes de iniciar o servidor, você deve configurar as zonas de segurança. [Saiba mais](../../installation/using/security-zones.md) e [veja aqui](../../migration/using/general-configurations.md#security)

* Fluxos de trabalho

   Se estiver migrando de uma plataforma v5.11, você deverá verificar a pasta de workflows. [Saiba mais](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Rastreamento

   Ao migrar de uma plataforma v5.11, você deve configurar o modo de rastreamento. [Saiba mais](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Interação

   Se você usar **Interação**, você deve ajustar os parâmetros após a migração. [Saiba mais](../../migration/using/general-configurations.md#interaction)

* Painéis

   Se um erro de cliente for exibido, é necessário atualizar seus painéis com o novo código Adobe Campaign v7 ou copiar manualmente os seguintes arquivos da instância v6.02 para a instância v7:

   ```
   v6.02 files and spaces:
   /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
   /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
   v6.1 files and spaces:
   /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
   /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
   ```


## Configurações específicas de v5.11 para v7{#specific-configurations-in-v5-11}

![](../../assets/v7-only.svg)

Esta seção detalha a configuração adicional necessária ao migrar da v5.11. Você também deve definir as configurações detalhadas no [Configurações gerais](../../migration/using/general-configurations.md) seção.

### Aplicações web {#web-applications-v5}

O seguinte aviso será exibido automaticamente durante a migração:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Alguns componentes de aplicações Web, por exemplo, os vários campos de fórmula, têm atributos @id. Eles são usados no código XML de aplicações web e não são mais gerados da mesma maneira. Eles não estão visíveis na interface e você não deve usá-los normalmente. No entanto, em alguns casos, atributos @id podem ter sido usados para personalizar a renderização de aplicações Web, por exemplo, por meio de uma folha de estilos ou usando o código JavaScript.

Durante a migração, você **must** verifique o caminho do arquivo de log especificado no aviso:

* **O arquivo não está vazio**: contém avisos relativos a inconsistências registradas antes da migração e que ainda existem. Pode ser um código JavaScript em um aplicativo da Web que faz referência a uma ID inexistente. Cada erro deve ser verificado e corrigido.
* **O arquivo está vazio**: isso significa que o Adobe Campaign não detectou nenhum problema.

Independentemente de o arquivo estar vazio ou não, você deve verificar se essas IDs não são usadas para configuração em outro lugar (e adaptar a configuração se esse for o caso).

### Fluxos de trabalho {#workflows}

Como o nome do diretório de instalação do Adobe Campaign foi alterado, alguns workflows podem não funcionar após a migração. Se um workflow fizer referência ao diretório nl5 em uma de suas atividades, ocorrerá um erro. Substitua esta referência por **build**. Você pode executar uma consulta SQL para identificar esses workflows (exemplo PostgreSQL):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>O MySQL só é compatível no v7 como o mecanismo de banco de dados principal ao migrar da versão 6.02 ou 5.11 usando esse mecanismo.

O MySQL não gerencia fusos horários por padrão. Para habilitar o gerenciamento de fuso horário, execute o seguinte comando:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Para obter mais informações, consulte [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) página.

Se modificações tiverem sido feitas na estrutura do banco de dados, durante a configuração, por exemplo (criação de índices específicos, criação de visualizações SQL, etc.), determinadas precauções devem ser tomadas ao migrar. Com efeito, certas modificações podem ser geradas a partir de incompatibilidades com o procedimento de migração. Por exemplo, criação de exibições SQL contendo **Carimbo de data e hora** os campos não são compatíveis com a variável **usetimestamptz** opção. Portanto, recomendamos que você siga as recomendações abaixo:

1. Antes de iniciar a migração, faça backup do banco de dados.
1. Excluir alterações no SQL.
1. Executar pós-atualização
   >[!NOTE]
   >
   >Você deve seguir as etapas de migração apresentadas em [esta seção](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. Reintegrar alterações de SQL.

Neste exemplo, um **NmcTrackingLogMessages** foi criada e isso tem uma **Carimbo de data e hora** nome do campo **tslog**. Nesse caso, o procedimento de migração falha e a seguinte mensagem de erro é exibida:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

Para garantir que a pós-atualização funcione, é necessário excluir a exibição antes da migração e recriá-la após a migração, adaptando-a ao modo TIMESTAMP WITH TIMEZONE.

### Rastreamento {#tracking}

A fórmula de rastreamento foi modificada. Ao migrar, a fórmula antiga (v5) é substituída pela nova (v7). Se você usar uma fórmula personalizada no Adobe Campaign v5, essa configuração deverá ser adaptada no Adobe Campaign v7 (**NmsTracking_ClickFormula** e **NmsTracking_OpenFormula** opções).

A gestão de rastreamento Web também foi modificada. Depois que a migração para o v7 for realizada, você deverá iniciar o assistente de implantação para concluir a configuração do rastreamento Web.

![](assets/migration_web_tracking.png)

Três modos estão disponíveis:

* **Acompanhamento da Web da sessão**: Se a variável **[!UICONTROL Leads]** não tiver sido instalado, essa opção será selecionada por padrão. Essa opção é a mais ideal em termos de desempenho e permite limitar o tamanho dos logs de rastreamento.
* **Acompanhamento permanente da Web**
* **Rastreamento Web anônimo**: Se a variável **[!UICONTROL Leads]** estiver instalado, essa opção será selecionada por padrão. É a opção que consome mais recursos. Como acima, a variável **sSourceId** deve ser indexada (na tabela de rastreamento e no **CrmIncomingLead** tabela).

>[!NOTE]
>
>Para obter mais informações sobre esses três modos, consulte [esta seção](../../configuration/using/about-web-tracking.md).

### Estrutura em árvore do Adobe Campaign v7 {#campaign-vseven-tree-structure}

Durante a migração, a estrutura em árvore é automaticamente reorganizada com base nos padrões do v7. As novas pastas são adicionadas, as pastas obsoletas são excluídas e seu conteúdo é colocado na pasta &quot;Para mover&quot;. Todos os itens nessa pasta devem ser verificados após a migração e o consultor deve decidir mantê-la ou excluir cada um. Os artigos a conservar devem ser transferidos para o local certo.

Uma opção foi adicionada para desativar a migração automática da árvore de navegação. Esta operação agora é manual. As pastas obsoletas não são excluídas e as novas pastas não são adicionadas. Essa opção só deve ser usada se a árvore de navegação v5 predefinida tiver sofrido muitas alterações. Adicione a opção ao console, antes de migrar, na **[!UICONTROL Administration > Options]** nó:

* Nome interno: NlMigration_KeepFolderStructure
* Tipo de dados: Número inteiro
* Valor (texto): 1

Se usar essa opção, após a migração, será necessário excluir pastas obsoletas, adicionar as novas pastas e executar todas as verificações necessárias.

**Lista de novas pastas**:

As seguintes pastas precisam ser adicionadas após a migração:

| Nome interno | Rótulo | Condição |
|---|---|---|
| nmsAutoObjects | Objetos criados automaticamente | - |
| nmsCampaignAdmin | Gerenciamento de campanhas | - |
| nmsCampaignMgt | Gerenciamento de campanhas | - |
| nmsCampaignRes | Gerenciamento de campanhas | - |
| nmsModels | Modelos | - |
| nmsOnlineRes | Online | - |
| nmsProduction | Produção | - |
| nmsProfilProcess | Processos | - |
| xtkDashboard | Painéis | - |
| xtkPlatformAdmin | Plataforma | - |
| nmsLocalOrgUnit | Unidades organizacionais | - |
| nmsMRM | MRM | MRM instalado |
| nmsOperations | Campanhas | Campanha instalada |

**Lista de pastas obsoletas**:

As pastas obsoletas a serem excluídas após a migração são as seguintes:

>[!NOTE]
>
>Todo o conteúdo das pastas obsoletas deve ser verificado e, para cada item, o consultor decide se deseja mantê-lo ou excluí-lo. Os artigos a conservar devem ser transferidos para o local adequado.

| Nome interno | Rótulo | Condição |
|---|---|---|
| nmsAdministration | Administração | - |
| nmsDeliveryMgt | Execução da campanha | - |
| ncmContent | Gestão de conteúdo | Gerenciador de conteúdo instalado |
| ncmForm | Formulário de entrada | Gerenciador de conteúdo instalado |
| ncmImage | Imagens | Gerenciador de conteúdo instalado |
| ncmJavascript | Códigos JavaScript | Gerenciador de conteúdo instalado |
| ncmJst | Modelos JavaScript | Gerenciador de conteúdo instalado |
| ncmParameters | Configuração | Gerenciador de conteúdo instalado |
| ncmSrcSchema | Esquemas de dados | Gerenciador de conteúdo instalado |
| ncmStylesheet | Arquivos de estilo XSL | Gerenciador de conteúdo instalado |
| nmsAdminPlan | Administração | Campanha instalada |
| nmsResourcePlan | Recursos | Campanha instalada |
| nmsResourcesModels | Modelos | Campanha instalada |
| nmsRootPlan | Gerenciamento de campanhas | Campanha instalada |
| nmsOperator | Operadores de marketing | MRM instalado |


## Configurações específicas da v6.02 para v7{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

A seção a seguir detalha a configuração adicional necessária ao migrar da v6.02. Você também deve definir as configurações detalhadas em [esta página](../../migration/using/general-configurations.md).

### Aplicações web {#web-applications-v6}

Se você estiver migrando da v6.02, os registros de erros relacionados aos aplicativos do tipo visão geral da Web poderão ser exibidos. Exemplos de mensagem de erro:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Esses aplicativos Web usavam SQLData e não são compatíveis com o v7, devido a maior segurança. Esses erros levarão a uma falha de migração.

Se você não tiver usado esses aplicativos Web, execute o seguinte script de limpeza e execute novamente o postupgrade:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Se você modificou essas aplicações Web e gostaria de continuar usando-as no v7, é necessário ativar a variável **allowSQLInjection** em suas diferentes zonas de segurança e reinicie a pós-atualização. Consulte a [SQLData](../../migration/using/general-configurations.md#sqldata) para obter mais informações.

### Centro de mensagens {#message-center}

Após a migração da instância de controle do Centro de Mensagens, é necessário republicar os templates de mensagem transacional para que eles funcionem.

No v7, os nomes dos templates de mensagem transacional em instâncias de execução foram alterados. No momento, eles são prefixados pelo nome do operador que corresponde à instância de controle na qual foram criados, por exemplo **control1_template1_rt** em que **control1** é o nome do operador). Se você tiver um volume significativo de modelos, recomendamos excluir os modelos antigos nas instâncias de controle.