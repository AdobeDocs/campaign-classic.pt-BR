---
product: campaign
title: Parâmetros adicionais de rastreamento Web
description: Saiba mais sobre parâmetros para rastreamento Web
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Parâmetros adicionais de rastreamento Web{#additional-parameters}

## Definição dos parâmetros {#definition-of-parameters}

A plataforma Adobe Campaign oferece dois parâmetros de rastreamento Web tipo TRANACTION como padrão:

* **quantia**: representa o valor de uma transação,
* **artigo**: representa o número de itens em uma transação.

Esses parâmetros são definidos na variável **nms:webTrackingLog** e são alguns dos indicadores vistos nos relatórios.

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

Você pode exibir os valores desses parâmetros configurando a lista de logs de rastreamento (de um delivery ou recipient).

## Redirecionar configuração do servidor {#redirection-server-configuration}

Na configuração do servidor, é possível definir o número máximo de caracteres a serem considerados nos parâmetros de rastreamento Web.

>[!IMPORTANT]
>
>O aumento do número máximo de caracteres a serem considerados pode afetar o desempenho do rastreamento Web de sua plataforma.

Para fazer isso, modifique o **webTrackingParamSize** do **`<trackinglogd>`** no **serverConf.xml** arquivo. Esse arquivo é salvo no **conf** subdiretório do diretório de instalação do Adobe Campaign.

**Exemplo**:

O valor padrão é 64 caracteres. Esse valor permite considerar a variável **quantia** e **artigo** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&quot;) parâmetros padrão.

Levando em conta ambos os parâmetros (tamanho do nome + tamanho do valor) indicados no exemplo de esquema de extensão acima, você pode modificar a configuração para levar 100 caracteres em consideração (&quot;amount=xxxxxxxx&amp;article=xxxxxxxxx&amp;mode=xxxxxxxxxxx&amp;code=xxxxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Quando a configuração tiver sido modificada, você deverá:

* Pare o servidor da Web que hospeda o módulo de redirecionamento (Apache, IIS etc.),
* Pare o servidor do Adobe Campaign: **net stop nlserver6** no Windows, **/etc/init.d/nlserver6 stop** no Linux,

   >[!NOTE]
   >
   >A partir da versão 20.1, recomendamos usar o seguinte comando (para Linux): **systemctl stop nlserver**

* No Linux, exclua os segmentos de memória compartilhada usando o **ipcrm** comando,
* Reinicie o servidor do Adobe Campaign: **net start nlserver6** no Windows, **/etc/init.d/nlserver6 start** no Linux,

   >[!NOTE]
   >
   >A partir da versão 20.1, recomendamos usar o seguinte comando (para Linux): **systemctl start nlserver**

* Reinicie o servidor da Web.

**Exemplo**: considerando a configuração no Linux.

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
>Para Linux, se você aumentar o tamanho da variável **webTrackingParamSize** ou **maxSharedLogs** , talvez seja necessário aumentar o tamanho da memória compartilhada (SHM).
