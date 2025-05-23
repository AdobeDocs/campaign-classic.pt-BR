---
product: campaign
title: Privacidade e consentimento
description: Saiba mais sobre privacidade e consentimento
feature: Privacy, Privacy Tools
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: d2451b62-bddf-4dee-8789-35aaae8348e1
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: ht
source-wordcount: '1907'
ht-degree: 100%

---

# Privacidade e consentimento{#privacy-and-recommendations}


## Recomendações gerais {#general-recommendations}

O Adobe Campaign é uma ferramenta poderosa para coletar e processar quantidades extremamente grandes de dados, incluindo informações pessoais e dados confidenciais. É por isso que a privacidade precisa de ser gerenciada com cuidado.

* Utilize sempre as informações pessoais de modo responsável e ético.

* Evite enviar emails não solicitados, notificações por push e mensagens SMS (&quot;spam&quot;). A Adobe acredita fortemente nos princípios da permissão de marketing para promover o valor e a fidelidade do cliente e, portanto, é estritamente proibido o uso do Adobe Campaign para o envio de mensagens não solicitadas.

Reserve tempo para acessar a lista de [Verificação de segurança e privacidade](../../installation/using/get-started-security-privacy.md) e conhecer seus principais elementos.

### Regras de privacidade {#privacy-regulations}

