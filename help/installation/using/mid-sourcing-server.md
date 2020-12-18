---
solution: Campaign Classic
product: campaign
title: Instalação de um servidor mid-sourcing na Campanha
description: Esta seção detalha a instalação e configuração de um servidor mid-sourcing na Campanha
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 0%

---


# Servidor Mid-sourcing{#mid-sourcing-server}

Esta seção detalha a instalação e configuração de um servidor mid-sourcing, bem como a implantação de uma instância que permite que terceiros enviem mensagens no modo **mid-sourcing**.

A arquitetura &quot;mid-sourcing&quot; é apresentada em [Mid-sourcing deployment](../../installation/using/mid-sourcing-deployment.md).

A instalação de um servidor mid-sourcing segue o mesmo processo que a instalação de um servidor da maneira normal (consulte a configuração padrão). É uma instância independente com seu próprio banco de dados que pode ser usada para executar delivery. Simplificando, ele contém uma configuração extra para permitir que instâncias remotas executem delivery através dele no modo mid-sourcing.

>[!CAUTION]
>
>Depois que o servidor mid-sourcing tiver sido configurado e os workflows [sync](../../workflow/using/transfer-to-mid-sourcing.md) tiverem sido executados pela primeira vez, certifique-se de não atualizar o nome interno das contas externas mid-sourcing.

## Etapas para instalar e configurar uma instância {#steps-for-installing-and-configuring-an-instance}

### Pré-requisitos para instalar e configurar uma instância {#prerequisites-for-installing-and-configuring-an-instance}

* JDK no servidor de aplicativos.
* Acesso a um servidor de banco de dados no servidor de aplicativos.
* Firewall configurado para abrir portas HTTP (80) ou HTTPS (443) no servidor mid-sourcing.

O procedimento a seguir detalha uma configuração usando um único servidor mid-sourcing. Também é possível usar vários servidores. Da mesma forma, também é possível enviar determinadas mensagens (como notificações de fluxo de trabalho, por exemplo) de uma configuração interna.

### Instalação e configuração do servidor de aplicativos para implantação do mid-sourcing {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

