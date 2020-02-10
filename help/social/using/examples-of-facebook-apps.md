---
title: Exemplos de aplicativos do Facebook
seo-title: Exemplos de aplicativos do Facebook
description: Exemplos de aplicativos do Facebook
seo-description: null
page-status-flag: never-activated
uuid: 336f4006-3545-4b04-959d-61cd0446af27
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: annexes
discoiquuid: 07be1d3c-b038-48ca-be37-a33adb8e0fc0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7f03e1fbb94bbd5b00fa0094a0b5e9be45629ec7

---


# Exemplos de aplicativos do Facebook{#examples-of-facebook-apps}

Quando um usuário clica na guia de um aplicativo do Facebook, ela é exibida em um espaço com 810 pixels de largura. O Adobe Campaign usa um aplicativo da Web tipo Facebook para permitir que você defina e personalize o conteúdo exibido no aplicativo do Facebook, facilitando a aquisição de perfis.

>[!NOTE]
>
>Também é possível integrar o Adobe Campaign a um aplicativo do Facebook desenvolvido por um parceiro. Nesse caso, não há necessidade de usar o aplicativo da Web Adobe Campaign para adquirir perfis do Facebook. For more on this, refer to [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

>[!CAUTION]
>
>Siga as etapas de configuração descritas em [Criar um aplicativo](../../social/using/creating-a-facebook-application.md)do Facebook.

>[!NOTE]
>
>Esta seção detalha os elementos vinculados aos aplicativos da Web do tipo Facebook. Todos os elementos compartilhados com aplicativos da Web padrão são detalhados [nesta seção](../../web/using/about-web-applications.md).

Os exemplos de aplicativos da Web do tipo Facebook detalhados aqui são:

* Como criar um aplicativo do Facebook em 7 etapas. Consulte Início [rápido: criação de um aplicativo do Facebook em 7 etapas](#quick-start--creating-a-facebook-application-in-7-steps).
* Como encaminhar configurações para um aplicativo do Facebook. Consulte [Como encaminhar configurações para um aplicativo do Facebook?](#how-to-forward-settings-to-a-facebook-application-).
* Como adquirir dados do ventilador. Consulte [Como adquirir dados do ventilador?](#how-to-acquire-fan-data-).

>[!CAUTION]
>
>Estes casos de uso simples são fornecidos como exemplos para ilustrar as funcionalidades de aplicativos da Web do tipo Facebook.

## Recomendações {#recommendations}

As seguintes limitações estão vinculadas diretamente ao Facebook:

* Você deve criar todos os aplicativos da Web em HTTPS.
* Um aplicativo do Facebook exibido por meio de uma guia tem uma largura de 810 pixels.

## Início rápido: criação de um aplicativo do Facebook em 7 etapas {#quick-start--creating-a-facebook-application-in-7-steps}

Este exemplo fornece um processo passo a passo de como exibir um aplicativo criado pelo Adobe Campaign no Facebook. Nesse caso, queremos criar um aplicativo que permita exibir a mensagem de **boas-vindas** quando o usuário clicar na guia do aplicativo (**App01**).

Para criar esse aplicativo, aplique as seguintes etapas:

1. Crie um aplicativo no Facebook ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)). Para obter mais informações, consulte: [Criação de um aplicativo](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)do Facebook.

   ![](assets/social_create_facebook_app_002.png)

1. Crie um **[!UICONTROL Facebook Connect]** tipo de conta externa e insira os parâmetros do aplicativo do Facebook. For more on this, refer to: [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

   ![](assets/social_quick_start_2.png)

1. Digite os links **[!UICONTROL Terms of service]** e **[!UICONTROL Privacy policy]** a serem exibidos na tela de solicitação de permissão do Facebook. Para obter mais informações, consulte: [Inserir os links](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links)dos Termos de serviço e da Política de privacidade.

   ![](assets/social_quick_start_1.png)

1. Crie um aplicativo da Web tipo Facebook no Adobe Campaign. Para obter mais informações, consulte: [Criação de um aplicativo](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)da Web tipo Facebook.

   ![](assets/social_webapp_005.png)

1. Edite seu aplicativo da Web. Neste exemplo, adicionamos uma **[!UICONTROL Page]** atividade e definimos um título para ela.

   ![](assets/social_quick_start_4.png)

1. Implante seu aplicativo.

   ![](assets/social_webapp_004.png)

1. Configure seu aplicativo do Facebook para que ele seja exibido como uma guia em sua página do Facebook. For more on this, refer to: [Configuring Facebook tabs](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs).

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

Verifique se a guia do aplicativo **App01** é exibida em sua página do Facebook. Clicar nele deve chamar uma mensagem de **boas-vindas** .

![](assets/social_webapp_042.png)

## Como encaminhar configurações para um aplicativo do Facebook? {#how-to-forward-settings-to-a-facebook-application-}

>[!CAUTION]
>
>Siga as etapas de configuração detalhadas em [Criação de um aplicativo](../../social/using/creating-a-facebook-application.md)do Facebook.

No exemplo 1, personalizamos a exibição da página do Facebook de acordo com o valor no **[!UICONTROL Fan of the page]** campo. Também é possível processar o **[!UICONTROL Application settings]** campo. Esse campo permite recuperar dados contidos em um link gerado pelo Adobe Campaign, via Facebook.

Vejamos o exemplo de uma empresa que decide enviar uma campanha por email. Na entrega, um link aponta para o aplicativo do Facebook. Esse link é personalizado graças ao **[!UICONTROL app_data]** parâmetro adicionado ao final do URL. O valor desse parâmetro pode ser um indicador que reflete a significância do cliente. Em nosso exemplo, os valores do **[!UICONTROL app_data]** parâmetro são **[!UICONTROL big]** (cliente significativo) e **[!UICONTROL small]** (cliente menos significativo).

Depois de personalizada, o URL fica assim:

* `http://<path of the Facebook application>&app_data=big` (para um cliente significativo)
* `http://<path of the Facebook application>&app_data=small` (para um cliente menos significativo)

Entre os dados anônimos encaminhados ao Adobe Campaign pelo Facebook, o valor do **[!UICONTROL Application parameters]** campo é coletado, permitindo que o Adobe Campaign personalize a exibição do aplicativo com base nesse parâmetro.

Se o usuário for um cliente significativo (o valor do **[!UICONTROL app_data]** parâmetro é **[!UICONTROL big]**), a seguinte imagem será exibida:

![](assets/social_webapp_017.png)

Se o usuário for um cliente menos significativo (o valor do **[!UICONTROL app_data]** parâmetro é **[!UICONTROL small]**), a seguinte imagem será exibida:

![](assets/social_webapp_016.png)

Para recriar esse caso de uso, criamos um aplicativo da Web composto pelos seguintes elementos:

* Uma **[!UICONTROL Test]** atividade baseada no **[!UICONTROL Application parameter]** campo.
* duas páginas que contêm as imagens a serem exibidas de acordo com o valor do **[!UICONTROL Application parameter]** campo.

![](assets/social_webapp_018.png)

## Como adquirir dados de ventiladores? {#how-to-acquire-fan-data-}

>[!CAUTION]
>
>Siga as etapas de configuração detalhadas em [Criação de um aplicativo](../../social/using/creating-a-facebook-application.md)do Facebook.

Este exemplo mostra como entrar em contato com usuários do Facebook e oferecer a eles para compartilhar suas informações de perfil. Vejamos o exemplo de uma empresa que quer adquirir perspectivas e organiza um concurso em sua página do Facebook para atraí-las.

Sempre que um usuário clica na **[!UICONTROL App03]** guia, perguntamos se ele deseja participar da concorrência.

![](assets/social_webapp_fb_000.png)

Se decidirem participar no concurso, oferecemos-lhes que partilhem as suas informações de perfil.

![](assets/social_webapp_021.png)

Se eles concordarem em compartilhar suas informações, a tela a seguir será exibida.

![](assets/social_webapp_022.png)

Para criar esse caso de uso, criamos um aplicativo da Web que inclui os seguintes elementos:

* a **[!UICONTROL Test]** activity
* três páginas
* uma **[!UICONTROL Access control]** atividade
* a **[!UICONTROL Pre-loading]** activity
* a **[!UICONTROL Save]** activity
* uma **[!UICONTROL End]** atividade

![](assets/social_webapp_019.png)

### Atividade de teste {#test-activity}

A **[!UICONTROL Test]** atividade se baseia no campo **[!UICONTROL ID]** e **[!UICONTROL Application parameters]** .

![](assets/social_webapp_023.png)

É composto por três ramos:

* **[!UICONTROL identifier (UID) is empty]** : o identificador só será encaminhado pelo Facebook se o usuário já tiver concordado em compartilhar suas informações. O primeiro ramo da **[!UICONTROL Test]** atividade permite que você disponibilize a concorrência somente para usuários que nunca entraram, ou seja, aqueles com uma ID vazia.
* **[!UICONTROL application parameter equals 'thanks']** : para evitar um erro de exibição vinculado ao Facebook, a página final do aplicativo da Web aponta para o URL do aplicativo do Facebook ao qual o **[!UICONTROL app_data]** parâmetro é adicionado ao uso do **[!UICONTROL thanks]** valor (para obter mais informações, consulte: Atividade [final](#end-activity)). A segunda ramificação permite descobrir se o usuário provém da **[!UICONTROL End]** atividade da primeira ramificação (e acabou de entrar na concorrência) para exibir uma mensagem de agradecimento. Para obter mais informações sobre como usar parâmetros de URL adicionais, consulte: [Como encaminhar configurações para um aplicativo do Facebook?](#how-to-forward-settings-to-a-facebook-application-).
* **[!UICONTROL Default branch]** : se o usuário já tiver entrado na concorrência (ID já inserida) em uma data anterior (parâmetro de aplicativo diferente de **[!UICONTROL thanks]**), exibiremos uma página informando que já foi inserida.

### Página da concorrência {#competition-page}

Para contornar o erro de exibição vinculado ao Facebook, você também precisa selecionar **[!UICONTROL Parent window]** ou **[!UICONTROL In the top window]** no campo da página da **[!UICONTROL Window]** concorrência.

![](assets/social_webapp_028.png)

### Atividade de controle de acesso {#access-control-activity}

A **[!UICONTROL Access control]** atividade permite exibir a página de solicitação de permissão do Facebook quando o usuário entra na concorrência. Se eles concordarem em compartilhar suas informações, elas serão recuperadas durante o pré-carregamento. For more on this, refer to: [Pre-loading activity](#pre-loading-activity).

Se você tiver inserido a conta externa ao criar o aplicativo da Web (consulte [Criar um aplicativo](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)da Web tipo Facebook), não será necessário editar a atividade. Caso contrário, vá para o **[!UICONTROL Application]** campo e selecione a conta externa vinculada ao aplicativo do Facebook.

![](assets/social_webapp_024.png)

### Atividade de pré-carregamento {#pre-loading-activity}

Selecione a fonte de dados a ser usada para pré-carregamento:

* **[!UICONTROL Marketing database]** : essa opção permite pré-carregar dados pelo banco de dados do Adobe Campaign.
* **[!UICONTROL Facebook]** : essa opção permite pré-carregar dados usando o Facebook.

![](assets/social_webapp_029.png)

**Banco de dados de marketing**

Essa opção permite recuperar os dados de um perfil que existe na tabela de visitantes. A verificação é realizada com base na ID externa do Facebook recuperada quando o usuário clica na guia do aplicativo do Facebook. Se um formulário for adicionado após a **[!UICONTROL Pre-loading]** atividade, os campos que contêm informações no banco de dados serão pré-carregados.

![](assets/social_webapp_030.png)

>[!NOTE]
>
>Para obter mais informações sobre como pré-carregar dados pelo banco de dados do Adobe Campaign, consulte [esta seção](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

**Facebook**

Essa opção permite que você defina as informações de perfil do Facebook a serem coletadas, dentre as quais o usuário concordou em compartilhar, para salvá-las.

![](assets/social_webapp_025.png)

A **[!UICONTROL Database information]** opção permite coletar os seguintes dados:

* **[!UICONTROL External ID]**: ID do usuário
* **[!UICONTROL Gender]**: gênero do usuário
* **[!UICONTROL Verified]** : esse campo especifica se o usuário tem ou não uma conta verificada do Facebook.
* **[!UICONTROL Full name]**: nome completo do usuário
* **[!UICONTROL First name]**: nome do usuário
* **[!UICONTROL Last name]**: sobrenome do usuário
* **[!UICONTROL Language]**: idioma do usuário

Você também pode coletar a foto do perfil, a lista de amigos, o endereço de email, a data de nascimento, os interesses e o local, marcando as caixas apropriadas.

Antes de clicar **[!UICONTROL Ok]**, marque a **[!UICONTROL I agree to comply with Facebook conditions of use]** caixa.

>[!NOTE]
>
>Se você marcar uma ou mais caixas na **[!UICONTROL Private information]** seção, a tela de solicitação de permissão do Facebook exibirá automaticamente a solicitação de acesso para esses dados.
>
>Para que você colete as informações selecionadas, o usuário deve concordar em compartilhá-las.
>
>Se quiser que os dois tipos de pré-carregamento (via Adobe Campaign e via Facebook) adicionem duas caixas de pré-carregamento uma após a outra.

### Salvar atividade {#save-activity}

A **[!UICONTROL Save]** atividade permite armazenar as informações coletadas durante os estágios anteriores na tabela de visitantes.

Se o perfil já existir na tabela dos visitantes, seus dados serão atualizados com os novos dados coletados.

Se o perfil não existir no banco de dados e o endereço de email do usuário do Facebook tiver sido coletado, um visitante será criado na tabela dos visitantes.

![](assets/social_webapp_026.png)

1. No **[!UICONTROL Visitor creation folder]** campo, selecione a pasta na qual o perfil será criado. No caso de um aplicativo da Web tipo Facebook, a pasta de criação padrão é **[!UICONTROL Visitors]**.
1. No **[!UICONTROL Reconciliation mode]** campo, selecione o modo de reconciliação que deseja usar:

   * **[!UICONTROL Automatic]** : A reconciliação é realizada com base no email, sobrenome, nome e data de nascimento.
   * **[!UICONTROL Manual]** : Selecione uma ou mais chaves de reconciliação.
   * **[!UICONTROL None]** : Não haverá reconciliação.

1. No **[!UICONTROL Mapping]** campo, selecione o esquema no qual deseja realizar a reconciliação.

   >[!CAUTION]
   >
   >Certifique-se de que os campos da **[!UICONTROL Social networks]** guia estejam inseridos corretamente no mapeamento de entrega. Os mapeamentos de entrega são acessados pelo **[!UICONTROL Administration > Campaign management > Target mappings]** nó.

1. Você pode selecionar uma pasta de pesquisa para reconciliação e uma pasta de criação para novos perfis. Se os campos estiverem vazios, os perfis serão pesquisados e criados na pasta padrão do esquema de mapeamento.

### Finalizar atividade {#end-activity}

Para contornar o erro de exibição vinculado ao Facebook, é necessário marcar a **[!UICONTROL Use an external URL]** caixa e inserir o URL do aplicativo do Facebook, seguido pelo **[!UICONTROL app_data]** parâmetro e um valor. Esse valor será usado na **[!UICONTROL Test]** atividade para detectar se o usuário acabou de entrar na concorrência e para exibir uma mensagem de agradecimento, se aplicável. For more on this, refer to: [Test activity](#test-activity).

Em nosso exemplo, o valor usado é **graças**.

![](assets/social_webapp_027.png)

### Tela de detalhes de um visitante {#details-screen-of-a-visitor}

Assim como para os seguidores do Twitter (consulte: Princípio [](../../social/using/publishing-on-twitter.md#operating-principle)operacional), os perfis do Facebook recuperados são armazenados na tabela dos visitantes. Para exibir a lista de visitantes, vá para o **[!UICONTROL Profiles and Targets > Visitors]** nó.

Cada cliente potencial do Facebook que concorda em compartilhar suas informações de perfil é adicionado à lista de visitantes. Se a **[!UICONTROL Friends]** caixa estiver marcada na **[!UICONTROL Pre-load]** atividade (consulte: Atividade [de](#pre-loading-activity)pré-carregamento), amigos também são adicionados.

![](assets/social_webapp_037.png)

Na **[!UICONTROL Summary]** seção da janela de detalhes do visitante, há dois estados possíveis para o **[!UICONTROL New Contact]** indicador:

![](assets/social_webapp_038.png)

Se uma marca de seleção verde for exibida, isso significa que o visitante não foi reconciliado com nenhum destinatário. Nesse caso, um novo perfil é criado na lista de destinatários.

![](assets/social_webapp_039.png)

Uma cruz vermelha significa que o visitante foi reconciliado com um destinatário. Você pode clicar na lente de aumento à direita do **[!UICONTROL Recipient]** campo para exibir o destinatário correspondente.

![](assets/social_webapp_040.png)

Vá para a janela detalhada de um destinatário para exibir o visitante correspondente, se aplicável. Selecione a **[!UICONTROL Others]** guia e clique duas vezes no nome do visitante na **[!UICONTROL Web identities]** seção.

![](assets/social_webapp_041.png)

A **[!UICONTROL Activities]** tela da página de detalhes do visitante contém as seguintes informações:

* Atividades do ventilador do tipo &quot;Open Graph&quot;: música reproduzida, vídeos assistidos, artigos lidos e inferidos das aplicações instaladas (Deezer, Spotify, Dailymotion, Yahoo News etc.)

   ![](assets/social_facebook_activities.png)

* &quot;Curtidas&quot; e comentários adicionados pelo fã após as entregas enviadas pelo Adobe Campaign
* páginas curtidas pelo ventilador
* check-ins pelo ventilador

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >Para que o Adobe Campaign colete os check-ins de um ventilador, é necessário clicar no **[!UICONTROL Subscribe]** botão na tela de configuração do serviço. For more on this, refer to [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

## Como pré-carregar os campos de um formulário usando dados de perfil do Facebook {#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}

O **[!UICONTROL Social Marketing]** aplicativo também permite que você adicione um botão a um formulário, para pré-carregar campos usando informações de perfil do Facebook. Esta opção, que está disponível em todos os modelos de aplicativos da Web (**[!UICONTROL Page]** atividades de tipo), está detalhada [nesta seção](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/social_webapp_035.png)

>[!NOTE]
>
>Antes de começar a usar essa função, é necessário criar um aplicativo do Facebook e uma conta externa de **[!UICONTROL Facebook Connect]** tipo. For more on this, refer to [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

