---
title: Criação de uma conexão compartilhada
seo-title: Criação de uma conexão compartilhada
description: Criação de uma conexão compartilhada
seo-description: null
page-status-flag: never-activated
uuid: 30d6d23b-72c6-4454-8d6b-a10102f89262
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 7f471ac1-cd6a-4371-977e-52d60ce8d968
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: f4ecdab4c17a6ba8deb3b98079f57bb7a9adf4a0
workflow-type: ht
source-wordcount: '1002'
ht-degree: 100%

---


# Criação de uma conexão compartilhada{#creating-a-shared-connection}

>[!IMPORTANT]
>
>* Extensões de schema feitas nos schemas usados pelos [workflows técnicos do Centro de Mensagens](../../message-center/using/technical-workflows.md) em instâncias de controle ou de execução precisam ser duplicadas nas outras instâncias usadas pelo módulo de mensagens transacionais do Adobe Campaign.
>* A instância de controle e a instância de execução devem ser instaladas em máquinas diferentes. Elas não podem compartilhar a mesma instância do Campaign.
>



## Instância de controle {#control-instance}

Se você tiver uma arquitetura dividida, precisará especificar as instâncias de execução vinculadas à instância de controle e conectá-las. Os templates de mensagem transacional são implantados nas instâncias de execução. A conexão entre a instância de controle e as instâncias de execução é criada configurando as contas externas do tipo **[!UICONTROL Execution instance]**. A quantidade de contas externas precisa ser igual à quantidade de instâncias de execução.

