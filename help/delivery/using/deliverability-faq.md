---
title: Pontos principais ao gerenciar a capacidade de delivery no Adobe Campaign Classic
description: Quais são os principais pontos a serem verificados ao gerenciar a capacidade de delivery no Adobe Campaign Classic?
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 15581517df8d2f397285bbadebd83b7f4539dfd7
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 11%

---


# Solução de problemas de entrega{#deliverability-faq}

Você está enfrentando um problema de entrega? Você pode encontrar a solução aqui.

## Erro de regra MX {#mx-rule-error}

**O que significa a mensagem de erro &quot;Quotas atendidas&quot;?**

Esta mensagem indica que você atingiu o limite de cota de um MX específico e que precisa aguardar para poder enviar outro email para esse provedor.

No Adobe Campaign, há uma configuração sobre o número de emails por hora que podem ser enviados. Essa configuração deve ser usada com cuidado, pois o número definido na instância diz respeito ao número de conexões realizadas com o ISP e não o número de emails realmente enviados.

Isso significa que uma conexão pode usar uma regra MX sem enviar um email com êxito. Nesse caso, uma configuração com um IP ou um domínio com pouca reputação terá de tentar várias conexões antes de enviar um email. Para cada tentativa, será usado um crédito de mensagens por hora. Como resultado, o desempenho da campanha de marketing será significativamente afetado.

