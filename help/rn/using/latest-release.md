---
product: campaign
title: Versão mais recente
description: Notas de versão mais recentes do Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 631188b5974eaa4cd1bf667c5df9f2ff0f983cf0
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 28%

---

# Versão mais recente {#latest-release}

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign Classic v7**. Cada nova build vem com um status que é materializado por uma cor. Saiba mais sobre os status de build do Campaign Classic v7 [nesta página](rn-overview.md).

## Versão 7.4.2 - Build 9390 {#release-7-4-2}

[!BADGE Disponibilidade limitada]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade limitada"}

_sábado, 21 de março de 2025_

>[!AVAILABILITY]
>
>Esta versão está em **Disponibilidade limitada** (LA). É restrito somente a usuários do Hosted/Managed Services. Esta versão estará em breve disponível para clientes híbridos e no local.

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### Melhorias de segurança {#security-7-4-2}

Esta versão vem com várias correções de segurança.

A conexão com soluções e aplicativos da Adobe por meio da conta externa **[!UICONTROL Adobe Experience Cloud]** foi atualizada para reforçar a segurança.

### Correções {#release-7-4-2-fixes}

Essa versão vem com as seguintes correções principais:

* Conexão TLS/SMPP - Problemas de estabilidade SMPP corrigidos

* Correções do Google BigQuery:

   * Regressões fixas em tipos de dados BOOLEAN
   * Correção de problemas de configurações de proxy
   * Regressões fixas nos tipos de dados DATETIME
   * Estabilidade fixa da carga em massa
   * Testes internos aprimorados em versões ODBC
   * Correção de um problema com caracteres especiais na cadeia de conexão
   * Tempo limite padrão removido (5 min) em consultas do Google BigQuery

* Agente de Transferência de Correspondência (MTA) - Corrigido o MTA órfão filho a ficar preso no status **[!UICONTROL Start pending]**.

Os seguintes problemas também foram corrigidos nesta versão:

NEO47269, NEO59059, NEO62455, NEO65774, NEO66462, NEO66989, NEO77898, NEO78843, NEO79373, NEO79598, NEO80145, NEO80245, NEO80434, NEO80683, NEO81222, NEO81433, NEO81864, NEO82351, NEO82781, NEO82838, NEO8392 NEO83252, NEO83809, NEO83826, NEO84024, NEO84553, NEO85150

