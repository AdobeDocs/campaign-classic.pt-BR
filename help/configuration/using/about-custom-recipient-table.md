---
title: Sobre a tabela de destinatários personalizados
seo-title: Sobre a tabela de destinatários personalizados
description: Sobre a tabela de destinatários personalizados
seo-description: null
page-status-flag: never-activated
uuid: 4b162da4-90d2-44ff-9f89-ff0275540359
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: c3ff8462-e47e-4637-8213-769fdeb86a57
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 668a0093616e1a2b49623b010ae5055f4d43d9b9

---


# Sobre a tabela de destinatários personalizados{#about-custom-recipient-table}

Esta seção detalha os princípios para usar uma tabela de destinatários não padrão.

Por padrão, o Adobe Campaign oferece uma tabela de destinatários padrão à qual funções e processos prontos para uso estão vinculados. A tabela de destinatários padrão tem vários campos e tabelas predefinidos que podem ser facilmente estendidos usando uma tabela de extensão.

Se esse método de extensão oferecer uma boa flexibilidade para estender uma tabela, ele não permitirá a redução do número de campos ou links nela contidos. O uso de uma tabela não padrão, ou &quot;tabela de destinatários externos&quot;, permite maior flexibilidade, mas requer determinadas precauções ao implementá-la.

## Precisões {#precisions}

Essa funcionalidade permite que o Adobe Campaign processe dados de um banco de dados externo: esses dados serão usados como um conjunto de perfis para entregas. A implementação deste processo envolve várias precisões que podem ser relevantes de acordo com as necessidades do cliente. Como:

* Nenhum fluxo de atualização de e para o banco de dados do Adobe Campaign: os dados desta tabela podem ser atualizados diretamente pelo mecanismo de banco de dados que os hospeda.
* Nenhuma alteração nos processos que operam no banco de dados existente.
* Usando um banco de dados de perfil com uma estrutura não padrão: possibilidade de fornecer perfis salvos em várias tabelas com várias estruturas, usando uma única instância.
* Nenhuma alteração ou manutenção é necessária ao atualizar o banco de dados do Adobe Campaign.
* A tabela de destinatários padrão é inútil se você não precisar da maioria dos campos de tabela ou se o modelo de banco de dados não estiver centralizado nos destinatários.
* Para ser eficiente, uma tabela com alguns campos é necessária se você tiver um número significativo de perfis. A tabela de destinatários padrão tem muitos campos para esse caso específico.

Esta seção descreve os pontos principais que permitem mapear tabelas existentes no Adobe Campaign e a configuração a ser aplicada para executar entregas com base em qualquer tabela. Por fim, ele descreve como fornecer aos usuários interfaces de consulta tão práticas quanto aquelas disponíveis na tabela de destinatários padrão. Para entender o material apresentado nesta seção, é necessário um bom conhecimento dos princípios de projeto de tela e esquema.

## Recomendações e limitações {#recommendations-and-limitations}

O uso de uma tabela de destinatários externos tem as seguintes limitações:

* O Adobe Campaign não oferece suporte a vários esquemas de destinatários, conhecidos como esquemas de definição de metas, vinculados aos mesmos esquemas de registro de transmissão e/ou rastreamento. Caso contrário, isso pode resultar em anomalias na reconciliação de dados posteriormente.

   O gráfico abaixo detalha a estrutura relacional necessária para cada esquema de destinatário personalizado:
   ![](assets/custom_recipient_limitation.png)

   Recomendamos:

   * Dedicando os **[!UICONTROL nms:BroadLogRcp]** e **[!UICONTROL nms:TrackingLogRcp]** esquemas ao pronto-a-usar **[!UICONTROL nms:Recipientschema]**. Essas duas tabelas de log não devem ser vinculadas a nenhuma tabela de destinatários personalizada adicional.
   * Definindo esquemas dedicados de log de fluxo e log de rastreamento para cada novo esquema de destinatário personalizado. Isso pode ser feito automaticamente ao configurar o mapeamento de destino, consulte Mapeamento [do](../../configuration/using/target-mapping.md)Target.

* Não é possível usar o padrão **[!UICONTROL Services and Subscriptions]** oferecido no produto.

   Isto significa que a operação global descrita na [presente seção](../../delivery/using/managing-subscriptions.md) não é aplicável.

* O link com a **[!UICONTROL visitor]** tabela não funciona.

   Assim, para usar o módulo **[!UICONTROLSSocial Marketing]** , é necessário configurar a etapa de armazenamento para fazer referência à tabela correta.

   Da mesma forma, ao utilizar funções de referência, o modelo de transferência de mensagem inicial padrão deve ser adaptado.

* Não é possível adicionar perfis manualmente em uma lista.

   Por conseguinte, o procedimento descrito na [presente seção](../../platform/using/creating-and-managing-lists.md) não é aplicável sem uma configuração adicional.

   >[!NOTE]
   >
   >Você ainda pode criar listas de destinatários usando fluxos de trabalho. Para obter mais informações, consulte [Criação de uma lista de perfis com um fluxo de trabalho](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

Também recomendamos verificar os valores padrão usados nas diferentes configurações predefinidas: em função das funcionalidades utilizadas, devem ser efetuadas várias adaptações.

Por exemplo:

* Alguns relatórios padrão, em especial os oferecidos pela **Interaction** e pelas Aplicações **** Móveis, devem ser redesenvolvidos. Consulte a seção [Gerenciar relatórios](../../configuration/using/managing-reports.md) .
* As configurações padrão para determinadas atividades de fluxo de trabalho fazem referência à tabela de destinatários padrão (**[!UICONTROL nms:recipient]**): essas configurações devem ser alteradas quando usadas para uma tabela de destinatários externos. Consulte a seção [Gerenciamento de fluxos de trabalho](../../configuration/using/managing-workflows.md) .
* O bloco de **[!UICONTROL Unsubscription link]** personalização padrão deve ser adaptado.
* O mapeamento de destino dos modelos de entrega padrão deve ser modificado.
* Os formulários V4 não são compatíveis para uso com uma tabela de destinatários externos: você deve usar aplicativos da Web.

