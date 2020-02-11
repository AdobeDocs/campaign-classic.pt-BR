---
title: Instalação de um servidor de mid-sourcing no Adobe Campaign Classic
description: Esta seção detalha a instalação e configuração de um servidor de mid-sourcing no Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 9b891a64-d75e-44d2-8de2-17334e1b8dca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 34ee3d99-4ffb-4279-b994-5ab7abc7cf06
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 25ae29490f8b4c58dad499669f5bccff43de8b7a

---


# Servidor de fornecedores intermediários{#mid-sourcing-server}

Esta seção detalha a instalação e configuração de um servidor de mid-sourcing, bem como a implantação de uma instância que permite a terceiros enviar mensagens no modo de **mid-sourcing** .

A arquitetura de &quot;mid-sourcing&quot; é apresentada na implantação [de](../../installation/using/mid-sourcing-deployment.md)mid-sourcing.

A instalação de um servidor de mid-sourcing segue o mesmo processo de instalação de um servidor da maneira normal (consulte a configuração padrão). É uma instância independente com seu próprio banco de dados que pode ser usada para executar entregas. Simplificando, ele contém uma configuração extra para permitir que instâncias remotas executem entregas por meio dele no modo de mid-sourcing.

## Etapas para instalar e configurar uma instância {#steps-for-installing-and-configuring-an-instance}

### Pré-requisitos para instalar e configurar uma instância {#prerequisites-for-installing-and-configuring-an-instance}

* JDK no servidor de aplicativos.
* Acesso a um servidor de banco de dados no servidor de aplicativos.
* Firewall configurado para abrir portas HTTP (80) ou HTTPS (443) no servidor de mid-sourcing.

O procedimento a seguir detalha uma configuração usando um único servidor de mid-sourcing. Também é possível usar vários servidores. Da mesma forma, também é possível enviar determinadas mensagens (como notificações de fluxo de trabalho, por exemplo) de uma configuração interna.

### Instalação e configuração do servidor de aplicativos para implantação de mid-sourcing {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

