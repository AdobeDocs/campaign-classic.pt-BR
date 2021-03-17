---
solution: Campaign Classic
product: campaign
title: Interação - buffer de dados
description: Interação - buffer de dados
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 17%

---


# Interação - buffer de dados{#interaction-data-buffer}

É possível configurar uma zona de buffer de dados para aumentar o desempenho do Interaction de entrada ao dessincronizar os cálculos de apresentação de oferta. Essa configuração deve ser executada no próprio arquivo de configuração da instância (config-Instance.xml).

No Adobe Campaign, uma **zona de buffer de dados** foi introduzida no módulo Interação. Isso permite **aumentar o desempenho** da interação de entrada ao dessincronizar cálculos de estoque e oferta.

Ela só diz respeito à interação de entrada, seja por uma chamada (com ou sem dados de chamada) ou por uma atualização de status (updateStatus).

Para evitar uma fila ao escrever propostas relacionadas a um recipient, um novo processo gera uma **zona de buffer de dados** que permite que as propostas sejam **escritas de forma assíncrona**. Essa zona de buffer de dados é periodicamente lida e esvaziada. O período padrão é de cerca de um segundo.A escrita da proposta é então agrupada.

>[!NOTE]
>
>Esse parâmetro é essencial se usar o Interaction com uma arquitetura distribuída.

A zona de buffer de dados **configuration** pode ser feita no arquivo de configuração da instância (config-Instance.xml).

>[!CAUTION]
>
>Algumas configurações só podem ser executadas pelo Adobe para implantações hospedadas pelo Adobe. Por exemplo, para acessar os arquivos de configuração do servidor e da instância. Para saber mais sobre as diferentes implantações, consulte a seção [Modelos de hospedagem](../../installation/using/hosting-models.md) ou [esta página](../../installation/using/capability-matrix.md).
>
>Qualquer alteração feita na configuração requer uma reinicialização do servidor da Web (Apache:IIS) e dos processos do Adobe Campaign.\
>Após configurar a zona de buffer de dados, verifique se uma configuração de hardware adaptada está disponível. (quantidade de memória presente).


Após configurar a zona de buffer de dados, verifique se uma configuração de hardware adaptada está disponível. (quantidade de memória presente).

A definição de um daemon de gravação (processo chamado: interação) é o seguinte:

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Se você usar a Interação de entrada, o atributo @autostart deverá ser &quot;true&quot; para iniciar automaticamente o processo quando o servidor do Adobe Campaign for iniciado.

Detalhes do argumento:

```
 args: Start-up parameters 
 autoStart: Automatic start Default: false 
 callDataSize: Max. number of characters stored in the shared memory for call data
 Default: 0 
 initScript: ID of JavaScript to execute when starting the process 
 maxProcessMemoryAlertMb: Alert concerning the amount of RAM consumed (in Mb) by a given process Default: 1800 
 maxProcessMemoryWarningMb: Warning concerning the amount of RAM consumed (in Mb) by a given process Default: 1600 
 maxSharedEntries: Max. number of events stored in the shared memory. Default: 25000 
 nextOffersSize: Maximum number of eligible offers sorted right after propositions, to be stored for statistics Default: 0 
 processRestartTime: Time of the day when the process is automatically restartedDefault: '06:00:00' 
 runLevel: Priority at start Default: 10 
 targetKeySize: Max. number of characters stored in the shared memory for identifying individuals Default: 16 
```

