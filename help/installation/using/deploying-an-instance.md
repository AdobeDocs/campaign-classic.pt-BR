---
title: Implantação de uma instância
seo-title: Implantação de uma instância
description: Implantação de uma instância
seo-description: null
page-status-flag: never-activated
uuid: 5694b07a-6c1c-45a3-8a22-fd9da163c28c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: 71fc8bfc-40e0-4592-a540-bd6807ded3a0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Implantação de uma instância{#deploying-an-instance}

>[!NOTE]
>
>As configurações do lado do servidor só podem ser executadas pela Adobe para implantações hospedadas pela Adobe. Para saber mais sobre as diferentes implantações, consulte a seção Modelos [de](../../installation/using/hosting-models.md) hospedagem ou [este artigo](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Assistente de implantação {#deployment-wizard}

Um assistente gráfico, disponível no console do cliente Adobe Campaign, permite que você defina os parâmetros da instância à qual você se conectará.

Para iniciar o assistente de implantação, selecione **Ferramentas > Avançado > Assistente** de implantação.

![](assets/s_ncs_install_deployment_wiz_01.png)

As etapas de configuração são as seguintes:

1. [Parâmetros gerais](#general-parameters)
1. [Parâmetros de canal de email](#email-channel-parameters)
1. [Gerenciamento de emails salvos](#managing-bounced-emails)
1. [Configuração de rastreamento](#tracking-configuration)
1. [Parâmetros do canal móvel](#mobile-channel-parameters)
1. [Configurações regionais](#regional-settings)
1. [Acesso através da Internet](#access-from-the-internet)
1. [Gestão dos recursos públicos](#managing-public-resources)
1. [Expurgando dados](#purging-data)

## Parâmetros gerais {#general-parameters}

A primeira etapa do assistente de implantação permite que você insira informações gerais sobre a instância.

![](assets/s_ncs_install_deployment_wiz_02.png)

### Informações gerais {#general-information}

A seção inferior da janela permite selecionar as opções a serem ativadas.

* **[!UICONTROL Customer identifier used in billing]** : pode ser o nome da instância e o número da versão.
* **[!UICONTROL Common name of the customer]** : Insira uma string de caracteres com o nome da sua empresa. Essas informações podem ser usadas nos links de cancelamento de assinatura.
* **[!UICONTROL Namespace]** : Insira um identificador curto em minúsculas. O objetivo é distinguir entre a configuração específica e a configuração de fábrica no caso de uma atualização. O namespace padrão é **cus** - para cliente.

### Opções técnicas {#technical-options}

A seção inferior da janela permite selecionar as opções a serem ativadas.

As seguintes opções estão disponíveis:

* **[!UICONTROL Email channel]** : para ativar a entrega de email. Consulte Parâmetros [de canal de](#email-channel-parameters)email.
* **[!UICONTROL Tracking]** : Para ativar o rastreamento da população de destino (abre e clica). Consulte Configuração [de](#tracking-configuration)rastreamento.
* **[!UICONTROL Managing bounced emails]** : Para definir a conta POP usada para coletar e-mails de entrada. Consulte [Gerenciamento de emails](#managing-bounced-emails)enviados.
* **[!UICONTROL LDAP integration]** : Para configurar a autenticação do usuário por meio de um diretório LDAP. Consulte [Conexão por meio do LDAP](../../installation/using/connecting-through-ldap.md).

## Parâmetros de canal de email {#email-channel-parameters}

A etapa a seguir permite definir as informações a serem exibidas nos cabeçalhos de mensagem.

Esses parâmetros podem ser sobrecarregados em modelos de entrega e individualmente para cada entrega (se os usuários tiverem os direitos necessários).

### Parâmetros para e-mails entregues {#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

Indique os seguintes parâmetros:

* **[!UICONTROL Sender name]** : Nome do remetente,
* **[!UICONTROL Sender address]** : O endereço do remetente,
* **[!UICONTROL Reply address text]** : O nome, que é personalizável, que será usado quando o destinatário clicar no **[!UICONTROL Reply]** botão em seu software cliente de e-mail,
* **[!UICONTROL Reply address]** : O endereço de email a ser usado quando o destinatário clicar no **[!UICONTROL Reply]** botão em seu software cliente de email,
* **[!UICONTROL Error address]** : Endereço de email das mensagens com erros. Esse é o endereço técnico usado para lidar com emails de rejeição, incluindo emails recebidos pelo servidor do Adobe Campaign devido a endereços de destino inexistentes.

Além disso, você pode especificar as **máscaras** autorizadas para o endereço do remetente e o endereço do erro. Se necessário, essas máscaras podem ser separadas por vírgulas. Essa configuração é opcional. Quando os campos são inseridos, o Adobe Campaign verifica no momento da entrega (durante a análise, se o endereço não incluir nenhuma variável) se os endereços são válidos. Esse modo operacional garante que não sejam usados endereços que possam causar problemas de entrega. Os endereços de entrega devem ser configurados no servidor de entrega.

### Caracteres autorizados em endereços {#characters-authorized-in-addresses}

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

No banco de dados do Adobe Campaign, todos os endereços de email devem ser criados da seguinte forma: `x@y.z`. Os caracteres **x**, **y** e **z** não devem estar vazios e não devem incluir caracteres não autorizados.

É possível definir aqui os caracteres autorizados (&#39;política de dados&#39;) no campo de email do banco de dados. Os caracteres não incluídos na lista serão proibidos e, portanto, recusados ao inserir informações no banco de dados por meio da interface, por meio de um formulário da Web e também ao importar dados.

Duas listas estão disponíveis: Apenas **** europeus ou apenas **** americanos. Outros caracteres podem ser adicionados, se necessário.

### Parâmetros de entrega {#delivery-parameters}

**Os parâmetros** avançados... o link permite acessar opções de entrega, parâmetros vinculados a tentativas e quarentena.

![](assets/s_ncs_install_deployment_wiz_05.png)

Essa janela permite definir, para todas as campanhas por email, as opções de gerenciamento de qualidade de endereço e entrega.

As seguintes opções estão disponíveis:

* **[!UICONTROL Delivery duration of messages]** : Além desse tempo, a entrega é interrompida (por padrão, 5 dias),
* **[!UICONTROL Online resources validity duration]** : Tempo durante o qual as informações do perfil do destinatário são mantidas para gerar páginas espelhadas,
* **[!UICONTROL Exclude recipients who no longer wish to be contacted]** : Quando esta opção for selecionada, os destinatários da lista negra não serão contatados,
* **[!UICONTROL Automatically ignore doubles]** : Quando essa opção for selecionada, a entrega não será feita para duplicar endereços.

### Repetir parâmetros {#retry-parameters}

As informações sobre recuperações são fornecidas nos períodos **de** recuperação e nos campos **Número de recuperações** : quando um destinatário estiver inacessível, por exemplo, se sua caixa de entrada estiver cheia, por padrão o programa tentará contatá-lo 5 vezes, com um intervalo de uma hora entre cada tentativa (durante o tempo máximo de entrega). Esses valores podem ser alterados de acordo com suas necessidades.

### Parâmetros de quarentena {#quarantine-parameters}

As opções de configuração para quarentena são as seguintes:

* **[!UICONTROL Duration between two significant errors]** : digite um valor (&quot;1d&quot; por padrão: 1 dia) para definir o tempo que o aplicativo aguarda antes de incrementar o contador de erros em caso de falha,
* **[!UICONTROL Maximum number of errors before quarantine]** : quando esse valor for atingido, o endereço de email será colocado em quarentena (por padrão, &quot;5&quot;: o endereço será colocado em quarentena no sexto erro). Isso significa que o contato será automaticamente excluído das entregas subsequentes.

## Gerenciamento de emails salvos {#managing-bounced-emails}

O e-mail de rejeição é extremamente importante para qualificar os erros de entrega. Esses erros são classificados no diretório NP@I depois que as regras determinarem sua causa.

Esta etapa só estará disponível se as opções de gerenciamento de canal **de e-** mail e **Rejeitar e-mail** estiverem selecionadas na primeira etapa do assistente de implantação. Consulte Parâmetros [gerais](#general-parameters).

Esta etapa permite definir configurações para gerenciar emails de rejeição.

![](assets/s_ncs_install_deployment_wiz_06.png)

### Conta POP usada para recuperar emails recebidos {#pop-account-used-to-retrieve-incoming-mails}

Indique os parâmetros a serem conectados à conta para recuperar emails recebidos.

* **[!UICONTROL Label]** : Nome que inclui todos os parâmetros abaixo indicados,
* **[!UICONTROL Server]** : Servidor utilizado para recuperar correio de rejeição (correio de entrada),
* **[!UICONTROL Security]** : Se necessário, selecione **[!UICONTROL SSL]** na lista suspensa,
* **[!UICONTROL Port]** : porta do servidor (geralmente 110),
* **[!UICONTROL Account]** : Nome da conta usada para o correio de rejeição,
* **[!UICONTROL Password]** : Senha associada à conta.

Depois que as configurações de POP forem especificadas, clique em **Testar** para verificar se estão corretas.

### Mensagens de rejeição não processadas {#unprocessed-bounce-mails}

As rejeições são feitas automaticamente pelo Adobe Campaign, aplicando as regras listadas em **Administração > Gerenciamento de campanha > Gerenciamento de não entregas > Nó de qualificação** do log de entrega. Para obter mais informações, consulte Gerenciamento [de e-mail de](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management)rejeição.

Rejeições não processadas não são exibidas na interface do Adobe Campaign. Eles são excluídos automaticamente, a menos que sejam transferidos para uma caixa de correio de terceiros usando os seguintes campos:

* **[!UICONTROL Forwarding address]** : Preencha esse campo para transferir para um endereço de terceiros todas as mensagens de erro (processadas ou não processadas) coletadas pela plataforma do Adobe Campaign.
* **[!UICONTROL Address for errors]** : Preencha este campo para transferir para um endereço de terceiros apenas as mensagens de erro que o processo do InMail não pôde qualificar.
* **[!UICONTROL SMTP server]** : Servidor usado para enviar emails de rejeição não processados.

>[!CAUTION]
>
>Para encaminhar emails de rejeição não processados, a Adobe recomenda preencher apenas o **[!UICONTROL Address for errors]** campo. No entanto, verifique se o endereço usado é verificado regularmente, pois isso pode colocar uma carga pesada em seu servidor de email. Entre em contato com o executivo da sua conta para obter mais informações.

## Configuração de rastreamento {#tracking-configuration}

A próxima etapa permite configurar o rastreamento para a instância. A instância deve ser declarada e registrada com os servidores de rastreamento.

Esta etapa só é oferecida quando as opções Canal **de** email e **Rastreamento** são selecionadas na primeira página do assistente de implantação. Consulte Parâmetros [gerais](#general-parameters).

Para obter informações mais detalhadas sobre o rastreamento da Web (modo de rastreamento, criação e inserção de tags...), consulte [este documento](../../configuration/using/about-web-tracking.md).

### Princípio operacional {#operating-principle}

Quando você ativa o rastreamento em uma instância, os URLs nas entregas são alterados durante o envio para ativar o rastreamento.

* As informações sobre URLs externos (seguras ou não) inseridas nesta página do assistente de implantação são usadas para criar o novo URL. Além dessas informações, o link modificado contém: os identificadores da entrega, o destinatário e o URL.

   As informações de rastreamento são coletadas pelo Adobe Campaign nos servidores de rastreamento para aprimorar os perfis de destinatários e os dados vinculados à entrega ( **[!UICONTROL Tracking]** guias).

   As informações sobre URLs internos só são usadas pelo servidor de aplicativos do Adobe Campaign para entrar em contato com os servidores de rastreamento.

   For more on this, refer to [Tracking server](#tracking-server).

* Depois que os URLs forem configurados, será necessário ativar o rastreamento. Para fazer isso, a instância deve estar registrada nos servidores de rastreamento.

   For more on this, refer to [Saving tracking](#saving-tracking).

### Servidor de rastreamento {#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

Para garantir a eficiência do rastreamento nesta instância, as seguintes informações devem ser exibidas:
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL External URL]** e/ou **[!UICONTROL Secure external URL]** : Insira o URL de redirecionamento a ser usado no email a ser enviado.
* **[!UICONTROL Internal URL(s)]** : URLs usados apenas pelo servidor do Adobe Campaign para entrar em contato com os servidores de rastreamento para coletar registros e carregar os URLs. Não é necessário associá-lo à instância.

   Se você não especificar um URL, o URL de rastreamento será usado por padrão.

Com a arquitetura de terceirização, você pode externalizar o gerenciamento de rastreamento. Para fazer isso:

1. Selecione a opção **[!UICONTROL Externalize tracking management]** : isso permite usar um servidor de mid-sourcing como um servidor de rastreamento.
1. Preencha os campos **[!UICONTROL External account]** e **[!UICONTROL Instance name]** para poder se conectar ao servidor de mid-sourcing.

   Para obter mais informações, consulte o servidor [de](../../installation/using/mid-sourcing-server.md)terceirização.

1. Clique no **[!UICONTROL Enable the tracking instance]** botão para aprovar a conexão com o servidor.

   ![](assets/s_ncs_install_deployment_wiz_18.png)

### Salvando rastreamento {#saving-tracking}

Depois que os URLs forem preenchidos, você deverá registrar o servidor de rastreamento.

Clique no link **Registro no(s) servidor(es)** de rastreamento e selecione uma das opções disponíveis.

![](assets/s_ncs_install_deployment_wiz_09.png)

Existem três tipos possíveis de arquitetura para implementar o rastreamento:

1. **Adicionar suporte para rastreamento em uma instância existente**

   Essa opção se aplica se a instância já tiver sido criada para outras necessidades (servidor MTA etc.) em servidores que serão usados como servidores de rastreamento.

   ![](assets/s_ncs_install_deployment_wiz_11.png)

   Digite a senha da conta **interna** nos servidores de redirecionamento para configurar a instância de rastreamento.

   >[!NOTE]
   >
   >Se vários servidores de rastreamento forem usados, todos devem usar o mesmo nome e senha.

   Especifique o nome da instância e a senha.

1. **Criar uma nova instância dedicada ao rastreamento**

   Essa opção é útil quando instâncias de rastreamento são reservadas para rastreamento e não têm outros módulos de aplicativo.

   ![](assets/s_ncs_install_deployment_wiz_10.png)

   Digite a senha da conta **interna** nos servidores de redirecionamento para configurar a instância de rastreamento.

   >[!NOTE]
   >
   >Se vários servidores de rastreamento estiverem configurados, todos devem usar a mesma senha.

   Especifique o nome da instância, a senha e quaisquer máscaras de DNS associadas, como **[!UICONTROL Campaign*]**.

1. **Validar uma instância de rastreamento já pré-configurada para você**

   Esta opção é usada quando você não tem a senha para a conta **interna** ; Nesse caso, uma conta de rastreamento é pré-configurada para você nos servidores de rastreamento. Digite a senha da conta de rastreamento dos servidores de redirecionamento para validar a instância de rastreamento.

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   Especifique o nome da instância a ser validada.

Clique em **Aprovar** para iniciar o processo de gravação com o servidor de rastreamento.

Na janela anterior, uma mensagem confirma o registro no nível do servidor de rastreamento:

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

Os parâmetros vinculados às pesquisas de URL não **devem ser modificados** para uma instalação padrão. Para todos os outros parâmetros, entre em contato com a Adobe.

## Parâmetros do canal móvel {#mobile-channel-parameters}

A próxima etapa permite que você defina as configurações padrão para entregas em dispositivos móveis (SMS e Push WAP).

>[!NOTE]
>
>O canal móvel é opcional: essa etapa só aparecerá se tiver sido adquirida. Verifique o contrato de licença.

![](assets/s_ncs_install_deployment_wiz_12.png)

### Conta padrão para entrega de SMS {#default-account-for-sms-delivery}

Insira a seguinte informação:

* **[!UICONTROL Label]** : Insira um nome para esta conta SMS/Wap Push. Por exemplo, você pode desejar usar o nome do roteador.
* Para os campos **[!UICONTROL Server]**, **[!UICONTROL Port]**, **[!UICONTROL Account]**, **[!UICONTROL Password]**, **[!UICONTROL Connector]**, **[!UICONTROL Send Endpoint]**, **[!UICONTROL Reception Endpoint]**, **[!UICONTROL Notification Endpoint]** : Entre em contato com seu provedor de serviços para obter as configurações necessárias.

### Parâmetros do SMS enviado {#parameters-of-sms-sent}

Na lista suspensa **Prioridade** : Selecione &quot;Normal&quot;, &quot;Alto&quot; ou &quot;Urgente&quot; para aplicá-lo às mensagens a serem enviadas.

### Parâmetros avançados {#advanced-parameters}

**Os parâmetros** avançados... permite acessar as opções de repetição e quarentena.

![](assets/s_ncs_install_deployment_wiz_13.png)

As informações sobre tentativas estão disponíveis nos campos **Período de tentativas** e **Número de tentativas** : Por padrão, quando um dispositivo móvel está inacessível, o programa tentará novamente 5 vezes em intervalos de pelo menos 15 minutos (para o período máximo de entrega). Esses valores podem ser adaptados às suas necessidades.

As opções de configuração para quarentena são as seguintes:

* **[!UICONTROL Time between two significant errors]** : Digite um valor padrão (por padrão, &quot;1d&quot;: dia) para definir o tempo que o aplicativo aguarda antes de incrementar o contador de erros para uma falha.
* **[!UICONTROL Maximum number of errors before quarantine]** : Quando esse valor for atingido, o número de dispositivos móveis será colocado em quarentena (por padrão, &quot;5&quot;: o número será colocado em quarentena após o sexto erro). Isso significa que o contato será automaticamente excluído das entregas futuras.

## Configurações regionais {#regional-settings}

Essa etapa permite incluir preferências de política de dados.

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Consider all phone numbers as international ones]** : Quando essa opção é selecionada, o aplicativo aplica o formato internacional a números de telefone (o prefixo do país é então obrigatório, pois o número de dígitos não será verificado antes de aplicar a formatação). Se essa opção não estiver selecionada, você deve prefixar o número de telefone internacional com &quot;+&quot; ou &quot;00&quot;.
* **[!UICONTROL Store all phone numbers using the international format]** : Esta opção só diz respeito aos números de telefone **domésticos** que são importados ou editados. Defina se deseja usar um formato interno (como 425 555 0150) ou internacional (por exemplo, +1 425 555 0150)

## Acesso através da Internet {#access-from-the-internet}

>[!CAUTION]
>
>Por motivos de privacidade, recomendamos usar HTTPS para todos os recursos externos.

Essa etapa permite definir URLs de acesso para páginas do Adobe Campaign expostas na Internet.

Você também deve indicar aqui as opções de publicação vinculadas a formulários da Web.

![](assets/s_ncs_install_deployment_wiz_15.png)

### Servidores expostos na Web {#servers-exposed-on-the-web}

Use esta página para preencher os URLs do servidor para:

1. Acesse o servidor de aplicativos exposto na Internet: formulários de assinatura/cancelamento de assinatura, extranet etc.
1. Acesse o servidor de aplicativos para obter recursos não expostos na Web: formulários, intranet, páginas de confirmação.
1. Acesse as páginas espelhadas das entregas.

   Uma página espelhada é uma página dinâmica que exibe o conteúdo do email. É acessado por meio de um link inserido na mensagem enviada ao destinatário e pode conter elementos personalizados. A página espelhada oferece ao destinatário a possibilidade de ler a mensagem em um navegador da Internet em vez do software de email, independentemente do formato de entrega (texto ou HTML). No entanto, as páginas espelhadas são geradas somente para uma determinada entrega se o conteúdo HTML necessário tiver sido definido.

O Adobe Campaign permite diferenciar esses três URLs para espalhar a carga por várias plataformas.

## Gestão dos recursos públicos {#managing-public-resources}

>[!CAUTION]
>
>Por motivos de privacidade, recomendamos usar HTTPS para todos os recursos externos.

Para serem vistas de fora, as imagens usadas em emails e recursos públicos vinculados a campanhas devem estar presentes em um servidor acessível externamente. Eles podem então estar disponíveis para destinatários ou operadores externos.

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

Para esta etapa, é necessário inserir:

1. O novo URL de recurso público. Para obter mais informações, consulte a seção URL [de recursos](#public-resources-url) públicos.
1. O modo de detecção de imagem em uma entrega. Para obter mais informações, consulte a seção Detecção [de imagem de](#delivery-image-detection) entrega.
1. Opções de publicação. For more information, refer to the [Publication modes](#publication-modes) section.

Os recursos públicos são acessíveis por meio do nó **Administração > Recursos > Online > Recursos** públicos da árvore do Adobe Campaign. Eles são coletados em uma biblioteca e podem ser incluídos em e-mails, mas também usados em campanhas ou tarefas e no gerenciamento de conteúdo.

![](assets/install_pub_resources_view.png)

### URL de recursos públicos {#public-resources-url}

O primeiro campo permite que você especifique o início do URL usado para os recursos após o upload. Quando carregados, os recursos são acessíveis por meio desse novo URL.

Em uma entrega, você pode usar imagens armazenadas na biblioteca de recursos pública ou qualquer outra imagem ou imagem local armazenada em um servidor.

* Para imagens de email, o URL **https://** server **/res/img** .

   Esse valor pode ser substituído para cada entrega.

* Para recursos públicos, o URL **https://** server **/res/** instance ****onde **instance**é o nome da instância de rastreamento.

### Detecção de imagens de entrega {#delivery-image-detection}

Em uma entrega, você pode usar imagens armazenadas na biblioteca de recursos pública ou qualquer outra imagem ou imagem local armazenada em um servidor.

As máscaras **de** URL do campo permitem especificar a lista de máscaras de URL a serem ignoradas ao carregar imagens automaticamente. Por exemplo, se você usar imagens que estão armazenadas em um site acessível do lado de fora, em particular em um site da Internet, poderá digitar o URL do site neste campo.

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

É possível especificar várias máscaras de URL usando uma vírgula para separá-las.

* Para obter informações sobre como usar e gerenciar imagens em emails, consulte [esta seção](../../delivery/using/defining-the-email-content.md#adding-images).
* No assistente de entrega, as imagens chamadas desses URLs terão o status &quot;Ignorado&quot;.

### Modos de publicação {#publication-modes}

A seção inferior do assistente permite selecionar as opções de publicação de recursos públicos e imagens. Essas opções também estão disponíveis para formulários da Web e pesquisas.

Os seguintes modos de publicação estão disponíveis:

* Servidor(es) de rastreamento

   Os recursos serão copiados automaticamente para os diferentes servidores de rastreamento. Eles estão configurados na configuração [de](#tracking-configuration)rastreamento de etapa.

* Outros servidores do Adobe Campaign

   Você pode usar mais um servidor do Adobe Campaign onde os recursos serão copiados.

   No lado do servidor, para usar um servidor dedicado do Adobe Campaign, é necessário criar uma nova instância com o seguinte comando:

   ```
   nlserver config -addtrackinginstance:<trackingA>/<trackingA*>
   ```

   Em seguida, insira a senha.

   Os parâmetros do(s) servidor(es) dedicado(s) são fornecidos nos campos **[!UICONTROL Media URL(s)]**, **[!UICONTROL Password]** e **[!UICONTROL Instance name]** .

   ![](assets/s_ncs_install_images_upload_b.png)

* Script de publicação manual (somente para recursos públicos)

   ![](assets/s_ncs_install_images_upload_c.png)

   É possível publicar as imagens usando um script:

   * Você deve criar este script: Seu conteúdo depende da sua configuração.
   * O script será chamado pelo seguinte comando:

      ```
      [INSTALL]/copyToFrontal.vbs "$(XTK_INSTALL_DIR)\var\<instance>\upload\" "img1,img2,img3"
      ```

      onde `[INSTALL]` é o caminho de acesso para a pasta de instalação do Adobe Campaign.

   * No Unix, verifique se o script é executável.

Para imagens, ele deve copiá-las da pasta &quot;images&quot; especificada pela opção **NmsDelivery_ImageSubDirectory** para um ou mais servidores frontais. Esses servidores armazenarão as imagens para torná-las acessíveis por meio do novo URL configurado.

No caso de publicação em um servidor do Adobe Campaign sem um script de publicação manual, por padrão, as imagens de uma entrega são armazenadas no `$(XTK_INSTALL_DIR)/var/res/img/ directory`. O URL correspondente é o seguinte: **`https://server/res/img`**.

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`. O URL correspondente é o seguinte: **`https://server/res/instance`** onde instância é o nome da instância de rastreamento.

>[!NOTE]
>
>É possível alterar o diretório de armazenamento de recursos públicos. Para obter mais informações, consulte [Gerenciamento de recursos](#managing-public-resources)públicos.

### Sincronizar recursos públicos {#synchronizing-public-resources}

Essa funcionalidade permite **sincronizar recursos** públicos em vários servidores sobressalentes.

Se um recurso público não estiver presente no servidor de rastreamento ou se o recurso retornar um erro 404, o servidor de rastreamento tentará localizar o recurso em um dos servidores sobressalentes.

A declaração e configuração de servidores sobressalentes devem ser feitas no arquivo **serverConf.xml** do servidor de marketing. Todos os parâmetros disponíveis no **serverConf.xml** estão listados nesta [seção](../../installation/using/the-server-configuration-file.md).

**Declaração**

```
<redirection>
<spareServer enabledIf="" id="" url=""/>
</redirection>
```

**Configuração**

Para cada recurso público que precisa ser sincronizado, é necessário adicionar um atributo de status ao `<url>` elemento na `<relay>` parte:

O atributo status pode ser um dos três valores:

* reserva: O recurso público está sincronizado

* normal: Comportamento existente (sem sincronização)

* lista negra: O URL será bloqueado se retornar um erro 404. A duração (em segundos) da lista negra é definida por um atributo de **tempo limite** cujo valor padrão é 60s.

A configuração predefinida da sincronização é:

```
(extracted from the serverConf.xml file)

<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="false" trackingPassword="">
<spareServer enabledIf="" id="1" url=""/>
</redirection>

....


<relay debugRelay="false" forbiddenCharsInAuthority="?#.@/:" forbiddenCharsInPath="?#/"
           modDir="index.html" startRelay="false" startRelayInModule="true" timeout="60">
   <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/view/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jsp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jssp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/webApp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/report/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/jssp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/strings/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/interaction/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/barcode/*"/>

      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/favicon.*"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.html"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.png"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.jpg"/>

 </relay>
```

## Expurgando dados {#purging-data}

A última etapa do assistente de implantação permite configurar a remoção automática de dados obsoletos. Os valores são expressos em dias.

![](assets/s_ncs_install_deployment_wiz_16.png)

Os dados são excluídos automaticamente pelo fluxo de trabalho de limpeza do Banco de Dados. Para obter mais informações sobre como configurar e operar esse fluxo de trabalho e detalhes sobre os itens excluídos, consulte este [documento](../../production/using/database-cleanup-workflow.md).
