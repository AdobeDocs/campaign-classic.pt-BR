---
product: campaign
title: Configuração técnica de email
description: Saiba como configurar o Campaign para controlar a saída de suas instâncias ao entregar emails
feature: Installation, Deliverability
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 515adad2-6129-450a-bb9e-fc80127835af
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '3094'
ht-degree: 13%

---

# Configurações técnicas de email{#email-deliverability}



## Visão geral {#overview}

A seção a seguir fornece uma visão geral da configuração necessária para controlar a saída das instâncias do Adobe Campaign ao enviar emails.

>[!NOTE]
>
>Algumas configurações só podem ser executadas por Adobe para implantações hospedadas por Adobe, por exemplo, para acessar os arquivos de configuração do servidor e da instância. Para saber mais sobre as diferentes implantações, consulte a seção [Modelos de hospedagem](../../installation/using/hosting-models.md) ou [esta página](../../installation/using/capability-matrix.md).

Para obter mais informações sobre os conceitos e as práticas recomendadas relacionadas à capacidade de entrega com o Adobe Campaign, consulte esta [seção](../../delivery/using/about-deliverability.md).

Para aprofundar o assunto, incluindo todas as recomendações técnicas relacionadas ao envio e recebimento eficientes de emails por uma plataforma Adobe, consulte o [Manual de práticas recomendadas de capacidade de entrega do Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR).

## Princípio operacional {#operating-principle}

É possível controlar a saída de uma ou mais instâncias do Adobe Campaign para restringir o número de emails enviados, dependendo de um domínio. Por exemplo, você pode restringir a saída a 20.000 por hora para endereços **yahoo.com**, ao configurar 100.000 mensagens por hora para todos os outros domínios.

A saída da mensagem precisa ser controlada para cada endereço IP usado pelos servidores de entrega (**mta**). Vários **mta** detalhados em várias máquinas e pertencentes a várias instâncias do Adobe Campaign podem compartilhar o mesmo endereço IP para entrega de email: é necessário configurar um processo para coordenar o uso desses endereços IP.

O módulo **stat** faz isso: encaminha todas as solicitações de conexão e mensagens a serem enviadas aos servidores de email para um conjunto de endereços IP. O servidor de estatísticas rastreia os deliveries e pode habilitar ou desabilitar o envio com base em cotas definidas.

![](assets/s_ncs_install_mta.png)

* O servidor de estatísticas (**stat**) está vinculado a uma base do Adobe Campaign para carregar sua configuração.
* Os servidores de entrega (**mta**) usam um UDP para contatar um servidor de estatísticas que nem sempre pertence a sua própria instância.

### Servidores de entrega {#delivery-servers}

O módulo **mta** distribui mensagens para seus módulos filho **mtachild**. Cada **mtachild** prepara mensagens antes de solicitar uma autorização do servidor de estatísticas e enviá-las.

As etapas são as seguintes:

1. O **mta** seleciona mensagens qualificadas e atribui a elas uma **mtachild** disponível.
1. O **mtachild** carrega todas as informações necessárias para criar a mensagem (conteúdo, elementos de personalização, anexos, imagens etc.) e encaminha a mensagem para o **Formatador de Tráfego de Email**.
1. Assim que o formador de tráfego de email receber a autorização do servidor de estatísticas (**smtp stat**), a mensagem será enviada ao destinatário.

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

O endereço IP de origem corresponde ao endereço IP público, ou seja, ao endereço como é visto pelo servidor de email remoto. Este endereço IP pode ser diferente do endereço da máquina que hospeda o **mta**, se um roteador NAT for fornecido. É por isso que o servidor de estatísticas usa um identificador que corresponde ao IP público (**publicId**). A associação entre o endereço local e este identificador é declarada no arquivo de configuração **serverConf.xml**. Todos os parâmetros disponíveis no **serverConf.xml** estão listados nesta [seção](../../installation/using/the-server-configuration-file.md).

## Controle de saída de entrega {#delivery-output-controlling}

Para enviar mensagens a servidores de email, o componente **Formatador de Tráfego de Email** solicita uma conexão do servidor de estatísticas. Depois que a solicitação é aceita, a conexão é aberta.

