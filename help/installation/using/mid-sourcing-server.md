---
product: campaign
title: Instalação de um servidor mid-sourcing no Campaign
description: Esta seção detalha a instalação e a configuração de um servidor mid-sourcing no Campaign
feature: Installation, Instance Settings
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 3e55d7f5-2858-4390-bba9-8fb5be0c3d98
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 3%

---

# Servidor Mid-sourcing{#mid-sourcing-server}



Esta seção detalha a instalação e a configuração de um servidor mid-sourcing, bem como a implantação de uma instância que permite a terceiros enviar mensagens no **mid-sourcing** modo.

A arquitetura de &quot;mid-sourcing&quot; é apresentada na [Implantação Mid-sourcing](../../installation/using/mid-sourcing-deployment.md).

A instalação de um servidor mid-sourcing segue o mesmo processo que a instalação de um servidor da maneira normal (consulte a configuração padrão). É uma instância independente com seu próprio banco de dados que pode ser usada para executar deliveries. Simplificando, ele contém uma configuração extra para permitir que as instâncias remotas executem deliveries por meio dele no modo de mid-sourcing.

>[!CAUTION]
>
>Depois que o servidor mid-sourcing for configurado e a variável [sincronizar workflows](../../workflow/using/about-technical-workflows.md) for executada pela primeira vez, certifique-se de não atualizar o nome interno das contas externas de mid-sourcing.

## Etapas para instalar e configurar uma instância {#steps-for-installing-and-configuring-an-instance}

### Pré-requisitos para instalar e configurar uma instância {#prerequisites-for-installing-and-configuring-an-instance}

* JDK no servidor de aplicativos.
* Acesso a um servidor de banco de dados no servidor de aplicativos.
* Firewall configurado para abrir portas HTTP (80) ou HTTPS (443) para o servidor mid-sourcing.

O procedimento a seguir detalha uma configuração usando um único servidor mid-sourcing. Também é possível usar vários servidores. Da mesma forma, também é possível enviar determinadas mensagens (como notificações de workflow, por exemplo) de uma configuração interna.

### Instalação e configuração do servidor de aplicativos para implantação de mid-sourcing {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

