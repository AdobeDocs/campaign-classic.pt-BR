---
product: campaign
title: Desempenho do banco de dados
description: Desempenho do banco de dados
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 8%

---

# Desempenho do banco de dados{#database-performances}



A maioria dos problemas de desempenho está vinculada à manutenção do banco de dados. Estes são quatro leads principais que ajudam a encontrar a causa do desempenho lento:

* Configuração
* Instalação e configuração da plataforma Adobe Campaign
* Manutenção do banco de dados
* Diagnóstico em tempo real

## Configuração {#configuration}

Verifique se a configuração inicial da plataforma Adobe Campaign ainda é válida e, se necessário, reavalie as necessidades do cliente em termos de deliverability ou tamanho do banco de dados. Também recomendamos executar uma verificação completa de hardware (CPU, RAM, sistema de E/S).

>[!NOTE]
>
>Você pode se referir a [Guia de dimensionamento de hardware do Adobe Campaign](https://helpx.adobe.com/br/campaign/kb/hardware-sizing-guide.html) para obter insights.

## Configuração da plataforma {#platform-configuration}

A configuração inadequada pode afetar o desempenho da plataforma. Recomendamos que você verifique a configuração da rede, as opções de capacidade de entrega da plataforma e a configuração de MTA no **serverConf.xml** arquivo.

## Manutenção do banco de dados {#database-maintenance}

**Tarefa de limpeza do banco de dados**

Verifique se a tarefa de limpeza do banco de dados está operacional. Para fazer isso, exiba os arquivos de log para ver se eles contêm erros. Para obter mais informações, consulte [esta seção](../../production/using/database-cleanup-workflow.md).

**Planos de manutenção**

Verifique se a manutenção do banco de dados está agendada e executada corretamente. Para fazer isso, entre em contato com o administrador do banco de dados para saber mais sobre:

* Seu cronograma de manutenção
* Planos de manutenção executados anteriormente
* Visualização dos logs de script

Para obter mais informações, consulte [esta seção](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Se você estiver usando uma configuração mid-sourcing, é essencial que os bancos de dados sejam mantidos regularmente. Ao analisar um delivery na plataforma de marketing, a instância de marketing envia informações para a instância de mid-sourcing. Se o processo for retardado, a instância de marketing será afetada.

**Gerenciamento de tabelas de trabalho**

Verifique o número e o tamanho das tabelas de trabalho. Quando elas excedem um determinado tamanho, o desempenho do banco de dados é afetado. Essas tabelas são criadas por workflows e deliveries. Eles permanecem no banco de dados enquanto os workflows e deliveries estão ativos. Para limitar o tamanho das tabelas de trabalho, você pode realizar as seguintes operações:

* Parar ou excluir deliveries com os seguintes status: **[!UICONTROL Failed]**, **[!UICONTROL In progress]**, **[!UICONTROL Ready for delivery]** ou **[!UICONTROL Paused]**.
* Parar ou excluir workflows que estão pausados devido a um erro.
* Interrompa todos os workflows usados para testes que não contêm um **[!UICONTROL End]** atividade e cujo status assim permanece **[!UICONTROL Paused]**.

>[!IMPORTANT]
>
>Se a operação demorar muito e liberar muito espaço, isso significa que é necessária uma manutenção detalhada (reconstrução de índice, etc.). Para obter mais informações, consulte [esta seção](../../production/using/recommendations.md).

**Monitoramento de processos do Adobe Campaign**

Dependendo das configurações de instalação do Adobe Campaign, duas ferramentas podem ser usadas para monitoramento da plataforma:

* A página de produção da instância. Para obter mais informações, consulte [Monitoramento manual](../../production/using/monitoring-processes.md#manual-monitoring).
* O *netreport* script. Para obter mais informações, consulte [Monitoramento automático por meio de scripts Adobe Campaign](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Especificações {#specifics}

Pode ser necessário executar um diagnóstico em tempo real para identificar a causa do problema. Comece verificando o processo e os arquivos de log da plataforma e monitore a atividade do banco de dados enquanto recria o problema. Preste especial atenção ao seguinte:

* O plano de execução da manutenção
* Consultas SQL sendo executadas
* Se os processos externos estão ou não em execução ao mesmo tempo (limpeza, importações, cálculo agregado, etc.).
