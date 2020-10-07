---
title: Comandos usuais
seo-title: Comandos usuais
description: Comandos usuais
seo-description: null
page-status-flag: never-activated
uuid: f06df8c0-d4ec-4d6b-84d5-f46d852388a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 90718075-87a7-4e9a-935b-571010908e79
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 3%

---


# Comandos usuais{#usual-commands}

Esta seção lista os comandos comuns no Adobe Campaign.

O comando **nlserver** é o comando input para todo o aplicativo Adobe Campaign.

Esse comando tem a seguinte sintaxe: **nlserver **`<command>`****`<arguments>`****

O parâmetro **`<command>`** corresponde ao módulo.

>[!NOTE]
>
>* Em qualquer caso, você pode adicionar o argumento **-noconsole** para excluir os comentários exibidos assim que os módulos forem iniciados.
>* Por outro lado, é possível adicionar o argumento **-detalhado** para exibir mais informações.

>



## Comandos de monitoramento {#monitoring-commands-}

>[!NOTE]
>
>Para lista de todos os módulos, é necessário usar o comando **nlserver pdump** .

Você pode adicionar o parâmetro **- que** deve lista as conexões em andamento (banco de dados e aplicativo).

```
nlserver pdump -who
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
web@default (9984) - 50.1 Mo
watchdog (2273) - 6.6 Mo
syslogd@default (9931) - 7.0 Mo
trackinglogd@default (9985) - 45.6 Mo
mta@test (9986) - 9.6 Mo
wfserver@test (9987) - 8.8 Mo

Connections ------------------------------------------------------
Last Access IP Instance Login 
DD/MM/YYYY HH:MM:SS 127.0.0.1 default formation_fr|tracking
DD/MM/YYYY HH:MM:SS 127.0.0.1 default internal|monitoring

Connection pool --------------------------------------------------
Datasource Server Provider Login 
default xxxxx myserver myprovider test400
```

Outro comando útil é o monitor **nlserver**. Ele lista o arquivo XML de monitoramento (obtido no cliente Adobe Campaign ou pela página da Web **monitor.jsp** ).

Você pode adicionar o parâmetro **-missing** para lista dos módulos ausentes (erro em módulos, módulos desligados etc.)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Isso corresponde aos módulos com inicialização automática, mas que não foram iniciados.

## Comandos de inicialização do módulo {#module-launch-commands}

A sintaxe para iniciar módulos ainda terá o seguinte formato:

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** corresponde ao nome da instância conforme inserido nos arquivos de configuração, ou **padrão** para módulos de instância mono.

## Serviços de desligamento {#shut-down-services}

Para parar os serviços Adobe Campaign, use um dos seguintes comandos:

* Se você tiver acesso de raiz ou de administrador:

   * No Linux:

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >A partir do 20.1, recomendamos usar o seguinte comando (para Linux): **system ctl stop nlserver**

   * No Windows:

      ```
      net stop nlserver6
      ```

* Caso contrário, na conta da Adobe Campaign:

   ```
   nlserver shutdown 
   ```

## Reiniciar serviços {#restart-services}

Da mesma forma, para reiniciar o Adobe Campaign, você pode usar um dos seguintes comandos:

* Se você tiver acesso de raiz ou de administrador:

   * No Linux: start /etc/init.d/nlserver6

      >[!NOTE]
      >
      >A partir do 20.1, recomendamos usar o seguinte comando (para Linux): **start nlserver do systemctl**

   * No Windows: start net nlserver6

* Caso contrário, na conta Adobe Campaign: **nlserver watchdog -svc -noconsole**

## O comando config {#the-config-command}

O comando **config** permite gerenciar a configuração do servidor, incluindo a reconfiguração da conexão do banco de dados.

Use o comando **config** do arquivo executável **nlserver** com o parâmetro **-setdblogin** .

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Digite a senha.

Para alterar a senha **interna** : **nlserver config -internalpassword**

>[!CAUTION]
>
>Para fazer logon com o identificador **Interno** , é necessário ter definido uma senha previamente. Para obter mais informações, consulte [esta seção](../../installation/using/campaign-server-configuration.md#internal-identifier).

>[!NOTE]
>
>* Em geral, em vez de modificar os arquivos de configuração manualmente, você pode usar o comando **config**
>* Para obter a lista dos parâmetros, use o **-?** parâmetro: **configuração nlserver -?**
>* No caso de um banco de dados Oracle, você não deve especificar a conta. A sintaxe será a seguinte:

>
>  
nlserver config -setdblogin:Oracle:test6@dbserver


