---
product: campaign
title: Práticas recomendadas de desempenho de entrega
description: Saiba mais sobre o desempenho da entrega e as práticas recomendadas
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Deliverability
role: User, Data Engineer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 100%

---

# Práticas recomendadas de desempenho de entrega {#delivery-performances}

Recomendamos seguir as diretrizes abaixo para garantir que suas entregas tenham bom desempenho, bem como as verificações de desempenho caso haja problemas com entregas.

**Tópicos relacionados:**

* [Painel de entrega](delivery-dashboard.md)
* [Solução de problemas de entrega](delivery-troubleshooting.md)
* [Sobre a capacidade de entrega](about-deliverability.md)

## Práticas recomendadas de desempenho {#best-practices-performance}

* Não mantenha as entregas em estado de falha na instância, pois tabelas temporárias serão mantidas e o desempenho será afetado.

* Remova as entregas que não são mais necessárias.

* Recipients inativos nos últimos 12 meses a serem removidos do banco de dados para manter a qualidade do endereço.

* Não tente programar entregas grandes juntas. Há um intervalo de 5 a 10 minutos para espalhar a carga uniformemente sobre o sistema. Coordene a programação de entregas com os outros membros da equipe para garantir o melhor desempenho. Quando o servidor de marketing estiver lidando com várias tarefas diferentes ao mesmo tempo, ele poderá retardar o desempenho.

* Mantenha o tamanho do seus emails o menor possível. O tamanho máximo recomendado de um email é de aproximadamente 35 KB. O tamanho de uma entrega de email gera uma certa quantidade de volume nos servidores de envio.

* Entregas grandes, como para mais de um milhão de destinatários, precisam de espaço nas filas de envio. Isso por si só não é um problema para o servidor, mas quando combinado com dezenas de outras grandes entregas, sendo todas enviadas ao mesmo tempo, pode gerar um atraso no envio.

* A personalização em emails extrai dados do banco de dados para cada destinatário. Se houver muitos elementos de personalização, isso aumentará a quantidade de dados necessários para preparar a entrega.

* Endereços de índice. Para otimizar o desempenho das consultas SQL usadas no aplicativo, um índice pode ser declarado a partir do elemento principal do esquema de dados.

>[!NOTE]
>
>Os ISPs desativariam endereços após um período de inatividade. As mensagens com rejeição são enviadas aos remetentes para informá-los sobre esse novo status.

## Lista de verificação de problemas de desempenho {#performance-issues}

Se os desempenhos de entrega forem ruins, você poderá verificar:

* **O tamanho da entrega**: entregas grandes podem levar mais tempo para serem concluídas. Os MTA filho estão configurados para lidar com um tamanho de lote padrão, que funciona para a maioria das instâncias, mas precisam ser verificados quando as entregas estiverem constantemente lentas.
* **O target da entrega**: os desempenhos de entrega são afetados por erros de devolução temporária, que são manipulados de acordo com a configuração de repetição. Quanto maior o número de erros, mais tentativas são necessárias.
* **O carregamento da plataforma geral**: quando várias entregas grandes estão sendo enviadas, a plataforma geral pode ser afetada. Você também pode verificar problemas de reputação de IP e capacidade de entrega. Para obter mais informações, consulte [esta seção](about-deliverability.md) e o [Manual de práticas recomendadas de capacidade de entrega da Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR).

A manutenção da plataforma e do banco de dados também pode afetar os desempenhos de envio de entrega. Para obter mais informações, consulte [esta página](../../production/using/database-performances.md).
