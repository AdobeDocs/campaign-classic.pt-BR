---
product: campaign
title: Publicar um formulário web
description: Publicar um formulário web
badge-v8: label="Também se aplica à versão v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Web Forms
exl-id: 1c66b8e8-7590-4767-9b2f-a9a509df4508
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 99%

---

# Publicar um formulário web{#publishing-a-web-form}



## Pré-carregamento dos dados do formulário {#pre-loading-the-form-data}

Se quiser atualizar os perfis armazenados no banco de dados por meio de um formulário web, use uma caixa de pré-carregamento. A caixa de pré-carregamento permite indicar como localizar o registro a ser atualizado no banco de dados.

Os seguintes métodos de identificação são possíveis:

* **[!UICONTROL Adobe Campaign Encryption]**

  Esse método de criptografia usa o identificador (ID) criptografado do Adobe Campaign. Esse método só é aplicável em um objeto do Adobe Campaign e a ID criptografada só pode ser gerada pela plataforma Adobe Campaign.

  Ao usar esse método, você precisa adaptar a URL do formulário a ser entregue ao endereço de email adicionando o parâmetro **`<%=escapeUrl(recipient.cryptedId) %>`**. Para obter mais informações, consulte [Entrega de um formulário por email](#delivering-a-form-via-email).

* **[!UICONTROL DES encryption]**

  ![](assets/s_ncs_admin_survey_preload_methods_001.png)

  Esse método de criptografia usa um identificador (ID) fornecido externamente, vinculado a uma chave compartilhada pela Adobe Campaign e pelo provedor externo. O campo **[!UICONTROL Des key]** permite inserir essa chave de criptografia.

* **[!UICONTROL List of fields]**

  Essa opção permite escolher entre os campos no contexto atual do formulário, aquelas que serão usadas para localizar o perfil correspondente no banco de dados.

  ![](assets/s_ncs_admin_survey_preload_methods_002.png)

  Os campos podem ser adicionados às propriedades do formulário por meio da guia **[!UICONTROL Parameters]** (consulte [Adicionar parâmetros](defining-web-forms-properties.md#adding-parameters)). Eles são colocados na URL do formulário ou nas zonas de entrada.

  >[!CAUTION]
  >
  >Os dados nos campos selecionados não estão criptografados. Eles não devem ser fornecidos em um formulário criptografado porque o Adobe Campaign não poderá retirar a criptografia se a opção **[!UICONTROL Field list]** estiver selecionada.

  No exemplo a seguir, o pré-carregamento de perfis é baseado no endereço de email.

  A URL pode incluir o endereço de email não criptografado, nesse caso, os usuários têm acesso direto às páginas referentes.

  ![](assets/s_ncs_admin_survey_preload_methods_003.png)

  Caso contrário, eles serão solicitados a fornecer sua senha.

  ![](assets/s_ncs_admin_survey_preload_methods_004.png)

  >[!CAUTION]
  >
  >Se vários campos forem especificados na lista, os dados de **TODOS OS CAMPOS** deverão corresponder aos dados armazenados no banco de dados para que o perfil seja atualizado. Caso contrário, um novo perfil será criado.
  > 
  >Essa função é particularmente útil para aplicações web, mas não recomendada para formulários públicos. A opção de controle de acesso selecionado deve ser &quot;Habilitar controle de acesso&quot;.

A opção **[!UICONTROL Skip preloading if no ID]** deve ser selecionada se você não deseja atualizar os perfis. Nesse caso, cada perfil inserido será adicionado ao banco de dados após a aprovação do formulário. Essa opção é usada, por exemplo, quando o formulário é postado em um site.

A opção **[!UICONTROL Auto-load data referenced in the form]** permite pré-carregar automaticamente os dados que correspondem aos campos de entrada e mesclagem no formulário. Porém, os dados referenciados nas atividades **[!UICONTROL Script]** e **[!UICONTROL Test]** não estão relacionados. Se esta opção não estiver selecionada, você precisará definir os campos utilizando a opção **[!UICONTROL Load additional data]**.

A opção **[!UICONTROL Load additional data]** permite adicionar informações que não são usadas nas páginas do formulário, mas ainda serão pré-carregadas.

É possível, por exemplo, pré-carregar o gênero do destinatário e direcionar automaticamente para a página adequada através de uma caixa de teste.

![](assets/s_ncs_admin_survey_preload_ex.png)

## Gerenciamento de entrega e de rastreamento de formulários Web {#managing-web-forms-delivery-and-tracking}

Depois que o formulário tiver sido criado, configurado e publicado, você poderá entregar e rastrear as respostas do usuário.

### Ciclo de vida de um formulário {#life-cycle-of-a-form}

Há três estágios no ciclo de vida de um formulário:

1. **Em edição**

   Esta é a fase de design inicial. Quando um novo formulário é criado, ele está na fase de edição. Acesse o formulário, somente para fins de teste, e exija que o parâmetro **[!UICONTROL __uuid]** seja usado no URL. Essa URL pode ser acessada na subguia **[!UICONTROL Preview]**. Consulte [Parâmetros da URL do formulário](defining-web-forms-properties.md#form-url-parameters).

   >[!CAUTION]
   >
   >Desde que o formulário esteja sendo editado, sua URL de acesso é uma URL especial.

1. **Publicação pendente**

   Em alguns casos (como ao [importar um formulário por meio de um pacote](#import-web-packages)), um formulário web pode ter o status **[!UICONTROL Pending publication]** até ser publicado.

   >[!NOTE]
   >
   >Para aplicações web técnicas (disponíveis no menu **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Web applications]**), um formulário com o status **[!UICONTROL Pending publication]** é automaticamente [publicado](#publishing-a-form) e recebe o status **[!UICONTROL Online]**.

1. **Online**

   Quando a fase de design é concluída, o formulário pode ser entregue.

   Quando um formulário tem o status **[!UICONTROL Being edited]** ou **[!UICONTROL Pending publication]**, ele deve ser [publicado](#publishing-a-form) para ficar online e acessível por meio do URL do formulário web em um navegador.

   Após a publicação, o formulário ficará acessível até expirar.

   O formulário ficará **[!UICONTROL Live]** até expirar.

   >[!CAUTION]
   >
   >Para ser entregue, o URL do formulário não pode ter o parâmetro **[!UICONTROL __uuid]**.

1. **Fechado**

   Depois que o formulário for fechado, a fase de entrega será finalizada e o formulário ficará indisponível: ele não estará mais acessível aos usuários.

   A data de expiração pode ser definida na janela de propriedades do formulário. Para obter mais informações, consulte [Disponibilizar um formulário online](#making-a-form-available-online).

O status da publicação de um formulário é exibido na lista de formulários.

![](assets/s_ncs_admin_survey_status.png)

### Publicação de um formulário {#publishing-a-form}

Para alterar o estado de um formulário, você precisa publicá-lo. Para fazer isso, clique no botão **[!UICONTROL Publication]** acima da lista de formulários web e selecione o estado na caixa suspensa.

![](assets/webapp_publish_webform.png)

### Disponibilização de um formulário online {#making-a-form-available-online}

Para ser acessado por usuários, o formulário deve estar em produção e ter sido iniciado, ou seja, estar em seu período de vigência. As datas de validade são inseridas por meio do link **[!UICONTROL Properties]** do formulário.

* Use os campos na seção **[!UICONTROL Project]** para inserir datas de início e término do formulário.

  ![](assets/webapp_availability_date.png)

* Clique no link **[!UICONTROL Personalize the message displayed if the form is closed...]** para definir a mensagem de erro que será exibida se o usuário tentar acessar o formulário enquanto ele não for válido.

  Consulte [Acessibilidade do formulário](defining-web-forms-properties.md#accessibility-of-the-form).

### Entrega de um formulário por email {#delivering-a-form-via-email}

Ao entregar um convite por email, você pode usar a opção **[!UICONTROL Adobe Campaign Encryption]** para reconciliação de dados. Para fazer isso, vá para o assistente da entrega e adapte o link ao formulário adicionando o seguinte parâmetro:

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

Nesse caso, a chave de reconciliação para o armazenamento de dados deve ser o identificador criptografado do destinatário. Para obter mais informações, consulte [Pré-carregamento dos dados do formulário](#pre-loading-the-form-data).

Nesse caso, você precisa verificar a opção **[!UICONTROL Update the preloaded record]** na caixa de registro. Para obter mais informações, consulte [Salvar respostas de formulários Web](web-forms-answers.md#saving-web-forms-answers).

![](assets/s_ncs_admin_survey_save_box_option.png)

### Registrar respostas {#log-responses}

O rastreamento de resposta pode ser ativado em uma guia dedicada para monitorar o impacto do formulário Web. Para fazer isso, clique no link **[!UICONTROL Advanced parameters...]** na janela de propriedades do formulário e selecione a opção **[!UICONTROL Log responses]**.

![](assets/s_ncs_admin_survey_trace.png)

A guia **[!UICONTROL Responses]** aparece para permitir que você visualize a identidade dos entrevistados.

![](assets/s_ncs_admin_survey_trace_tab.png)

Selecione um destinatário e clique no botão **[!UICONTROL Detail...]** para exibir as respostas fornecidas.

![](assets/s_ncs_admin_survey_trace_edit.png)

Você pode processar os logs de resposta fornecidos em queries, por exemplo, para direcionar somente aqueles que não responderam ao enviar lembretes ou oferecer comunicações específicas apenas aos que responderam.

### Importação de pacotes de formulários web {#import-web-packages}

Ao exportar e importar um pacote incluindo um formulário web de uma instância para outra (por exemplo, do preparo para produção), o status do formulário web na nova instância pode variar de acordo com várias condições. Os diferentes casos estão listados abaixo.

Saiba mais sobre os diferentes status de um formulário web [nesta seção](#life-cycle-of-a-form).

>[!NOTE]
>
>Ao exportar um formulário web por meio de um pacote, o status do formulário fica visível no conteúdo do pacote resultante.

* Se o status do formulário web era **[!UICONTROL Pending publication]** ou **[!UICONTROL Online]** quando exportado da primeira instância:

   * O formulário web ficará o status **[!UICONTROL Pending publication]** quando importado na nova instância.

   * Se o formulário web já existir na nova instância, ele será substituído pela nova versão do formulário e assumirá o status **[!UICONTROL Pending publication]**, mesmo que a versão antiga do formulário fosse **[!UICONTROL Online]**.

   * Independentemente da existência de um formulário igual, este deverá ser [publicado](#publishing-a-form) para se tornar **[!UICONTROL Online]** na nova instância e acessível através do URL do formulário web em um navegador.

* Se o status do formulário web era **[!UICONTROL Being edited]** quando exportado:

   * Se o formulário web for novo na instância em que o pacote foi importado, ele receberá o status **[!UICONTROL Being edited]**.

   * Se já houver um formulário web igual na nova instância, o formulário importado se tornará uma modificação desse formulário já existente. Se a versão antiga do formulário estava **[!UICONTROL Online]**, a versão antiga permanecerá online até que a nova versão do formulário seja [publicada](#publishing-a-form) na nova instância.

  >[!NOTE]
  >
  >É possível verificar a versão mais recente do seu formulário web na guia **[!UICONTROL Preview]**.

<!--For RN:
* Now, when a web form has the **Pending publication** status, it must be published before it becomes **Online** and accessible through the web form URL in a web browser. [Read more](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)
-->
