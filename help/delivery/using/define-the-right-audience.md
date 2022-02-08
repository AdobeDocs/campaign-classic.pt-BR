---
product: campaign
title: Definir o público correto
description: Saiba mais sobre as práticas recomendadas ao selecionar seu público-alvo
feature: Audiences
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 98%

---

# Definir o público correto {#define-the-right-audience}

![](../../assets/common.svg)

A segmentação de público-alvo é fundamental: crie suas listas cuidadosamente, teste seus emails em clientes de email populares e dispositivos móveis e verifique se suas listas de email estão atualizadas (sem endereços desconhecidos ou obsoletos). Você também pode enviar provas que ajudam a configurar um ciclo de validação completo.

Saiba mais sobre as populações de públicos-alvos [nesta seção](steps-defining-the-target-population.md)

## Direcionar ao público-alvo correto {#target-the-right-audience}

Quando seu conteúdo estiver pronto, será necessário definir com cuidado quem receberá sua mensagem.

Para que seu delivery seja bem-sucedido, o conteúdo personalizado mais relevante deve ser enviado aos recipients corretos. O Adobe Campaign permite criar o público mais preciso: você pode selecionar os recipients de acordo com a idade, localização, o que compraram, se clicaram em um link em um delivery anterior, etc. Com o Adobe Campaign, também é possível definir perfis de teste, grupos de controle e endereços de seed para verificar se o público-alvo está correto.

## Direcionar mapeamentos {#target-mappings}

Por padrão, os modelos de delivery no Campaign Classic direcionam os **Recipients**. O Adobe Campaign oferece outros target mappings para seus deliveries, que podem ser modificados conforme suas necessidades.

Você pode, por exemplo, entregar deliveries a visitantes cujos perfis tenham sido coletados nas redes sociais, ou a visitantes que estejam inscritos em um serviço de informação.

Esses mapeamentos são apresentados [nesta seção](selecting-a-target-mapping.md).

Você também pode criar e usar um target mapping personalizado. Para obter mais informações, consulte [esta seção](../../configuration/using/target-mapping.md).

## Recipients externos {#external-recipients}

Você pode enviar deliveries para destinatários armazenados em um arquivo externo em vez de salvos no banco de dados. Saiba mais [nesta seção](steps-defining-the-target-population.md#selecting-external-recipients).

## Enviar para os assinantes {#send-to-subscribers}

Para enviar mensagens aos assinantes de um informativo, é possível direcionar diretamente os assinantes para o serviço de informação correspondente. Saiba mais [nesta seção](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Testar recipients e seed addresses {#test-recipients-seed-addresses}

Para testar seu delivery, use provas antes de enviar para o público-alvo principal.

Selecione os recipients de prova apropriados, porque eles validam a forma e o conteúdo da mensagem. As etapas para definir os recipients de prova são apresentadas [nesta seção](steps-defining-the-target-population.md#selecting-the-proof-target).

Os seed addresses são usados para direcionar recipients que não correspondem aos critérios de direcionamento definidos para testar um delivery antes de enviar ao público-alvo principal. Eles são apresentados [nesta seção](about-seed-addresses.md).

## Cancelar endereços duplicados {#deduplicate-addresses}

É importante evitar emails duplicados, pois eles podem afetar seu público-alvo:

* A mesma mensagem pode ser enviada mais de uma vez quando um público-alvo é dividido.

* Se um destinatário cancelar a assinatura após receber uma mensagem, seu perfil duplicado ainda receberá mensagens futuras.

O cancelamento da duplicação de endereços protege a reputação de envio e garante um bom gerenciamento de quarentena.

**Tópicos relacionados:**

* [Atividade de desduplicação](../../workflow/using/deduplication.md).
* [Caso de uso: uso da funcionalidade de mesclagem de atividades de desduplicação](../../workflow/using/deduplication-merge.md)

## Indexar endereços de email {#index-addresses}

Para otimizar o desempenho das consultas SQL usadas no aplicativo, um índice pode ser declarado a partir do elemento principal do esquema de dados.

As etapas para adicionar um índice ao endereço de email são apresentadas [nesta seção](../../configuration/using/database-mapping.md#indexed-fields).
