---
title: Rastrear uma campanha
seo-title: Rastrear uma campanha
description: Rastrear uma campanha
seo-description: null
page-status-flag: never-activated
uuid: 66919c81-b22c-4138-a654-ea53154ba718
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: e1f8958d-f036-4635-be6e-ebdbea6ac116
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: eee744eb5bc7a43fd412ffb01f0546385146a978

---


# Rastrear uma campanha{#tracking-a-campaign}

Os operadores de entidade central podem rastrear pedidos de campanha na lista de pacotes de campanha.

Isso permite:

* [Pacotes de filtro](#filter-packages),
* [Edição de pacotes](#edit-packages),
* [Cancelamento de um pacote](#cancel-a-package),
* [Reinicializar um pacote](#reinitializing-a-package).

## Pacotes de filtro {#filter-packages}

No **[!UICONTROL Campaigns universe]**, é possível exibir a lista de **[!UICONTROL Campaign packages]** que reagrupa todas as campanhas existentes de Marketing Distribuído. É possível filtrar essa lista para exibir somente as campanhas publicadas, atrasadas, pendentes de aprovação etc. Para fazer isso, clique nos links na seção superior desta exibição ou use o link **[!UICONTROL Filter list]** e selecione o status do pacote da campanha a ser exibido.

![](assets/mkg_dist_catalog_filter.png)

## Edição de pacotes {#edit-packages}

A página **[!UICONTROL Campaign packages]** permite visualizar o resumo de cada pacote.

Este resumo mostra as seguintes informações: rótulo, tipo de campanha, bem como o nome da campanha da qual foi criada e a pasta.

Clique no nome do pacote para editá-lo. Você também pode visualizar pedidos por suas entidades locais e pelo seus status.

Essas informações também estão disponíveis na visualização **[!UICONTROL Campaign orders]**, que lista todas as ordens.

![](assets/mkg_dist_catalog_op_command_details.png)

O operador central pode editar o pedido. Há duas maneiras de fazer isso:

1. O operador pode clicar no nome do pedido para editá-lo: isso exibe o detalhe do pedido.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   A guia **[!UICONTROL Edit > General]** permite visualizar informações inseridas pela entidade local quando solicita a campanha.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. O operador pode clicar no rótulo do pacote de campanha para editá-lo e alterar determinadas configurações.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Cancelamento de um pacote {#cancel-a-package}

A entidade central pode cancelar um pacote de campanha a qualquer momento.

Clique em **[!UICONTROL Cancel]** no **[!UICONTROL Dashboard]** do pacote de campanha.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

O campo **[!UICONTROL Comment]** permite justificar o cancelamento.

Para **campanhas locais**, cancelar um pacote o remove da lista de campanhas de marketing disponíveis.

Para **campanhas colaborativas**, cancelar um pacote inicia várias ações:

1. Quaisquer pedidos relacionados a este pacote serão cancelados,

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. A campanha de referência é cancelada e todos os processos ativos (workflows, deliveries) são interrompidos,

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. Uma notificação é enviada a todas as entidades locais relacionadas.

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

Os pacotes cancelados ainda podem ser acessados e reiniciados pela entidade central (veja abaixo) se necessário. Eles só serão oferecidas às entidades locais quando forem aprovados e iniciados. O processo de reinicialização de pacote é mostrado abaixo.

## Reinicializar um pacote {#reinitializing-a-package}

Os pacotes de campanha que já foram publicados podem ser reiniciados, modificados e disponibilizados às entidades locais.

1. Selecione o pacote desejado.
1. Clique no link **[!UICONTROL Reinitialize the package to reuse it]** e clique em **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Clique em **[!UICONTROL Save]** para aprovar o pacote reinicialização.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. O status do pacote muda para **[!UICONTROL Being edited]**. Modifique, aprove e publique ele novamente para restaurá-lo na lista de pacotes de campanha.

>[!NOTE]
>
>Você também pode reinicializar pacotes de campanha cancelados.

