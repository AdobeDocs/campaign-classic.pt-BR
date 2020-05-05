---
title: Pontos principais ao gerenciar a capacidade de delivery no Adobe Campaign Classic
description: Quais são os principais pontos a serem verificados ao gerenciar a capacidade de delivery no Adobe Campaign Classic?
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# Principais pontos da capacidade de delivery{#deliverability-key-points}

A capacidade de delivery consiste em medir o sucesso das campanhas em chegar à caixa de entrada dos recipients sem rejeição ou sem serem marcadas como spam.

Para otimizar a capacidade de delivery de emails do Adobe Campaign, recomendamos o uso das práticas recomendadas listadas abaixo. Os problemas de capacidade de delivery estão geralmente ligados às medidas de proteção contra spam implementadas pelos provedores de serviços de Internet e administradores de servidores de correio.

A capacidade de fornecimento de email refere-se ao conjunto de características que determinam a capacidade de uma mensagem de alcançar seu destino por meio de um endereço de email pessoal, dentro de um curto período e com a qualidade esperada em termos de conteúdo e formato.

Essas características dividem-se em quatro categorias principais:
* Qualidade dos dados
* Mensagem e conteúdo
* Infraestrutura de envio
* Reputação

Juntos, elas formam a base de um programa bem-sucedido de capacidade de fornecimento de email.

A taxa de delivery é o número de emails enviados que foram entregues com êxito aos recipients.

A taxa de delivery depende de vários fatores, especialmente:
* A configuração correta das instâncias
* A reputação do endereço IP
* A qualidade dos endereços de destino
* Baixas taxas de reclamação e rejeição
* O conteúdo da mensagem
* Autenticação da mensagem (SPF, DKIM, DMARC)
* Reputação do remetente

Esta é uma lista dos pontos principais a serem verificados para garantir um bom delivery.

## Verificar a configuração da rede {#network-configuration}

Os remetentes de spam tentam ocultar a verdadeira identidade e, assim, dificultam a identificação dos servidores. Uma configuração de rede legítima que não tente ocultar a identidade do servidor é essencial para enviar emails em grandes volumes.

## Enviar para endereços válidos {#valid-addresses}

Os remetentes de spam utilizam frequentemente geradores de endereços baseados em listas de nomes frequentes e nomes próprios; além disso, raramente processam notificações técnicas enviadas de volta pelos servidores de email. Muitas vezes, uma alta taxa de endereços inválidos é interpretada como um sinal de spam. Os mecanismos de aceitação dupla e o tratamento eficaz das mensagens técnicas de rejeição permitem evitar esta situação.

## Reduzir as taxas de reclamação e rejeição {#reduce-complaint-rates}

Geralmente, os provedores de internet têm um meio proeminente de reportar uma mensagem recebida como spam. Isso permite identificar fontes não confiáveis. Ao atender rapidamente às solicitações de recusa, fazer uso regular de uma determinada lista, verificar o consentimento por meio de um sistema de aceitação dupla e implementar loops de feedback, você pode reduzir as taxas de reclamação.

## Enviar para endereços honeypot {#honeypot-addresses}

Os provedores de acesso e outras organizações (consulte http://www.projecthoneypot.org/) usam caixas de correio que não correspondem às pessoas físicas, mas são criadas apenas para enganar spammers. Esses endereços, chamados de &quot;honey pot&quot;, são publicados na Web para serem recolhidos por spambots e, assim, capturar remetentes ilegítimos. O uso de um mecanismo de aceitação dupla impede que esse tipo de endereço seja adicionado a uma lista. Ao usar uma lista de terceiros, é necessário ter certeza dos métodos empregados pelo responsável principal.

## Adaptar o conteúdo da mensagem {#message-content}

Em menor grau, o conteúdo de determinadas mensagens pode levar a que determinados filtros as detectem como spam. A utilização de determinadas palavras e o uso de pontos de exclamação na linha de assunto e nas mensagens são interpretados como sinais reveladores de spam. Os remetentes de spam também são conhecidos por substituir o texto por imagens para impedir que o texto ofensivo seja analisado automaticamente por filtros anti-spam. Em resposta a isso, uma mensagem (em formato HTML) com uma alta proporção de imagens, ou imagens como anexos, pode acabar sendo bloqueada.

## Trabalhe sua reputação {#reputation}

Os remetentes de spam fazem deliveries programados para manter a reputação ao longo do tempo. Por vezes, eles precisam adaptar o plano de marketing para cumprir as melhores práticas impostas pelos ISPs e, por isso, após um pico de reputação (aumento), configuram deliveries regulares.