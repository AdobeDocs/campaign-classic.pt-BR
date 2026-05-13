---
product: campaign
title: Versão mais recente
description: Notas de versão mais recentes do Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
TQID: https://experienceleague.adobe.com/Xq9y8r6xU-hypq1Eeo9ijaiGng7qqkWVqiCXW5fYx2c
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 3ebf57870a8fa7b2ad742f3978e982bc80c798d2
workflow-type: tm+mt
source-wordcount: 376
ht-degree: 76%

---

# Versão mais recente {#latest-release}

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign Classic v7**. Cada nova build vem com um status que é materializado por uma cor. Saiba mais sobre os status de build do Campaign Classic v7 [nesta página](rn-overview.md).

## Versão 7.4.3 – Build 9394 {#release-7-4-3}

[!BADGE Disponibilidade geral]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade geral"}

>[!CAUTION]
>
> A atualização do Console do Cliente é obrigatória.

_31 de março de 2026_

### Melhorias de segurança {#security-7-4-3}

* Para manter a segurança, a estabilidade e a conformidade ideais, o Debian foi atualizado para a versão 13 e o PostgreSQL para a versão 17. Consulte a [matriz de compatibilidade](compatibility-matrix.md).

### Correções {#fixes-7-4-3}

>[!NOTE]
>
> As correções listadas abaixo foram gradativamente implementadas em builds 7.4.3 sucessivas. Navegue até o **[!UICONTROL Help > About...]** [menu](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) para verificar se você tem a compilação 9394@28aaec9 mais recente. Entre em contato com seu representante da Adobe para obter mais informações.

* Corrigimos um problema em que o componente de código de barras permitia um parâmetro de altura ilimitado, o que poderia causar uma vulnerabilidade de segurança. (NEO-89984)
* Corrigimos um problema em que os campos de enumeração em listas criadas por meio de fluxos de trabalho não possuíam atributos de nome temporário, o que fazia com que rótulos de enumeração incorretos ou em branco fossem exibidos na interface. (NEO-91158)
* Corrigimos um problema em que a preparação da entrega falhava devido a erros de personalização ao usar campos targetData em fluxos de trabalho com atividades de desduplicação. (NEO-87693)
* Corrigimos um problema em que a concatenação de campos de strings de caractere único com outras strings falhava no PostgreSQL 15 devido a requisitos de conversão de tipos. (NEO-88028)
* Corrigimos um problema em que os logs de rastreamento das campanhas colaborativas no marketing distribuído não estavam sendo gravados no banco de dados devido a uma incompatibilidade entre as IDs de entrega pai e filho. (NEO-86836)
* Corrigimos um problema em que os logs de entrega exibiam mensagens como canceladas, mesmo que tivessem sido enviadas com sucesso, afetando especialmente as entregas com agendamento por lotes. (NEO-78933)
* Corrigimos um problema em que o fluxo de trabalho de limpeza do banco de dados não estava eliminando os dados de forma eficiente, o que poderia afetar o desempenho. (NEO-76439)

<!-- BUILD 7.0.9394.28aaec9 -->

* Corrigimos um problema em que as estatísticas de entrega não eram totalmente recalculadas para algumas entregas, o que afetava especialmente os indicadores de sucesso. (NEO-88106) <!-- moved from original 7.4.3 GA Fixes section -->
* Correção de um problema em que o Console do cliente podia falhar ao abrir determinados workflows que faziam referência a um esquema de direcionamento upstream ausente. (NEO-28727)
* Correção de um problema em que a versão do Console do cliente não podia ser identificada após uma falha na inicialização, pois o arquivo de versão estava ausente no pacote de instalação. (NEO-94798)

<!--
other fixes - ommitted from release notes

Internal/non-customer-facing:

* Fixed an internal DevOps build race condition when copying the `teradata_timezones.txt` file during build packaging. (NEO-66532) — internal only; the Jira description states "No impact for customers: either it builds (99.9% of the time) or it does not."
* Fixed an internal CI/CD issue where AWS CodeBuild jobs could fail randomly on EC2 Docker containers when copying files during build. (NEO-90823) — internal CI/CD infrastructure only

Customer-specific hotfixes:

* Fixed an issue where coupon assignment could fail during delivery message preparation due to a SQL syntax error when looking up coupon codes. (NEO-92857) — Verizon only
* Fixed an issue where the error count and status in the `nms:address` table were not consistently updated on the marketing server after recurring soft bounces, causing recipients to not be quarantined as expected even though they were correctly flagged on the mid-sourcing server. (NEO-94422) — Walgreens only
-->

