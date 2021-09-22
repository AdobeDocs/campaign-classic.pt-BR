---
product: campaign
title: Utilização de servidores MX com o Campaign
description: Saiba como os servidores MX funcionam com a Adobe Campaign Classic.
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 1%

---

# Utilização de servidores MX com o Campaign {#using-mx-servers}

![](../../assets/v7-only.svg)

Saiba como os servidores MX funcionam com a Adobe Campaign Classic.

## Servidores MX {#mx-servers}

### O que é um servidor MX?

Um registro do permutador de correio (registro MX) é um tipo de registro de recurso no Sistema de Nomes de Domínio (DNS) que especifica um servidor de correio responsável por aceitar mensagens de correio eletrônico em nome de um domínio.

### Como funciona um servidor MX?

Ao enviar um email, o servidor de software estabelece uma conexão com o servidor de domínio do recipient. A comunicação entre os dois servidores usa a linguagem SMTP e um domínio pode ter mais de um servidor MX. A conexão com esse domínio será iniciada a partir da prioridade mais alta (menor figura) e outros servidores serão chamados de servidores de &quot;backup&quot;. O protocolo de conexão deve ser respeitado.

### Como um servidor MX funciona com o Adobe Campaign?

No protocolo de conexão, as regras devem ser respeitadas para evitar o spamming e a monopolização dos servidores. Os mais importantes são os seguintes:

* **Número máximo de conexões permitidas**: Quando esse número é respeitado, os IPs não estão na lista de bloqueios e os emails não são recusados devido a conexões extras.
* **Número máximo de mensagens**: Durante a conexão, o número de mensagens permitidas para serem enviadas deve ser definido. Se esse número não estiver definido, o servidor enviará o máximo possível. Isso resulta na identificação como um spammer e na adição à  lista de bloqueios pelo ISP.
* **Mensagens por hora**: Para corresponder à sua reputação eletrônica, a Adobe Campaign controlará o número de emails que seus IPs podem enviar por hora. Esse sistema protegerá você contra recusa de e-mail ou lista de bloqueios.

## Emails de entrada

### O que é um email de entrada?

É o processo usado pela Adobe Campaign para processar erros durante as comunicações do servidor.

### Como funciona um email de Entrada?

O endereço de erro processará rejeições enviadas de volta pelos ISPs. O processo analisará diferentes códigos de erro SMTP e aplicará a ação correta de acordo com o padrão RegEx.

Por exemplo, um endereço de email tem um feedback &quot;550 Usuário desconhecido&quot; enviado por um ISP. Esse código de erro é processado pelo endereço de erro do Adobe Campaign (endereço returnpath). Esse erro é então comparado ao padrão RegEx e a regra correta será aplicada. O email é considerado um *Hard bounce* (correspondendo ao tipo) e então *User Unknown* (correspondendo ao motivo) e enviado em quarentena após o primeiro loop para o sistema.

### Como a Adobe Campaign a gerencia?

O Adobe Campaign gerencia esse processo com uma correspondência entre um tipo de erro e um motivo:

* **[!UICONTROL User Unknown]**: Endereço que está sintaticamente correto, mas que não existe. Esse erro é categorizado como uma devolução permanente e enviado para a quarentena no primeiro erro.
* **[!UICONTROL Mailbox full]**: Caixa de correio que atingiu a capacidade máxima. Esse erro também pode indicar que o usuário não está mais usando essa caixa de entrada. Esse erro é categorizado como uma devolução temporária e enviado para a quarentena dentro do terceiro erro e removido da quarentena após um período de 30 dias.
* **[!UICONTROL Inactive User]**: A caixa de entrada foi desativada pelo ISP devido a um usuário inativo nos últimos 6 meses. Esse erro é categorizado como uma devolução temporária e enviado para a quarentena dentro do terceiro erro.
* **[!UICONTROL Invalid domain]**: O domínio no endereço de email não existe. Esse erro é categorizado como uma devolução temporária e enviado para a quarentena dentro do terceiro erro.
* **[!UICONTROL Refused]**: O ISP se recusou a entregar o email para seus usuários. Esse erro é categorizado como uma devolução temporária e não é enviado para quarentena, pois o erro não está vinculado ao endereço de email, mas à reputação do IP ou de um domínio.

>[!NOTE]
>
>Para saber mais sobre tipos e motivos de falha de delivery, consulte esta [seção](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## Instância de entregabilidade

Uma atualização diária das regras MX e regras de entrada é gerenciada por um workflow específico na instância do cliente que está conectado ao proprietário da instância de Deliverability dessas regras.

Essa atualização diária está em execução para todos os clientes que desejam manter a instância atualizada por meio de um processo de transparência.

As regras MX têm 6 níveis diferentes de throughput, que são usados principalmente durante o processo de aumento:

![](assets/mx-rules-throughput.png)

O modo Personalizado é para clientes avançados que desejam definir suas próprias regras MX. Quando o modo Personalizado é ativado, o cliente não será atualizado pela instância Deliverability , pois a sincronização será desativada.

## Exemplos de rejeição

* **Usuário desconhecido**  (devolução permanente): 550 5.1.1 ... O usuário é desconhecido {mx003}
* **Caixa de entrada cheia**  (rejeição temporária): 550 5.2.2 Cota de usuário excedida
* **Caixa de entrada inativa**  (rejeição temporária): 550 5.7.1 : Endereço do destinatário rejeitado: Caixa de Correio Inativa, não publicada por mais de 6 meses
* **Domínio inválido**  (devolução temporária): Falha na consulta DNS para &#39;ourdan.com&#39;
* **Recusado**  (devolução temporária): Rejeição do email de entrada (a regra &#39;Feedback_loop_Hotmail&#39; correspondeu a essa rejeição)
* **Inacessível**  (devolução temporária): 421 4.16.55  [TS01] Mensagens de x.x.x.x temporariamente adiadas devido a reclamações excessivas do usuário

**Tópicos relacionados:**
* [Configuração MX](../../installation/using/email-deliverability.md#mx-configuration)
* [Configuração técnica de email](../../installation/using/email-deliverability.md)
* [Compreender as falhas de entrega](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic - Recommendations técnico](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html)
