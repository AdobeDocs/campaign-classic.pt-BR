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
translation-type: ht
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: ht
source-wordcount: '1341'
ht-degree: 100%

---


# Solução de problemas da capacidade de entrega{#deliverability-faq}

Ocorreu algum problema com a capacidade de entrega? Encontre a solução aqui.

## Erro de regra MX {#mx-rule-error}

**O que significa a mensagem de erro &quot;Cotas atendidas&quot;?**

Esta mensagem indica que o limite de cota de um MX específico foi atingido e que é preciso aguardar para enviar outro email para esse provedor.

No Adobe Campaign, há uma configuração sobre o número de emails por hora que podem ser enviados. Essa configuração deve ser usada com cuidado, pois o número definido na instância diz respeito ao número de conexões realizadas com o ISP e não o número de emails realmente enviados.

Isso significa que uma conexão pode usar uma regra MX sem enviar um email com êxito. Nesse caso, uma configuração com um IP ou um domínio com pouca reputação terá de tentar várias conexões antes de enviar um email. Para cada tentativa, será usado um crédito de mensagens por hora. Como resultado, o desempenho da campanha de marketing será bastante afetado.

Por isso, as &quot;cotas atendidas&quot; não são apenas uma questão de configuração, mas também podem estar ligadas à reputação. É importante analisar as mensagens de erro no [registro SMTP](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

Para obter mais configurações MX, consulte [esta seção](../../installation/using/email-deliverability.md#mx-configuration).

## Mesma mensagem de erro para um ISP {#same-error-for-an-isp}

**Por que recebo sempre a mesma mensagem de erro para um provedor de serviços específico?**

Ao receber sempre a mesma mensagem de erro para um ISP, o email ou IP pode ter sido detectado como defeituoso pelo ISP. Siga as seguintes recomendações:
* Verifique se você recebeu uma grande porcentagem de falhas vinculadas a endereços de email inexistentes (falhas **desconhecidas do usuário**).
* Atualize os formulários de subscrição para detectar qualquer erro nos nomes de domínio inseridos (por exemplo: gmaul.com ou yaho.com).
* Se ocorrer erros que indicam que as mensagens são declaradas como spam ou que estão constantemente bloqueadas, tente excluir os destinatários que não abriram ou clicaram em uma das mensagens nos últimos 12 meses a partir do público-alvo.

Se o problema persistir, entre em contato com os serviços comerciais ou de entrega, o Atendimento ao cliente do Adobe Campaign ou o suporte do Adobe Campaign.

##  Lista de bloqueios × quarentena {#denylist-versus-quarantine}

* **Qual é a diferença entre um endereço de email incluído na lista de bloqueios e um email na quarentena?**

   * O status **[!UICONTROL Denylisted]** é resultado de um ciclo de feedback (quando uma pessoa reporta uma mensagem como spam).

   * O status **[!UICONTROL Quarantined]** é resultado de um salto suave ou forte.
   Para obter mais informações, consulte [esta seção](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist).

* **O que significam os diferentes motivos de erro de quarentena?**

   Aqui estão os 10 possíveis motivos: não definido, usuário desconhecido, domínio inválido, endereço incluído na lista de bloqueios, recusado, erro ignorado, inacessível, conta desativada, caixa de correio cheia e não conectado.

   Para obter mais informações, consulte [Entendendo o gerenciamento da quarentena](../../delivery/using/understanding-quarantine-management.md).

## Remoção da lista de bloqueios {#remove-from-denylist}

* **Um dos meus recipients foi adicionado à lista de bloqueios por engano. Como faço para excluí-los da lista de bloqueios para que eu possa iniciar o envio de mensagens para eles novamente?**

   * Vá para **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * Nos detalhes do registro correspondente, defina o valor do campo **[!UICONTROL Status]** como **[!UICONTROL Valid]**.
   * Salve o registro.

* **Como é possível descobrir se um dos IPs está incluído na lista de bloqueios? Como remover meus IPs de uma lista de bloqueios?**

   É possível usar vários sites para verificar se o endereço IP está na lista de bloqueios, como:
   * [MX Toolbox](https://mxtoolbox.com/)
   * [Qual é meu endereço IP](https://whatismyipaddress.com)

   Geralmente, o resultado da verificação do endereço IP retorna uma lista que contém os detalhes da lista bloqueios e também o nome do site que colocou o endereço IP na lista.

   Ao clicar no link correspondente, é possível acessar os detalhes do site. É possível solicitar que seu site seja excluído da lista de bloqueios do site que incluiu o endereço IP à lista de bloqueios.

   >[!NOTE]
   >
   >O processo de exclusão pode variar dependendo do site. Alguns sites exigem a criação de uma conta, enquanto outros precisam apenas do endereço IP.

## Práticas recomendadas {#best-practices}

Abaixo estão algumas práticas recomendadas que podem ajudar a identificar e solucionar os problemas da capacidade de entrega.

### Identifique um problema da capacidade de entrega {#identify-deliverability-issue}

Os seguintes elementos podem chamar a atenção:

* Métricas de mala direta ou campanha: cancelar inscrição, as queixas de abuso e/ou as taxas de rejeição são mais altas que o normal.
* Atividade do assinante: abertura, cliques e/ou as transações menores do que o normal.
* As contas de seed mostram as malas diretas filtradas ou não entregues.

### Hipóteses de possíveis causas {#potential-causes}

Faça as seguintes perguntas para identificar as possíveis causas para o problema da capacidade de entrega:

* Houve uma mudança recente na segmentação das listas?
* Foram adquiridas novas fontes de dados?
* Algum arquivo foi enviado acidentalmente para quarentena?
* O problema pode ser devido ao conteúdo da mensagem?
* Os emails são enviados com frequência suficiente para manter os IPs aquecidos?
* As mensagens estão sendo segmentadas por atividade/envolvimento ou estão enviando arquivos completos?
* Qual é o segmento &quot;seguro&quot; no arquivo em termos de recenticidade?
* Existem estratégias de reativação e reconfirmação em vigor para os segmentos que não estão definidos como seguros?

### Resolver o problema {#address-issue}

**Reclamações**

As reclamações são definidas por assinantes que **relatam os emails como spam** ao pressionar o botão correspondente em sua caixa de entrada.

Se o problema com seu delivery foi causado por reclamações:
* É necessário tentar determinar por que os destinatários estão reclamando.
* Você pode mudar o link de cancelamento de assinatura para a parte superior do email. Os assinantes serão incentivados a cancelar a assinatura em vez de reclamar com o botão de spam.

Os remetentes podem obter uma grande quantidade de informações a partir das reclamações de [loop de feedback](../../delivery/using/technical-recommendations.md#feedback-loop):
* É importante agrupar os dados e procurar por padrões em coisas como origem da aceitação, quanto tempo o endereço está inscrito ou até mesmo alguns dados demográficos comportamentais.
* As queixas podem frequentemente identificar uma fonte de dados ou segmento com risco dentro do arquivo. O risco é definido como o mais provável de reclamação, o que pode prejudicar a reputação e, por sua vez, as taxas da caixa de entrada.

As reclamações também vêm de assinantes que não querem mais receber email:
* Isso pode ocorrer, muitas vezes, ao excesso de mensagens, à percepção dos assinantes sobre a mensagem, por não esperarem a mensagem ou não se lembrarem de aceitar o recebimento.
* Também é importante executar uma auditoria para garantir que todos os pontos de coleta estejam claros e que não haja caixas pré-marcadas nos pontos de aquisição.
* Também é necessário enviar um email de boas-vindas quando os assinantes optarem por definir o tom e explicar com que frequência eles podem receber emails.

**Validade dos dados**

**As rejeições** ocorrem quando você envia para um **endereço que não pode ser entregue** em um ISP. Um endereço pode não ser entregue por vários motivos, como:
* Endereço com erro ortográfico. Isso pode ser resolvido com um serviço de validação de dados em tempo real ou por meio da exigência de uma aceitação confirmada antes de enviar emails de marketing para esse endereço.
* Lista ou fonte de dados incorreta. Se for proveniente de uma nova fonte, analise como os endereços foram coletados e verifique se havia permissão.
* Enviar mala direta para um endereço que já esteve ativo, mas que foi fechado ou encerrado após um período de inatividade.

**Envolvimento**

Além das reclamações e da validade dos dados, os provedores de internet estão se concentrando mais do que nunca no **envolvimento positivo** para tomar decisões de entrega. Eles procuram saber se os assinantes estão abrindo seus emails ou se estão os excluindo antes de ler. Como eles não compartilham esses dados com os remetentes, devemos utilizar as informações que temos disponíveis e traduzir aberturas/cliques/transações como envolvimento.

Como parte da manutenção contínua da reputação, é importante entender como os assinantes estão envolvidos em sua lista e desenvolver uma **hierarquia de risco de recenticidade** para os assinantes em cada arquivo. A recenticidade é definida como a última data de abertura/clique/transação ou de assinatura. Esse período pode diferir por setor. Para fazer isso:

1. Determine os segmentos ativos (&quot;seguros&quot;) para cada setor. Normalmente, são assinantes que estiveram ativos nos últimos 3 a 6 meses.
1. Reduza a frequência para inativos.
1. Crie uma série de [reenvolvimentos](../../delivery/using/re-engagement-best-practices.md) para iniciativas de risco moderado. Normalmente, são de 6 a 9 meses sem envolvimento.
1. Desenvolva uma campanha de reconfirmação para iniciativas de maior risco. Normalmente, são assinantes que não leem um email há um período de 9 a 12 meses.
1. Por fim, defina uma regra suspensa e remova os assinantes que não abriram seus emails em &quot;x&quot; meses. Normalmente, recomendamos mais de 12 meses, mas isso pode ser diferente com base no ciclo de vendas e compras.
