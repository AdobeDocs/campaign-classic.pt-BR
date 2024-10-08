---
product: campaign
title: Migração de uma plataforma Microsoft Windows para o Adobe Campaign v7
description: Saiba como migrar uma plataforma Microsoft Windows para o Adobe Campaign v7
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
hide: true
hidefromtoc: true
exl-id: 3743d018-3316-4ce3-ae1c-25760aaf5785
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 0%

---

# Migração de uma plataforma Microsoft Windows para o Campaign v7{#migrating-in-windows-for-adobe-campaign}



Para um ambiente Microsoft Windows, as etapas de migração são as seguintes:

1. Parar todos os serviços - [Saiba mais](#service-stop).
1. Faça backup do banco de dados - [Saiba mais](#back-up-the-database).
1. Migrar a plataforma - [Saiba mais](#deploying-adobe-campaign-v7).
1. Migrar o servidor de redirecionamento (IIS) - [Saiba mais](#migrating-the-redirection-server--iis-).
1. Reiniciar serviço - [Saiba mais](#re-starting-the-services).
1. Excluir e limpar versão anterior do Adobe Campaign - [Saiba mais](#deleting-and-cleansing-adobe-campaign-previous-version).

## Interrupção do serviço {#service-stop}

Primeiro, pare todos os processos com acesso ao banco de dados em todas as máquinas relacionadas.

1. Todos os servidores que usam o módulo de redirecionamento (**webmdl** service) devem ser interrompidos. Para o IIS, execute o seguinte comando:

   ```
   iisreset /stop
   ```

1. O módulo **mta** e seus módulos filho (**mtachild**) devem ser interrompidos usando os seguintes comandos:

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. Interrompa os serviços da Adobe Campaign em todos os servidores. Efetue logon com direitos de administrador e execute o seguinte comando:

   ```
   net stop nlserver6
   ```

<!--

   If you are migrating from v5.11, run the following command:

   ```
   net stop nlserver5
   ```

-->

1. Para cada servidor, verifique se os serviços do Adobe Campaign foram interrompidos corretamente. Efetue logon com direitos de administrador e execute o seguinte comando:

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   A lista de processos ativos, juntamente com a ID (PID), é exibida.

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. Se um ou mais processos do Adobe Campaign ainda estiverem ativos ou bloqueados após alguns minutos, elimine-os. Efetue logon com direitos de administrador e execute o seguinte comando:

   ```
   taskkill /IM nlserver* /T
   ```

1. Se alguns processos ainda estiverem ativos após alguns minutos, você poderá forçá-los a fechar usando o comando:

   ```
   taskkill /F /IM nlserver* /T
   ```

## Fazer backup do banco de dados do Campaign {#back-up-the-database}

Este é o procedimento para fazer backup do Adobe Campaign v6.1.

<!--

### For Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Make a backup of the Adobe Campaign database.
1. Make a backup of the **Neolane v5** directory using the following command:

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **Neolane v5.back** folder and save it elsewhere in a safe location other than the server.

1. In the windows service management console, disable the automatic startup of the 5.11 application server service. You can also use the following command:

   ```
   sc config nlserver5 start= disabled
   ```

1. Edit the **config-`<instance name>`.xml** (in the **Neolane v5. back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart**.

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

-->

<!--
### For Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Make a backup of the Adobe Campaign database.
1. Make a backup of the **Neolane v6** directory using the following command:

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **Neolane v6.back** folder and save it elsewhere in a safe location other than the server.

1. In the Windows service manager, deactivate the 6.02 application server automatic startup. You can also use the following command:

   ```
   sc config nlserver6 start= disabled
   ```

1. Edit the **config-`<instance name>`.xml** (in the **Neolane v6. back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart**.

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword" provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

-->

1. Faça um backup do banco de dados do Adobe Campaign.
1. Faça backup do diretório **Adobe Campaign v6** usando o seguinte comando:

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >Como precaução, recomendamos que você compacte a pasta **Adobe Campaign v6.back** e salve-a em outro local seguro que não seja o servidor.

1. No console de gerenciamento de serviços do Windows, desative a inicialização automática do serviço do servidor de aplicativos 6.11. Você também pode usar o seguinte comando:

   ```
   sc config nlserver6 start= disabled
   ```

## Implantar o Adobe Campaign v7 {#deploying-adobe-campaign-v7}

A implantação do Adobe Campaign envolve duas etapas:

* Instalando build v7: esta operação deve ser executada em cada servidor.
* O post upgrade: esse comando deve ser iniciado em cada instância.

Para implantar o Adobe Campaign, siga as etapas abaixo:

1. Instale a compilação mais recente do Adobe Campaign v7 executando o arquivo de instalação **setup.exe**. Para obter mais informações sobre como instalar o servidor Adobe Campaign no Windows, consulte [esta seção](../../installation/using/installing-the-server.md).

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >O Adobe Campaign v7 é instalado por padrão no diretório **C:\Program Files\Adobe\Adobe Campaign v7**.

1. Para disponibilizar o programa de instalação do console do cliente, copie o arquivo **setup-client-7.0.XXXX.exe** no diretório de instalação do Adobe Campaign: **C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**.

   >[!NOTE]
   >
   >Para obter mais informações sobre como instalar o Adobe Campaign no Windows, consulte [esta seção](../../installation/using/installing-the-server.md).

1. Inicie a instância para o primeiro uso com os seguintes comandos:

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >Esses comandos permitem criar o sistema de arquivos interno do Adobe Campaign v7: diretório **conf** (com os arquivos **config-default.xml** e **serverConf.xml**), diretório **var** etc.

1. Copie e cole (substitua) os arquivos de configuração e as subpastas de cada instância por meio do **arquivo de backup Neolane v5.back**, **Neolane v6.back** ou **arquivo de backup Adobe Campaign v6.back** (dependendo da versão da qual você está migrando - consulte [esta seção](#back-up-the-database-and-the-current-installation)).
1. De acordo com a versão da qual você está migrando, execute os seguintes comandos:

   ```
   copy "Neolane v5.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v5.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v5.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Neolane v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Adobe Campaign v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Adobe Campaign v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Adobe Campaign v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   >[!IMPORTANT]
   >
   >Para o primeiro comando acima, não copie o arquivo **config-default.xml**.

1. Nos arquivos **serverConf.xml** e **config-default.xml** do Adobe Campaign v7, aplique as configurações específicas da versão anterior do Adobe Campaign. Para o arquivo **serverConf.xml**, use o arquivo **Neolane v5/conf/serverConf.xml.diff**, **Neolane v6/conf/serverConf.xml.diff** ou **Adobe Campaign v6/conf/serverConf.xml.diff**.

   >[!NOTE]
   >
   >Ao relatar configurações da versão anterior do Adobe Campaign para o Adobe Campaign v7, verifique se os caminhos para os diretórios físicos levam ao Adobe Campaign v7 (e não ao Neolane v5, Neolane v6 ou Adobe Campaign v6).

1. Recarregue a configuração do Adobe Campaign v7 usando o seguinte comando:

   ```
   nlserver config -reload
   ```

1. Inicie o processo de pós-atualização usando o seguinte comando:

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>Não inicie os serviços da Adobe Campaign ainda: algumas alterações precisam ser feitas no IIS.

## Migrar o servidor de redirecionamento {#migrating-the-redirection-server--iis-}

Nesse estágio, o servidor IIS deve ser interrompido. Consulte [Parada de serviço](#service-stop).

1. Abra o console **Gerenciador do IIS (Serviços de Informações da Internet)**.
1. Alterar as associações (portas de escuta) do site usado para a versão anterior do Adobe Campaign:

   * Clique com o botão direito no site usado para a versão anterior do Adobe Campaign e selecione **[!UICONTROL Edit bindings]**.
   * Para cada tipo de porta de escuta (**[!UICONTROL http]** e/ou **[!UICONTROL https]**), selecione a linha apropriada e clique em **[!UICONTROL Edit]**.
   * Insira uma porta diferente. Por padrão, a porta de escuta é 80 para http e 443 para https. Verifique se a nova porta está disponível.

     ![](assets/_migration_iis_3_611.png)

     >[!NOTE]
     >
     >Se o servidor IIS incluir vários sites para o Adobe Campaign com uma configuração avançada (porta compartilhada e endereços IP diferentes), entre em contato com o administrador.

1. Crie um novo site para o Adobe Campaign v7:

   * Clique com o botão direito na pasta **[!UICONTROL Sites]** e selecione **[!UICONTROL Add Web Site...]**.

     ![](assets/_migration_iis_4.png)

   * Insira o nome do site, **Adobe Campaign v7** por instância.
   * O caminho de acesso para o diretório básico do site não é usado, mas o campo **[!UICONTROL Physical access path]** deve ser inserido. Insira o caminho de acesso padrão do IIS: **C:\inetpub\wwwroot**.
   * Clique no botão **[!UICONTROL Connect as...]** como e verifique se a opção **[!UICONTROL Application user]** está selecionada.
   * Você pode deixar os valores padrão nos campos **[!UICONTROL IP address]** e **[!UICONTROL Port]**. Se quiser usar outros valores, verifique se o endereço IP e/ou a porta estão disponíveis.
   * Marque a caixa **[!UICONTROL Start Web site immediately]**.

     ![](assets/_migration_iis_5_7.png)

1. Execute o script **iis_neolane_setup.vbs** para configurar automaticamente os recursos usados pelo servidor do Adobe Campaign no diretório virtual criado anteriormente.

   * Este arquivo foi encontrado no diretório **`[Adobe Campaign v7]`\conf**, onde **`[Adobe Campaign v7]`** é o caminho de acesso para o diretório de instalação do Adobe Campaign. O comando para executar o script é o seguinte (para administradores):

     ```
     cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\conf
     cscript iis_neolane_setup.vbs
     ```

   * Clique em **[!UICONTROL OK]** para confirmar a execução do script.

     ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * Digite o número do site criado anteriormente para o Adobe Campaign v7 e clique em **[!UICONTROL OK]**.

     ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * Uma mensagem de confirmação deve aparecer:

     ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * Na guia **[!UICONTROL Content view]**, verifique se a configuração do Site está definida corretamente com os recursos do Adobe Campaign:

     ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

     >[!NOTE]
     >
     >Se a estrutura de árvore não for exibida, reinicie o IIS.
     >
     >As etapas de configuração do IIS a seguir estão detalhadas em [esta seção](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

<!--
## Security zones {#security-zones}

If you are migrating from v6.02 or earlier, you must configure your security zones before starting services. [Learn more](../../migration/using/general-configurations.md#security)
-->

## Reiniciar serviços {#re-starting-the-services}

Inicie os serviços do IIS e da Adobe Campaign em cada um dos seguintes servidores:

1. Servidor de rastreamento e redirecionamento.
1. Servidor Mid-sourcing.
1. Servidor de marketing.

Antes de passar para a próxima etapa, execute um teste completo da nova instalação, verifique se não há regressões e se tudo funciona.

## Excluir a versão anterior {#deleting-and-cleansing-adobe-campaign-previous-version}

Este é o procedimento para excluir o Adobe Campaign v6.1.

<!--

### For Adobe Campaign v5 {#adobe-campaign-v5}

Before you delete and cleanse the Adobe Campaign v5 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v5 once you are certain that no rollback is necessary.

1. In IIS, delete the **Neolane v5** website, then the **Neolane v5** application pool. 
1. Rename the **Neolane v5.back** folder as **Neolane v5**.
1. Uninstall Adobe Campaign v5 using the Add/remove components assistant. 

   ![](assets/migration_wizard_2.png)

1. Delete the **nlserver5** Windows service using the following command:

   ```
   sc delete nlserver5
   ```

1. Re-start the server.

### For Adobe Campaign v6.02 {#adobe-campaign-v6-02}

Before you delete and cleanse the Adobe Campaign v6.02 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v6.02 once you are certain that no rollback is necessary.

1. In IIS, delete the **Neolane v6** website, then the **Neolane v6** application pool. 
1. Rename the **Neolane v6.back** folder as **Neolane v6**.
1. Uninstall Adobe Campaign v6.02 using the Add/remove components assistant. 

   ![](assets/migration_wizard_2.png)

1. Re-start the server.

-->

Antes de excluir e limpar a instalação do Adobe Campaign v6, você deve aplicar as seguintes recomendações:

* Faça com que as equipes funcionais executem uma verificação completa da nova instalação.
* Desinstale o Adobe Campaign v6 somente depois de ter certeza de que nenhuma reversão é necessária.

1. No IIS, exclua o site do **Adobe Campaign v6** e o pool de aplicativos do **Adobe Campaign v6**.
1. Renomeie a pasta **Adobe Campaign v6.back** como **Adobe Campaign v6**.
1. Desinstale o Adobe Campaign v6 usando o assistente Adicionar/remover componentes.

   ![](assets/migration_wizard_2.png)

1. Reinicie o servidor.
