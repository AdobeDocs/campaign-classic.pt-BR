---
product: campaign
title: Migrar para o Adobe Analytics Connector
description: Campaign - Perguntas frequentes sobre o Analytics Connector
feature: Technote, Analytics Integration
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações no local e híbridas do v7"
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
hide: true
hidefromtoc: true
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 3%

---

# Como migrar integrações de Genesis existentes para o Adobe Analytics Connector {#acc-aa-faq}

A partir da versão 21.1.3 do Campaign Classic v7, o Conector de dados do Adobe Analytics não será mais utilizado. [Saiba mais](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html?lang=pt-BR)

Em 1º de agosto de 2021, o Adobe Campaign Classic foi removido da interface herdada do Data Connectors. No entanto, as integrações existentes do Campaign continuarão a coletar e transmitir dados para o Adobe Analytics até 17 de agosto de 2022. Após essa data, a integração deixará de coletar e transmitir dados para o Adobe Analytics.

Você **deve implementar** a nova integração do Adobe Analytics Connector no Adobe Exchange, que substitui a integração herdada do Data Connectors. Para saber mais sobre o Adobe Analytics Connector, consulte [esta página](../../integrations/using/gs-aa.md).

Para perguntas sobre essas alterações, leia as [Perguntas frequentes](#faq-aa). Para obter mais informações, contate o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

>[!NOTE]
>
>Se você estiver migrando de um Conector de dados do Adobe Analytics existente (anteriormente conhecido como integração de Genesis) e usando a Nova arquitetura de classificação no Adobe Analytics, será necessário ter versões de build a partir da versão 7.3.1 ou 8.4.1 para poder migrar para o novo Conector do Adobe Analytics.

## O que mudou?

Uma nova integração entre o Campaign Classic v7 e o Adobe Analytics está disponível. As principais alterações estão listadas abaixo.

* A Classificação **Data de contato**, que é do tipo data, foi descontinuada pela Adobe Analytics. Para integrações migradas, ele ainda permanecerá do mesmo tipo. Para qualquer **Data de Contato** criada pelo Campaign, o tipo será **Cadeia de caracteres**.

* **As Regras de processamento** são criadas pela Adobe Campaign como parte das novas integrações. As **Regras de Processamento** devem ser criadas manualmente a partir do Adobe Analytics ou usar diretamente a implementação do Javascript do lado do cliente. As **Regras de processamento** permanecerão intactas para integrações existentes.

* Os workflows técnicos integrados e seu comportamento permanecem os mesmos. Somente as APIs de back-end usadas pelos workflows para enviar/receber dados de/para o Adobe Analytics foram alteradas.

* Observe que o processo `nlserver` deve ser configurado com o Usuário de conta técnica IMS para que o novo conector funcione. Essa alteração deve ser feita por Adobe. Para implementar, entre em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Se você era um usuário de APIs do Adobe Genesis em fluxos de trabalho personalizados para extrair e enviar dados do Adobe Analytics, agora é necessário usar as novas APIs do Adobe Analytics 1.4/2.0. [Saiba mais](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Você será afetado?

Se você estiver usando o Conector de dados do Adobe Analytics existente (anteriormente conhecido como integração de Genesis) e a integração tiver sido implementada em uma build inferior ao Campaign 21.1.3, você será afetado.

Saiba como verificar sua versão [nesta seção](../../integrations/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Como atualizar?

Você precisa atualizar para o Campaign 21.1.3 (ou posterior) **antes de 17 de agosto de 2022**.

Como cliente hospedado, o Adobe trabalhará com você para atualizar sua(s) instância(s) para a versão mais recente. Você poderá usar o [conector do Adobe Analytics](../../platform/using/gs-aa.md).

Como cliente local/híbrido, é necessário atualizar para uma das versões mais recentes para se beneficiar da nova integração.
Depois que todas as instâncias forem atualizadas, você poderá [implementar a nova integração](../../integrations/using/adobe-analytics-provisioning.md) com o Adobe Analytics Connector e garantir uma transição contínua.

## Perguntas frequentes{#faq-aa}

**Como posso obter logs?**

A configuração e os fluxos de trabalho da interface do usuário estão equipados com o log **verbose**.

No modo detalhado, os cabeçalhos de solicitação e resposta também são impressos para cada solicitação de API para o Adobe Analytics.

Como usuário local, você pode implementar o modo detalhado da seguinte maneira:

* Para habilitar o modo detalhado para a interface do usuário: execute novamente o processo `web` no modo detalhado.
* Para habilitar o modo detalhado para os fluxos de trabalho do **webAnalytics**: selecione a opção **Executar no mecanismo** nas propriedades do fluxo de trabalho e execute `wfserver` novamente no modo detalhado.

**O que significa o erro &#39;Proprietário da integração não é administrador&#39;?**

Saiba mais sobre o Erro `Integration Owner Not Admin` do Data Connectors em [esta página](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Depois que a migração para o novo conector for concluída, o que acontecerá com os dados e conjuntos de relatórios antigos?**

Após a migração, um novo conector (migrado do conector antigo) começará a enviar dados para o mesmo conjunto de relatórios e os dados existentes não serão afetados: ele será adicionado aos dados existentes.

**Algumas evars/eventos/conjuntos de relatórios existentes no Analytics não estão visíveis no Campaign. O que devo fazer?**

A integração depende dos dados no Token de conta técnica para a operação diária. Se não houver permissão para uma dimensão/métrica/conjunto de relatórios no perfil de produto associado ao Usuário técnico da conta, as APIs que usamos simplesmente falharão para essas solicitações.

Se estivermos lendo para obter detalhes de um componente do Analytics (como métricas/dimensões/segmentos/conjuntos de relatórios), a API não retornará esses componentes no resultado (que pode parecer que algo foi excluído no Analytics ou não está presente). A API do Analytics rejeitará essas solicitações e ocorrerá um erro.

A solução é atualizar o **Perfil de Produto** no Contexto de Usuário do Analytics do Token de Usuário Técnico com os componentes recém-criados/ausentes adicionando esses componentes no [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}. Para obter mais orientações, entre em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Links úteis

* [Atualizar o ambiente](../../production/using/build-upgrade.md)
* [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md)
* [Baixar compilação de Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html)
* [Disponibilizar o novo Console do cliente para os usuários](../../installation/using/client-console-availability-for-windows.md)
* [Instalar o console do cliente do Campaign](../../installation/using/installing-the-client-console.md)
