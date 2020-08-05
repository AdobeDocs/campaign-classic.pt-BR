---
title: Práticas recomendadas para o delivery de Campanhas
seo-title: Práticas recomendadas para delivery
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
source-git-commit: f599bc5483779ae62dd4d5eb1936cbc2760639b5
workflow-type: tm+mt
source-wordcount: '4348'
ht-degree: 32%

---


# Práticas recomendadas para delivery {#delivery-best-practices}

## Otimizar a entrega {#optimize-delivery}

Antes mesmo de começar a criar as entregas, você pode realizar várias ações para proteger e otimizar o fluxo do processo de envio.

A seção a seguir descreve as práticas recomendadas e os procedimentos recomendados para a configuração ideal do Adobe Campaign. Seguir essas práticas minimizará os problemas que você pode enfrentar em downstream.

### Desempenho da plataforma

Vários fatores podem afetar diretamente o desempenho do servidor e retardar a plataforma:

* O número e o tipo de elementos de personalização: a personalização em emails extrai dados do banco de dados para cada recipient. Se houver muitos elementos de personalização, isso aumentará a quantidade de dados necessários para preparar o delivery.  Saiba mais sobre a personalização [nesta seção](../../delivery/using/about-personalization.md)

* O servidor carrega: quando o servidor de marketing estiver manipulando várias tarefas diferentes ao mesmo tempo, ele pode retardar o desempenho. O servidor de marketing precisa coordenar todos os dados de entrada e saída de todos os delivery para garantir que os dados estejam corretos e no momento certo.

   **DICA** - Para evitar isso, coordene o agendamento de delivery com os outros membros da equipe para garantir o melhor desempenho.

