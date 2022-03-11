---
product: campaign
title: Entender o gerenciamento de quarentena
description: Entender o gerenciamento de quarentena
feature: Monitoring, Deliverability
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: ht
source-wordcount: '2837'
ht-degree: 100%

---

# Entender o gerenciamento de quarentena{#understanding-quarantine-management}

![](../../assets/common.svg)

O Adobe Campaign gerencia uma lista de endereços em quarentena. Os recipients cujo endereço está em quarentena são excluídos por padrão durante a análise de delivery e não serão direcionados. Um endereço de e-mail pode ser colocado em quarentena, por exemplo, quando a caixa de correio está cheia ou se o endereço não existe. Em qualquer caso, o procedimento de quarentena está em conformidade com as regras específicas descritas abaixo.

>[!NOTE]
>
>Esta seção se aplica aos canais online: email, SMS, notificação por push.

## Otimizar seu delivery por meio do gerenciamento de quarentena {#optimizing-your-delivery-through-quarantines}

Os perfis cujos endereços de email ou número de telefone estão em quarentena são excluídos automaticamente durante a preparação da mensagem (consulte [Identificar endereços em quarentena para um delivery](#identifying-quarantined-addresses-for-a-delivery)). Isso irá acelerar os deliveries, pois a taxa de erro tem um efeito significativo na velocidade do delivery.

Alguns provedores de acesso à Internet consideram automaticamente emails como spam se a taxa de endereços inválidos é muito alta. A quarentena, portanto, evita que você seja adicionado à lista de bloqueios por esses provedores.

Além disso, a quarentena ajuda a reduzir os custos de envio de SMS, excluindo números de telefone incorretos dos deliveries.

Para obter mais informações sobre as práticas recomendadas para proteger e otimizar seus deliveries, consulte [esta página](delivery-best-practices.md).

### Quarentena versus Lista de bloqueios {#quarantine-vs-denylist}

A quarentena e a lista de bloqueios não se aplicam ao mesmo objeto:

* A **quarentena** se aplica somente a um **endereço** (ou número de telefone etc.), não ao próprio perfil. Por exemplo, um perfil cujo endereço de email esteja em quarentena pode atualizar seu perfil e inserir um novo endereço, podendo então ser direcionado em ações de delivery novamente. Da mesma forma, se dois perfis tiverem o mesmo número de telefone, ambos serão afetados se o número estiver em quarentena.

   Os endereços em quarentena ou os números de telefone são exibidos nos [logs de exclusão](#identifying-quarantined-addresses-for-a-delivery) (para um delivery) ou na [lista de quarentena](#identifying-quarantined-addresses-for-the-entire-platform) (para toda a plataforma).

* Por outro lado, com a inclusão na **lista de bloqueios**, o **perfil** não será mais direcionado pelo delivery, por exemplo, depois de um cancelamento de inscrição (recusa de participação) de um determinado canal. Por exemplo, se um perfil na lista de bloqueios para o canal de email tiver dois endereços de email, ambos os endereços serão excluídos do delivery.

   Você pode verificar se um perfil está na lista de bloqueios para um ou mais canais na seção **[!UICONTROL No longer contact]** da guia **[!UICONTROL General]** do perfil. Consulte [esta seção](../../platform/using/editing-a-profile.md#general-tab).

>[!NOTE]
>
>A quarentena inclui um status **[!UICONTROL Denylisted]**, que se aplica quando os recipients marcam sua mensagem como spam ou respondem a uma mensagem SMS com uma palavra-chave como &quot;PARAR&quot;. Nesse caso, o endereço envolvido do perfil ou o número de telefone é enviado para quarentena com o status **[!UICONTROL Denylisted]**. Para obter mais informações sobre como gerenciar mensagens SMS PARAR, consulte [esta seção](../../delivery/using/sms-send.md#processing-inbound-messages).

## Identificar endereços em quarentena {#identifying-quarantined-addresses}

Os endereços em quarentena podem ser listados para um delivery específico ou para toda a plataforma.

### Identificar endereços em quarentena para um delivery {#identifying-quarantined-addresses-for-a-delivery}

Os endereços em quarentena para um delivery específico são listados durante a fase de preparação do delivery, nos logs do delivery do painel de delivery (consulte [Histórico e logs do delivery](delivery-dashboard.md#delivery-logs-and-history)).

### Identificar endereços em quarentena para toda a plataforma {#identifying-quarantined-addresses-for-the-entire-platform}

Os administradores podem listar os endereços em quarentena para toda a plataforma do nó **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.

>[!NOTE]
>
>Este menu lista os elementos colocados em quarentena para os canais de **email**, **SMS** e **notificação por push** .

As seguintes informações estão disponíveis para cada endereço:

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>O aumento no número em quarentena é um efeito normal, relacionado ao &quot;desgaste&quot; do banco de dados. Por exemplo, se o tempo de vida de um endereço de email for considerado três anos e a tabela de recipients aumentar em 50% todo ano, o aumento da quarentena poderá ser calculado da seguinte maneira:
>
>Fim do Ano 1: (1*0.33)/(1+0.5)=22%.
>Fim do Ano 2: ((1.22*0.33)+0.33)/(1.5+0.75)=32.5%.

### Identificar endereços em quarentena nos relatórios do delivery {#identifying-quarantined-addresses-in-delivery-reports}

Os seguintes relatórios fornecem informações sobre os endereços em quarentena:

* Para cada delivery, o relatório **[!UICONTROL Delivery summary]** mostra o número de endereços em quarentena no target do delivery. Ele exibe:

   * O número de endereços colocados em quarentena durante a análise de delivery,

   * O número de endereços colocados em quarentena após a ação de delivery.

* O relatório **[!UICONTROL Non-deliverables and bounces]** exibe informações sobre os endereços em quarentena, os tipos de erro encontrados e etc., além de um detalhamento de falha por domínio.

Você pode visualizar essas informações para todos os deliveries da plataforma (**[!UICONTROL Home page > Reports]**) ou para um delivery específico. Você também pode criar relatórios personalizados e selecionar as informações a serem exibidas.

### Identificar endereços em quarentena para um recipient {#identifying-quarantined-addresses-for-a-recipient}

Você pode consultar o status do endereço de email de qualquer recipient. Para fazer isso, selecione o perfil do recipient e clique na guia **[!UICONTROL Deliveries]**. Para todos os deliveries para esse recipient, você pode descobrir se o endereço falhou, estava em quarentena durante a análise, etc. Para cada pasta, é possível exibir apenas os recipients cujo endereço de email está em quarentena. Para fazer isso, use o filtro de aplicação **[!UICONTROL Quarantined email address]**.

![](assets/tech_quarant_recipients_filter.png)

### Remover um endereço em quarentena {#removing-a-quarantined-address}

Caso necessário, você pode remover manualmente um endereço da lista da quarentena. Além disso, os endereços que correspondem a condições específicas são automaticamente excluídos da lista de quarentena pelo fluxo de trabalho [Limpeza do banco de dados](../../production/using/database-cleanup-workflow.md). 

Para remover manualmente um endereço da lista da quarentena, execute uma das ações abaixo.

>[!IMPORTANT]
>Excluir manualmente um endereço de email da quarentena significa que você reiniciará o delivery para esse endereço. Consequentemente, isso pode ter graves impactos na sua capacidade de entrega e reputação de IP, o que pode eventualmente levar ao bloqueio do seu endereço IP ou domínio de envio. Continue com muito cuidado ao considerar a remoção de qualquer endereço da quarentena. Em caso de dúvidas, entre em contato com um especialista em capacidade de delivery.

* É possível alterar seu status para **[!UICONTROL Valid]** a partir do nó **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.

   ![](assets/tech_quarant_error_status.png)

* Você também pode alterar o status para **[!UICONTROL Allowlisted]**. Nesse caso, o endereço permanece na lista da quarentena, mas será direcionado sistematicamente, mesmo que um erro seja encontrado.

Os endereços são removidos automaticamente da lista de quarentena nos seguintes casos:

* Os endereços em um status **[!UICONTROL With errors]** serão removidos da lista de quarentena após um delivery bem-sucedido.
* Os endereços em um status **[!UICONTROL With errors]** serão removidos da lista de quarentena se o último retorno de erro tiver ocorrido há mais de 10 dias. Para obter mais informações sobre o gerenciamento de erros de software, consulte [esta seção](#soft-error-management).
* Os endereços em um status **[!UICONTROL With errors]** que tiverem retornado com o erro **[!UICONTROL Mailbox full]** serão removidos da lista de quarentena após 30 dias.

O status muda então para **[!UICONTROL Valid]**.

>[!IMPORTANT]
>Os recipients com um endereço em um status **[!UICONTROL Quarantine]** ou **[!UICONTROL Denylisted]** nunca serão removidos, mesmo se receberem um email.

Para instalações hospedadas ou híbridas, se você tiver atualizado para o [MTA aprimorado](sending-with-enhanced-mta.md), o número máximo de tentativas a efetuar em caso de status **[!UICONTROL Erroneous]**, e o atraso mínimo entre tentativas agora se baseiam no desempenho histórico e atual de um IP em um determinado domínio.

Para instalações no local e instalações hospedadas/híbridas usando o MTA herdado do Campaign, você pode modificar o número de erros e o período entre dois erros. Para fazer isso, altere as configurações correspondentes no [assistente de implantação](../../installation/using/deploying-an-instance.md) (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**) ou [no nível do delivery](../../delivery/using/steps-sending-the-delivery.md#configuring-retries).

## Condições para enviar um endereço para quarentena {#conditions-for-sending-an-address-to-quarantine}

O Adobe Campaign gerencia a quarentena de acordo com o tipo de falha do delivery e o motivo atribuído durante a qualificação de mensagens de erro (consulte [Qualificação de emails de devolução](understanding-delivery-failures.md#bounce-mail-qualification) e os [tipos e motivos de falha de delivery](understanding-delivery-failures.md#delivery-failure-types-and-reasons)).

* **Erro ignorado**: os erros ignorados não enviam um endereço para quarentena.
* **Erro grave**: o endereço de email correspondente é enviado imediatamente para quarentena.
* **Erro suave**: erros suaves não enviam um endereço imediatamente para quarentena, mas incrementam um contador de erros. Para obter mais informações, consulte [Gerenciamento de erros leves](#soft-error-management).

Se um usuário qualificar um email como spam ([loop de feedback](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=pt-BR#feedback-loops)), a mensagem será automaticamente redirecionada para uma caixa de entrada técnica gerenciada pela Adobe. Em seguida, o endereço de email do usuário será enviado automaticamente para quarentena com o status **[!UICONTROL Denylisted]**. Esse status se refere apenas ao endereço. O perfil não é incluído na lista de bloqueio para que o usuário continue recebendo mensagens SMS e notificações por push.

>[!NOTE]
>A quarentena no Adobe Campaign diferencia maiúsculas de minúsculas. Certifique-se de importar endereços de email em letras minúsculas, para que não sejam redirecionados posteriormente.

Na lista de endereços em quarentena (consulte [Identificação de endereços em quarentena para toda a plataforma](#identifying-quarantined-addresses-for-the-entire-platform)), o campo **[!UICONTROL Error reason]** indica por que o endereço selecionado foi colocado em quarentena.

![](assets/tech_quarant_error_reasons.png)

### Gerenciamento de erros leves {#soft-error-management}

Ao contrário de erros graves, os erros recuperáveis não enviam um endereço imediatamente para quarentena, mas incrementam um contador de erros.

As tentativas serão executadas no decorrer da [duração do delivery](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period). Quando o contador de erros atinge o limite da cota, o endereço vai para a quarentena. Para obter mais informações, consulte [Tentativas após uma falha temporária de delivery](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

O contador de erros será reinicializado se o último erro significativo ocorrer há mais de 10 dias. O status do endereço é alterado para **Válido** e excluído da lista de quarentenas pelo workflow de [limpeza do banco de dados](../../production/using/database-cleanup-workflow.md).

## Quarentenas de notificação por push {#push-notification-quarantines}

O mecanismo de quarentena para notificações por push é globalmente igual ao processo geral. Consulte [Sobre quarentenas](#about-quarantines). No entanto, certos erros são gerenciados de forma diferente para notificações por push. Por exemplo, para determinados erros suaves, nenhuma tentativa é executada no mesmo delivery. As especificidades para notificação por push estão listadas abaixo. O mecanismo de tentativa (número de tentativas, frequência) é igual ao dos emails.

Os itens colocados em quarentena são tokens de dispositivo.

### Quarentena do iOS {#ios-quarantine}

O protocolo HTTP/V2 permite um feedback e status direto para cada delivery por push. Se o conector do protocolo HTTP/V2 for usado, o serviço de feedback não será mais chamado pelo workflow **[!UICONTROL mobileAppOptOutMgt]**. Um token é considerado não registrado quando um aplicativo móvel é desinstalado ou reinstalado.

Em sincronia, se o APNs retornar um status &quot;não registrado&quot; para uma mensagem, o token do público alvo será colocado imediatamente em quarentena.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Cenário</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Mensagem de erro</strong><br /> </td> 
   <td> <strong>Tipo de falha</strong><br /> </td> 
   <td> <strong>Motivo da falha</strong><br /> </td> 
   <td> <strong>Tentativa</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Dispositivo alvo ligado<br /> </td> 
   <td> Ok<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Dispositivo alvo desligado<br /> </td> 
   <td> Ok<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> O usuário desabilita notificações para o aplicativo<br /> </td> 
   <td> Ok<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Fase de análise/criação de mensagens - carga muito grande<br /> </td> 
   <td> Falha<br /> </td> 
   <td> Carga muito longa<br /> </td> 
   <td> Suave<br /> </td> 
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr> 
  <tr> 
   <td> Fase de análise/criação de mensagens – problema inesperado de formato de conteúdo<br /> </td> 
   <td> Falha<br /> </td> 
   <td> Várias mensagens de erro de acordo com o erro<br /> </td> 
   <td> Suave<br /> </td> 
   <td> Indefinido<br /> </td> 
   <td> Não<br /> </td> 
  </tr> 
  <tr> 
   <td> Problema de certificado (senha, corrupção, etc.) e teste de conexão para problema APNs<br /> </td> 
   <td> Falha<br /> </td> 
   <td> Várias mensagens de erro de acordo com o erro<br /> </td> 
   <td> Suave<br /> </td> 
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr> 
  <tr> 
   <td> Conexão de rede perdida durante o envio<br /> </td> 
   <td> Falha<br /> </td> 
   <td> Erro de conexão<br /> </td> 
   <td> Indefinido<br /> </td> 
   <td> Inacessível<br /> </td> 
   <td> Sim<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejeição da mensagem APNs: cancelamento de registro<br /> o usuário removeu o aplicativo ou o token expirou<br /> </td> 
   <td> Falha<br /> </td> 
   <td> Registro cancelado<br /> </td> 
   <td> Grave<br /> </td> 
   <td> Usuário desconhecido<br /> </td> 
   <td> Não<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejeição de mensagem APNs: todos os outros erros<br /> </td> 
   <td> Falha<br /> </td> 
   <td> A causa de rejeição do erro será exibida na mensagem de erro<br /> </td> 
   <td> Suave<br /> </td> 
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Quarentena do Android {#android-quarantine}

**Para Android V1**

A cada notificação, o Adobe Campaign recebe os erros síncronos diretamente do servidor FCM. O Adobe Campaign os trata instantaneamente e gera erros graves ou suaves, de acordo com a gravidade do erro, e tentativas podem ser executadas:

* Comprimento de carga excedido, problema de conexão, problema de disponibilidade de serviço: tentativa executava, erro leve, o motivo da falha é **[!UICONTROL Refused]**.
* Cota de dispositivo excedida: sem tentativa, erro leve, o motivo da falha é **[!UICONTROL Refused]**.
* Token inválido ou não registrado, erro inesperado, problema da conta do remetente: sem tentativa, erro grave, o motivo de falha é **[!UICONTROL Refused]**.

O workflow **[!UICONTROL mobileAppOptOutMgt]** é executado a cada 6 horas para atualizar a tabela **AppSubscriptionRcp**. Para os tokens declarados não registrados ou não mais válidos, o campo **Desativado** é definido como **Verdadeiro** e a subscrição vinculada a esse token de dispositivo será excluída automaticamente dos deliveries futuros.

Durante a análise de delivery, todos os dispositivos excluídos do target são automaticamente adicionados à tabela **excludeLogAppSubRcp** .

>[!NOTE]
>Para clientes que usam o conector Baidu, aqui estão os diferentes tipos de erros:
>* Problema de conexão no início do delivery: falha do tipo **[!UICONTROL Undefined]**, razão da falha **[!UICONTROL Unreachable]**, a tentativa é executada.
>* Perda de conexão durante um delivery: erro leve, razão da falha **[!UICONTROL Refused]**, a tentativa é executada.
>* Erro síncrono retornado pelo Baidu durante o envio: erro grave, motivo da falha **[!UICONTROL Refused]**, não haverá nova tentativa.
>O Adobe Campaign contata o servidor Baidu a cada 10 minutos para recuperar o status da mensagem enviada e atualiza os broadlogs. Se uma mensagem for declarada como enviada, o status da mensagem nos broadlogs será definido como **[!UICONTROL Received]**. Se o Baidu declarar um erro, o status será definido como **[!UICONTROL Failed]**.

**Para Android V2**

O mecanismo de quarentena do Android V2 usa o mesmo processo que o Android V1, o mesmo se aplica à atualização de assinaturas e exclusões. Para obter mais informações, consulte a seção [Android V1](#android-quarantine)

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Cenário</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Mensagem de erro</strong><br /> </td> 
   <td> <strong>Tipo de falha</strong><br /> </td> 
   <td> <strong>Motivo da falha</strong><br /> </td> 
   <td> <strong>Tentativa</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Fase de análise/criação de mensagens: palavras-chave ilegais usadas nos campos personalizados<br /> </td> 
   <td> Falha<br /> </td> 
   <td> As seguintes palavras-chave não podem ser usadas: {1}<br /> </td> 
   <td> Suave<br /> </td> 
   <td> </td> 
   <td> Não<br /> </td> 
  </tr> 
  <tr> 
   <td> Fase de análise/criação de mensagens: carga muito grande<br /> </td> 
   <td> Falha<br /> </td> 
   <td> A notificação é muito pesada: {1} bits, enquanto apenas {2} estão autorizados<br /> </td> 
   <td> Suave<br /> </td> 
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr> 
  <tr> 
   <td> Conexão de rede perdida durante o envio<br /> </td> 
   <td> Falha<br /> </td> 
   <td> Nenhuma resposta do serviço Firebase Cloud Messaging no endereço: {1}<br /> </td> 
   <td> Suave<br /> </td> 
   <td> Inacessível<br /> </td> 
   <td> Sim<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejeição da mensagem FCM: o servidor FCM está temporariamente indisponível (por exemplo, com tempos limites). <br /> </td> 
   <td> Falha<br /> </td> 
   <td> O serviço Firebase Cloud Messaging está temporariamente indisponível<br /> </td> 
   <td> Suave<br /> </td> 
   <td> Inacessível<br /> </td> 
   <td> Sim<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejeição da mensagem FCM: erro ao autenticar a conta do remetente<br /> </td> 
   <td> Falha<br /> </td> 
   <td> Falha ao identificar a conta do desenvolvedor, verifique seu ID e senha<br /> </td> 
   <td> Suave<br /> </td> 
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejeição da mensagem FCM: cota do dispositivo excedida<br /> </td> 
   <td> Falha<br /> </td> 
   <td> </td> 
   <td> Suave<br /> </td> 
   <td> Recusado<br /> </td> 
   <td> Sim<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejeição da mensagem FCM: registro inválido/não registrado<br /> </td> 
   <td> Falha<br /> </td> 
   <td> </td> 
   <td> Grave<br /> </td> 
   <td> Usuário desconhecido<br /> </td> 
   <td> Não<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejeição da mensagem FCM: todos os outros erros<br /> </td> 
   <td> Falha<br /> </td> 
   <td> O servidor Firebase Cloud Messaging retornou um código de erro inesperado: {1} </td> 
   <td> </td> 
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr> 
    <tr> 
   <td> Rejeição da mensagem FCM: argumento inválido<br /> </td> 
   <td> Falha<br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> Ignorado</td> 
   <td> Indefinido<br /> </td> 
   <td> Não<br /> </td> 
  </tr>
    <tr> 
   <td> Rejeição da mensagem FCM: erro de autenticação de terceiros<br /> </td> 
   <td> Falha<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> Ignorado</td>
   <td> Recusado<br /> </td> 
   <td> Sim<br /> </td> 
  </tr>
    <tr> 
   <td> Rejeição da mensagem FCM: incompatibilidade de ID do remetente<br /> </td> 
   <td> Falha<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> Suave</td>
   <td> Usuário desconhecido<br /> </td> 
   <td> Não<br /> </td> 
  </tr>
    <tr> 
   <td> Rejeição da mensagem FCM: não registrado<br /> </td> 
   <td> Falha<br /> </td>
   <td> REGISTRO CANCELADO </td> 
   <td> Grave</td> 
   <td> Usuário desconhecido<br /> </td> 
   <td> Não<br /> </td> 
  </tr>
    <tr> 
   <td> Rejeição da mensagem FCM: interno<br /> </td> 
   <td> Falha<br /> </td> 
   <td> INTERNO </td> 
   <td> Ignorado</td> 
   <td> Recusado<br /> </td> 
   <td> Sim<br /> </td> 
  </tr>
    <tr> 
   <td> Rejeição da mensagem FCM: indisponível<br /> </td> 
   <td> Falha<br /> </td> 
   <td> INDISPONÍVEL</td> 
   <td> Ignorado</td> 
   <td> Recusado<br /> </td> 
   <td> Sim<br /> </td> 
  </tr>
    <tr> 
   <td> Rejeição da mensagem FCM: código de erro inesperado<br /> </td> 
   <td> Falha<br /> </td> 
   <td> código de erro inesperado</td> 
   <td> Ignorado</td> 
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr>
  <tr> 
   <td> Autenticação: problema de conexão<br /> </td> 
   <td> Falha<br /> </td> 
   <td> Impossível conectar-se ao servidor de autenticação </td> 
   <td> Ignorado</td>
   <td> Recusado<br /> </td> 
   <td> Sim<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticação: cliente ou escopo não autorizado na solicitação.<br /> </td> 
   <td> Falha<br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignorado</td>
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticação: o cliente não está autorizado a recuperar tokens de acesso usando este método ou o cliente não está autorizado para nenhum dos escopos solicitados.<br /> </td> 
   <td> Falha<br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignorado</td>
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticação: acesso negado<br /> </td> 
   <td> Falha<br /> </td>
   <td> access_denied</td> 
   <td> Ignorado</td>
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticação: email inválido<br /> </td> 
   <td> Falha<br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignorado</td> 
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticação: JWT inválido<br /> </td> 
   <td> Falha<br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignorado</td> 
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticação: assinatura JWT inválida<br /> </td> 
   <td> Falha<br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignorado</td> 
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticação: escopo Oauth inválido ou público de token de ID fornecido<br /> </td> 
   <td> Falha<br /> </td> 
   <td> unauthorized_client</td> 
   <td> Ignorado</td> 
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticação: cliente OAuth desabilitado<br /> </td> 
   <td> Falha<br /> </td> 
   <td> disabled_client</td> 
   <td> Ignorado</td> 
   <td> Recusado<br /> </td> 
   <td> Não<br /> </td> 
  </tr>
 </tbody> 
</table>

## Quarentenas de SMS {#sms-quarantines}

**Para conectores padrão**

O mecanismo de quarentena para mensagens SMS é globalmente igual ao processo geral. Consulte [Sobre quarentenas](#about-quarantines). As especificidades para SMS estão listadas abaixo.

>[!NOTE]
>A tabela **[!UICONTROL Delivery log qualification]** não se aplica ao conector **SMPP genérico estendido**.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Cenário</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Mensagem de erro</strong><br /> </td> 
   <td> <strong>Tipo de falha</strong><br /> </td> 
   <td> <strong>Motivo da falha</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Enviado para o provedor<br /> </td> 
   <td> Sent<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Recebido no celular<br /> </td> 
   <td> Recebido<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Erro retornado pelo provedor<br /> </td> 
   <td> Falha<br /> </td> 
   <td> Erro ao receber dados (SR ou MO)<br /> </td> 
   <td> Suave<br /> </td> 
   <td> Inacessível<br /> </td> 
  </tr> 
  <tr> 
   <td> Confirmação MT inválida<br /> </td> 
   <td> Falha<br /> </td> 
   <td> Erro '{1}' ao processar quadro de confirmação para enviar query<br /> </td> 
   <td> Suave<br /> </td> 
   <td> Inacessível<br /> </td> 
  </tr> 
  <tr> 
   <td> Erro ao enviar o MT<br /> </td> 
   <td> Falha<br /> </td> 
   <td> Erro ao enviar mensagens<br /> </td> 
   <td> Suave<br /> </td> 
   <td> Inacessível<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Para o conector SMPP genérico estendido**

Ao usar o protocolo SMPP para enviar mensagens SMS, a gestão de erros é tratada de forma diferente. Para obter mais informações sobre o conector SMPP genérico estendido, consulte [esta página](sms-set-up.md#creating-an-smpp-external-account).

O conector SMPP recupera dados da mensagem SR (Relatório do Status) que é retornada usando expressões regulares (regexes) para filtrar seu conteúdo. Esses dados são comparados com as informações encontradas na tabela **[!UICONTROL Delivery log qualification]** (disponível no menu **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**).

Antes de um novo tipo de erro ser qualificado, o motivo da falha é sempre definido como **Refused** por padrão.

>[!NOTE]
>Os tipos de falha e os motivos para falha são os mesmos dos emails. Consulte [Tipos e motivos de falha de delivery](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>Peça ao seu provedor uma lista de códigos e status de erros para definir os tipos apropriados de falhas e os motivos para falha na tabela de qualificação de log de delivery.

Exemplo de uma mensagem gerada:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* Todas as mensagens de erro começam com **SR** para distinguir códigos de erro de SMS de códigos de erro de email.
* A segunda parte (**Generic** neste exemplo) da mensagem de erro refere-se ao nome da implementação SMSC, como definido no campo **[!UICONTROL SMSC implementation name]** da conta externa do SMS. Consulte [esta página](sms-set-up.md#creating-an-smpp-external-account).

   Como o mesmo código de erro pode ter um significado diferente para cada provedor, esse campo permite que você saiba qual provedor gerou o código de erro. Você pode então encontrar o erro na documentação do provedor relevante.

* A terceira parte (**DELIVRD** neste exemplo) da mensagem de erro corresponde ao código de status recuperado do SR usando a extração de status regex definido na conta externa do SMS.

   Esse regex é especificado na guia **[!UICONTROL SMSC specificities]** da conta externa. Consulte [esta página](sms-set-up.md#creating-an-smpp-external-account).

   ![](assets/tech_quarant_error_regex.png)

   Por padrão, o regex extrai o campo **stat:** conforme definido pela seção **Apêndice B** da **especificação 3.4 SMPP**.

* A quarta parte (**000** neste exemplo) da mensagem de erro corresponde ao código de erro extraído do SR usando a extração de código de erro regex definida na conta externa do SMS.

   Esse regex é especificado na guia **[!UICONTROL SMSC specificities]** da conta externa. Consulte [esta página](sms-set-up.md#creating-an-smpp-external-account).

   Por padrão, o regex extrai o campo **err:** conforme definido pela seção **Apêndice B** da **especificação 3.4 SMPP**.

* Tudo que vem após o símbolo da barra vertical (|) é exibido somente na coluna **[!UICONTROL First text]** da tabela **[!UICONTROL Delivery log qualification]**. Este conteúdo é sempre substituído por **#MESSAGE#** após a mensagem ser normalizada. Esse processo evita ter várias entradas para erros semelhantes e é igual ao dos emails. Para obter mais informações, consulte [Qualificação de email de devolução](understanding-delivery-failures.md#bounce-mail-qualification).

O conector SMPP genérico estendido aplica uma heurística para encontrar valores padrão adequados: se o status começar com **DELIV**, é considerado um sucesso porque ele corresponde aos status comuns **DELIVRD** ou **DELIVERED** usados pela maioria dos provedores. Qualquer outro status gera uma falha grave.