Portanto, &quot;quotas cumpridas&quot; não é apenas uma questão de configuração, mas também pode estar ligada à reputação. It is important to analyze error messages in the [SMTP log](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

For more on MX configuration, see [this section](../../installation/using/email-deliverability.md#mx-configuration).

## Mesma mensagem de erro para um ISP {#same-error-for-an-isp}

**Por que recebo sempre a mesma mensagem de erro para um provedor de serviços específico?**

Se você receber sempre a mesma mensagem de erro para um ISP, seu email ou IP pode ter sido detectado como defeituoso pelo ISP. Execute as seguintes recomendações:
* Verifique se você recebe uma grande porcentagem de falhas vinculadas a endereços de email inexistentes (falhas desconhecidas **do** usuário).
* Atualize seus formulários de subscrição para detectar quaisquer erros nos nomes de domínio inseridos (por exemplo: gmaul.com ou yaho.com).
* Se você notar erros que indicam que suas mensagens são declaradas como spam, ou que suas mensagens estão constantemente bloqueadas, tente excluir os recipient que não abriram ou clicaram em uma de suas mensagens nos últimos 12 meses a partir do público alvo.

Se o problema persistir, entre em contato com os serviços comerciais ou de entrega, com o Adobe Campaign Client Care ou com o suporte ao Adobe Campaign.

## Listas negras versus quarentenas {#blacklisting-versus-quarantine}

* **Qual é a diferença entre um endereço de email incluído na blacklist e um endereço de email em quarentena?**

   * O status **[!UICONTROL Blacklisted]** é resultado de um ciclo de feedback (quando uma pessoa reporta uma mensagem como spam).

   * O status **[!UICONTROL Quarantined]** é resultado de um salto suave ou forte.
   Para obter mais informações, consulte [esta seção](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-blacklisting).

* **O que significam os diferentes motivos de erro de quarentena?**

   Aqui estão 10 possíveis motivos: não definido, usuário desconhecido, domínio inválido, endereço incluído na blacklist, recusado, erro ignorado, inacessível, conta desativada, caixa de correio cheia, não conectado.

   For more on this, see [Understanding quarantine management](../../delivery/using/understanding-quarantine-management.md).

## Sem lista negra {#unblacklisting}

* **Um dos meus recipient foi incluído na blacklist por engano. Como faço para desfazer a lista negra deles para que eu possa start de enviar mensagens para eles novamente?**

   * Vá para **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * Nos detalhes do registro correspondente, defina o valor do **[!UICONTROL Status]** campo como **[!UICONTROL Valid]**.
   * Salve o registro.

* **Como posso descobrir se um dos meus IPs é incluído na blacklist? Como faço para desfazer a lista negra de meus IPs?**

   Para verificar se seu endereço IP é incluído na blacklist, você pode usar vários sites para verificá-lo:
   * [https://mxtoolbox.com/](https://mxtoolbox.com/)
   * [https://whatismyipaddress.com/blacklist-check](https://whatismyipaddress.com/blacklist-check)
   * [https://www.blacklistalert.org/](https://www.blacklistalert.org/)
   Geralmente, o resultado da verificação de endereço IP retornará uma lista que contém detalhes da lista negra e também o nome do site que incluído na blacklist o endereço IP.

   Ao clicar no link correspondente, você pode acessar os detalhes do site. Em seguida, você pode solicitar que seu site seja excluído do site que incluído na blacklist o endereço IP.

   >[!NOTE]
   >
   >O processo de exclusão pode variar dependendo do site. Alguns sites exigem que você crie uma conta, enquanto outros precisam apenas que você forneça o endereço IP.

## Práticas recomendadas {#best-practices}

Abaixo estão algumas práticas recomendadas que podem ajudar a identificar e solucionar problemas de entrega.

### Identificar um problema de entrega {#identify-deliverability-issue}

Os seguintes elementos podem chamar a sua atenção:

* Métricas de correspondência ou campanha: cancelar a inscrição, abusar da reclamação e/ou das taxas de rejeição são mais altas do que o normal.
* atividade do assinante: for aberto, os cliques e/ou as transações forem menores do que o normal.
* As contas de semente mostram as correspondências filtradas ou não entregues.

### Hipóteses de possíveis causas {#potential-causes}

Faça as seguintes perguntas para identificar as possíveis causas para o problema de entrega:

* Houve uma mudança recente na segmentação de listas?
* Adquirei novas fontes de dados?
* Eu enviei acidentalmente um arquivo de quarentena?
* O problema pode ser devido ao conteúdo da minha mensagem?
* É frequente enviar emails com frequência suficiente para manter IPs aquecidos?
* Estou segmentando minhas mensagens por atividade/envolvimento ou enviando arquivos completos?
* Qual é o segmento &quot;seguro&quot; no meu arquivo em termos de recenticidade?
* Tenho estratégias de reativação e reconfirmação em vigor para segmentos que não estão definidos como seguros?

### Resolver o problema {#address-issue}

**Reclamações**

As reclamações são definidas por assinantes que **relatam emails como spam** ao pressionar o botão correspondente em sua caixa de entrada.

Se o problema com seu delivery foi causado por reclamações:
* Você precisa tentar determinar por que os recipient estão reclamando.
* Você também pode querer mudar seu link de cancelamento de assinatura para a parte superior do e-mail. Isso incentivará os assinantes a cancelarem a assinatura em vez de reclamarem com o botão de spam.

Os remetentes podem obter uma grande quantidade de informações a partir de suas queixas de [feedback](../../delivery/using/technical-recommendations.md#feedback-loop) :
* É importante agrupar os dados e procurar padrões em coisas como origem de aceitação, quanto tempo o endereço foi inscrito ou até mesmo certos dados demográficos comportamentais.
* As queixas podem frequentemente identificar uma fonte de dados ou segmento com risco dentro do arquivo. O risco é definido como o mais provável de se queixar, o que pode prejudicar a reputação e, por sua vez, as taxas da caixa de entrada.

As reclamações também vêm de assinantes que não querem mais receber e-mail:
* Isso pode ser devido, muitas vezes, a mensagens excessivas, à percepção dos seus assinantes da mensagem, de que eles não estavam esperando a mensagem ou não se lembram de opt in.
* Também é importante executar uma auditoria para garantir que todos os pontos de coleta sejam claros e que não haja caixas pré-marcadas em seus pontos de aquisição.
* Você também deve enviar um email de boas-vindas quando os assinantes optarem por definir o tom e explicar com que frequência eles podem receber emails de você.

**Validade dos dados**

**As rejeições** ocorrem quando você envia para um endereço **** que não pode ser entregue em um ISP. Um endereço pode não ser entregue por vários motivos, como:
* Endereço com erro ortográfico. Isso pode ser resolvido com um serviço de validação de dados em tempo real ou exigindo uma aceitação confirmada antes de enviar emails de marketing para esse endereço.
* lista ou fonte de dados incorreta. Se for proveniente de uma nova fonte, analise como os endereços foram coletados e verifique se havia permissão.
* Enviar para um endereço que estava ativo de uma vez, mas que foi fechado ou terminado após um período de inatividade.

**Envolvimento**

Além das reclamações e da validade dos dados, os provedores de internet estão se concentrando mais do que nunca no compromisso **** positivo de tomar decisões delivery. Eles procuram saber se seus assinantes estão abrindo seus emails ou excluindo-os sem lê-los. Como eles não compartilham esses dados com os remetentes, devemos utilizar as informações que temos disponíveis e traduzir abrir/clicar/transações como envolvimento.

Como parte da manutenção contínua da reputação, é importante entender como os assinantes estão envolvidos em sua lista e desenvolver uma hierarquia **de risco** recente para os assinantes em cada arquivo. A Idade é definida como a última data de abertura/clique/transação ou de inscrição. Esse período pode diferir pela vertical. Para fazer isso:

1. Determine os segmentos ativos (&quot;seguros&quot;) para cada vertical. Normalmente, são assinantes que estiveram ativos nos últimos 3 a 6 meses.
1. Reduza a frequência para inativos.
1. Crie uma série de [reenvolvimento](../../delivery/using/re-engagement-best-practices.md) para iniciativas de risco moderado. Normalmente, são de 6 a 9 meses sem envolvimento.
1. Desenvolver uma campanha de confirmação para inativas de maior risco. Normalmente, são assinantes que não se envolvem em um email há 9 a 12 meses.
1. Finalmente, defina uma regra suspensa e remova os assinantes que não abriram seus emails em &#39;x&#39; meses. Normalmente, recomendamos mais de 12 meses, mas isso pode ser diferente com base no ciclo de vendas e compras.
