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
translation-type: ht
source-git-commit: c804745ae58a9bded885ac5aef32f019f43e82be
workflow-type: ht
source-wordcount: '1269'
ht-degree: 100%

---


# Criar conteúdo personalizado {#build-personalized-content}

Ao criar o conteúdo da sua mensagem, tente evitar problemas comuns que possam impedir a execução do delivery. Na maioria das vezes, possíveis erros estão relacionados à [personalização](../../delivery/using/about-personalization.md), [formatação](../../delivery/using/defining-the-email-content.md#message-content) e [imagens](../../delivery/using/defining-the-email-content.md#adding-images).

## Otimizar personalização {#optimize-personalization}

Para evitar problemas comuns que podem impedir a execução do delivery e melhorar a experiência dos recipients, o Adobe Campaign permite personalizar suas mensagens.

Você pode usar os dados dos recipients armazenados no banco de dados do Adobe Campaign ou coletados por meio de rastreamento, páginas iniciais, assinaturas, etc.
As noções básicas de personalização são apresentadas [nesta seção](../../delivery/using/personalization-fields.md).

Verifique se o conteúdo da sua mensagem foi projetado corretamente para evitar erros, que geralmente estão relacionados à personalização.

**Dicas**: em campos de personalização provenientes de arquivos externos disponibilizados por fornecedores terceirizados, o conteúdo HTML externo pode estar incorreto. Para evitar isso, verifique a sintaxe, o uso de tags, caracteres, etc. Por exemplo, uma tag de personalização do Adobe Campaign apresenta sempre o seguinte formato: &lt;%=table.field%>. Para obter mais informações, consulte [esta seção](../../delivery/using/about-personalization.md).

O uso incorreto de parâmetros em blocos de personalização pode ser um problema. Por exemplo, as variáveis em JavaScript devem ser usadas da seguinte forma:

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

Para obter mais informações sobre blocos de personalização, consulte [esta seção](../../delivery/using/personalization-blocks.md).

Você pode preparar dados de personalização em um workflow para melhorar a análise de preparação de delivery. Isso deve ser usado se os dados de personalização vierem de uma tabela através do Federated Data Access (FDA). Esta opção está descrita nesta [seção](../../delivery/using/personalization-fields.md#optimizing-personalization)

## Criar conteúdo otimizado {#optimize-content}

Ao criar e-mails, lembre-se das práticas recomendadas gerais abaixo.

* Mantenha o design simples

* Lembre-se dos usuários de dispositivos móveis

* Evite criar emails só com imagens

* Use fontes seguras para emails

* Codifique caracteres especiais

### Linha de assunto

Trabalhe a [linha de assunto](../../delivery/using/defining-the-email-content.md#message-content) para melhorar as taxas de abertura:

* Evite assuntos muito longos. Use no máximo 50 caracteres

* Evite usar palavras repetitivas como “grátis” ou “oferta”, que podem ser consideradas spam

* Evite letras maiúsculas e caracteres especiais como “!”, “£”, “€” e “$”.

### Mirror page

Sempre inclua um link de mirror page. A posição preferencial é a parte superior do email. [Saiba mais](../../delivery/using/sending-messages.md#generating-the-mirror-page)

### Link de unsubscription

O link de unsubscription é essencial. Deve ser visível e válido e o formulário deve ser funcional. Por padrão, quando a mensagem é analisada, uma [regra de tipologia](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) verifica se um link para opção de não participação foi incluído e gera um aviso caso este esteja ausente.

**Dica**: como o erro humano é sempre possível, verifique se o link para opção de não participação funciona corretamente antes de cada envio. Por exemplo, ao enviar a prova, verifique se o link é válido, se o formulário está online e se o campo “Não contatar mais este recipient” foi alterado para Sim.

Veja [nesta seção](../../delivery/using/personalization-blocks.md#personalization-blocks-example) como inserir um link para opção de não participação.

### Tamanho do email

Para evitar problemas de desempenho ou de delivery, o tamanho máximo recomendado de um email é de aproximadamente **35 KB**. Para verificar o tamanho da mensagem, acesse a guia **[!UICONTROL Preview]** e escolha um perfil de teste. Uma vez gerada a mensagem, seu tamanho será exibido no canto superior direito.

Para manter o email abaixo do limite, considere o seguinte:

* Remover estilos redundantes ou em desuso

* Mover um conteúdo de email para uma página inicial

* Minimizar o uso de código

Verificar se você testou as alterações antes do envio final

### Duração do SMS

Por padrão, o número de caracteres em um SMS atende aos padrões do GSM (Global System for Mobile Communications). As mensagens SMS que usam a codificação GSM são limitadas a 160 caracteres ou a 153 caracteres por SMS para as mensagens enviadas em várias partes.

A transliteração consiste em substituir um caractere de um SMS por outro quando esse caractere não é considerado pelo padrão GSM. Observe que a inserção de campos de personalização no conteúdo da mensagem SMS pode inserir caracteres que não são considerados pela codificação GSM. Você pode autorizar a transliteração de caracteres marcando a caixa correspondente na guia Configurações do canal SMPP da **[!UICONTROL External account]** correspondente.
Saiba mais [nesta seção](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Dicas**:

* Para manter todos os caracteres inalterados nas mensagens SMS, a fim de não alterar os nomes próprios por exemplo, não ative a transliteração.

* No entanto, se suas mensagens SMS contiverem muitos caracteres que não forem considerados pelo padrão GSM, habilite a transliteração para limitar os custos de envio das mensagens.

Saiba mais [nesta seção](../../delivery/using/sms-channel.md#about-character-transliteration).

## Trabalhar na formatação {#formatting}

Para evitar erros comuns de formatação, verifique os seguintes elementos:

* **Formato de data** correto: o Adobe Campaign fornece funções de formatação de data para modelos JavaScript e folha de estilos XSL. [Saiba mais](../../delivery/using/formatting.md#date-display)

* Uso de **caracteres autorizados** em emails: a lista de caracteres válidos para endereços de email é definida na opção &quot;XtkEmail_Characters&quot;. Saiba como acessar as opções do Campaign [nesta seção](../../installation/using/configuring-campaign-options.md). Para trabalhar corretamente com caracteres especiais, o Adobe Campaign precisa ser instalado em Unicode.

* Configuração da **autenticação de email**: verifique se os cabeçalhos de email contêm a assinatura DKIM. Com a autenticação DKIM (Domain Keys Identified Mail), o servidor de email de recebimento pode verificar se uma mensagem foi enviada pela pessoa ou entidade que alega tê-la enviado e se o conteúdo da mensagem foi alterado entre o momento em que foi originalmente enviada (e o DKIM “assinado”) e o momento em que foi recebida. Em geral, esse padrão usa o domínio no cabeçalho “De” ou “Remetente”. Para obter mais informações, consulte [esta seção](../../delivery/using/technical-recommendations.md#dkim).

### Design de email responsivo

O design responsivo garante que o email seja processado de maneira ideal para o dispositivo no qual ele é aberto.

* Use HTML responsivo de email em vez de HTML para web

* Use o modo de visualização e envie provas para testar a renderização no máximo de dispositivos possível

* O módulo do Editor de conteúdo digital (DCE) do Adobe Campaign Classic inclui alguns modelos formatados com design responsivo disponíveis em **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Saiba mais [neste artigo](https://theblog.adobe.com/responsive-email-design-101/)

## Gestão de imagens {#manage-images}

Siga as diretrizes abaixo ao usar imagens.

### Impedir o bloqueio de imagens

Alguns clientes de e-mail bloqueiam imagens por padrão, e alguns usuários alteram suas configurações para impedir que imagens sejam salvas em caso de uso de dados. Portanto, se as imagens não forem baixadas, a mensagem inteira poderá ser perdida. Para evitar isso:

* Equilibre imagens e texto no seu conteúdo. Evite e-mails totalmente baseados em imagens.

* Se o texto precisa estar contido em uma imagem, use alt e title para garantir que sua mensagem seja exibida. Estilize o texto alt/title para melhorar a aparência.

* Evite o uso de imagens de fundo, pois elas não são suportadas por alguns clientes de e-mail.

### Tornar as imagens responsivas

Tente tornar as imagens responsivas e redimensionáveis. Observe que isso pode ter um impacto no custo, pois demora mais para ser criado.

### Usar referência de imagem absoluta

Para serem acessadas de fora, as imagens usadas em emails e recursos públicos vinculados a campanhas devem estar presentes em um servidor acessível externamente.

* Você pode verificar se a configuração da instância ativa o gerenciamento de recursos públicos. [Saiba mais](../../installation/using/deploying-an-instance.md#managing-public-resources)

* No assistente do delivery, você pode importar uma página HTML contendo imagens ou inserir imagens diretamente usando o editor de HTML pelo ícone **[!UICONTROL Image]**. [Saiba mais](../../delivery/using/defining-the-email-content.md#adding-images)

* Caso as imagens não sejam exibidas, verifique se elas estão disponíveis no servidor. Para fazer isso, clique na guia Origem no delivery. Localize suas imagens e copie e cole o URL de cada imagem em um navegador da web. Caso as imagens não sejam exibidas, entre em contato com o administrador de TI ou fornecedor terceirizado e disponibilize seu conteúdo de delivery.

## Visualizar sua mensagem  {#preview-msg}

A Adobe recomenda visualizar a mensagem para verificar a personalização e como os recipients verão o delivery.

* No assistente de delivery, a subguia **[!UICONTROL Preview]** permite visualizar a renderização de cada conteúdo para um recipient. Os campos de personalização e os elementos condicionais do conteúdo são substituídos pelas informações correspondentes para o perfil selecionado. [Saiba mais](../../delivery/using/defining-the-email-content.md#message-content)

* Uma verificação automática de antispam é executada durante cada pré-visualização. Na subguia **[!UICONTROL Preview]**, verifique a pontuação de spam do [SpamAssassin](../../delivery/using/spamassassin.md).  Clique em **[!UICONTROL More...]** para obter mais informações sobre o aviso.  Antes disso, verifique se o SpamAssassin está instalado e configurado corretamente no servidor de aplicativos do Adobe Campaign. [Saiba mais](../../installation/using/configuring-spamassassin.md)
