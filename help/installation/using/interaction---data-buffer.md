---
product: campaign
title: Interação - buffer de dados
description: Interação - buffer de dados
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 17%

---

# Interação - buffer de dados{#interaction-data-buffer}



É possível configurar uma zona de buffer de dados para aumentar o desempenho do Interaction de entrada ao dessincronizar os cálculos de apresentação de oferta. Essa configuração deve ser executada no próprio arquivo de configuração da instância (config-Instance.xml).

No Adobe Campaign, uma **zona de buffer de dados** foi introduzido no módulo de interação. Isso permite **aumentar o desempenho** de interação de entrada ao dessincronizar cálculos de estoque e oferta.

Ela só afeta a interação de entrada, seja por uma chamada (com ou sem dados de chamada) ou por uma atualização de status (updateStatus).

Para evitar uma fila ao escrever propostas relacionadas a um recipient, um novo processo gera uma **zona de buffer de dados** que permita que as propostas sejam **gravado de forma assíncrona**. Essa zona de buffer de dados é lida e esvaziada periodicamente. O período padrão está no espaço de aproximadamente um segundo. A gravação da proposta é, portanto, agrupada.

>[!NOTE]
>
>Esse parâmetro é essencial se usar o Interaction com uma arquitetura distribuída.

Zona de buffer de dados **configuração** pode ser feito no arquivo de configuração da instância (config-Instance.xml).

>[!CAUTION]
>
>Algumas configurações só podem ser executadas por Adobe para implantações hospedadas por Adobe. Por exemplo, para acessar os arquivos de configuração do servidor e da instância. Para saber mais sobre as diferentes implantações, consulte o [Modelos de hospedagem](../../installation/using/hosting-models.md) ou para [esta página](../../installation/using/capability-matrix.md).
>
>Quaisquer alterações feitas na configuração exigem uma reinicialização do servidor Web (Apache:IIS) e dos processos do Adobe Campaign.\
>Depois de configurar a zona de buffer de dados, verifique se uma configuração de hardware adaptada está disponível. (quantidade de memória presente).


Depois de configurar a zona de buffer de dados, verifique se uma configuração de hardware adaptada está disponível. (quantidade de memória presente).

A definição de um daemon de gravação (processo chamado: interação) é a seguinte:

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
