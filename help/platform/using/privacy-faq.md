---
solution: Campaign Classic
product: campaign
title: Privacidade e consentimento
description: Saiba mais sobre privacidade e consentimento
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: ht
source-git-commit: 9e31f69fde38dcdc7f4e6d3ba3fb17911f96ded8
workflow-type: ht
source-wordcount: '808'
ht-degree: 100%

---


# Perguntas frequentes sobre privacidade {#privacy-faq}

Estas são algumas das perguntas frequentes sobre privacidade e consentimento ao usar o Adobe Campaign.

## Termos principais {#key-terms}

**Quais são os termos principais sobre privacidade?**

Os itens listados abaixo vinculam-se aos principais termos e conceitos relacionados à privacidade e consentimento no Adobe Campaign:

* [Regulamentos sobre a gestão da privacidade](../../platform/using/privacy-management.md#privacy-management-regulations)
* [Dados pessoais e personalidades](../../platform/using/privacy-and-recommendations.md#personal-data)
* [Direito de acesso e Direito ao esquecimento](../../platform/using/privacy-management.md#right-access-forgotten)
* [Consentimento, retenção e funções](../../platform/using/privacy-management.md#consent-retention-roles)

## Preparação para as regras de privacidade {#privacy-regulations-readiness}

**Qual é a sugestão do Adobe Campaign para cumprir com as mais recentes regulamentações de privacidade?**

A Adobe não presta aconselhamento jurídico. Você deve consultar seu próprio serviço jurídico para garantir que sejam tomadas todas as medidas necessárias para o GDPR, CCPA, PDPA, LGPD ou qualquer outra preparação para regulamentação aplicável.

**Prepare-se para solicitações de acesso e exclusão de dados**

* Identifique um processo para receber/responder às solicitações do titular de dados, incluindo a nomeação de um ponto de contato de privacidade.

* Revise os vários dados do cliente armazenados no Adobe Campaign e determine identificadores exclusivos (provavelmente haverá mais de um).

* Determine uma política e um processo de validação/autenticação para confirmar a identidade do titular dos dados.

* Verifique se a resposta do titular dos dados é facilmente compreensível.

**Considere o consentimento**

* Relacione e atualize, conforme necessário, todos os pontos de contato para captar dados para o GDPR (ou seja, considere o idioma, o mecanismo de consentimento e os logs de consentimento).

* Certifique-se de que todos os emails de marketing incluam os links para o cancelamento da inscrição.

* Avalie a estratégia global de marketing por email para determinar implementações específicas da localidade geográfica.

**Entenda seus dados**

* Revise todas as fontes de importação e captura de dados nas quais os dados fluem para o Adobe Campaign e registre quais campos estão sendo usados para suas iniciativas de marketing.

* Remova todos os atributos de dados não utilizados do banco de dados do Adobe Campaign.

* Use os dados disponíveis no Adobe Campaign cuja intenção tenha sido capturada e ofereça a seus recipients experiências mais customizadas.

* Revise e atualize as permissões de acesso aos dados para garantir que os usuários do Adobe Campaign possam aproveitar totalmente apenas os dados necessários para executar suas campanhas, sem acessar nenhum outro dado.

* Certifique-se de que cada usuário do Adobe Campaign tenha os direitos de acesso apropriados para executar as tarefas necessárias, mas não tenha outros direitos para a execução de tarefas adicionais.

## Preservar o engajamento do usuário {#preserve-user-engagement}

**Como os controladores de dados podem obter consentimento causando o mínimo de impacto no engajamento do usuário?**

Nos casos em que seja necessário o consentimento para determinadas atividades de marketing, o consentimento do consumidor terá de estar ativo (ou seja, sem o silenciamento da caixa de aprovação ou pré-seleção), desagregado e poderá não estar sujeito à oferta dos serviços.

Pode até haver casos em que certos consentimentos precisem ser atualizados para que possam continuar usando os dados a partir de agora.

Em vez de pensar nos requisitos de consentimento aprimorados como um risco para o universo comercializável, os profissionais de marketing poderiam adotá-los como um verdadeiro indicador de engajamento e lealdade com a marca, assim como da satisfação e confiança do cliente.

## Gerenciar o consentimento {#manage-consent}

**Como os controladores de dados podem gerenciar o consentimento no Adobe Campaign?**

O Adobe Campaign já oferece recursos para gerenciar o consentimento em mais níveis do que a maioria dos profissional de marketing por meio de campos de dados personalizados ou por meio de um ou mais serviços.

Os profissionais de marketing devem consultar o serviço jurídico para obter orientação sobre como proceder e usar os recursos já incorporados ao Adobe Campaign.

Por exemplo, estender o modelo de dados no Adobe Campaign para rastrear não apenas o consentimento, mas também o registro de data e hora da aceitação, e algum tipo de indicador que capture o escopo preciso do consentimento.

## Exclusão de dados {#data-deletion}

**Quais dados os controladores de dados podem excluir no Adobe Campaign em resposta a uma solicitação do cliente por um titular dos dados?**

Todos os dados associados ao titular dos dados serão excluídos, incluindo tabelas predefinidas e personalizadas.

Tecnicamente, todos os dados vinculados ao titular dos dados com `integrity="own"` serão excluídos.

Como Controlador de dados, você tem a opção de personalizar alterando a integridade dos links definidos nos esquemas de dados (por exemplo, caso tenha uma justificativa comercial para não excluir determinados dados).

**O que muda nos relatórios quando o delivery e os logs de rastreamento são excluídos?**

Os relatórios do Adobe Campaign são baseados em indicadores computados em dados agregados de delivery e logs de rastreamento. Como resultado, a remoção de registros individuais não deve afetar as métricas exibidas nos relatórios.

## Reimportar dados {#re-import-data}

**Muitas vezes no Adobe Campaign, o registro é carregado a partir de uma fonte externa de dados. Preciso ter cuidado com a possibilidade de reimportar dados posteriormente?**

A partir do recebimento de uma solicitação de exclusão, o Controlador de dados precisará garantir a exclusão de todos os dados necessários sobre o titular dos dados de todos os sistemas.

## Aceitar novamente {#opt-in-again}

**Um titular de dados cujos dados tenham sido cancelados no Adobe Campaign pode ser aceito novamente?**

É possível que um titular de dados faça a adesão novamente ou seja adicionado como um novo recipient depois que seus dados tenham sido cancelados do Adobe Campaign.

Você pode usar a trilha de auditoria que detalha quando a exclusão anterior foi executada e quando o novo recipient foi criado.