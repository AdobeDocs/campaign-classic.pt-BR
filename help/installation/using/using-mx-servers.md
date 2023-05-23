---
product: campaign
title: Utilização de servidores MX com o Campaign
description: Saiba como os servidores MX funcionam com o Adobe Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 1%

---

# Utilização de servidores MX com o Campaign {#using-mx-servers}



Saiba como os servidores MX funcionam com o Adobe Campaign Classic.

## Servidores MX {#mx-servers}

### O que é um servidor MX?

Um registro de servidor de email (registro MX) é um tipo de registro de recurso no Sistema de Nomes de Domínio (DNS) que especifica um servidor de email responsável por aceitar mensagens de email em nome de um domínio.

### Como funciona um servidor MX?

Ao enviar um email, o servidor de software estabelecerá uma conexão com o servidor de domínio do recipient. A comunicação entre os dois servidores usa a linguagem SMTP e um domínio pode ter mais de um servidor MX. A conexão com esse domínio começará com a prioridade mais alta (número menor) e outros servidores serão chamados de servidores de &quot;backup&quot;. O protocolo de conexão deve ser respeitado.

### Como um servidor MX funciona com o Adobe Campaign?

No protocolo de conexão, as regras devem ser respeitadas para evitar spam e monopolizar servidores. Os mais importantes são:

* **Número máximo de conexões permitidas**: quando esse número é respeitado, os IPs não estão na inclui na lista de bloqueios e os emails não são recusados devido a conexões adicionais.
* **Número máximo de mensagens**: durante a conexão, o número de mensagens permitidas para serem enviadas deve ser definido. Se esse número não for definido, o servidor enviará o máximo possível. Isso resulta na identificação como um remetente de spam e na adição ao incluo na lista de bloqueios pelo ISP.
* **Mensagens por hora**: para corresponder à sua reputação eletrônica, o Adobe Campaign controlará o número de emails que seus IPs podem enviar por hora. Este sistema irá protegê-lo contra a recusa de e-mail ou/e incluir na lista de bloqueios.

## Emails de entrada

### O que é um email de entrada?

É o processo usado pelo Adobe Campaign para processar erros durante as comunicações do servidor.

### Como funciona um email de entrada?

O endereço de erro processará rejeições enviadas por ISPs. O processo analisará diferentes códigos de erro SMTP e aplicará a ação correta de acordo com o padrão RegEx.

Por exemplo, um endereço de email tem um feedback &quot;550 usuário desconhecido&quot; enviado por um ISP. Esse código de erro é processado pelo endereço de erro do Adobe Campaign (endereço do caminho de retorno). Esse erro é comparado ao padrão RegEx e a regra correta será aplicada. O email é considerado um *Rejeição permanente* (correspondente ao tipo) e, em seguida, *Usuário desconhecido* (correspondendo ao motivo) e colocados em quarentena após o primeiro loop no sistema.

### Como a Adobe Campaign está gerenciando a TI?

O Adobe Campaign gerencia esse processo com uma correspondência entre um tipo de erro e um motivo:

* **[!UICONTROL User Unknown]**: endereço que está sintaticamente correto, mas não existe. Esse erro é categorizado como uma rejeição permanente e colocado em quarentena no primeiro erro.
* **[!UICONTROL Mailbox full]**: Caixa de correio que atingiu a capacidade máxima. Esse erro também pode indicar que o usuário não está mais usando essa caixa de correio. Esse erro é categorizado como uma rejeição temporária e colocado em quarentena no terceiro erro e removido da quarentena após um período de 30 dias.
* **[!UICONTROL Inactive User]**: a caixa de correio foi desativada pelo ISP devido a um usuário inativo nos últimos 6 meses. Esse erro é categorizado como uma rejeição temporária e colocado em quarentena no terceiro erro.
* **[!UICONTROL Invalid domain]**: o domínio no endereço de email não existe. Esse erro é categorizado como uma rejeição temporária e colocado em quarentena no terceiro erro.
* **[!UICONTROL Refused]**: o ISP se recusou a enviar o email aos usuários. Esse erro é categorizado como uma rejeição temporária e não é enviado para quarentena, pois o erro não está vinculado ao endereço de email, mas à reputação de IP ou/ou de um domínio.

>[!NOTE]
>
>Para saber mais sobre os tipos e motivos de falha de delivery, consulte esta [seção](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## Instância de entrega {#deliveratbility-env}

Uma atualização diária das regras MX e das regras de rejeições é gerenciada por um fluxo de trabalho específico na instância do cliente, que está conectada ao proprietário da instância Deliverability dessas regras.

Essa atualização diária está sendo executada para todos os clientes que desejam manter sua instância atualizada por meio de um processo de transparência.

As regras MX têm 6 níveis diferentes de rendimento que são usados principalmente durante o processo de aumento:

![](assets/mx-rules-throughput.png)

O modo Personalizado é para clientes avançados que desejam definir suas próprias regras MX. Quando o modo Personalizado for ativado, o cliente não será atualizado pela instância de Entrega, pois a sincronização será desativada.

## Exemplos de rejeição

* **Usuário desconhecido** (rejeição permanente): 550 5.1.1 ... Usuário desconhecido {mx003}
* **Caixa de entrada cheia** (rejeição temporária): 550 5.2.2 Cota de usuário excedida
* **Caixa de Correio Inativa** (rejeição temporária): 550 5.7.1 : endereço do destinatário rejeitado: Caixa de correio inativa, não lançado por mais de 6 meses
* **Domínio inválido** (rejeição temporária): falha na consulta DNS para &#39;ourdan.com&#39;
* **Recusado** (rejeição temporária): rejeição de email de entrada (a regra &quot;Feedback_loop_Hotmail&quot; correspondeu a essa rejeição)
* **Inacessível** (rejeição temporária): 421 4.16.55 [TS01] Mensagens de x.x.x.x adiadas temporariamente devido a reclamações excessivas do usuário

**Tópicos relacionados:**
* [Configuração MX](../../installation/using/email-deliverability.md#mx-configuration)
* [Configuração técnica de email](../../installation/using/email-deliverability.md)
* [Compreender as falhas de entrega](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic - Recommendations técnico](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html)
