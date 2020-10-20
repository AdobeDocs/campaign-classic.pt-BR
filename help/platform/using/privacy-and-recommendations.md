---
title: Privacidade e recomendações
seo-title: Privacidade e recomendações
description: Privacidade e recomendações
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
translation-type: tm+mt
source-git-commit: 247d73933991047603b8d61c7489d976c448dd52
workflow-type: tm+mt
source-wordcount: '1804'
ht-degree: 92%

---


# Privacidade e consentimento{#privacy-and-recommendations}

## Recomendações gerais {#general-recommendations}

O Adobe Campaign é uma ferramenta poderosa para coletar e processar quantidades extremamente grandes de dados, incluindo informações pessoais e dados confidenciais. É por isso que a privacidade precisa de ser gerenciada com cuidado.

* Utilize sempre as informações pessoais de modo responsável e ético.

* Evite enviar emails não solicitados, notificações por push e mensagens SMS (&quot;spam&quot;). A Adobe acredita fortemente nos princípios da permissão de marketing para promover o valor e a fidelidade do cliente e, portanto, é estritamente proibido o uso do Adobe Campaign para o envio de mensagens não solicitadas.

Reserve tempo para acessar a lista de [Verificação de segurança e privacidade](https://helpx.adobe.com/br/campaign/kb/acc-security.html) e conhecer seus principais elementos.

### Regras de privacidade {#privacy-regulations}

Para gerenciar corretamente a privacidade e os dados pessoais, trabalhe dentro das legislações aplicáveis às regiões onde você opera. Estas regras incluem:
* [GDPR](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en) (Regulamento geral europeu de proteção de dados)
* [APD](https://www.gov.uk/data-protection) (Aplicação do GDPR pelo Reino Unido)
* [Diretiva europeia relativa à privacidade e às comunicações eletrônicas](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) (Lei norte-americana que define as regras e os requisitos para o email comercial)
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=) (Ato de Privacidade do Consumidor da Califórnia)
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) (Lei de Proteção de Dados Pessoais da Tailândia)
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) (Lei Geral Brasileira de Proteção de Dados) - entrará em vigor a partir de 16 de agosto de 2020

