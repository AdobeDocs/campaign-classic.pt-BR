---
product: campaign
title: Configuração das configurações de Delivery de campanha
description: Saiba como definir as configurações de Entrega do Campaign
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 5%

---

# Definir configurações de entrega {#delivery-settings}

![](../../assets/v7-only.svg)

Os parâmetros de delivery devem ser configurados na pasta **serverConf.xml**.

* **Configuração** DNS: especifique o domínio de delivery e os endereços IP (ou host) dos servidores DNS usados para responder a consultas DNS do tipo MX feitas pelo módulo MTA a partir de  **`<dnsconfig>`** agora.

   >[!NOTE]
   >
   >O parâmetro **nameServers** é essencial para uma instalação no Windows. Para uma instalação no Linux, ela deve ficar vazia.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Você também pode executar as seguintes configurações, dependendo das suas necessidades e configurações: configure um [retransmissão SMTP](#smtp-relay), adapte o número de [processos filho MTA](#mta-child-processes), [Gerenciar tráfego SMTP de saída](#managing-outbound-smtp-traffic-with-affinities).

## Retransmissão SMTP {#smtp-relay}

O módulo MTA atua como um agente de transferência de email nativo para transmissão SMTP (porta 25).

No entanto, é possível substituí-lo por um servidor de retransmissão se a política de segurança o exigir. Nesse caso, a taxa de transferência global será a de retransmissão (desde que a taxa de transferência do servidor de retransmissão seja inferior à da Adobe Campaign).

Nesse caso, esses parâmetros são definidos configurando o servidor SMTP na seção **`<relay>`**. Você deve especificar o endereço IP (ou host) do servidor SMTP usado para transferir emails e sua porta associada (25 por padrão).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Esse modo operacional implica sérias limitações nas entregas, pois pode reduzir bastante a taxa de transferência devido aos desempenhos intrínsecos do servidor de retransmissão (latência, largura de banda...). Além disso, a capacidade de qualificar erros de delivery síncronos (detectados pela análise do tráfego SMTP) será limitada e o envio não será possível se o servidor de retransmissão não estiver disponível.

## Processos filho MTA {#mta-child-processes}

É possível controlar o número de processos secundários (maxSpareServers por padrão 2) para otimizar o desempenho da transmissão de acordo com a potência da CPU dos servidores e os recursos de rede disponíveis. Essa configuração deve ser feita na seção **`<master>`** da configuração MTA em cada computador individual.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Consulte também [Otimização do envio de email](../../installation/using/email-deliverability.md#email-sending-optimization).

## Gerenciar o tráfego SMTP de saída com afinidades {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>A configuração de afinidade precisa ser consistente de um servidor para outro. Recomendamos que você entre em contato com o Adobe para obter a configuração de afinidade, pois as alterações de configuração devem ser replicadas em todos os servidores de aplicativos que executam o MTA.

Você pode melhorar o tráfego SMTP de saída por meio de afinidades com endereços IP.

Para fazer isso, siga as etapas abaixo:

1. Insira as afinidades na seção **`<ipaffinity>`** do arquivo **serverConf.xml**.

   Uma afinidade pode ter vários nomes diferentes: para separá-los, use o caractere **;**.

   Exemplo:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Para visualizar os parâmetros relevantes, consulte o arquivo **serverConf.xml**.

1. Para ativar a seleção de afinidade nas listas suspensas, é necessário adicionar os nomes de afinidade na enumeração **IPAffinity**.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >As enumerações são detalhadas em [this document](../../platform/using/managing-enumerations.md).

   Você pode selecionar a afinidade a ser usada, conforme mostrado abaixo para tipologias:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >Você também pode consultar [Configuração do servidor de delivery](../../installation/using/email-deliverability.md#delivery-server-configuration).

**Tópicos relacionados**
* [Configurações técnicas de email](email-deliverability.md)
* [Utilização de servidores MX com o Campaign](using-mx-servers.md)
* [Configurar email Cco](email-archiving.md)