* A execução do fluxo de trabalho: o monitoramento de seus workflows é essencial para evitar problemas de desempenho da plataforma. Siga as diretrizes listadas [neste documento](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* Como cliente hospedado, você pode aproveitar os recursos [do Painel de controle de](https://docs.adobe.com/content/help/pt-BR/control-panel/using/discover-control-panel/key-features.html) Campanha para monitorar sua plataforma, usando as funcionalidades de monitoramento [de](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) desempenho.

### Verificando a configuração da rede {#network-config}

Para otimizar o delivery ao manipular e-mails em grandes volumes e evitar ser confundido com um spammer, verifique se você tem uma configuração de rede legítima que não tenta ocultar a identidade do servidor.

**Dica**:  Use um endereço de remetente transparente correspondente ao site da sua marca. Por exemplo, a empresa TravelAgency gerencia a cadeia de hotéis do Valentino. É proprietária do domínio valentino.com para o seu site. Para promover o hotel Valentino em Paris, ele usa o subdomínio paris.valentino.com. Portanto, um endereço de remetente relevante pode ser hotel@paris.valentino.com.

### Gerenciamento de deliverability {#deliverability-management}

Para alcançar a caixa de entrada de seus destinatários sem precisar saltar ou ser marcado como spam, você precisa melhorar a taxa de entrega de suas mensagens.

* O que é a capacidade de entrega?

   * Refere-se aos fatores de um e-mail que determinam sua capacidade de ser aceito pelo servidor do destinatário. Os ISPs (Internet Provedores de serviço) filtram e-mails que identificam como SPAM, ou bloqueiam o download de imagens. Se determinarem que determinado domínio está enviando muitos emails, definirão um limite para o número de emails que aceitarão desse remetente.

   * Ao verificar seu e-mail quanto à capacidade de entrega, você deseja se concentrar em quatro categorias principais: qualidade de dados, mensagem e conteúdo, infraestrutura de envio e reputação. Para um mergulho mais profundo sobre esse tópico, consulte [esta seção](../../delivery/using/about-deliverability.md).

* Aplique as recomendações detalhadas [neste documento](../../delivery/using/deliverability-key-points.md).

* Entre em contato com seu representante de Adobe para obter ajuda.

### Gerenciamento de Quarentenas {#quarantine-management}

É do seu melhor interesse manter bons processos de gerenciamento de quarentenas.

Ao começar a enviar e-mails em uma nova plataforma, você pode usar uma lista de endereços que não são totalmente qualificados. Se você enviar para endereços inválidos ou endereços honeypot (caixas de correio criadas apenas para enganar spammers), a reputação da sua plataforma será afetada. Os bons processos de gerenciamento de quarentenas ajudam a: mantenha a qualidade do endereço, evite a lista de bloqueios dos provedores de acesso à Internet e reduza sua taxa de erro, acelerando delivery e throughput.

**Dicas**

* Se você tiver uma lista de endereços inválidos, o Adobe recomenda importá-la para a tabela de quarentena, por meio de **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* Os recipients cujos endereços estão em quarentena são excluídos por padrão durante a análise de delivery: não são direcionados. Isso irá acelerar os deliveries, pois a taxa de erro tem um efeito significativo na velocidade do delivery. Um endereço de email pode ser colocado em quarentena, por exemplo, quando a caixa de entrada estiver cheia ou se o endereço não existir. [Saiba mais](#identifying-quarantined-addresses-for-a-delivery)

* A Adobe Campaign gerencia endereços incorretos de acordo com o tipo de erro retornado. Para obter mais informações, consulte [esta seção](../../delivery/using/understanding-quarantine-management.md).


* Alguns provedores de acesso à Internet consideram automaticamente emails como spam se a taxa de endereços inválidos for muito alta. A Quarentena, portanto, permite evitar que você seja adicionado a uma lista de bloqueios por esses provedores.

* O gerenciamento do Quarentena também ajudará a reduzir os custos de envio de SMS, excluindo números de telefone errados de delivery.

### Mecanismo de aceitação de Duplos {#double-opt-in}

Para evitar o envio de mensagens para endereços inválidos, limitar as comunicações inadequadas e melhorar a reputação do remetente, o Adobe recomenda a implementação de um mecanismo de aceitação do duplo para confirmação pós-subscrição. Isso ajuda a garantir que um destinatário seja inscrito intencionalmente.

Os pormenores relativos à implementação deste mecanismo são descritos na [presente seção](../../web/using/use-cases--web-forms.md).

## Usar modelos {#use-templates}

Os Templates do delivery permitem maior eficiência ao fornecer cenários prontos para os tipos mais comuns de atividades. Com modelos, os profissionais de marketing podem implantar novas campanhas com personalização mínima em um período de tempo menor.

Saiba mais sobre templates do delivery [nesta seção](../../delivery/using/creating-a-delivery-template.md).

### Introdução aos templates do delivery {#gs-templates}

Um [template do delivery](../../delivery/using/creating-a-delivery-template.md) permite que você defina uma vez um conjunto de propriedades técnicas e funcionais que atendam às suas necessidades e que possam ser reutilizadas para delivery futuros. Você pode economizar tempo e padronizar delivery quando necessário.

Quando você gerencia várias marcas no Adobe Campaign, a Adobe recomenda ter um subdomínio por marca. Por exemplo, um banco pode ter vários subdomínios correspondentes a cada uma de suas agências regionais. Se um banco possuir o domínio bluebank.com, seus subdomínios poderão ser @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, etc. Ter um modelo de entrega por subdomínio permite usar sempre os parâmetros pré-configurados certos para cada marca, o que evita erros e economiza tempo.

**Dica**:  Para evitar erros de configuração no Campaign Standard, recomendamos que você duplicado um modelo nativo e altere suas propriedades em vez de criar um novo modelo.

**Configurar endereços**

* O endereço do remetente é obrigatório para permitir o envio de um email.

* Alguns ISPs (Provedores de serviço da Internet) verificam a validade do endereço do remetente antes de aceitarem mensagens.

* Um endereço mal formado pode resultar na rejeição pelo servidor de recebimento. Tem de se certificar de que é fornecido o endereço correto.

* O endereço deve identificar explicitamente o remetente. O domínio deve ser de propriedade e registrado no remetente.

* O Adobe recomenda criar contas de email que correspondam aos endereços especificados para delivery e respostas. Verifique com o administrador do sistema de mensagens.

Para configurar endereços na interface de Campanha, siga as etapas abaixo:

1. No [template do delivery](../../delivery/using/creating-a-delivery-template.md), clique no **[!UICONTROL From]** link. Na **[!UICONTROL Email header parameters]** janela, preencha os seguintes campos:

   ![](assets/d_best_practices_email_header.png)

1. No **[!UICONTROL Sender address]** campo, verifique se o domínio de endereço é o mesmo que o subdomínio que você delegou ao Adobe. Você pode alterar a parte anterior a &#39;@&#39;, mas não o endereço do domínio.

1. No **[!UICONTROL From]** campo, use um nome facilmente identificável pelos recipient, como o nome da sua marca, para aumentar a taxa de abertura dos delivery. Para melhorar ainda mais a experiência do recipient, adicione o nome de uma pessoa, por exemplo &quot;Emma from Megastore&quot;.

1. Nos **[!UICONTROL Reply address text]** arquivos, o endereço do remetente é usado por padrão para respostas. Entretanto, a Adobe recomenda usar um endereço real existente, como o atendimento ao cliente da sua marca. Nesse caso, se um destinatário enviar uma resposta, o atendimento ao cliente poderá resolvê-lo.

**Configurar um grupo de controle**

Depois que a entrega é enviada, você pode comparar o comportamento dos destinatários excluídos com os destinatários que receberam a entrega. Você pode então medir a eficiência de suas campanhas. Saiba mais sobre grupos de controle [nesta seção](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Para configurar um grupo de controle, clique no **[!UICONTROL To]** link. Na **[!UICONTROL Select target]** janela, selecione a **[!UICONTROL Control group]** guia. Você pode extrair uma parte do público alvo, por exemplo, uma amostra aleatória de 5%.

![](assets/d_best_practices_control_group.png)

**Usar tipologias para aplicar filtros ou regras de controle**

Uma tipologia contém regras de verificação aplicadas durante a fase de análise, antes de enviar qualquer mensagem.

Na **[!UICONTROL Typology]** guia das propriedades do modelo, altere a tipologia padrão de acordo com suas necessidades.

Por exemplo, para controlar melhor o tráfego de saída, você pode definir quais endereços IP podem ser usados definindo uma afinidade por subdomínio e criando uma tipologia por afinidade. As afinidades são definidas no arquivo de configuração da instância. Entre em contato com o administrador da Adobe Campaign.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).

## Design e personalização {#design-and-personalize}

Ao criar o conteúdo da sua mensagem, tente evitar problemas comuns que possam impedir a execução de sua entrega. Na maioria das vezes, possíveis erros estão relacionados à [personalização](../../delivery/using/about-personalization.md), [formatação](../../delivery/using/defining-the-email-content.md#message-content) e [imagens](../../delivery/using/defining-the-email-content.md#adding-images).

### Otimizar personalização {#optimize-personalization}

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

### Criar conteúdo otimizado {#optimize-content}

Ao criar seus e-mails, lembre-se das práticas recomendadas gerais abaixo.

* Mantenha o design simples

* Lembre-se dos usuários de dispositivos móveis

* Evite e-mails totalmente baseados em imagens

* Use fontes seguras para e-mails

* Codifique caracteres especiais

**Linha** temática - Trabalhos na linha [](../../delivery/using/defining-the-email-content.md#message-content) temática para melhorar as taxas abertas:

* Evite assuntos muito longos. Use no máximo 50 caracteres

* Evite usar palavras repetitivas como &quot;grátis&quot; ou &quot;oferta&quot;, que podem ser consideradas spam

* Evite letras maiúsculas e caracteres especiais como &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

**Mirror page** - Sempre inclua um link de mirror page. A posição preferencial é a parte superior do email. [Saiba mais](../../delivery/using/sending-messages.md#generating-the-mirror-page)

**Link** de Unsubscription - O link de unsubscription é essencial. Deve ser visível e válido e o formulário deve ser funcional. By default, when the message is analyzed, a [typology rule](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) checks whether an opt-out link has been included and generates a warning if it is missing.

**Dica**: Como o erro humano é sempre possível, verifique se o link para opção de não participação funciona corretamente antes de cada vez que você enviar. Por exemplo, ao enviar a prova, verifique se o link é válido, se o formulário está on-line e se o campo Não contate mais esse recipient foi alterado para Sim.

Saiba como inserir um link de opção de não participação [nesta seção](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

**Tamanho** do email - Para evitar problemas de desempenho ou de entrega, o tamanho máximo recomendado de um email é de cerca de **35 KB**. To check the message size, go the **[!UICONTROL Preview]** tab and choose a test profile. Uma vez gerada a mensagem, seu tamanho será exibido no canto superior direito.

Para manter seu e-mail abaixo do limite, considere o seguinte:

* Remover estilos redundantes ou não utilizados

* Mover algum conteúdo de email para uma landing page

* Minifique seu código

Certifique-se de que testou as alterações antes do envio final

**Duração do SMS**

Por padrão, o número de caracteres em um SMS atende aos padrões GSM (Global System for Mobile Communications). As mensagens SMS que usam a codificação GSM são limitadas a 160 caracteres ou a 153 caracteres por SMS para as mensagens enviadas em várias partes.

A transliteração consiste em substituir um caractere de um SMS por outro quando esse caractere não é considerado pelo padrão GSM. Observe que inserir campos de personalização no conteúdo de sua mensagem SMS pode introduzir caracteres que não são considerados pela codificação GSM. Você pode autorizar a transliteração de caracteres marcando a caixa correspondente na guia Configurações do canal SMPP do correspondente **[!UICONTROL External account]**.
Learn more [in this section](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Dicas**:

* Para manter todos os caracteres nas mensagens SMS como estão, para não alterar os nomes próprios, por exemplo, não ative a transliteração.

* No entanto, se suas mensagens SMS contiverem muitos caracteres que não forem considerados pelo padrão GSM, permita a transliteração para limitar os custos de envio das mensagens.

Learn more [in this section](../../delivery/using/sms-channel.md#about-character-transliteration).

### Trabalhar na formatação {#formatting}

Para evitar erros comuns de formatação, verifique os seguintes elementos:

* Correct **date formatting**: Adobe Campaign provides date formatting functions for the JavaScript templates and XSL stylesheets. [Saiba mais](../../delivery/using/formatting.md#date-display)

* Uso de caracteres **** autorizados em emails: a lista de caracteres válidos para endereços de email é definida na opção &quot;XtkEmail_Characters&quot;. Saiba como acessar as opções de Campanha [nesta seção](../../installation/using/configuring-campaign-options.md). Para lidar corretamente com caracteres especiais, o Adobe Campaign precisa ser instalado em Unicode.

* Configuração da autenticação de **email**: verifique se os cabeçalhos de email contêm a assinatura DKIM. A autenticação DKIM (Domain Keys Identified Mail) permite que o servidor de email de recebimento verifique se uma mensagem foi enviada pela pessoa ou entidade pela qual ela alega ter sido enviada e se o conteúdo da mensagem foi alterado entre o momento em que foi enviada originalmente (e o DKIM &quot;assinado&quot;) e o momento em que foi recebida. Normalmente, esse padrão usa o domínio no cabeçalho De ou Remetente. Para obter mais informações, consulte [esta seção](../../delivery/using/technical-recommendations.md#dkim).

* **O design responsivo de e-mail garante que um e-mail seja processado de maneira ideal para o dispositivo no qual ele é aberto.**

   * Use HTML responsivo de e-mail em vez de HTML para web.

   * Use o modo de visualização e envie provas para testar a renderização no máximo de dispositivos possível.

   * The Adobe Campaign Classic Digital Content Editor (DCE) module includes some responsive design formatted templates for mobile available via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Saiba mais [neste artigo](https://theblog.adobe.com/responsive-email-design-101/).



### Gestão de imagens {#manage-images}

Siga as diretrizes abaixo ao usar imagens.

* **Impedir bloqueio** de imagens - Alguns clientes de email bloqueiam imagens por padrão, e alguns usuários alteram suas configurações para bloquear imagens para salvar no uso de dados. Portanto, se as imagens não forem baixadas, a mensagem inteira poderá ser perdida. Para evitar isso:

   * Equilibre imagens e texto no seu conteúdo. Evite e-mails totalmente baseados em imagens.

   * Se o texto precisa estar contido em uma imagem, use alt e title para garantir que sua mensagem seja exibida. Estilize o texto alt/title para melhorar a aparência.

   * Evite o uso de imagens de fundo, pois elas não são suportadas por alguns clientes de e-mail.

* **Torne as imagens responsivas** - Tente tornar as imagens responsivas e redimensionáveis. Observe que isso pode ter um impacto no custo, pois demora mais para ser criado.

* **Usar referências** de imagem absolutas - para serem acessíveis do lado de fora, as imagens usadas em emails e recursos públicos vinculados ao campanha devem estar presentes em um servidor acessível externamente.

   * Você pode verificar se a configuração da instância ativa o gerenciamento de recursos públicos. [Saiba mais](../../installation/using/deploying-an-instance.md#managing-public-resources)

   * No assistente do delivery, você pode importar uma página HTML contendo imagens ou inserir imagens diretamente usando o editor de HTML pelo ícone **[!UICONTROL Image]**. [Saiba mais](../../delivery/using/defining-the-email-content.md#adding-images)

   * Se as imagens não forem exibidas, verifique se elas estão disponíveis no servidor. Para fazer isso, clique na guia Origem do seu delivery. Localize suas imagens e copie e cole o URL de cada imagem em um navegador da Web. Se as imagens não forem exibidas, entre em contato com seu administrador de TI ou com seu fornecedor, provendo-lhes seu conteúdo de entrega.

### Visualizar sua mensagem {#preview-msg}

A Adobe recomenda visualizar sua mensagem para verificar sua personalização e como seus destinatários verão a entrega.

* In the delivery wozard, the **[!UICONTROL Preview]** sub-tab lets you view the rendering of each content for a recipient. Os campos de personalização e os elementos condicionais do conteúdo são substituídos pelas informações correspondentes para o perfil selecionado. [Saiba mais](../../delivery/using/defining-the-email-content.md#message-content)

* Uma verificação automática de antisspam é executada durante cada pré-visualização. Na **[!UICONTROL Preview]** subguia, verifique a pontuação de spam do [SpamAssassin](../../delivery/using/spamassassin.md) .  Clique em **[!UICONTROL More...]** para saber mais sobre o aviso.  Antes de fazer isso, verifique se o SpamAssassin está instalado e configurado corretamente no servidor de aplicativos Adobe Campaign. [Saiba mais](../../installation/using/configuring-spamassassin.md)

## Definir o público-alvo correto {#define-the-right-target}

A população-alvo é fundamental: crie suas listas cuidadosamente, teste seus e-mails em clientes de e-mail populares e dispositivos móveis e verifique se suas listas de e-mail estão atualizadas (sem endereços desconhecidos ou obsoletos). Você também pode enviar provas que ajudam a configurar um ciclo de validação completo.

Saiba mais sobre as populações de públicos alvos [nesta seção](../../delivery/using/steps-defining-the-target-population.md)

### Público alvo da audiência direita {#target-the-right-audience}

Quando seu conteúdo estiver pronto, será necessário definir com cuidado quem receberá sua mensagem.

Para que sua entrega seja bem-sucedida, o conteúdo personalizado mais relevante deve ser enviado aos destinatários corretos. O Adobe Campaign permite criar o destino mais preciso: você pode selecionar os destinatários de acordo com a idade, localização, o que compraram, se clicaram em um link em uma entrega anterior, etc. Com a Adobe Campaign, também é possível definir perfis de teste, grupos de controle e seeds addresses para verificar se o público alvo está correto.

### Target mapping {#target-mappings}

In Campaign Classic, by default, delivery templates target **Recipients**. A Adobe Campaign oferta outros target mapping para seus delivery, que podem ser alterados de acordo com suas necessidades.

Por exemplo, você pode entregar a visitantes cujos perfis tenham sido coletados pelas redes sociais ou a visitantes que estejam inscritos em um serviço de informação.

Esses mapeamentos são apresentados [nesta seção](../../delivery/using/selecting-a-target-mapping.md).

Você também pode criar e usar um target mapping personalizado. Para obter mais informações, consulte [esta seção](../../configuration/using/target-mapping.md).

### recipient externos {#external-recipients}

Você pode enviar entregas para destinatários armazenados em um arquivo externo em vez de salvos no banco de dados. Learn more [in this section](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

### Enviar para seus assinantes {#send-to-subscribers}

Para enviar mensagens aos assinantes de um boletim informativo, é possível público alvo direto dos assinantes para o serviço de informação correspondente. Learn more [in this section](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


### Testar recipient e seeds addresses {#test-recipients-seed-addresses}

Para testar seu delivery, use provas antes de enviar para o público alvo principal.

Certifique-se de selecionar recipient de prova apropriados, pois eles validam o formulário e o conteúdo da mensagem. As etapas para definir os recipient de prova são apresentadas [nesta seção](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

Os seed addresses são usados para direcionar destinatários que não correspondem aos critérios de target definidos para testar uma entrega antes de enviar ao target principal. They are presented [in this section](../../delivery/using/about-seed-addresses.md).

### Desduplicar endereços {#deduplicate-addresses}

É importante evitar o uso de endereços de e-mail de duplicado, pois isso pode afetar seu público alvo:

* A mesma mensagem pode ser enviada mais de uma vez quando um público alvo é dividido.

* Se um destinatário cancelar a assinatura após receber uma mensagem, seu perfil duplicado ainda receberá mensagens futuras.

A desduplicação de endereços protege a reputação do seu envio e garante um bom gerenciamento de quarentenas.

Saiba mais [neste caso](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery)de uso.


### Endereços de email do índice {#index-addresses}

Para otimizar o desempenho das consultas SQL usadas no aplicativo, um índice pode ser declarado a partir do elemento principal do esquema de dados.

As etapas para adicionar um índice ao endereço de email são apresentadas [nesta seção](../../configuration/using/database-mapping.md#indexed-fields).

## Executar todas as verificações antes de enviar {#perform-all-checks}

Quando a mensagem estiver pronta, certifique-se de que seu conteúdo está sendo exibido corretamente, em todos os dispositivos, e de que não contém erros, como personalização incorreta ou links quebrados.

Antes de enviar sua mensagem, verifique também se os parâmetros e a configuração estão consistentes na entrega.

### A validação é a chave {#validation-is-key}

Antes de enviar uma entrega, você precisa garantir que seus destinatários receberão a mensagem que você realmente deseja enviar. Para fazer isso, é necessário validar o conteúdo da mensagem e os parâmetros do delivery.

Esta etapa permite que você detecte possíveis erros e os corrija antes de entregar para o público alvo principal.

As etapas para validar um delivery são apresentadas [nesta seção](../../delivery/using/steps-validating-the-delivery.md).

### Renderização da caixa de entrada {#inbox-and-email-rendering}

A renderização da caixa de entrada permite que você pré-visualização suas mensagens nos principais clientes de email, verifique o conteúdo e a reputação, descubra como os recipient estão lendo as mensagens.

**Dicas**:

* Você pode visualização a mensagem enviada nos diferentes contextos nos quais ela pode ser recebida: webmail, serviço de mensagens, celular etc.

* Os recursos de renderização da caixa de entrada são cruciais para identificar se suas campanhas de email ultrapassam com êxito os filtros dos principais ISPs (Provedores de serviço da Internet) e serviços de email. Essas ferramentas enviam uma cópia de pré-impressão de um email para uma rede de caixas de entrada de teste, para que você possa ver como a mensagem será exibida ou irá renderizar nesses serviços. Elas também podem incluir relatórios e opções de correção de código que ajudam a identificar e fazer correções rapidamente que melhoram o deliverability.

Learn more [in this section](../../delivery/using/inbox-rendering.md).

### Mensagens de Prova {#proof-messages}

O envio de provas permite que você verifique o link de opção de não participação, o mirror page e quaisquer outros links, valide a mensagem, verifique se as imagens são exibidas, detecte possíveis erros etc. Você também pode verificar seu design e renderização em diferentes dispositivos.

Learn more [in this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Configurar delivery de teste A/B {#a-b-testing-deliveries}

Se você tiver vários conteúdos para um delivery de email, poderá usar o teste A/B para descobrir qual versão terá o maior impacto na população-alvo.

**Dicas**:

* Envie as diferentes versões para alguns dos seus destinatários

* Selecione aquele com a maior taxa de sucesso e envie-o para o restante do seu público alvo

Learn more [in this section](../../workflow/using/a-b-testing.md).

### Certifique-se de que sua mensagem foi entregue {#make-sure-your-message-is-delivered}

Como etapa final, maximize suas chances e aproveite o poder do Adobe Campaign Classic para garantir que sua mensagem seja de fato entregue aos destinatários relevantes.

**Execute um processo** de validação - você pode definir um processo de validação completo, envolvendo operadores e grupos da Adobe Campaign, para validar o público alvo e o conteúdo da mensagem. Isso garantirá o monitoramento e o controle completos dos vários processos da campanha: definição de metas, conteúdo, orçamento, extração e envio de uma prova. Dependendo de suas permissões, os usuários serão notificados, receberão provas e poderão validar ou rejeitar a mensagem. Learn more [in this section](../../campaign/using/marketing-campaign-approval.md#approval-process).

**Usar o ondas** - é possível aumentar progressivamente o volume enviado usando o ondas. Isso evitará que suas mensagens sejam marcadas como spam ou quando você quiser restringir o número de mensagens por dia. Ao usar ondas, você pode dividir as entregas em vários lotes, em vez de enviar grandes volumes de mensagens ao mesmo tempo. Learn more [in this section](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

**Priorizar mensagens** - Você pode definir a ordem de envio para seus delivery informando o nível de prioridade. Para fazer isso:

1. Edite as propriedades do delivery e selecione a **[!UICONTROL Delivery]** guia.

1. Defina o nível de prioridade do delivery em uma escala de **[!UICONTROL Very low]** para **[!UICONTROL Very high]**.

>[!NOTE]
>
>Não é possível definir a ordem de envio de mensagens a partir de um delivery.

**Configurar Afinidades** IP - Para controlar melhor o tráfego SMTP de saída, você pode gerenciar afinidades definindo quais endereços IP específicos podem ser usados para cada afinidade. Isso permite a restrição do número de emails para envios específicas em máquinas ou endereços de saída. Por exemplo, você pode usar uma afinidade por país ou subdomínio. Em seguida, é possível criar uma tipologia por país e vincular cada afinidade à tipologia correspondente.

Você pode:

* Defina as afinidades IP no arquivo de configuração serverConf.xml. [Saiba mais](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Para cada elemento IPAffinity, declare os endereços IP que podem ser usados. [Saiba mais](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* Na [tipologia](../../campaign/using/about-campaign-typologies.md) de sua escolha, use o **[!UICONTROL Managing affinities with IP addresses]** campo para vincular delivery ao servidor do delivery (MTA) que gerencia a afinidade. [Saiba mais](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* Depois que o email for enviado, verifique o cabeçalho para verificar de qual endereço IP o delivery foi enviado. O administrador de e-mail deve ajudá-lo a obter as informações do cabeçalho.

>[!NOTE]
>
>A maioria dessas etapas só pode ser executada por um usuário especialista.

**Usar tipologias** - você pode usar regras de tipologia para excluir parte do público alvo com base em critérios específicos. Isso garante que as mensagens enviadas atendam melhor às necessidades e expectativas dos clientes, de acordo com as políticas de comunicação da empresa. Por exemplo, você pode filtrar os destinatários menores de idade do público-alvo do seu boletim informativo. Saiba mais [neste exemplo](../../campaign/using/filtering-rules.md).

**Evitar anexos** - Os anexos permanecem um dos vetores mais comuns para a proliferação de malware, especialmente quando são enviados em massa. Inclua um link seguro no documento em vez de anexá-lo. Isso garante uma camada adicional de segurança para impedir a redistribuição não intencional e reduz consideravelmente as chances de a mensagem ser rejeitada em gateways de entrada de email por motivos de tamanho de mensagem ou de segurança.

## Rastrear e monitorar {#track-and-monitor}

Você clicou no botão Enviar? Vamos ver o que acontece. Depois que a entrega é enviada, o Adobe Campaign permite que você acompanhe as mensagens enviadas e descubra como seus destinatários reagem à sua entrega. Isso o ajudará a melhorar o envio futuro e a otimizar suas próximas campanhas.

### Monitoramento de deliveries {#monitoring-deliveries}

Para controlar suas campanhas, você deve garantir que a mensagem tenha sido entregue aos seus destinatários.

No painel do delivery da Campanha, você pode verificar as mensagens processadas e os registros de auditoria do delivery.
Você também pode controlar o status das mensagens nos logs do delivery. [Saiba mais](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

E se os delivery não estiverem sendo enviados e seu status permanecer **Pendente**?

* O processo de execução está aguardando a disponibilidade de alguns recursos. O MTA pode não ter sido iniciado.
Verifique se os seus mta@instanceétodos estão abertos nos servidores MTA e start o módulo MTA, se necessário. [Saiba mais](../../production/using/administration.md).

* O delivery pode estar usando uma afinidade que não foi configurada na instância de envio.
Dica: Verifique a configuração do gerenciamento de tráfego (afinidade IP). Para obter mais informações, consulte Controlar tráfego SMTP de saída.

>[!NOTE]
>
>Essas etapas só podem ser executadas por um usuário especialista.

### Rastreamento {#tracking-deliveries}

Para conhecer melhor o comportamento de seus destinatários, você pode acompanhar como eles reagem a uma entrega: recebimento, abertura, cliques em links, assinaturas canceladas, etc. No Campaign Classic, essas informações são exibidas na guia Rastreamento dos recipient direcionados pelo delivery e na guia Rastreamento do delivery. No Campaign Standard, ele é exibido na guia Logs de rastreamento do delivery.

**Dica**: O rastreamento de mensagens está ativado por padrão. Para configurar URLs, selecione a opção Exibir URLs na seção inferior do assistente do delivery. Para cada URL da mensagem, você pode escolher se deseja ativar o rastreamento.

Para obter mais informações, consulte a seção [Configuração de rastreamento](../../delivery/using/how-to-configure-tracked-links.md) e a descrição dos indicadores [de](../../reporting/using/delivery-reports.md#tracking-indicators) rastreamento.

### Desempenho do delivery {#delivery-performances}

Para medir a velocidade de entrega das mensagens, é possível controlar a taxa de transferência do delivery. Os critérios são o número de mensagens enviadas por hora e o tamanho das mensagens (em bits por segundo). For more on this, see [Delivery throughput](../../reporting/using/global-reports.md#delivery-throughput).

**Dicas**:

* Não mantenha as entregas em estado de falha na instância, pois isso mantém tabelas temporárias e afeta o desempenho.

* Remova as remessas que não são mais necessárias e os destinatários inativos do banco de dados para manter a qualidade do endereço.

* Não tente programar entregas grandes em conjunto. Observe que pode levar de 5 a 10 minutos para espalhar a carga uniformemente sobre o sistema.

## solução de problemas do Delivery {#delivery-troubleshooting}

Ações específicas podem ser executadas ao encontrar problemas com delivery:

* [Problemas de produtividade](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemas de exibição de imagem](../../production/using/image-display-issues.md)

* [Problemas de desempenho do Delivery](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Problemas](../../production/using/temporary-files.md) de arquivos temporários - somente clientes *locais*
