---
product: campaign
title: Gerenciamento de privacidade
description: Saiba mais sobre o Gerenciamento de privacidade
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 23c873fd-9016-4d32-842c-772cfff0e23e
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 100%

---

# Gerenciamento de privacidade {#privacy-management}

![](../../assets/common.svg)

O Adobe Campaign oferece um conjunto de ferramentas para ajudar você a cumprir as [regras de privacidade](#privacy-management-regulations) (incluindo GDPR, CCPA, PDPA, LGPD).

Estes são os cinco principais recursos oferecidos pelo Adobe Campaign para garantir a conformidade com o GDPR e outras regras de privacidade:
* **Direito de acesso**
* **Direito de exclusão**
* **Gerenciamento de consentimento**
* **Retenção de dados**
* **Gerenciamento de direitos**

![](assets/privacy-gdpr-use-cases.png)

Para obter mais informações, consulte [Direito de acesso e direito de ser esquecido](#right-access-forgotten) e [Consentimento, retenção e funções](#consent-retention-roles).

<!--This section presents general information on what Privacy management is and the features provided by Adobe Campaign to manage the [Right to Access and Right to be Forgotten](#right-access-forgotten).

It also contains information on important features to manage Privacy ([Consent, Retention and Roles](#consent-retention-roles)), as well as best practices to help you with your Privacy compliance when using Adobe Campaign.-->

## Regulamentos sobre o gerenciamento de privacidade {#privacy-management-regulations}

Os recursos do Adobe Campaign ajudam você a cumprir os seguintes requisitos:

* **O GDPR** ([Regulamento Geral sobre a Proteção de Dados](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en)) é a lei de privacidade da União Europeia (UE) que adequa e moderniza os requisitos de proteção de dados nos países membros da UE.
* **O CCPA** ([Ato de privacidade do consumidor da Califórnia](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=)) fornece aos residentes da Califórnia novos direitos no que diz respeito a suas informações pessoais e impõe responsabilidades de proteção de dados a determinadas entidades com negócios na Califórnia.
* O **PDPA** ([Ato de proteção de dados pessoais)](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) é a nova lei de privacidade que adequa e moderniza os requisitos de proteção de dados na Tailândia.
* **A LGPD** ([Lei Geral de Proteção de Dados](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf)) entrará em vigor no início de 2021 para todas as empresas que coletam ou processam dados pessoais no Brasil.

Todos esses regulamentos se aplicam a clientes do Adobe Campaign que detêm dados para residentes nas respectivas regiões ou países mencionados acima (UE, Califórnia, Tailândia e Brasil).

<!--Several Privacy capabilities are available in Adobe Campaign, including consent management, data retention settings, and rights management. See [Consent, Retention and Roles](#consent-retention-roles). In addition to this, Adobe Campaign helps facilitate your readiness as Data Controller for certain Privacy requests. See [Right to Access and Right to be Forgotten](#right-access-forgotten).-->

>[!NOTE]
>
>Para obter mais informações sobre dados pessoais e as diferentes entidades que gerenciam os dados (Controlador de dados, Operador de dados e Titular de dados), consulte [Dados pessoais e Personalidades](../../platform/using/privacy-and-recommendations.md#personal-data).

## Direito de acesso e Direito ao esquecimento {#right-access-forgotten}

Para facilitar a conformidade com a privacidade, o Adobe Campaign permite manipular solicitações de **Acesso** e **Exclusão**.

* O **Direito de acesso** é o direito do Titular de dados de obter a confirmação do Controlador de dados, caso os dados relativos a ele estiverem sendo processados, onde e com qual finalidade. O Controlador de dados deve fornecer uma cópia gratuita dos dados pessoais em formato eletrônico.

* Também conhecido como Eliminação de dados, o **Direito ao esquecimento** (solicitação de exclusão) permite que o Titular de dados tenha seus dados pessoais apagados pelo Controlador de dados, interrompendo a divulgação e, possivelmente, o processamento desses dados por parte de terceiros.

Para saber como criar solicitações de **Acesso** e **Exclusão** e como o Adobe Campaign as processa, consulte as [etapas de implementação](../../platform/using/privacy-requests.md).

<!--Tutorials on Privacy management in Campaign Standard are also available [here](https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/privacy/privacy-overview.html).
https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/privacy/privacy-overview.html?lang=en-->

## Consentimento, retenção e funções {#consent-retention-roles}

Além dos recursos mais recentes de **Direito de acesso** e **Direito ao esquecimento**, o Adobe Campaign oferece outros recursos importantes, essenciais para a privacidade:

* [Gerenciamento do consentimento](#consent-management): funcionalidade de assinatura para gerenciamento de preferências
* [Retenção de dados](#data-retention): períodos de retenção de dados em todas as tabelas de log padrão; períodos de retenção adicionais podem ser configurados com workflows
* [Gerenciamento de direitos](#rights-management): acesso a dados gerenciados por direito nomeado     

### Gerenciamento de consentimento {#consent-management}

Consentimento significa a aprovação do Titular dos dados para o tratamento de dados pessoais relativos à pessoa em questão. A obtenção de qualquer consentimento necessário para esse processamento é de responsabilidade do Controlador de Dados. Embora o Adobe Campaign forneça alguns recursos para ajudar o cliente a gerenciar o consentimento relacionado ao serviço, o Adobe não é responsável pelo consentimento. Os clientes devem trabalhar com os próprios serviços jurídicos para determinar seus próprios processos e práticas para qualquer consentimento necessário.

Os recursos para ajudar a gerenciar alguns aspectos do consentimento são fundamentais para o Adobe Campaign desde o início. Por meio do nosso processo de gerenciamento de assinatura, os clientes podem acompanhar quais recipients participaram de quais tipos de assinatura, sejam boletins informativos, promoções diárias ou semanais ou qualquer outro tipo de programa de marketing.

![](assets/privacy-consent-management.png)

Para obter mais informações sobre o Gerenciamento de consentimento, consulte a [documentação detalhada](../../delivery/using/managing-subscriptions.md).

Além das ferramentas de Gestão do consentimento oferecidas pelo Adobe Campaign, você tem a possibilidade de monitorar a opção do cliente pela recusa da venda de informações pessoais.
Consulte [esta seção](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa).

### Retenção de dados {#data-retention}

Quanto à retenção, as tabelas de log integradas no Campaign têm períodos de retenção predefinidos, geralmente limitando o armazenamento dos dados a seis meses ou menos.

A seguir estão os valores de retenção padrão para tabelas integradas. Esteja ciente de que a configuração de retenção é definida pelos administradores técnicos da Adobe durante a implementação e os valores podem variar com base nos requisitos do cliente.

* **Rastreamento consolidado**: 1 ano
* **Registros de entrega**: 6 meses
* **Logs de rastreamento**: 1 ano
* **Deliveries excluídos**: 1 semana
* **Importação de rejeitos**: 6 meses
* **Perfis do visitante**: 1 mês
* **Apresentações da oferta**: 1 ano
* **Eventos**: 1 mês
* **Estatísticas de processamento de evento**: 1 ano
* **Eventos arquivados**: 1 ano
* **Eventos de pipeline ignorados**: 1 mês

Assim como excluir, usando a funcionalidade padrão do workflow, é possível configurar períodos de retenção para qualquer tabela personalizada.

Entre em contato com os consultores da Adobe ou administradores técnicos para saber mais sobre retenção ou se é necessário definir a retenção para tabelas personalizadas.

### Gerenciamento de direitos {#rights-management}

O Adobe Campaign oferece a capacidade de gerenciar os direitos atribuídos aos vários operadores do Campaign por meio de diferentes funções pré-concebidas ou personalizadas.

Um dos benefícios é permitir a gestão da decisão sobre quem poderá acessar os diferentes tipos de dados na empresa. Por exemplo, é possível ter diferentes profissionais de marketing que cubram diversas regiões e cada um deles só poderá acessar os dados da sua região geográfica.

Da mesma forma, essa funcionalidade também permite a configuração de diferentes recursos para cada usuário, como limitar quem pode enviar deliveries, ou algo mais relevante para o Gerenciamento de privacidade, como quem pode alterar ou exportar dados.

![](assets/privacy-user-management.png)

Para obter mais informações sobre o gerenciamento de acesso, consulte a [documentação detalhada](../../platform/using/access-management.md).
