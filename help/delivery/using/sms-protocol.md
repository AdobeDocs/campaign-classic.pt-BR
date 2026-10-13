---
product: campaign
title: Protocolo e configurações do conector de SMS
description: Saiba mais sobre o conector SMS e como configurá-lo
feature: SMS
role: Developer
exl-id: fded088a-11a2-4b87-a368-7b197334aca4
TQID: 'https://experienceleague.adobe.com/-e39I2kK3veYtZTufN0ZZrnZPAAco47dU8HFlCtlIxY'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
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
  - id: b1bd1421-1927-4c59-9bc6-ce292360e43b
    internal-label: SMS Messaging
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '4785'
ht-degree: 98%
---
# Protocolo e configurações do conector de SMS {#sms-connector-protocol}

>[!NOTE]
>
>Por meio desse documento, todas as referências a detalhes sobre o protocolo, nomes de campos e valores se referem à [especificação SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).
>

Como parte da transição do Campaign v7 para o v8, o conjunto de documentações do Campaign Classic foi simplificado e reorganizado. Os recursos comuns agora estão disponíveis apenas no conjunto de documentações do Campaign v8. Para saber mais sobre as configurações do conector SMS, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account){target=_blank}.

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account){target=_blank}

## Visão geral {#overview}

O SMS pode limitar-se a enviar mensagens de texto curtas sem formatação, mas a sua simplicidade faz dele um canal de comunicação valioso.

Há duas formas principais de enviar um SMS:

* Enviá-lo manualmente por um telefone, a maneira habitual de se comunicar diretamente entre as pessoas.
* Enviá-lo pela Internet, da maneira como o Adobe Campaign envia mensagens. Para isso, você precisa de um provedor de serviço SMS que conecte a Internet à rede móvel.
O Adobe Campaign usa o protocolo SMPP para enviar SMS a um provedor de serviço.

Este documento o guiará durante a configuração da conexão entre o Adobe Campaign e um provedor SMPP.

Às vezes, os provedores SMPP podem se desviar da especificação oficial, mas o conector SMS no Adobe Campaign oferece muitas opções para adaptar o comportamento a fim de que seja compatível com a maioria dos provedores.

>[!IMPORTANT]
>
>A configuração de uma conexão com um novo provedor pode exigir algumas habilidades técnicas, conhecimentos de TCP, representação binária e hexadecimal e codificações de texto. Exigirá também a cooperação ativa com o provedor.

## Protocolo SMPP {#smpp-protocol}

