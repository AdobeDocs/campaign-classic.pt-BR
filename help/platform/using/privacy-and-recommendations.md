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
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 33bf5c5a08613cf88eaace91b85a76157cac7ba1

---


# Privacidade e recomendações{#privacy-and-recommendations}

## Sobre privacidade e consentimento {#about-privacy-and-consent}

O Adobe Campaign é uma ferramenta poderosa para coletar e processar quantidades extremamente grandes de dados, incluindo informações pessoais. Recomendamos que todos os usuários do Adobe Campaign trabalhem dentro da legislação (DPA, CAN-SPAM, Diretiva Europeia sobre Privacidade e Comunicações eletrônicas, GDPR da Europa, CCPA etc.), façam uso responsável e ético de informações pessoais e evitem o envio de mensagens de email, notificações por push e mensagens SMS não solicitadas (&quot;spam&quot;). Acreditamos fortemente nos princípios da permissão de marketing para promover o valor e a fidelidade do cliente e, portanto, é estritamente proibido o uso do Adobe Campaign para o envio de mensagens não solicitadas.

Para obter mais informações, consulte a [privacidade da Adobe Experience Cloud](https://www.adobe.com/br/privacy/marketing-cloud.html).

Reserve tempo para acessar a lista de [Verificação de segurança e privacidade](https://helpx.adobe.com/br/campaign/kb/acc-security.html) e conhecer seus principais elementos.

## Gerenciamento de privacidade {#privacy-management}

O RGPD (Regulamento Geral sobre a Proteção de Dados) é a lei de privacidade da União européia (EU) que harmoniza e moderniza os requisitos de proteção de dados. O GDPR aplica-se aos clientes do Adobe Campaign que coletam dados de residentes da UE.

A CCPA (Lei de privacidade do consumidor da Califórnia) fornece aos residentes da Califórnia novos direitos no que diz respeito a suas informações pessoais e impõe responsabilidades de proteção de dados a determinadas entidades com negócios na Califórnia.

Além do gerenciamento de consentimento, das configurações de retenção de dados e do gerenciamento de direitos, fornecemos, na nossa função de Processador de dados, recursos adicionais para ajudar a facilitar sua condição de Controlador de dados para certas solicitações de Privacidade.

Neste [artigo](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html), você aprenderá como o Adobe Campaign ajuda a gerenciar os diferentes recursos da chave de privacidade: Direito de acesso, direito de ser esquecido, consentimento, retenção de dados e funções de usuário. Você também encontrará as práticas recomendadas para ajudar você a estar em conformidade com a privacidade ao usar nosso serviço.

## Cookies e recursos de rastreamento {#cookies-and-tracking-capabilities}

Graças às suas funcionalidades de rastreamento, o Adobe Campaign permite que você rastreie a navegação dos seus destinatários de entregas em um site. Para fazer isso, o Adobe Campaign usa cookies de sessão e cookies permanentes.

A diretiva europeia 2009/136/CE em &quot;Privacidade e Comunicações eletrônicas&quot; e o Regulamento Geral sobre a Proteção de Dados (GDPR) da Europa declaram que as empresas precisam ter o consentimento dos usuários do site antes da instalação de quaisquer cookies. Você deve informar aos usuários que seus sites estão equipados com ferramentas de rastreamento Web por meio de uma solicitação de autorização (que aparece sobre a página, por exemplo) com uma caixa de seleção para permitir a instalação de cookies ou adicionar um anúncio na parte superior da primeira página. Janelas pop-up devem ser evitadas, pois são frequentemente bloqueadas pelos navegadores.

A configuração da gestão do rastreamento de usuários está disponível para os aplicativos da Web e para as páginas de aterrissagem com um banner para descadastramento. Consulte [esta página](../../web/using/web-application-tracking-opt-out.md).

O Adobe Campaign usa dois tipos de cookies:

1. Um cookie de sessão (nlid): contém o identificador do e-mail enviado ao contato (broadlogId) e o identificador do modelo de mensagem (deliveryId). Ele é adicionado quando o contato clica em uma URL incluída em um e-mail enviado pelo Adobe Campaign e permite que você acompanhe seu comportamento na Web. Esse cookie de sessão é apagado automaticamente quando o navegador é fechado. O contato pode configurar o navegador para recusar cookies.
1. Um cookie permanente (uuid230): permite que você identifique os usuários que interagem com o Adobe Campaign ao visitarem um site. Ele é usado pelo Adobe Campaign para contar o número de cliques e estimar a taxa de transferência durante uma campanha de marketing. Ele é inserido quando o contato clica em um e-mail, preenche um formulário no Adobe Campaign ou durante a chamada para o mecanismo de interação de entrada. O usuário pode configurar o navegador para excluí-lo ou recusá-lo.

## Integridade do banco de dados {#database-integrity}

O Adobe Campaign tem muitos recursos. Portanto, ele usa uma complexa estrutura de banco de dados. O banco de dados contém muitas tabelas, campos, links e índices. Algums tabelas intermediárias não são exibidas na interface. O software cria, exclui ou modifica automaticamente determinados links, campos e índices. Somente as interfaces do Adobe Campaign (interface gráfica, programa de importação, módulo de servidor, módulo da Web, servidores de entrega, adição de campo, extensão de banco de dados, etc.) podem modificar o conteúdo do banco de dados e, ao mesmo tempo, preservar sua integridade.

**Nunca modifique o conteúdo ou a estrutura do banco de dados usando qualquer outra ferramenta que não seja esse software**. É muito provável que essas modificações corrompam o banco de dados, resultando em: modificação acidental ou perda de links, criação de registros ou links fantasmas, mensagens de erros graves, etc. Além disso, elas anulam a garantia e o contrato de suporte técnico fornecidos pelo Adobe Campaign.

No sistema Adobe Campaign, todas as informações são armazenadas no banco de dados. A operação adequada de todo o sistema Adobe Campaign depende da disponibilidade desses dados para: módulos da Web para assinatura, administração e cancelamento de assinaturas, telas de administração, filas de entrega, mecanismos de otimização de entregas etc.

## Apache Tomcat {#apache-tomcat}

O Adobe Campaign inclui o Apache Tomcat, desenvolvido pela Apache Software Foundation ([https://www.apache.org/](https://www.apache.org/)).
