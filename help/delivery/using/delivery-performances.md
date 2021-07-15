---
product: campaign
title: Práticas recomendadas de desempenho de entrega
description: Saiba mais sobre o desempenho do delivery e as práticas recomendadas.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: ht
source-wordcount: '458'
ht-degree: 100%

---

# Práticas recomendadas de desempenho de entrega {#delivery-performances}

Recomendamos seguir as diretrizes abaixo para garantir que seus deliveries tenham bom desempenho, bem como as verificações de desempenho caso haja problemas com deliveries.

**Tópicos relacionados:**

* [Painel de entrega](delivery-dashboard.md)
* [Solução de problemas de entrega](delivery-troubleshooting.md)
* [Sobre a capacidade de entrega](about-deliverability.md)

## Práticas recomendadas de desempenho {#best-practices-performance}

* Não mantenha os deliveries em estado de falha na instância, pois tabelas temporárias serão mantidas e o desempenho será afetado.

* Remova os deliveries que não são mais necessários.

* Recipients inativos nos últimos 12 meses a serem removidos do banco de dados para manter a qualidade do endereço.

* Não tente programar deliveries grandes juntos. Há um intervalo de 5 a 10 minutos para espalhar a carga uniformemente sobre o sistema. Coordene a programação de deliveries com os outros membros da equipe para garantir o melhor desempenho. Quando o servidor de marketing estiver lidando com várias tarefas diferentes ao mesmo tempo, ele poderá retardar o desempenho.

* Mantenha o tamanho do seus emails o menor possível. O tamanho máximo recomendado de um email é de aproximadamente 35 KB. O tamanho de um delivery de email gera uma certa quantidade de volume nos servidores de envio.

* Deliveries grandes, como para mais de um milhão de recipients, precisam de espaço nas filas de envio. Isso por si só não é um problema para o servidor, mas quando combinado com dezenas de outros grandes deliveries, sendo todos enviados ao mesmo tempo, pode gerar um atraso no envio.

* A personalização em emails extrai dados do banco de dados para cada recipient. Se houver muitos elementos de personalização, isso aumentará a quantidade de dados necessários para preparar o delivery.

* Endereços de índice. Para otimizar o desempenho das consultas SQL usadas no aplicativo, um índice pode ser declarado a partir do elemento principal do esquema de dados.

>[!NOTE]
>
>Os ISPs desativariam endereços após um período de inatividade. As mensagens com rejeição são enviadas aos remetentes para informá-los sobre esse novo status.

## Lista de verificação de problemas de desempenho {#performance-issues}

Se os desempenhos de delivery forem ruins, você poderá verificar:

* **O tamanho do delivery**: deliveries grandes podem levar mais tempo para serem concluídos. Os MTA filho estão configurados para lidar com um tamanho de lote padrão, que funciona para a maioria das instâncias, mas precisam ser verificados quando os deliveries estiverem constantemente lentos.
* **O target do delivery**: os desempenhos de delivery são afetados por erros de devolução temporária, que são manipulados de acordo com a configuração de repetição. Quanto maior o número de erros, mais tentativas são necessárias.
* **O carregamento da plataforma geral**: quando vários deliveries grandes estão sendo enviados, a plataforma geral pode ser afetada. Você também pode verificar problemas de reputação de IP e capacidade de delivery. Para obter mais informações, consulte [esta seção](about-deliverability.md) e o [Manual de práticas recomendadas de capacidade de delivery da Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR).

A manutenção da plataforma e do banco de dados também pode afetar os desempenhos de envio de delivery. Para obter mais informações, consulte [esta página](../../production/using/database-performances.md).
