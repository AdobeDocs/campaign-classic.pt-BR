---
product: campaign
title: Configuração técnica de email
description: Saiba como configurar o Campaign para controlar a saída de suas instâncias ao entregar emails
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 515adad2-6129-450a-bb9e-fc80127835af
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '3023'
ht-degree: 20%

---

# Configurações técnicas de email{#email-deliverability}



## Visão geral {#overview}

A seção a seguir fornece uma visão geral da configuração necessária para controlar a saída das instâncias do Adobe Campaign ao enviar emails.

>[!NOTE]
>
>Algumas configurações só podem ser executadas por Adobe para implantações hospedadas por Adobe, por exemplo, para acessar os arquivos de configuração do servidor e da instância. Para saber mais sobre as diferentes implantações, consulte o [Modelos de hospedagem](../../installation/using/hosting-models.md) ou para [esta página](../../installation/using/capability-matrix.md).

Para obter mais informações sobre os conceitos e as práticas recomendadas relacionadas à capacidade de delivery com o Adobe Campaign, consulte este [seção](../../delivery/using/about-deliverability.md).

Para aprofundar o assunto, incluindo todas as recomendações técnicas relacionadas ao envio e recebimento eficientes de emails por uma plataforma Adobe, consulte o [Guia de práticas recomendadas de capacidade de delivery do Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR).

## Princípio operacional {#operating-principle}

É possível controlar a saída de uma ou mais instâncias do Adobe Campaign para restringir o número de emails enviados, dependendo de um domínio. Por exemplo, é possível restringir a saída a 20.000 por hora para **yahoo.com** ao configurar 100.000 mensagens por hora para todos os outros domínios.

A saída de mensagens precisa ser controlada para cada endereço IP usado pelos servidores de entrega (**mta**). Vários **mta** divididos em várias máquinas e pertencentes a várias instâncias do Adobe Campaign podem compartilhar o mesmo endereço IP para entrega de email: é necessário configurar um processo para coordenar o uso desses endereços IP.

É o que a **stat** O módulo faz: encaminha todas as solicitações de conexão e mensagens a serem enviadas aos servidores de email para um conjunto de endereços IP. O servidor de estatísticas rastreia os deliveries e pode habilitar ou desabilitar o envio com base em cotas definidas.

![](assets/s_ncs_install_mta.png)

* O servidor de estatísticas (**stat**) está vinculado a uma base do Adobe Campaign para carregar sua configuração.
* Os servidores de entrega (**mta**) usar um UDP para contatar um servidor de estatísticas que nem sempre pertence à sua própria instância.

### Servidores de entrega {#delivery-servers}

A variável **mta** O módulo distribui mensagens para seus **mtachild** módulos filhos. Each **mtachild** prepara as mensagens antes de solicitar uma autorização do servidor de estatísticas e enviá-las.

As etapas são as seguintes:

1. A variável **mta** seleciona mensagens qualificadas e atribui a elas uma mensagem disponível **mtachild**.
1. A variável **mtachild** carrega todas as informações necessárias para criar a mensagem (conteúdo, elementos de personalização, anexos, imagens etc.) e encaminhará a mensagem para o **Formatador de Tráfego de Email**.
1. Assim que o formador de tráfego de email receber a autorização do servidor de estatísticas (**estado smtp**), a mensagem será enviada ao recipient.

![](assets/s_ncs_install_email_traffic_shaper.png)

### Estatísticas e limitações do servidor de email {#email-server-statistics-and-limitations}

O servidor de estatísticas mantém as seguintes estatísticas para cada servidor de email que recebe mensagens:

* Número de conexões point-in-time abertas,
* Número de mensagens enviadas na última hora,
* Taxa de conexões com êxito/rejeitadas,
* Taxa de conexões com servidores inacessíveis.

Ao mesmo tempo, o módulo carrega uma lista de limitações para determinados servidores de email:

* Número máximo de conexões simultâneas,
* Número máximo de mensagens por hora,
* Número máximo de mensagens por conexão.

### Gerenciamento de endereços IP {#managing-ip-addresses}

