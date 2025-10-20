---
product: campaign
title: Definir a população alvo
description: Saiba como definir a população alvo
feature: Audiences, Proofs
role: User
hide: true
hidefromtoc: true
exl-id: d0ed7be7-3147-4cb8-9ce7-ea51602e9048
source-git-commit: 8817b485fd5b6d6aeb9d71c1106f16fbb6bc3c5b
workflow-type: ht
source-wordcount: '1730'
ht-degree: 100%

---

# Definir a população alvo {#defining-the-target-population}

Para cada entrega, você poderá definir vários tipos de populações de destino.

* **Público-alvo principal**: perfis que receberão mensagens. [Saiba mais](steps-defining-the-target-population.md#selecting-the-main-target)
* **Prova**: destinatários de mensagens de prova, envolvidos no ciclo de validação. [Saiba mais](steps-defining-the-target-population.md#defining-a-specific-proof-target)
* **Seed addresses**: destinatários que estão fora do target da entrega, mas receberão a entrega (somente no contexto de uma campanha de marketing). [Saiba mais](about-seed-addresses.md)
* **Grupos de controle**: população que não receberá a entrega, usado para rastrear o comportamento e o impacto da campanha (somente no contexto de uma campanha de marketing). [Saiba mais](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).

## Selecionar os principais destinatários da entrega {#selecting-the-main-target}

Na maioria dos casos, o público-alvo principal é extraído do banco de dados do Adobe Campaign (modo padrão). No entanto, os destinatários também podem ser armazenados em um arquivo externo. Saiba mais [nesta seção](steps-defining-the-target-population.md#selecting-external-recipients).

Para selecionar os destinatários da entrega, siga as etapas abaixo:

1. No editor de entrega, selecione **[!UICONTROL To]**.
1. Se os destinatários estiverem armazenados no banco de dados, selecione a primeira opção.

   ![](assets/s_ncs_user_wizard_email02a.png)

1. Selecione o target mapping na lista suspensa **[!UICONTROL Target mapping]**. O target mapping padrão do Adobe Campaign é **[!UICONTROL Recipients]**, baseado no esquema **nms:recipient**.

   Outros target mappings estão disponíveis e alguns podem ser relacionados à sua configuração específica.[Saiba mais](#select-a-target-mapping).

1. Clique no botão **[!UICONTROL Add]** para definir os filtros de restrição.

   Em seguida, é possível selecionar o tipo de filtragem a ser aplicado:

   ![](assets/s_ncs_user_wizard_email02b.png)

   Você poderá selecionar destinatários usando os tipos de direcionamento definidos no banco de dados. Para usar um tipo de target, selecione-o e clique em **[!UICONTROL Next]**. Para cada target, você poderá exibir os destinatários relacionados ao clicar na guia **[!UICONTROL Preview]**. Para certos tipos de target, o botão **[!UICONTROL Refine target]** permite combinar vários critérios de direcionamento.

   Os seguintes tipos de target são oferecidos por padrão:

   * **[!UICONTROL Filtering conditions]**: esta opção permite que você defina uma consulta e exiba o resultado. Para mais informações sobre filtros, consulte a [documentação do Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.
   * **[!UICONTROL Subscribers of an information service]**: esta opção permite que você selecione um boletim informativo ao qual os destinatários devem ser inscritos para receberem a entrega que está sendo criada.

     ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]**: essa opção permite definir os destinatários de uma entrega existente como um critério de direcionamento. Você deverá selecionar a entrega na lista:

     ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]**: essa opção permite selecionar uma pasta de entrega e apontar os destinatários das entregas nessa pasta.

     ![](assets/s_ncs_user_wizard_email02e.png)

     Você poderá filtrar o comportamento dos destinatários ao selecionar na lista suspensa:

     ![](assets/s_ncs_user_wizard_email02f.png)

     >[!NOTE]
     >
     >A opção **[!UICONTROL Include sub-folders]** também permite direcionar as entregas contidas nas pastas localizadas na estrutura de árvore abaixo do nó selecionado.

   * **[!UICONTROL Recipients included in a folder]**: essa opção permite que você direcione aos perfis contidos em uma pasta específica da árvore.
   * **[!UICONTROL A recipient]**: essa opção permite selecionar um destinatário específico dos perfis no banco de dados.
   * **[!UICONTROL A list of recipients]**: essa opção permite direcionar a uma lista de destinatários. As listas são apresentadas [nesta seção](../../platform/using/creating-and-managing-lists.md).
   * **[!UICONTROL User filters]**: essa opção permite que você acesse os filtros pré-configurados para usá-los como critérios de filtragem para perfis no banco de dados. Para mais informações sobre filtros, consulte a [documentação do Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.
   * A opção **[!UICONTROL Exclude recipients corresponding to this segment]** permite apontar os destinatários que não atendem aos critérios de target definidos. Para usar essa opção, selecione a caixa apropriada e, em seguida, aplique o direcionamento, conforme definido anteriormente, para excluir os perfis resultantes.

     ![](assets/s_ncs_user_wizard_email02g.png)

1. Insira um nome para esse direcionamento no campo **[!UICONTROL Label]**. Por padrão, o rótulo será o do primeiro critério de direcionamento. Para uma combinação, é melhor usar um nome explícito.
1. Clique em **[!UICONTROL Finish]** para validar o direcionamento configurado.

   Os critérios de direcionamento definidos são resumidos na seção central da guia de configuração do target principal. Clique em um critério para exibir seu conteúdo (configuração e visualização). Para excluir um critério, clique na cruz localizada depois de seu rótulo.

   ![](assets/s_ncs_user_wizard_email02h.png)

### Selecionar destinatários externos {#selecting-external-recipients}

Você poderá iniciar uma entrega nos destinatários que não estão salvos no banco de dados, mas armazenados em um arquivo externo. Por exemplo, enviaremos aqui uma entrega para os destinatários importados de um arquivo de texto.

Para isso:

1. Clique no link **[!UICONTROL To]** para selecionar os destinatários da sua entrega.
1. Selecione a opção **[!UICONTROL Defined in an external file]**.

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. Por padrão, os destinatários são importados do banco de dados. Você deverá selecionar o **[!UICONTROL Target mapping]**. [Saiba mais](#select-a-target-mapping)

   Você também pode escolher **[!UICONTROL Do not import the recipients into the database]**.

1. Ao importar os destinatários, clique no link **[!UICONTROL File format definition...]** para selecionar e configurar o arquivo externo.

   Para obter mais informações sobre importação de dados, consulte [esta seção](../../platform/using/executing-import-jobs.md#step-2---source-file-selection).

1. Clique em **[!UICONTROL Finish]** e configure sua entrega como uma entrega padrão.

>[!CAUTION]
>
>Ao definir o conteúdo da mensagem para entrega de email, não inclua o link para a mirror page; ele não poderá ser gerado nesse modo de entrega.

### Definir configurações de exclusão {#define-exclusion-settings}

Os erros de endereço e as classificações de qualidade são fornecidos pelo provedor de serviços (IAP). Essas informações são atualizadas automaticamente no perfil do destinatário após as ações de entrega e com arquivos retornados por provedores de serviços. Ele pode ser exibido no perfil somente como leitura.

Você poderá optar por excluir endereços que atingiram um determinado número de erros consecutivos ou cuja classificação de qualidade está abaixo de um limite especificado nessa janela. Você também poderá escolher se autoriza ou não endereços não qualificados para os quais nenhum dado foi retornado.

>[!NOTE]
>
>Se dois destinatários tiverem o mesmo nome, sobrenome, código postal e cidade em uma entrega direta de correspondência direta, ocorrerá um erro de duplicação. A duplicata não será levada em consideração.

A guia **[!UICONTROL Exclusions]** é usada para limitar o número de mensagens.

>[!NOTE]
>
>Os parâmetros padrão são recomendados, mas você poderá adaptar as configurações dependendo das suas necessidades. No entanto, essas opções só devem ser alteradas por um usuário expert para evitar qualquer erro ou mau uso.

Clique no link **[!UICONTROL Edit...]** para modificar a configuração padrão.

![](assets/s_ncs_user_wizard_email02i.png)

As seguintes opções estão disponíveis:

* **[!UICONTROL Exclude duplicate addresses during delivery]**. Essa opção está ativa por padrão: permite eliminar endereços de email duplicados durante a entrega. A estratégia aplicada pode variar de acordo com a forma como o Adobe Campaign é usado e o tipo de dados no banco de dados.

  O valor padrão da opção poderá ser configurado para cada modelo de entrega.

  Por exemplo:

   * Entrega de um boletim informativo ou entrega eletrônica de documentos. Nenhuma exclusão de duplicados, em alguns casos, se os dados não tiverem duplicados nativos. Um casal que faça assinatura usando o mesmo endereço de email poderá esperar receber duas mensagens de email personalizadas específicas: uma endereçada para cada pessoa por nome. Nesse caso, essa opção poderá ser desmarcada.
   * Entrega de uma campanha de marketing: a exclusão dos duplicados é essencial para evitar o envio de muitas mensagens para o mesmo destinatário. Nesse caso, essa opção poderá ser selecionada.

     Se você desmarcar esta opção, poderá acessar uma opção adicional: **[!UICONTROL Keep duplicate records (same identifier)]**. Ela permite autorizar várias entregas a destinatários que atendem a vários critérios de direcionamento.

     ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]**, ou seja, destinatários cujos endereços de email estão na lista de bloqueios (“opt out”). Essa opção deve permanecer selecionada para observar a ética profissional de marketing digital e as leis que regem o comércio eletrônico.
* **[!UICONTROL Exclude quarantined recipients]**. Essa opção permite excluir do target qualquer perfil que não responda. É altamente recomendável manter essa opção selecionada.

  >[!NOTE]
  >
  >Para obter mais informações sobre o gerenciamento de quarentena, consulte [Entender o gerenciamento de quarentena](understanding-quarantine-management.md).

* **[!UICONTROL Limit delivery]** para um determinado número de mensagens. Essa opção permite que você insira o número máximo de mensagens a serem enviadas. Se o conteúdo do target exceder o número de mensagens indicadas, uma seleção aleatória será aplicada ao target.

### Reduzir o tamanho da população alvo {#reducing-the-size-of-the-target-population}

É possível reduzir o tamanho da população do target. Para fazer isso, especifique o número de destinatários a serem exportados no campo **[!UICONTROL Requested quantity]**.

![](assets/s_ncs_user_edit_del_exe_tab.png)

## Selecionar os destinatários das mensagens de prova {#selecting-the-proof-target}

A prova é uma mensagem especial que permite testar uma entrega antes de enviá-la para o target principal. Os destinatários de prova são responsáveis pela aprovação do formulário e do conteúdo da mensagem.

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](#seeds-and-proofs-video)


Para selecionar o target das provas, siga as etapas abaixo:

1. Clique no link **[!UICONTROL To]**.
1. Clique na guia **[!UICONTROL Target of the proofs]**.
1. Clique no campo **[!UICONTROL Targeting mode]** para escolher o método a ser aplicado: **[!UICONTROL Definition of a specific proof target]** , **[!UICONTROL Substitution of the address]** , **[!UICONTROL Seed addresses]** ou **[!UICONTROL Specific target and seed addresses]**.

>[!NOTE]
>
>Normalmente, o target da prova poderá ser adicionado ao target principal. Para fazer isso, selecione a opção apropriada na seção inferior da guia **[!UICONTROL Main target]**.

## Definir público alvo específico da prova {#defining-a-specific-proof-target}

Ao selecionar o target da prova, a opção **[!UICONTROL Definition of a specific proof target]** permite selecionar os destinatários da prova nos perfis do banco de dados.

Selecione essa opção para escolher os destinatários usando o botão **[!UICONTROL Add]**, como no caso de definição do target principal. Consulte [Selecionar público alvo principal](steps-defining-the-target-population.md#selecting-the-main-target).

![](assets/s_ncs_user_wizard_email01_143.png)

Para saber mais sobre o envio de prova, consulte [esta seção](steps-validating-the-delivery.md#sending-a-proof).

### Usar substituição de endereço na prova {#using-address-substitution-in-proof}

Em vez de selecionar destinatários dedicados no banco de dados, você poderá usar a opção **[!UICONTROL Substitution of the address]**.

Essa opção permite usar os perfis de destinatário da entrega e substituir seus endereços de email por um ou mais endereços que receberão a prova.

Quando essa opção é selecionada, os endereços de prova são preenchidos por meio de um editor especial que permite configurar as substituições.

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

A configuração é executada da seguinte maneira:

1. Clique no ícone **[!UICONTROL Add]** para definir uma substituição.
1. Digite o endereço do destinatário a ser usado ou selecione-o na lista.
1. Selecione o perfil a ser usado na prova: salve o valor **[!UICONTROL Random]** na coluna **[!UICONTROL Profile to use]** para usar os dados de qualquer perfil do target na prova.

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. Clique no ícone **[!UICONTROL Detail]** para selecionar um perfil no target principal, como no exemplo a seguir:

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   É possível definir quantos endereços de substituição forem necessários.

## Usar seed addresses como prova {#using-seed-addresses-as-proof}

Você poderá usar **[!UICONTROL Seed addresses]** como target das provas: essa opção permite usar ou importar uma lista de seed addresses existente.

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>Os seed addresses são apresentados em [Sobre seed addresses](about-seed-addresses.md).

Você poderá combinar a definição de um target de prova específico e o uso de seed addresses usando a opção **[!UICONTROL Specific target and Seed addresses]**. As configurações relacionadas serão então definidas em duas sub-guias separadas.

Consulte também:

* [Selecionar o público alvo da prova](#selecting-the-proof-target)
* [Sobre seed addresses](about-seed-addresses.md)
* [Caso de uso: selecionar seed addresses de acordo com critérios](use-case-selecting-seed-addresses-on-criteria.md)

## Selecionar um target mapping {#select-a-target-mapping}

Por padrão, modelos de entrega direcionam **[!UICONTROL Recipients]**. O target mapping, portanto, usa os campos da tabela **nms:recipient**. O Adobe Campaign oferece outros target mapping para suas entregas, para serem usados conforme suas necessidades.

![](assets/delivery_select_mapping.png)

Esses mappings são os seguintes:

| Nome | Uso | Esquema padrão |
|---|---|---|
| Recipients | Entregar aos destinatários do banco de dados do Adobe Campaign | nms:recipient |
| Visitantes | Entregue aos visitantes cujos perfis foram coletados por meio de referências (marketing viral) ou por meio de redes sociais (X, anteriormente conhecido como Twitter, Facebook), por exemplo. | mns:visitor |
| Subscrições | Entregar aos destinatários que assinam um serviço de informações, como um boletim informativo | nms:subscription |
| Assinaturas do visitante | Entregar aos visitantes que são inscritos em um serviço de informações | nms:visitorSub |
| Serviço | Publicar em uma conta do X ou em uma página do Facebook | nms:service |
| Operadores | Entregar aos operadores do Adobe Campaign | nms:operator |
| Arquivo externo | Entregar por meio de um arquivo que contenha todas as informações necessárias para a entrega | Nenhum esquema vinculado, nenhum target inserido |


## Tutorial em vídeo {#seeds-and-proofs-video}

Este vídeo mostra como adicionar seeds e provas a um email existente e o procedimento para o seu envio.

>[!VIDEO](https://video.tv.adobe.com/v/35801?captions=por_br&quality=12)

Vídeos extras sobre procedimentos do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
