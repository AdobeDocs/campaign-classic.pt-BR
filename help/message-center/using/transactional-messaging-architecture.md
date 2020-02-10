---
title: Arquitetura de mensagens transacionais do Adobe Campaign Classic
description: Esta seção descreve a arquitetura de mensagens transacionais do Adobe Campaign Classic.
page-status-flag: never-activated
uuid: a8fe7a37-6df7-49f4-838f-97a72e4a38f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: a910d5fe-cef4-47d8-b3bc-0055ef0d1afd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 25ae29490f8b4c58dad499669f5bccff43de8b7a

---


# Arquitetura de mensagens transacionais{#transactional-messaging-architecture}

## Sobre as instâncias de execução e de controle {#about-execution-and-control-instances}

No Adobe Campaign, os recursos de mensagens transacionais (também conhecidos como Centro de mensagens) foram projetados para oferecer suporte à escalabilidade e um serviço 24 horas por dia, 7 dias por semana. Ele é composto por várias instâncias:

* uma instância de controle, onde os templates de mensagem são criados,
* uma ou mais instâncias de execução que recebem eventos e entregam mensagens.

Para usar esses recursos, os usuários do Adobe Campaign fazem logon na instância de controle para criar templates de mensagem transacional, gerar a pré-visualização da mensagem usando uma lista de propagação, exibir relatórios e monitorar instâncias de execução.

As instâncias de execução recebem eventos, os vinculam a templates de mensagem transacional e enviam uma mensagem personalizada para cada recipient.

![](assets/messagecenter_diagram.png)

## Suporte a várias instâncias de controle {#supporting-several-control-instances}

>[!CAUTION]
>
>O compartilhamento de um cluster de execução com várias instâncias de controle só é compatível com ambientes locais.

