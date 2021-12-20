---
product: campaign
title: Fim da vida útil do suporte para TLS 1.0 e 1.1
description: Fim da vida útil do suporte para TLS 1.0 e 1.1
audience: delivery
content-type: reference
topic-tags: tracking-messages
source-git-commit: 70240d5f62fd3d7b755389b5ad8c4b499c94657d
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 1%

---

# Fim da vida útil do suporte para TLS 1.0 e 1.1{#eol-tls-support}

![](../../assets/v7-only.svg)

O Adobe não oferece mais suporte a sistemas de usuários e sistemas clientes que não são compatíveis com o protocolo TLS 1.2. Se você continuar usando versões mais antigas do TLS, poderá perder o acesso a todos os produtos e serviços do Adobe.

## Por que estou vendo esta página?

Caso veja a seguinte mensagem: **Esta página não pode ser exibida**, isso significa que os aplicativos do Adobe, a página da Web ou o serviço que você está tentando acessar exigem uma conexão de rede mais segura com seu navegador da Web, sistema operacional ou aplicativo. É obrigatório usar **TLS 1.2** para comunicações seguras de rede e intercâmbio de dados entre sistemas de usuários, aplicativos Adobe e serviços da Web.

O Adobe substituiu o suporte para versões inferiores do TLS (incluindo TLS 1.0 e 1.1). Para obter detalhes técnicos sobre o protocolo TLS 1.2, consulte [Perguntas frequentes](#faq).

## O que posso fazer para retomar o serviço?

Navegadores da Web modernos são compatíveis com TLS 1.2. Atualizar seu navegador pode permitir que você acesse esses aplicativos e serviços.

Você pode baixar e instalar um dos seguintes navegadores populares:

* [Google Chrome](https://www.google.com/chrome/)
* [Apple Safari](https://www.apple.com/safari/)
* [Firefox](https://www.mozilla.org/en-US/firefox/new/)
* [Microsoft Edge](https://www.microsoft.com/en-us/edge)

Se estiver usando outro navegador, verifique se ele é compatível com TLS 1.2.

Seu sistema operacional e estruturas de aplicativo também devem ser compatíveis com TLS 1.2. Se a atualização do navegador não resolver o problema, verifique se o computador atende aos requisitos de sistema listados em [Matriz de compatibilidade de campanha](../../rn/using/compatibility-matrix.md).

## Perguntas frequentes{#faq}

* **O que é a Segurança da camada de transporte (TLS)?**

   [Segurança da camada de transporte](https://en.wikipedia.org/wiki/Transport_Layer_Security) (TLS) é um protocolo de segurança que fornece privacidade e integridade de dados entre dois aplicativos de comunicação. Ele é amplamente implantado em navegadores da Web e outros aplicativos que exigem o intercâmbio seguro de dados em uma rede.

   De acordo com a especificação do protocolo, o TLS inclui duas camadas, o protocolo TLS Record e o protocolo TLS Handshake. O protocolo Record fornece segurança de conexão. O protocolo Handshake permite que o servidor e o cliente se autentiquem e negoceiem algoritmos de criptografia e chaves criptográficas antes da troca de dados.

* **Qual é o impacto?**

   A partir de maio de 2018, os padrões de conformidade do Adobe exigem a desativação dos protocolos mais antigos e o uso do TLS 1.2 como a versão atualizada. Se o seu sistema não for compatível com TLS 1.2, o acesso a alguns aplicativos e serviços do Adobe é restrito.

* **Como o TLS afeta você?**

   Você só pode se envolver com alguns aplicativos e serviços do Adobe por meio de uma conexão de rede segura. O TLS ajuda a garantir que a conexão entre seu navegador e esses aplicativos e serviços da Web seja segura e confiável.

   À medida que novos navegadores e sistemas operacionais são lançados, os padrões de segurança são atualizados para garantir níveis mais altos de privacidade e integridade dos dados. No entanto, versões mais antigas desses navegadores ou SO não são atualizadas para incluir os padrões mais recentes.

   À medida que o nível aceitável de segurança aumenta, essas versões e aplicativos mais antigos e menos seguros do navegador são deixados para trás.

   Para se conectar a sites seguros, atualize as versões do sistema operacional e do navegador.

* **O TLS é vulnerável a hackers?**

   Houve ataques documentados contra o TLS 1.0 usando um método de criptografia mais antigo e as versões mais antigas são mais vulneráveis do que o TLS 1.2. Para obter mais informações, consulte Ataques contra TLS/SSL.

* **Por que o Adobe está desativando o suporte para TLS 1.0 e 1.1?**

   O Adobe tem padrões de conformidade de segurança que exigem a desativação do suporte para protocolos mais antigos. Um desses padrões garante a conformidade com o PCI (Payment Card Industry, setor de cartões de pagamento). O servidor de adaptação PCI é um conjunto de padrões de segurança que exigem que as organizações aceitem, processem, armazenem ou transmitam informações de cartão de crédito para manter um ambiente seguro.

   A conformidade com a PCI exige o uso do TLS 1.1 ou superior a partir de maio de 2018.

* **Por que o Adobe está mandando o uso do TLS 1.2 em vez de permitir o TLS 1.1 ou o TLS 1.0?**

   A maioria das solicitações de aplicativos e serviços da Web do Adobe é proveniente de sistemas de usuários compatíveis com TLS 1.2, com tráfego baixo de sistemas TLS 1.1.

   O Adobe migrou para o TLS 1.2 para que seus aplicativos e serviços da Web sejam acessados com mais segurança.

* **Qual é a última data em que posso usar uma versão mais antiga do TLS?**

   O Adobe incentiva os usuários a abandonarem rapidamente as versões mais antigas para evitar a exposição a vulnerabilidades de segurança. Para obter mais informações, entre em contato com o Atendimento ao cliente do Adobe ou com o gerente de sucesso do cliente.

* **Qual mensagem de erro aparece se eu usar um navegador não configurado para TLS 1.2?**

   Depende do navegador que você está usando. Todos os navegadores mencionados em [Matriz de compatibilidade de campanha](../../rn/using/compatibility-matrix.md) são configuradas para usar o TLS 1.2. Se estiver usando um navegador ou versão que não figura na lista, atualize seu navegador.

   O Adobe não controla mensagens de erro geradas pela camada de comunicações SSL. O navegador gera essas mensagens antes de se conectar aos aplicativos e serviços do Adobe. Este é um exemplo de erro que pode ocorrer com o Internet Explorer 11 no Windows 7:

   ![](assets/do-not-translate/page-not-displayed.png)

   O TLS 1.2 é ativado no Internet Explorer 11 por padrão, mas se estiver desativado, você pode ativá-lo. Nesse caso, ative o TLS 1.2 na caixa de diálogo de configurações avançadas, em vez de usar outras opções. Outros erros, como os seguintes, também podem ocorrer:

   * Não é possível ligar ao serviço
   * Serviço não disponível
   * Erro na conexão
