---
title: Desempenho do banco de dados
seo-title: Desempenho do banco de dados
description: Desempenho do banco de dados
seo-description: null
page-status-flag: never-activated
uuid: 47ff7532-1fe7-47c2-bc3b-0f46d3a4a288
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 6358c8fd-2b75-4462-acd1-887ee44d3110
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# Desempenho do banco de dados{#database-performances}

A maioria dos problemas de desempenho está vinculada à manutenção do banco de dados. Estas são quatro principais indicações para ajudá-lo a encontrar a causa do desempenho lento:

* Configuração,
* Instalação e configuração da plataforma Adobe Campaign,
* Manutenção do banco de dados,
* Diagnóstico em tempo real.

## Configuração {#configuration}

Verifique se a configuração inicial da plataforma do Adobe Campaign ainda é válida e, se necessário, reavalie as necessidades do cliente em termos de entrega ou tamanho do banco de dados. Também recomendamos executar uma verificação completa de hardware (CPU, RAM, sistema de E/S).

>[!NOTE]
>
>Consulte o Guia [de dimensionamento do](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html) Adobe Campaign Harware para obter mais informações.

## Configuração da plataforma {#platform-configuration}

A configuração inadequada pode afetar o desempenho da plataforma. Recomendamos que você verifique a configuração da rede, as opções de fornecimento da plataforma e a configuração MTA no arquivo **serverConf.xml** .

## Manutenção do banco de dados {#database-maintenance}

**Tarefa de limpeza do banco de dados**

Certifique-se de que a tarefa de limpeza da base de dados está operacional. Para fazer isso, visualize os arquivos de registro para ver se eles contêm erros. Para obter mais informações, consulte [esta seção](../../production/using/database-cleanup-workflow.md).

**Planos de manutenção**

Verifique se a manutenção do banco de dados está programada e executada corretamente. Para fazer isso, entre em contato com o administrador do banco de dados para saber mais sobre:

* o seu programa de manutenção,
* planos de manutenção anteriormente executados,
* exibir os registros de scripts.

Para obter mais informações, consulte [esta seção](../../production/using/recommendations.md).

>[!CAUTION]
>
>Se você estiver usando uma configuração de mid-sourcing, é essencial que os bancos de dados sejam mantidos regularmente. Ao analisar uma entrega na plataforma de marketing, a instância de marketing envia informações para a instância de mid-sourcing. Se o processo estiver lento, a instância de marketing será afetada.

**Gerenciamento de tabelas de trabalho**

Verifique o número e o tamanho das tabelas de trabalho. Quando excedem um determinado tamanho, o desempenho do banco de dados é afetado. Essas tabelas são criadas por fluxos de trabalho e entregas. Eles permanecem no banco de dados enquanto os fluxos de trabalho e as entregas estão ativos. Para limitar o tamanho das tabelas de trabalho, é possível realizar as seguintes operações:

* interromper ou excluir entregas com os seguintes status: **[!UICONTROL Failed]** , **[!UICONTROL In progress]** , **[!UICONTROL Ready for delivery]** , ou **[!UICONTROL Paused]** .
* interromper ou excluir fluxos de trabalho que estão pausados devido a um erro,
* interromper todos os fluxos de trabalho usados para testes que não contêm uma **[!UICONTROL End]** atividade e cujo status, portanto, permanece **[!UICONTROL Paused]** .

>[!CAUTION]
>
>Se a operação levar muito tempo e liberar muito espaço, isso significa que é necessária uma manutenção profunda (reconstrução de índice etc.). Para obter mais informações, consulte [esta seção](../../production/using/recommendations.md).

**Monitoramento do processo do Adobe Campaign**

Dependendo das configurações de instalação do Adobe Campaign, duas ferramentas podem ser usadas para o monitoramento da plataforma:

* a página de produção da instância. For more on this, refer to [Manual monitoring](../../production/using/monitoring-processes.md#manual-monitoring).
* o script netreport. Para obter mais informações, consulte Monitoramento [automático por meio de scripts](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)do Adobe Campaign.

## Especificações {#specifics}

Pode ser necessário executar um diagnóstico em tempo real para identificar a causa do problema. Comece verificando o processo e os arquivos de log da plataforma e monitore a atividade do banco de dados ao recriar o problema. Preste especial atenção ao seguinte:

* o plano de execução da manutenção,
* consultas SQL em execução,
* se os processos externos estão ou não em execução ao mesmo tempo (limpeza, importações, cálculo agregado, etc.).

