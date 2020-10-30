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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '448'
ht-degree: 100%

---


# Rastrear e monitorar {#track-and-monitor}

Você clicou no botão Enviar? Vamos ver o que acontece. Depois que o delivery é enviado, o Adobe Campaign permite acompanhar as mensagens enviadas e descobrir como os recipients reagem ao seu delivery. Isso o ajudará a melhorar o envio futuro e a otimizar as próximas campanhas.

## Monitoramento de deliveries {#monitoring-deliveries}

Para controlar suas campanhas, você deve garantir que a mensagem tenha sido entregue aos recipients.

No painel de delivery do Campaign é possível verificar as mensagens processadas e os logs de auditoria do delivery.
Você também pode controlar o status das mensagens nos logs do delivery. [Saiba mais](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

E se os deliveries não estiverem sendo enviados e seu status permanecer **Pendente**?

* O processo de execução está aguardando a disponibilidade de alguns recursos. O MTA pode não ter sido iniciado.
Verifique se os módulos mta@instance estão abertos nos servidores MTA e, caso necessário, inicie o módulo MTA. [Saiba mais](../../production/using/administration.md).

* Pode ser que o delivery esteja usando uma afinidade não configurada no instância de envio.
Dica: verifique a configuração do gerenciamento de tráfego (afinidade IP). Para obter mais informações, consulte Controlar tráfego SMTP de saída.

>[!NOTE]
>
>Essas etapas só podem ser executadas por um usuário especialista.

## Rastreamento {#tracking-deliveries}

Para conhecer melhor o comportamento dos recipients, você pode acompanhar como eles reagem a um delivery: recebimento, abertura, cliques em links, assinaturas canceladas, etc. No Campaign Classic, essas informações são exibidas na guia Rastreamento dos recipients direcionados pelo delivery e na guia Rastreamento de delivery. No Campaign Standard, ele é exibido na guia Logs de rastreamento do delivery.

**Dica**: o rastreamento de mensagens é habilitado por padrão. Para configurar URLs, selecione a opção Exibir URLs na seção inferior do assistente do delivery. Para cada URL da mensagem, você pode escolher se deseja ativar o rastreamento.

Para obter mais informações, consulte a seção [Configuração de rastreamento](../../delivery/using/how-to-configure-tracked-links.md) e a descrição dos [Indicadores de rastreamento](../../reporting/using/delivery-reports.md#tracking-indicators).

## Desempenho do delivery {#delivery-performances}

É possível controlar a taxa de transferência do delivery para medir a velocidade de delivery de cada mensagem. Os critérios são o número de mensagens enviadas por hora e o tamanho das mensagens (em bits por segundo). Para obter mais informações, consulte [Taxa de transferência de delivery](../../reporting/using/global-reports.md#delivery-throughput).

**Dicas**:

* Não mantenha os deliveries em estado de falha na instância, pois tabelas temporárias serão mantidas e o desempenho será afetado.

* Remova as remessas que não são mais necessárias e os destinatários inativos do banco de dados para manter a qualidade do endereço.

* Não tente programar deliveries grandes juntos. Observe que pode levar de 5 a 10 minutos para que a carga seja uniformemente espalhada sobre o sistema.

## Solução de problemas de delivery {#delivery-troubleshooting}

Ações específicas podem ser executadas para a resolução de problemas com deliveries:

* [Problemas com delivery](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemas de exibição de imagem](../../production/using/image-display-issues.md)

* [Problemas de desempenho do delivery](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Problemas com arquivos temporários](../../production/using/temporary-files.md) – *somente clientes locais*