O procedimento de instalação é idêntico ao da instância independente. Consulte [Instalação e configuração (computador único)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

No entanto, você deve aplicar o seguinte:

* Na etapa **5**, Você deve desativar o **mta** (entrega) e **inMail** (emails devolvidos) módulos. A variável **wfserver** (workflow) no entanto, deve permanecer ativado.

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

  Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#enabling-processes).

* Etapas **6**, **9** e **10** não são necessárias.
* Durante as etapas **12** e **13**, é necessário indicar a porta 8080 no URL de conexão (já que o console se comunica com o Tomcat diretamente, não através do servidor Web). O URL torna-se `http://console.campaign.net:8080`. Durante a etapa **13**, selecione o **[!UICONTROL Issue towards Mid-sourcing]** pacote, bem como aqueles a serem instalados.

  ![](assets/s_ncs_install_midsourcing02.png)

  >[!CAUTION]
  >
  >O roteamento padrão de deliveries técnicos é substituído automaticamente pelo roteamento de email via Mid-sourcing.

### Instalação e configuração do servidor mid-sourcing {#installing-and-configuring-the-mid-sourcing-server}

No console do cliente, localize o **Roteamento de email usando mid-sourcing** conta de mid-sourcing (no **/Administration/External accounts/** pasta). Preencha o **URL do servidor**, **account**, **senha** e **URL da mirror page** com as informações fornecidas pelo provedor de servidor que hospeda o servidor mid-sourcing. Testa a conexão.

>[!NOTE]
>
>A variável **mid-sourcingEmitter** a opção cria dois **Mid-sourcing** fluxos de trabalho. É um processo que é executado por padrão a cada 1 hora e 20 minutos e coleta informações de delivery no servidor mid-sourcing.

## Implantar um servidor mid-sourcing {#deploying-a-mid-sourcing-server}

1. Instalando o servidor de aplicativos:

   >[!CAUTION]
   >
   >Se você instalar o servidor mid-sourcing e quiser instalar módulos adicionais do Adobe Campaign, recomendamos usar o módulo Delivery e não o módulo Campaign.

   Siga o mesmo procedimento para a disponibilização padrão, selecionando apenas o **[!UICONTROL Mid-sourcing platform]** opção.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Configuração de recebimento no modo de mid-sourcing

   Defina a senha da conta de envio: na caixa **/Mid-sourcing/Access Management/Operators/** pasta, a variável **mid** O operador é usado pela instância remota para envios no modo de mid-sourcing. Você deve definir uma senha para esse operador e fornecê-la ao administrador da instância de envio.

   A variável **Plataforma Mid-sourcing** cria as pastas padrão para armazenar os deliveries enviados e o operador padrão que executa os envios.

## Multiplexação do servidor mid-sourcing {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>A multiplexação só é compatível com ambientes locais.

É possível que uma instância mid-sourcing seja compartilhada por várias instâncias de envio. Cada uma dessas instâncias precisa ser associada a um operador no banco de dados de mid-sourcing. Para criar uma segunda conta no servidor mid-sourcing:

1. Crie uma pasta na **[!UICONTROL Mid-sourcing > Deliveries]** nó que será associado à conta mid-sourcing padrão (por exemplo: prod).
1. Crie uma pasta na **[!UICONTROL Mid-sourcing > Deliveries]** nó com o mesmo nome da conta (por exemplo: acceptance_test).

   ![](assets/mid_recette_account.png)

1. Entrada **[!UICONTROL Mid-sourcing > Access Management > Operators]**, crie uma nova conta.

   ![](assets/mid_recette_user_create.png)

1. No **[!UICONTROL Access rights]** dê a este operador os direitos de **Envios de mid-sourcing** grupo. Esse direito de acesso está disponível em **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. Selecione o **[!UICONTROL Restrict to data in the sub-folders of]** e selecione a pasta deliveries para restringir esse operador à pasta mid-sourcing deliveries.

   ![](assets/mid_recette_user_restrictions.png)

1. Reinicie o módulo Web usando o seguinte comando: **Web de reinicialização do nlserver**.

Você deve alterar a configuração do servidor mid-sourcing no arquivo serverConf.xml. A linha a seguir deve ser adicionada à seção &quot;Management of affinities with IP addresses&quot;, na linha existente:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

O atributo &#39;@name&#39; deve respeitar as seguintes regras:

**&#39;marketing_account_operator_name&#39;.&#39;affinity_name&#39;.&#39;affinity_group&#39;**

&#39;marketing_account_operator_name&#39; está relacionado ao nome interno da conta de mid-sourcing declarada na instância de mid-sourcing.

&#39;affinity_name&#39; está relacionado ao nome arbitrário fornecido para a afinidade. Esse nome deve ser exclusivo. Os caracteres autorizados são `[a-z]``[A-Z]``[0-9]`. O objetivo é declarar um grupo de endereços IP públicos.

&#39;affinity_group&#39; relaciona a subafinidade declarada no target mapping usado em cada um dos deliveries. A última parte, incluindo o caractere &#39;.&#39; é ignorado se não houver Subafinidade. Os caracteres autorizados são `[a-z]``[A-Z]``[0-9]`.

Você deve interromper e reiniciar o servidor para que a modificação seja considerada.

## Configuração do rastreamento em um servidor mid-sourcing {#configuring-tracking-on-a-mid-sourcing-server}

**Configuração do servidor mid-sourcing**

1. Acesse &quot;operators&quot; e selecione o operador **[!UICONTROL mid]**.
1. No **[!UICONTROL Frontal servers]** insira os parâmetros de conexão do servidor de rastreamento.

   Para criar uma instância de rastreamento, insira o URL do servidor de rastreamento, a senha da conta interna do servidor de rastreamento e o nome da instância, sua senha e as máscaras DNS associadas a ela.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Quando tiver informado os parâmetros de conexão, clique em **[!UICONTROL Confirm the configuration]**.
1. Se necessário, especifique o local onde as imagens contidas nos deliveries devem ser armazenadas. Para fazer isso, selecione um dos modos de publicação na lista suspensa.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Se você escolher a variável **[!UICONTROL Tracking server(s)]** , as imagens serão copiadas no servidor mid-sourcing.

**Configuração da plataforma do cliente**

1. Vá para a conta externa de roteamento de mid-sourcing.
1. Na guia **[!UICONTROL Mid-Sourcing]**, especifique os parâmetros de conexão do servidor mid-sourcing.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Confirme sua configuração clicando em **[!UICONTROL Test the connection]**.
1. Declarar a instância de rastreamento referenciada no servidor mid-sourcing:

   Clique no link **[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   Especifique o nome da instância de rastreamento e confirme a conexão com o servidor de rastreamento.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Se o delivery de mensagens for gerenciado por vários servidores mid-sourcing, selecione a opção **[!UICONTROL Routing with alternating mid-sourcing accounts]** e especifique os diferentes servidores.

![](assets/s_ncs_install_midsourcing_tracking04.png)
