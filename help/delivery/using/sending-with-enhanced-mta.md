---
solution: Campaign Classic
product: campaign
title: Envio com o MTA aprimorado no Adobe Campaign Classic
description: Saiba mais sobre o escopo e as especificidades do envio de emails com o Adobe Campaign Enhanced MTA.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 07ed17a093cb6fb2d7aae376325a127c61b1dcc2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Envio com MTA aprimorado {#sending-with-enhanced-mta}

O **Adobe Campaign Enhanced MTA** (Mail Transfer Agent) fornece uma infraestrutura de envio atualizada que permite um melhor fornecimento, reputação, throughput, relatórios, tratamento de rejeição, aumento do IP e gerenciamento da configuração de conexão.

Ele é implementado para melhorar a escalabilidade, aumentar a throughput do delivery e ajudar a enviar mais e-mails mais rapidamente. Isso é feito com novas técnicas de delivery adaptáveis que alteram as configurações de envio de email em tempo real, com base no feedback dos Provedores de serviço da Internet.

>[!IMPORTANT]
>
>O Adobe Campaign Enhanced MTA só está disponível para clientes Campaign Classic hospedados ou híbridos. As instalações locais de Campaign Classic não podem ser atualizadas para usar o MTA aprimorado.

Se você tiver provisionado uma instância Campaign Classic após setembro de 2018, estará usando o MTA aprimorado. Para todos os outros clientes do Campaign Classic, consulte as [Perguntas frequentes](#enhanced-mta-faq) abaixo.

A implementação aprimorada do MTA pode afetar algumas das funcionalidades de Campanha existentes. Para obter mais informações, consulte [Especificidades MTA aprimoradas](#enhanced-mta-impacts).

## Perguntas frequentes {#enhanced-mta-faq}

### Uso e benefícios

**O que é o MTA aprimorado?**

A Adobe Campaign agora pode ser atualizada para usar um novo MTA (Mail Transfer Agent) que executa o MTA de email comercial do SparkPost chamado **Momentum**.

O momento representa uma tecnologia MTA inovadora e de alto desempenho, que inclui um tratamento mais inteligente de rejeição e um recurso automatizado de otimização de entrega que ajuda os remetentes a alcançarem e manterem as taxas ideais de delivery da caixa de entrada. <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**Quais são os benefícios?**

* Os clientes Adobe Campaign que usam o Enhanced MTA viram um <!--300%-->aumento maciço na velocidade geral de throughput e uma <!--90%+-->redução significativa nas rejeições de software.
* A MTA aprimorada usa a mais recente tecnologia MTA para oferecer a você as velocidades de throughput ideais para o seu delivery de e-mail.
* Ao adaptar-se instantaneamente e automaticamente ao feedback que recebe, ele também garante um delivery de email mais preciso e inteligente com dados de delivery em tempo real.

**Posso usar o Adobe Campaign MTA nativo e o MTA aprimorado ao mesmo tempo?**

Não. Somente o MTA aprimorado pode ser usado para seus delivery de e-mail depois que sua instância for atualizada.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Atualização para o MTA aprimorado

**O que é necessário para atualizar para o MTA aprimorado?**

Se você tiver provisionado uma instância Campaign Classic após setembro de 2018, nenhuma ação será necessária, pois você já está usando o MTA aprimorado.

Para todos os outros clientes hospedados ou parcialmente hospedados (híbridos), a equipe da Adobe Campaign tentará coordenar uma data para a migração e fornecerá detalhes sobre as etapas apropriadas necessárias para a migração.

>[!IMPORTANT]
>
>O MTA aprimorado não está disponível para instalações locais.

**Qual é o processo para atualizar minha instância para o MTA aprimorado?**

Todo o processo das instâncias hospedadas requer alguns minutos de inatividade. O Adobe monitorará a throughput e a capacidade de entrega do e-mail por até 24 horas após a atualização para avaliar qualquer impacto nos delivery de e-mail.

Caso algum problema seja detectado, o Adobe pode reverter rápida e temporariamente sua instância de volta para o Adobe Campaign MTA nativo.

Atualmente, o MTA aprimorado afeta apenas o canal de email. Suas notificações por push e delivery SMS continuarão a usar a Campanha MTA nativa e não serão afetados de nenhuma forma pela atualização.

**Preciso passar pelo aquecimento de IP novamente depois de atualizar para o MTA aprimorado?**

Não. A atualização não requer a alternância para novos IPs, portanto, você pode continuar usando seus IPs de e-mail existentes e aquecidos.

**A atualização para o MTA aprimorado afetará quaisquer campanhas ou delivery em andamento?**

Qualquer delivery que tenha sido preparado antes da sua instância ter sido atualizado para usar o Enhanced MTA precisará ser repreparado para usar corretamente o novo MTA.

Para os clientes que usam a funcionalidade de mensagens transacionais da Adobe Campaign, todas as chamadas da API para acionar um email serão enfileiradas durante o curto tempo de inatividade da atualização e serão tentadas após a conclusão da atualização.

## Especificidades MTA aprimoradas {#enhanced-mta-impacts}

### Cabeçalhos MTA aprimorados

As instâncias de Campaign Classic mais recentes incluem código que adiciona os cabeçalhos MTA aprimorados necessários a cada mensagem. Se você estiver usando o Adobe Campaign 19.1 (build 9032) ou superior e esse não for o caso, é necessário adicionar o parâmetro &quot;useMomentum=true&quot; à configuração da instância de marketing (no arquivo [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)).

No entanto, se você estiver usando uma instância mais antiga que não inclui esse código, uma nova regra de tipologia chamada **[!UICONTROL Typology Rule for Enhanced MTAs]** deverá ser adicionada a todas as tipologias existentes na instância da Campanha.
Essa regra é adicionada por um pacote **[!UICONTROL Typology]** instalado como parte da atualização para o MTA aprimorado.

>[!IMPORTANT]
>
>Se você vir essa regra de tipologia em suas tipologias, não exclua nem modifique-a de nenhuma forma. Caso contrário, seus delivery de email poderão ser afetados negativamente.

Este pacote **[!UICONTROL Typology]** precisa ser instalado na instância de marketing da Adobe Campaign.

Se você for um cliente híbrido, a equipe da Adobe Campaign fornecerá instruções sobre como instalar o pacote **[!UICONTROL Typology]** em sua instância de marketing como parte da atualização para o MTA aprimorado. Entre em contato com o executivo da sua conta para obter instruções completas.

>[!IMPORTANT]
>
>As instruções fornecidas pela equipe da Adobe Campaign sobre como instalar o pacote **[!UICONTROL Typology]** devem ser cuidadosamente seguidas. Caso contrário, você poderá encontrar problemas importantes com seus IPs usados para enviar emails.

Para obter mais informações sobre tipologias, consulte [esta seção](../../campaign/using/about-campaign-typologies.md).

### Novas regras MX

As regras de throughput do delivery de gerenciamento MX não são mais usadas. O MTA aprimorado tem suas próprias regras MX que permitem personalizar sua throughput por domínio com base na sua própria reputação histórica de email e no feedback em tempo real proveniente dos domínios em que você está enviando emails.

Para obter mais configurações MX, consulte [esta seção](../../installation/using/email-deliverability.md#mx-configuration).

### Qualificação de rejeição

As qualificações de rejeição na tabela **[!UICONTROL Delivery log qualification]** da Campanha não são mais usadas para **mensagens de erro de falha de delivery síncronas**. O MTA aprimorado determinará o tipo de devolução e a qualificação e enviará essas informações para o Campaign.

>[!NOTE]
>
>O MTA aprimorado qualifica a rejeição SMTP e envia essa qualificação de volta à Campanha no formato de um código de rejeição mapeado para um motivo de rejeição e qualificação de Campanha.

Para obter mais informações sobre qualificação de rejeição, consulte [esta seção](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification).

### Status enviado com MTA aprimorado

Na visualização **[!UICONTROL Summary]** de um delivery de e-mail [painel](../../delivery/using/delivery-dashboard.md), a porcentagem **[!UICONTROL Success]** é start em 100% e, em seguida, diminui progressivamente durante todo o delivery [período de validade](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period), à medida que as rejeições em software e hardware são reportadas de volta do MTA aprimorado à Campanha.

Na verdade, todas as mensagens são exibidas como **[!UICONTROL Sent]** no [remetendo logs](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) assim que são repassadas com êxito da Campanha para o MTA Avançado. Eles permanecem nesse status, a menos que [bounce](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) para essa mensagem seja comunicada de volta do MTA aprimorado para a Campanha.

Quando as mensagens de ressalto rígido são reportadas do MTA Avançado, seu status muda de **[!UICONTROL Sent]** para **[!UICONTROL Failed]** e a porcentagem **[!UICONTROL Success]** é diminuída de acordo.

Quando as mensagens de salto em modo suave são reportadas de volta do MTA aprimorado, elas ainda são exibidas como **[!UICONTROL Sent]** e a porcentagem **[!UICONTROL Success]** ainda não é atualizada. As mensagens de ressalto automático são então [repetidas](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) durante todo o período de validade do delivery:

* Se uma nova tentativa for bem-sucedida antes do final do período de validade, o status da mensagem permanecerá como **[!UICONTROL Sent]** e a porcentagem **[!UICONTROL Success]** permanecerá inalterada.

* Caso contrário, o status mudará para **[!UICONTROL Failed]** e a porcentagem **[!UICONTROL Success]** será diminuída de acordo.

Consequentemente, você deve aguardar até o final do período de validade para ver a porcentagem final **[!UICONTROL Success]** e o número final das mensagens **[!UICONTROL Sent]** e **[!UICONTROL Failed]**.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### Taxa de transferência da entrega

O gráfico de throughput do Delivery da Campanha não exibirá mais a throughput para seus recipient de e-mail. Esse gráfico agora mostrará a velocidade de saída para o relé de suas mensagens da Campanha para o MTA aprimorado.

Para obter mais informações sobre a taxa de transferência do delivery, consulte [esta seção](../../reporting/using/global-reports.md#delivery-throughput).

### Período de validade

A configuração do período de validade em seus delivery de Campanha será usada pelo MTA aprimorado somente se for definida como **3,5 dias ou menos**. Se você definir um valor superior a 3,5 dias na Campanha, ele não será considerado.

Por exemplo, se o período de validade estiver definido com o valor padrão de 5 dias na Campanha, as mensagens de salto em modo suave entrarão na fila de tentativas aprimoradas do MTA e serão repetidas por apenas 3,5 dias a partir do momento em que a mensagem chegou ao MTA aprimorado. Nesse caso, o valor definido na Campanha não será usado.

Quando uma mensagem estiver na fila do MTA aprimorado por 3,5 dias e não for entregue, o tempo limite expirará, e seu status será atualizado de **[!UICONTROL Sent]** para **[!UICONTROL Failed]** nos logs de delivery.

Para obter mais informações sobre o período de validade, consulte [esta seção](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

### Assinatura DKIM

A assinatura de autenticação de email DKIM (DomainKeys Identified Mail) é feita pelo MTA aprimorado. A assinatura do DKIM pelo MTA nativo do Campaign será desativada na tabela Domain management como parte da atualização do MTA aprimorado.
Para obter mais informações sobre o DKIM, consulte [esta seção](../../delivery/using/technical-recommendations.md#dkim).