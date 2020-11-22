---
solution: Campaign Classic
product: campaign
title: Desempenho do banco de dados
description: Desempenho do banco de dados
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 8%

---


# Desempenho do banco de dados{#database-performances}

A maioria dos problemas de desempenho está vinculada à manutenção do banco de dados. Estas são quatro principais indicações para ajudá-lo a encontrar a causa do desempenho lento:

* Configuração,
* Instalação e configuração da plataforma Adobe Campaign,
* Manutenção do banco de dados,
* Diagnóstico em tempo real.

## Configuração {#configuration}

Verifique se a configuração inicial da plataforma Adobe Campaign ainda é válida e, se necessário, reavalie as necessidades do cliente em termos de entrega ou tamanho do banco de dados. Também recomendamos executar uma verificação completa de hardware (CPU, RAM, sistema de E/S).

>[!NOTE]
>
>Consulte o Guia [de dimensionamento do](https://helpx.adobe.com/br/campaign/kb/hardware-sizing-guide.html) Adobe Campaign Harware para obter mais informações.

## Configuração da plataforma {#platform-configuration}

A configuração inadequada pode afetar o desempenho da plataforma. Recomendamos que você verifique a configuração da rede, as opções de fornecimento da plataforma e a configuração MTA no arquivo **serverConf.xml** .

## Manutenção do banco de dados {#database-maintenance}

**Tarefa de limpeza do banco de dados**

Verifique se a tarefa de limpeza do banco de dados está operacional. Para fazer isso, visualização os arquivos de registro para ver se eles contêm erros. Para obter mais informações, consulte [esta seção](../../production/using/database-cleanup-workflow.md).

**Planos de manutenção**

Verifique se a manutenção do banco de dados está programada e executada corretamente. Para fazer isso, entre em contato com o administrador do banco de dados para saber mais sobre:

* o seu programa de manutenção,
* planos de manutenção anteriormente executados,
* visualização nos registros de scripts.

Para obter mais informações, consulte [esta seção](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Se você estiver usando uma configuração de mid-sourcing, é essencial que os bancos de dados sejam mantidos regularmente. Ao analisar um delivery na plataforma de marketing, a instância de marketing envia informações para a instância do mid-sourcing. Se o processo for retardado, a instância de marketing será afetada.

**Gerenciamento de tabelas de trabalho**

Verifique o número e o tamanho das tabelas de trabalho. Quando excedem um determinado tamanho, o desempenho do banco de dados é afetado. Essas tabelas são criadas por workflows e delivery. Eles permanecem no banco de dados enquanto workflows e delivery estão ativos. Para limitar o tamanho das tabelas de trabalho, é possível realizar as seguintes operações:

* parar ou excluir delivery com os seguintes status: **[!UICONTROL Failed]** , **[!UICONTROL In progress]** , **[!UICONTROL Ready for delivery]** , ou **[!UICONTROL Paused]** .
* parar ou eliminar workflows que estejam em pausa devido a um erro,
* Parar todos os workflows utilizados para ensaios que não contenham uma **[!UICONTROL End]** atividade e cujo estado se mantenha **[!UICONTROL Paused]** .

>[!IMPORTANT]
>
>Se a operação levar muito tempo e liberar muito espaço, isso significa que é necessária uma manutenção profunda (reconstrução de índice, etc.). Para obter mais informações, consulte [esta seção](../../production/using/recommendations.md).

**Monitoramento de processos da Adobe Campaign**

Dependendo das configurações de instalação do Adobe Campaign, duas ferramentas podem ser usadas para monitoramento da plataforma:

* a página de produção da instância. For more on this, refer to [Manual monitoring](../../production/using/monitoring-processes.md#manual-monitoring).
* o script netreport. Para obter mais informações, consulte Monitoramento [automático por meio de scripts](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)Adobe Campaign.

## Specifics {#specifics}

Pode ser necessário executar um diagnóstico em tempo real para identificar a causa do problema. Start verificando o processo e os arquivos de log da plataforma, em seguida, monitore a atividade do banco de dados ao recriar o problema. Preste especial atenção ao seguinte:

* o plano de execução da manutenção,
* QUERY SQL sendo executados,
* se os processos externos estão ou não em execução ao mesmo tempo (limpeza, importações, cálculo de agregação, etc.).

