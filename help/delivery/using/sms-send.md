---
product: campaign
title: Enviar, monitorar e rastrear SMS
description: Saiba como enviar, monitorar e rastrear SMS no Campaign
feature: SMS
role: User
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 99%

---

# Configuração adicional{#sms-properties}

<!--
## Send SMS messages {#sending-sms-messages}

To approve your message and send it to the recipients of the delivery being created, click **[!UICONTROL Send]**.

The detailed process when validating and sending a delivery is presented in the sections below:

* [Validate the delivery](steps-validating-the-delivery.md)
* [Send the delivery](steps-sending-the-delivery.md)
-->

## Parâmetros avançados {#advanced-parameters}

O botão **[!UICONTROL Properties]** dá acesso ao parâmetro de entrega avançado. Os parâmetros específicos para entregas de SMS estão na seção **[!UICONTROL SMS parameters]** da guia **[!UICONTROL Delivery]**.

As seguintes opções estão disponíveis:

* **Endereço do remetente**: permite personalizar o nome do remetente da entrega usando uma string de caracteres alfanuméricos limitada a onze caracteres. O campo não deve ser criado exclusivamente com figuras. Você pode definir uma condição para exibir, por exemplo, nomes diferentes de acordo com o código de área do destinatário:

  ```
  <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
  ```

  >[!IMPORTANT]
  >
  >Verifique a lei em seu país em relação à edição dos nomes dos remetentes. Você também deve verificar se sua operadora oferece essa funcionalidade.

* **Modo de transmissão**: transmissão de mensagem por SMS.
* **Prioridade**: nível de importância atribuída a uma mensagem. A prioridade **[!UICONTROL Normal]** é selecionada por padrão. Pergunte ao seu provedor de serviços sobre o custo do SMS enviado com prioridade **[!UICONTROL High]**.
* **Tipo de aplicativo**: escolha o aplicativo que deseja atribuir a sua entrega de SMS. A opção **[!UICONTROL Direct Marketing]** é selecionada por padrão e é a mais usada.

**Parâmetros específicos do conector NetSize**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Use vários SMS para uma única mensagem**: isso permite enviar uma mensagem com mais de 160 caracteres por meio de várias mensagens SMS.

**Parâmetros específicos de um conector SMPP**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Número máximo de SMS por mensagem**: essa opção permite que você defina o número de SMS para usar ao enviar uma mensagem. Se o número for definido como 0, você poderá usar um SMS para entregar sua mensagem. Se o número de SMS estiver definido como 1 ou 2, por exemplo, e a mensagem exceder esse limite, ele não será enviado.

<!--
## Monitor and track SMS {#monitoring-and-tracking-sms-deliveries}

After sending messages, you can monitor and track your deliveries. For more on this, refer to these sections:

* [Monitor a delivery](about-delivery-monitoring.md)
* [Understand delivery failures](understanding-delivery-failures.md)
* [About message tracking](about-message-tracking.md)
-->

## Processar mensagens de entrada {#processing-inbound-messages}

O módulo de **sms nlserver** consulta o roteador SMS em intervalos regulares. Isso permite que o Adobe Campaign rastreie o progresso das entregas e gerencie os relatórios de status e as solicitações de unsubscription de destinatários.

* **Relatórios de status**: exibe logs da entrega para verificar o status das mensagens.

  >[!NOTE]
  >
  >Cada SMS enviado é vinculado a uma conta externa em sua chave primária. Deste modo:
  >
  > * Os relatórios de status de uma conta externa de SMS excluída não são processados corretamente.
  > * Uma conta SMS só pode ser vinculada a uma única conta externa para garantir que os relatórios de status sejam atribuídos à conta correta

* **Unsubscription**: destinatários que desejam parar de receber entregas de SMS podem retornar uma mensagem contendo a palavra PARAR. Se o seu provedor permitir sob os termos do contrato, você poderá recuperar mensagens por meio da atividade de workflow de **SMS de entrada** e criar um query para habilitar a opção **Não entrar em contato com este destinatário** para os destinatários relacionados.

  Consulte a guia [Workflows](../../workflow/using/architecture.md) .

