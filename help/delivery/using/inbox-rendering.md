---
product: campaign
title: Renderização da caixa de entrada   no Campaign
description: Saiba como capturar renderizações de email e disponibilizá-las em um relatório dedicado
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Inbox Rendering, Monitoring, Email Rendering
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
source-git-commit: e011333411af79b985166a4e73592a1860749cf1
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 98%

---

# Renderização da caixa de entrada{#inbox-rendering}



## Sobre renderização da caixa de entrada {#about-inbox-rendering}

Antes de clicar no botão **Enviar**, verifique se a sua mensagem será exibida aos recipients de forma eficaz em uma variedade de clientes Web, Webmails e dispositivos.

Para permitir isso, o Adobe Campaign aproveita a solução de teste de email baseada na Web [Litmus](https://litmus.com/email-testing) para capturar a renderização e disponibilizá-la em um relatório específico. Isso permite que você visualize a mensagem enviada nos diferentes contextos em que ela pode ser recebida e verificar a compatibilidade nos principais desktops e aplicativos.

>[!CAUTION]
>A renderização da caixa de entrada não é compatível com [entregas recorrentes](communication-channels.md#recurring-delivery).

O Litmus é um aplicativo de validação e visualização de email com recursos completos. Ele permite que criadores de conteúdo de email visualizem o conteúdo de sua mensagem em mais de 70 renderizadores de email, como a caixa de entrada do Gmail ou o cliente Apple Mail.

Os clientes de dispositivos móveis, mensagens e webmail disponíveis para a **Renderização da caixa de entrada** no Adobe Campaign estão listados no [site do Litmus](https://litmus.com/email-testing) (clique em **Exibir todos os clientes de email**).

>[!NOTE]
>
>A renderização da caixa de entrada não é necessária para testar a personalização nos deliveries. A personalização pode ser verificada com as ferramentas do Adobe Campaign, como **[!UICONTROL Preview]** e [Provas](steps-validating-the-delivery.md#sending-a-proof).

## Ativação da renderização da caixa de entrada {#activating-inbox-rendering}

[!BADGE No local e híbrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplicável somente a implantações locais e híbridas"}

Para clientes hospedados e híbridos, a renderização da Caixa de entrada é configurada em sua instância pelo suporte técnico e consultores da Adobe. Para obter mais informações, entre em contato com o executivo da sua conta Adobe.

Para instalações no local, siga as etapas abaixo para configurar a renderização da Caixa de entrada.

1. Instale o pacote **[!UICONTROL Inbox rendering (IR)]** usando o menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**. Para obter mais informações, consulte [Instalação de pacotes padrão do Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).
1. Configure uma conta externa do tipo HTTP por meio do nó **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**. Para obter mais informações, consulte [Criação de uma conta externa](../../installation/using/external-accounts.md#creating-an-external-account).
1. Defina os parâmetros da conta externa da seguinte maneira:
   * **[!UICONTROL Label]**: informações de entregabilidade do servidor
   * **[!UICONTROL Internal name]**: deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: nenhuma
   * Marque a opção **[!UICONTROL Enabled]**.

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Vá para o nó **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Procure a opção **[!UICONTROL DmRendering_cuid]** e entre em contato com o suporte para obter o identificador de relatórios da entrega que precisa ser copiado para o campo **[!UICONTROL Value (text)]**.
1. Edite o arquivo **serverConf.xml** para permitir uma chamada para o servidor Litmus. Adicione a seguinte linha à `<urlPermission>` seção:

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. Recarregue a configuração usando o seguinte comando:

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>Talvez seja necessário fazer logout do console e login novamente para poder usar a renderização da Caixa de entrada.

## Sobre tokens Litmus {#about-litmus-tokens}

Como Litmus é um serviço de terceiros, ele funciona em um modelo credit-per-usage. Cada vez que um usuário chamar a funcionalidade Litmus, o crédito será deduzido.

No Adobe Campaign, o crédito corresponde ao número de renderizações disponíveis (conhecidos como tokens).

>[!NOTE]
>
>O número de tokens Litmus disponíveis depende da licença adquirida do Campaign. Verifique o contrato da licença.

Cada vez que você usa o recurso **[!UICONTROL Inbox rendering]** em uma entrega, cada renderização gerada diminui um de seus tokens disponíveis.

>[!IMPORTANT]
>
>Os tokens são contabilizados para cada renderização individual e não para o relatório de renderização da Caixa de Entrada, significando que:
>
>* Cada vez que o relatório de renderização da Caixa de Entrada é gerado, é deduzido um token por cliente da mensagem: um token para a renderização do Outlook 2000, um para a renderização do Outlook 2010, um para a renderização do Apple Mail 9 e assim por diante.
>* Para a mesma entrega, se você gerar a renderização da Caixa de Entrada novamente, o número de tokens disponíveis será reduzido novamente pelo número de renderizações geradas.
>


O número de tokens disponíveis restantes é exibido no **[!UICONTROL General summary]** do [relatório de renderização da Caixa de entrada](#inbox-rendering-report)

![](assets/s_tn_inbox_rendering_tokens.png)

Normalmente, o recurso de renderização da Caixa de Entrada é usado para testar a estrutura HTML de um email recém-criado. Cada renderização requer aproximadamente até 70 tokens (dependendo do número de ambientes geralmente testados). No entanto, em alguns casos, podem ser necessários vários relatórios de renderização da caixa de entrada para testar totalmente sua entrega. Portanto, seriam necessários mais tokens para completar várias verificações.

## Acesso ao relatório de renderização da caixa de entrada {#accessing-the-inbox-rendering-report}

Após criar sua entrega de email e definir seu conteúdo, assim como a população alvo, siga as etapas abaixo.

Para obter mais informações sobre como criar, desenvolver e segmentar uma entrega, consulte [esta seção](about-email-channel.md).

1. Na barra superior da entrega, clique no botão **[!UICONTROL Inbox rendering]**.
1. Selecione **[!UICONTROL Analyze]** para iniciar o processo de captura.

   ![](assets/s_tn_inbox_rendering_button.png)

   Uma prova é enviada. Você pode acessar as miniaturas de renderização nessa prova alguns minutos após o envio dos emails. Para obter mais informações sobre o envio de provas, consulte [esta seção](steps-validating-the-delivery.md#sending-a-proof).

1. Após ser enviada, a prova aparece na lista de entregas. Clique duas vezes nela.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. Vá para a guia **Renderização da caixa de entrada** da prova.

   ![](assets/s_tn_inbox_rendering_tab.png)

   O relatório de renderização da caixa de entrada é exibido.

## Relatório de renderização da caixa de entrada {#inbox-rendering-report}

Este relatório exibe as renderizações da caixa de entrada como são exibidas para o recipient. As renderizações podem ser diferentes com base em como o recipient abre a entrega de email: em um navegador, em um dispositivo móvel ou por um aplicativo de email.

O **[!UICONTROL General summary]** apresenta em uma lista e por meio de uma representação gráfica colorida o número de mensagens recebidas, indesejadas (spam), não recebidas ou com recebimento pendente.

![](assets/s_tn_inbox_rendering_summary.png)

Passe o mouse sobre o gráfico para exibir os detalhes para cada cor.

O conjunto do relatório está dividido em três partes: **[!UICONTROL Mobile]**, **[!UICONTROL Messaging clients]** e **[!UICONTROL Webmails]**. Role para baixo no relatório para exibir todas as renderizações agrupadas nessas três categorias.

![](assets/s_tn_inbox_rendering_report.png)

Para obter os detalhes de cada relatório, clique no cartão correspondente. A renderização é exibida para o método de recebimento selecionado.

![](assets/s_tn_inbox_rendering_example.png)
