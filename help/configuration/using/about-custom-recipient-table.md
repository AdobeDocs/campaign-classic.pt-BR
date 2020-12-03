---
solution: Campaign Classic
product: campaign
title: Sobre tabela de recipient personalizada
description: Sobre tabela de recipient personalizada
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 2%

---


# Sobre tabela de recipient personalizada{#about-custom-recipient-table}

Esta seção detalha os princípios para usar uma tabela de recipient não padrão.

Por padrão, a Adobe Campaign oferta uma tabela de recipient padrão à qual funções e processos prontos para uso estão vinculados. A tabela de recipient padrão tem vários campos e tabelas predefinidos que podem ser facilmente estendidos usando uma tabela de extensão.

Se esse método de extensão oferta uma boa flexibilidade para estender uma tabela, ele não permitirá a redução do número de campos ou links nela contidos. O uso de uma tabela não padrão, ou &quot;tabela de recipient externos&quot;, permite maior flexibilidade, mas requer determinadas precauções ao implementá-la.

## Precisões {#precisions}

Essa funcionalidade permite que a Adobe Campaign processe dados de um banco de dados externo: esses dados serão usados como um conjunto de perfis para delivery. A implementação deste processo envolve várias precisões que podem ser relevantes de acordo com as necessidades do cliente. Como:

* Nenhum fluxo de atualização de e para o banco de dados Adobe Campaign: os dados desta tabela podem ser atualizados diretamente pelo mecanismo de banco de dados que os hospeda.
* Nenhuma alteração nos processos que operam no banco de dados existente.
* Usando um banco de dados de perfis com uma estrutura não padrão: possibilidade de entrega em perfis salvos em várias tabelas com várias estruturas, usando uma única instância.
* Nenhuma alteração ou manutenção necessária ao atualizar o banco de dados Adobe Campaign.
* A tabela de recipient padrão é inútil se você não precisar da maioria dos campos da tabela ou se o modelo de banco de dados não estiver centralizado nos recipient.
* Para ser eficiente, uma tabela com poucos campos é necessária se você tiver um número significativo de perfis. A tabela de recipient padrão tem muitos campos para esse caso específico.

Esta seção descreve os pontos principais que permitem mapear tabelas existentes no Adobe Campaign e a configuração a ser aplicada para executar delivery com base em qualquer tabela. Por fim, ele descreve como fornecer aos usuários interfaces de consulta tão práticas quanto aquelas disponíveis na tabela de recipient padrão. Para compreender o material apresentado nesta seção, é necessário um bom conhecimento dos princípios de concepção do ecrã e do schema.

## Recommendations e limitações {#recommendations-and-limitations}

O uso de uma tabela de recipient externos tem as seguintes limitações:

* A Adobe Campaign não suporta vários schemas de recipient, conhecidos como schemas de definição de metas, vinculados aos mesmos schemas de registro de transmissão e/ou rastreamento. Caso contrário, isso pode resultar em anomalias na reconciliação de dados posteriormente.

   O gráfico abaixo detalha a estrutura relacional necessária para cada schema de recipient personalizado:
   ![](assets/custom_recipient_limitation.png)

   Recomendamos:

   * Dedicando os schemas **[!UICONTROL nms:BroadLogRcp]** e **[!UICONTROL nms:TrackingLogRcp]** aos  predefinidos **[!UICONTROL nms:Recipientschema]**. Essas duas tabelas de log não devem ser vinculadas a nenhuma tabela de recipient personalizada adicional.
   * Definição de schemas personalizados de log de fluxo e rastreamento para cada novo schema de recipient personalizado. Isso pode ser feito automaticamente ao configurar o target mapping, consulte [Target mapping](../../configuration/using/target-mapping.md).

* Você não pode usar o padrão **[!UICONTROL Services and Subscriptions]** oferecido no produto.

   Isso significa que a operação geral detalhada em [this section](../../delivery/using/managing-subscriptions.md) não é aplicável.

* O link com a tabela **[!UICONTROL visitor]** não funciona.

   Assim, para usar o módulo **[!UICONTROL Social Marketing]**, é necessário configurar a etapa do armazenamento para fazer referência à tabela correta.

   Da mesma forma, ao utilizar funções de referência, o modelo de transferência de mensagem inicial padrão deve ser adaptado.

* Não é possível adicionar perfis manualmente em uma lista.

   Portanto, o procedimento detalhado em [this section](../../platform/using/creating-and-managing-lists.md) não é aplicável sem uma configuração adicional.

   >[!NOTE]
   >
   >Você ainda pode criar listas recipient usando workflows. Para obter mais informações, consulte [Criar uma lista de perfil com um fluxo de trabalho](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

Também recomendamos verificar os valores padrão usados nas diferentes configurações predefinidas: em função das funcionalidades utilizadas, devem ser efetuadas várias adaptações.

Por exemplo:

* Determinados relatórios padrão, especialmente aqueles oferecidos por **Interação** e **Aplicativos móveis** devem ser redesenvolvidos. Consulte a seção [Gerenciar relatórios](../../configuration/using/managing-reports.md).
* As configurações padrão para determinadas atividades de fluxo de trabalho fazem referência à tabela de recipient padrão (**[!UICONTROL nms:recipient]**): essas configurações devem ser alteradas quando usadas para uma tabela de recipient externos. Consulte a seção [Gerenciar workflows](../../configuration/using/managing-workflows.md).
* O bloco de personalização padrão **[!UICONTROL Unsubscription link]** deve ser adaptado.
* O target mapping dos templates do delivery padrão deve ser modificado.
* Os formulários V4 não são compatíveis para uso com uma tabela de recipient externos: você deve usar aplicativos da Web.

