---
product: campaign
title: Versões do Campaign Classic 2024
description: Saiba mais sobre as versões do Campaign Classic 2024
feature: Release Notes
role: User
level: Beginner
exl-id: 8e20391d-3628-4d0c-b413-c34e046ae810
source-git-commit: bf45c8bcdd41e614f9be09bc0fd6385707159841
workflow-type: ht
source-wordcount: '387'
ht-degree: 100%

---

# Versões de 2024{#release-2024}

## Versão 7.4.1 - Build 9383 {#release-7-4-1}

[!BADGE Disponibilidade geral]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade geral"}

_18 de junho de 2024_

### Alterações e melhorias {#release-7-4-1-changes}

* Visto que a Adobe descontinuou a credencial de conta de serviço (JWT), as integrações de saída do Campaign com soluções e aplicativos da Adobe agora dependem da credencial de “servidor para servidor” do OAuth. Se você implementou integrações de saída, como a integração do Campaign com o Analytics ou a integração de acionadores da Experience Cloud, será necessário atualizar o ambiente do Campaign para a v7.4.1 e migrar sua conta técnica para oAuth antes de 27 de janeiro de 2025. [Saiba mais](../../integrations/using/oauth-technical-account.md)

* Depois de [migrar os operadores técnicos do Campaign para o Developer Console](../../technotes/using/ims-migration.md) e [fazer a transição para IMS para a autenticação do usuário final](../../technotes/using/migrate-users-to-ims.md), habilite a interface e as restrições da API para remover opções e recursos específicos da autenticação nativa. [Saiba mais](../../technotes/using/impact-ims-migration.md)


### Atualizações de compatibilidade {#release-7-4-1-compat}

A [matriz de compatibilidade do Adobe Campaign](compatibility-matrix.md) foi atualizada com as alterações incluídas nesta nova versão, as quais estão listadas abaixo.

* O Adobe Campaign agora é compatível com o sistema operacional **Microsoft Server 2022**.
* O Adobe Campaign agora é compatível com o sistema operacional **RHEL 9**.

  >[!CAUTION]
  >
  >Como cliente local usando RHEL 9, se quiser usar a autenticação DKIM (Domain Keys Identified Mail), atualize as configurações do sistema, conforme detalhado [nesta seção](../../installation/using/installing-packages-with-linux.md#rhel-9-update).


* O Adobe Campaign agora é compatível com os sistemas de gerenciamento de banco de dados relacionais **Microsoft SQL Server 2022** e **Oracle 23c**, bem como o Federated Data Access (FDA).

* O Adobe Campaign agora exige pelo menos um Java Development Kit (JDK) 11. No Windows, o JRE deve estar disponível conforme descrito [nesta seção](../../installation/using/application-server.md#jdk).

* O SDK do Campaign (Neolane) para aplicativos móveis foi descontinuado Você deve fazer a transição para o SDK da Adobe Experience Platform. [Saiba mais](deprecated-features.md).

  Enquanto isso, para garantir a continuidade do serviço, o Campaign v7.4 inclui:

   * um novo SDK 1.0.27 do Campaign para iOS, compatível com o iOS 16 e 17 e os mais recentes [requisitos de solicitação de privacidade do Apple iOS](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * um novo SDK do Campaign para Android 14.

### Outras alterações {#release-7-4-1-other}

A partir da v7.4.1, as bibliotecas de XML para pacotes de RPM do Linux não estão mais incluídas no Campaign. Como cliente local ou híbrido, sua administração precisa instalar estas bibliotecas. [Saiba mais](../../installation/using/installing-packages-with-linux.md)

### Patches {#release-7-4-1-patches}

Esta versão inclui as seguintes correções:

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-69651, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-62575, NEO-58734, NEO-40531, NEO-36189, NEO-29592


