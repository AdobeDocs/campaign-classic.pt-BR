---
product: campaign
title: Versão mais recente
description: Notas de versão mais recentes do Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: d31aa28da06e65664da655b6b082563767b35f7a
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 19%

---

# Versão mais recente {#latest-release}

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign v7**. Cada nova build vem com um status que é materializado por uma cor. Saiba mais sobre os status de build do Campaign Classic v7 [nesta página](rn-overview.md).

## Versão 7.4.1 — Build 9383 {#release-7-4-1}

[!BADGE Disponibilidade geral]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade geral"}

_quarta-feira, 18 de junho de 2024_

### Alterações e melhorias {#release-7-4-1-changes}

* Com a credencial Conta de serviço (JWT) sendo descontinuada pelo Adobe, as integrações de saída do Campaign com soluções e aplicativos Adobe agora dependem da credencial de servidor para servidor OAuth. Se você implementou integrações de saída, como integração do Campaign com o Analytics ou integração do Experience Cloud Triggers, será necessário atualizar seu ambiente do Campaign para a v7.4.1 e migrar sua conta técnica para oAuth antes de 27 de janeiro de 2025. [Saiba mais](../../integrations/using/oauth-technical-account.md)

* Depois de [operadores técnicos do Campaign migrados para o Console do desenvolvedor](../../technotes/using/ims-migration.md) e [Transição para IMS para autenticação do usuário final](../../technotes/using/migrate-users-to-ims.md), agora é possível habilitar a interface de usuário e as restrições de API para remover opções e recursos específicos da autenticação nativa. [Saiba mais](../../technotes/using/impact-ims-migration.md)



### Atualizações de compatibilidade {#release-7-4-1-compat}

A variável [matriz de compatibilidade do Adobe Campaign](compatibility-matrix.md) O foi atualizado com as alterações que vêm com esta nova versão e listado abaixo.

* O Adobe Campaign agora é compatível com o **Microsoft Server 2022** e **RHEL 9** como sistemas operacionais.

* O Adobe Campaign agora é compatível com o **Microsoft SQL Server 2022** e **Oracle 23c** como Sistemas de Gerenciamento de Bancos de Dados de Relações e no FDA (Federated Data Access — Acesso a Dados Federados).

* O Adobe Campaign agora exige pelo menos um Java Development Kit (JDK) 11. No Windows, o JRE deve estar disponível conforme descrito em [nesta seção](../../installation/using/application-server.md#jdk).

* O SDK do Campaign (Neolane) para aplicativos móveis agora está obsoleto. Agora, você deve fazer a transição para o Adobe Experience Platform SDK. [Saiba mais](deprecated-features.md).

  Enquanto isso, para garantir a continuidade do serviço, o Campaign v7.4 vem com:

   * um novo SDK 1.0.27 do Campaign para iOS, compatível com o iOS 16 e 17 e os mais recentes [Requisitos da solicitação de privacidade do Apple iOS](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * um novo SDK do Campaign para Android 14.


### Correções {#release-7-4-1-patches}

Esta versão vem com as seguintes correções:

NEO74754, NEO73174, NEO72504, NEO71534, NEO71473, NEO70195, NEO69663, NEO69651, NEO67620, NEO67235, NEO66777, NEO64680, NEO63706, NEO63657, NEO62964, NEO62575, NEO58734, NEO40531, NEO36189, NEO29592

