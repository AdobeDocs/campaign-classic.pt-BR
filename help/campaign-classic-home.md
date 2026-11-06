---
keywords: Campaign Classic;página inicial;tópicos populares
product: campaign
title: Documentação do produto Adobe Campaign Classic v7
exl-id: 6b3f1689-80de-49fd-b7ee-7a2a1931d157
TQID: 'https://experienceleague.adobe.com/Q6Oc24mo-1qDAxCWu2lGT4UvRLXB78Tr5X4sb2kHFw8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: 186021e65b592522f3c491fb518594b5bac5d003
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 41%
---
# Documentação do Campaign Classic v7 {#campaign-classic-documentation}

Esta documentação abrange o Campaign Classic v7 para **implantações locais e híbridas**: instalação, configuração, atualizações, operações e os recursos específicos do v7. Se sua instância for hospedada pelo Adobe (Managed Cloud Services), consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/campaign-home){target="_blank"}. O conteúdo que o Campaign v8 documenta da mesma maneira não é mais duplicado aqui: consulte [Da v7 para a v8](#from-v7-to-v8).

<!--![](platform/using/assets/do-not-localize/banner_acc_doc.jpg) -->

## Novidades

Dê uma olhada nos últimos aprimoramentos do produto e da documentação do Adobe Campaign Classic v7. Para obter uma lista de todos os recursos, melhorias e correções, confira as [Notas de versão](rn/using/latest-release.md) detalhadas.

>[!BEGINTABS]


>A versão de [!TAB outubro de 2026 está disponível!]

A build do Campaign Classic v7.4.5 - outubro de 2026 (Build 9420) fornece correções para a conta externa do Analytics, deliveries presos no status de personalização pendente, uso do CPU do servidor, falhas intermitentes de atualização do modelo de dados, o erro de verificação de spam na criação de delivery e a quarentena de rejeições temporárias recorrentes.

[![imagem](assets/do-not-localize/learn-more-button.svg)](rn/using/latest-release.md)

>[!TAB Migrar para o Adobe IMS]

Para aprimorar a segurança e o processo de autenticação, o Adobe Campaign recomenda migrar o modo de autenticação do usuário final da autenticação nativa de logon/senha para o Sistema de gerenciamento de identidades da Adobe (IMS).

[![imagem](assets/do-not-localize/learn-more-button.svg)](technotes/using/ac-ims.md)


>[!ENDTABS]

## Comece com as noções básicas

<table style="table-layout:fixed">
  <tr style="border: 0;">
    <td>
    <a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/start-launch.png"></a></a>
    <div><strong>Inicialização do Adobe Campaign</strong><br/>Saiba como iniciar o console do cliente do Campaign e conectar-se aos servidores de aplicativos do Campaign.</div>
    </td>
    <td>
    <a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/start-profiles.png"></a>
    <div><strong>Adição e gerenciamento de perfis</strong><br/>Conheça o gerenciamento de perfis no banco de dados do Adobe Campaign v7 com facilidade. Adicione perfis manualmente ou por meio de importações, refinando os dados de clientes e personalizando campanhas facilmente.</div>
    </td>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/start-workflows.jpeg"></a>
    <div><strong>Automatização com fluxos de trabalho</strong><br/>Saiba como aproveitar fluxos de trabalho para projetar processos, incluindo segmentação, execução de campanha, processamento de arquivos, participação humana, entre outros.
    </div></td>
    <td>
    <a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/start-deliveries.jpeg"></a>
    <div><strong>Criação de entregas</strong><br/>Saiba como enviar mensagens em vários canais, como email, SMS, notificações por push etc.</div>
    </td>
  </tr>
  <tr style="border: 0;">
    <td align="center"><a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    </tr>
</table>

## Conheça a documentação

<table style="table-layout:auto">
  <tr style="border: 0;">
    <td>
      <img src="assets/do-not-localize/icon-configure.svg" width="35px">
      <br/>
      <strong>Administradores</strong><br/><a href="production/using/general-architecture.md">Princípios de arquitetura</a> - <a href="production/using/configuration.md">Configurar o Campaign</a> - <a href="platform/using/launching-adobe-campaign.md">Conectar-se ao Campaign</a> - <a href="installation/using/external-accounts.md">Conectar-se a sistemas externos</a> - <a href="platform/using/access-management.md">Permissões</a> - <a href="platform/using/privacy-management.md">Privacidade e consentimento</a> - <a href="production/using/build-upgrade.md">Executando uma atualização de compilação</a> - <a href="delivery/using/about-deliverability.md">Capacidade de entrega</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-send.svg" width="35px">
      <br/>
      <strong>Profissionais de marketing</strong><br/><a href="https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/new/campaign-ui" target="_blank">Interface do usuário</a> (documentação do Campaign v8) - <a href="https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/data/import" target="_blank">Importar e exportar dados</a> (documentação do Campaign v8) - <a href="https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/audience/create-audiences/create-audiences" target="_blank">Criar listas</a> (documentação do Campaign v8) - <a href="delivery/using/about-services-and-subscriptions.md">Serviços e assinaturas</a> - <a href="delivery/using/communication-channels.md">Canais de comunicação</a> - <a href="delivery/using/about-personalization.md">Personalization</a> - <a href="https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/create-message" target="_blank">Enviar provas</a> (documentação do Campaign v8) - <a href="delivery/using/get-started-a-b-testing.md">Teste A/B</a> - <a href="message-center/using/about-transactional-messaging.md">Mensagens transacionais</a> - <a href="interaction/using/interaction-and-offer-management.md">Interação e gerenciamento de ofertas</a> - <a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank">Automatizar com fluxos de trabalho</a> (documentação do Campaign v8) - <a href="https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=pt-BR" target="_blank">Campanha de marketing</a> - <a href="https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/tracking/tracking" target="_blank">Rastreamento de mensagens</a> (documentação do Campaign v8) - <a href="https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/reports/gs-reporting" target="_blank">Relatórios</a> (documentação do Campaign v8)
    </td>
    <td>
      <img src="assets/do-not-localize/icon-dev.svg" width="35px">
      <br/>
      <strong>Desenvolvedores</strong><br/><a href="https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/developer/datamodel" target="_blank">Descrição do modelo de dados</a> (documentação do Campaign v8) - <a href="configuration/using/about-schema-reference.md">Estrutura do esquema</a> - <a href="configuration/using/editing-forms.md">Formulários de entrada</a> - <a href="configuration/using/about-web-services.md">APIs</a> - <a href="https://experienceleague.adobe.com/pt-br/tools/campaign-api" target="_blank">Documentação de referência JSAPI</a> - <a href="configuration/using/about-custom-recipient-table.md">Tabela de destinatários personalizada</a>
    </td>
  </tr>
</table>

## Da v7 para v8 {#from-v7-to-v8}

O conteúdo documentado na documentação do Campaign v8 foi removido da documentação do v7. Use esta tabela para encontrá-la.

| Se você estiver procurando por... | Acesse a documentação do Campaign v8 |
| --- | --- |
| A interface do usuário | [Descobrir a interface do usuário](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/new/campaign-ui){target="_blank"} |
| Perfis, listas, importação e exportação | [Importar perfis e dados](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/data/import){target="_blank"} |
| Fluxos de trabalho | [Sobre fluxos de trabalho](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows){target="_blank"} |
| Campanhas de marketing | [Introdução às campanhas de marketing](https://experienceleague.adobe.com/en/docs/campaign/automation/campaign-orchestration/set-up-campaigns){target="_blank"} |
| Criação e envio de deliveries | [Criar uma mensagem](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/create-message){target="_blank"} |
| Relatórios integrados | [Introdução aos relatórios](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/reports/gs-reporting){target="_blank"} |
| Permissões | [Introdução a permissões](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"} |
| Formulários de entrada | [Introdução aos formulários de entrada](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/developer/schemas-forms/forms){target="_blank"} |

## Recursos adicionais

[Descrição do produto Adobe Campaign](https://helpx.adobe.com/br/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"} – [Matriz de compatibilidade](rn/using/compatibility-matrix.md) – [Tutoriais](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR){target="_blank"} – [Painel de controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=pt-BR){target="_blank"} – [Pixels de rastreamento de email e orientações da CNIL](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/new/cnil-pixel-tracking){target="_blank"}