>[!NOTE]
>
>Quando as instâncias de execução são usadas por várias instâncias de controle, os dados podem ser divididos por pasta e por operador. Para obter mais informações, consulte [Uso de várias instâncias de controle](#using-several-control-instances).

Para criar uma conta externa do tipo instância de execução, siga as etapas abaixo:

1. Vá para a pasta de **[!UICONTROL Administration > Platform > External accounts]**.
1. Selecione uma das contas externas do tipo instância de execução fornecidas com o Adobe Campaign, clique com o botão direito do mouse e escolha **[!UICONTROL Duplicate]**.

   ![](assets/messagecenter_create_extaccount_001.png)

1. Altere o rótulo de acordo com suas necessidades.

   ![](assets/messagecenter_create_extaccount_002.png)

1. Selecione a opção **[!UICONTROL Enabled]** para tornar a conta externa operacional.

   ![](assets/messagecenter_create_extaccount_003.png)

1. Especifique o endereço do servidor no qual a instância de execução está instalada.

   ![](assets/messagecenter_create_extaccount_004.png)

1. A conta deve corresponder ao Agente do Centro de Mensagens conforme definido na pasta do operador. Por padrão, a conta integrada fornecida pelo Adobe Campaign é **[!UICONTROL mc]**.

   ![](assets/messagecenter_create_extaccount_005.png)

1. Digite a senha da conta conforme definido na pasta do operador.

   >[!NOTE]
   >
   >Para evitar digitar a senha sempre que fizer logon na instância, especifique o endereço IP da instância de controle na instância de execução Para obter mais informações, consulte [Instância de execução](#execution-instance).

1. Especifique o método de recuperação a ser usado pela instância de execução.

   Os dados a serem recuperados são encaminhados à instância de controle pela instância de execução para adicionar a uma mensagem transacional e a arquivamentos de eventos.

   ![](assets/messagecenter_create_extaccount_007.png)

   A coleta de dados ocorre por meio de um serviço Web que usa o acesso HTTP/HTTPS ou através do módulo Federated Data Access (FDA).

   >[!NOTE]
   >
   >Observe que ao usar FDA em HTTP, somente as instâncias de execução usando um banco de dados Postgres são compatíveis. Não há suporte para bancos de dados MSSQL ou Oracle.

   O segundo método é recomendado se a instância de controle tiver acesso direto ao banco de dados das instâncias de execução. Caso contrário, escolha o acesso do serviço Web. A conta FDA para especificar coincide com a conexão com os bancos de dados das várias instâncias de execução criadas na instância de controle.

   ![](assets/messagecenter_create_extaccount_008.png)

   Para obter mais informações sobre o Federated Data Access (FDA), consulte [Acesso a um banco de dados externo](../../platform/using/about-fda.md).

1. Clique em **[!UICONTROL Test the connection]** para verificar se a instância de controle e a instância de execução estão vinculadas.

   ![](assets/messagecenter_create_extaccount_006.png)

1. Cada instância de execução deve ser associada a um identificador. Esse identificador pode ser atribuído a cada instância de execução manualmente, usando o assistente de implantação (consulte [Identificação de instâncias de execução](../../message-center/using/identifying-execution-instances.md)) ou automaticamente, clicando no botão **Initialize connection** na instância de controle.

   ![](assets/messagecenter_create_extaccount_006bis.png)

## Instância de execução {#execution-instance}

Para que a instância de controle possa se conectar à instância de execução sem ter que fornecer uma senha, basta digitar o endereço IP da instância de controle na seção direitos de acesso do **Centro de Mensagens** . No entanto, senhas vazias são proibidas por padrão.

Para usar uma senha vazia, vá para as instâncias de execução e defina uma zona de segurança limitada ao endereço IP do sistema de informações que entrega os eventos. Essa zona de segurança deve permitir senhas vazias e aceitar conexões do tipo `<identifier> / <password>`. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#defining-security-zones).

>[!NOTE]
>
>Quando as instâncias de execução são usadas por várias instâncias de controle, os dados podem ser divididos por pasta e por operador. Para obter mais informações, consulte [Uso de várias instâncias de controle](#using-several-control-instances).

1. Abra a pasta do operador na instância de execução (**[!UICONTROL Administration > Access management > Operators]** ).
1. Selecione o agente **Message Center**.

   ![](assets/messagecenter_operator_001.png)

1. Selecione a guia **[!UICONTROL Edit]**, clique em **[!UICONTROL Access rights]** e depois clique no link **[!UICONTROL Edit the access parameters...]**.

   ![](assets/messagecenter_operator_002.png)

1. Na janela **[!UICONTROL Access settings]**, clique no link **[!UICONTROL Add a trusted IP mask]** e adicione o endereço IP da instância de controle.

   ![](assets/messagecenter_operator_003.png)

## Uso de várias instâncias de controle {#using-several-control-instances}

Você pode compartilhar um cluster de execução com várias instâncias de controle. Esse tipo de arquitetura requer a seguinte configuração.

Por exemplo, se sua empresa gerencia duas marcas, cada uma com sua própria instância de controle: **Control 1** e **Control 2**. Duas instâncias de execução também são usadas. É necessário inserir um operador diferente do Centro de Mensagens para cada instância de controle: um operador **mc1** para a instância de **Controle 1** e um operador **mc2** para a instância de **Controle 2** .

Na árvore de todas as instâncias de execução, crie uma pasta por operador (**Pasta 1** e **Pasta 2**) e restrinja os dados de cada operador à sua pasta.

### Configuração de instâncias de controle {#configuring-control-instances}

1. Na instância de controle do **Controle 1**, crie uma conta externa por instância de execução e insira o operador **mc1** em cada conta externa. O operador **mc1** será criado em todas as instâncias de execução (consulte [Configuração de instâncias de execução](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_1.png)

1. Na instância de controle do **Controle 2**, crie uma conta externa por instância de execução e insira o operador **mc2** em cada conta externa. O operador **mc2** será criado em todas as instâncias de execução (consulte [Configuração de instâncias de execução](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >Para obter mais informações sobre como configurar uma instância de controle, consulte [Instância de controle](#control-instance).

### Configuração de instâncias de execução {#configuring-execution-instances}

Para usar várias instâncias de controle, essa configuração deve ser executada em TODAS as instâncias de execução.

1. Crie uma pasta por operador no nó **[!UICONTROL Administration > Production > Message Center]**: **Folder 1** e **Folder 2**. Para obter mais informações sobre criação de pastas e visualizações, consulte [Plataforma](../../platform/using/access-management.md#folders-and-views).

   ![](assets/messagecenter_multi_control_3.png)

1. Crie os operadores **mc1** e **mc2** duplicando o operador do Centro de Mensagens fornecido por padrão (**mc**). Para obter mais informações sobre criação de operadores, consulte [esta seção](../../platform/using/access-management.md#operators).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >Os operadores **mc1** e **mc2** devem ter os direitos de **[!UICONTROL Message Center execution]** e não podem ter acesso ao console do cliente do Adobe Campaign. Um operador deve estar sempre vinculado a uma zona de segurança. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#defining-security-zones).

1. Para cada operador, marque a caixa **[!UICONTROL Restrict to information found in sub-folders of]** e selecione a pasta relevante (**Folder 1** para o operador **mc1** e **Folder 2** para o operador **mc2**).

   ![](assets/messagecenter_multi_control_5.png)

1. Forneça permissões de leitura e gravação ao operador para sua pasta. Para fazer isso, clique com o botão direito do mouse e selecione **[!UICONTROL Properties]**. Em seguida, selecione a guia **[!UICONTROL Security]** e adicione o operador relevante (**mc1** para **Folder 1** e **mc2** para **Folder 2**). Verifique se as caixas **[!UICONTROL Read/Write data]** estão marcadas.

   ![](assets/messagecenter_multi_control_6.png)