Para gerenciar corretamente a privacidade e os dados pessoais, trabalhe dentro das legislações aplicáveis às regiões onde você opera. Os recursos do Adobe Campaign ajudam a cumprir os regulamentos listados [nesta página](../../platform/using/privacy-management.md#privacy-management-regulations).

### Privacidade da Adobe Experience Cloud {#experience-cloud-privacy}

O Adobe Campaign faz parte das soluções da Adobe Experience Cloud. A maneira como a privacidade é tratada no Campaign obedece aos princípios gerais da Experience Cloud, como os seguintes:

* **Quais informações são coletadas ao usar a Adobe Experience Cloud**

  Como empresa usando as soluções da Adobe Experience Cloud, você escolhe quais informações coletar e enviar para sua conta da Adobe Experience Cloud. Exemplos dos tipos de informações que podem ser coletadas incluem atividade de navegação na web, endereços IP, informações de localização de dispositivos móveis, taxas de sucesso de campanha, itens comprados ou colocados no carrinho de compras, etc.

  >[!NOTE]
  >
  >Quanto a todos os produtos da Adobe, o Campaign coleta informações sobre os usuários do aplicativo e do site. Para obter mais informações, consulte a [Política de privacidade da Adobe](https://www.adobe.com/br/privacy/policy.html).

* **Como a Adobe Experience Cloud é usada para coletar informações**

   * As soluções da Adobe Experience Cloud usam cookies e tecnologias semelhantes, como web beacons (também conhecidos como tags ou pixels), para permitir que você colete informações. Para obter mais informações sobre cookies e recursos de rastreamento com o Adobe Campaign, consulte [esta seção](#tracking-capabilities).
   * Você também pode usar as tecnologias da Adobe Experience Cloud em seus aplicativos móveis. Para obter mais informações sobre como enviar entrega móvel com o Campaign, consulte [canal SMS](../../delivery/using/sms-channel.md) e [canal de aplicativo móvel](../../delivery/using/about-mobile-app-channel.md).

* **As opções de privacidade dos usuários sobre o uso da Adobe Experience Cloud**

  A Adobe solicita que você forneça aos seus clientes políticas de privacidade descrevendo:

   * Suas práticas de privacidade em conexão com a Adobe Experience Cloud
   * Como os usuários podem definir suas preferências para a coleção ou usar suas informações em conexão com a Adobe Experience Cloud

  >[!NOTE]
  >
  >Quanto a todos os produtos da Adobe, os usuários do Campaign podem recusar o compartilhamento das informações coletadas sobre eles por meio de aplicativos e sites. Para obter mais informações, consulte as [Perguntas frequentes sobre o uso de informações com a Adobe Experience Cloud](https://www.adobe.com/br/privacy/experience-cloud-usage-info-faq.html).

Para obter mais detalhes sobre a privacidade da Adobe Experience Cloud, consulte [esta página](https://www.adobe.com/br/privacy/marketing-cloud.html).

## Dados pessoais e Personas {#personal-data}

Ao gerenciar a privacidade, é importante definir quais dados devem ser tratados com cuidado e por quem.
* **Dados pessoais** são informações que podem identificar direta ou indiretamente um indivíduo vivo.
* **Dados confidenciais pessoais** são informações relacionadas à raça, opiniões políticas, crenças religiosas, antecedentes criminais, informações genéticas, dados de saúde, preferência sexual e informações biométricas de uma pessoa física, bem como sua filiação sindical.

Ao integrar o Campaign a outras soluções da Experience Cloud, nas quais é possível transferir públicos-alvo de um sistema para outro, como o [Adobe Analytics](../../integrations/using/gs-aa.md), [Públicos-alvo da Experience Cloud](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md), [Campaign Standard](../../integrations/using/synchronizing-audiences.md) ou outras soluções que utilizam [conectores de CRM](../../platform/using/crm-connectors.md), tome bastante cuidado com a proteção de dados pessoais.

As [principais legislações](#privacy-regulations) referem-se às diferentes entidades que gerenciam os dados da seguinte forma:

* Um **Controlador de dados** é a autoridade que determina os meios e a finalidade de coleta, utilização e compartilhamento de dados pessoais.

* Um **Processador de dados** é qualquer pessoa física ou parte que coleta, utiliza ou compartilha dados pessoais, conforme determinado pelo Controlador de dados.

* Um **Titular de dados** é qualquer pessoa viva cujos dados pessoais estejam sendo coletados, utilizados ou compartilhados, e que possa ser identificada, direta ou indiretamente, por referência a esses dados pessoais.

Portanto, como uma empresa que coleta e compartilha dados pessoais, você é o Controlador de dados, seus clientes são os Titulares dos dados e o Adobe Campaign atua como um Processador de dados ao tratar os dados pessoais indicados por você. Observe que é sua responsabilidade como Controlador de dados, tratar a relação com os Titulares dos dados, como ao gerenciar [solicitações de privacidade](#privacy-requests).

### Cenário de caso de uso {#use-case-scenario}

Para ilustrar como as diferentes personalidades estão interagindo, veja um exemplo de um caso de uso de experiência de um cliente de GDPR de alto nível.

Neste exemplo, uma companhia aérea é o cliente do Adobe Campaign. Esta empresa é o **controlador de dados** e todos os clientes da companhia aérea são **titulares dos dados**. Laura, neste caso particular, é cliente da companhia aérea.

Aqui estão as diferentes personalidades usadas neste exemplo:

* **Laura** é a **titular dos dados**. Ela é o destinatário que recebe mensagens da companhia aérea. Laura pode ser uma passageira frequente, mas pode decidir a certa altura que não quer receber mensagens personalizadas com propaganda ou marketing da companhia aérea. Ela pedirá à companhia aérea (com base em seu processo) que exclua seu número de passageiro frequente.

* **Ana** é a **controladora de dados** da companhia aérea. Ela recebe a solicitação de Laura, recupera as IDs úteis solicitadas para identificar o titular dos dados e envia a solicitação no Adobe Campaign.

* O **Adobe Campaign** é o **operador de dados**.

![](assets/privacy-gdpr-flow.png)

Este é o fluxo geral para este caso de uso:

1. A **titular dos dados** (Laura) envia uma solicitação de GDPR para o **controlador de dados**, por email, via atendimento ao cliente ou um portal da web.

1. A **controladora de dados** (Ana) envia a solicitação de GDPR para o Campaign através da interface ou usando uma API.

1. Depois que o **operador de dados** (Adobe Campaign) receber as informações, executará então a solicitação do GDPR e enviará uma resposta ou uma confirmação à **controladora de dados** (Ana).

1. Em seguida, a **controlador de dados** (Ana) revisa as informações e as envia de volta para a **titular dos dados** (Laura).

## Aquisição de dados {#data-acquisition}

O Adobe Campaign permite coletar dados, inclusive informações pessoais e confidenciais. Portanto, é essencial que você receba e monitore o consentimento de seus destinatários.

* Tenha sempre o consentimento do destinatário para o recebimento de comunicações. Para fazer isso, continue atendendo às solicitações de recusa o mais rápido possível e verifique o consentimento por meio de um duplo processo de aceitação. Para obter mais informações, consulte [Criar um formulário de inscrição com dupla aceitação](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in).
* Não importe listas fraudulentas e utilize seed addresses para verificar se o arquivo do cliente não está sendo usado de forma fraudulenta. Para obter mais informações, consulte [Sobre seed addresses](../../delivery/using/about-seed-addresses.md).
* Por meio do gerenciamento de consentimento e direitos, você pode rastrear as preferências dos destinatários, bem como gerenciar quem em sua organização pode acessar quais dados. Para obter mais informações, consulte [esta seção](#consent).
* Facilite e gerencie solicitações de privacidade de seus destinatários. Para obter mais informações, consulte [esta seção](#privacy-requests).

## Gerenciamento de privacidade {#privacy-management}

O gerenciamento de privacidade está relacionado a todos os processos e ferramentas que podem ajudar você a cumprir as regras de privacidade (RGPD, CCPA, etc.). Obtenha uma visão geral do que é o gerenciamento de privacidade [nesta página](privacy-and-recommendations.md).

O Adobe Campaign oferece vários conjuntos de recursos dedicados ao gerenciamento de privacidade:
* Gerenciamento de consentimento, retenção de dados e funções de usuário. Consulte [esta seção](#consent).
* Solicitações de privacidade (Direito de acesso e Direito de ser esquecido). Consulte [esta seção](#privacy-requests).
* Recusar a venda de informações pessoais (específico para CCPA). Consulte [esta seção](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa).

Os principais recursos de privacidade do Campaign e um exemplo das personalidades envolvidas são apresentados nesta [seção](https://helpx.adobe.com/br/campaign/kb/campaign-privacy-more.html#gdprpersonasandflow).

### Consentimento, retenção e funções {#consent}

Originalmente, o Adobe Campaign oferece recursos importantes que são essenciais à privacidade:

* **Gerenciamento de consentimento**: por meio do processo de gerenciamento de assinaturas, você pode gerenciar suas preferências de destinatário e rastrear quais destinatários aceitaram e que tipo de assinatura. Para obter mais informações, consulte [Sobre assinaturas](../../delivery/using/about-services-and-subscriptions.md).
* **Retenção de dados**: todas as tabelas de registro padrão incorporadas têm períodos de retenção predefinidos, geralmente limitando seu armazenamento de dados a 6 meses ou menos. Períodos de retenção adicionais podem ser configurados com workflows. Para obter mais informações, entre em contato com os consultores ou administradores técnicos da Adobe.
* **Gerenciamento de direitos**: o Adobe Campaign oferece a capacidade de gerenciar os direitos atribuídos aos vários operadores do Campaign por meio de diferentes funções pré-concebidas ou personalizadas. Isso permite gerenciar quem em sua empresa pode acessar, modificar ou exportar diferentes tipos de dados. Para obter mais informações, consulte [Sobre o gerenciamento de acesso](../../platform/using/access-management.md).

Para obter mais informações sobre esses recursos e como gerenciá-los no Adobe Campaign, consulte [esta seção](../../platform/using/privacy-management.md#consent-retention-roles).

### Solicitações de privacidade {#privacy-requests}

O Adobe Campaign fornece recursos adicionais para ajudar você se tornar um Controlador de dados para determinadas Solicitações de privacidade:

* O **Direito de acesso** é o Direito do titular de dados de obter a confirmação do Controlador de dados, caso os dados relativos a ele estejam sendo processados, onde e com que finalidade.

* O **Direito ao esquecimento** (solicitação de exclusão) permite que o Titular dos dados tenha seus dados pessoais apagados pelo Controlador de dados.

As solicitações de **Acesso** e **Exclusão** são apresentadas [nesta seção](../../platform/using/privacy-management.md#right-access-forgotten).

As etapas de implementação para criar essas solicitações estão detalhadas nesta [seção](../../platform/using/privacy-requests.md).

## Recursos de rastreamento {#tracking-capabilities}

### Cookies {#cookies}

Graças às suas funcionalidades de rastreamento, o Adobe Campaign permite rastrear a navegação de destinatários de entrega usando três tipos de cookies: um cookie de sessão e dois cookies permanentes.

* Um cookie de **sessão**: o cookie **nlid** contém o identificador do email enviado ao contato (**broadlogId**) e ao identificador do modelo de mensagem (**deliveryId**). Ele é adicionado quando o contato clica em um URL incluído em um email enviado pelo Adobe Campaign e permite que você acompanhe seu comportamento na Web. Esse cookie de sessão é apagado automaticamente quando o navegador é fechado. O contato pode configurar o navegador para recusar cookies.

* Dois cookies **permanentes**:
   * O cookie **UUID** (Universal Unique IDentifier) é compartilhado entre as soluções da Adobe Experience Cloud. É definido uma vez até que desapareça do navegador do cliente quando um novo valor é gerado. Este cookie identifica os usuários que interagem com as soluções da Experience Cloud quando visitam um site. Ele pode ser depositado por uma landing page (para associar atividades desconhecidas do cliente a um destinatário) ou por uma entrega. A descrição deste cookie está disponível [nesta página](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-mc.html?lang=pt-BR#ec-cookies).
   * O cookie **nllastdelid** (introduzido no Campaign Classic 20.3) é um cookie permanente que contém o **deliveryId** da última entrega do qual o usuário clicou no link. Esse cookie é usado quando o cookie da sessão está ausente, para identificar a tabela de rastreamento que será usada.

Regulamentos como o Regulamento Geral sobre a Proteção de Dados (GDPR) afirmam que as empresas exigem o acordo dos usuários do site antes da instalação de qualquer cookie.

* Você deve informar aos usuários que seus sites estão equipados com ferramentas de rastreamento web por meio de uma solicitação de autorização (que aparece, por exemplo, sobre a página) com uma caixa de seleção que autoriza a utilização de cookies ou adicionando um banner na parte superior da primeira página, etc.
* As janelas pop-up devem ser evitadas, pois geralmente são bloqueadas pelos navegadores.

### Rastreamento de mensagens {#message-tracking}

O Adobe Campaign permite rastrear os emails enviados e o comportamento dos destinatário da entrega: abrir, clicar em links, cancelamento de assinatura, etc. Para obter mais informações, consulte [Sobre o rastreamento de mensagens](../../delivery/using/about-message-tracking.md).

Para fazer isso, adicione [links rastreados](../../delivery/using/how-to-configure-tracked-links.md) às suas mensagens para medir o impacto do comportamento da entrega e do destinatário na guia [Rastreamento](../../delivery/using/delivery-dashboard.md#tracking-logs) do painel da entrega. Os dados de rastreamento são interpretados no relatório de [Indicadores de rastreamento](../../reporting/using/delivery-reports.md#tracking-indicators).

### Rastreamento web {#web-tracking}

O Adobe Campaign também permite monitorar como os destinatários navegam em seu site: insira tag de rastreamento para coletar informações e medir visitas em páginas de aplicativos da Web. Para obter mais informações, consulte [Rastreamento de um aplicativo da web](../../web/using/tracking-a-web-application.md).

A configuração de rastreamento na web é apresentada [nesta seção](../../configuration/using/about-web-tracking.md).

Para gerenciar ainda mais o rastreamento, o Adobe Campaign permite exibir um banner de recusa de participação para interromper o rastreamento de comportamentos da web de usuários finais que recusam o rastreamento comportamental. Para obter mais informações, consulte [Recusa de rastreamento em aplicação web](../../web/using/web-application-tracking-opt-out.md).
