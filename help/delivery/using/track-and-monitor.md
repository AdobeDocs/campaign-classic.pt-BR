---
product: campaign
title: Rastrear e monitorar mensagens
description: Saiba como rastrear e monitorar mensagens
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Monitoring, Reporting
role: User
hide: true
hidefromtoc: true
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: ht
source-wordcount: '449'
ht-degree: 100%

---

# Rastrear e monitorar {#track-and-monitor}

Você clicou no botão **Enviar**? Vamos ver o que acontece. Depois que a entrega é enviada, o Adobe Campaign permite acompanhar as mensagens enviadas e descobrir como os destinatários reagem a sua entrega. Isso o ajudará a melhorar o envio futuro e a otimizar as próximas campanhas.

## Monitorar entregas {#monitoring-deliveries}

Para controlar suas campanhas, você deve garantir que a mensagem tenha sido entregue aos destinatários.

No painel de entrega do Campaign é possível verificar as mensagens processadas e os logs de auditoria da entrega.
Você também pode controlar o status das mensagens nos logs da entrega. [Saiba mais](about-delivery-monitoring.md).

E se as entregas não estiverem sendo enviadas e seu status permanecer **Pendente**?

* O processo de execução está aguardando a disponibilidade de alguns recursos. O MTA pode não ter sido iniciado.
Verifique se os módulos mta@instance estão abertos nos servidores MTA e, caso necessário, inicie o módulo MTA. [Saiba mais](../../production/using/administration.md).

* Pode ser que a entrega esteja usando uma afinidade não configurada na instância de envio.
Dica: verifique a configuração do gerenciamento de tráfego (afinidade IP). Para obter mais informações, consulte Controlar tráfego SMTP de saída.

>[!NOTE]
>
>Essas etapas só podem ser executadas por um usuário especialista.

## Rastrear comportamento {#track-behaviour}

Para conhecer melhor o comportamento dos destinatários, você pode acompanhar como eles reagem a uma entrega: recebimento, abertura, cliques em links, assinaturas canceladas etc. No Campaign Classic, essas informações são exibidas na guia Rastreamento dos destinatários direcionados pela entrega e na guia Rastreamento da entrega.

**Dica**: o rastreamento de mensagens é habilitado por padrão. Para configurar URLs, selecione a opção “Exibir URLs” na seção inferior do assistente de entrega. Para cada URL da mensagem, você pode escolher se deseja ativar o rastreamento.

Para obter mais informações, consulte a seção [Configuração de rastreamento](how-to-configure-tracked-links.md) e a descrição dos [Indicadores de rastreamento](../../reporting/using/delivery-reports.md#tracking-indicators).

## Desempenho da entrega {#delivery-performances}

É possível controlar a taxa de transferência da entrega para medir a velocidade de entrega de cada mensagem. Os critérios são o número de mensagens enviadas por hora e o tamanho das mensagens (em bits por segundo). Para obter mais informações, consulte [Taxa de transferência de entrega](../../reporting/using/global-reports.md#delivery-throughput).

**Dicas**:

* Não mantenha as entregas em estado de falha na instância, pois tabelas temporárias serão mantidas e o desempenho será afetado.

* Remova as remessas que não são mais necessárias e os destinatários inativos do banco de dados para manter a qualidade do endereço.

* Não tente programar entregas grandes juntas. Observe que pode levar de 5 a 10 minutos para que a carga seja uniformemente espalhada sobre o sistema.

## Solução de problemas de entrega {#delivery-troubleshooting}

Ações específicas podem ser executadas para a resolução de problemas de entregas:

* [Problemas na capacidade de entrega](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemas de exibição de imagem](../../production/using/image-display-issues.md)

* [Problemas de desempenho da entrega](delivery-performances.md)

* [Problemas com arquivos temporários](../../production/using/temporary-files.md) – *somente clientes locais*
