---
product: campaign
title: Enviar emails em dispositivos móveis japoneses com o Adobe Campaign Classic
description: Saiba como configurar, criar e enviar emails que serão lidos em um dispositivo móvel japonês
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Email, Email Design
role: User
hide: true
exl-id: 44634227-2340-49c4-b330-740c739ea551
TQID: https://experienceleague.adobe.com/-IaAfjCvy9znHFt89tg-gGkcbAHpJExugPFr9T6RwWA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 738
ht-degree: 100%

---

# Enviar emails em dispositivos móveis japoneses {#sending-emails-on-japanese-mobiles}

## Formatos de email para celulares japoneses {#email-formats-for-japanese-mobiles}

O Adobe Campaign gerencia três formatos específicos em japonês para email em dispositivos móveis: **Deco-mail** (celulares DoCoMo), **Decore Mail** (celulares Softbank) e **Decoration Mail** (celulares KDDI AU). Esses formatos impõem restrições específicas de codificação, estrutura e tamanho. Saiba mais sobre limitações e recomendações [nesta seção](#limitations-and-recommendations).

Para que o destinatário receba corretamente mensagens em um desses formatos, recomendamos selecionar **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** ou **[!UICONTROL Decoration Mail (KDDI AU)]** no perfil correspondente:

![](assets/deco-mail_03.png)

No entanto, se você deixar a opção **[!UICONTROL Email format]** como **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** ou **[!UICONTROL Text]**, o Adobe Campaign detectará automaticamente (ao enviar o email) o formato japonês a ser usado para que a mensagem seja exibida corretamente.

Esse sistema de detecção automática baseia-se na lista de domínios predefinidos no conjunto de regras de email **[!UICONTROL Management of Email Formats]**. Para saber mais sobre gestão de formatos de email, consulte [esta página](../../installation/using/email-deliverability.md#managing-email-formats).

## Limitações e recomendações {#limitations-and-recommendations}

Determinado número de restrições se aplica no envio de emails que serão lidos em um dispositivo móvel operado por um provedor japonês (Softbank, DoCoMo, KDDI AU).

Portanto, você deve:

* Usar somente imagens no formato JPEG ou GIF
* Criar uma entrega com seções de texto e HTML que são estritamente inferiores a 10.000 bytes (para KDDI AU e DoCoMo)
* Usar imagens com tamanho total (antes de codificar) abaixo de 100 KB
* Usar até 20 imagens por mensagem
* Usar um formato HTML de tamanho reduzido (um número limitado de tags está disponível para cada operador)

>[!NOTE]
>
>Limitações específicas a cada operador devem ser consideradas ao criar sua mensagem. Consulte a documentação do produto.


## Testar o conteúdo do email {#testing-the-email-content}

### Pré-visualizar a mensagem {#previewing-the-message}

O Adobe Campaign permite verificar se o formato da mensagem é compatível com um celular japonês.

Após definir seu conteúdo e inserir o assunto do email, você poderá verificar a exibição e a formatação quando a mensagem for criada.

Na guia **[!UICONTROL Preview]** da janela de edição de conteúdo, ao clicar em **[!UICONTROL More... > Deco-mail diagnostic]** você poderá:

* Verifique se as tags de conteúdo HTML estão em conformidade com as restrições do formato japonês
* Verifique se o número de imagens na mensagem não excede o limite imposto pelo formato (20 imagens)
* Verifique o tamanho total da mensagem (até 100kB)

  ![](assets/deco-mail_06.png)

### Executar regra de tipologia {#running-typology-rule}

Além do diagnóstico de pré-visualização, uma segunda verificação é realizada ao enviar uma prova ou uma entrega: uma regra de tipologia específica, **[!UICONTROL Deco-mail check]**, é iniciada durante a análise.

>[!IMPORTANT]
>
>Essa regra de tipologia só será executada se pelo menos um dos destinatários estiver configurado para receber emails no formato **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** ou **[!UICONTROL Decoration Mail (KDDI AU)]**.

Essa regra de tipologia permite verificar se a entrega respeita as [restrições de formato](#limitations-and-recommendations) definidas pelos operadores japoneses, especialmente em relação ao tamanho total do email, ao tamanho das seções HTML e de texto, ao número de imagens nas mensagens e às tags no conteúdo HTML.

### Enviar provas {#sending-proofs}

Você pode enviar provas para testar sua entrega. Quando você envia a prova, se estiver usando endereços de substituição, digite os endereços que correspondem ao formato do email do perfil usado.

Por exemplo, você pode substituir o endereço de um perfil por test@softbank.ne.jp, se o formato do email desse perfil tiver sido definido antecipadamente no **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

## Enviar mensagens {#sending-messages}

Para enviar um email para destinatários com formatos de email japoneses com o Campaign, há duas opções:

* Criar duas entregas: uma somente para destinatários japoneses e outra para outros destinatários. Consulte [esta seção](#designing-a-specific-delivery-for-japanese-formats).
* Criar uma única entrega e o Adobe Campaign detectará automaticamente o formato a ser usado. Consulte [esta seção](#designing-a-delivery-for-all-formats).

### Criar uma entrega específica para formatos japoneses {#designing-a-specific-delivery-for-japanese-formats}

Você pode criar um fluxo de trabalho que contenha duas entregas: uma para ser lida em um celular japonês e outra para destinatários com formato do email padrão.

Para fazer isso, use a atividade **[!UICONTROL Split]** no fluxo de trabalho e defina os formatos de email japonês (Deco-mail, Decoration Mail e Decore Mail) como condições de filtragem.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### Criar uma entrega para todos os formatos {#designing-a-delivery-for-all-formats}

Quando o Adobe Campaign gerencia dinamicamente os formatos de acordo com o domínio (perfis com formatos de email definidos como **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** ou **[!UICONTROL Text]**), você pode enviar a mesma entrega a todos os destinatários.

O contato da mensagem será exibido corretamente para os usuários em celulares japoneses, assim como para os destinatários padrão.

>[!IMPORTANT]
>
>Respeite os recursos especiais associados a cada formato do email japonês (Deco-mail, Decoration Mail e Decore Mail). Para obter mais informações sobre as limitações, consulte [esta seção](#limitations-and-recommendations).
