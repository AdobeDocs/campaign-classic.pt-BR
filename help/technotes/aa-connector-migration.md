---
product: campaign
title: Migrar para o Adobe Analytics Connector
description: Campaign - Perguntas frequentes sobre o conector do Analytics
source-git-commit: e61f9facac61f942d26b4ffcb5a84a43ede6872d
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 5%

---

# Como migrar para o Adobe Analytics Connector {#acc-aa-faq}

A partir da versão 21.1.3 do Campaign Classic v7, o Adobe Analytics Data Connector será descontinuado. [Saiba mais](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

Em 1º de agosto de 2021, a Adobe Campaign Classic será removida da interface do usuário herdada dos Data Connectors, no entanto, as integrações existentes do Campaign continuarão a coletar e a transmitir dados para a Adobe Analytics até 1º de março de 2022. Em 1º de março de 2022, a integração deixará de coletar e transmitir dados para a Adobe Analytics.

Você deve migrar para a nova integração do Adobe Analytics Connector no Adobe Exchange, que substitui a integração herdada dos Data Connectors, conforme detalhado em [this page](../platform/using/adobe-analytics-connector.md).


>[!NOTE]
>
>Para dúvidas sobre essas alterações, leia as [Perguntas frequentes](#faq-aa). Para obter mais informações, entre em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## O que mudou?

Uma nova integração entre o Campaign Classic v7 e o Adobe Analytics está disponível. As alterações importantes estão listadas abaixo.

* A integração entre a autenticação Adobe Campaign Classic e Adobe Analytics foi movida de usuário/senha para Adobe Identity Management Service (IMS). Como consequência, você deve implementar o Adobe IMS e se conectar ao Campaign [por meio de um Adobe ID](../integrations/using/about-adobe-id.md), antes de iniciar a implementação do Analytics Connector.

* A Classificação **Data do Contato**, que costumam ser do tipo data, foi descontinuada pelo Adobe Analytics. Para integrações migradas, elas ainda permanecerão do mesmo tipo. Para qualquer **Data de Contato** criada pelo Campaign, o tipo será **Cadeia de caracteres**.

* **As** regras de processamento são criadas pela Adobe Campaign como parte de novas integrações. As **Regras de processamento** devem ser criadas manualmente no Adobe Analytics ou usar diretamente a implementação do Javascript do lado do cliente. **As** Regras de processamento permanecerão intactas para integrações existentes.

* Os workflows técnicos integrados e seu comportamento permanecem os mesmos. Somente as APIs de back-end usadas pelos workflows para enviar/receber dados de/para o Adobe Analytics foram alteradas.

* Observe que o processo `nlserver` deve ser configurado com o IMS Technical Account User (Usuário da conta técnica IMS) para que o novo conector funcione. Essa mudança deve ser feita por Adobe. Para que isso seja implementado, entre em contato com o [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Se você era APIs do Adobe Genesis em fluxos de trabalho personalizados para obter e enviar os dados do Adobe Analytics, agora é necessário usar as novas APIs do Adobe Analytics 1.4/2.0. [Saiba mais](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Você será afetado?

Se estiver usando o Conector de dados Adobe Analytics existente (anteriormente conhecido como Genesis integration) e a integração tiver sido implementada em uma build inferior à Campanha 21.1.3, você será afetado.

Saiba como verificar sua versão [nesta seção](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Como atualizar?

Você precisa atualizar para o Campaign 21.1.3 (ou mais) **antes de 1º de março de 2022**.

Como cliente hospedado, o Adobe trabalhará com você para atualizar suas instâncias para a versão mais recente.

Como cliente local/híbrido, é necessário atualizar para uma das versões mais recentes para se beneficiar da nova integração.

Depois que todas as instâncias forem atualizadas, você poderá [implementar a nova integração](../platform/using/adobe-analytics-connector.md) no Adobe Analytics Connector e garantir uma transição contínua.


## Perguntas frequentes{#faq-aa}

**Como posso obter registros?**

A configuração da interface do usuário e os workflows são equipados com o registro **verbose**.

No modo detalhado, os cabeçalhos de solicitação e resposta também são impressos para cada solicitação de API para o Adobe Analytics.

Como um usuário local, você pode implementar o modo detalhado da seguinte maneira:

* Para ativar o modo detalhado para a interface do usuário: execute novamente o processo `web` no modo detalhado.
* Para habilitar o modo detalhado para os workflows **webAnalytics**: selecione a opção **Execute in the engine** nas propriedades do workflow e execute novamente `wfserver` no modo detalhado.

**O que significa o erro &quot;Proprietário da integração não administrador&quot;?**

Saiba mais sobre o Erro dos Data Connectors `Integration Owner Not Admin` em [esta página](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Quando a migração para o novo conector for feita, o que acontece com os dados antigos e os conjuntos de relatórios?**

Após a migração, um novo conector (migrado do conector antigo) começará a enviar dados para o mesmo conjunto de relatórios e os dados existentes não serão afetados: será adicionado aos dados existentes.

**Algumas evars/eventos/conjuntos de relatórios existentes no Analytics não estão visíveis no Campaign. O que devo fazer?**

A integração depende de dados no Token de conta técnica para a operação diária. Se não houver permissão para uma dimensão/métrica/conjunto de relatórios do perfil de produto associado ao usuário de conta técnica, as APIs que usamos serão retidas para essas solicitações.

Se estamos lendo os detalhes de um componente do Analytics (como métricas/dimensões/segmentos/conjuntos de relatórios), a API não retornará esses componentes no resultado (que pode parecer que algo foi excluído do lado do Analytics ou não está presente). A API do Analytics rejeitará essas solicitações e rejeitará o erro.

A solução é atualizar o **Perfil de produto** no Contexto de Usuário do Analytics do Token de Usuário Técnico com os componentes recém-criados/ausentes, adicionando esses componentes em [Adobe Admin Console](https://adminconsole.adobe.com/). Para obter mais orientações, entre em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Links úteis

* [Atualizar seu ambiente](../production/using/build-upgrade.md)
* [Perguntas frequentes de atualização de build](../platform/using/faq-build-upgrade.md)
* [Baixar a build do Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Disponibilizar o novo Console do cliente para os usuários](../installation/using/client-console-availability-for-windows.md)
* [Instalar o console do cliente do Campaign](../installation/using/installing-the-client-console.md)
