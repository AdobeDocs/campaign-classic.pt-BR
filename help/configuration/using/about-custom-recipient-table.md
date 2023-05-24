---
product: campaign
title: Sobre tabela de recipient personalizada
description: Sobre tabela de recipient personalizada
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Custom Resources
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 2%

---

# Usar tabela de recipient personalizada{#about-custom-recipient-table}



Esta seção detalha os princípios para usar uma tabela de recipient personalizada (ou externa).

Por padrão, o Adobe Campaign oferece uma tabela de recipients integrada à qual funções e processos prontos para uso são vinculados. A tabela de recipients integrada tem vários campos e tabelas predefinidos que podem ser facilmente estendidos usando uma tabela de extensão.

Se esse método de extensão oferecer boa flexibilidade para estender uma tabela, ele não permitirá a redução do número de campos ou links nela. O uso de uma tabela não padrão, ou &quot;tabela de recipient externa&quot;, permite uma maior flexibilidade, mas requer determinadas precauções ao implementá-la.

Essa funcionalidade permite que o Adobe Campaign processe dados de um banco de dados externo: esses dados serão usados como um conjunto de perfis para deliveries. A implementação desse processo envolve várias precisões que podem ser relevantes de acordo com as necessidades do cliente. Tais como:

* Nenhum fluxo de atualização de e para o banco de dados do Adobe Campaign: os dados dessa tabela podem ser atualizados diretamente pelo mecanismo de banco de dados que os hospeda.
* Nenhuma alteração nos processos que estão operando no banco de dados existente.
* Uso de um banco de dados de perfil com uma estrutura não padrão: possibilidade de entrega para perfis salvos em várias tabelas com várias estruturas, usando uma única instância.
* Não são necessárias alterações ou manutenção ao atualizar o banco de dados do Adobe Campaign.
* A tabela de recipients integrada é inútil se você não precisar da maioria dos campos da tabela ou se o template do banco de dados não estiver centralizado nos recipients.
* Para ser eficiente, se você tiver um número significativo de perfis, será necessária uma tabela com poucos campos. A tabela de destinatários interna tem muitos campos para este caso específico.

Esta seção descreve os pontos principais que permitem mapear tabelas existentes no Adobe Campaign e a configuração a ser aplicada para executar deliveries com base em qualquer tabela. Por fim, descreve como fornecer aos usuários interfaces de consulta tão práticas quanto aquelas disponíveis com a tabela de recipient integrada. Para entender o material apresentado nesta seção, é necessário um bom conhecimento dos princípios de design de tela e esquema.

## Recommendations e limitações {#recommendations-and-limitations}

O uso de uma tabela de recipient personalizada tem as seguintes limitações:

* O Adobe Campaign não é compatível com vários esquemas de recipient, conhecidos como esquemas de direcionamento, vinculados aos mesmos esquemas de broadlog e/ou trackinglog. Caso contrário, isso pode levar a anomalias na reconciliação de dados posteriormente.

   O gráfico abaixo detalha a estrutura relacional necessária para cada esquema de recipient personalizado:
   ![](assets/custom_recipient_limitation.png)

   Recomendamos:

   * Dedicar a **[!UICONTROL nms:BroadLogRcp]** e **[!UICONTROL nms:TrackingLogRcp]** esquemas para uso imediato **[!UICONTROL nms:Recipientschema]**. Essas duas tabelas de log não devem estar vinculadas a nenhuma tabela de recipient personalizada adicional.
   * Definição de esquemas broadlog e trackinglog personalizados dedicados para cada novo esquema de recipient personalizado. Isso pode ser feito automaticamente ao configurar o target mapping, consulte [Target mapping](../../configuration/using/target-mapping.md).

* Não é possível usar o padrão **[!UICONTROL Services and Subscriptions]** oferecida no produto.

   Isso significa a operação geral detalhada em [nesta seção](../../delivery/using/managing-subscriptions.md) não é aplicável.

* O link com o **[!UICONTROL visitor]** não funciona.

   Assim, para utilizar o **[!UICONTROL Social Marketing]** módulo, você deve configurar a etapa de armazenamento para fazer referência à tabela correta.

   Da mesma forma, ao usar funções de referência, o template de transferência de mensagem inicial padrão deve ser adaptado.

* Não é possível adicionar perfis manualmente em uma lista.

   Por conseguinte, o procedimento [nesta seção](../../platform/using/creating-and-managing-lists.md) não é aplicável sem uma configuração adicional.

   >[!NOTE]
   >
   >Você ainda pode criar listas de recipients usando workflows. Para obter mais informações, consulte [Criação de uma lista de perfis com base em um fluxo de trabalho](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

Também recomendamos verificar os valores padrão usados nas diferentes configurações prontas para uso: dependendo das funcionalidades usadas, várias adaptações devem ser realizadas.

Por exemplo:

* Certos relatórios-tipo, em especial os **Interação** e a variável **Aplicativos móveis** deve ser redesenvolvida. Consulte a [Gerenciamento de relatórios](../../configuration/using/managing-reports.md) seção.
* As configurações padrão para determinadas atividades de workflow fazem referência à tabela de recipients padrão (**[!UICONTROL nms:recipient]**): essas configurações devem ser alteradas quando usadas para uma tabela externa de recipients. Consulte a [Gerenciamento de workflows](../../configuration/using/managing-workflows.md) seção.
* O padrão **[!UICONTROL Unsubscription link]** o bloco de personalização deve ser adaptado.
* O target mapping dos templates do delivery padrão deve ser modificado.
* Os formulários V4 não são compatíveis para uso com uma tabela externa de recipients: você deve usar aplicações web.
