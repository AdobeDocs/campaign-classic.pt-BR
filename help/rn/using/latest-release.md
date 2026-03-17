---
product: campaign
title: Versão mais recente
description: Notas de versão mais recentes do Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: b9a716f327b8fdd68c3bf36dbe864535308def30
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 28%

---

# Versão mais recente {#latest-release}

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign Classic v7**. Cada nova build vem com um status que é materializado por uma cor. Saiba mais sobre os status de build do Campaign Classic v7 [nesta página](rn-overview.md).

## Versão 7.4.3 - Build 9394 {#release-7-4-3}

[!BADGE Disponibilidade geral]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade geral"}

_terça-feira, 16 de março de 2026_

>[!CAUTION]
>
> A atualização do Console do cliente é obrigatória.

### Melhorias de segurança {#security-7-4-3}

* Para manter a segurança, a estabilidade e a conformidade ideais, o Debian foi atualizado para a versão 13 e o PostgreSQL para a versão 17. Consulte a [matriz de compatibilidade](compatibility-matrix.md).

### Correções {#fixes-7-4-3}

* Correção de um problema em que o componente de código de barras permitia um parâmetro de altura não vinculado, o que poderia resultar em uma vulnerabilidade de segurança. (NEO-89984)
* Correção de um problema em que os campos de enumeração em listas criadas por meio de workflows não tinham atributos de nome temporários, fazendo com que rótulos de enumeração incorretos ou em branco fossem exibidos na interface. (NEO-91158)
* Correção de um problema em que as estatísticas de delivery não eram totalmente recalculadas para algumas deliveries, afetando particularmente os indicadores de sucesso. (NEO-88106)
* Correção de um problema em que a preparação do delivery falhava com erros de personalização ao usar campos targetData em workflows com atividades de desduplicação. (NEO-87693)
* Correção de um problema em que a concatenação de campos de sequência de caracteres únicos com outras sequências falhava no PostgreSQL 15 devido a requisitos de conversão de tipo. (NEO-88028)
* Correção de um problema em que os logs de rastreamento de campanhas colaborativas em Marketing distribuído não eram gravados no banco de dados devido a uma incompatibilidade entre IDs de entrega pai e filho. (NEO-86836)
* Correção de um problema em que os logs do delivery mostravam mensagens como canceladas mesmo que fossem enviadas com êxito, afetando principalmente os deliveries com agendamento de onda. (NEO-78933)
* Correção de um problema em que o fluxo de trabalho de limpeza do banco de dados não limpava dados com eficiência, o que poderia afetar o desempenho. (NEO-76439)