Antes de enviar mensagens, o módulo solicita &quot;tokens&quot; do servidor. Geralmente, esses são conjuntos de pelo menos 10 tokens, o que reduz o número de queries ao servidor.

O servidor salva todas as estatísticas relacionadas a conexões e deliveries. No caso de reinicialização, as informações são temporariamente perdidas: cada cliente mantém uma cópia local de suas estatísticas de envio e as retorna ao servidor regularmente (a cada 2 minutos). O servidor pode então reagregar os dados.

As seções a seguir descrevem o processamento de uma mensagem pelo componente **Formatador de Tráfego de Email**.

### Entrega de mensagem {#message-delivery}

Quando uma mensagem é enviada, há três resultados possíveis:

1. **Êxito**: a mensagem foi enviada com êxito. A mensagem é atualizada.
1. **Falha na Mensagem**: o servidor de contato rejeitou a mensagem para o destinatário escolhido. Esse resultado corresponde aos códigos de retorno 550 a 599, mas as exceções podem ser definidas.
1. **Sessão com Falha** (para 5.11 acima): se o **mta** receber uma resposta para esta mensagem, ela será abandonada (consulte [Abandono de mensagem](#message-abandonment)). A mensagem será enviada para outro caminho ou definida como pendente se nenhum outro caminho estiver disponível (consulte [Mensagem pendente](#message-pending)).

   >[!NOTE]
   >
   >Um **caminho** é uma conexão entre o **mta** da Adobe Campaign e o **mta** de destino. O Adobe Campaign **mta** pode escolher entre vários IPs iniciais e vários IPs de domínio de destino.

### Abandono de mensagem {#message-abandonment}

Mensagens abandonadas retornam ao **mta** e não são mais gerenciadas pelo **mtachild**.

O **mta** decide sobre o procedimento para esta mensagem (recuperação, abandono, quarentena, etc.) dependendo do código de resposta e das regras.

### Mensagem pendente {#message-pending}

Uma mensagem fica pendente quando chega à fila ativa e não há caminhos disponíveis.

Um caminho geralmente é marcado como indisponível por um período variável após um erro de conexão. O período de indisponibilidade depende da frequência e da idade dos erros.

## Configuração do servidor de estatísticas {#statistics-server-configuration}

O servidor de estatísticas pode ser usado por várias instâncias: ele deve ser configurado independentemente das instâncias que o usarão.

Comece definindo o banco de dados do Adobe Campaign que hospedará a configuração.

### Configuração inicial {#start-configuration}

Por padrão, o módulo **stat** é iniciado para cada instância. Quando as instâncias são agrupadas na mesma máquina ou quando as instâncias compartilham o mesmo endereço IP, um único servidor de estatísticas é usado: as outras precisam ser desativadas.

### Definição da porta do servidor {#definition-of-the-server-port}

Por padrão, o servidor de estatísticas escuta na porta 7777. Esta porta pode ser modificada no arquivo **serverConf.xml**. Todos os parâmetros disponíveis no **serverConf.xml** estão listados nesta [seção](../../installation/using/the-server-configuration-file.md).

```
<stat port="1234"/>
```

## Configuração MX {#mx-configuration}

>[!IMPORTANT]
>
>Para instalações hospedadas ou híbridas, se você atualizou para o [MTA aprimorado](../../delivery/using/sending-with-enhanced-mta.md), as regras de taxa de transferência da entrega **[!UICONTROL MX management]** não são mais usadas. O MTA aprimorado usa regras de MX próprias que permitem personalizar a taxa de transferência por domínio com base na sua própria reputação histórica de email e no feedback em tempo real proveniente dos domínios em que você está enviando emails.

### Sobre as regras MX {#about-mx-rules}

>[!NOTE]
>
>Esta seção e as seções abaixo se aplicam apenas às instalações no local e instalações hospedadas/híbridas que usam o MTA herdado do Campaign.

As regras MX (Mail eXchanger) são as regras que gerenciam a comunicação entre um servidor de envio e um servidor de recebimento.

Essas regras são recarregadas automaticamente todas as manhãs às 6h (horário do servidor) para fornecer regularmente a instância do cliente.

Dependendo da capacidade do material e da política interna, um ISP aceitará um número predefinido de conexões e mensagens por hora. Essas variáveis podem ser modificadas automaticamente pelo sistema ISP, dependendo da reputação do IP e do domínio de envio. Por meio da sua plataforma de deliverability, o Adobe Campaign gerencia mais de 150 regras específicas pelo ISP e, além disso, uma regra genérica para outros domínios.

O número máximo de conexões não depende exclusivamente do número de endereços IP públicos usados pelo MTA.

Por exemplo, se você permitiu cinco conexões nas regras MX e configurou dois IPs públicos, talvez pense que não é possível abrir mais de dez conexões simultaneamente para esse domínio. Isso não é verdade, de fato, o número máximo de conexões se refere a um caminho, e um caminho que é uma combinação de um de nossos IPs públicos de MTA e um IP público do MTA do cliente.

No exemplo abaixo, o usuário tem dois endereços IP públicos configurados e o domínio é yahoo.com.

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

Registros MX para yahoo.com nos dizem que yahoo.com tem 3 Mail Exchangers. Para conectar o Peer Mail Exchanger, o MTA solicitará o endereço IP do DNS.

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

Para esse registro, o usuário pode entrar em contato com 8 endereços IP de mesmo nível. Como o usuário tem dois endereços IP públicos, ele recebe 8 * 2 = 16 combinações para acessar os servidores de email yahoo.com. Cada uma dessas combinações é chamada de caminho.

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

Quatro desses oito endereços IP já são usados no mta5 (98.136.216.26, 98.138.112.38, 63.250.192.46 e 98.136.217.203). Esse registro permite que o usuário use quatro novos endereços IP. O terceiro registro MX fará o mesmo.

No total, temos 16 endereços IP remotos. Em combinação com nossos dois IPs públicos locais, temos 32 caminhos para alcançar servidores de email yahoo.com.

>[!NOTE]
>
>Se 2 registros MX estiverem fazendo referência ao mesmo endereço IP, este será contado como um caminho e não dois.

Abaixo estão alguns exemplos de uso de regras MX:

![](assets/s_ncs_examples_mx_rules.png)

No exemplo abaixo, o usuário tem um limite de 10.000 mensagens por hora para determinado domínio, mas a capacidade da taxa de transferência MTA é maior que esse limite.

Nesse caso, o tráfego é dividido em 12 períodos de 5 minutos para cada hora e o limite real é 833 mensagens por período.

Essas mensagens serão entregues o mais rápido possível.

![](assets/s_ncs_traffic_shaping.png)

### Configuração da gestão MX {#configuring-mx-management}

As regras a serem seguidas para MX são definidas no documento **[!UICONTROL MX management]** do nó **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** da árvore.

Se o documento **[!UICONTROL MX management]** não existir no nó, você poderá criá-lo manualmente. Para fazer isso:

1. Crie um novo conjunto de regras de email.
1. Escolha o modo **[!UICONTROL MX management]**.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. Insira **defaultMXRules** no campo **[!UICONTROL Internal name]**.

Para que as alterações sejam consideradas, é necessário reiniciar o servidor de estatísticas.

Para recarregar a configuração sem reiniciar o servidor de estatísticas, use o seguinte comando na máquina que hospeda o servidor: `nlserver stat -reload`

>[!NOTE]
>
>Esta linha de comando é preferível à **nreinicialização do servidor**. Ela evita que as estatísticas coletadas antes da reinicialização sejam perdidas e evita picos de uso, o que pode ir contra as cotas definidas nas regras MX.

### Configuração de regras MX {#configuring-mx-rules}

O documento **[!UICONTROL MX management]** lista todos os domínios vinculados a uma regra MX.

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

  Nesse caso, a regra MX `*.google.com` será usada. Como você pode ver, a máscara de regra MX não corresponde necessariamente ao domínio no email. As regras MX aplicadas para endereços de email gmail.com serão aquelas com a máscara `*.google.com`.

* **[!UICONTROL Range of identifiers]**: essa opção permite indicar os intervalos de identificadores (publicID) aos quais a regra se aplica. Você pode especificar:

   * Um número: a regra será aplicada somente a essa publicId,
   * Um intervalo de números (**number1-number2**): a regra será aplicada a todas as publicIds entre esses dois números.

  >[!NOTE]
  >
  >Se o campo estiver vazio, a regra se aplica a todos os identificadores.

  Uma ID pública é um identificador interno de um IP público usado por um ou vários MTAs. Essas IDs são definidas nos servidores MTA no arquivo **config-instance.xml** .

  ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**: define o escopo das propriedades para esta regra MX. Quando marcado, todos os parâmetros serão compartilhados em todos os IPs disponíveis na instância. Quando desmarcadas, as regras MX são definidas para cada IP. O número máximo de mensagens é multiplicado pelo número de IPs disponíveis.
* **[!UICONTROL Maximum number of connections]**: número máximo de conexões simultâneas com o domínio do remetente.
* **[!UICONTROL Maximum number of messages]**: número máximo de mensagens que podem ser enviadas em uma conexão. Quando as mensagens excedem esse número, a conexão é fechada e uma nova é aberta.
* **[!UICONTROL Messages per hour]**: número máximo de mensagens que podem ser enviadas em uma hora para o domínio do remetente.
* **[!UICONTROL Connection time out]**: limite de tempo para conexão com um domínio.

  >[!NOTE]
  >
  >O Windows pode emitir um **tempo limite** antes desse limite, que depende da sua versão do Windows.

* **[!UICONTROL Timeout Data]**: tempo máximo de espera após o envio do conteúdo da mensagem (seção DATA do protocolo SMTP).
* **[!UICONTROL Timeout]**: tempo máximo de espera para outras trocas com o servidor SMTP.
* **[!UICONTROL TLS]**: O protocolo TLS, que permite criptografar entregas de email, pode ser habilitado seletivamente. Para cada máscara MX, as seguintes opções estão disponíveis:

   * **[!UICONTROL Default configuration]**: esta é a configuração geral especificada no arquivo de configuração serverConf.xml que é aplicada.

     >[!IMPORTANT]
     >
     >Não é recomendável modificar a configuração padrão.

   * **[!UICONTROL Disabled]** : As mensagens são enviadas sistematicamente sem criptografia.
   * **[!UICONTROL Opportunistic]**: a entrega de mensagens é criptografada se o servidor de recebimento (SMTP) puder gerar o protocolo TLS.

Exemplo de configuração:

![](assets/s_ncs_install_mx_mgt_rule_details.png)

>[!NOTE]
>
>Para obter mais informações sobre como usar servidores MX com o Adobe Campaign, consulte [esta seção](../../installation/using/using-mx-servers.md).

### Gerenciamento de formatos de email {#managing-email-formats}

Você pode definir o formato das mensagens enviadas, para que o conteúdo exibido se adapte automaticamente de acordo com o domínio do endereço de cada recipient.

Para fazer isso, vá para o documento **[!UICONTROL Management of email formats]**, localizado em **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**.

Este documento contém uma lista de todos os domínios predefinidos que correspondem aos formatos japoneses gerenciados pelo Adobe Campaign. Para obter mais informações, consulte [este documento](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

O parâmetro **estrutura MIME** (Extensões de Email de Internet Multipropósito) permite definir a estrutura de mensagens que será enviada para clientes de email diferentes. Há três opções disponíveis:

* **Multipart**: a mensagem é enviada no formato de texto ou HTML. Se o formato HTML não for aceito, a mensagem ainda poderá ser exibida no formato de texto.

  Por padrão, a estrutura multipart é **multipart/alternative**, mas automaticamente se torna **multipart/related** quando uma imagem é adicionada à mensagem. Alguns provedores esperam o formato **multipart/related** por padrão. A opção **[!UICONTROL Force multipart/related]** impõe esse formato mesmo se nenhuma imagem estiver anexada.

* **HTML**: somente uma mensagem HTML é enviada. Se o formato HTML não for aceito, a mensagem não será exibida.
* **Texto**: uma mensagem no formato somente texto é enviada. A vantagem das mensagens em formato de texto é seu tamanho muito pequeno.

Se a opção **[!UICONTROL Image inclusion]** estiver habilitada, elas serão exibidas diretamente no corpo do email. As imagens serão carregadas e os links de URL serão substituídos pelo conteúdo.

Esta opção é usada principalmente pelo mercado japonês para **Deco-mail**, **Decore Mail** ou **Decoration Mail**. Para obter mais informações, consulte [este documento](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

>[!IMPORTANT]
>
>A inserção de imagens em um email aumenta consideravelmente seu tamanho.

## Configuração do servidor de entrega {#delivery-server-configuration}

### Sincronização do relógio {#clock-synchronization}

Os relógios de todos os servidores que compõem a plataforma Adobe Campaign (incluindo o banco de dados) devem ser sincronizados e seus sistemas definidos para o mesmo fuso horário.

### Coordenadas do servidor de estatísticas {#coordinates-of-the-statistics-server}

O endereço do servidor de estatísticas deve ser fornecido em **mta**.

A propriedade **statServerAddress** do elemento **mta** da configuração permite especificar o endereço e o número da porta a ser usada.

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

Para usar o servidor de estatísticas na mesma máquina, você deve inserir pelo menos o nome da máquina com o valor **localhost**:

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>Se este campo não for preenchido, o **mta** não será iniciado.

### Lista de endereços IP a serem usados {#list-of-ip-addresses-to-use}

A configuração relacionada ao gerenciamento de tráfego está localizada no elemento **mta/child/smtp** do arquivo de configuração.

Para cada elemento **IPAffinity**, é necessário declarar os endereços IP que podem ser usados para a máquina.

Exemplo:

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

Os parâmetros são os seguintes:

* **endereço**: este é o endereço IP da máquina host do MTA que será usado.
* **heloHost**: esse identificador representa o endereço IP como ele será visto pelo servidor SMTP.

* **publicId**: esta informação é útil quando um endereço IP é compartilhado por vários Adobe Campaign **mtas** atrás de um roteador NAT. O servidor de estatísticas usa esse identificador para memorizar a conexão e enviar estatísticas entre esse ponto de partida e o servidor de destino.
* **weight**: permite definir a frequência relativa de uso do endereço. Por padrão, todos os endereços têm um peso igual a 1.

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

* **includeDomains**: permite reservar este endereço IP para emails pertencentes a um domínio específico. Esta é uma lista de máscaras que podem conter um ou mais curingas (&#39;&#42;&#39;). Se o atributo não for especificado, todos os domínios poderão usar esse endereço IP.

  Exemplo: **includeDomains=&quot;wanadoo.com,orange.com,yahoo.&#42;&quot;**

* **excludeDomains**: exclui uma lista de domínios para este endereço IP. Este filtro é aplicado após o filtro **includeDomains**.

  ![](assets/s_ncs_install_mta_ips.png)

## Otimização do envio de email {#email-sending-optimization}

A arquitetura interna do Adobe Campaign **mta** afeta a configuração de otimização da entrega de emails. Estas são algumas dicas para melhorar seus deliveries.

### Ajustar o parâmetro maxWaitingMessages {#adjust-the-maxwaitingmessages-parameter}

O parâmetro **maxWaitingMessages** indica o maior número de mensagens preparadas antecipadamente por **mtachild**. As mensagens só são excluídas dessa lista depois de serem enviadas ou abandonadas.

Esse parâmetro é muito importante e particularmente importante se as mensagens não forem classificadas por domínio.

Quando o limite **maxWorkingSetMb** (256) é atingido, o servidor de entrega para de enviar mensagens. O desempenho diminuirá significativamente até que o **mtachild** reinicie. Para contornar esse problema, aumente o limite do parâmetro **maxWorkingSetMb** ou diminua o limite do parâmetro **maxWaitingMessages**.

O parâmetro **maxWorkingSetMb** é calculado empiricamente, multiplicando-se o número máximo de mensagens pelo tamanho médio da mensagem e multiplicando-se o resultado por 2,5. Por exemplo, se uma mensagem tiver um tamanho médio de 50 kB e o parâmetro **maxWaitingMessages** for igual a 1.000, a memória usada terá em média 125 MB.

### Ajustar o número de mtachild {#adjust-the-number-of-mtachild}

O número de filhos não deve exceder o número de processadores na máquina (aprox. 1000 sessões). Recomendamos que você não exceda 8 **mtachild**. Em seguida, você poderá aumentar o número de mensagens por **criança** (**maxMsgPerChild**) para obter um tempo de vida suficiente.
