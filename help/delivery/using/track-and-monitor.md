---
product: campaign
title: Rastrear e monitorar mensagens
description: Saiba como rastrear e monitorar mensagens
feature: Monitoring
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: ht
source-wordcount: '438'
ht-degree: 100%

---

# Rastrear e monitorar {#track-and-monitor}

![](../../assets/common.svg)

Você clicou no botão **Enviar**? Vamos ver o que acontece. Depois que o delivery é enviado, o Adobe Campaign permite acompanhar as mensagens enviadas e descobrir como os recipients reagem ao seu delivery. Isso o ajudará a melhorar o envio futuro e a otimizar as próximas campanhas.

## Monitorar deliveries {#monitoring-deliveries}

Para controlar suas campanhas, você deve garantir que a mensagem tenha sido entregue aos recipients.

No painel de delivery do Campaign é possível verificar as mensagens processadas e os logs de auditoria do delivery.
Você também pode controlar o status das mensagens nos logs do delivery. [Saiba mais](about-delivery-monitoring.md).

E se os deliveries não estiverem sendo enviados e seu status permanecer **Pendente**?

* O processo de execução está aguardando a disponibilidade de alguns recursos. O MTA pode não ter sido iniciado.
Verifique se os módulos mta@instance estão abertos nos servidores MTA e, caso necessário, inicie o módulo MTA. [Saiba mais](../../production/using/administration.md).

* Pode ser que o delivery esteja usando uma afinidade não configurada no instância de envio.
Dica: verifique a configuração do gerenciamento de tráfego (afinidade IP). Para obter mais informações, consulte Controlar tráfego SMTP de saída.

>[!NOTE]
>
>Essas etapas só podem ser executadas por um usuário especialista.

## Rastrear comportamento {#track-behaviour}

Para conhecer melhor o comportamento dos recipients, você pode acompanhar como eles reagem a uma entrega: recebimento, abertura, cliques em links, assinaturas canceladas etc. No Campaign Classic, essas informações são exibidas na guia Rastreamento dos recipients direcionados pela entrega e na guia Rastreamento da entrega.

**Dica**: o rastreamento de mensagens é habilitado por padrão. Para configurar URLs, selecione a opção Exibir URLs na seção inferior do assistente do delivery. Para cada URL da mensagem, você pode escolher se deseja ativar o rastreamento.

Para obter mais informações, consulte a seção [Configuração de rastreamento](how-to-configure-tracked-links.md) e a descrição dos [Indicadores de rastreamento](../../reporting/using/delivery-reports.md#tracking-indicators).

## Desempenho da entrega {#delivery-performances}

É possível controlar a taxa de transferência do delivery para medir a velocidade de delivery de cada mensagem. Os critérios são o número de mensagens enviadas por hora e o tamanho das mensagens (em bits por segundo). Para obter mais informações, consulte [Taxa de transferência de delivery](../../reporting/using/global-reports.md#delivery-throughput).

**Dicas**:

* Não mantenha os deliveries em estado de falha na instância, pois tabelas temporárias serão mantidas e o desempenho será afetado.

* Remova as remessas que não são mais necessárias e os destinatários inativos do banco de dados para manter a qualidade do endereço.

* Não tente programar deliveries grandes juntos. Observe que pode levar de 5 a 10 minutos para que a carga seja uniformemente espalhada sobre o sistema.

## Solução de problemas de entrega {#delivery-troubleshooting}

Ações específicas podem ser executadas para a resolução de problemas de entregas:

* [Problemas na capacidade de delivery](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemas de exibição de imagem](../../production/using/image-display-issues.md)

* [Problemas de desempenho do delivery](delivery-performances.md)

* [Problemas com arquivos temporários](../../production/using/temporary-files.md) – *somente clientes locais*
