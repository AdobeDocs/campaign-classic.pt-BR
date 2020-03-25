---
title: Gerenciamento de acesso
seo-title: Gerenciamento de acesso
description: Gerenciamento de acesso
seo-description: null
page-status-flag: never-activated
uuid: 3f0cfa8f-1511-4445-9acb-b5be46e78295
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: c0eb06fd-192c-4ee4-9a38-c9bedbe6aea0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 92f4047628eca0fc1d71aded0329720c094463bd

---


# Gerenciamento de acesso{#access-management}

## Sobre permissões {#about-permissions}

O Adobe Campaign permite definir e gerenciar os direitos atribuídos aos diversos operadores. Veja um conjunto de direitos e restrições que autorizam ou negam:

* Acesso a certas funcionalidades (por meio dos direitos nomeados),
* Acesso a certos registros,
* Criação, modificação e/ou exclusão de registros (ações, contatos, campanhas, grupos, etc.).

As permissões se aplicam a perfis ou grupos de operadores.

Os perfis são preenchidos por parâmetros de segurança vinculados ao modo de conexão do operador para o Adobe Campaign. Para obter mais informações, consulte [esta página](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Há dois tipos de permissões que você pode conceder a um usuário:

* Você pode definir grupos de operadores para atribuir direitos e, em seguida, associar os operadores a um ou mais grupos. Isso permite que você reutilize os direitos e torne os perfis de operadores mais consistentes. Também facilita o gerenciamento e a manutenção de perfis. Group creation and management are presented in [Operator groups](#operator-groups).
* Você pode atribuir direitos nomeados diretamente aos usuários, em alguns casos para sobrecarregar os direitos alocados por meio de grupos. Estes direitos são apresentados em [Direitos nomeados](#named-rights).

>[!NOTE]
>
>Antes de começar a definir as permissões, a Adobe recomenda que você leia a [Lista de verificação de configuração de segurança](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html).

## Operadores {#operators}

### Sobre operadores {#about-operators}

Um operador é um usuário do Adobe Campaign que tem permissões para fazer o login e executar ações.

Por padrão, os operadores são armazenados no **[!UICONTROL Administration > Access management > Operators]** nó.

![](assets/s_ncs_user_list_operators.png)

Os operadores podem ser criados manualmente ou mapeados em um diretório LDAP existente.

O procedimento completo para criar um operador é descrito  [nesta página](#creating-an-operator).

Para obter mais informações sobre o Adobe Campaign e a integração de LDAP, consulte [esta página](../../installation/using/connecting-through-ldap.md).

>[!CAUTION]
>
>Os operadores devem ser vinculados a uma zona de segurança para fazer logon em uma instância. Para obter mais informações sobre as zonas de segurança do Adobe Campaign, consulte [esta página](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Usuários podem se conectar ao Adobe Campaign usando a Adobe ID. Para obter mais informações, consulte esta [página](../../integrations/using/about-adobe-id.md).

### Criação de um operador {#creating-an-operator}

Para criar um novo operador e conceder permissões, siga as etapas abaixo:

1. Click the **[!UICONTROL New]** button located above the list of operators, and enter the details of the new operator.

   ![](assets/s_ncs_user_operator_new.png)

1. Specify the **[!UICONTROL Identification parameters]** of the user: its login, password and name. O login e a senha serão usados pelo operador para se conectar ao Adobe Campaign. Once the user is logged on, they can change their password via the **[!UICONTROL Tools > Change password]** menu. O e-mail do operador é essencial, pois permite que o operador receba notificações, por exemplo, ao processar aprovações.

   Esta seção também permite vincular um operador a uma entidade organizacional. Para obter mais informações, consulte [esta página](../../campaign/using/about-distributed-marketing.md).

1. Select the permissions granted to the operator in the **[!UICONTROL Operator access rights]** section.

   To assign rights to the operator, click the **[!UICONTROL Add]** button located above the list of rights, then select a group of operators from the list of available groups:

   ![](assets/s_ncs_user_permissions_operators.png)

   You can also select one or more named rights (refer to [Named rights](#named-rights)). To do this, click the arrow to the right of the **[!UICONTROL Folder]** field, and select **[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   Select groups and/or named rights to be assigned and click **[!UICONTROL OK]** to validate.

1. Click **[!UICONTROL Ok]** to create the operator: the profile is added to the list of existing operators.

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>Você pode organizar os operadores de acordo com suas necessidades criando novas pastas de operadores. To do this, right-click the operator folder and select **[!UICONTROL Add an 'Operators' folder]**.

Após criar o perfil do operador, você pode adicionar ou atualizar suas informações. To do this, click the **[!UICONTROL Edit]** tab.

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>The **[!UICONTROL Session timeout]** field lets you adjust the delay before the FDA session timeout. Para obter mais informações, consulte [About Federated Data Acces](../../platform/using/about-fda.md).

### Fuso horário do operador {#time-zone-of-the-operator}

In the **[!UICONTROL General]** tab, you can select the time zone of the operator. Por padrão, os operadores trabalham no fuso horário do servidor. No entanto, é possível selecionar outro fuso horário usando a lista suspensa.

A configuração de fusos horários é descrita [nesta página](../../installation/using/time-zone-management.md).

>[!NOTE]
>
>Colaborações em diferentes fusos horários exigem o armazenamento de datas em formato UTC. As datas são convertidas no fuso horário apropriado nos seguintes contextos: quando uma data é exibida no fuso horário do usuário, quando os arquivos são importados e exportados, quando um delivery de e-mail é agendado, quando as atividades são agendadas em um workflow (agendador, espera, restrição de tempo e etc.)
>
>Restrições e recomendações vinculadas a esses contextos são apresentadas nas seções relacionadas da documentação do Adobe Campaign.

In addition, the **[!UICONTROL Regional settings]** drop-down list lets you select the format to display dates and numbers.

### Opções de direitos de acesso {#access-rights-options}

Use the **[!UICONTROL Access rights]** tab to update the groups and named rights linked to the operator.

![](assets/operator_profile_security_options.png)

O **[!UICONTROL Edit the access parameters...]** link permite acessar as seguintes opções:

* The **[!UICONTROL Disable account]** option lets you disable the operator&#39;s account: he will no longer access Adobe Campaign.
* The **[!UICONTROL Forbid access from the rich client]** option lets you restrict the use of Adobe Campaign to [Web access](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) or through APIs: access to the Adobe Campaign client console is no longer available.
* É possível vincular uma zona de segurança ao operador. Para obter mais informações, consulte [esta página](../../installation/using/configuring-campaign-server.md#defining-security-zones).
* Também é possível definir uma máscara IP confiável usando o link apropriado.

   O operador poderá se conectar ao Adobe Campaign sem inserir a senha se o endereço IP estiver nessa lista.

   Você também pode especificar um conjunto de endereços IP que serão autorizados a se conectar sem uma senha, como no exemplo a seguir:

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >Para manter seguro o acesso à sua plataforma, essa opção deve ser usada com cuidado.

* The **[!UICONTROL Restrict to information found in sub-folders of:]** option lets you limit the rights attributed to the operator of a folder. Somente as subpastas do nó especificado nessa opção estarão visíveis para o usuário:

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!CAUTION]
   >
   >Essa é uma restrição muito rígida e deve ser usada com cuidado. Um operador conectado com este tipo de direito pode ver SOMENTE o conteúdo da pasta especificada e não tem acesso a nenhum outro nó da árvore por meio do explorador. No entanto, dependendo das funcionalidades que ele tem acesso (por exemplo: workflows), é possível exibir dados que normalmente são armazenados em nós que não podem ser vistos.

### Pastas, aprovação e tarefas de um operador {#folders--approval-and-tasks-of-an-operator}

The **[!UICONTROL Audit]** tab lets you view information related to the operator. As várias guias são adicionadas automaticamente com base nas configurações definidas na área de intervenção do operador.

Você pode acessar:

* A lista de direitos nas pastas vinculadas ao operador.

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >Para obter mais informações, consulte Gerenciamento [de acesso de](#folder-access-management)pasta.

* O log de aprovações do operador.

   ![](assets/operator_profile_validations.png)

* A lista de fóruns de discussão que eles assinaram.
* Eventos em seu calendário.
* A lista de tarefas atribuídas a eles.

### Operadores padrão {#default-operators}

O Adobe Campaign usa operadores técnicos com perfis configurados por padrão: Administrador (&#39;admin&#39;), Faturamento (&#39;faturamento&#39;), Monitoramento, agente de Aplicação web (&#39;webapp&#39;) etc. Alguns deles dependem dos aplicativos e opções instalados na plataforma: operadores &#39;central&#39; e &#39;local&#39;, por exemplo, só estarão visíveis se a opção Marketing distribuído estiver instalada.

>[!CAUTION]
>
>Esses operadores técnicos são notificados por padrão quando as mensagens de informação são devolvidas pela plataforma. É altamente recomendável fornecer um e-mail de contato para eles.
>
>Para garantir que os aplicativos Web funcionem corretamente, também recomendamos não definir configurações regionais específicas para o operador &#39;webapp&#39;.

Por padrão, o operador técnico &#39;webapp&#39; tem o direito nomeado ADMINISTRATION, que pode levar a riscos de segurança. Para corrigir esse problema, recomendamos remover esse direito. Para fazer isso:

1. No **[!UICONTROL Administration > Access management > Named rights]** nó, clique **[!UICONTROL New]** para criar um direito e nomeá-lo WEBAPP.

   ![](assets/s_ncs_default_operators_webapp_right.png)

   Named rights are detailed in the [Named rights](#named-rights) section.

1. From the **[!UICONTROL Administration > Access management > Operators]** node, select the Web applications agent operator (&#39;webapp&#39;).

   Select the **[!UICONTROL Edit]** tab, then the **[!UICONTROL Access rights]** tab and delete the ADMINISTRATION named right from the list.

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   Click **[!UICONTROL Add]** and select the WEBAPP right that you have just created, then save your changes.

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. Atribua ao operador “webapp” direitos de acesso para leitura e gravação de dados nas pastas que dizem respeito a esse operador, que são principalmente as pastas “Recipient”.

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   Modifying rights on tree folders is detailed in the [Folder access management](#folder-access-management) section.

>[!NOTE]
>
>Para obter mais informações sobre Diretrizes de segurança, consulte a [lista de verificação de configuração do Adobe Campaign Security](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html).

## Grupos de operadores {#operator-groups}

Operator groups are created via the **[!UICONTROL Administration > Access management > Operator groups]** node in the tree.

### Criação de um novo grupo de operadores {#creating-a-new-operator-group}

Para criar um novo grupo de operadores, siga as etapas abaixo:

1. Click the **[!UICONTROL New]** button to the right of the list of groups or right-click the list and choose **[!UICONTROL New]**.
1. In the section lower window, from the **[!UICONTROL General]** tab, enter the name and a description for this group in the corresponding fields.

   ![](assets/s_ncs_user_create_operator_gp.png)

1. Click the **[!UICONTROL Content]** tab to define authorizations for this group.
1. Click the **[!UICONTROL Add]** button to select an appointed right or an operator to associate to the group.
1. Click the drop-down list or on the folder to the right of the **[!UICONTROL Folder]** field to locate the appointed rights or operators to associate to this group.
1. Select the rights or operators to add and click **[!UICONTROL OK]** to validate.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   Repita essa operação para adicionar outros direitos ou operadores.

1. Click the **[!UICONTROL Save]** button to add the group to the list.

### Grupos padrão {#default-groups}

Os grupos de operadores padrão são:

1. Operadores de delivery

   Os operadores nesse grupo são responsáveis pelo gerenciamento de deliveries: eles permitem o acesso aos principais recursos necessários para a criação e preparação de deliveries (tipologias de campanha, mapeamentos de delivery, templates padrão, blocos de personalização, etc.).

   Esse grupo contém os seguintes direitos nomeados:

   * PREPARE DELIVERIES: direito de criar, editar e iniciar a análise de delivery,
   * START DELIVERIES: direito de aprovar deliveries previamente analisadas.

1. Gestores de campanha

   Os operadores nesse grupo podem gerenciar campanhas de marketing: isso permite acessar os objetos vinculados às campanhas (planos, programas, workflows, orçamentos, etc.).

   Esse grupo contém os seguintes direitos nomeados:

   * INSERT FOLDERS: direito de inserir pastas à árvore do Adobe Campaign (se você tiver o direito de editar ramificações),
   * WORKFLOW: direito de usar workflows.
   >[!NOTE]
   >
   >Esse grupo não permite que os operadores iniciem deliveries.

1. Colaboradores de conteúdo

   Os operadores nesse grupo podem acessar as pastas Conteúdo, dentro da estrutura de **Gestão de conteúdo** (módulo opcional do Adobe Campaign). Esse grupo não concede direitos adicionais.

1. Acesso a relatórios

   Esse grupo é reservado para operadores externos, para acessar os relatórios do delivery por meio de um acesso à Web.

1. Execução do workflow

   Esse grupo permite atribuir aos operadores o direito de gerenciar workflows que não estão relacionados a campanhas.

1. Supervisores de workflow

   Os operadores nesse grupo recebem uma notificação por e-mail no caso de alertas relativos aos workflows da campanha.

1. Gerenciamento local / central

   Esses grupos permitem usar o **Marketing distribuído** (módulo opcional do Adobe Campaign).

## Direitos nomeados {#named-rights}

Por padrão, o Adobe Campaign propõe um conjunto de direitos nomeados que permitem definir as autorizações atribuídas aos operadores e grupos de operadores. These rights can be edited from the **[!UICONTROL Administration > Access management > Named rights]** node of the tree.

![](assets/s_ncs_admin_named_rights.png)

Esses direitos são os seguintes:

* **[!UICONTROL ADMINISTRATION]**: Operadores com **[!UICONTROL ADMINISTRATION]** direito têm acesso total na instância. Os usuários administradores podem executar/criar/editar/excluir qualquer objeto, como fluxo de trabalho, delivery, scripts etc.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: É possível definir várias etapas de aprovação em workflows e delivery para garantir que o estado atual tenha sido aprovado por um operador ou grupo atribuído. Os usuários com **[!UICONTROL APPROVAL ADMINISTRATION]** direito podem definir etapas de aprovação e também atribuir um operador ou grupo de operadores que devem aprovar essas etapas.

* **[!UICONTROL CENTRAL]**: Direito de gerenciamento central (Marketing distribuído).

* **[!UICONTROL DELETE FOLDER]**: Direito de excluir pastas. Com esse direito, os usuários podem excluir pastas da visualização do explorador.

* **[!UICONTROL EDIT FOLDERS]**: Direito de alterar as propriedades da pasta, como nome interno, rótulo, imagem associada, ordem de subpastas etc.

* **[!UICONTROL EXPORT]**: Os usuários podem exportar dados de suas instâncias de Adobe Campaign para um arquivo no servidor ou computador local usando a atividade de fluxo de trabalho **[!UICONTROL EXPORT]** .

* **[!UICONTROL FILES ACCESS]**: Direito de ler e gravar o acesso de arquivos por meio de um script que pode ser gravado na atividade de fluxo de trabalho para arquivos de leitura/gravação em um servidor. **[!UICONTROL JavaScript]**

* **[!UICONTROL IMPORT]**: Direito de importação de dados genéricos. **[!UICONTROL IMPORT]** permite importar dados para qualquer outra tabela, enquanto o **[!UICONTROL RECIPIENT IMPORT]** direito permite importar somente para a tabela do recipient.

* **[!UICONTROL INSERT FOLDERS]**: Direito de inserir pastas. Os usuários com **[!UICONTROL INSERT FOLDERS]** direitos podem criar novas pastas na árvore de pastas na visualização do explorador.

* **[!UICONTROL LOCAL]**: Direito para gerenciamento local (Marketing distribuído).

* **[!UICONTROL MERGE]**: Direito de unir os registros selecionados em um. Se houver recipient como duplicados, a **[!UICONTROL MERGE]** direita permitirá que o usuário selecione os duplicados e os mescle em um recipient primário.

* **[!UICONTROL PREPARE DELIVERIES]**: Direito de criar, editar e salvar um delivery. Os usuários com **[!UICONTROL PREPARE DELIVERIES]** direito também podem start o processo de análise do delivery.

* **[!UICONTROL PRIVACY DATA RIGHT]**: Direito de coletar e excluir dados de privacidade. Para obter mais informações, consulte esta [página](https://helpx.adobe.com/campaign/kb/acc-privacy.html).

* **[!UICONTROL PROGRAM EXECUTION]**: Direito de executar comandos em várias linguagens de programação.

* **[!UICONTROL RECIPIENT IMPORT]**: Direito de importar recipients. Os usuários com **[!UICONTROL RECIPIENT IMPORT]** direito podem importar um arquivo local para a tabela do recipient.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Direito de executar qualquer comando SQL diretamente no banco de dados.

* **[!UICONTROL START DELIVERIES]**: Direito de aprovar deliveries anteriormente analisados. Após a análise do delivery, o delivery pausará em várias etapas de aprovação e precisará ser aprovado para retomar. Os usuários com **[!UICONTROL START DELIVERIES]** direito podem aprovar delivery.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: Direito de escrever seus próprios scripts SQL usando a atividade de Gestão de dados SQL, para criar e preencher tabelas de trabalho (consulte [esta seção](../../workflow/using/sql-data-management.md)).

* **[!UICONTROL WORKFLOW]**: Direito de executar workflows. Sem esse direito, os usuários não podem start, parar ou reiniciar workflows.

* **[!UICONTROL WEBAPP]**: Direito de utilizar aplicativos Web.

>[!NOTE]
>
>Essa lista pode variar dependendo dos complementos instalados na plataforma.

## Matriz de direitos de acesso {#access-rights-matrix}

Os grupos padrão e os direitos nomeados permitem que os operadores acessem determinadas pastas na hierarquia de navegação e concedam permissões de leitura, gravação e exclusão.

A matriz de direitos de acesso do Adobe Campaign está disponível [aqui](/help/platform/using/assets/accessrights.pdf).

## Gerenciamento de acesso a pastas {#folder-access-management}

Cada pasta da árvore tem direitos de acesso de leitura, gravação e exclusão atribuídos a ela. Para acessar um arquivo, um operador ou grupo de operadores deve ter pelo menos acesso de leitura a ele.

### Editar permissões em uma pasta {#edit-permissions-on-a-folder}

Para editar permissões em uma pasta específica da árvore, siga as etapas abaixo:

1. Right-click on the folder and select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. Click the **[!UICONTROL Security]** tab to view authorizations on this folder.

   ![](assets/s_ncs_user_folder_properties_security.png)

### Modificar permissões {#modify-permissions}

Para modificar permissões, você pode:

* **Substituir um grupo ou um operador**. Para fazer isso, clique em um dos grupos (ou operadores) com direitos à pasta e selecione um novo grupo (ou um novo operador) na lista suspensa:

   ![](assets/s_ncs_user_folder_properties_security02.png)

* **Autorizar um grupo ou um operador**. To do this, click the **[!UICONTROL Add]** button and select the group or operator to which you want to assign authorizations for this folder.
* **Proibir um grupo ou operador**. To do this, click **[!UICONTROL Delete]** and select the group or operator from which you want to remove authorization for this folder.
* **Selecionar os direitos atribuídos a um grupo ou a um operador**. Para fazer isso, clique no grupo ou operador relacionado, selecione os direitos de acesso que deseja conceder e desmarque os outros.

   ![](assets/s_ncs_user_folder_properties_security03.png)

### Propagar permissões {#propagate-permissions}

Você pode propagar autorizações e direitos de acesso. To do this, select the **[!UICONTROL Propagate]** option in the folder properties.

As autorizações definidas nessa janela serão aplicadas a todas as subpastas do nó atual. É possível sobrecarregar essas autorizações para cada uma das subpastas.

>[!NOTE]
>
>Limpar essa opção para uma pasta não a limpa automaticamente para as subpastas. Você deve limpá-la explicitamente para cada uma das subpastas.

### Conceder acesso a todos os operadores {#grant-access-to-all-operators}

In the **[!UICONTROL Security]** tab, if the **[!UICONTROL System folder]** option is selected, all operators will have access to this data, regardless of their rights. Se essa opção estiver desmarcada, você deverá adicionar explicitamente o operador (ou seu grupo) à lista de autorizações para que ele tenha acesso.

![](assets/s_ncs_user_folder_properties_security03b.png)

## Pastas e visualizações {#folders-and-views}

### Sobre pastas e visualizações {#about-folders-and-views}

Pastas são nós na árvore do Adobe Campaign. These nodes are created by right-clicking the tree, via the **[!UICONTROL Add new folder]** menu. Por padrão, o primeiro menu permite adicionar a pasta correspondente ao contexto atual.

![](assets/s_ncs_user_add_folder_in_tree.png)

É possível conceder permissões a essas pastas como em todas as outras pastas da árvore. Consulte Gerenciamento [de acesso de](#folder-access-management)pasta.

Além disso, você pode criar visualizações para restringir o acesso aos dados e organizar o conteúdo da árvore para atender aos seus requisitos. É possível atribuir direitos às visualizações.

Uma visualização é uma pasta que exibe os registros fisicamente armazenados em uma ou mais pastas do mesmo tipo. Por exemplo, se você criar uma pasta do Campaing que seja uma visualização, ela exibirá todas as campanhas presentes no banco de dados por padrão, independente de sua origem. Esses dados podem ser filtrados.

Quando você converte uma pasta em uma visualização, todos os dados correspondentes ao tipo de pasta presentes no banco de dados são exibidos na visualização, independentemente da pasta em que são salvos. É possível filtrar para restringir a lista de dados exibidos.

>[!CAUTION]
>
>As visualizações contêm dados e fornecem acesso a eles, mas os dados não são armazenados fisicamente na pasta de visualização. O operador deve ter os direitos apropriados para a ação desejada nas pastas da fonte de dados (acesso de leitura no mínimo).
>
>Para conceder acesso a uma visualização sem conceder acesso à pasta de origem, basta não conceder acesso de leitura no nó pai da pasta de origem.

### Adição de pastas e criação de visualizações {#adding-folders-and-creating-views}

No exemplo abaixo, criaremos novas pastas para exibir dados específicos:

1. Create a new **[!UICONTROL Deliveries]** type folder, and name it **Deliveries France**.
1. Right-click this folder and select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_add_folder_exple.png)

1. Na **[!UICONTROL Restriction]** guia, selecione **[!UICONTROL This folder is a view]**. Todos os deliveries no banco de dados serão exibidos.

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. Defina os critérios do filtro de delivery no editor de query na seção intermediária da janela: as campanhas correspondentes ao filtro definido serão exibidas.

   >[!NOTE]
   >
   >O editor de query é apresentado [nesta seção](../../platform/using/about-queries-in-campaign.md).

   Com as seguintes condições de filtro:

![](assets/s_ncs_user_add_folder_exple00.png)

Os seguintes deliveries serão exibidos na visualização:

![](assets/s_ncs_user_add_folder_exple02.png)