## Esquema InSMS {#insms-schema}

O schema InSMS contém informações relevantes para o SMS de entrada. Uma descrição desses campos está disponível por meio do atributo desc.

* **mensagem**: conteúdo do SMS recebido.
* **origem**: número do celular na origem da mensagem.
* **providerId**: identificador da mensagem retornada pelo SMSC (centro de mensagens).
* **criada**: a data da mensagem de entrada foi inserida no Adobe Campaign.
* **extAccount**: conta externa do Adobe Campaign.

  >[!IMPORTANT]
  >
  >Os campos a seguir são específicos para NetSize.
  >
  >Se o operador em uso não for NetSize, esses campos serão considerados vazios.

* **alias**: alias da mensagem de entrada.
* **separator**: separador entre o alias e o corpo da mensagem.
* **messageDate**: data da mensagem fornecida pelo operador.
* **receivalDate**: data da mensagem do operador recebida por SMSC (centro de mensagem).
* **deliveryDate**: mensagem de data enviada por SMSC (centro de mensagens).
* **largeAccount**: código de conta do cliente vinculado ao SMS de entrada.
* **countryCode**: código do país do operador.
* **operatorCode**: código de rede do operador.
* **linkedSmsId**: identificador do Adobe Campaign (broadlogId) vinculado ao SMS de saída, em que este SMS é a resposta.

## Gerenciar respostas automáticas (Regulamentação norte-americana) {#managing-automatic-replies--american-regulation-}

Quando os assinantes respondem a uma mensagem SMS enviada via Adobe Campaign e usam uma palavra-chave como PARAR, AJUDA ou SIM, é necessário, no mercado dos EUA, configurar mensagens que são automaticamente retornadas.

Por exemplo, se os destinatários enviam a palavra-chave PARAR, eles recebem automaticamente uma mensagem de confirmação informando que a assinatura foi cancelada.

O nome do remetente desse tipo de mensagem é um código curto geralmente usado para enviar entregas.

>[!IMPORTANT]
>
>O procedimento detalhado a seguir é válido apenas para conectores SMPP, exceto para o conector SMPP genérico estendido. Para obter mais informações, consulte a seção [Criar uma conta externa SMPP](sms-set-up.md#creating-an-smpp-external-account).
>
>Faz parte do processo de certificação realizado pelos operadores norte-americanos para campanhas de marketing nos EUA. Essas respostas às mensagens SMS de assinantes que contêm a palavra-chave devem ser enviadas de volta a eles imediatamente após receber uma mensagem deles.

1. Crie este tipo de arquivo XML:

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. Para o atributo **name** da tag **`<shortcode>`**, especifique o código curto que será exibido no lugar do nome do remetente da mensagem.

   Em cada tag **`<reply>`**, insira o atributo **keyword** com uma palavra-chave e o atributo **text** com a mensagem que gostaria de enviar para essa palavra-chave.

   >[!NOTE]
   >
   >Cada palavra-chave deve ser escrita em letras maiúsculas.

   Se desejar enviar a mesma mensagem para várias palavras-chave, duplique a linha correspondente.

   Por exemplo:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. Depois de concluído, salve este arquivo com o nome **smsAutoReply.xml**.

   Observe que o nome do arquivo diferencia maiúsculas de minúsculas no Linux.

1. Copie esse arquivo no diretório **conf** no Adobe Campaign, no mesmo lugar que o servidor Web.

>[!IMPORTANT]
>
>Esses tipos de mensagens automáticas não mantêm um histórico. Portanto, não aparecem no painel de entrega. [Saiba mais](delivery-dashboard.md).
>
>Essas mensagens não são consideradas nas regras de pressão comercial. [Saiba mais](../../campaign-opt/using/pressure-rules.md).