O servidor de estatísticas pode combinar várias instâncias ou várias máquinas com o mesmo endereço IP público. Portanto, não está vinculado a uma instância específica, mas precisa entrar em contato com uma instância para recuperar as limitações por domínio.

As estatísticas de delivery são mantidas para cada MX de destino e para cada IP de origem. Por exemplo, se o domínio direcionado tiver 5 MX e a plataforma puder usar 3 endereços IP diferentes, o servidor poderá gerenciar até 15 séries de indicadores para esse domínio.

O endereço IP de origem corresponde ao endereço IP público, ou seja, ao endereço como é visto pelo servidor de email remoto. Esse endereço IP pode ser diferente do endereço da máquina que hospeda o **mta**, se um roteador NAT for fornecido. É por isso que o servidor de estatísticas usa um identificador que corresponde ao IP público (**publicId**). A associação entre o endereço local e esse identificador é declarada na variável **serverConf.xml** arquivo de configuração. Todos os parâmetros disponíveis no **serverConf.xml** estão listados neste [seção](../../installation/using/the-server-configuration-file.md).

## Controle de saída de entrega {#delivery-output-controlling}

Para enviar mensagens a servidores de email, a variável **Formatador de Tráfego de Email** O componente solicita uma conexão do servidor de estatísticas. Depois que a solicitação é aceita, a conexão é aberta.

Antes de enviar mensagens, o módulo solicita &quot;tokens&quot; do servidor. Geralmente, esses são conjuntos de pelo menos 10 tokens, o que reduz o número de queries ao servidor.

O servidor salva todas as estatísticas relacionadas a conexões e deliveries. No caso de reinicialização, as informações são temporariamente perdidas: cada cliente mantém uma cópia local de suas estatísticas de envio e as retorna ao servidor regularmente (a cada 2 minutos). O servidor pode então reagregar os dados.

As seções a seguir descrevem o processamento de uma mensagem pelo **Formatador de Tráfego de Email** componente.

### Entrega de mensagem {#message-delivery}

Quando uma mensagem é enviada, há três resultados possíveis:

