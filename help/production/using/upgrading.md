---
title: Atualização para uma nova criação
description: Saiba mais sobre as etapas técnicas para atualizar para uma nova versão
page-status-flag: never-activated
uuid: f24552d4-6bdf-411c-a1f2-b8f339c311f4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: f8e3633d-7232-44a5-842b-1a70c4f2bca2
translation-type: tm+mt
source-git-commit: cb2fb5a338220c54aba96b510a7371e520c2189e
workflow-type: tm+mt
source-wordcount: '1158'
ht-degree: 1%

---


# Atualização para uma nova compilação (local){#upgrading}

Antes de iniciar o processo de atualização, determine e confirme para qual versão do Adobe Campaign será atualizada e consulte as Notas de [versão](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>Recomendamos fazer um backup de banco de dados em cada instância antes de atualizar. Para obter mais informações, consulte [Backup](../../production/using/backup.md).\
>Para executar uma atualização, verifique se você tem a capacidade e as permissões para acessar instâncias e registros.

>[!NOTE]
>
>Consulte também o guia [de](../../installation/using/general-architecture.md) instalação e a introdução da atualização [da](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html) compilação.

## Windows {#in-windows}

Para atualizar o Adobe Campaign em uma nova versão ao fornecer uma nova compilação, o seguinte procedimento deve ser aplicado no Windows:

* [Desligar serviços](#shut-down-services),
* [Atualize o aplicativo](#upgrade-the-adobe-campaign-server-application)do servidor Adobe Campaign,
* [Sincronizar recursos](#synchronize-resources),
* [Reinicie os serviços](#restart-services).

Para saber como atualizar o console do cliente, consulte [esta seção](../../installation/using/client-console-availability-for-windows.md).

### Serviços de desligamento {#shut-down-services}

Para substituir todos os arquivos pela nova versão, é necessário encerrar todas as instâncias do serviço nlserver.

1. Desligue os seguintes serviços:

   * Serviços Web (IIS):

      **iisreset /stop**

   * Serviço Adobe Campaign: **net stop nlserver6**
   >[!IMPORTANT]
   >
   >Você também precisa verificar se o servidor de redirecionamento (webmdl) está parado, para que o arquivo **nlsrvmod.dll** usado pelo IIS possa ser substituído pela nova versão.

1. Verifique se nenhum tarefa está ativo executando o comando **nlserver pdump** . Deve aparecer o seguinte:

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   Você pode usar o Gerenciador de Tarefas do Windows para garantir que todos os processos sejam interrompidos.

### Atualizar o aplicativo do servidor Adobe Campaign {#upgrade-the-adobe-campaign-server-application}

Para executar o arquivo de atualização, aplique as seguintes etapas:

1. Execute **setup.exe**.

   Para baixar este arquivo, conecte-se ao portal [de distribuição de](https://experience.adobe.com/downloads) software usando suas credenciais de usuário. Learn more about Software distribution in [this page](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

1. Selecione o modo de instalação: choice **[!UICONTROL Update or repair]**
1. Clique em **[!UICONTROL Next]** .
1. Clique em **[!UICONTROL Finish]** .

   O programa de instalação copia os novos arquivos.

1. Quando a operação estiver concluída, clique em **[!UICONTROL Finish]** .

### Sincronizar recursos {#synchronize-resources}

Use a seguinte linha de comando:

**nlserver config -post-upgrade -allinnesse**

Isso permitirá que você realize as seguintes operações:

* Sincronizar recursos,
* schemas de atualização,
* atualize o banco de dados.

>[!NOTE]
>
>Essa operação deve ser executada apenas uma vez e somente em um servidor de aplicativos (**nlserver web**).

Em seguida, verifique se a sincronização gerou erros ou avisos. Para obter mais informações, consulte [Resolução de conflitos](#resolving-upgrade-conflicts)de atualização.

### Reiniciar serviços {#restart-services}

Os serviços a serem reiniciados são:

* Serviços Web (IIS):

   **iisreset /start**

* Serviço Adobe Campaign: **start net nlserver6**

## Linux {#in-linux}

Para atualizar o Adobe Campaign em uma nova versão quando uma nova compilação for entregue, o procedimento para Linux é o seguinte:

* [Obter pacotes](#obtain-updated-packages)atualizados,
* [Executar uma atualização](#perform-an-update),
* [Reinicialize o servidor](#reboot-the-web-server)da Web.

Para saber como atualizar o console do cliente, consulte [esta seção](../../installation/using/client-console-availability-for-linux.md).

>[!NOTE]
>
>A partir do build 8757, a biblioteca de terceiros não é mais necessária.

### Obter pacotes atualizados {#obtain-updated-packages}

Start recuperando ambos os pacotes atualizados do Adobe Campaign: conecte-se ao portal [de distribuição de](https://experience.adobe.com/downloads) software usando suas credenciais de usuário. Learn more about Software distribution in [this page](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

O arquivo é **nlserver6-v7-XXX.rpm**

### Executar uma atualização {#perform-an-update}

* Distribuição baseada em RPM (RedHat, SuSe)

   Para instalá-los, execute como raiz:

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   em que XXX é a versão do arquivo.

   O arquivo rpm tem dependências em pacotes que você pode encontrar nas distribuições CentOS/Red Hat. Se não quiser usar algumas dessas dependências, talvez seja necessário usar a opção &quot;nodeps&quot; de rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

* Distribuição baseada em DEB (Debian)

   Para instalá-los, execute como raiz:

   ```
   dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
   ```

>[!NOTE]
>
>Os procedimentos completos de instalação são detalhados na [presente seção](../../installation/using/installing-campaign-standard-packages.md). Os recursos são sincronizados automaticamente, no entanto, é necessário verificar se não ocorreram erros. Para obter mais informações, consulte [Resolução de conflitos](#resolving-upgrade-conflicts)de atualização.

### Reinicialize o servidor da Web {#reboot-the-web-server}

Você deve encerrar o Apache para que a nova biblioteca se torne aplicável.

Para fazer isso, execute o seguinte comando:

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* Seu script pode ser chamado de **httpd** em vez de **apache**.
>* É NECESSÁRIO executar esse comando até obter a seguinte resposta:

   >
   >   
   Essa operação é necessária para que o Apache aplique a nova biblioteca.


Em seguida, reinicie o Apache:

```
/etc/init.d/apache start
```

## Resolução de conflitos de atualização {#resolving-upgrade-conflicts}

Durante a sincronização de recursos, o comando **pós-atualização** permite detectar se a sincronização gerou erros ou avisos.

### Visualização do resultado da sincronização {#view-the-synchronization-result}

Há duas maneiras de visualizar o resultado da sincronização:

* Na interface da linha de comando, os erros são materializados por uma divisa tripla **>>** e a sincronização é interrompida automaticamente. Os avisos são materializados por uma divisa de duplo **>>** e devem ser resolvidos assim que a sincronização for concluída. No final da pós-atualização, um resumo é exibido no prompt de comando. Pode parecer com isto:

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Se o aviso disser respeito a um conflito de recursos, é necessário prestar atenção ao usuário para resolvê-lo.

* O arquivo de log **pós-upgrade_`<server version number>_<time of postupgrade>`.log** contém o resultado da sincronização. Está disponível por padrão no seguinte diretório: **`<installation directory>/var/<instance/postupgrade`**. Erros e avisos são indicados pelos atributos de erro e aviso.

### Resolução de conflitos {#resolving-conflicts}

Para resolver conflitos, aplique o seguinte processo:

1. Na árvore do Adobe Campaign, acesse **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. Selecione o conflito que deseja resolver na lista.

Há três maneiras de resolver um conflito:

* **[!UICONTROL Declare as resolved]** : requer uma intervenção do usuário antecipadamente.
* **[!UICONTROL Accept the new version]** : recomendado se os recursos fornecidos com o Adobe Campaign não tiverem sido alterados pelo usuário.
* **[!UICONTROL Keep the current version]** : significa que a atualização foi rejeitada.

   >[!IMPORTANT]
   >
   >Se você selecionar esse modo de resolução, talvez não se beneficie das correções na nova versão.

Se você optou por resolver o conflito manualmente, proceda da seguinte maneira:

1. Na seção inferior da janela, procure a string de **_conflito_** para localizar as entidades com conflitos. A entidade instalada com a nova versão contém o **novo** argumento, a entidade que corresponde à versão anterior contém o argumento **cus** .

   ![](assets/s_ncs_production_conflict002.png)

1. Exclua a versão que não deseja manter. Exclua a sequência de caracteres de **_conflito_argumento_** da entidade que você está mantendo.

   ![](assets/s_ncs_production_conflict003.png)

1. Vá para o conflito que você resolveu. Click the **[!UICONTROL Actions]** icon and select **[!UICONTROL Declare as resolved]** .
1. Salve as alterações: o conflito está agora resolvido.

### Práticas recomendadas {#best-practices}

Uma falha de atualização pode estar vinculada à configuração do banco de dados. Verifique se as configurações realizadas pelo administrador técnico e pelo administrador do banco de dados são compatíveis.

Por exemplo, um banco de dados unicode não deve autorizar apenas o armazenamento de dados LATIN1, etc.

## Avise os consoles cliente da atualização disponível {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Na máquina em que o servidor de aplicativos Adobe Campaign (**nlserver web**) está instalado, baixe e copie o arquivo

**setup-client-6.XXXX.exe**

em **[caminho do aplicativo]**datakitnlength jsp

Na próxima vez que os consoles cliente forem conectados, uma janela informará os usuários sobre a disponibilidade de uma atualização e oferta a possibilidade de baixá-la e instalá-la.

>[!NOTE]
>
>Verifique se o usuário IIS_XPG tem os direitos de leitura apropriados para esse arquivo de instalação e consulte o guia [de](../../installation/using/general-architecture.md) instalação para obter mais informações.

### Linux {#in-linux-1}

Na máquina em que o servidor de aplicativos Adobe Campaign (**nlserver web**) está instalado, recupere o seguinte pacote:

**setup-client-6.XXXX.exe**

e copie-o, salvando como **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

Na próxima vez que os consoles cliente forem conectados, uma janela informará os usuários sobre a disponibilidade de uma atualização e oferta a possibilidade de baixá-la e instalá-la.

>[!NOTE]
>
>Verifique se o usuário do Apache tem os direitos de leitura apropriados para esse arquivo de instalação e consulte o guia [de](../../installation/using/general-architecture.md) instalação para obter mais informações.

