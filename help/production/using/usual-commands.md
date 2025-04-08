---
product: campaign
title: Comandos usuais
description: Comandos usuais
feature: Monitoring
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 6%

---

# Comandos usuais{#usual-commands}



Esta seção lista os comandos habituais no Adobe Campaign.

O comando **nlserver** é o comando de entrada para todo o aplicativo Adobe Campaign.

Este comando tem a seguinte sintaxe: **nlserver **`<command>`****`<arguments>`****

O parâmetro **`<command>`** corresponde ao módulo.

>[!NOTE]
>
>* Em qualquer caso, você pode adicionar o argumento **-noconsole** para excluir comentários exibidos depois que os módulos forem iniciados.
>* Por outro lado, você pode adicionar o argumento **-verbose** para exibir mais informações.
>

## Monitoramento de comandos {#monitoring-commands-}

>[!NOTE]
>
>Para listar todos os módulos, é necessário usar o comando **nlserver pdump**.

Você pode adicionar o parâmetro **-who** para listar as conexões em andamento (banco de dados e aplicativo).

```sql
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

Outro comando útil é **nlserver monitor**. Ele lista o arquivo XML de monitoramento (obtido no cliente Adobe Campaign ou por meio da página da Web **monitor.jsp**).

Você pode adicionar o parâmetro **-missing** para listar os módulos ausentes (erro nos módulos, módulos encerrados, etc.)

```sql
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Isso corresponde aos módulos com inicialização automática, mas que não foram inicializados.

## Comandos de inicialização do módulo {#module-launch-commands}

A sintaxe dos módulos de inicialização ainda terá o seguinte formato:

```sql
nlserver start <module>@<INSTANCE>
```

```sql
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** corresponde ao nome da instância conforme inserido nos arquivos de configuração, ou **default** para módulos de instância única.

## Desligar serviços {#shut-down-services}

Para interromper serviços do Adobe Campaign, use um dos seguintes comandos:

* Se você tiver acesso de raiz ou administrador:

   * No Linux:

     ```sql
     /etc/init.d/nlserver6 stop
     ```

     >[!NOTE]
     >
     >A partir da versão 20.1, recomendamos usar o seguinte comando (para Linux): **systemctl stop nlserver**

   * No Windows:

     ```sql
     net stop nlserver6
     ```

* Caso contrário, na conta do Adobe Campaign:

  ```sql
  nlserver shutdown 
  ```

## Reiniciar serviços {#restart-services}

Da mesma forma, para reiniciar o Adobe Campaign, você pode usar um dos seguintes comandos:

* Se você tiver acesso de raiz ou administrador:

   * No Linux: `/etc/init.d/nlserver6 start`

     >[!NOTE]
     >
     >A partir da versão 20.1, recomendamos usar o seguinte comando (para Linux): **systemctl start nlserver**

   * No Windows: `net start nlserver6`

* Caso contrário, na conta do Adobe Campaign: **nlserver watchdog -svc -noconsole**

## O comando config {#the-config-command}

O comando **config** permite gerenciar a configuração do servidor, incluindo a reconfiguração da conexão do banco de dados.

Use o comando **config** do arquivo executável **nlserver** com o parâmetro **-setdblogin**.

```sql
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```sql
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Digite a senha.

Para alterar a senha **interna**: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>Para fazer logon com o identificador **Interno**, é necessário definir uma senha antecipadamente. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* Em geral, em vez de modificar manualmente os arquivos de configuração, você pode usar o comando **config**
>* Para obter a lista de parâmetros, use os parâmetros **-?** parâmetro: **nlserver config -?**
>* No caso de um banco de dados Oracle, você não deve especificar a conta. A sintaxe será a seguinte:
>
>  `nlserver config -setdblogin:Oracle:test6@dbserver`
>

Veja um exemplo do MSSQL:

```sql
nlserver config -setdblogin:mssql:<login>/"<password>"@<server> -instance:<instance_name> 
```

* logon (por exemplo, account:user) e o servidor podem ser encontrados no nó dataSource do arquivo config-&lt;instance_name>.xml.
* A senha deve ser colocada entre aspas &quot;&quot;.

