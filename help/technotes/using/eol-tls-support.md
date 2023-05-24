---
product: campaign
title: Fim da vida útil do suporte para TLS 1.0 e 1.1
description: Fim da vida útil do suporte para TLS 1.0 e 1.1
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: e18d43b6-2a77-4881-85e7-ca36248d4634
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---

# Fim da vida útil do suporte para TLS 1.0 e 1.1{#eol-tls-support}



O Adobe não é mais compatível com sistemas de usuários e sistemas de clientes que não são compatíveis com o protocolo TLS 1.2. Se você continuar a usar versões mais antigas do TLS, poderá perder o acesso a todos os produtos e serviços da Adobe.

## Por que estou vendo esta página?

Se você vir a seguinte mensagem: **Esta página não pode ser exibida**, isso significa que os aplicativos Adobe, a página da Web ou o serviço que você está tentando acessar exigem uma conexão de rede mais segura com seu navegador da Web, sistema operacional ou aplicativo. É obrigatório usar **TLS 1.2** para comunicações seguras em rede e troca de dados entre sistemas de usuários e aplicativos e serviços da web para o Adobe.

O Adobe descontinuou o suporte para versões anteriores do TLS (incluindo TLS 1.0 e 1.1). Para obter detalhes técnicos sobre o protocolo TLS 1.2, consulte [Perguntas frequentes](#faq).

## O que posso fazer para retomar o serviço?

Os navegadores da Web modernos são compatíveis com TLS 1.2. A atualização do navegador pode permitir que você acesse esses aplicativos e serviços.

Você pode baixar e instalar um dos seguintes navegadores populares:

* [Google Chrome](https://www.google.com/chrome/)
* [Apple Safari](https://www.apple.com/safari/)
* [Firefox](https://www.mozilla.org/en-US/firefox/new/)
* [Microsoft Edge](https://www.microsoft.com/en-us/edge)

Se você estiver usando outro navegador, verifique se ele é compatível com TLS 1.2.

O sistema operacional e as estruturas de aplicativo também devem ser compatíveis com TLS 1.2. Se atualizar o navegador não resolver o problema, verifique se o computador atende aos requisitos de sistema listados na [Matriz de compatibilidade do Campaign](../../rn/using/compatibility-matrix.md).

## Perguntas frequentes{#faq}

* **O que é TLS (Transport Layer Security)?**

   [Segurança da camada de transporte](https://en.wikipedia.org/wiki/Transport_Layer_Security) O (TLS) é um protocolo de segurança que fornece privacidade e integridade de dados entre dois aplicativos de comunicação. Ele é amplamente implantado para navegadores da Web e outros aplicativos que exigem que os dados sejam trocados com segurança em uma rede.

   De acordo com a especificação do protocolo, o TLS inclui duas camadas, o protocolo de Registro TLS e o protocolo de Interação TLS. O protocolo Record oferece segurança de conexão. O protocolo Handshake permite que o servidor e o cliente se autentiquem e negociem algoritmos de criptografia e chaves criptográficas antes da troca de dados.

* **Qual é o impacto?**

   Os padrões de conformidade de segurança do Adobe exigem a desativação de protocolos mais antigos a partir de maio de 2018 e exigem o uso do TLS 1.2 como a versão atualizada. Se o seu sistema não for compatível com TLS 1.2, o acesso a alguns aplicativos e serviços do Adobe será restrito.

* **Como o TLS afeta você?**

   Você só pode se envolver com alguns aplicativos e serviços Adobe por meio de uma conexão de rede segura. O TLS ajuda a garantir que a conexão entre seu navegador e esses aplicativos e serviços da Web seja segura e confiável.

   À medida que novos navegadores e sistemas operacionais são lançados, os padrões de segurança são atualizados para garantir níveis mais altos de privacidade e integridade dos dados. No entanto, as versões mais antigas desses navegadores ou SO não são atualizadas para incluir os padrões mais recentes.

   À medida que o nível aceitável de segurança aumenta, essas versões e aplicativos mais antigos e menos seguros do navegador são deixados para trás.

   Para poder se conectar com sites seguros, atualize o sistema operacional e as versões do navegador.

* **O TLS é vulnerável a hackers?**

   Há ataques documentados contra TLS 1.0 usando um método de criptografia mais antigo e as versões mais antigas são mais vulneráveis que o TLS 1.2. Para obter mais informações, consulte Ataques contra TLS/SSL.

* **Por que o Adobe está desabilitando o suporte para TLS 1.0 e 1.1?**

   O Adobe tem padrões de conformidade de segurança que exigem a desativação do suporte para protocolos mais antigos. Um desses padrões garante a conformidade com o PCI (Payment Card Industry, setor de cartões de pagamento). O servidor de adaptação PCI é um conjunto de padrões de segurança que exigem que as organizações aceitem, processem, armazenem ou transmitam informações de cartão de crédito para manter um ambiente seguro.

   A conformidade com o PCI exige o uso do TLS 1.1 ou superior a partir de maio de 2018.

* **Por que o Adobe está exigindo o uso de TLS 1.2 em vez de permitir TLS 1.1 ou TLS 1.0?**

   A maioria das solicitações de aplicativos e serviços da Web para Adobe são originados de sistemas de usuários compatíveis com TLS 1.2, com baixo tráfego de sistemas TLS 1.1.

   O Adobe migrou para TLS 1.2 para que seus aplicativos e serviços da Web sejam acessados com mais segurança.

* **Qual é a última data em que posso usar uma versão mais antiga do TLS?**

   O Adobe incentiva os usuários a abandonarem rapidamente as versões mais antigas para evitar a exposição a vulnerabilidades de segurança. Para obter mais informações, entre em contato com o Atendimento ao cliente da Adobe ou com o gerente de sucesso do cliente.

* **Que mensagem de erro será exibida se eu usar um navegador não configurado para TLS 1.2?**

   Depende do navegador que você está usando. Todos os navegadores mencionados em [Matriz de compatibilidade do Campaign](../../rn/using/compatibility-matrix.md) são configurados para usar TLS 1.2. Se você estiver usando um navegador ou uma versão que não consta na lista, atualize o navegador.

   O Adobe não controla as mensagens de erro geradas pela camada de comunicações SSL. O navegador gera essas mensagens antes de se conectar a aplicativos e serviços Adobe. Este é um exemplo de erro que pode ocorrer com o Internet Explorer 11 no Windows 7:

   ![](assets/do-not-translate/page-not-displayed.png)

   O TLS 1.2 está habilitado no Internet Explorer 11 por padrão, mas se estiver desativado, você poderá ativá-lo. Nesse caso, ative o TLS 1.2 na caixa de diálogo de configurações avançadas em vez de usar outras opções. Outros erros, como os seguintes, também podem ocorrer:

   * Não é possível conectar-se ao serviço
   * Serviço indisponível
   * Erro na conexão