1. **Sucesso**: a mensagem foi enviada com êxito. A mensagem é atualizada.
1. **Falha na mensagem**: o servidor de contato rejeitou a mensagem para o recipient escolhido. Esse resultado corresponde aos códigos de retorno 550 a 599, mas as exceções podem ser definidas.
1. **Sessão falha** (para 5.11 acima): se a variável **mta** receber uma resposta para esta mensagem, ela será abandonada (consulte [Abandono de mensagem](#message-abandonment)). A mensagem é enviada para outro caminho ou é definida como pendente se nenhum outro caminho estiver disponível (consulte [Mensagem pendente](#message-pending)).

   >[!NOTE]
   >
   >A **caminho** é uma conexão entre a Adobe Campaign **mta** e o público alvo **mta**. O ADOBE CAMPAIGN **mta** O pode escolher entre vários IPs iniciais e vários IPs de domínio de destino.

### Abandono de mensagem {#message-abandonment}

As mensagens abandonadas são retornadas à **mta** e não são mais gerenciados pela **mtachild**.

A variável **mta** decide sobre o procedimento para essa mensagem (recuperação, abandono, quarentena etc.) dependendo do código de resposta e das regras.

### Mensagem pendente {#message-pending}

Uma mensagem fica pendente quando chega à fila ativa e não há caminhos disponíveis.

Um caminho geralmente é marcado como indisponível por um período variável após um erro de conexão. O período de indisponibilidade depende da frequência e da idade dos erros.

## Configuração do servidor de estatísticas {#statistics-server-configuration}

O servidor de estatísticas pode ser usado por várias instâncias: ele deve ser configurado independentemente das instâncias que o usarão.

Comece definindo o banco de dados do Adobe Campaign que hospedará a configuração.

### Configuração inicial {#start-configuration}

Por padrão, a variável **stat** O módulo é iniciado para cada instância. Quando as instâncias são agrupadas na mesma máquina ou quando as instâncias compartilham o mesmo endereço IP, um único servidor de estatísticas é usado: as outras precisam ser desativadas.

### Definição da porta do servidor {#definition-of-the-server-port}

Por padrão, o servidor de estatísticas escuta na porta 7777. Essa porta pode ser modificada no **serverConf.xml** arquivo. Todos os parâmetros disponíveis no **serverConf.xml** estão listados neste [seção](../../installation/using/the-server-configuration-file.md).

```
<stat port="1234"/>
```

## Configuração MX {#mx-configuration}

>[!IMPORTANT]
>
>Para instalações hospedadas ou híbridas, se você atualizou para o [MTA aprimorado](../../delivery/using/sending-with-enhanced-mta.md), as regras de taxa de trasferência do delivery **[!UICONTROL MX management]** não são mais usadas. O MTA aprimorado usa regras de MX próprias que permitem personalizar a taxa de transferência por domínio com base na sua própria reputação histórica de email e no feedback em tempo real proveniente dos domínios em que você está enviando emails.

### Sobre as regras MX {#about-mx-rules}

>[!NOTE]
>
>Esta seção e as seções abaixo se aplicam apenas às instalações no local e instalações hospedadas/híbridas que usam o MTA herdado do Campaign.

As regras MX (Mail eXchanger) são as regras que gerenciam a comunicação entre um servidor de envio e um servidor de recebimento.

Essas regras são recarregadas automaticamente todas as manhãs às 6h (horário do servidor) para fornecer regularmente a instância do cliente.

Dependendo das capacidades do material e da política interna, um ISP aceitará um número predefinido de conexões e mensagens por hora. Essas variáveis podem ser modificadas automaticamente pelo sistema ISP, dependendo da reputação do IP e do domínio de envio. Por meio da sua plataforma de deliverability, o Adobe Campaign gerencia mais de 150 regras específicas pelo ISP e, além disso, uma regra genérica para outros domínios.

O número máximo de conexões não depende exclusivamente do número de endereços IP públicos usados pelo MTA.

Por exemplo, se você permitiu 5 conexões nas regras MX e configurou 2 IPs públicos, talvez ache que não é possível ter mais de 10 conexões abertas simultaneamente nesse domínio. Isso não é verdade, de fato, o número máximo de conexões se refere a um caminho, e um caminho que é uma combinação de um de nossos IPs públicos de MTA e um IP público do MTA do cliente.

No exemplo abaixo, o usuário tem dois endereços IP públicos configurados e o domínio é yahoo.com.

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

Os registros MX para yahoo.com informam que o yahoo.com tem 3 Mail Exchangers. Para conectar o Peer Mail Exchanger, o MTA solicitará o endereço IP do DNS.

```
user:~ user$ host -t a mta5.am0.yahoodns.net
                mta5.am0.yahoodns.net has address 98.136.216.26
                mta5.am0.yahoodns.net has address 98.136.217.202
                mta5.am0.yahoodns.net has address 98.138.112.38
                mta5.am0.yahoodns.net has address 66.196.118.37
                mta5.am0.yahoodns.net has address 63.250.192.46
                mta5.am0.yahoodns.net has address 66.196.118.240
                mta5.am0.yahoodns.net has address 98.136.217.203
                mta5.am0.yahoodns.net has address 98.138.112.35
```

Para este registro, o usuário poderá contatar 8 endereços IP parceiros. Como o usuário tem dois endereços IP públicos, ele recebe 8 * 2 = 16 combinações para acessar os servidores de email yahoo.com. Cada uma dessas combinações é chamada de caminho.

O segundo registro MX aparece como:

```
user:~ user$ host -t a mta6.am0.yahoodns.net
                mta6.am0.yahoodns.net has address 98.138.112.38
                mta6.am0.yahoodns.net has address 98.136.216.26
                mta6.am0.yahoodns.net has address 63.250.192.46
                mta6.am0.yahoodns.net has address 66.196.118.35
                mta6.am0.yahoodns.net has address 98.136.217.203
                mta6.am0.yahoodns.net has address 98.138.112.32
                mta6.am0.yahoodns.net has address 98.138.112.37
                mta6.am0.yahoodns.net has address 66.196.118.33
```

4 desses 8 endereços IP já são usados em mta5 (98.136.216.26, 98.138.112.38, 63.250.192.46 e 98.136.217.203). Esse registro permite que o usuário use 4 novos endereços IP. O terceiro registro MX fará o mesmo.

No total, temos 16 endereços IP remotos. Em combinação com nossos dois IPs públicos locais, temos 32 caminhos para alcançar servidores de email yahoo.com.

>[!NOTE]
>
>Se 2 registros MX estiverem fazendo referência ao mesmo endereço IP, este será contado como um caminho e não dois.

Abaixo estão alguns exemplos de uso das regras MX:

![](assets/s_ncs_examples_mx_rules.png)

No exemplo abaixo, o usuário tem um limite de 10.000 mensagens por hora para determinado domínio, mas a capacidade da taxa de transferência MTA é maior que esse limite.

Nesse caso, o tráfego é dividido em 12 períodos de 5 minutos para cada hora e o limite real é 833 mensagens por período.

Essas mensagens serão entregues o mais rápido possível.

![](assets/s_ncs_traffic_shaping.png)

### Configuração da gestão MX {#configuring-mx-management}

As regras a cumprir para a MX são definidas no **[!UICONTROL MX management]** documento do **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** nó da árvore.

Se a variável **[!UICONTROL MX management]** documento não existe no nó, você pode criá-lo manualmente. Para fazer isso:

1. Crie um novo conjunto de regras de email.
1. Escolha o **[!UICONTROL MX management]** modo.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. Enter **defaultMXRules** no **[!UICONTROL Internal name]** campo.

Para que as alterações sejam consideradas, é necessário reiniciar o servidor de estatísticas.

Para recarregar a configuração sem reiniciar o servidor de estatísticas, use o seguinte comando na máquina que hospeda o servidor: `nlserver stat -reload`

>[!NOTE]
>
>Esta linha de comando é preferível a **nlserver restart**. Ela evita que as estatísticas coletadas antes da reinicialização sejam perdidas e evita picos de uso, o que pode ir contra as cotas definidas nas regras MX.

### Configuração de regras MX {#configuring-mx-rules}

A variável **[!UICONTROL MX management]** documento lista todos os domínios vinculados a uma regra MX.

Essas regras são aplicadas em sequência: a primeira regra cuja máscara MX é compatível com o MX direcionado é aplicada.

Os seguintes parâmetros disponíveis para cada regra são:

* **[!UICONTROL MX mask]**: domínio no qual a regra é aplicada. Cada regra define uma máscara de endereço para o MX. Qualquer MX cujo nome corresponda a essa máscara será, portanto, elegível. A máscara pode conter &quot;&#42;&quot; e &quot;?&quot; caracteres genéricos.

   Por exemplo, os seguintes endereços:

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

   são compatíveis com as seguintes máscaras:

   * &#42;.yahoo.com
   * ?.mx.yahoo.com

   Por exemplo, para o endereço de email foobar@gmail.com, o domínio é gmail.com e o registro MX é:

   ```
   gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
   ```

   Nesse caso, a regra MX `*.google.com` serão usados. Como você pode ver, a máscara de regra MX não corresponde necessariamente ao domínio no email. As regras MX aplicadas para endereços de email gmail.com serão aquelas com a máscara `*.google.com`.

* **[!UICONTROL Range of identifiers]**: essa opção permite indicar os intervalos de identificadores (publicID) aos quais a regra se aplica. Você pode especificar:

   * Um número: a regra será aplicada somente a essa publicId,
   * Um intervalo de números (**número1-número2**): a regra será aplicada a todas as publicIds entre esses dois números.

   >[!NOTE]
   >
   >Se o campo estiver vazio, a regra se aplica a todos os identificadores.

   Uma ID pública é um identificador interno de um IP público usado por um ou vários MTAs. Essas IDs são definidas nos servidores MTA no arquivo **config-instance.xml** .

   ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**: define o escopo das propriedades para esta regra MX. Quando marcado, todos os parâmetros são compartilhados em todos os IPs disponíveis na instância. Quando desmarcado, as regras MX são definidas para cada IP. O número máximo de mensagens é multiplicado pelo número de IPs disponíveis.
* **[!UICONTROL Maximum number of connections]**: número máximo de conexões simultâneas com o domínio do remetente.
* **[!UICONTROL Maximum number of messages]**: número máximo de mensagens que podem ser enviadas em uma conexão. Quando as mensagens excedem esse número, a conexão é fechada e uma nova é aberta.
* **[!UICONTROL Messages per hour]**: número máximo de mensagens que podem ser enviadas em uma hora para o domínio do remetente.
* **[!UICONTROL Connection time out]**: limite de tempo para conexão com um domínio.

   >[!NOTE]
   >
   >O Windows pode emitir um **timeout** antes desse limite, que depende da sua versão do Windows.

* **[!UICONTROL Timeout Data]**: tempo máximo de espera após o envio do conteúdo da mensagem (seção DATA do protocolo SMTP).
* **[!UICONTROL Timeout]**: tempo máximo de espera para outras trocas com o servidor SMTP.
* **[!UICONTROL TLS]**: o protocolo TLS, que permite criptografar deliveries de email, pode ser habilitado seletivamente. Para cada máscara MX, as seguintes opções estão disponíveis:

   * **[!UICONTROL Default configuration]**: esta é a configuração geral especificada no arquivo de configuração serverConf.xml que é aplicada.

      >[!IMPORTANT]
      >
      >Não é recomendável modificar a configuração padrão.

   * **[!UICONTROL Disabled]** : As mensagens são enviadas sistematicamente sem criptografia.
   * **[!UICONTROL Opportunistic]** : o delivery de mensagens é criptografado se o servidor de recebimento (SMTP) puder gerar o protocolo TLS.

Exemplo de configuração:

![](assets/s_ncs_install_mx_mgt_rule_details.png)

>[!NOTE]
>
>Para obter mais informações sobre o uso de servidores MX com o Adobe Campaign, consulte [nesta seção](../../installation/using/using-mx-servers.md).

### Gerenciamento de formatos de email {#managing-email-formats}

Você pode definir o formato das mensagens enviadas, para que o conteúdo exibido se adapte automaticamente de acordo com o domínio do endereço de cada recipient.

Para fazer isso, acesse o **[!UICONTROL Management of email formats]** documento, localizado em **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**.

Este documento contém uma lista de todos os domínios predefinidos que correspondem aos formatos japoneses gerenciados pelo Adobe Campaign. Para obter mais informações, consulte [este documento](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

A variável **Estrutura MIME** (Multipurpose Internet Mail Extensions) permite definir a estrutura da mensagem que será enviada aos diferentes clientes de e-mail. Há três opções disponíveis:

* **Várias partes**: A mensagem é enviada no formato de texto ou HTML. Se o formato HTML não for aceito, a mensagem ainda poderá ser exibida no formato de texto.

   Por padrão, a estrutura de várias partes é **multipart/alternative**, mas automaticamente se torna **multipart/related** quando uma imagem é adicionada à mensagem. Alguns provedores esperam que o **multipart/related** por padrão, a variável **[!UICONTROL Force multipart/related]** A opção impõe esse formato mesmo se nenhuma imagem estiver anexada.

* **HTML**: Uma mensagem somente HTML é enviada. Se o formato HTML não for aceito, a mensagem não será exibida.
* **Texto**: uma mensagem no formato somente texto é enviada. A vantagem das mensagens em formato de texto é seu tamanho muito pequeno.

Se a variável **[!UICONTROL Image inclusion]** estiver ativada, elas serão exibidas diretamente no corpo do email. As imagens serão carregadas e os links de URL serão substituídos pelo conteúdo.

Esta opção é particularmente utilizada pelo mercado japonês para **Deco-mail**, **Decore Mail** ou **Email de decoração**. Para obter mais informações, consulte [este documento](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

>[!IMPORTANT]
>
>A inserção de imagens em um email aumenta consideravelmente seu tamanho.

## Configuração do servidor de entrega {#delivery-server-configuration}

### Sincronização do relógio {#clock-synchronization}

Os relógios de todos os servidores que compõem a plataforma Adobe Campaign (incluindo o banco de dados) devem ser sincronizados e seus sistemas definidos para o mesmo fuso horário.

### Coordenadas do servidor de estatísticas {#coordinates-of-the-statistics-server}

O endereço do servidor de estatísticas deve ser fornecido na variável **mta**.

A variável **statServerAddress** propriedade do **mta** o elemento da configuração permite especificar o endereço e o número da porta a ser usada.

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

Para usar o servidor de estatísticas na mesma máquina, você deve inserir pelo menos o nome da máquina com o **localhost** valor:

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>Se esse campo não estiver preenchido, a variável **mta** não iniciará.

### Lista de endereços IP a serem usados {#list-of-ip-addresses-to-use}

A configuração relativa ao gerenciamento de tráfego está localizada na variável **mta/child/smtp** elemento do arquivo de configuração.

Para cada **IPAffinity** é necessário declarar os endereços IP que podem ser usados para a máquina.

Exemplo:

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

Os parâmetros são os seguintes:

* **endereço**: este é o endereço IP da máquina host do MTA que será usada.
* **heloHost**: esse identificador representa o endereço IP como ele será visto pelo servidor SMTP.

* **publicId**: essas informações são úteis quando um endereço IP é compartilhado por vários Adobe Campaign **mtas** atrás de um roteador NAT. O servidor de estatísticas usa esse identificador para memorizar a conexão e enviar estatísticas entre esse ponto de partida e o servidor de destino.
* **peso**: permite definir a frequência relativa de uso do endereço. Por padrão, todos os endereços têm um peso igual a 1.

>[!NOTE]
>
>No arquivo serverConf.xml, é necessário verificar se um IP corresponde a um único helohost com um identificador exclusivo (public_id). Ele não pode ser mapeado para vários helohosts, o que pode resultar em problemas de limitação de delivery.

No exemplo anterior, com condições normais, os endereços serão distribuídos da seguinte maneira:

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

Se, por exemplo, o primeiro endereço não puder ser usado para um determinado MX, as mensagens serão enviadas da seguinte maneira:

    * &quot;2&quot;: 5 / (5+1) = 83%
    * &quot;3&quot;: 1 / (5+1) = 17%

* **includeDomains**: permite reservar esse endereço IP para emails pertencentes a um domínio específico. Esta é uma lista de máscaras que podem conter um ou mais curingas (&#39;&#42;&#39;). Se o atributo não for especificado, todos os domínios poderão usar esse endereço IP.

   Exemplo: **includeDomains=&quot;wanadoo.com,orange.com,yahoo.&#42;&quot;**

* **excludeDomains**: exclui uma lista de domínios para este endereço IP. Esse filtro é aplicado depois que a variável **includeDomains** filtro.

   ![](assets/s_ncs_install_mta_ips.png)

## Otimização do envio de email {#email-sending-optimization}

A arquitetura interna do Adobe Campaign **mta** O tem um impacto na configuração para otimizar a entrega de emails. Estas são algumas dicas para melhorar seus deliveries.

### Ajustar o parâmetro maxWaitingMessages {#adjust-the-maxwaitingmessages-parameter}

A variável **maxWaitingMessages** indica o maior número de mensagens preparadas antecipadamente pelo **mtachild**. As mensagens só são excluídas dessa lista depois de serem enviadas ou abandonadas.

Esse parâmetro é muito importante e particularmente importante se as mensagens não forem classificadas por domínio.

Quando a variável **maxWorkingSetMb** (256) se o limite for atingido, o servidor de delivery parará de enviar mensagens. O desempenho diminuirá significativamente até que o **mtachild** O é iniciado novamente. Para contornar esse problema, você pode aumentar o limite do **maxWorkingSetMb** parâmetro ou diminua o limite da variável **maxWaitingMessages** parâmetro.

A variável **maxWorkingSetMb** é calculado empiricamente multiplicando o número máximo de mensagens pelo tamanho médio da mensagem e multiplicando o resultado por 2,5. Por exemplo, se uma mensagem tiver um tamanho médio de 50 kB e a variável **maxWaitingMessages** for igual a 1.000, a memória usada terá em média 125 MB.

### Ajustar o número de mtachild {#adjust-the-number-of-mtachild}

O número de filhos não deve exceder o número de processadores na máquina (aprox. 1000 sessões). Recomendamos que você não exceda 8 **mtachild**. Você poderá então aumentar o número de mensagens por **filho** (**maxMsgPerChild**) para atingir um tempo de vida suficiente.
