---
product: campaign
title: Atualização para um novo build
description: Saiba mais sobre as etapas técnicas para atualizar para uma nova build
feature: Monitoring, Upgrade
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: fee880f4b200b322c2b2a0034f17975993c862b3
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 2%

---

# Atualização para uma nova build (no local){#upgrading}

Antes de iniciar o processo de atualização, determine e confirme para qual versão do Adobe Campaign está sendo atualizada e consulte as [Notas de Versão](../../rn/using/latest-release.md).

>[!IMPORTANT]
>
>* A Adobe recomenda fazer um backup do banco de dados em cada instância antes da atualização. Para obter mais informações, consulte [esta seção](../../production/using/backup.md).
>* Para executar uma atualização, verifique se você tem a capacidade e as permissões para acessar instâncias e logs.
>* Leia [esta seção](../../installation/using/general-architecture.md) e o capítulo de [atualização de compilação](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html) antes de iniciar.
>

## Windows {#in-windows}

Em um ambiente Windows, siga as etapas abaixo para atualizar o Adobe Campaign para uma nova build:

* [Desligar serviços](#shut-down-services),
* [Atualizar o servidor de aplicativos](#upgrade-the-adobe-campaign-server-application),
* [Sincronizar recursos](#synchronize-resources),
* [Reiniciar serviços](#restart-services).

Para saber como atualizar o console do cliente, consulte [esta seção](../../installation/using/client-console-availability-for-windows.md).

### Desligar serviços {#shut-down-services}

Para substituir todos os arquivos pela nova versão, é necessário desligar todas as instâncias do serviço nlserver.

1. Encerre os seguintes serviços:

   * Serviços Web (IIS):

     **iisreset /stop**

   * Serviço Adobe Campaign: **net stop nlserver6**

   >[!IMPORTANT]
   >
   >Você também precisa verificar se o servidor de redirecionamento (webmdl) está parado, para que o arquivo **nlsrvmod.dll** usado pelo IIS possa ser substituído pela nova versão.

1. Verifique se nenhuma tarefa está ativa executando o comando **nlserver pdump**. O seguinte deve aparecer:

   ```sql
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   Você pode usar o Gerenciador de tarefas do Windows para verificar se todos os processos foram interrompidos.

### Atualizar o aplicativo do servidor do Adobe Campaign {#upgrade-the-adobe-campaign-server-application}

Para executar o arquivo de upgrade, siga as etapas abaixo:

1. Execute **setup.exe**.

   Para baixar este arquivo, conecte-se ao [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) usando suas credenciais de usuário. Saiba mais sobre a Distribuição de softwares em [esta página](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=pt-BR).

1. Selecione o modo de instalação: escolha **[!UICONTROL Update or repair]**
1. Clique em **[!UICONTROL Next]**.
1. Clique em **[!UICONTROL Finish]**.

   O programa de instalação copia os novos arquivos.

1. Quando a operação for concluída, clique em **[!UICONTROL Finish]**.

### Sincronizar recursos {#synchronize-resources}

Usar a seguinte linha de comando:

**nlserver config -postupgrade -allinstances**

Isso permitirá que você execute as seguintes operações:

* Sincronizar recursos
* Atualizar esquemas
* atualizar o banco de dados

>[!NOTE]
>
>Esta operação deve ser executada apenas uma vez e somente em um servidor de aplicativos (**nlserver web**).

Em seguida, verifique se a sincronização gerou erros ou avisos. Para obter mais informações, consulte [Resolvendo conflitos de atualização](#resolving-upgrade-conflicts).

### Reiniciar serviços {#restart-services}

Os serviços a serem reiniciados são:

* Serviços Web (IIS):

  **iisreset /start**

* Serviço Adobe Campaign: **net start nlserver6**

## Linux {#in-linux}

Em um ambiente Linux, siga as etapas abaixo para atualizar o Adobe Campaign para uma nova build:

* [Baixe os pacotes atualizados](#obtain-updated-packages),
* [Executar a atualização](#perform-an-update),
* [Reinicialize o servidor Web](#reboot-the-web-server).

[Saiba mais sobre a disponibilidade do Console do Cliente](../../installation/using/client-console-availability-for-windows.md).

### Obter pacotes atualizados {#obtain-updated-packages}

Comece recuperando ambos os pacotes atualizados do Adobe Campaign: conecte-se ao [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) usando suas credenciais de usuário. Saiba mais sobre a Distribuição de softwares em [esta página](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=pt-BR).

O arquivo é **nlserver6-v7-XXX.rpm**

>[!AVAILABILITY]
>
>A partir da v7.4.1, as bibliotecas XML para pacotes RPM Linux não serão mais incluídas no Campaign. Você deve instalar essas bibliotecas.
> 


### Executar uma atualização {#perform-an-update}

* Distribuição baseada em RPM (RedHat, SuSe)

  Para instalá-los, execute como raiz:

  ```
  $rpm -Uvh nlserver6-v7-XXXX.rpm
  ```

  XXX é a versão do arquivo.

  O arquivo rpm depende dos pacotes que podem ser encontrados nas distribuições CentOS/Red Hat. Se você não quiser usar algumas dessas dependências, talvez seja necessário usar a opção &quot;nodeps&quot; do rpm:

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
>Os procedimentos completos de instalação estão detalhados em [esta seção](../../installation/using/installing-campaign-standard-packages.md). Os recursos são sincronizados automaticamente, no entanto, você precisa garantir que nenhum erro ocorreu. Para obter mais informações, consulte [Resolver conflitos de atualização](#resolving-upgrade-conflicts).

### Reinicializar o servidor Web {#reboot-the-web-server}

Você deve desligar o Apache para que a nova biblioteca se torne aplicável.

Para fazer isso, execute o seguinte comando:

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* Seu script pode ser chamado **httpd** em vez de **apache**.
>* Você DEVE executar este comando até obter a seguinte resposta:
>
>   Essa operação é necessária para que o Apache aplique a nova biblioteca.

Em seguida, reinicie o Apache:

```
/etc/init.d/apache start
```

## Resolver conflitos de atualização {#resolving-upgrade-conflicts}

Durante a sincronização de recursos, o comando **postupgrade** permite detectar se a sincronização gerou erros ou avisos.

### Exibir o resultado da sincronização {#view-the-synchronization-result}

Há duas maneiras de exibir o resultado da sincronização:

* Na interface de linha de comando, os erros são materializados por uma divisa tripla **>>** e a sincronização é interrompida automaticamente. Os avisos são materializados por uma divisa dupla **>** e devem ser resolvidos quando a sincronização estiver concluída. No final da pós-atualização, um resumo é exibido no prompt de comando. Ele pode ter esta aparência:

  ```
  2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
  2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
  2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  Se o aviso aborda um conflito de recursos, é necessária atenção do usuário para resolvê-lo.

* O arquivo de log **postupgrade_`<server version number>_<time of postupgrade>`.log** contém o resultado da sincronização. Está disponível por padrão no seguinte diretório: **`<installation directory>/var/<instance/postupgrade`**. Os erros e avisos são indicados pelos atributos de erro e aviso.

### Resolver conflitos {#resolving-conflicts}

Para resolver conflitos, aplique o seguinte processo:

1. Na árvore do Adobe Campaign, vá para **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. Selecione o conflito que deseja resolver na lista.

Há três maneiras de resolver um conflito:

* **[!UICONTROL Declare as resolved]** : requer intervenção do usuário antecipadamente.
* **[!UICONTROL Accept the new version]** : recomendado se os recursos fornecidos com o Adobe Campaign não tiverem sido alterados pelo usuário.
* **[!UICONTROL Keep the current version]** : significa que a atualização foi rejeitada.

  >[!IMPORTANT]
  >
  >Se você selecionar esse modo de resolução, talvez não se beneficie das correções na nova versão.

Se você optou por resolver o conflito manualmente, proceda da seguinte maneira:

1. Na seção inferior da janela, procure a sequência de caracteres **_conflito_** para localizar as entidades com conflitos. A entidade instalada com a nova versão contém o argumento **new**. A entidade que corresponde à versão anterior contém o argumento **cus**.

   ![](assets/s_ncs_production_conflict002.png)

1. Exclua a versão que não deseja manter. Exclua a cadeia de caracteres **_conflict_argument_** da entidade que você está mantendo.

   ![](assets/s_ncs_production_conflict003.png)

1. Vá para o conflito que você resolveu. Clique no ícone **[!UICONTROL Actions]** e selecione **[!UICONTROL Declare as resolved]** .
1. Salve as alterações: o conflito agora está resolvido.

### Práticas recomendadas {#best-practices}

Uma falha de atualização pode estar vinculada à configuração do banco de dados. Verifique se as configurações executadas pelo administrador técnico e pelo administrador do banco de dados são compatíveis.

Por exemplo, um banco de dados unicode não deve apenas autorizar o armazenamento de dados LATIN1 etc.

## Avisar os consoles cliente sobre a atualização disponível {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Na máquina em que o servidor de aplicativos do Adobe Campaign está instalado (**nlserver web**), baixe e copie o arquivo **setup-client-6.XXXX.exe** no **[caminho do aplicativo]/datakit/nl/eng/jsp**.

Na próxima vez que os consoles do cliente estiverem conectados, uma janela informará os usuários sobre a disponibilidade de uma atualização e oferecerá a eles a possibilidade de baixá-la e instalá-la.

>[!NOTE]
>
>Verifique se o usuário IIS_XPG tem os direitos de leitura apropriados para este arquivo de instalação e consulte o [guia de instalação](../../installation/using/general-architecture.md) para obter mais informações.

### Linux {#in-linux-1}

Na máquina em que o servidor de aplicativos do Adobe Campaign (**nlserver web**) está instalado, recupere o pacote **setup-client-6.XXXX.exe** e copie-o, salvando como **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

Na próxima vez que os consoles do cliente estiverem conectados, uma janela informará os usuários sobre a disponibilidade de uma atualização e oferecerá a eles a possibilidade de baixá-la e instalá-la.

>[!NOTE]
>
>Verifique se o usuário do Apache tem os direitos de leitura apropriados para este arquivo de instalação e consulte o [guia de instalação](../../installation/using/general-architecture.md) para obter mais informações.
