---
product: campaign
title: Parâmetros adicionais de rastreamento Web
description: Saiba mais sobre parâmetros de rastreamento Web
feature: Configuration, Instance Settings
role: Developer
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Parâmetros adicionais de rastreamento Web{#additional-parameters}

## Definição de parâmetros {#definition-of-parameters}

Sua plataforma Adobe Campaign oferece dois parâmetros de rastreamento Web do tipo TRANSAÇÃO como padrão:

* **amount**: representa a quantidade de uma transação,
* **artigo**: representa o número de itens em uma transação.

Esses parâmetros estão definidos no esquema **nms:webTrackingLog** e são alguns dos indicadores vistos nos relatórios.

Para definir parâmetros adicionais, é necessário estender esse schema.

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

Você pode exibir os valores desses parâmetros configurando a lista de log de rastreamento (de um delivery ou recipient).

## Configuração do servidor de redirecionamento {#redirection-server-configuration}

Na configuração do servidor, é possível definir o número máximo de caracteres a serem considerados nos parâmetros de rastreamento Web.

>[!IMPORTANT]
>
>O aumento do número máximo de caracteres a serem considerados pode afetar o desempenho do rastreamento web da sua plataforma.

Para fazer isso, modifique o atributo **webTrackingParamSize** do elemento **`<trackinglogd>`** no arquivo **serverConf.xml**. Este arquivo foi salvo no subdiretório **conf** do diretório de instalação do Adobe Campaign.

**Exemplo**:

O valor padrão é 64 caracteres. Este valor permite que você considere o **valor** e o **artigo** (&quot;valor=xxxxxxx&amp;artigo=xxxxxxxx&quot;) parâmetros padrão.

Considerando ambos os parâmetros (tamanho do nome + tamanho do valor) indicados no exemplo de esquema de extensão acima, você pode modificar a configuração para considerar 100 caracteres (&quot;amount=xxxxxxx&amp;article=xxxxxxx&amp;mode=xxxxxxxxx&amp;code=xxxxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Quando a configuração tiver sido modificada, você deverá:

* Pare o servidor Web que hospeda o módulo de redirecionamento (Apache, IIS etc.),
* Pare o servidor do Adobe Campaign: **net stop nlserver6** no Windows, **/etc/init.d/nlserver6 stop** no Linux,

  >[!NOTE]
  >
  >A partir da versão 20.1, recomendamos usar o seguinte comando (para Linux): **systemctl stop nlserver**

* No Linux, exclua os segmentos de memória compartilhada usando o comando **ipcrm**,
* Reinicie o servidor Adobe Campaign: **net start nlserver6** no Windows, **/etc/init.d/nlserver6 start** no Linux,

  >[!NOTE]
  >
  >A partir da versão 20.1, recomendamos usar o seguinte comando (para Linux): **systemctl start nlserver**

* Reinicie o servidor Web.

**Exemplo**: levando em conta a configuração no Linux.

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
>Para Linux, se você aumentar o tamanho dos parâmetros **webTrackingParamSize** ou **maxSharedLogs**, talvez seja necessário aumentar o tamanho da memória compartilhada (SHM).
