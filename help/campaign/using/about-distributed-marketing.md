---
title: Sobre marketing distribuído
seo-title: Sobre marketing distribuído
description: Sobre marketing distribuído
seo-description: null
page-status-flag: never-activated
uuid: 7f7ece67-c644-4072-a06c-c5b49f3acb5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 6d694f5c-1d1f-4686-b3bf-8697d919a0c8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Sobre marketing distribuído{#about-distributed-marketing}

## Introdução {#introduction}

O Adobe Campaign oferece um aplicativo de **Marketing distribuído** para implementar campanhas cooperativas entre entidades centrais (sede, departamentos de marketing etc.) e entidades locais (pontos de vendas, agências regionais etc.). This cooperation is based on a shared workspace known as the **[!UICONTROL list of campaign packages]**, where centrally created campaign templates and instances are offered to local entities.

A entidade central fornece campanhas que entidades locais poderão usar. As campanhas são materializadas por pacotes que representam campanhas locais ou colaborativas. Para usar uma campanha, a entidade local deverá fazer solicitá-la e a solicitação deverá ser aprovada.

>[!CAUTION]
>
>O módulo de Marketing distribuído é uma opção de **Campanha** . Verifique o contrato de licença.

## Terminologia {#terminology}

### Entidades centrais {#central-entities}

As entidades centrais são compostas por operadores de marketing responsáveis por especificar comunicações e ajudar entidades locais a executar sua campanha de marketing.

O módulo de marketing distribuído permite à entidade central:

* configurar pacotes de campanha de marketing para entidades locais,
* aumentar o grau de autonomia das entidades locais em relação à sua escolha para comunicação com cliente/prospecto, direcionamento, conteúdo etc.
* gerenciar e controlar custos,
* lidar com uma rede de agências.

### Entidades locais {#local-entities}

As entidades locais podem ser agências, lojas ou grupos de operadores locais específicos (gerentes regionais ou de país, gerentes de marca etc.).

O Marketing distribuído permite que entidades locais tenham mais autonomia, enquanto otimizam os custos de execução.

### Localização {#localization}

Localização é a capacidade de uma entidade local modificar o target e o conteúdo de uma campanha. O nível possível de localização depende do tipo de campanha e sua implementação.

### Lista de pacotes de campanha {#list-of-campaign-packages}

A lista de pacotes de campanha contém as campanhas disponíveis para entidades locais.

### Pacote de campanha {#campaign-package}

Template (ou instância de campanha) criado por uma entidade central e disponibilizado para um conjunto de entidades locais.

### Campanha local {#local-campaign}

A local campaign is an instance created from a template referenced in the list of **[!UICONTROL campaign packages]** with a **specific execution schedule**. Seu objetivo é atender a uma comunicação local usando um template de campanha que foi criado e configurado pela entidade central.

O grau de autonomia da entidade local depende da implementação usada.

Consulte [Criação de uma campanha](../../campaign/using/creating-a-local-campaign.md)local.

### Campanha colaborativa {#collaborative-campaign}

Uma campanha colaborativa é uma campanha cujo **cronograma de execução é definido** pela entidade central, que a entidade local pode usar. O conteúdo permanece o mesmo para cada entidade local, mas os custos são compartilhados. Para participarem, as entidades locais se inscrevem na campanha colaborativa.

* **[!UICONTROL Collaborative campaign (by form)]**: recomendado para campanhas envolvendo até 300 entidades locais. A entidade local pode inserir parâmetros predefinidos para definição de alvos e personalização de conteúdo em um formulário da Web. O formulário pode ser um formulário do Adobe Campaign ou um formulário externo (cliente extranet). Um administrador funcional pode definir e configurar o formulário com base em um template de formulário definido pelo integrador. Para solicitar a campanha, a entidade local precisa apenas de acesso à Web.
* **[!UICONTROL Collaborative campaign (by campaign)]**: recomendado para campanhas destinadas a dezenas de entidades locais. Esse tipo de campanha cria campanhas filho para cada entidade local. Once the **[!UICONTROL collaborative campaign (by campaign)]** is approved by the central entity, the campaign is made available to the local entity, who can modify it. A execução é automaticamente sincronizada entre campanhas pai e filho. A entidade local deve ter acesso a uma instância para solicitar uma campanha e participar dela.
* **[!UICONTROL Collaborative campaign (by target approval)]**: recomendado para campanhas direcionadas a milhares de entidades locais. A entidade local recebe uma lista de contatos que foi predefinida pela entidade central. A entidade local decide se mantém determinados contatos com base no conteúdo da campanha, por meio de um formulário da Web. As entidades locais são selecionadas da lista de contatos selecionados. Para participar da campanha, a entidade local só precisa de acesso à Web.
* **[!UICONTROL Collaborative campaign (simple)]**: esse modo garante a compatibilidade com os processos de execução específicos das versões anteriores.

Consulte [Criação de uma campanha](../../campaign/using/creating-a-collaborative-campaign.md)colaborativa.

### Solicitar pacotes de campanha {#ordering-campaign-packages}

Se uma entidade local se registra em uma campanha, isso é transformado em um pedido que reagrupa todas as informações relativas à localização da campanha.

## Área de Trabalho {#workspace}

The list of campaign packages can be accessed from the **Campaigns** universe: click the **[!UICONTROL Campaign packages]** link.

![](assets/mkg_dist_home_local_op.png)

Essa janela permite que todos os operadores visualizem as campanhas disponíveis para sua agência local.

No caso de agências centrais, essa janela exibe todos os pacotes disponíveis na lista de pacotes de campanha e oferece links adicionais para edição da lista.

## Operadores e entidades {#operators-and-entities}

Start by specifying the central and local entity operators via the **[!UICONTROL Access management]** folder.

![](assets/s_advuser_mkg_dist_tree.png)

### Operadores {#operators}

É preciso criar operadores centrais e locais.

Central operators must belong to the **[!UICONTROL Central management]** operator group or have the **[!UICONTROL CENTRAL]** named right.

Local operators must belong to the **[!UICONTROL Local management]** operator group or have the **[!UICONTROL LOCAL]** named right. Eles também devem estar vinculados à sua entidade local.

![](assets/s_advuser_mkg_dist_local_create.png)

### Entidades organizacionais {#organizational-entities}

To create an organizational entity, click the **[!UICONTROL Administration > Access management > Organizational entities]** node and click the **[!UICONTROL New]** icon above the list of entities.

![](assets/s_advuser_mkg_dist_local_list.png)

Cada entidade organizacional contém informações de identificação (etiqueta, nome interno, informações de contato etc.) e grupos envolvidos no processo de aprovação de pedidos. Elas são definidas na **[!UICONTROL Notifications and approvals]** seção encontrada na **[!UICONTROL General]** guia.

* Definir um grupo de notificação de pacote: operadores neste grupo receberão uma notificação sempre que um novo pacote for adicionado à lista de pacites de campanha e cada vez que uma campanha estiver disponível.
* Selecione o grupo de revisores responsáveis pela aprovação de pedidos, ou seja, aqueles responsáveis pela aprovação de campanhas solicitadas pela entidade local.
* Finalmente, selecione o grupo de revisores responsáveis pela aprovação da campanha local (target, conteúdo, orçamento etc.). Esse grupo pode ser adicionado ao solicitar uma campanha, dependendo do template.

>[!NOTE]
>
>The approval process is presented in the [Approval process](../../campaign/using/creating-a-local-campaign.md#approval-process) section.

## Implementação {#implementation}

As campanhas de Marketing Distribuído são criadas e publicadas pela entidade central. Eles podem ser usados por entidades locais e centrais conforme necessário.

O procedimento de implementação depende do tipo de pacote de campanha usado e dos níveis de delegação da entidade local.

### Lado do integrador {#integrator-side}

1. Criar entidades locais.
1. Vincule recipients com os operadores que gerenciam entidades locais.

   ![](assets/mkg_dist_local_entity_association.png)

1. Especificar direitos e regras de navegação para entidades locais
1. Especifique o conjunto de campos necessários para a localização da campanha:

   * definição de target e tamanho máximo,
   * definição de conteúdo,
   * cronograma de execução (data de contato e data de extração), **somente para operadores locais**,
   * extensão do schema do pedido com todos os campos adicionais necessários.

1. Crie um formulário Web (Adobe ou extranet) que permita exibir parâmetros de localização, avalie o alvo e o orçamento, bem como pré-visualize o conteúdo e aprove o pedido.

   Para **collaborative campaigns (by target approval)**, crie a tabela onde as aprovações de cada entidade local serão salvas.

### Lado do administrador funcional {#functional-administrator-side}

Essas etapas devem ser executadas ao criar cada campanha.

1. Atualize o formulário com os campos usados para localização da campanha.
1. Crie uma instância de um template de campanha apropriado (campanha colaborativa) ou duplique o template de campanha (campanha local).
1. Configure a campanha com os campos de localização e a referência de formulário.
1. Publique a campanha.

### Lado do operador local {#local-operator-side}

Essas etapas devem ser executadas para cada campanha.

1. Após receber a notificação da disponibilidade do pacote de campanha, especifique o local da campanha (opcional).
1. Avalie o target, o orçamento, etc.
1. Pré-visualize o conteúdo da campanha.
1. Solicite a campanha.

