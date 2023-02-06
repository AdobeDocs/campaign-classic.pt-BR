---
product: campaign
title: Atualizar qualificação de devolução após interrupção do Italia Online
description: Saiba como atualizar a qualificação de devolução após a interrupção do Italia Online
feature: Deliverability
hide: true
hidefromtow: true
source-git-commit: 3cf6ffb2b69d44b56615492dd9db8965ae3cf4e1
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 26%

---

# Atualize as devoluções incorretas após a interrupção do Italia Online {#update-bounce-italia}

![](../../assets/common.svg)

## Contexto{#outage-context}

Desde 22 de janeiro (horário local), o Italia Online passou por uma interrupção que resultou em vários atrasos e rejeitou emails. O serviço começou a retomar com capacidade limitada em 26 de janeiro.

Os domínios afetados são: **libero.it**, **virgilio.it**, **inwind.it**, **iol.it** e **blu.it**.

Esse problema ocorreu de 22/01/2023 a 26/01/2023, mas a maioria das quarentenas equivocadas aconteceu em 26 de janeiro.

Saiba mais na comunicação oficial [here](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Impacto{#outage-impact}

No caso de uma interrupção de um ISP, os emails enviados por meio do Campaign não podem ser entregues com êxito ao recipient: esses emails serão marcados incorretamente como rejeições. Isso não está afetando apenas o Adobe, mas todos tentando enviar emails para o Italia Online.

Os sintomas são:

* **Devoluções diferenciais** com a mensagem `452 requested action aborted: try again later` são observadas - são repetidas automaticamente e nenhuma ação é necessária. Eles devem melhorar à medida que o ISP recupera a capacidade total.

* **Devoluções permanentes** com a mensagem `550 <email address> recipient rejected` foram retornados pelo ISP em 26 de janeiro, entre 8h e 14h horário local, para evitar que os remetentes continuem sobrecarregando seus servidores. Como confirmado pelo Italia Online Postmaster, essas não são devoluções reais, então recomendamos cancelar a quarentena de todos os endereços de email que foram excluídos em 26 de janeiro de 2023 devido a essa mensagem.

## Processo para atualização{#outage-update}

De acordo com a lógica padrão de manipulação de rejeição, o Adobe Campaign adicionou automaticamente esses recipients à lista de quarentena com uma configuração **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corrigir isso, você precisa atualizar a tabela de quarentena no Campaign localizando e removendo esses recipients ou alterando seus **[!UICONTROL Status]** para **[!UICONTROL Valid]** para que o fluxo de trabalho de limpeza noturna os remova.

Para encontrar os recipients que foram afetados por esse problema, ou caso isso aconteça novamente com qualquer outro ISP, consulte as instruções [nesta página](../../delivery/using/understanding-quarantine-management.md#unquarantine-bulk).
