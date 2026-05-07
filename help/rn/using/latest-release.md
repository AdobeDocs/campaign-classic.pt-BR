---
product: campaign
title: Versão mais recente
description: Notas de versão mais recentes do Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: b9a716f327b8fdd68c3bf36dbe864535308def30
workflow-type: ht
source-wordcount: '294'
ht-degree: 100%

---

# Versão mais recente {#latest-release}

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign Classic v7**. Cada nova build vem com um status que é materializado por uma cor. Saiba mais sobre os status de build do Campaign Classic v7 [nesta página](rn-overview.md).

## Versão 7.4.3 – Build 9394 {#release-7-4-3}

[!BADGE Disponibilidade geral]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade geral"}

_16 de março de 2026_

>[!CAUTION]
>
> A atualização do Console do Cliente é obrigatória.

### Melhorias de segurança {#security-7-4-3}

* Para manter a segurança, a estabilidade e a conformidade ideais, o Debian foi atualizado para a versão 13 e o PostgreSQL para a versão 17. Consulte a [matriz de compatibilidade](compatibility-matrix.md).

### Correções {#fixes-7-4-3}

* Corrigimos um problema em que o componente de código de barras permitia um parâmetro de altura ilimitado, o que poderia causar uma vulnerabilidade de segurança. (NEO-89984)
* Corrigimos um problema em que os campos de enumeração em listas criadas por meio de fluxos de trabalho não possuíam atributos de nome temporário, o que fazia com que rótulos de enumeração incorretos ou em branco fossem exibidos na interface. (NEO-91158)
* Corrigimos um problema em que as estatísticas de entrega não eram totalmente recalculadas para algumas entregas, o que afetava especialmente os indicadores de sucesso. (NEO-88106)
* Corrigimos um problema em que a preparação da entrega falhava devido a erros de personalização ao usar campos targetData em fluxos de trabalho com atividades de desduplicação. (NEO-87693)
* Corrigimos um problema em que a concatenação de campos de strings de caractere único com outras strings falhava no PostgreSQL 15 devido a requisitos de conversão de tipos. (NEO-88028)
* Corrigimos um problema em que os logs de rastreamento das campanhas colaborativas no marketing distribuído não estavam sendo gravados no banco de dados devido a uma incompatibilidade entre as IDs de entrega pai e filho. (NEO-86836)
* Corrigimos um problema em que os logs de entrega exibiam mensagens como canceladas, mesmo que tivessem sido enviadas com sucesso, afetando especialmente as entregas com agendamento por lotes. (NEO-78933)
* Corrigimos um problema em que o fluxo de trabalho de limpeza do banco de dados não estava eliminando os dados de forma eficiente, o que poderia afetar o desempenho. (NEO-76439)