>[!NOTE]
>
>Para obter mais informações sobre como o GDPR, CCPA, PDPA e LGPD se aplicam ao Adobe Campaign, consulte [esta página](https://helpx.adobe.com/br/campaign/kb/campaign-privacy-overview.html#whatisgdpr).

### Privacidade da Adobe Experience Cloud {#experience-cloud-privacy}

O Adobe Campaign faz parte das soluções da Adobe Experience Cloud. A maneira como a privacidade é tratada no Campaign obedece aos princípios gerais da Experience Cloud, como os seguintes:

* **Quais informações são coletadas ao usar a Adobe Experience Cloud**

   Como empresa usando as soluções da Adobe Experience Cloud, você escolhe quais informações coletar e enviar para sua conta da Adobe Experience Cloud. Exemplos dos tipos de informações que podem ser coletadas incluem atividade de navegação na web, endereços IP, informações de localização de dispositivos móveis, taxas de sucesso de campanha, itens comprados ou colocados no carrinho de compras, etc.

   >[!NOTE]
   >
   >Quanto a todos os produtos da Adobe, o Campaign coleta informações sobre os usuários do aplicativo e do site. Para obter mais informações, consulte a [Política de privacidade da Adobe](https://www.adobe.com/br/privacy/policy.html).

* **Como a Adobe Experience Cloud é usada para coletar informações**

   * As soluções da Adobe Experience Cloud usam cookies e tecnologias semelhantes, como web beacons (também conhecidos como tags ou pixels), para permitir que você colete informações. Para obter mais informações sobre cookies e recursos de rastreamento com o Adobe Campaign, consulte [esta seção](#tracking-capabilities).
   * Você também pode usar as tecnologias da Adobe Experience Cloud em seus aplicativos móveis. Para obter mais informações sobre como enviar delivery móvel com o Campaign, consulte [canal SMS](../../delivery/using/sms-channel.md) e [canal de aplicativo móvel](../../delivery/using/about-mobile-app-channel.md).

* **As opções de privacidade dos usuários sobre o uso da Adobe Experience Cloud**

   A Adobe solicita que você forneça aos seus clientes políticas de privacidade descrevendo:

   * Suas práticas de privacidade em conexão com a Adobe Experience Cloud
   * Como os usuários podem definir suas preferências para a coleção ou usar suas informações em conexão com a Adobe Experience Cloud

   >[!NOTE]
   >
   >Quanto a todos os produtos da Adobe, os usuários do Campaign podem recusar o compartilhamento das informações coletadas sobre eles por meio de aplicativos e sites. Para obter mais informações, consulte as [Perguntas frequentes sobre o uso de informações com a Adobe Experience Cloud](https://www.adobe.com/br/privacy/experience-cloud-usage-info-faq.html).

Para obter mais detalhes sobre a privacidade da Adobe Experience Cloud, consulte [esta página](https://www.adobe.com/br/privacy/marketing-cloud.html).

## Dados pessoais e Personalidades {#personal-data}

Ao gerenciar a privacidade, é importante definir quais dados devem ser tratados com cuidado e por quem.
* **Dados pessoais** são informações que podem identificar direta ou indiretamente um indivíduo vivo.
* **Dados confidenciais pessoais** são informações relacionadas a raça, visão política, crenças religiosas, antecedentes criminais, informações genéticas, dados de saúde, preferência sexual, informações biométricas, bem como participação em uniões comerciais.

As [principais legislações](#privacy-regulations) referem-se às diferentes entidades que gerem os dados da seguinte forma:
* Um **Controlador de dados** é a autoridade que determina os meios e a finalidade de coleta, utilização e compartilhamento de dados pessoais.
* Um **Processador de dados** é qualquer pessoa física ou parte que coleta, utiliza ou compartilha dados pessoais, conforme determinado pelo Controlador de dados.
* Um **Titular de dados** é qualquer pessoa viva cujos dados pessoais estejam sendo coletados, utilizados ou compartilhados, e que possa ser identificada, direta ou indiretamente, por referência a esses dados pessoais.

Portanto, como uma empresa que coleta e compartilha dados pessoais, você é o Controlador de dados, seus clientes são os Titulares dos dados e o Adobe Campaign atua como um Processador de dados ao tratar os dados pessoais indicados por você. Observe que é sua responsabilidade como Controlador de dados, tratar a relação com os Titulares dos dados, como ao gerenciar [solicitações de privacidade](#privacy-requests).

Ao integrar o Campaign a outras soluções da Experience Cloud, onde os públicos-alvo podem ser transferidos de um sistema para outro, como o [Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md), o [serviço principal do Audience Manager ou People](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md), o [Campaign Standard](../../integrations/using/synchronizing-audiences.md) ou outras soluções por meio dos [Conectores CRM](../../platform/using/crm-connectors.md), é necessário ter cuidado extra com a proteção de dados pessoais.

## Aquisição de dados {#data-acquisition}

O Adobe Campaign permite coletar dados, inclusive informações pessoais e confidenciais. Portanto, é essencial que você receba e monitore o consentimento de seus recipients.

* Tenha sempre o consentimento do recipient para o recebimento de comunicações. Para fazer isso, continue atendendo às solicitações de recusa o mais rápido possível e verifique o consentimento por meio de um duplo processo de aceitação. Para obter mais informações, consulte [Criar um formulário de inscrição com dupla aceitação](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).
* Não importe listas fraudulentas e utilize seed addresses para verificar se o arquivo do cliente não está sendo usado de forma fraudulenta. Para obter mais informações, consulte [Sobre seed addresses](../../delivery/using/about-seed-addresses.md).
* Por meio do gerenciamento de consentimento e direitos, você pode rastrear as preferências dos recipients, bem como gerenciar quem em sua organização pode acessar quais dados. Para obter mais informações, consulte [esta seção](#consent).
* Facilite e gerencie solicitações de privacidade de seus recipients. Para obter mais informações, consulte [esta seção](#privacy-requests).

## Gerenciamento de privacidade {#privacy-management}

O gerenciamento de privacidade está relacionado a todos os processos e ferramentas que podem ajudar você a cumprir as regras de privacidade (RGPD, CCPA, etc.). Obtenha uma visão geral do que é o gerenciamento de privacidade [nesta página](https://helpx.adobe.com/br/campaign/kb/campaign-privacy-overview.html).

O Adobe Campaign oferece vários conjuntos de recursos dedicados ao gerenciamento de privacidade:
* Gerenciamento de consentimento, retenção de dados e funções de usuário. Consulte [esta seção](#consent).
* Solicitações de privacidade (Direito de acesso e Direito de ser esquecido). Consulte [esta seção](#privacy-requests).
* Recusar a venda de informações pessoais (específico para CCPA). Consulte [esta seção](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html#ccpa).

Os principais recursos de privacidade do Campaign e um exemplo das personalidades envolvidas são apresentados nesta [seção](https://helpx.adobe.com/br/campaign/kb/campaign-privacy-more.html#gdprpersonasandflow).


### Consentimento, retenção e funções {#consent}

Originalmente, o Adobe Campaign oferece recursos importantes que são essenciais à privacidade:

* **Gerenciamento de consentimento**: por meio do processo de gerenciamento de assinaturas, você pode gerenciar suas preferências de recipient e rastrear quais recipients aceitaram e que tipo de assinatura. Para obter mais informações, consulte [Sobre assinaturas](../../delivery/using/about-services-and-subscriptions.md).
* **Retenção de dados**: todas as tabelas de registro padrão incorporadas têm períodos de retenção predefinidos, geralmente limitando seu armazenamento de dados a 6 meses ou menos. Períodos de retenção adicionais podem ser configurados com workflows. Para obter mais informações, entre em contato com os consultores ou administradores técnicos da Adobe.
* **Gerenciamento de direitos**: o Adobe Campaign oferece a capacidade de gerenciar os direitos atribuídos aos vários operadores do Campaign por meio de diferentes funções pré-concebidas ou personalizadas. Isso permite gerenciar quem em sua empresa pode acessar, modificar ou exportar diferentes tipos de dados. Para obter mais informações, consulte [Sobre o gerenciamento de acesso](../../platform/using/access-management.md).

Para obter mais informações sobre esses recursos e como gerenciá-los no Adobe Campaign, consulte [esta página](https://helpx.adobe.com/br/campaign/kb/campaign-privacy-overview.html#consent).

### Solicitações de privacidade {#privacy-requests}

O Adobe Campaign fornece recursos adicionais para ajudar você se tornar um Controlador de dados para determinadas Solicitações de privacidade:

* O **Direito de acesso** é o Direito do titular de dados de obter a confirmação do Controlador de dados, caso os dados relativos a ele estejam sendo processados, onde e com que finalidade.

* O **Direito de ser esquecido** (solicitação de exclusão) autoriza o Titular dos dados a ter seus dados pessoais cancelados pelo Controlador de dados.

>[!NOTE]
>
>Este conjunto de ferramentas está aqui para ajudar você com sua conformidade de privacidade para GDPR, CCPA, PDPA e LGPD. Para obter mais informações sobre esses diferentes regulamentos, consulte [esta página](https://helpx.adobe.com/br/campaign/kb/campaign-privacy-overview.html#whatisgdpr).

<!--* **GDPR** (General Data Protection Regulation) is the European Union’s (EU) privacy law that harmonizes and modernizes data protection requirements. GDPR applies to Adobe Campaign customers who hold data for Data Subjects residing in the EU.

* **CCPA** (California Consumer Privacy Act) provides California residents new rights in regards to their personal information and imposes data protection responsibilities on certain entities whom conduct business in California.

* **Thailand's PDPA** (Personal Data Protection Act) is the new privacy law that harmonizes and modernizes data protection requirements for Thailand. This regulation applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.

Brazil's Lei Geral de Proteção de Dados (LGPD) will be effective starting Aug, 16 for all companies collecting or processing personal data in Brazil. This regulation also applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.-->

As solicitações de **Acesso** e **Exclusão** são apresentadas [nesta página](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html#righttoaccess). As etapas de implementação para criar essas solicitações estão detalhadas nesta [seção](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html#ManagingPrivacyRequests). <!--Tutorials are also available [here](https://docs.adobe.com/content/help/en/campaign-standard-learn/tutorials/privacy/privacy-overview.html).-->

## Recursos de rastreamento {#tracking-capabilities}

### Cookies {#cookies}

Graças às suas funcionalidades de rastreamento, a Adobe Campaign permite que você rastreie a navegação de recipient de delivery usando três tipos de cookies: um cookie de sessão e dois cookies permanentes.

* A **session cookie**: the **nlid** cookie contains the identifier of the email sent to the contact (**broadlogId**) and the identifier of the message template (**deliveryId**). Ele é adicionado quando o contato clica em um URL incluído em um email enviado pelo Adobe Campaign e permite que você acompanhe seu comportamento na Web. Esse cookie de sessão é apagado automaticamente quando o navegador é fechado. O contato pode configurar o navegador para recusar cookies.

* Um cookie **** permanente: o cookie **UUID** (Universal Unique IDentifier) é compartilhado entre as soluções da Adobe Experience Cloud. É definido uma vez até que desapareça do navegador do cliente quando um novo valor é gerado. Este cookie permite identificar os usuários que interagem com as soluções de Experience Cloud quando visitam um site. Ele pode ser depositado por uma landing page (para associar atividades desconhecidas do cliente a um recipient) ou por um delivery. A descrição deste cookie está disponível [aqui](https://docs.adobe.com/content/help/pt-BR/core-services/interface/ec-cookies/cookies-mc.html).

<!--The **nllastdelid** cookie (introduced in Campaign Classic 20.3) is a permanent cookie which contains the **deliveryId** of the last delivery that user clicked the link from. This cookie is used - when the session cookie is missing - to identify the tracking table that will be used.-->

Regulamentos como o Regulamento Geral sobre a Proteção de Dados (GDPR) afirmam que as empresas exigem o acordo dos usuários do site antes da instalação de qualquer cookie.

* Você deve informar aos usuários que seus sites estão equipados com ferramentas de rastreamento web por meio de uma solicitação de autorização (que aparece, por exemplo, sobre a página) com uma caixa de seleção que autoriza a utilização de cookies ou adicionando um banner na parte superior da primeira página, etc.
* As janelas pop-up devem ser evitadas, pois geralmente são bloqueadas pelos navegadores.

### Rastreamento de mensagens {#message-tracking}

O Adobe Campaign permite rastrear os emails enviados e o comportamento dos recipient do delivery: abrir, clicar em links, cancelamento de assinatura, etc. Para obter mais informações, consulte [Sobre o rastreamento de mensagens](../../delivery/using/about-message-tracking.md).

Para fazer isso, adicione [links rastreados](../../delivery/using/how-to-configure-tracked-links.md) às suas mensagens para medir o impacto do comportamento do delivery e do recipient na guia [Rastreamento](../../delivery/using/monitoring-a-delivery.md#tracking-logs) do painel do delivery. Os dados de rastreamento são interpretados no relatório de [Indicadores de rastreamento](../../reporting/using/delivery-reports.md#tracking-indicators).

### Acompanhamento da Web {#web-tracking}

O Adobe Campaign também permite monitorar como os recipients navegam em seu site: insira tag de rastreamento para coletar informações e medir visitas em páginas de aplicativos da Web. Para obter mais informações, consulte [Rastreamento de um aplicativo da web](../../web/using/tracking-a-web-application.md).

A configuração de rastreamento na web é apresentada [nesta seção](../../configuration/using/about-web-tracking.md).

Para gerenciar ainda mais o rastreamento, o Adobe Campaign permite exibir um banner de recusa de participação para interromper o rastreamento de comportamentos da web de usuários finais que recusam o rastreamento comportamental. Para obter mais informações, consulte [Recusa de rastreamento em aplicação web](../../web/using/web-application-tracking-opt-out.md).
