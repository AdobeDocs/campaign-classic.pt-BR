---
title: Definir a audiência correta
seo-title: Definir a audiência correta
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 32%

---


# Definir a audiência correta {#define-the-right-audience}

A população-alvo é fundamental: crie suas listas cuidadosamente, teste seus e-mails em clientes de e-mail populares e dispositivos móveis e verifique se suas listas de e-mail estão atualizadas (sem endereços desconhecidos ou obsoletos). Você também pode enviar provas que ajudam a configurar um ciclo de validação completo.

Saiba mais sobre as populações de públicos alvos [nesta seção](../../delivery/using/steps-defining-the-target-population.md)

## Público alvo da audiência direita {#target-the-right-audience}

Quando seu conteúdo estiver pronto, será necessário definir com cuidado quem receberá sua mensagem.

Para que sua entrega seja bem-sucedida, o conteúdo personalizado mais relevante deve ser enviado aos destinatários corretos. O Adobe Campaign permite criar o destino mais preciso: você pode selecionar os destinatários de acordo com a idade, localização, o que compraram, se clicaram em um link em uma entrega anterior, etc. Com a Adobe Campaign, também é possível definir perfis de teste, grupos de controle e seeds addresses para verificar se o público alvo está correto.

## Target mapping {#target-mappings}

In Campaign Classic, by default, delivery templates target **Recipients**. A Adobe Campaign oferta outros target mapping para seus delivery, que podem ser alterados de acordo com suas necessidades.

Por exemplo, você pode entregar a visitantes cujos perfis tenham sido coletados pelas redes sociais ou a visitantes que estejam inscritos em um serviço de informação.

Esses mapeamentos são apresentados [nesta seção](../../delivery/using/selecting-a-target-mapping.md).

Você também pode criar e usar um target mapping personalizado. Para obter mais informações, consulte [esta seção](../../configuration/using/target-mapping.md).

## Recipient externos {#external-recipients}

Você pode enviar entregas para destinatários armazenados em um arquivo externo em vez de salvos no banco de dados. Learn more [in this section](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

## Enviar para seus assinantes {#send-to-subscribers}

Para enviar mensagens aos assinantes de um boletim informativo, é possível público alvo direto dos assinantes para o serviço de informação correspondente. Learn more [in this section](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Testar recipient e seeds addresses {#test-recipients-seed-addresses}

Para testar seu delivery, use provas antes de enviar para o público alvo principal.

Certifique-se de selecionar recipient de prova apropriados, pois eles validam o formulário e o conteúdo da mensagem. As etapas para definir os recipient de prova são apresentadas [nesta seção](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

Os seed addresses são usados para direcionar destinatários que não correspondem aos critérios de target definidos para testar uma entrega antes de enviar ao target principal. They are presented [in this section](../../delivery/using/about-seed-addresses.md).

## Desduplicar endereços {#deduplicate-addresses}

É importante evitar o uso de endereços de e-mail de duplicado, pois isso pode afetar seu público alvo:

* A mesma mensagem pode ser enviada mais de uma vez quando um público alvo é dividido.

* Se um destinatário cancelar a assinatura após receber uma mensagem, seu perfil duplicado ainda receberá mensagens futuras.

A desduplicação de endereços protege a reputação do seu envio e garante um bom gerenciamento de quarentenas.

Saiba mais [neste caso](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery)de uso.

## Endereços de email do índice {#index-addresses}

Para otimizar o desempenho das consultas SQL usadas no aplicativo, um índice pode ser declarado a partir do elemento principal do esquema de dados.

As etapas para adicionar um índice ao endereço de email são apresentadas [nesta seção](../../configuration/using/database-mapping.md#indexed-fields).