O procedimento de instalação é idêntico ao da instância independente. Consulte [Instalação e configuração (máquina única)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

No entanto, você deve aplicar o seguinte:

* Na etapa **5**, você deve desativar os módulos **mta** (entrega) e **inMail** (e-mails de rejeição). Entretanto, o módulo **wfserver** (fluxo de trabalho) deve permanecer ativado.

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="false"/>  
       <wfserver autoStart="true"/>  
       <inMail autoStart="false"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

* Os passos **6**, **9** e **10** não são necessários.
* Durante as etapas **12** e **13**, é necessário indicar a porta 8080 no URL de conexão (já que o console se comunica diretamente com o Tomcat, não pelo servidor Web). O URL se torna [http://console.campaign.net:8080](http://console.campaign.net). Durante a etapa **13**, selecione o **[!UICONTROL Issue towards Mid-sourcing]** pacote e os que deseja instalar.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >O roteamento padrão de entregas técnicas é automaticamente substituído pelo roteamento de email por meio da Meid-sourcing.

### Instalação e configuração do servidor de mid-sourcing {#installing-and-configuring-the-mid-sourcing-server}

No console do cliente, localize o roteamento de **email usando a conta mid-sourcing** mid-sourcing (na pasta **/Administration/External accounts/** ). Preencha o **URL do servidor**, da **conta**, da **senha** e das configurações de URL **da página** Espelho com as informações fornecidas pelo provedor de servidor que hospeda o servidor de mid-sourcing. Teste a conexão.

>[!NOTE]
>
>A opção **mid-sourcingEmitter** cria dois fluxos de trabalho de **Meid-sourcing** . É um processo que é executado por padrão a cada 1 hora e 20 minutos e coleta informações de entrega no servidor de mid-sourcing.

## Implantação de um servidor de mid-sourcing {#deploying-a-mid-sourcing-server}

1. Instalação do servidor de aplicativos:

   >[!CAUTION]
   >
   >Se você instalar o servidor de mid-sourcing e quiser instalar módulos adicionais do Adobe Campaign, recomendamos o uso do módulo Entrega e não do módulo Campaign.

   Siga o mesmo procedimento que para a implantação padrão, selecionando somente a **[!UICONTROL Mid-sourcing platform]** opção.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Configuração para recebimento no modo mid-sourcing

   Defina a senha da conta de envio: Na pasta **/Mid-sourcing/Gerenciamento de acesso/Operadores/** , o operador **mid** é usado pela instância remota para envios no modo mid-sourcing. Você deve definir uma senha para esse operador e atribuí-la ao administrador da instância de envio.

   A opção plataforma **de** Mid-sourcing cria as pastas padrão para armazenar as entregas enviadas e o operador padrão que está executando as envias.

## Multiplexação do servidor de mid-sourcing {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>A multiplexação só é compatível com ambientes locais.

É possível que uma instância de mid-sourcing seja compartilhada por várias instâncias de envio. Cada uma dessas instâncias precisa ser associada a um operador no banco de dados de mid-sourcing. Para criar uma segunda conta no servidor de mid-sourcing:

1. Crie uma pasta no **[!UICONTROL Mid-sourcing > Deliveries]** nó que será associada à conta padrão de mid-sourcing (por exemplo: prod).
1. Crie uma pasta no **[!UICONTROL Mid-sourcing > Deliveries]** nó com o mesmo nome da conta (por exemplo: accept_test).

   ![](assets/mid_recette_account.png)

1. Em **[!UICONTROL Mid-sourcing > Access Management > Operators]**, crie uma nova conta.

   ![](assets/mid_recette_user_create.png)

1. Na **[!UICONTROL Access rights]** guia, atribua a esse operador os direitos do grupo de envios **de** Mid-sourcing. Este direito de acesso está disponível em **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. Selecione a **[!UICONTROL Restrict to data in the sub-folders of]** opção e a pasta de entregas para restringir esse operador à pasta de entregas de mid-sourcing.

   ![](assets/mid_recette_user_restrictions.png)

1. Reinicie o módulo Web usando o seguinte comando: Web **de reinicialização do** nlserver.

É necessário alterar a configuração do servidor de mid-sourcing no arquivo serverConf.xml. A seguinte linha deve ser adicionada à seção &quot;Gerenciamento de afinidades com endereços IP&quot;, na linha existente:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

O atributo &#39;@name&#39; deve respeitar as seguintes regras:

**&#39;marketing_account_operador_name&#39;.&#39;afinity_name&#39;.&#39;afinity_group&#39;**

&#39;marketing_account_operador_name&#39; está relacionado ao nome interno da conta de mid-sourcing declarada na instância de mid-sourcing.

&#39;afinity_name&#39; está relacionado ao nome arbitrário dado à afinidade. Esse nome deve ser exclusivo. Caracteres autorizados são `[a-z]``[A-Z]``[0-9]`. O objetivo é declarar um grupo de endereços IP públicos.

&#39;afinity_group&#39; relaciona a Sub-afinidade declarada no mapeamento de destino usado em cada uma das entregas. A última parte, incluindo o &quot;.&quot; é ignorada se não houver sub-afinidade. Caracteres autorizados são `[a-z]``[A-Z]``[0-9]`.

Você deve parar e reiniciar o servidor para que a modificação seja considerada.

## Configurando o rastreamento em um servidor de mid-sourcing {#configuring-tracking-on-a-mid-sourcing-server}

**Configuração do servidor de mid-sourcing**

1. Vá para &#39;operadores&#39; e selecione o operador **[!UICONTROL mid]**.
1. Na **[!UICONTROL Frontal servers]** guia, digite os parâmetros de conexão do servidor de rastreamento.

   Para criar uma instância de rastreamento, digite o URL do servidor de rastreamento, a senha da conta interna do servidor de rastreamento e o nome da instância, sua senha e as máscaras de DNS associadas a ela.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Quando tiver inserido os parâmetros de conexão, clique em **[!UICONTROL Confirm the configuration]**.
1. Se necessário, especifique o local onde as imagens contidas nas entregas serão armazenadas. Para fazer isso, selecione um dos modos de publicação na lista suspensa.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Se você escolher a **[!UICONTROL Tracking server(s)]** opção, as imagens serão copiadas no servidor de mid-sourcing.

**Configuração da plataforma do cliente**

1. Vá para a conta externa de roteamento de mid-sourcing.
1. Na **[!UICONTROL Mid-Sourcing]** guia, especifique os parâmetros de conexão do servidor de mid-sourcing.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Confirme sua configuração clicando em **[!UICONTROL Test the connection]**.
1. Declarar a instância de rastreamento referenciada no servidor de mid-sourcing:

   Clique no link **[!UICONTROL Use this platform as a platform to access the tracking servers]**,

   Especifique o nome da instância de rastreamento e confirme a conexão com o servidor de rastreamento.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Se a entrega de mensagens for gerenciada por vários servidores de mid-sourcing, selecione a opção **[!UICONTROL Routing with alternating mid-sourcing accounts]** e especifique os diferentes servidores.

![](assets/s_ncs_install_midsourcing_tracking04.png)

