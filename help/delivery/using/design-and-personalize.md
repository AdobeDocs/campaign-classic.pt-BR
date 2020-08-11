---
title: Criar conteúdo personalizado
seo-title: Criar conteúdo personalizado
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c804745ae58a9bded885ac5aef32f019f43e82be
workflow-type: tm+mt
source-wordcount: '1269'
ht-degree: 37%

---


# Criar conteúdo personalizado {#build-personalized-content}

Ao criar o conteúdo da sua mensagem, tente evitar problemas comuns que possam impedir a execução de sua entrega. Na maioria das vezes, possíveis erros estão relacionados à [personalização](../../delivery/using/about-personalization.md), [formatação](../../delivery/using/defining-the-email-content.md#message-content) e [imagens](../../delivery/using/defining-the-email-content.md#adding-images).

## Otimizar personalização {#optimize-personalization}

Para evitar problemas comuns que podem impedir a execução da entrega e melhorar a experiência dos destinatários, o Adobe Campaign permite personalizar suas mensagens.

Você pode usar dados de recipient armazenados no banco de dados da Adobe Campaign ou coletados por meio de rastreamento, landings page, subscrições etc.
As noções básicas de personalização são apresentadas [nesta seção](../../delivery/using/personalization-fields.md).

Certifique-se de que o conteúdo da sua mensagem foi projetado corretamente para evitar erros, que geralmente estão relacionados à personalização.

**Dicas**: Em campos de personalização provenientes de arquivos externos fornecidos por fornecedores terceirizados, o conteúdo HTML externo pode estar incorreto. Para evitar isso, verifique a sintaxe, o uso de tags, caracteres etc. Por exemplo, uma tag de personalização do Adobe Campaign sempre tem o seguinte formulário: &lt;%=table.field%>. Para obter mais informações, consulte [esta seção](../../delivery/using/about-personalization.md).

O uso incorreto de parâmetros em alocos de personalização pode ser um problema. Por exemplo, as variáveis no JavaScript devem ser usadas da seguinte forma:

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

For more on personalization blocks, refer to the [this section](../../delivery/using/personalization-blocks.md).

Você pode preparar dados de personalização em um fluxo de trabalho para melhorar a análise de preparação de delivery. Isso deve ser usado especialmente se os dados de personalização vierem de uma tabela externa até o Federated Data Acces (FDA). Esta opção está descrita nesta [seção](../../delivery/using/personalization-fields.md#optimizing-personalization)

## Criar conteúdo otimizado {#optimize-content}

Ao criar seus e-mails, lembre-se das práticas recomendadas gerais abaixo.

* Mantenha o design simples

* Lembre-se dos usuários de dispositivos móveis

* Evite e-mails totalmente baseados em imagens

* Use fontes seguras para e-mails

* Codifique caracteres especiais

### Linha de assunto

Work on the [subject line](../../delivery/using/defining-the-email-content.md#message-content) to improve open rates:

* Evite assuntos muito longos. Use no máximo 50 caracteres

* Evite usar palavras repetitivas como &quot;grátis&quot; ou &quot;oferta&quot;, que podem ser consideradas spam

* Evite letras maiúsculas e caracteres especiais como &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

### Mirror page

Sempre inclua um link de mirror page. A posição preferencial é a parte superior do email. [Saiba mais](../../delivery/using/sending-messages.md#generating-the-mirror-page)

### Link de cancelamento de assinatura.

O link de unsubscription é essencial. Deve ser visível e válido e o formulário deve ser funcional. By default, when the message is analyzed, a [typology rule](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) checks whether an opt-out link has been included and generates a warning if it is missing.

**Dica**: Como o erro humano é sempre possível, verifique se o link para opção de não participação funciona corretamente antes de cada vez que você enviar. Por exemplo, ao enviar a prova, verifique se o link é válido, se o formulário está on-line e se o campo Não contate mais esse recipient foi alterado para Sim.

Saiba como inserir um link de opção de não participação [nesta seção](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

### Tamanho do email

Para evitar problemas de desempenho ou de entrega, o tamanho máximo recomendado de um email é de aproximadamente **35 KB**. To check the message size, go the **[!UICONTROL Preview]** tab and choose a test profile. Uma vez gerada a mensagem, seu tamanho será exibido no canto superior direito.

Para manter seu e-mail abaixo do limite, considere o seguinte:

* Remover estilos redundantes ou não utilizados

* Mover algum conteúdo de email para uma landing page

* Minifique seu código

Certifique-se de que testou as alterações antes do envio final

### Duração do SMS

Por padrão, o número de caracteres em um SMS atende aos padrões GSM (Global System for Mobile Communications). As mensagens SMS que usam a codificação GSM são limitadas a 160 caracteres ou a 153 caracteres por SMS para as mensagens enviadas em várias partes.

A transliteração consiste em substituir um caractere de um SMS por outro quando esse caractere não é considerado pelo padrão GSM. Observe que inserir campos de personalização no conteúdo de sua mensagem SMS pode introduzir caracteres que não são considerados pela codificação GSM. Você pode autorizar a transliteração de caracteres marcando a caixa correspondente na guia Configurações do canal SMPP da correspondente **[!UICONTROL External account]**.
Learn more [in this section](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Dicas**:

* Para manter todos os caracteres nas mensagens SMS como estão, para não alterar os nomes próprios, por exemplo, não ative a transliteração.

* No entanto, se suas mensagens SMS contiverem muitos caracteres que não forem considerados pelo padrão GSM, permita a transliteração para limitar os custos de envio das mensagens.

Learn more [in this section](../../delivery/using/sms-channel.md#about-character-transliteration).

## Trabalhar na formatação {#formatting}

Para evitar erros comuns de formatação, verifique os seguintes elementos:

* Correct **date formatting**: Adobe Campaign provides date formatting functions for the JavaScript templates and XSL stylesheets. [Saiba mais](../../delivery/using/formatting.md#date-display)

* Uso de caracteres **** autorizados em emails: a lista de caracteres válidos para endereços de email é definida na opção &quot;XtkEmail_Characters&quot;. Saiba como acessar as opções de Campanha [nesta seção](../../installation/using/configuring-campaign-options.md). Para lidar corretamente com caracteres especiais, o Adobe Campaign precisa ser instalado em Unicode.

* Configuração da autenticação de **email**: verifique se os cabeçalhos de email contêm a assinatura DKIM. A autenticação DKIM (Domain Keys Identified Mail) permite que o servidor de email de recebimento verifique se uma mensagem foi enviada pela pessoa ou entidade pela qual ela alega ter sido enviada e se o conteúdo da mensagem foi alterado entre o momento em que foi enviada originalmente (e o DKIM &quot;assinado&quot;) e o momento em que foi recebida. Normalmente, esse padrão usa o domínio no cabeçalho De ou Remetente. Para obter mais informações, consulte [esta seção](../../delivery/using/technical-recommendations.md#dkim).

### Design de email responsivo

O design responsivo de garante que um e-mail seja processado de maneira ideal para o dispositivo no qual ele é aberto.

* Use HTML responsivo de e-mail em vez de HTML para web

* Use o modo de visualização e envie provas para testar a renderização no máximo de dispositivos possível

* The Adobe Campaign Classic Digital Content Editor (DCE) module includes some responsive design formatted templates for mobile available via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Saiba mais [neste artigo](https://theblog.adobe.com/responsive-email-design-101/)

## Gestão de imagens {#manage-images}

Siga as diretrizes abaixo ao usar imagens.

### Impedir o bloqueio de imagens

Alguns clientes de e-mail bloqueiam imagens por padrão, e alguns usuários alteram suas configurações para impedir que imagens sejam salvas em caso de uso de dados. Portanto, se as imagens não forem baixadas, a mensagem inteira poderá ser perdida. Para evitar isso:

* Equilibre imagens e texto no seu conteúdo. Evite e-mails totalmente baseados em imagens.

* Se o texto precisa estar contido em uma imagem, use alt e title para garantir que sua mensagem seja exibida. Estilize o texto alt/title para melhorar a aparência.

* Evite o uso de imagens de fundo, pois elas não são suportadas por alguns clientes de e-mail.

### Tornar as imagens responsivas

Tente tornar as imagens responsivas e redimensionáveis. Observe que isso pode ter um impacto no custo, pois demora mais para ser criado.

### Usar referências de imagem absolutas

Para serem acessíveis de fora, as imagens usadas em emails e recursos públicos vinculados ao campanha devem estar presentes em um servidor acessível externamente.

* Você pode verificar se a configuração da instância ativa o gerenciamento de recursos públicos. [Saiba mais](../../installation/using/deploying-an-instance.md#managing-public-resources)

* No assistente do delivery, você pode importar uma página HTML contendo imagens ou inserir imagens diretamente usando o editor de HTML pelo ícone **[!UICONTROL Image]**. [Saiba mais](../../delivery/using/defining-the-email-content.md#adding-images)

* Se as imagens não forem exibidas, verifique se elas estão disponíveis no servidor. Para fazer isso, clique na guia Origem do seu delivery. Localize suas imagens e copie e cole o URL de cada imagem em um navegador da Web. Se as imagens não forem exibidas, entre em contato com seu administrador de TI ou com seu fornecedor, provendo-lhes seu conteúdo de entrega.

## Visualizar sua mensagem {#preview-msg}

A Adobe recomenda visualizar sua mensagem para verificar sua personalização e como seus destinatários verão a entrega.

* In the delivery wozard, the **[!UICONTROL Preview]** sub-tab lets you view the rendering of each content for a recipient. Os campos de personalização e os elementos condicionais do conteúdo são substituídos pelas informações correspondentes para o perfil selecionado. [Saiba mais](../../delivery/using/defining-the-email-content.md#message-content)

* Uma verificação automática de antisspam é executada durante cada pré-visualização. Na **[!UICONTROL Preview]** subguia, verifique a pontuação de spam do [SpamAssassin](../../delivery/using/spamassassin.md) .  Clique em **[!UICONTROL More...]** para saber mais sobre o aviso.  Antes de fazer isso, verifique se o SpamAssassin está instalado e configurado corretamente no servidor de aplicativos Adobe Campaign. [Saiba mais](../../installation/using/configuring-spamassassin.md)
