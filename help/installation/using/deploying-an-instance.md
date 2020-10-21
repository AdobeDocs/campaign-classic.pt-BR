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
translation-type: tm+mt
source-git-commit: 3acf2359c74a3dc4b18c8976fee14dcbaf3fa510
workflow-type: tm+mt
source-wordcount: '3058'
ht-degree: 3%

---


# Implantação de uma instância{#deploying-an-instance}

>[!NOTE]
>
>As configurações do lado do servidor só podem ser executadas por Adobe para implantações hospedadas pelo Adobe. Para saber mais sobre as diferentes implantações, consulte a seção Modelos [de](../../installation/using/hosting-models.md) hospedagem ou [esta página](../../installation/using/capability-matrix.md).

## Assistente de implantação {#deployment-wizard}

Um assistente gráfico, disponível no console do cliente Adobe Campaign, permite que você defina os parâmetros da instância à qual você se conectará.

Para start do assistente de implantação, selecione **Ferramentas > Avançado > Assistente** de implantação.

![](assets/s_ncs_install_deployment_wiz_01.png)

As etapas de configuração são as seguintes:

1. [Parâmetros gerais](#general-parameters)
1. [Parâmetros de canal de email](#email-channel-parameters)
1. [Gerenciamento de emails salvos](#managing-bounced-emails)
1. [Configuração de rastreamento](#tracking-configuration)
1. [Parâmetros do canal móvel](#mobile-channel-parameters)
1. [Configurações regionais](#regional-settings)
1. [Acesso através da Internet](#access-from-the-internet)
1. [Gerenciamento de recursos públicos](#managing-public-resources)
1. [Expurgando dados](#purging-data)

## Parâmetros gerais {#general-parameters}

A primeira etapa do assistente de implantação permite que você insira informações gerais sobre a instância.

![](assets/s_ncs_install_deployment_wiz_02.png)

### Informações gerais {#general-information}

A seção inferior da janela permite selecionar as opções a serem ativadas.

* **[!UICONTROL Customer identifier used in billing]** : pode ser o nome da instância e o número da versão.
* **[!UICONTROL Common name of the customer]** : Insira uma string de caracteres com o nome da empresa. Essas informações podem ser usadas nos links de unsubscription.
* **[!UICONTROL Namespace]** : Insira um identificador curto em minúsculas. O objetivo é distinguir entre a configuração específica e a configuração de fábrica no caso de uma atualização. A namespace padrão é **cus** - para clientes.

### Opções técnicas {#technical-options}

A seção inferior da janela permite selecionar as opções a serem ativadas.

As seguintes opções estão disponíveis:

* **[!UICONTROL Email channel]** : para ativar o delivery de e-mail. Consulte Parâmetros [do canal de](#email-channel-parameters)email.
* **[!UICONTROL Tracking]** : Para ativar o rastreamento da população do público alvo (abre e clica). Refer to [Tracking configuration](#tracking-configuration).
* **[!UICONTROL Managing bounced emails]** : Para definir a conta POP usada para coletar e-mails de entrada. Consulte [Gerenciamento de e-mails](#managing-bounced-emails)enviados.
* **[!UICONTROL LDAP integration]** : Para configurar a autenticação do usuário por meio de um diretório LDAP. Consulte [Conexão por meio do LDAP](../../installation/using/connecting-through-ldap.md).

## Parâmetros de canal de email {#email-channel-parameters}

A etapa a seguir permite definir as informações a serem exibidas nos cabeçalhos de mensagem.

Esses parâmetros podem ser sobrecarregados em templates do delivery e individualmente para cada delivery (se os usuários tiverem os direitos necessários).

### Parâmetros para e-mails entregues {#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

Indique os seguintes parâmetros:

* **[!UICONTROL Sender name]** : Nome do remetente,
* **[!UICONTROL Sender address]** : O endereço do remetente,
* **[!UICONTROL Reply address text]** : O nome, que é personalizável, que será usado quando o recipient clicar no **[!UICONTROL Reply]** botão em seu software cliente de e-mail,
* **[!UICONTROL Reply address]** : O endereço de email a ser usado quando o recipient clicar no **[!UICONTROL Reply]** botão em seu software cliente de email,
* **[!UICONTROL Error address]** : Endereço de email das mensagens com erros. Este é o endereço técnico usado para lidar com emails de rejeição, incluindo emails recebidos pelo servidor Adobe Campaign devido a endereços de público alvo inexistentes.

Além disso, você pode especificar as **máscaras** autorizadas para o endereço do remetente e o endereço do erro. Se necessário, essas máscaras podem ser separadas por vírgulas. Essa configuração é opcional. Quando os campos são inseridos, a Adobe Campaign verifica no momento do delivery (durante a análise, se o endereço não incluir nenhuma variável) se os endereços são válidos. Esse modo operacional garante que não sejam usados endereços que possam acionar problemas de delivery. Os endereços dos delivery devem ser configurados no servidor do delivery.

### Caracteres autorizados em endereços {#characters-authorized-in-addresses}

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

No banco de dados Adobe Campaign, todos os endereços de email devem ser criados da seguinte forma: `x@y.z`. Os caracteres **x**, **y** e **z** não devem estar vazios e não devem incluir caracteres não autorizados.

É possível definir aqui os caracteres autorizados (&#39;política de dados&#39;) no campo de email do banco de dados. Os caracteres não incluídos na lista serão proibidos e, portanto, recusados ao inserir informações no banco de dados por meio da interface, por meio de um formulário da Web e também ao importar dados.

Duas listas estão disponíveis: **Apenas** europeus ou apenas **** EUA. Outros caracteres podem ser adicionados, se necessário.

### Parâmetros do delivery {#delivery-parameters}

Os parâmetros **avançados...** o link permite acessar opções de delivery, parâmetros vinculados a novas tentativas e quarentenas.

![](assets/s_ncs_install_deployment_wiz_05.png)

Essa janela permite que você defina, para todas as campanhas de e-mail, as opções de gerenciamento de qualidade de delivery e endereço.

As seguintes opções estão disponíveis:

* **[!UICONTROL Delivery duration of messages]** : Além desse tempo, o delivery é parado (por padrão, 5 dias),
* **[!UICONTROL Online resources validity duration]** : Tempo durante o qual são mantidas as informações do perfil do recipient para gerar mirrores page,
* **[!UICONTROL Exclude recipients who no longer wish to be contacted]** : Quando essa opção for selecionada, não será lista de bloqueios contato com recipient de ,
* **[!UICONTROL Automatically ignore doubles]** : Quando essa opção for selecionada, o delivery não será feito para endereços de duplicado.

### Repetir parâmetros {#retry-parameters}

As informações sobre recuperações são fornecidas nos períodos **de** recuperação e nos campos **Número de recuperações** : quando um recipient é inacessível, por exemplo, se sua caixa de entrada estiver cheia, por padrão o programa tentará contatá-los 5 vezes, com um intervalo de uma hora entre cada tentativa (durante o tempo máximo do delivery). Esses valores podem ser alterados de acordo com suas necessidades.

### Parâmetros de quarentena {#quarantine-parameters}

As opções de configuração para quarentena são as seguintes:

* **[!UICONTROL Duration between two significant errors]** : insira um valor (&quot;1d&quot; por padrão: 1 dia) para definir o tempo que o aplicativo aguarda antes de incrementar o contador de erros em caso de falha,
* **[!UICONTROL Maximum number of errors before quarantine]** : quando esse valor for atingido, o endereço de email será colocado em quarentena (por padrão, &quot;5&quot;: o endereço será colocado em quarentena no sexto erro). Isso significa que o contato será automaticamente excluído dos próximos deliveries.

## Gerenciamento de emails salvos {#managing-bounced-emails}

O e-mail de rejeição é extremamente importante para qualificar erros de delivery. Esses erros são classificados no diretório NP@I depois que as regras determinarem sua causa.

Esta etapa só estará disponível se as opções de gerenciamento de canal **de e-** mail e **Rejeição de e-mail** estiverem selecionadas na primeira etapa do assistente de implantação. Refer to [General parameters](#general-parameters).

Esta etapa permite definir configurações para gerenciar e-mails de rejeição.

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

As rejeições são feitas automaticamente pela Adobe Campaign, aplicando as regras listadas em **Administração > Gestão de campanha > Gerenciamento de não entregas > nó de qualificação** do log de Delivery. For more on this, refer to [Bounce mail management](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

Rejeições não processadas não são exibidas na interface do Adobe Campaign. Eles são excluídos automaticamente, a menos que sejam transferidos para uma caixa de correio de terceiros usando os seguintes campos:

* **[!UICONTROL Forwarding address]** : Preencha esse campo para transferir para um endereço de terceiros todas as mensagens de erro (processadas ou não processadas) coletadas pela plataforma Adobe Campaign.
* **[!UICONTROL Address for errors]** : Preencha este campo para transferir para um endereço de terceiros apenas as mensagens de erro que o processo do InMail não pôde qualificar.
* **[!UICONTROL SMTP server]** : Servidor usado para enviar emails de rejeição não processados.

>[!IMPORTANT]
>
>Para encaminhar emails de rejeição não processados, o Adobe recomenda preencher apenas o **[!UICONTROL Address for errors]** campo. No entanto, verifique se o endereço usado é verificado regularmente, pois isso pode colocar uma carga pesada em seu servidor de email. Entre em contato com o executivo da sua conta para obter mais informações.

## Configuração de rastreamento {#tracking-configuration}

A próxima etapa permite configurar o rastreamento para a instância. A instância deve ser declarada e registrada com os servidores de rastreamento.

Esta etapa só é oferecida quando as opções canal **de e-** mail e **Rastreamento** são selecionadas na primeira página do assistente de implantação. Refer to [General parameters](#general-parameters).

Para obter informações mais detalhadas sobre o rastreamento da Web (modo de rastreamento, criação e inserção de tags...), consulte [este documento](../../configuration/using/about-web-tracking.md).

### Princípio operacional {#operating-principle}

Quando você ativa o rastreamento em uma instância, os URLs nos delivery são alterados durante o envio para ativar o rastreamento.

* As informações sobre URLs externos (seguras ou não) inseridas nesta página do assistente de implantação são usadas para criar o novo URL. Além dessas informações, o link modificado contém: os identificadores do delivery, do recipient e do URL.

   As informações de rastreamento são coletadas pela Adobe Campaign nos servidores de rastreamento para enriquecer os perfis dos recipient e os dados vinculados ao delivery ( **[!UICONTROL Tracking]** guias).

   As informações sobre URLs internos só são usadas pelo servidor de aplicativos Adobe Campaign para entrar em contato com os servidores de rastreamento.

   For more on this, refer to [Tracking server](#tracking-server).

* Depois que os URLs forem configurados, será necessário ativar o rastreamento. Para fazer isso, a instância deve estar registrada nos servidores de rastreamento.

   For more on this, refer to [Saving tracking](#saving-tracking).

### Servidor de rastreamento {#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

Para garantir a eficiência do rastreamento nesta instância, as seguintes informações devem ser exibidas:
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL External URL]** e/ou **[!UICONTROL Secure external URL]** : Insira o URL de redirecionamento a ser usado no email a ser enviado.
* **[!UICONTROL Internal URL(s)]** : URLs usados apenas pelo servidor Adobe Campaign para entrar em contato com os servidores de rastreamento para coletar registros e fazer upload dos URLs. Não é necessário associá-lo à instância.

   Se você não especificar um URL, o URL de rastreamento será usado por padrão.

Com a arquitetura do Mid-sourcing, você pode externalizar o gerenciamento de rastreamento. Para fazer isso:

1. Selecione a opção **[!UICONTROL Externalize tracking management]** : isso permite que você use um servidor mid-sourcing como um servidor de rastreamento.
1. Preencha os campos **[!UICONTROL External account]** e **[!UICONTROL Instance name]** para se conectar ao servidor mid-sourcing.

   Para obter mais informações, consulte o servidor [Mid-sourcing](../../installation/using/mid-sourcing-server.md).

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

   Esta opção é usada quando você não tem a senha para a conta **interna** ; Nesse caso, uma conta de rastreamento é pré-configurada para você nos servidores de rastreamento. Digite a senha da conta de rastreamento do(s) servidor(es) de redirecionamento para validar a instância de rastreamento.

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   Especifique o nome da instância a ser validada.

Clique em **Aprovar** para start do processo de gravação com o servidor de rastreamento.

Na janela anterior, uma mensagem confirma o registro no nível do servidor de rastreamento:

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

Os parâmetros vinculados às pesquisas de URL não **devem ser modificados** para uma instalação padrão. Para todos os outros parâmetros, entre em contato com a Adobe.

## Parâmetros do canal móvel {#mobile-channel-parameters}

A próxima etapa permite definir as configurações padrão de delivery para dispositivos móveis (SMS e Push WAP).

>[!NOTE]
>
>O canal para portáteis é opcional: essa etapa só aparecerá se tiver sido adquirida. Verifique o contrato de licença.

![](assets/s_ncs_install_deployment_wiz_12.png)

### Conta padrão para delivery SMS {#default-account-for-sms-delivery}

Insira a seguinte informação:

* **[!UICONTROL Label]** : Insira um nome para esta conta SMS/Wap Push. Por exemplo, você pode desejar usar o nome do roteador.
* Para os campos **[!UICONTROL Server]**, **[!UICONTROL Port]**, **[!UICONTROL Account]**, **[!UICONTROL Password]**, **[!UICONTROL Connector]**, **[!UICONTROL Send Endpoint]**, **[!UICONTROL Reception Endpoint]**, **[!UICONTROL Notification Endpoint]** : Entre em contato com seu provedor de serviço para obter as configurações necessárias.

### Parâmetros do SMS enviado {#parameters-of-sms-sent}

Na lista suspensa **Prioridade** : Selecione &quot;Normal&quot;, &quot;Alto&quot; ou &quot;Urgente&quot; para aplicá-lo às mensagens a serem enviadas.

### Parâmetros avançados {#advanced-parameters}

Os parâmetros **avançados...** permite acessar as opções de nova tentativa e quarentena.

![](assets/s_ncs_install_deployment_wiz_13.png)

As informações sobre o tentativas estão disponíveis nos campos **Período de tentativas** e **Número de tentativas** : Quando um dispositivo móvel é inacessível, por padrão, o programa tentará novamente 5 vezes em intervalos de pelo menos 15 minutos (para o período máximo do delivery). Esses valores podem ser adaptados às suas necessidades.

As opções de configuração para quarentena são as seguintes:

* **[!UICONTROL Time between two significant errors]** : Digite um valor padrão (por padrão, &quot;1d&quot;: dia) para definir o tempo que o aplicativo aguarda antes de incrementar o contador de erros para uma falha.
* **[!UICONTROL Maximum number of errors before quarantine]** : Quando esse valor for atingido, o número de dispositivos móveis será colocado em quarentena (por padrão, &quot;5&quot;: o número será colocado em quarentena após o sexto erro). Isso significa que o contato será automaticamente excluído de delivery futuros.

## Configurações regionais {#regional-settings}

Essa etapa permite incluir preferências de política de dados.

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Consider all phone numbers as international ones]** : Quando essa opção é selecionada, o aplicativo aplica o formato internacional a números de telefone (o prefixo do país é então obrigatório, pois o número de dígitos não será verificado antes de aplicar a formatação). Se essa opção não estiver selecionada, você deve prefixar o número de telefone internacional com &quot;+&quot; ou &quot;00&quot;.
* **[!UICONTROL Store all phone numbers using the international format]** : Esta opção só diz respeito aos números de telefone **domésticos** que são importados ou editados. Defina se deseja usar um formato interno (como 425 555 0150) ou o formato internacional (por exemplo, +1 425 555 0150)

## Acesso através da Internet {#access-from-the-internet}

>[!IMPORTANT]
>
>Por motivos de privacidade, recomendamos usar HTTPS para todos os recursos externos.

Esta etapa permite definir URLs de acesso para páginas do Adobe Campaign expostas na Internet.

Você também deve indicar aqui as opções de publicação relacionadas aos Formulários web.

![](assets/s_ncs_install_deployment_wiz_15.png)

### Servidores expostos na Web {#servers-exposed-on-the-web}

Use esta página para preencher os URLs do servidor para:

1. Acesse o servidor de aplicativos exposto na Internet: Formulários de subscrição/unsubscription, extranet etc.
1. Acesse o servidor de aplicativos para obter recursos não expostos na Web: formulários, intranet, páginas de confirmação.
1. Acesse os mirrores page dos delivery.

   Um mirror page é uma página dinâmica que exibe o conteúdo do email. Ele é acessado por meio de um link inserido na mensagem enviada ao recipient e pode conter elementos personalizados. O mirror page oferece ao recipient a possibilidade de ler a mensagem em um navegador da Internet em vez do software de e-mail, independentemente do formato do delivery (texto ou HTML). No entanto, os mirrores page só são gerados para um determinado delivery se o conteúdo HTML necessário tiver sido definido.

A Adobe Campaign permite diferenciar esses três URLs para distribuir a carga por várias plataformas.

## Gerenciamento de recursos públicos {#managing-public-resources}

>[!IMPORTANT]
>
>Por motivos de privacidade, recomendamos usar HTTPS para todos os recursos externos.

Para serem vistas de fora, as imagens usadas em e-mails e recursos públicos vinculados a campanhas devem estar presentes em um servidor acessível externamente. Eles podem então estar disponíveis para recipient ou operadores externos.

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

Para esta etapa, é necessário inserir:

1. O novo URL do recurso público. Para obter mais informações, consulte a seção URL [dos](#public-resources-url) Recursos públicos.
1. O modo de detecção de imagem em um delivery. Para obter mais informações, consulte a seção Detecção [de imagem de](#delivery-image-detection) Delivery.
1. Opções de publicação. For more information, refer to the [Publication modes](#publication-modes) section.

Public resources are accessible via the **Administration > Resources > Online > Public resources** node of the Adobe Campaign tree. Eles são coletados em uma biblioteca e podem ser incluídos em e-mails, mas também usados em campanhas ou tarefas e na gestão de conteúdo.

![](assets/install_pub_resources_view.png)

### URL de recursos públicos {#public-resources-url}

O primeiro campo permite que você especifique o start do URL usado para os recursos após o upload. Quando carregados, os recursos são acessíveis por meio desse novo URL.

Em um delivery, você pode usar imagens armazenadas na biblioteca de recursos públicos ou qualquer outra imagem ou imagem local armazenada em um servidor.

* Para imagens de email, o URL **https://** server **/res/img** .

   Esse valor pode ser substituído para cada delivery.

* Para recursos públicos, o URL **https://** server **/res/** instance ****onde **instance**é o nome da instância de rastreamento.

### Detecção de imagem de delivery {#delivery-image-detection}

Em um delivery, você pode usar imagens armazenadas na biblioteca de recursos públicos ou qualquer outra imagem ou imagem local armazenada em um servidor.

As máscaras **de** URL do campo permitem especificar a lista de máscaras de URL a serem ignoradas ao carregar imagens automaticamente. Por exemplo, se você usar imagens que estão armazenadas em um site acessível do lado de fora, em particular em um site da Internet, poderá digitar o URL do site neste campo.

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

É possível especificar várias máscaras de URL usando uma vírgula para separá-las.

* Para obter informações sobre como usar e gerenciar imagens em emails, consulte [esta seção](../../delivery/using/defining-the-email-content.md#adding-images).
* No assistente do delivery, as imagens chamadas desses URLs terão o status &quot;Ignorado&quot;.

### Modos de publicação {#publication-modes}

A seção inferior do assistente permite que você selecione as opções de publicação de recursos públicos e imagens. Essas opções também estão disponíveis para Formulários web e pesquisas.

Os seguintes modos de publicação estão disponíveis:

* Servidor(es) de rastreamento

   Os recursos serão copiados automaticamente para os diferentes servidores de rastreamento. Eles estão configurados na configuração [de](#tracking-configuration)rastreamento de etapa.

* Outros servidores Adobe Campaign

   Você pode usar mais um servidor Adobe Campaign onde os recursos serão copiados.

   No lado do servidor, para usar um servidor Adobe Campaign dedicado, é necessário criar uma nova instância com o seguinte comando:

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

No evento de publicação em um servidor Adobe Campaign sem um script de publicação manual, por padrão, as imagens de um delivery são armazenadas no `$(XTK_INSTALL_DIR)/var/res/img/ directory`. O URL correspondente é o seguinte: **`https://server/res/img`**.

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`. O URL correspondente é o seguinte: **`https://server/res/instance`** em que instância é o nome da instância de rastreamento.

>[!NOTE]
>
>É possível alterar o diretório do armazenamento do recurso público. For more on this, refer to [Managing public resources](#managing-public-resources).

### Sincronização de recursos públicos {#synchronizing-public-resources}

Essa funcionalidade permite que você **sincronize recursos públicos** em vários servidores sobressalentes.

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

* sobressalente: O recurso público está sincronizado

* normal: Comportamento existente (sem sincronização)

* lista negra: O URL será adicionado à lista de bloqueios se retornar um erro 404. A duração (em segundos) do URL que está na lista de bloqueios é definida por um atributo de **tempo limite** cujo valor padrão é 60 s.

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

Os dados são excluídos automaticamente por meio do fluxo de trabalho de limpeza do Banco de Dados. Para obter mais informações sobre como configurar e operar esse fluxo de trabalho e detalhes sobre os itens excluídos, consulte este [documento](../../production/using/database-cleanup-workflow.md).
