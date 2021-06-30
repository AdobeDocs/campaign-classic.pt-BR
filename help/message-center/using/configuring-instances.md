---
product: campaign
title: Configurar instâncias
description: Saiba como configurar o controle de mensagens transacionais e as instâncias de execução no Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 23a384d1-27ce-46c2-98c3-0fb60a5c50ee
source-git-commit: e86350cf12db37e3f2c227563057b97922601729
workflow-type: ht
source-wordcount: '1222'
ht-degree: 100%

---


# Configurar instâncias {#creating-a-shared-connection}

Para usar os recursos de mensagens transacionais, é necessário configurar as instâncias de controle e de execução. É possível usar:
* [Uma instância de controle](#control-instance) associada a uma ou várias instâncias de execução
* [Várias instâncias de controle](#using-several-control-instances) associadas a várias instâncias de execução

>[!IMPORTANT]
>
>Extensões de esquema afetaram os recursos usados por [workflows técnicos do Centro de mensagens](../../message-center/using/additional-configurations.md#technical-workflows) nas instâncias de controle ou de execução que precisam ser duplicadas nas outras instâncias usadas pelo módulo de mensagens transacionais.

Você também precisa especificar e conectar as instâncias de execução às instâncias de controle.

Todas as etapas necessárias para configurar e conectar as instâncias de controle e de execução são descritas nesta seção.

>[!IMPORTANT]
>
>A instância de controle e a instância de execução devem ser instaladas em máquinas diferentes. Elas não podem compartilhar a mesma instância do Campaign.

## Configurar a instância de controle {#control-instance}

Para conectar a instância de controle e as instâncias de execução, você primeiro precisa criar e configurar um **[!UICONTROL Execution instance]** tipo de conta externa **na instância de controle**. Portanto, uma vez [publicado](../../message-center/using/publishing-message-templates.md#template-publication), os modelos de mensagem transacional podem ser implantados nas instâncias de execução.

Se você estiver usando várias instâncias de execução, será necessário criar quantas contas externas houver de instâncias de execução.

>[!NOTE]
>
>Quando as instâncias de execução são usadas por várias instâncias de controle, os dados podem ser divididos por pasta e por operador. Para obter mais informações, consulte [Usar várias instâncias de controle](#using-several-control-instances).

### Criar uma conta externa

>[!NOTE]
>
>As etapas abaixo devem ser executadas **na instância de controle**.

Para criar uma conta externa do tipo **[!UICONTROL Execution instance]**, aplique o seguinte:

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
   >Para evitar digitar a senha sempre que fizer logon na instância, especifique o endereço IP da instância de controle na instância de execução Para obter mais informações, consulte [Configurar as instâncias de execução](#execution-instance).

1. Especifique o método de recuperação que será usado pela instância de execução. Os dados a serem recuperados são encaminhados à instância de controle pela instância de execução para adicionar a uma mensagem transacional e a arquivamentos de eventos.

   ![](assets/messagecenter_create_extaccount_007.png)

   A coleta de dados ocorre por meio de um serviço Web que usa o acesso HTTP/HTTPS ou através do módulo Federated Data Access (FDA).

   >[!NOTE]
   >
   >Observe que ao usar FDA em HTTP, somente as instâncias de execução usando um banco de dados PostgreSQL são compatíveis. Não há suporte para bancos de dados MSSQL ou Oracle.

   O segundo método (FDA) é recomendado se a instância de controle tiver acesso direto ao banco de dados das instâncias de execução. Caso contrário, escolha o acesso do serviço Web. A conta FDA para especificar coincide com a conexão com os bancos de dados das várias instâncias de execução criadas na instância de controle.

   ![](assets/messagecenter_create_extaccount_008.png)

   Para obter mais informações sobre o Federated Data Access (FDA), consulte [esta seção](../../installation/using/about-fda.md).

1. Clique em **[!UICONTROL Test the connection]** para verificar se a instância de controle e a instância de execução estão vinculadas.

   ![](assets/messagecenter_create_extaccount_006.png)

Ao usar várias instâncias de execução, repita essas etapas para criar quantas contas externas houver de instâncias de execução.

### Identificar instâncias de execução {#identifying-execution-instances}

Cada instância de execução deve ser associada a um identificador exclusivo para diferenciar o histórico de cada instância de execução ao visualizá-lo na instância de controle.

Esse identificador pode ser atribuído a cada instância de execução **manualmente**. Nesse caso, essa etapa deve ser executada **em cada instância de execução**. Para fazer isso, use o assistente de implantação conforme detalhado abaixo:

1. Abra o assistente de implantação em uma instância de execução.
1. Acesse a janela do **[!UICONTROL Message Center]**.
1. Atribua o identificador escolhido à instância.

   ![](assets/messagecenter_id_execinstance_001.png)

1. Repita as etapas acima em cada instância de execução.

O identificador também pode ser **automaticamente** atribuído. Para fazer isso, vá para a **instância de controle** e clique no botão **[!UICONTROL Initialize connection]**.

![](assets/messagecenter_create_extaccount_006bis.png)

## Configurar as instâncias de execução {#execution-instance}

>[!NOTE]
>
>As etapas abaixo devem ser executadas **nas instâncias de execução**.

Para conectar as instâncias de execução à instância de controle, siga as etapas abaixo.

Para que a instância de controle possa se conectar à instância de execução sem ter que fornecer uma senha, basta digitar o endereço IP da instância de controle na seção de direitos de acesso do **Centro de Mensagens** No entanto, senhas vazias são proibidas por padrão.

Para usar uma senha vazia, vá para as instâncias de execução e defina uma zona de segurança limitada ao endereço IP do sistema de informações que entrega os eventos. Essa zona de segurança deve permitir senhas vazias e aceitar conexões do tipo `<identifier> / <password>`. Para obter mais informações, consulte [esta seção](../../installation/using/security-zones.md).

>[!NOTE]
>
>Quando as instâncias de execução são usadas por várias instâncias de controle, os dados podem ser divididos por pasta e por operador. Para obter mais informações, consulte [Usar várias instâncias de controle](#using-several-control-instances).

1. Em uma instância de execução, acesse a pasta do operador ( **[!UICONTROL Administration > Access management > Operators]** ).
1. Selecione o agente **Message Center**.

   ![](assets/messagecenter_operator_001.png)

1. Selecione a guia **[!UICONTROL Edit]**, clique em **[!UICONTROL Access rights]** e depois clique no link **[!UICONTROL Edit the access parameters...]**.

   ![](assets/messagecenter_operator_002.png)

1. Na janela **[!UICONTROL Access settings]**, clique no link **[!UICONTROL Add a trusted IP mask]** e adicione o endereço IP da instância de controle.

   ![](assets/messagecenter_operator_003.png)

Ao usar várias instâncias de execução, repita essas etapas para cada instância de execução.

## Usar várias instâncias de controle {#using-several-control-instances}

Você pode compartilhar um cluster de execução com várias instâncias de controle. Esse tipo de arquitetura requer a seguinte configuração.

Por exemplo, imagine que sua empresa gerencia duas marcas, cada uma com sua própria instância de controle: **Controe 1** e **Controle 2**. Duas instâncias de execução também são usadas. É necessário inserir um operador diferente do Centro de Mensagens para cada instância de controle: um operador **mc1** para a instância de **Controle 1** e um operador **mc2** para a instância de **Controle 2** .

Na árvore de todas as instâncias de execução, crie uma pasta por operador (**Pasta 1** e **Pasta 2**) e restrinja os dados de cada operador à sua pasta.

### Configurar instâncias de controle {#configuring-control-instances}

>[!NOTE]
>
>As etapas abaixo devem ser executadas **nas instâncias de controle**.

1. Na instância de controle **Controle 1**, crie uma conta externa por instância de execução e insira o operador **mc1** em cada conta externa. O operador **mc1** será posteriormente criado em todas as instâncias de execução (consulte [Configurar instâncias de execução](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_1.png)

1. Na instância de controle **Controle 2**, crie uma conta externa por instância de execução e insira o operador **mc2** em cada conta externa. O operador **mc2** será posteriormente criado em todas as instâncias de execução (consulte [Configurar instâncias de execução](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >Para obter mais informações sobre como configurar uma instância de controle, consulte [esta seção](#control-instance).

### Configurar instâncias de execução {#configuring-execution-instances}

>[!NOTE]
>
>As etapas abaixo devem ser executadas **nas instâncias de execução**.

Para usar várias instâncias de controle, essa configuração deve ser executada em TODAS as instâncias de execução.

1. Crie uma pasta por operador no nó **[!UICONTROL Administration > Production > Message Center]**: **Folder 1** e **Folder 2**. Para obter mais informações sobre criação de pastas e visualizações, consulte [esta página](../../platform/using/access-management-folders.md).

   ![](assets/messagecenter_multi_control_3.png)

1. Crie os operadores **mc1** e **mc2** duplicando o operador do Centro de Mensagens fornecido por padrão (**mc**). Para obter mais informações sobre criação de operadores, consulte [esta seção](../../platform/using/access-management-operators.md).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >Os operadores **mc1** e **mc2** devem ter os direitos de **[!UICONTROL Message Center execution]** e não podem ter acesso ao console do cliente do Adobe Campaign. Um operador deve estar sempre vinculado a uma zona de segurança. Para obter mais informações, consulte [esta seção](../../installation/using/security-zones.md).

1. Para cada operador, marque a caixa **[!UICONTROL Restrict to information found in sub-folders of]** e selecione a pasta relevante (**Folder 1** para o operador **mc1** e **Folder 2** para o operador **mc2**).

   ![](assets/messagecenter_multi_control_5.png)

1. Forneça permissões de leitura e gravação ao operador para sua pasta. Para fazer isso, clique com o botão direito do mouse e selecione **[!UICONTROL Properties]**. Em seguida, selecione a guia **[!UICONTROL Security]** e adicione o operador relevante (**mc1** para **Folder 1** e **mc2** para **Folder 2**). Verifique se as caixas **[!UICONTROL Read/Write data]** estão marcadas.

   ![](assets/messagecenter_multi_control_6.png)