É possível compartilhar um cluster de execução entre várias instâncias de controle. Por exemplo, se você gerenciar várias lojas especializadas, será possível configurar uma instância de controle por marca e vinculá-las para o mesmo cluster de execução.

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>Para obter mais informações sobre a configuração necessária, consulte [Usando várias instâncias](../../message-center/using/creating-a-shared-connection.md#using-several-control-instances)de controle.

## Instalação de instâncias {#installing-instances}

Deve-se tomar várias precauções ao instalar os pacotes de mensagens transacionais. A Adobe recomenda que você trabalhe em um ambiente de teste antes de colocá-los em produção. Você também precisará ter uma licença compatível com Adobe Campaign. Para obter mais informações, entre em contato com o executivo da sua conta Adobe.

>[!CAUTION]
>
>A instância de controle e a instância de execução devem ser instaladas em máquinas diferentes. Elas não podem compartilhar a mesma instância do Campaign.

Se precisar usar vários canais, instale e configure pacotes relacionados antes de instalar pacotes de mensagens transacionais. Consulte [Adicionar um canal](#adding-a-delivery-channel)de entrega.

* To install the control instance on your machine, select the **[!UICONTROL Transactional message control]** module.

   ![](assets/messagecenter_install_controlinstance_001.png)

* To install the execution instance on your machine, select the **[!UICONTROL Transactional message execution]** module.

   ![](assets/messagecenter_install_executioninstance_001.png)

## Adição de um canal de delivery {#adding-a-delivery-channel}

A adição de um canal de delivery (canal móvel, canal de aplicativo móvel, etc.) deverá ser executada antes de instalar o pacote de mensagens transacionais. Caso tenha iniciado um projeto de mensagens transacionais no canal de email e decida, durante o projeto, adicionar um novo canal, siga estas etapas:

1. Install the channel you need, for example the **Mobile channel**, using the package import wizard ( **[!UICONTROL Tools > Advanced > Import package... > Adobe Campaign Package]** ).
1. Execute uma importação de arquivo ( **[!UICONTROL Tools > Advanced > Import package... > File]** ) e selecione o arquivo ****`[Your language]`**datakitnmspackagemessageCenter.xml** .
1. In the **[!UICONTROL XML content of the data to import]** , keep only the delivery template that corresponds to the added channel. For example, if you have added the **Mobile channel**, keep only the **entities** element that corresponds to the **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). Caso tenha adicionado o **Canal de Aplicativo Móvel**, mantenha somente a **mensagem transacional do iOS** (iosTriggerMessage) e a **mensagem transacional do Android** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

## Mensagens transacionais e interação de entrada {#transactional-messages-and-inbound-interaction}

Quando combinadas com o módulo de Interação de entrada, as mensagens transacionais permitem que você insira uma oferta de marketing dedicada ao recipient na mensagem.

>[!NOTE]
>
>O módulo de Interação é detalhado em [Interação](../../interaction/using/interaction-and-offer-management.md).

Para usar mensagens transacionais com Interação, você precisa aplicar as seguintes configurações:

* Instale o pacote de **Interação** na instância de controle e configure seu catálogo de ofertas.

   >[!CAUTION]
   >
   >Não replique as ofertas nas instâncias de execução.

* O evento deverá incluir um identificador vinculado aos recipients, para personalizar ofertas. O atributo **@externalId** deverá conter o valor desse identificador. A **Interação** é configurada por padrão para identificar o recipient da chave primária:

   ```
   <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="1242"> 
   ```

   Você poderá configurar a **Interação** para que a identificação ocorra no campo de sua escolha, por exemplo, no endereço de email:

   ```
   <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="john.doe@yahoo.com"> 
   ```

Crie seus templates do delivery da maneira que faria com uma campanha de email:

* Adicione a oferta ao seu template de mensagem transacional.
* Verifique a pré-visualização, envie uma prova e publique o template.

Você também precisará habilitar o modo unitário nos espaços de oferta. Para obter mais informações, consulte [esta seção](../../interaction/using/creating-offer-spaces.md).

## Mensagens transacionais e notificações por push {#transactional-messaging-and-push-notifications}

Quando combinado com o módulo de canal de Aplicativo móvel, as mensagens transacionais permitem que você envie mensagens transacionais por meio de notificações em dispositivos móveis.

>[!NOTE]
>
>O canal de Aplicativo Móvel é detalhado [nesta seção](../../delivery/using/about-mobile-app-channel.md).

Para usar módulos de mensagem transacional com o Canal de aplicativo móvel, você precisará aplicar as seguintes configurações:

1. Instale o pacote **Canal de aplicativo móvel** nas instâncias de controle e de execução.
1. Replique o serviço do Adobe Campaign do tipo **Aplicativo móvel**, bem como os aplicativos móveis que ele contém nas instâncias de execução.

O evento deverá conter os seguintes elementos:

* A ID do dispositivo móvel (**registrationId** para Android e **deviceToken** para iOS). Essa ID representa o &quot;endereço&quot; para o qual a notificação será enviada.
* O link para o aplicativo móvel ou a chave de integração (**uuid**) que permite recuperar as informações de conexão específicas do aplicativo.
* O canal para o qual a notificação será enviada (**wantChannel**): 41 para iOS e 42 para Android
* Todos os dados úteis para personalização

Este é um exemplo de um evento que contém essas informações:

```
<SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Body>
     <urn:PushEvent>
         <urn:sessiontoken>mc/</urn:sessiontoken>
         <urn:domEvent>

              <rtEvent wishedChannel="41" type="DELIVERY" registrationToken="2cefnefzef758398493srefzefkzq483974">
                <mobileApp _operation=”none” uuid="com.adobe.NeoMiles"/>
                <ctx>
                    <deliveryTime>1:30 PM</deliveryTime>
                    <url>http://www.adobe.com</url>
                </ctx>
              </rtEvent>

         </urn:domEvent>
     </urn:PushEvent>           
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

>[!NOTE]
>
>A criação de templates de mensagem permanece igual.

## Mensagens transacionais e LINE {#transactional-messaging-and-line}

Combinadas com o Canal LINE, as mensagens transacionais permitem enviar mensagens em tempo real no aplicativo LINE instalado em dispositivos móveis do consumidor. Isso é usado para enviar a mensagem de boas-vindas quando um usuário do LINE adiciona a página da marca.

Para usar o módulo de mensagem transacional com o LINE, os seguintes elementos são necessários para a configuração na sua instância de **marketing** e na sua instância de **execução**:

* Install the **[!UICONTROL LINE Connect]** package on both instances.
* Install the **[!UICONTROL Transactional message control]** package on your marketing instance, and the **[!UICONTROL Transactional message execution]** package on the execution instance.
* Cria uma **conta externa** e o **serviço** do LINE em ambas as instâncias com nomes idênticos para que sejam sincronizados. Para obter mais informações sobre como criar uma conta externa e o serviço do LINE, consulte esta [página](../../delivery/using/line-channel.md#creating-a-line-account-and-an-external-account-).

Then, from the **[!UICONTROL Explorer]** , in **[!UICONTROL Platform]** > **[!UICONTROL External account]** , you need to configure different external accounts on both instances:

1. Create an **[!UICONTROL External database]** external account in your **execution** instance with the following configuration:

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Label]** e **[!UICONTROL Internal name]** : nomeie sua conta externa conforme necessário.
   * **[!UICONTROL Type]** : selecione **[!UICONTROL External database]** .
   * **[!UICONTROL Enabled]** deve estar marcada.
   Da **[!UICONTROL Connection]** categoria:

   * **[!UICONTROL Type]** : selecione seu servidor de banco de dados, por exemplo, PostgresSQL.
   * **[!UICONTROL Server]** : insira o URL do servidor de banco de dados.
   * **[!UICONTROL Account]** : informe sua conta de banco de dados.

      >[!NOTE]
      >
      >O usuário do banco de dados precisa ter direitos de leitura nas seguintes tabelas para conexão FDA: XtkOption, NmsVisitor, NmsVisitorSub, NmsService, NmsBroadLogRtEvent, NmsBroadLogBatchEvent, NmsTrackingLogRtEvent, NmsTrackingLogBatchEvent, NmsRtEvent, NmsBatchEvent, NmsBroadLog Msg, NmsTrackingUrl, NmsDelivery, NmsWebTrackingLogXtkFolder.

   * **[!UICONTROL Password]** : insira a senha da sua conta de banco de dados.
   * **[!UICONTROL Database]** : informe o nome do banco de dados da instância de execução.
   * **[!UICONTROL Target of an HTTP relay to remote database's account]** deve estar marcada.


1. Create an **[!UICONTROL External Database]** account in your **marketing** instance with the following configuration.

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Label]** e **[!UICONTROL Internal name]** : nomeie sua conta externa conforme necessário.
   * **[!UICONTROL Type]** : selecione **[!UICONTROL External database]** .
   * A caixa habilitada deverá estar marcada.
   Da **[!UICONTROL Connection]** categoria:

   * **[!UICONTROL Type]** : selecione **[!UICONTROL HTTP relay to remote Database]** .
   * **[!UICONTROL Server]** : insira o URL do servidor da campanha da instância de execução.
   * **[!UICONTROL Account]** : informe a conta usada para acessar a instância de execução.
   * **[!UICONTROL Password]** : digite a senha da conta usada para acessar a instância de execução.
   * **[!UICONTROL Data Source]** : digite a seguinte sintaxe **[!UICONTROL nms:extAccount:ID of your external database account in the execution instance]** .


1. Create an **[!UICONTROL Execution instance]** external account in your **marketing** instance using the following configuration to create the data synchronization workflow:

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Label]** e **[!UICONTROL Internal name]** : nomeie sua conta externa conforme necessário.
   * **[!UICONTROL Type]** : selecione **[!UICONTROL Execution instance]** .
   * A caixa habilitada deverá estar marcada.
   Da **[!UICONTROL Connection]** categoria:

   * **[!UICONTROL URL]** : insira o URL da instância de execução.
   * **[!UICONTROL Account]** : insira sua conta usada para acessar sua instância de execução.
   * **[!UICONTROL Password]** : digite a senha da conta usada para acessar a instância de execução.
   Da **[!UICONTROL Account connection method]** categoria:

   * **[!UICONTROL Method]** : selecione **[!UICONTROL Federated Data Access (FDA)]** .
   * **[!UICONTROL FDA account]** : selecione sua conta FDA no menu suspenso.
   * Clique no botão **[!UICONTROL Create the archiving workflow]**.
   * Click the **[!UICONTROL Create data synchronization workflow]** button to create the LINE data sync workflow.



1. Agora você poderá começar a criar mensagens transacionais. Para obter mais informações, consulte esta [página](../../message-center/using/introduction.md).
