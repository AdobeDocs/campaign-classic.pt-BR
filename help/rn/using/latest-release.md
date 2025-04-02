---
product: campaign
title: Versão mais recente
description: Notas de versão mais recentes do Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 86bc3bdfe628cc694e47a4670e99225e05b3df1b
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 100%

---

# Versão mais recente {#latest-release}

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign Classic v7**. Cada nova build vem com um status que é materializado por uma cor. Saiba mais sobre os status de build do Campaign Classic v7 [nesta página](rn-overview.md).

## Versão 7.4.2 - Build 9390 {#release-7-4-2}

[!BADGE Disponibilidade geral]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade geral"}

_quinta-feira, 2 de abril de 2025_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### Melhorias de segurança {#security-7-4-2}

Esta versão inclui várias correções de segurança.

A conexão com soluções e aplicativos da Adobe por meio da conta externa da **[!UICONTROL Adobe Experience Cloud]** foi atualizada para reforçar a segurança.

### Correções {#release-7-4-2-fixes}

Esta versão inclui as seguintes correções principais:

* Conexão TLS/SMPP: correção de problemas de estabilidade do SMPP

* Correções do Google BigQuery:

   * Correção de regressões em dados do tipo BOOLEAN
   * Correção de problemas de configurações de proxy
   * Correção de regressões em dados do tipo DATETIME
   * Correção da estabilidade do carregamento em massa
   * Testes internos aprimorados nas versões ODBC
   * Correção de um problema com caracteres especiais na string de conexão
   * Remoção do tempo-limite padrão (5 min.) de consultas do Google BigQuery

* Agente de transferência de correspondência (MTA): correção do MTA secundário órfão, que ficava preso no status **[!UICONTROL Start pending]**.

Os seguintes problemas também foram corrigidos nesta versão:

NEO-47269, NEO-59059, NEO-62455, NEO-65774, NEO-66462, NEO-66989, NEO-77898, NEO-78843, NEO-79373, NEO-79598, NEO-80145, NEO-80245, NEO-80434, NEO-80683, NEO-81222, NEO-81433, NEO-81864, NEO-82351, NEO-82781, NEO-82838, NEO-82923, NEO-83252, NEO-83809, NEO-83826, NEO-84024, NEO-84553, NEO-85150

