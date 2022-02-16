---
product: campaign
title: Migrar para o Adobe Analytics Connector
description: Campaign - Perguntas frequentes sobre o conector do Analytics
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
source-git-commit: c072cb5b2d33f93ff395e4670507744b0d20c9bc
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 6%

---

# Como migrar integrações existentes do Genesis para o Adobe Analytics Connector {#acc-aa-faq}

![](../../assets/v7-only.svg)

A partir da versão 21.1.3 do Campaign Classic v7, o Adobe Analytics Data Connector será descontinuado. [Saiba mais](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

Em 1º de agosto de 2021, a Adobe Campaign Classic foi removida da interface do usuário herdada dos Data Connectors, no entanto, as integrações existentes do Campaign continuarão a coletar e transmitir dados para o Adobe Analytics até 17 de agosto de 2022. Após essa data, a integração deixará de coletar e transmitir dados para o Adobe Analytics.

Você **deve implementar** a nova integração do Adobe Analytics Connector no Adobe Exchange, que substitui a integração herdada dos Data Connectors. Para saber mais sobre o Adobe Analytics Connector, consulte [esta página](../../platform/using/adobe-analytics-connector.md).

>[!NOTE]
>
>Para dúvidas sobre essas alterações, leia a [Perguntas frequentes](#faq-aa). Para obter mais informações, entre em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## O que mudou?

Uma nova integração entre o Campaign Classic v7 e o Adobe Analytics está disponível. As alterações importantes estão listadas abaixo.

* O **Data de contato** A classificação, que costumava ser do tipo data, foi descontinuada pelo Adobe Analytics. Para integrações migradas, elas ainda permanecerão do mesmo tipo. Para qualquer **Data de contato** criado pelo Campaign, o tipo será **String**.

* **Regras de processamento** são criados pela Adobe Campaign como parte de novas integrações. Ou **Regras de processamento** O deve ser criado manualmente no Adobe Analytics ou usar diretamente a implementação do Javascript no lado do cliente. **Regras de processamento** permanecerá intacta para integrações existentes.

* Os workflows técnicos integrados e seu comportamento permanecem os mesmos. Somente as APIs de back-end usadas pelos workflows para enviar/receber dados de/para o Adobe Analytics foram alteradas.

* Observe que a variável `nlserver` O processo deve ser configurado com o IMS Technical Account User (Usuário da conta técnica IMS) para que o novo conector funcione. Essa mudança deve ser feita por Adobe. Para implementar isso, entre em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Se você era APIs do Adobe Genesis em fluxos de trabalho personalizados para obter e enviar os dados do Adobe Analytics, agora é necessário usar as novas APIs do Adobe Analytics 1.4/2.0. [Saiba mais](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Você será afetado?

Se estiver usando o Conector de dados Adobe Analytics existente (anteriormente conhecido como Genesis integration) e a integração tiver sido implementada em uma build inferior à Campanha 21.1.3, você será afetado.

Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Como atualizar?

Você precisa atualizar para o Campaign 21.1.3 (ou mais) **antes de 17 de agosto de 2022**.

Como cliente hospedado, o Adobe trabalhará com você para atualizar suas instâncias para a versão mais recente. Você poderá usar [Conector Adobe Analytics](../../platform/using/adobe-analytics-connector.md).

Como cliente local/híbrido, é necessário atualizar para uma das versões mais recentes para se beneficiar da nova integração.
Depois que todas as instâncias forem atualizadas, você poderá [implementar a nova integração](../../platform/using/adobe-analytics-provisioning.md) para o Adobe Analytics Connector e garanta uma transição contínua.

## Perguntas frequentes{#faq-aa}

**Como posso obter registros?**

A configuração da interface do usuário e os workflows estão equipados com **verboso** fazendo logon.

No modo detalhado, os cabeçalhos de solicitação e resposta também são impressos para cada solicitação de API para o Adobe Analytics.

Como um usuário local, você pode implementar o modo detalhado da seguinte maneira:

* Para ativar o modo detalhado para a interface do usuário: execute novamente o `web` processar no modo detalhado.
* Para ativar o modo detalhado para o **webAnalytics** fluxos de trabalho: selecione o **Executar no motor** nas propriedades do fluxo de trabalho e execute novamente `wfserver` no modo detalhado.

**O que significa o erro &quot;Proprietário da integração não administrador&quot;?**

Saiba mais sobre os Data Connectors `Integration Owner Not Admin` Erro em [esta página](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Quando a migração para o novo conector for feita, o que acontece com os dados antigos e os conjuntos de relatórios?**

Após a migração, um novo conector (migrado do conector antigo) começará a enviar dados para o mesmo conjunto de relatórios e os dados existentes não serão afetados: será adicionado aos dados existentes.

**Algumas evars/eventos/conjuntos de relatórios existentes no Analytics não estão visíveis no Campaign. O que devo fazer?**

A integração depende de dados no Token de conta técnica para a operação diária. Se não houver permissão para uma dimensão/métrica/conjunto de relatórios do perfil de produto associado ao usuário de conta técnica, as APIs que usamos serão retidas para essas solicitações.

Se estamos lendo os detalhes de um componente do Analytics (como métricas/dimensões/segmentos/conjuntos de relatórios), a API não retornará esses componentes no resultado (que pode parecer que algo foi excluído do lado do Analytics ou não está presente). A API do Analytics rejeitará essas solicitações e rejeitará o erro.

A solução é atualizar a variável **Perfil de produto** no Contexto de usuário do Analytics do Token de usuário técnico com os componentes recém-criados/ausentes, adicionando esses componentes em [Adobe Admin Console](https://adminconsole.adobe.com/). Para obter mais orientações, entre em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Links úteis

* [Atualizar seu ambiente](../../production/using/build-upgrade.md)
* [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md)
* [Baixar a build do Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html)
* [Disponibilizar o novo Console do cliente para os usuários](../../installation/using/client-console-availability-for-windows.md)
* [Instalar o console do cliente do Campaign](../../installation/using/installing-the-client-console.md)
