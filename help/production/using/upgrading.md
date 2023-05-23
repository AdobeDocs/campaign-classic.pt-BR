---
product: campaign
title: Atualização para um novo build
description: Saiba mais sobre as etapas técnicas para atualizar para uma nova build
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 4%

---

# Atualização para uma nova build (no local){#upgrading}



Antes de iniciar o processo de atualização, determine e confirme para qual versão do Adobe Campaign está sendo atualizada e consulte o [Notas de versão](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>* A Adobe recomenda fazer um backup do banco de dados em cada instância antes da atualização. Para obter mais informações, consulte [esta seção](../../production/using/backup.md).
>* Para executar uma atualização, verifique se você tem a capacidade e as permissões para acessar instâncias e logs.
>* Ler [nesta seção](../../installation/using/general-architecture.md) e a variável [atualização de build](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html) antes de iniciar.
>


## Windows {#in-windows}

Em um ambiente Windows, siga as etapas abaixo para atualizar o Adobe Campaign para uma nova build:

* [Desligar serviços](#shut-down-services),
* [Atualizar o servidor de aplicativos](#upgrade-the-adobe-campaign-server-application),
* [Sincronizar recursos](#synchronize-resources),
* [Reiniciar serviços](#restart-services).

Para saber como atualizar o console do cliente, consulte [nesta seção](../../installation/using/client-console-availability-for-windows.md).

### Desligar serviços {#shut-down-services}

Para substituir todos os arquivos pela nova versão, é necessário desligar todas as instâncias do serviço nlserver.

1. Encerre os seguintes serviços:

   * Serviços Web (IIS):

      **iisreset /stop**

   * Serviço Adobe Campaign: **net stop nlserver6**
   >[!IMPORTANT]
   >
   >Verifique também se o servidor de redirecionamento (webmdl) está parado, para que o **nlsrvmod.dll** arquivo usado pelo IIS pode ser substituído pela nova versão.

1. Verifique se nenhuma tarefa está ativa executando o **despejo nlserver** comando. O seguinte deve aparecer:

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   Você pode usar o Gerenciador de tarefas do Windows para verificar se todos os processos foram interrompidos.

### Atualizar o aplicativo do servidor do Adobe Campaign {#upgrade-the-adobe-campaign-server-application}

Para executar o arquivo de upgrade, siga as etapas abaixo:

1. Executar **setup.exe**.

   Para baixar esse arquivo, conecte-se à [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) usando suas credenciais de usuário. Saiba mais sobre a Distribuição de software em [esta página](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=pt-BR).

1. Selecione o modo de instalação: escolha **[!UICONTROL Update or repair]**
1. Clique em **[!UICONTROL Next]** .
1. Clique em **[!UICONTROL Finish]** .

   O programa de instalação copia os novos arquivos.

1. Quando a operação estiver concluída, clique em **[!UICONTROL Finish]** .

### Sincronizar recursos {#synchronize-resources}

Usar a seguinte linha de comando:

**nlserver config -postupgrade -allinstances**

Isso permitirá que você execute as seguintes operações:

* Sincronizar recursos
* Atualizar esquemas
* atualizar o banco de dados

>[!NOTE]
>
>Esta operação deve ser executada apenas uma vez e somente em um (**nlserver web**) servidor de aplicativos.

Em seguida, verifique se a sincronização gerou erros ou avisos. Para obter mais informações, consulte [Resolução de conflitos de atualização](#resolving-upgrade-conflicts).

### Reiniciar serviços {#restart-services}

Os serviços a serem reiniciados são:

* Serviços Web (IIS):

   **iisreset /start**

* Serviço Adobe Campaign: **net start nlserver6**

## Linux {#in-linux}

Em um ambiente Linux, siga as etapas abaixo para atualizar o Adobe Campaign para uma nova build:

* [Baixar os pacotes atualizados](#obtain-updated-packages),
* [Executar a atualização](#perform-an-update),
* [Reinicializar o servidor Web](#reboot-the-web-server).

[Saiba mais sobre a disponibilidade do Console do cliente](../../installation/using/client-console-availability-for-windows.md).

>[!NOTE]
>
>A partir da build 8757, a biblioteca de terceiros não é mais necessária.

### Obter pacotes atualizados {#obtain-updated-packages}

Comece recuperando ambos os pacotes atualizados do Adobe Campaign: conecte-se à [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) usando suas credenciais de usuário. Saiba mais sobre a Distribuição de software em [esta página](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=pt-BR).

O arquivo é **nlserver6-v7-XXX.rpm**

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
>Os procedimentos completos de instalação são detalhados em [nesta seção](../../installation/using/installing-campaign-standard-packages.md). Os recursos são sincronizados automaticamente, no entanto, você precisa garantir que nenhum erro ocorreu. Para obter mais informações, consulte [Resolver conflitos de atualização](#resolving-upgrade-conflicts).

### Reinicializar o servidor Web {#reboot-the-web-server}

Você deve desligar o Apache para que a nova biblioteca se torne aplicável.

Para fazer isso, execute o seguinte comando:

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* Seu script pode ser chamado **https** em vez de **apache**.
>* Você DEVE executar este comando até obter a seguinte resposta:

   >
   >   Essa operação é necessária para que o Apache aplique a nova biblioteca.


Em seguida, reinicie o Apache:

```
/etc/init.d/apache start
```

## Resolver conflitos de atualização {#resolving-upgrade-conflicts}

Durante a sincronização de recursos, a variável **pós-atualização** permite detectar se a sincronização gerou erros ou avisos.

### Exibir o resultado da sincronização {#view-the-synchronization-result}

Há duas maneiras de exibir o resultado da sincronização:

* Na interface da linha de comando, os erros são materializados por uma divisa tripla **>>>** e a sincronização é interrompida automaticamente. Os avisos são materializados por uma divisa dupla **>>** e devem ser resolvidos quando a sincronização estiver concluída. No final da pós-atualização, um resumo é exibido no prompt de comando. Ele pode ter esta aparência:

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Se o aviso aborda um conflito de recursos, é necessária atenção do usuário para resolvê-lo.

* A variável **pós-atualização_`<server version number>_<time of postupgrade>`.log** o arquivo de log contém o resultado da sincronização. Ela está disponível por padrão no seguinte diretório: **`<installation directory>/var/<instance/postupgrade`**. Os erros e avisos são indicados pelos atributos de erro e aviso.

### Resolver conflitos {#resolving-conflicts}

Para resolver conflitos, aplique o seguinte processo:

1. Na árvore do Adobe Campaign, acesse **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. Selecione o conflito que deseja resolver na lista.

Há três maneiras de resolver um conflito:

* **[!UICONTROL Declare as resolved]** : requer a intervenção do usuário antecipadamente.
* **[!UICONTROL Accept the new version]** : recomendado se os recursos fornecidos com o Adobe Campaign não tiverem sido alterados pelo usuário.
* **[!UICONTROL Keep the current version]** : significa que a atualização foi rejeitada.

   >[!IMPORTANT]
   >
   >Se você selecionar esse modo de resolução, talvez não se beneficie das correções na nova versão.

Se você optou por resolver o conflito manualmente, proceda da seguinte maneira:

1. Na seção inferior da janela, procure pela variável **_conflito_** string para localizar as entidades com conflitos. A entidade instalada com a nova versão contém a variável **novo** argumento, a entidade que corresponde à versão anterior contém a variável **cus** argumento.

   ![](assets/s_ncs_production_conflict002.png)

1. Exclua a versão que não deseja manter. Exclua o **_argumento_de_conflito_** string da entidade que você está mantendo.

   ![](assets/s_ncs_production_conflict003.png)

1. Vá para o conflito que você resolveu. Clique em **[!UICONTROL Actions]** e selecione **[!UICONTROL Declare as resolved]** .
1. Salve as alterações: o conflito agora está resolvido.

### Práticas recomendadas {#best-practices}

Uma falha de atualização pode estar vinculada à configuração do banco de dados. Verifique se as configurações executadas pelo administrador técnico e pelo administrador do banco de dados são compatíveis.

Por exemplo, um banco de dados unicode não deve apenas autorizar o armazenamento de dados LATIN1 etc.

## Avisar os consoles cliente sobre a atualização disponível {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Na máquina em que o servidor de aplicativos do Adobe Campaign está instalado (**nlserver web**), baixe e copie o arquivo  **setup-client-6.XXXX.exe** i n **[caminho do aplicativo]/datakit/nl/eng/jsp**.

Na próxima vez que os consoles do cliente estiverem conectados, uma janela informará os usuários sobre a disponibilidade de uma atualização e oferecerá a eles a possibilidade de baixá-la e instalá-la.

>[!NOTE]
>
>Verifique se o usuário IIS_XPG tem os direitos de leitura apropriados para esse arquivo de instalação e consulte [guia de instalação](../../installation/using/general-architecture.md) para obter mais informações.

### Linux {#in-linux-1}

Na máquina em que o servidor de aplicativos do Adobe Campaign (**nlserver web**) estiver instalado, recupere o  **setup-client-6.XXXX.exe** empacotar e copiar, salvando como **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

Na próxima vez que os consoles do cliente estiverem conectados, uma janela informará os usuários sobre a disponibilidade de uma atualização e oferecerá a eles a possibilidade de baixá-la e instalá-la.

>[!NOTE]
>
>Verifique se o usuário do Apache tem os direitos de leitura apropriados para esse arquivo de instalação e consulte o [guia de instalação](../../installation/using/general-architecture.md) para obter mais informações.
