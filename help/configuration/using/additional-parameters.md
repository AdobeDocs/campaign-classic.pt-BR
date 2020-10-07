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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---


# Parâmetros adicionais{#additional-parameters}

## Definição dos parâmetros {#definition-of-parameters}

Sua plataforma Adobe Campaign oferta dois parâmetros de rastreamento da Web do tipo TRANSACTION como padrão:

* **montante**: representa o montante de uma transação,
* **artigo**: representa o número de itens em uma transação.

Esses parâmetros são definidos no schema **nms:webTrackingLog** e são alguns dos indicadores vistos no relatórios.

Para definir parâmetros adicionais, você deve estender esse schema.

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

É possível exibir os valores desses parâmetros configurando a lista do log de rastreamento (de um delivery ou recipient).

## Redirecionar configuração do servidor {#redirection-server-configuration}

Na configuração do servidor, é possível definir o número máximo de caracteres a serem considerados para seus parâmetros de rastreamento da Web.

>[!IMPORTANT]
>
>O aumento do número máximo de caracteres a serem considerados pode afetar o desempenho do rastreamento da Web de sua plataforma.

Para fazer isso, modifique o atributo **webTrackingParamSize** do **`<trackinglogd>`** elemento no arquivo **serverConf.xml** . Esse arquivo é salvo no subdiretório **conf** do diretório de instalação do Adobe Campaign.

**Exemplo**:

O valor padrão é 64 caracteres. Esse valor permite levar em conta a **quantidade** e os parâmetros padrão do **artigo** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxxx&quot;).

Levando em consideração os dois parâmetros (tamanho do nome + tamanho do valor) indicados no exemplo de schema de extensão acima, você pode modificar a configuração para levar em conta 100 caracteres (&quot;amount=xxxxxxxxx&amp;article=xxxxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Quando a configuração for modificada, você deverá:

* Pare o servidor Web que hospeda o módulo de redirecionamento (Apache, IIS etc.),
* Pare o servidor Adobe Campaign: **net stop nlserver6** in Windows, **/etc/init.d/nlserver6 stop** in Linux,

   >[!NOTE]
   >
   >A partir do 20.1, recomendamos usar o seguinte comando (para Linux): **system ctl stop nlserver**

* No Linux, exclua os segmentos de memória compartilhada usando o comando **ipcrm** ,
* Reinicie o servidor Adobe Campaign: **start net nlserver6** no Windows, start **/etc/init.d/nlserver6** no Linux,

   >[!NOTE]
   >
   >A partir do 20.1, recomendamos usar o seguinte comando (para Linux): **start nlserver do systemctl**

* Reinicie o servidor da Web.

**Exemplo**: tendo em conta a configuração no Linux.

```
adobe@selma:~$ systemctl stop nlserver
adobe@selma:~$ systemctl stop apache2
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
adobe@selma:~$ systemctl start nlserver
adobe@selma:~$ systemctl start apache2
```

>[!NOTE]
>
>Para Linux, se você aumentar o tamanho dos parâmetros **webTrackingParamSize** ou **maxSharedLogs** , talvez seja necessário aumentar o tamanho da memória compartilhada (SHM).

