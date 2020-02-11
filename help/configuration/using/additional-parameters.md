---
title: Parâmetros adicionais
seo-title: Parâmetros adicionais
description: Parâmetros adicionais
seo-description: null
page-status-flag: never-activated
uuid: c223c84a-f8fd-43d3-9deb-b1c19d442c65
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 1b2ae224-8406-4506-b589-6e5f6631e87f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# Parâmetros adicionais{#additional-parameters}

## Definição dos parâmetros {#definition-of-parameters}

Sua plataforma do Adobe Campaign oferece dois parâmetros de rastreamento da Web do tipo TRANSACTION como padrão:

* **montante**: representa o montante de uma transação,
* **artigo**: representa o número de itens em uma transação.

Esses parâmetros são definidos no esquema **nms:webTrackingLog** e são alguns dos indicadores vistos nos relatórios.

Para definir parâmetros adicionais, você deve estender este esquema.

**Exemplo**:

```
<srcSchema extendedSchema="nms:webTrackingLog" label="Web Tracking"
           mappingType="sql" name="webTrackingLog" 
           namespace="cus" xtkschema="xtk:srcSchema">

  <element name="webTrackingLog">
    <attribute desc="Payment method" label="Payment method" length="10" name="mode" type="string"/>
    <attribute desc="Offer code" label="Offer code" length="5" name="code" type="string"/>
  </element>
</srcSchema>
```

Você pode exibir os valores desses parâmetros configurando a lista de log de rastreamento (de uma entrega ou destinatário).

## Redirecionar configuração do servidor {#redirection-server-configuration}

Na configuração do servidor, é possível definir o número máximo de caracteres a serem considerados para seus parâmetros de rastreamento da Web.

>[!CAUTION]
>
>O aumento do número máximo de caracteres a serem considerados pode afetar o desempenho do rastreamento da Web de sua plataforma.

Para fazer isso, modifique o atributo **webTrackingParamSize** do **`<trackinglogd>`** elemento no arquivo **serverConf.xml** . Esse arquivo é salvo no subdiretório **conf** do diretório de instalação do Adobe Campaign.

**Exemplo**:

O valor padrão é 64 caracteres. Esse valor permite levar em conta a **quantidade** e os parâmetros padrão do **artigo** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxxx&quot;).

Levando em conta os dois parâmetros (tamanho do nome + tamanho do valor) indicados no exemplo de esquema de extensão acima, você pode modificar a configuração para levar em conta 100 caracteres (&quot;amount=xxxxxxxxx&amp;article=xxxxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Quando a configuração for modificada, você deverá:

* Pare o servidor Web que hospeda o módulo de redirecionamento (Apache, IIS etc.),
* Pare o servidor do Adobe Campaign: **net stop nlserver6** in Windows, **/etc/init.d/nlserver6 stop** in Linux,
* No Linux, exclua os segmentos de memória compartilhada usando o comando **ipcrm** ,
* Reinicie o servidor do Adobe Campaign: iniciar **net nlserver6** no Windows, **/etc/init.d/nlserver6 iniciar** no Linux,
* Reinicie o servidor Web.

**Exemplo**: tendo em conta a configuração no Linux.

```
adobe@selma:~$ /etc/init.d/nlserver6 stop
adobe@selma:~$ /etc/init.d/apache stop
adobe@selma:~$ ipcs shm

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x52020679 2097153    adobe   666        93608      8                       

------ Semaphore Arrays --------
key        semid      owner      perms      nsems     
0x52020678 4227081    adobe   666        1         

------ Message Queues --------
key        msqid      owner      perms      used-bytes   messages    

adobe@selma:~$ ipcrm shm 2097153                             
1 resource(s) deleted
adobe@selma:~$ /etc/init.d/nlserver6 start
adobe@selma:~$ /etc/init.d/apache start
```

>[!NOTE]
>
>Para Linux, se você aumentar o tamanho dos parâmetros **webTrackingParamSize** ou **maxSharedLogs** , talvez seja necessário aumentar o tamanho da memória compartilhada (SHM).

