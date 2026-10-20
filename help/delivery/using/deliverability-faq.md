---
product: campaign
title: Pontos principais ao gerenciar a capacidade de entrega no Adobe Campaign Classic
description: Saiba mais sobre os principais pontos a serem verificados ao gerenciar a capacidade de entrega no Adobe Campaign
feature: Deliverability, Troubleshooting
role: User
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
TQID: 'https://experienceleague.adobe.com/ZRai7Bd-IRaWUQQmkuUYwXhNXp2BI-B4k-4cGq1k6uk'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: 63876777-85c3-57e1-a2da-81f02956c63c
    internal-label: Deliverability
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: a39dbcf0-89cb-4765-9bcb-cf9dfbe2875f
    internal-label: Troubleshooting
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: ht
source-wordcount: '598'
ht-degree: 100%
---
# Solução de problemas da capacidade de entrega{#deliverability-faq}

Ocorreu algum problema com a capacidade de entrega? Encontre a solução aqui.

Como parte da transição do Campaign v7 para o v8, o conjunto de documentações do Campaign Classic foi simplificado e reorganizado. Os recursos comuns agora estão disponíveis apenas no conjunto de documentações do Campaign v8. Para saber mais sobre quarentenas, a lista de bloqueios e como remover um endereço dessa lista, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/quarantines){target=_blank}.

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/quarantines){target=_blank}

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

Se o problema persistir, entre em contato com os serviços comerciais ou de entrega, [Atendimento ao cliente da Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Remover um IP de uma lista de bloqueios {#remove-from-denylist}

* **Como é possível descobrir se um dos IPs está incluído na lista de bloqueios? Como remover meus IPs de uma lista de bloqueios?**

  É possível usar vários sites para verificar se o endereço IP está na lista de bloqueios, como:
  * [MX Toolbox](https://mxtoolbox.com/)
  * [Qual é meu endereço IP](https://whatismyipaddress.com)

  Geralmente, o resultado da verificação do endereço IP retorna uma lista que contém os detalhes da lista bloqueios e também o nome do site que colocou o endereço IP na lista.

  Ao clicar no link correspondente, é possível acessar os detalhes do site. É possível solicitar que seu site seja excluído da lista de bloqueios do site que incluiu o endereço IP à lista de bloqueios.

  >[!NOTE]
  >
  >O processo de exclusão pode variar dependendo do site. Alguns sites exigem a criação de uma conta, enquanto outros precisam apenas do endereço IP.