O procedimento de instalação é idêntico ao da instância independente. Consulte [Instalação e configuração (máquina única)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

No entanto, você deve aplicar o seguinte:

* Na etapa **5**, você deve desativar os módulos **mta** (delivery) e **inMail** (mensagens de rejeição). Entretanto, o módulo **wfserver** (fluxo de trabalho) deve permanecer ativado.

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

   Para obter mais informações, consulte [Ativando processos](../../installation/using/campaign-server-configuration.md#enabling-processes).

* As etapas **6**, **9** e **10** não são necessárias.
* Durante as etapas **12** e **13**, é necessário indicar a porta 8080 no URL de conexão (uma vez que o console se comunica diretamente com o Tomcat, não pelo servidor Web). O URL se torna [http://console.campaign.net:8080](http://console.campaign.net). Durante a etapa **13**, selecione o pacote **[!UICONTROL Issue towards Mid-sourcing]**, bem como os pacotes a serem instalados.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >O roteamento padrão dos delivery técnicos é automaticamente substituído pelo roteamento de e-mail via Mid-sourcing.

### Instalação e configuração do servidor mid-sourcing {#installing-and-configuring-the-mid-sourcing-server}

No console do cliente, localize o roteamento de e-mail usando a conta mid-sourcing **mid-sourcing (na pasta**/Administration/Conta externa/**).** Preencha as configurações **URL do servidor**, **account**, **password** e **URL do Mirror page** com as informações fornecidas pelo provedor do servidor que hospeda o servidor mid-sourcing. Teste a conexão.

>[!NOTE]
>
>A opção **mid-sourcingEmitter** cria dois workflows **Mid-sourcing**. É um processo que é executado por padrão a cada 1 hora e 20 minutos e coleta informações do delivery no servidor do mid-sourcing.

## Implantação de um servidor mid-sourcing {#deploying-a-mid-sourcing-server}

1. Instalação do servidor de aplicativos:

   >[!CAUTION]
   >
   >Se você instalar o servidor mid-sourcing e quiser instalar módulos Adobe Campaign adicionais, recomendamos o uso do módulo Delivery e não do módulo Campanha.

   Siga o mesmo procedimento que para a implantação padrão, selecionando apenas a opção **[!UICONTROL Mid-sourcing platform]**.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Configuração para recebimento no modo mid-sourcing

   Defina a senha da conta de envio: Na pasta **/Mid-sourcing/Access Management/Users/**, o operador **mid** é usado pela instância remota para envios no modo mid-sourcing. Você deve definir uma senha para esse operador e atribuí-la ao administrador da instância de envio.

   A opção **plataforma Mid-sourcing** cria as pastas padrão para armazenar os delivery enviados e o operador padrão que executa os envios.

## Multiplexação do servidor mid-sourcing {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>A multiplexação só é compatível com ambientes locais.

É possível que uma instância mid-sourcing seja compartilhada por várias instâncias de envio. Cada uma dessas instâncias deve ser associada a um operador no banco de dados do mid-sourcing. Para criar uma segunda conta no servidor mid-sourcing:

1. Crie uma pasta no nó **[!UICONTROL Mid-sourcing > Deliveries]** que será associada à conta mid-sourcing padrão (por exemplo: prod).
1. Crie uma pasta no nó **[!UICONTROL Mid-sourcing > Deliveries]** com o mesmo nome da conta (por exemplo: accept_test).

   ![](assets/mid_recette_account.png)

1. Em **[!UICONTROL Mid-sourcing > Access Management > Operators]**, crie uma nova conta.

   ![](assets/mid_recette_user_create.png)

1. Na guia **[!UICONTROL Access rights]**, conceda a esse operador os direitos do grupo **envios de Mid-sourcing**. Este direito de acesso está disponível em **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. Selecione a opção **[!UICONTROL Restrict to data in the sub-folders of]** e selecione a pasta delivery para restringir esse operador à pasta delivery mid-sourcing.

   ![](assets/mid_recette_user_restrictions.png)

1. Reinicie o módulo Web usando o seguinte comando: **nlserver restart web**.

É necessário alterar a configuração do servidor mid-sourcing no arquivo serverConf.xml. A seguinte linha deve ser adicionada à seção &quot;Gerenciamento de afinidades com endereços IP&quot;, na linha existente:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

O atributo &#39;@name&#39; deve respeitar as seguintes regras:

**&#39;marketing_account_operador_name&#39;.&#39;afinidade_name&#39;.&#39;afinidade_group&#39;**

&#39;marketing_account_operador_name&#39; está relacionado ao nome interno da conta de mid-sourcing declarada na instância de mid-sourcing.

&#39;afinidade_name&#39; está relacionado ao nome arbitrário dado à afinidade. Esse nome deve ser exclusivo. Os caracteres autorizados são `[a-z]``[A-Z]``[0-9]`. O objetivo é declarar um grupo de endereços IP públicos.

&#39;afinidade_group&#39; relaciona a subafinidade declarada no target mapping usado em cada um dos delivery. A última parte, incluindo o &quot;.&quot; é ignorada se não houver nenhuma Sub-afinidade. Os caracteres autorizados são `[a-z]``[A-Z]``[0-9]`.

Você deve parar e reiniciar o servidor para que a modificação seja considerada.

## Configurando o rastreamento em um servidor mid-sourcing {#configuring-tracking-on-a-mid-sourcing-server}

**Configuração do servidor mid-sourcing**

1. Vá para &#39;operadores&#39; e selecione o operador **[!UICONTROL mid]**.
1. Na guia **[!UICONTROL Frontal servers]**, digite os parâmetros de conexão do servidor de rastreamento.

   Para criar uma instância de rastreamento, insira o URL do servidor de rastreamento, a senha da conta interna do servidor de rastreamento e o nome da instância, sua senha e as máscaras de DNS associadas a ela.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Quando tiver inserido os parâmetros de conexão, clique em **[!UICONTROL Confirm the configuration]**.
1. Se necessário, especifique o local onde as imagens contidas nos delivery devem ser armazenadas. Para fazer isso, selecione um dos modos de publicação na lista suspensa.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Se você escolher a opção **[!UICONTROL Tracking server(s)]**, as imagens serão copiadas no servidor mid-sourcing.

**Configuração da plataforma do cliente**

1. Vá para a conta de roteamento mid-sourcing externa.
1. Na guia **[!UICONTROL Mid-Sourcing]**, especifique os parâmetros de conexão do servidor mid-sourcing.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Confirme sua configuração clicando em **[!UICONTROL Test the connection]**.
1. Declarar a instância de rastreamento referenciada no servidor mid-sourcing:

   Clique no link **[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   Especifique o nome da instância de rastreamento e confirme a conexão com o servidor de rastreamento.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Se o delivery de mensagens for gerenciado por vários servidores de mid-sourcing, selecione a opção **[!UICONTROL Routing with alternating mid-sourcing accounts]** e especifique os diferentes servidores.

![](assets/s_ncs_install_midsourcing_tracking04.png)

