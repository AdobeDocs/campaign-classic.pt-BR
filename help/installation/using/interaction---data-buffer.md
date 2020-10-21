---
title: Interação - buffer de dados
seo-title: Interação - buffer de dados
description: Interação - buffer de dados
seo-description: null
page-status-flag: never-activated
uuid: 4cb742b5-6bde-43e8-b26b-16f27dd65f72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: cbfdeb2f-4f20-45b8-8cc0-89362f9ea9c1
translation-type: tm+mt
source-git-commit: 3acf2359c74a3dc4b18c8976fee14dcbaf3fa510
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 4%

---


# Interação - buffer de dados{#interaction-data-buffer}

>[!NOTE]
>
>Algumas configurações só podem ser executadas por Adobe para implantações hospedadas por Adobe. Por exemplo, para acessar os arquivos de configuração do servidor e da instância. Para saber mais sobre as diferentes implantações, consulte a seção Modelos [de](../../installation/using/hosting-models.md) hospedagem ou [esta página](../../installation/using/capability-matrix.md).

No Adobe Campaign, uma zona **de buffer de** dados foi introduzida no módulo Interação. Isso permite **aumentar o desempenho** da interação de entrada ao dessincronizar cálculos de ações e ofertas.

Só diz respeito à Interação de entrada, seja por uma chamada (com ou sem dados de chamada) ou por uma atualização de status (updateStatus).

Para evitar uma fila ao escrever propostas relacionadas a um recipient, um novo processo gera uma zona **de buffer de** dados que permite que as propostas sejam **escritas de forma assíncrona**. Essa zona de buffer de dados é periodicamente lida e esvaziada. O período padrão está no espaço de aproximadamente um segundo.A escrita de propostas é, portanto, agrupada.

A **configuração** da zona de buffer de dados pode ser feita no arquivo de configuração da instância (config-Instance.xml).

>[!NOTE]
>
>Qualquer alteração feita na configuração requer uma reinicialização do servidor da Web (Apache:IIS) e dos processos da Adobe Campaign.\
>Depois de configurar a zona de buffer de dados, verifique se há uma configuração de hardware adaptada disponível. (quantidade de memória presente).

Depois de configurar a zona de buffer de dados, verifique se há uma configuração de hardware adaptada disponível. (quantidade de memória presente).

A definição de um daemon de gravação (processo chamado: interações) é o seguinte:

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Se você usar a Interação de entrada, o atributo @autostart deverá ser &quot;true&quot; para iniciar automaticamente o processo quando o servidor Adobe Campaign for iniciado.

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

