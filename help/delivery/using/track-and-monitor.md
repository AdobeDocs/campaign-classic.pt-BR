---
title: Rastrear e monitorar mensagens
seo-title: Rastrear e monitorar mensagens
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
source-wordcount: '448'
ht-degree: 28%

---


# Rastrear e monitorar {#track-and-monitor}

Você clicou no botão Enviar? Vamos ver o que acontece. Depois que a entrega é enviada, o Adobe Campaign permite que você acompanhe as mensagens enviadas e descubra como seus destinatários reagem à sua entrega. Isso o ajudará a melhorar o envio futuro e a otimizar suas próximas campanhas.

## Monitoramento de deliveries {#monitoring-deliveries}

Para controlar suas campanhas, você deve garantir que a mensagem tenha sido entregue aos seus destinatários.

No painel do delivery da Campanha, você pode verificar as mensagens processadas e os registros de auditoria do delivery.
Você também pode controlar o status das mensagens nos logs do delivery. [Saiba mais](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

E se os delivery não estiverem sendo enviados e seu status permanecer **Pendente**?

* O processo de execução está aguardando a disponibilidade de alguns recursos. O MTA pode não ter sido iniciado.
Verifique se os seus mta@instanceétodos estão abertos nos servidores MTA e start o módulo MTA, se necessário. [Saiba mais](../../production/using/administration.md).

* O delivery pode estar usando uma afinidade que não foi configurada na instância de envio.
Dica: Verifique a configuração do gerenciamento de tráfego (afinidade IP). Para obter mais informações, consulte Controlar tráfego SMTP de saída.

>[!NOTE]
>
>Essas etapas só podem ser executadas por um usuário especialista.

## Rastreamento {#tracking-deliveries}

Para conhecer melhor o comportamento de seus destinatários, você pode acompanhar como eles reagem a uma entrega: recebimento, abertura, cliques em links, assinaturas canceladas, etc. No Campaign Classic, essas informações são exibidas na guia Rastreamento dos recipient direcionados pelo delivery e na guia Rastreamento do delivery. No Campaign Standard, ele é exibido na guia Logs de rastreamento do delivery.

**Dica**: O rastreamento de mensagens está ativado por padrão. Para configurar URLs, selecione a opção Exibir URLs na seção inferior do assistente do delivery. Para cada URL da mensagem, você pode escolher se deseja ativar o rastreamento.

Para obter mais informações, consulte a seção [Configuração de rastreamento](../../delivery/using/how-to-configure-tracked-links.md) e a descrição dos indicadores [de](../../reporting/using/delivery-reports.md#tracking-indicators) rastreamento.

## Desempenho do delivery {#delivery-performances}

Para medir a velocidade de entrega das mensagens, é possível controlar a taxa de transferência do delivery. Os critérios são o número de mensagens enviadas por hora e o tamanho das mensagens (em bits por segundo). For more on this, see [Delivery throughput](../../reporting/using/global-reports.md#delivery-throughput).

**Dicas**:

* Não mantenha as entregas em estado de falha na instância, pois isso mantém tabelas temporárias e afeta o desempenho.

* Remova as remessas que não são mais necessárias e os destinatários inativos do banco de dados para manter a qualidade do endereço.

* Não tente programar entregas grandes em conjunto. Observe que pode levar de 5 a 10 minutos para espalhar a carga uniformemente sobre o sistema.

## solução de problemas do delivery {#delivery-troubleshooting}

Ações específicas podem ser executadas ao encontrar problemas com delivery:

* [Problemas de produtividade](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemas de exibição de imagem](../../production/using/image-display-issues.md)

* [Problemas de desempenho do delivery](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Problemas](../../production/using/temporary-files.md) de arquivos temporários - somente clientes *locais*
