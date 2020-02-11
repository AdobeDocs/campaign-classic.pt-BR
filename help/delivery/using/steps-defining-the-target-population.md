---
title: Definição da população do target
seo-title: Definição da população do target
description: Definição da população do target
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 62e6537ba306956cac3bf6e1dd18567bc1414917

---


# Definição da população do target {#defining-the-target-population}

## Sobre as populações do target {#about-target-populations}

Para cada entrega, é possível definir vários tipos de populações-alvo. A seção abaixo fornece mais informações sobre como selecionar:

* **Os principais destinatários da entrega**. [Leia mais](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target).
* **Os destinatários das mensagens** de prova, para configurar um ciclo de validação. [Leia mais](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target).

Além disso, também é possível definir endereços [](../../delivery/using/about-seed-addresses.md)semente e grupos [de](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)controle. se a entrega for incluída em uma campanha de marketing.

## Selecionar os principais destinatários da entrega {#selecting-the-main-target}

Na maioria dos casos, o target principal é extraído do banco de dados do Campaign (modo padrão).

Os recipients também podem ser armazenados em um arquivo externo. The configuration of this type of delivery is presented in [Selecting external recipients](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

Para selecionar os destinatários da entrega que está sendo criada, siga estas etapas:

1. Clique no **[!UICONTROL To]** link.
1. Se os recipients estiverem armazenados no banco de dados, selecione a primeira opção.

   ![](assets/s_ncs_user_wizard_email02a.png)

1. Select the target mapping in the **[!UICONTROL Target mapping]** drop-down list. Adobe Campaign default target mapping is **[!UICONTROL Recipients]**.

   Outros target mappings estão disponíveis e alguns podem ser relacionados à sua configuração específica. Para obter mais informações sobre mapeamentos de destino, consulte [Seleção de um mapeamento](../../delivery/using/selecting-a-target-mapping.md)de destino.

1. Click the **[!UICONTROL Add]** button to define restriction filters.

   Em seguida, é possível selecionar o tipo de filtragem a ser aplicado:

   ![](assets/s_ncs_user_wizard_email02b.png)

   Você poderá selecionar recipients usando os tipos de metas definidos no banco de dados. To use a target type, select it and click **[!UICONTROL Next]**. For each target, you can display the recipients concerned by clicking the **[!UICONTROL Preview]** tab. For certain types of target, the **[!UICONTROL Refine target]** button lets you combine several targeting criteria.

   Os seguintes tipos de target são oferecidos por padrão:

   * **[!UICONTROL Filtering conditions]** : essa opção permite definir uma consulta e exibir o resultado. O método para definir queries é apresentado [nesta seção](../../platform/using/creating-filters.md#creating-an-advanced-filter).
   * **[!UICONTROL Subscribers of an information service]** : essa opção permite que você selecione um boletim informativo no qual os destinatários devem se inscrever para ser direcionado pela entrega que está sendo criada.

      ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** : essa opção permite que você defina os destinatários de uma entrega existente como um critério de direcionamento. Você deverá selecionar o delivery na lista:

      ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** : essa opção permite selecionar uma pasta de entrega e direcionar os destinatários das entregas nessa pasta.

      ![](assets/s_ncs_user_wizard_email02e.png)

      Você poderá filtrar o comportamento dos recipients ao selecionar na lista suspensa:

      ![](assets/s_ncs_user_wizard_email02f.png)

      >[!NOTE]
      >
      >The **[!UICONTROL Include sub-folders]** option also lets you target the deliveries contained in folders located in the tree structure below the selected node.

   * **[!UICONTROL Recipients included in a folder]** : essa opção permite direcionar os perfis contidos em uma pasta específica da árvore.
   * **[!UICONTROL A recipient]** : essa opção permite selecionar um destinatário específico dos perfis no banco de dados.
   * **[!UICONTROL A list of recipients]** : essa opção permite direcionar uma lista de destinatários. As listas são apresentadas [neste seção](../../platform/using/creating-and-managing-lists.md).
   * **[!UICONTROL User filters]** : essa opção permite acessar os filtros pré-configurados para usá-los como critérios de filtragem para perfis no banco de dados. Os flitros pré-configurados são apresentados [nesta seção](../../platform/using/creating-filters.md#saving-a-filter).
   * The option **[!UICONTROL Exclude recipients corresponding to this segment]** lets you target on recipients who do not satisfy the defined target criteria. Para usar essa opção, selecione a caixa apropriada e, em seguida, aplique o direcionamento, conforme definido anteriormente, para excluir os perfis resultantes.

      ![](assets/s_ncs_user_wizard_email02g.png)

1. Enter a name for this targeting in the **[!UICONTROL Label]** field. Por padrão, o rótulo será o do primeiro critério de direcionamento. Para uma combinação, é melhor usar um nome explícito.
1. Click **[!UICONTROL Finish]** to validate the configured targeting.

   Os critérios de definição do target definidos são resumidos na seção central da guia de configuração do target principal. Clique em um critério para exibir seu conteúdo (configuração e visualização). Para excluir um critério, clique na cruz localizada depois de seu rótulo.

   ![](assets/s_ncs_user_wizard_email02h.png)

### Selecionando recipients externos {#selecting-external-recipients}

Você poderá iniciar um delivery nos recipients que não estão salvos no banco de dados, mas armazenados em um arquivo externo. Por exemplo, enviaremos aqui um delivery para os recipients importados de um arquivo de texto.

Para fazer isso:

1. Click the **[!UICONTROL To]** link to select the recipients of your delivery.
1. Selecione a **[!UICONTROL Defined in an external file]** opção.

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. Por padrão, os recipients são importados do banco de dados. Você deve selecionar o **[!UICONTROL Target mapping]**. Para obter mais informações sobre mapeamentos de destino, consulte [Selecionar um mapeamento de destino](../../delivery/using/selecting-a-target-mapping.md)

   Você também pode escolher **[!UICONTROL Do not import the recipients into the database]**.

1. When importing the recipients, click the **[!UICONTROL File format definition...]** link to select and configure the external file.

   Para obter mais informações sobre importanção de dados, consulte [esta seção](../../platform/using/importing-data.md#step-2---source-file-selection).

1. Click **[!UICONTROL Finish]** and configure your delivery as a standard delivery.

>[!CAUTION]
>
>Ao definir o conteúdo da mensagem para delivery de email, não inclua o link para a página espelho; ele não poderá ser gerado nesse modo de delivery.

### Configuração de configurações de exclusão {#customizing-exclusion-settings}

Os erros de endereço e as classificações de qualidade são fornecidos pelo provedor de serviços (IAP). Essas informações são atualizadas automaticamente no perfil do recipient após as ações de delivery e com arquivos retornados por provedores de serviços. Ele pode ser exibido no perfil somente como leitura.

Você poderá optar por excluir endereços que atingiram um determinado número de erros consecutivos ou cuja classificação de qualidade está abaixo de um limite especificado nessa janela. Você também poderá escolher se autoriza ou não endereços não qualificados para os quais nenhum dado foi retornado.

>[!NOTE]
>
>Se dois recipients tiverem o mesmo nome, sobrenome, código postal e cidade em uma delivery direto de mala direta, ocorrerá um erro de duplicação. A duplicata não será levada em consideração.

The **[!UICONTROL Exclusions]** tab is used to limit the number of messages.

>[!NOTE]
>
>Os parâmetros padrão são recomendados, mas você poderá adaptar as configurações dependendo das suas necessidades. No entanto, essas opções só devem ser alteradas por um usuário expert para evitar qualquer erro ou mau uso.

Click the **[!UICONTROL Edit...]** link to modify the default configuration.

![](assets/s_ncs_user_wizard_email02i.png)

As seguintes opções estão disponíveis:

* **[!UICONTROL Exclude duplicate addresses during delivery]**. Essa opção está ativa por padrão: permite eliminar endereços de email duplicados durante o delivery. A estratégia aplicada pode variar de acordo com a forma como o Adobe Campaign é usado e o tipo de dados no banco de dados.

   O valor padrão da opção poderá ser configurado para cada template de delivery.

   Por exemplo:

   * Delivery de um boletim informativo ou delivery eletrônica de documentos. Nenhuma exclusão de duplicatas, em alguns casos, se os dados não tiverem duplicatas nativas. Um casal que faça assinatura usando o mesmo endereço de email poderá esperar receber duas mensagens de email personalizadas específicas: uma endereçada para cada indivíduo por nome. Nesse caso, essa opção poderá ser desmarcada.
   * Delivery de uma campanha de marketing: a exclusão duplicata é essencial para evitar o envio de muitas mensagens para o mesmo recipient. Nesse caso, essa opção poderá ser selecionada.

      Se você desmarcar esta opção, poderá acessar uma opção adicional: **[!UICONTROL Keep duplicate records (same identifier)]**. Ela permite autorizar vários deliveries a recipients que atendem a vários critérios de definição do target.

      ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]** , ou seja, destinatários cujos endereços de email estão em uma lista negra (&quot;recusa&quot;). Essa opção deve permanecer selecionada para observar a ética profissional de marketing digital e as leis que regem o comércio eletrônico.
* **[!UICONTROL Exclude quarantined recipients]**. Essa opção permite excluir do target qualquer perfil que não responda. É altamente recomendável manter essa opção selecionada.

   >[!NOTE]
   >
   >Para obter mais informações sobre o gerenciamento de quarentena, consulte [Entendendo o gerenciamento](../../delivery/using/understanding-quarantine-management.md)de quarentena.

* **[!UICONTROL Limit delivery]** para um determinado número de mensagens. Essa opção permite que você insira o número máximo de mensagens a serem enviadas. Se o conteúdo do target exceder o número de mensagens indicadas, uma seleção aleatória será aplicada ao target.

### Redução do tamanho da população do target {#reducing-the-size-of-the-target-population}

Você poderá reduzir o tamanho da população do target. To do this, specify the number of recipients to be exported in the **[!UICONTROL Requested quantity]** field.

![](assets/s_ncs_user_edit_del_exe_tab.png)

## Selecionar os destinatários das mensagens de prova {#selecting-the-proof-target}

A prova é uma mensagem especial que permite testar um delivery antes de enviá-lo para o target principal. Os recipients de prova são responsáveis pela aprovação do formulário e do conteúdo da mensagem.

Para selecionar o target das provas, siga as etapas abaixo:

1. Clique no **[!UICONTROL To]** link.
1.  Clique na **[!UICONTROL Target of the proofs]** guia.
1. Clique no **[!UICONTROL Targeting mode]** campo para escolher o método a ser aplicado: **[!UICONTROL Definition of a specific proof target]** , **[!UICONTROL Substitution of the address]** , **[!UICONTROL Seed addresses]** ou **[!UICONTROL Specific target and seed addresses]**.

>[!NOTE]
>
>Normalmente, o target da prova poderá ser adicionado ao target principal. To do this, select the appropriate option in the lower section of the **[!UICONTROL Main target]** tab.

## Definição de um target de prova específico {#defining-a-specific-proof-target}

When selecting the proof target, the **[!UICONTROL Definition of a specific proof target]** option lets you select the proof recipients from the profiles in the database.

Select this option to choose recipients using the **[!UICONTROL Add]** button, as in the case of defining the main target. See [Selecting the main target](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target).

![](assets/s_ncs_user_wizard_email01_143.png)

For more on proof sending, refer to [this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Usar substituição de endereço na prova {#using-address-substitution-in-proof}

Instead of selecting dedicated recipients in the database, you can use the **[!UICONTROL Substitution of the address]** option.

Essa opção permite usar os perfis de recipient do delivery e substituir seus endereços de email por um ou mais endereços que receberão a prova.

Quando essa opção é selecionada, os endereços de prova são preenchidos por meio de um editor especial que permite configurar as substituições.

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

A configuração é executada da seguinte maneira:

1. Click the **[!UICONTROL Add]** icon to define a substitution.
1. Digite o endereço do recipient a ser usado ou selecione-o na lista.
1. Select the profile to use in the proof: save the **[!UICONTROL Random]** value in the **[!UICONTROL Profile to use]** column to use the data of any profile of the target in the proof.

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. Click the **[!UICONTROL Detail]** icon to select a profile from the main target, as in the following example:

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   Você poderá definir quantos endereços de substituição forem necessários.

## Utilizando seed addresses como prova {#using-seed-addresses-as-proof}

You can use **[!UICONTROL Seed addresses]** as target of the proofs: this option lets you use or import a list of existing seed addresses.

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>Os endereços semente são apresentados em [Sobre endereços](../../delivery/using/about-seed-addresses.md)semente.

You can combine the definition of a specific proof target and the use of seed addresses using the **[!UICONTROL Specific target and Seed addresses]** option. As configurações relacionadas serão então definidas em duas sub-guias separadas.