O Adobe Campaign Classic oferece suporte ao protocolo SMPP versão 3.4. Esse é um protocolo generalizado que permite enviar SMS a um provedor (SMSC) e receber SMS, bem como recibos. Para obter mais informações, consulte a [documentação do SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

O equipamento de rede do lado do provedor de serviço SMS é frequentemente chamado de SMSC.

### Conexões SMPP {#smpp-connections}

O Adobe Campaign se conecta ao equipamento de rede do provedor de serviço SMS via TCP. O protocolo SMPP define conexões TCP permanentes do Adobe Campaign para o provedor. As conexões TCP são sempre iniciadas pelo Adobe Campaign, mesmo para receber mensagens.
O SMPP abre uma ou duas conexões TCP, dependendo de seu modo. Todas as conexões são sempre iniciadas pelo Adobe Campaign.

O protocolo SMPP pode funcionar de dois modos:

* **Transmissor+receptor (ou TX+RX)**: duas conexões TCP separadas são usadas para transmitir e receber mensagens.
* **Transceptor (ou TRX)**: uma única conexão TCP é usada para transmitir e receber mensagens.

>[!NOTE]
>
> O Adobe Campaign Classic dá suporte apenas ao modo TX+RX. Essa limitação se deve à sua arquitetura técnica.

### PDU SMPP {#smpp-pdu}

As unidades de transmissão SMPP (&quot;pacotes&quot;) são chamadas de PDUs. Uma **PDU** contém um comando, um status, um número de sequência e dados.

Cada PDU deve ser reconhecida por um `SMPP RESP PDU` (resposta síncrona). Os pedidos podem ser encaminhados: o remetente pode enviar vários comandos sem aguardar `RESP`. O número de solicitações que podem ser encaminhadas a qualquer momento é chamado de janela. `RESP PDU` pode chegar em qualquer ordem, independentemente da ordem da PDU do iniciador correspondente.

No modo separado **Transmissor+receptor**, a conexão usada depende do tipo de mensagem transmitida. A conexão do transmissor é usada para MT, e a conexão do receptor é usada para MO e SR. As solicitações e respostas para cada tipo de mensagem são enviadas pela mesma conexão TCP.

Por exemplo, ao enviar um MT, a conexão do transmissor é usada e o `RESP` que reconhece o MT também é enviado pelo canal do transmissor. Quando você recebe um MO (ou um SR), a conexão do receptor é usada para receber o MO e para enviar o `RESP` que reconhece o MO.

![](assets/do-not-localize/sms_protocol_1.png)

No Adobe Campaign Classic, para vincular o SR ao seu MT correspondente, uma ID é retornada pelo SMSC com as etapas `SUBMIT_SM_RESP` e `DELIVER_SM`. O identificador é armazenado no campo `providerId` da tabela `nms::providerMsgId` e está vinculado a `broadLogId` e `deliveryId`. Essa operação correspondente é feita pelo processo de SMS ao gravar no banco de dados.

Um `SUBMIT_SM_RESP PDU` bem-sucedido aciona o status de mensagem &quot;enviado&quot; no log de envio, enquanto um `DELIVER_SM (SR) PDU` bem-sucedido aciona o status de mensagem &quot;recebido&quot;.

### Aspectos de segurança {#security-aspects}

O protocolo em si não está criptografado. A maioria dos provedores implementa uma variante de IP na lista de permissões para que os endereços IP do servidor do Adobe Campaign sejam declarados ao provedor.

O Adobe Campaign oferece suporte para a passagem de um logon e uma senha durante a fase de associação. Também dá suporte a SMPP sobre TLS. Observe que são necessários certificados para garantir a segurança adequada. Embora o conector SMPP permita ignorar verificações de certificados, ele deve ser usado apenas para testes, já que TLS sem certificados fornece um nível de segurança significativamente menor.

O conector usa os certificados padrão fornecidos pela biblioteca `openssl` do sistema. Normalmente, é fornecido pelo diretório `/etc/ssl/certs` no Debian. Esse diretório é fornecido pelo pacote &quot;ca-certificates&quot; por padrão, mas pode ser personalizado.

### Informações em cada tipo de PDU {#information-pdu}

Cada tipo de PDU tem campos distintos que transportam informações diferentes. Essas PDUs estão detalhadas na especificação [SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

Cada seção abaixo descreve a PDU e sua resposta síncrona (`*_RESP PDU`). Todas as PDUs devem ser reconhecidas por um `RESP` correspondente. Essa é uma parte obrigatória da especificação.

As PDUs podem ter campos opcionais. Somente os campos mais comuns são descritos aqui. Consulte a especificação [SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) para obter mais informações.

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_TRANSCEIVER**

Esta PDU é usada para iniciar uma conexão com o SMSC. **Os modos Transmissor**, **Receptor** e **Transceptor** só mudam o tipo de SMS que pode ser transferido através dessa conexão, especificamente:

| Modo | Tipos de SMS permitidos |
|:-:|:-:|
| Transmissor | MT |
| Receptor | MO + SR |
| Transceptor | MT + MO + SR |

Campos de destaque em `BIND_* PDU`:

* **system_id**: logon usado para autenticação. Definido na conta externa.

* **senha**: Senha usada para autenticação. Definido na conta externa.

* **system_type**: definição obrigatória com um valor específico para alguns provedores. Definido na conta externa. Disponível em todas as versões. Muitas vezes, distingue entre diferentes tipos de contratos, canais, países etc.

* **addr_ton** e **addr_npi**: exigido por alguns provedores. Definido pelas configurações `Bind TON` e `Bind NPI` na conta externa.

* **address_range**: exigido por alguns provedores. Na maioria das vezes, é uma lista de códigos de atalho permitidos nessa conexão. Definido na conta externa.

`BIND_*_RESP` não tem um campo específico. Confirma se a conexão foi bem-sucedida ou não.

#### DESVINCULAR {#unbind}

Essa PDU deve ser enviada pelo sistema antes da desconexão. Deve aguardar a PDU `UNBIND_RESP` correspondente antes de fechar a conexão.

A conformidade com o SMSC não deve fechar a conexão. A conexão TCP é controlada pelo conector do Adobe Campaign.

#### SUBMIT_SM {#submit-sm}

Essa PDU envia um MT ao SMSC. A PDU de resposta fornece a ID do MT.

Campos de destaque em uma PDU `SUBMIT_SM`:

* **service_type**: exigido por alguns provedores. Definido nas propriedades da entrega.

* **source_addr_ton** e **source_addr_npi**: indica que tipo de endereço de origem é transmitido. O significado desses campos é padronizado, mas como alguns provedores o usam de forma diferente, você deve solicitar ao provedor o valor correto. Definido na conta externa.

* **source_addr**: o endereço de origem/oADC do MT. Será exibido no telefone celular. Definido na conta externa e na entrega, o valor na entrega tem precedência sobre o valor da conta externa.

* **dest_addr_ton** e **dest_addr_npi**: indica que tipo de endereço de destino é transmitido (por exemplo, formato local ou internacional). O significado desses campos é padronizado, mas como alguns provedores o usam de forma diferente, você deve solicitar ao provedor o valor correto. Definido na conta externa.

* **target_addr**: endereço, número de telefone ou MSISDN do destinatário.

* **esm_class**: usado para informar se UDH é usado ou não no campo de texto. Habilitado automaticamente pelo conector para SMS dividido se o modo `message_payload` não for usado.

* **priority_flag**: prioridade dessa mensagem sobre outras. É ligado à prioridade da própria entrega.

* **valid_period**: carimbo de data e hora após o qual nenhuma nova tentativa deve ser feita. Definido na própria entrega.

* **registered_delivery**: informa se um SR é solicitado ou não. O Adobe Campaign sempre define esse sinalizador, exceto para respostas automáticas. Para mensagens de várias partes, o sinalizador é definido somente para a primeira parte. Todas as versões têm o mesmo comportamento.

* **data_coding**: indica a codificação usada no campo de texto. Consulte a seção [codificação de texto SMS](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/sms/sms-channel#sms-text-encoding){target="_blank"} (documentação do Campaign v8) para obter mais informações.

* **short_message**: o texto da mensagem. Se UDH for usado, isso também conterá o cabeçalho UHD.

O Adobe Campaign é compatível com estes campos opcionais:

* **dest_addr_subunit**: usado para especificar o target do SMS: flash, dispositivo móvel ou cartão SIM. Definido nas propriedades da entrega.

* **message_payload**: quando habilitado na conta externa, mensagens longas serão enviadas em uma única PDU, e o texto será transmitido nesse campo, em vez do campo `short_message`.

#### SUBMIT_SM_RESP {#submit-sm-resp}

Esta PDU conterá a ID do MT. Isso é útil para corresponder ao SR recebido.

>[!IMPORTANT]
>
>Muitos provedores transmitem a ID do MT em hexadecimal. Defina o formato de ID **na configuração da notificação da MT** corretamente na conta externa.

Alguns provedores enviam `SUBMIT_SM_RESP` depois de enviar o SR. Para levar em conta esse comportamento, o Adobe Campaign aguarda 30 segundos antes de responder com a **ID de mensagem inválida** a um SR com uma ID desconhecida.

#### DELIVER_SM {#delivery-sm}

Essa PDU é enviada pelo SMSC para o Adobe Campaign. Ela contém um MO ou um SR.

A maioria dos campos tem o mesmo significado que sua contraparte `SUBMIT_SM`. Esta é a lista de campos úteis:

* **source_addr**: endereço de origem do MO/SR. Geralmente, é um número de telefone.

* **target_addr**: código curto que recebeu o MO ou o SR.

* **esm_class**: usado para informar se a PDU é um MO ou um SR.

* **short_message**: texto da mensagem. No caso de SR, contém os dados descritos no apêndice B da especificação do protocolo SMPP. Consulte [Gerenciamento de erros do SR](sms-protocol.md#sr-error-management) para obter mais detalhes.

O Adobe Campaign pode ler a ID da mensagem no campo opcional `receipted_message_id` com alguma configuração.

#### DELIVER_SM_RESP {#deliver-sm-resp}

Essa PDU é enviada pelo Adobe Campaign para reconhecer o SR e o MO.

O Adobe Campaign Classic reconhece o SR e o MO depois de inseridos no banco de dados. Alguns erros de processamento poderão ocorrer mesmo se uma PDU `DELIVER_SM_RESP` bem-sucedida tiver sido enviada. Essa limitação é causada pela arquitetura de software do Adobe Campaign Classic.

#### ENQUIRE_LINK {#enquire-links}

Essa PDU só é usada para verificar se a conexão está ativa. Sua frequência deve ser estabelecida de acordo com as necessidades do provedor.

Os 60 segundos padrão devem corresponder à maioria das configurações definidas na conta externa.

#### ENQUIRE_LINK_RESP {#enquire-links-resp}

Essa PDU reconhece que a conexão está ativa.

### SMS multiparte (SMS longo) {#multipart}

>[!IMPORTANT]
>
> O Adobe Campaign é compatível somente com SMS multiparte ou SMS longo para envio. UDH e `message_payload` não são compatíveis com o SMS de entrada (MO), o que significa que o MO é limitado a 160 caracteres.

### Limite e janelas de tráfego {#throughput-capping}

A maioria dos provedores exige um limite de rendimento para cada conexão SMPP. Isso pode ser feito por meio da definição de um número de SMS na conta externa. Observe que a limitação de rendimento ocorre por conexão. O rendimento efetivo total é o limite por conexão multiplicado pelo número total de conexões. Isso é detalhado na seção [Conexões simultâneas](sms-protocol.md#connection-settings).

Para atingir o máximo de rendimento possível, é necessário ajustar a janela de envio máxima. A janela de envio é o número de `SUBMIT_SM PDU`s que podem ser enviados sem esperar por um `SUBMIT_SM_RESP`. Consulte a seção [Configuração da janela de envio](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account#smpp-delays){target="_blank"} (documentação do Campaign v8) para obter mais detalhes.

### SR e gerenciamento de erros (&quot;Apêndice B&quot;) {#sr-error-management}

O protocolo SMPP define erros síncronos padrão em `RESP PDU`s, mas não define códigos de erro para SR. Cada provedor usa seus próprios códigos de erro com o respectivo significado.

Uma recomendação é feita na seção Apêndice B da [especificação do protocolo SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (página 167), mas não lista os códigos de erro reais nem o respectivo significado.

Para se adaptar ao gerenciamento de erros, o sistema de mensagem de banda larga do Adobe Campaign foi aproveitado para provisionar adequadamente os erros e sua gravidade (hardware, software etc.).

Como mencionado acima, existem dois tipos diferentes de erros:

* respostas síncronas em `SUBMIT_SM_RESP` que ocorrem imediatamente após a mensagem ser enviada ao SMSC
* recebimentos que poderão vir muito mais tarde, quando o celular tiver recebido a mensagem ou quando a mensagem expirar. Nesse caso, o erro é encontrado em um SR.

Quando um SR é recebido, o status e o erro podem ser encontrados em seu campo `short_message` (exemplo para implementações em conformidade com o Apêndice B). O campo `short_message` da PDU é frequentemente chamado de **campo de texto**, pois contém texto no MT. No caso de SR, contém informações técnicas, mais um subcampo chamado **Texto**. Esses dois campos são diferentes e `short_message` na verdade contém o campo **Texto** e outras informações.

Os conectores do Adobe Campaign Classic (exceto SMPP estendido) usam um comportamento codificado que depende do provedor selecionado. O SMPP genérico só distingue entre sucesso e erro, sem detalhes. O log de entrega pode conter algumas informações que não são garantidas.

#### Formato de campo de texto SR {#sr-text-field-format}

A especificação recomenda o uso desse formato para o campo de texto SR. É uma lista de subcampos, separados por espaços com dois-pontos para separar o nome do campo e seu valor. Os nomes de campo não diferenciam maiúsculas de minúsculas.

Exemplo de um campo de texto SR que corresponde à recomendação do Apêndice B:

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

O campo id é a ID recebida em `SUBMIT_SM_RESP PDU`, a confirmação do MT.

`sub` e `dlvrd` devem contar a quantidade de partes e mensagens entregues, mas isso não é usado pelo Adobe Campaign, já que o sistema de transmissão fornece informações melhores e mais integradas.

Os campos`submit date` e `done date` são carimbos de data e hora indicativos do envio do MT e do envio do SR pelo dispositivo móvel. Espere alguns problemas com fusos horários ou até mesmo carimbos de data e hora errados fornecidos por dispositivos móveis com data definida incorretamente.

O campo stat é importante, pois informa o status da mensagem. Os únicos status importantes são `DELIVRD`, `UNDELIV` e `REJECTD`. O status `DELIVRD` indica sucesso. Os outros dois indicam erro. Outros valores são possíveis, mas normalmente são notificações intermediárias; por exemplo, o MT chegou à operadora de celular, mas não ao telefone celular. Essas notificações intermediárias são ignoradas pelo Adobe Campaign.

O campo err contém o código de erro específico do provedor. O provedor deve fornecer uma tabela de possíveis códigos de erro, juntamente com o respectivo significado, para que seja possível interpretar esse valor.

Finalmente, o campo de texto geralmente contém o início do texto do MT. Isso é ignorado pelo Adobe Campaign, e alguns provedores não o transmitem para evitar o vazamento de informações de identificação pessoal e o consumo de largura de banda da rede. Ele pode ser usado durante a solução de problemas para detectar o SR que corresponde a um MT de teste, mais facilmente lendo esse campo.

### Exemplo de processamento SR no SMPP genérico estendido do Adobe Campaign Classic {#sr-processing}

Este exemplo exibe o caso de uma implementação seguindo a recomendação do Apêndice B, os valores padrão na conta externa e um SMS MT bem-sucedido.

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Primeiro, o regex `id extraction` é aplicado para extrair a ID e reconciliá-la com o MT correspondente.

Em seguida, os regex `status extraction` e `error code extraction` são aplicados para extrair esses campos e são anexados à string.

A mensagem de transmissão é criada com essas informações, e a string original inalterada é anexada para referência:

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

A mensagem é então normalizada, removendo a parte da MENSAGEM para poder corresponder a várias mensagens com os mesmos códigos de estado e erro.

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

Se a mensagem ainda não tiver sido provisionada na tabela de mensagens de transmissão, uma nova entrada será criada, usando a mensagem inteira como **firstText** e a mensagem normalizada. Em seguida, o conector usa o sucesso e o regex `error` para determinar se foi um sucesso ou uma falha:

* Se ele corresponder ao regex `success`, será considerado um sucesso.

* Se ele corresponder ao regex `error`, a mensagem será qualificada como um erro.

* Se nenhum desses dois regex for correspondente, o SR será ignorado. Pode ser uma notificação intermediária, que não é tratada pelo Adobe Campaign.

Por padrão, todos os erros são provisionados como erros leves. Isso significa que os erros graves devem ser provisionados manualmente.

## Parâmetros de conta externa SMPP {#SMPP-parameters-external}

Cada implementação do protocolo SMPP tem muitas variações. Para melhorar a compatibilidade e a adaptabilidade, há várias configurações disponíveis para alterar o comportamento do conector SMPP. Esta seção descreve cada parâmetro e seus efeitos no conector.

### Parâmetros gerais e roteamento {#general-parameters-routing}

**Limitar instâncias de MTA para esta conta**

É possível definir um limite para o número de instâncias de MTA permitidas para se conectar ao provedor de SMPP. Quando marcado, você pode especificar quantos MTAs podem ser usados no máximo.

Essa opção permite um controle mais fino sobre o número de conexões. Consulte [Conexões simultâneas](sms-protocol.md#connection-settings).

Se você definir um valor maior que o número de MTAs em execução, todos os MTAs serão executados normalmente: essa opção é apenas um limite e não pode gerar MTAs adicionais.

Se você precisar controlar com precisão o número de conexões (por exemplo, o requisito do provedor), será recomendável sempre definir essa opção, mesmo se a implantação atual tiver o número correto de MTAs em execução. Se MTAs forem adicionados posteriormente, o limite de conexão continuará a ser respeitado.

### Configurações de conexão {#connection-settings}

#### Nome da implementação SMSC {#smsc-implementation-name}

Define o nome da implementação SMSC. Ele deve ser definido com o nome do seu provedor. Entre em contato com o administrador ou com a equipe de capacidade de entrega para saber o que adicionar a esse campo. A função desse campo é descrita na seção [Gerenciamento de erro do SR](sms-protocol.md#sr-error-management).

>[!NOTE]
>
>O compromisso da equipe de capacidade de entrega é baseado no contrato e os clientes devem entrar em contato com seu representante da Adobe para obter informações relacionadas ao compromisso de capacidade de entrega.

#### Número de conexões filho do MTA {#number-mta-child}

No Adobe Campaign Classic, define o número de conexões por filho do MTA.

O conector Adobe Campaign Classic Extended SMPP pode controlar o número de conexões por filho do MTA. Para controlar o limite global de conexões, você terá que limitar o número de processos de filho do MTA, o que geralmente significa ter uma plataforma mid-sourcing dedicada para SMS.

Para o Adobe Campaign Classic, pode haver um número diferente de conexões de receptor e transmissor:

* **Conexões do transmissor = número de conexões filhas do MTA * número de processos filhos do MTA * número de MTAs (se a resposta automática estiver definida) * número de conexões filhas do MTA**

Como sugerido acima, o processo de SMS do Adobe Campaign Classic abrirá mais conexões de transmissor se a resposta automática estiver habilitada. Essas conexões extras são usadas para enviar as respostas automáticas.

* **Conexões de receptor = número de conexões filho do MTA**

Se você configurar respostas automáticas, o processo SMS abrirá pares de transmissores/receptores, aumentando o número de conexões de transmissores. Se você não tiver configurado nenhuma resposta automática, ela abrirá somente as conexões do receptor.

#### Habilitar TLS em SMPP {#enable-TLS}

Use o TLS para se conectar ao provedor. A conexão será criptografada. A conexão TLS é gerenciada pela biblioteca OpenSSL. Qualquer item aplicável ao OpenSSL será verdadeiro para essa conexão.

#### Habilitar rastreamentos SMPP detalhados no arquivo de log {#enable-verbose-log-file}

Essa configuração descarta todo o tráfego SMPP no arquivos de log. Geralmente é necessário ajustar parâmetros durante a configuração inicial. Isso deve ser habilitado ao solucionar problemas do conector e comparado ao tráfego visto pelo provedor.

No Adobe Campaign Classic, o output do log está no log de MTA para tráfego relacionado ao MT e no log de SMS para tráfego relacionado ao MO e ao SR.

### Configuração de conexão do receptor {#receiver-connection}

Essa seção só é visível no modo separado de **transmissor+receptor**.

#### Use parâmetros diferentes para o receptor {#receiver-parameters}

Quando a caixa está desmarcada, as mesmas configurações são usadas para transmissor e receptor.

Quando a caixa estiver marcada, as configurações na seção **Configurações de conexão** serão aplicadas ao transmissor e as configurações nas configurações **Conexão do receptor** serão aplicadas ao receptor.

**Servidor do receptor, porta, conta, senha, tipo de sistema**

Essas configurações se aplicam ao receptor quando no modo transmissor+receptor. Elas funcionam como a parte transmissora. Veja mais detalhes acima.

### Configurações de canal de SMPP {#smpp-channel-settings}

#### Armazenar o MO recebido no banco de dados {#incoming-mo-storing}

Quando habilitado, o MO recebido será armazenado na tabela inSMS do banco de dados. Esta tabela pode ser consultada usando a atividade de query de qualquer fluxo de trabalho.

O Adobe Campaign Classic sempre armazena todos os MOs no banco de dados do InSMS. Portanto, essa opção não está disponível.

#### Habilitar atualizações de KPI em tempo real durante o processamento de SR {#real-time-kpi}

Quando habilitados, os KPIs serão atualizados em tempo real na página principal da entrega ao receber o SR do erro.

A desvantagem pode ser o baixo desempenho devido à contenção do banco de dados gerado. Se desabilitadas, as estatísticas são atualizadas pelo fluxo de trabalho **syncformexec** , em execução a cada 20 minutos.

O Adobe Campaign Classic tem um mecanismo totalmente diferente para KPIs. Portanto, essa opção não está disponível.

#### Código curto {#short-code}

Indica o código curto principal da conta. Se vários códigos curtos forem usados para esta conta ou se o código curto for desconhecido, deixe este campo vazio.

A especificação de código curto é útil para dois recursos:

* A visualização exibirá o código curto se nenhum número de origem for fornecido. Isso refletirá o verdadeiro comportamento do dispositivo móvel.

* A configuração de lista de bloqueios do recurso de resposta automática só envia para a quarentena o usuário para um código curto específico.

### Especificações do SMSC {#SMSC-specifics}

Essas são configurações avançadas que adaptam o conector do Adobe Campaign à maioria das peculiaridades de implementação do SMPP.

#### Ignorar verificação de certificado TLS {#skip-tls}

Quando o TLS estiver habilitado, ignorar todas as verificações de certificado.

Quando marcado, a conexão não é mais segura. Ela não deve ser habilitada na produção.

Pode ser útil para depuração ou teste.

Você pode escolher entre três valores diferentes para a validação do certificado:

* Verificação de certificação completa (incluindo o nome do host), padrão.
* Ignorar a verificação do nome do host.
* Ignorar a verificação do certificado.

#### Regex aplicado para determinar o status de sucesso/erro {#regex-applied}

Quando mensagens com uma combinação desconhecida de campo de estado/erro são encontradas, esses regex são aplicados no campo de estado para determinar se o SR teve êxito ou se ocorreu um erro. Um SR com valores de estado que não correspondem a nenhum desses regex é ignorado.

Por padrão, valores de estado que começam com `DELIV`, por exemplo, `DELIVRD` no [Apêndice B](sms-protocol.md#sr-error-management), são considerados entregues com êxito, e todos os valores de estado que correspondem a erros, por exemplo, `REJECTED`, `UNDELIV`, são considerados erros.

#### Formato de ID na confirmação MT {#id-format-mt}

Isso indica o formato da ID retornada no campo `message_id` de `SUBMIT_SM_RESP PDU`.

* **Não modificar**: a ID é armazenada como está no banco de dados, como texto codificado em ASCII. Não ocorre pré-processamento nem filtragem.

* **Número decimal**: espera-se que a ID seja um número decimal no formato ASCII. Espaços à esquerda e à direita e zeros à esquerda são removidos quando essa configuração é usada.

* **Número hexadecimal**: espera-se que a ID seja um número hexadecimal no formato ASCII, sem “0x” à esquerda nem “h” à direita. A ID é convertida em um número decimal antes de ser armazenada no banco de dados.

* **String hexadecimal**: espera-se que a ID seja um texto codificado em ASCII que seja uma string de bytes codificada como hexadecimal. Por exemplo, na PDU, você encontrará `0x34 0x31 0x34 0x32 0x34 0x33`, o que significa ASCII &quot;414243&quot;. Essa string é então decodificada como uma string hexadecimal de bytes, e você obtém &quot;ABC&quot; como resultado: você armazenará a ID &quot;ABC&quot; no banco de dados.

#### Formato de ID no SR {#id-format-sr}

Isso indica o formato da ID capturada pelo regex `Extraction` da ID no SR. Os valores têm o mesmo significado e o mesmo comportamento que o formato no MT acima.

**ID SR ou código de erro no campo opcional**

>[!NOTE]
>
>Disponível apenas no conector SMPP Estendido do Adobe Campaign Classic.

Se marcado, o conteúdo dos campos opcionais será anexado ao texto processado pelos regex acima. O texto terá o formato `0xTAG:VALUE`, `0xTAG` sendo o valor hexadecimal de quatro dígitos da tag em maiúsculas, por exemplo, `0x002E`.

Por exemplo, convém capturar a ID no campo `receipted_message_id`. Para isso, habilite essa caixa de seleção. O seguinte texto será adicionado ao status:

```
0x001E:05e3299e-8d37-49d0-97c6-8e4fe60c7739
```

Neste exemplo, 0x001E é a tag do campo opcional, e o UUID é o valor do campo.

Para capturar esse valor, agora é possível definir o seguinte regex no regex de Extração da ID no campo SR:

```
\b0x001E:([0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})\b
```

>[!IMPORTANT]
>
>Você só pode capturar campos opcionais que tenham valores de texto (ASCII/UTF-8). Especificamente, os campos binários não podem ser capturados de forma confiável pelo sistema de regex atual.

**Tag de ID de serviço**

Permite adicionar um TLV personalizado. Esse campo define a parte da tag. O valor pode ser personalizado por entrega no valor **ID de serviço ou programa** nos parâmetros avançados da entrega.

Essa configuração permite adicionar apenas uma opção TLV por mensagem.

### Resposta automática enviada ao MO {#automatic-reply}

>[!IMPORTANT]
>
>No Adobe Campaign Classic e em uma arquitetura híbrida, a aplicação da resposta automática ao conector SMPP estendido requer a adição de acesso de gravação para o operador mid na pasta **Conta externa**.

Esse recurso permite responder rapidamente ao texto para o MO e processar o envio por código curto para a lista de bloqueios.

As colunas **Palavra-chave** e **Código curto** definem condições para acionar a resposta automática. Se ambos os campos forem correspondentes, o MO será enviado, e a ação adicional será acionada. Para especificar um curinga, deixe o campo vazio. A palavra-chave corresponde à primeira palavra alfanumérica no texto MO, ignorando a pontuação e os espaços à esquerda. Isso significa que o campo **Palavra-chave** não pode conter espaços e deve ser uma única palavra.

A configuração **Palavra-chave** é um prefixo. Por exemplo, se você especificar &quot;AD&quot;, ele corresponderá a &quot;AD&quot;, &quot;ADAPT&quot; e &quot;ADOBE&quot;. Se houver várias palavras-chave com um prefixo comum, será necessário prestar atenção à ordem, já que as palavras-chave são processadas de cima para baixo.

A coluna **Responder** é o texto a ser respondido. Nenhuma personalização está disponível nesse campo. Se você deixar esse campo vazio, nenhuma mensagem será respondida, mas a ação adicional será acionada mesmo assim.

A coluna **Ação adicional** fornece uma ação extra quando a **Palavra-chave** e o **Código curto** são correspondentes. Um código curto vazio corresponde a todos os códigos curtos. Você pode enviar para a quarentena ou remover da quarentena. O valor &quot;nenhum&quot; responde ao texto. Se você especificar uma **Ação adicional**, mas deixar o campo **Responder** vazio, a ação será executada, mas nenhuma resposta será enviada. A quarentena é aplicada somente ao código curto especificado, ou a todos os códigos curtos, se o campo está vazio.

>[!IMPORTANT]
>
>A configuração de envio de número de telefone completo afeta o comportamento do mecanismo de quarentena de resposta automática: se o número de telefone completo não estiver marcado, o número de telefone colocado em quarentena receberá um sinal de mais (&quot;+&quot;) para torná-lo compatível com o formato de número de telefone internacional.

Todas as entradas na tabela são processadas na ordem especificada, até que uma regra seja correspondente. Se várias regras corresponderem a um MO, somente a regra mais alta será aplicada.

## Parâmetros de modelo de entrega do SMS {#sms-delivery-template-parameters}

Alguns parâmetros podem ser definidos por modelo de entrega.

### Parâmetros de entrega {#delivery-parameters}

#### Modo de transmissão {#transmission-mode}

Esse campo indica o tipo de SMS que você deseja transferir: mensagens normais ou em flash, armazenando no celular ou no cartão SIM.

Essa configuração é transmitida no campo opcional `dest_addr_subunit` em `SUBMIT_SM PDU`.

* **Não especificado** não envia nenhum campo opcional na PDU.

* **Flash** define o valor como 1. Ele envia uma mensagem flash que é exibida no dispositivo móvel e não é armazenada na memória.

* **Normal** define o valor como 0. Envia uma mensagem normal.

* **Salvar no dispositivo móvel** define o valor como 2. Ele instrui o telefone a armazenar o SMS na memória interna.

* **Salvar no terminal** define o valor como 3. Ele instrui o telefone a armazenar o SMS no cartão SIM.

#### Período de validade {#validity-period}

O período de validade é transmitido no campo `validity_period` de `SUBMIT_SM PDU`. A data é sempre formatada como um formato de hora UTC absoluto. O campo de data terminará com &quot;00+&quot;.

## Conector SMPP genérico estendido {#acc-extended-connector}

![](assets/do-not-localize/sms_protocol_4.png)

As setas representam fluxos de dados.

Ao enviar partes da entrega, o MTA gera filhos de MTA. O número de processos filhos de MTA é dinâmico e depende de uma configuração em serverConf.xml. Cada filho de MTA instancia o conector `CSmppConnectorWorker` que se conecta ao provedor SMPP. As conexões serão mantidas ativas enquanto o filho do MTA for mantido ativo. Também configurável em serverConf.xml.

O processo SMS processa apenas o SR. Ele se conecta ao provedor e deixa a conexão aberta. O processo é reconectado a cada 10 minutos para recarregar novas configurações. Essa é uma operação normal.

### Correspondência de MT, SR e entradas de broadlog {#matching-mt}

Uma tabela intermediária `nmsProviderMsgId` é usada para armazenar temporariamente dados MT e SR antes de ser enviada assincronamente ao catálogo.

A tabela `nmsProviderMsgId` tem três grupos de colunas:

* Colunas atualizadas quando um MT é enviado e confirmado: `iBroadLogId`, `iDeliveryId`

* Colunas atualizadas quando um SR é recebido: `iMsgId`, `iStatus`

* Colunas que são sempre atualizadas: `tsCreated`, `sProviderId`

Quando o MT e o SR terminarem o processamento, você deverá ter linhas completas, com informações de status e de transmissão.

Aqui, `iMsgId` está vinculado à tabela `nmsBroadLogMsg`, indicando a mensagem de erro/status completo.

O processo SMS verifica se há linhas completas a cada minuto e, em seguida, as processa assincronamente:

* A linha completa é lida.
* O processo SMS calcula o nome da tabela de log de fluxo com base no mapeamento de entrega.
* O processo SMS atualiza a tabela de catálogo com a ID da mensagem e o status.

**Conexões paralelas e de tráfego**

Cada filho de MTA cria uma quantidade configurável de conexões. Portanto, limitar o número de filhos de MTA limitará o número de conexões. Como a correlação entre os processos filhos e o tráfego do MTA está correlacionada, isso pode ser controlado, mas ainda assim ser um pouco imprevisível.
