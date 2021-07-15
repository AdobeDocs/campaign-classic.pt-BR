---
product: campaign
title: Pontos principais ao gerenciar a capacidade de delivery no Adobe Campaign Classic
description: Quais são os principais pontos a serem verificados ao gerenciar a capacidade de delivery no Adobe Campaign Classic?
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: ht
source-wordcount: '657'
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

Se o problema persistir, entre em contato com os serviços comerciais ou de entrega, [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Lista de bloqueios × quarentena {#denylist-versus-quarantine}

* **Qual é a diferença entre um endereço de email incluído na lista de bloqueios e um email na quarentena?**

   * O status **[!UICONTROL Denylisted]** é resultado de um ciclo de feedback (quando uma pessoa reporta uma mensagem como spam).

   * O status **[!UICONTROL Quarantined]** é resultado de um salto suave ou forte.
   Para obter mais informações, consulte [esta seção](understanding-quarantine-management.md#quarantine-vs-denylist).

* **O que significam os diferentes motivos de erro de quarentena?**

   Aqui estão os 10 possíveis motivos: não definido, usuário desconhecido, domínio inválido, endereço incluído na lista de bloqueios, recusado, erro ignorado, inacessível, conta desativada, caixa de correio cheia e não conectado.

   Para obter mais informações, consulte [Entendendo o gerenciamento da quarentena](understanding-quarantine-management.md).

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
