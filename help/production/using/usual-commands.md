---
product: campaign
title: Comandos usuais
description: Comandos usuais
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 4%

---

# Comandos usuais{#usual-commands}



Esta seção lista os comandos habituais no Adobe Campaign.

O comando **nlserver** é o comando de entrada para todo o aplicativo do Adobe Campaign.

Esse comando tem a seguinte sintaxe: **nlserver **`<command>`****`<arguments>`****

O parâmetro **`<command>`** corresponde ao módulo.

>[!NOTE]
>
>* Em qualquer caso, você pode adicionar a variável **-noconsole** argumento para excluir comentários exibidos depois que os módulos são iniciados.
>* Por outro lado, é possível adicionar o argumento **-verboso** para exibir mais informações.
>


## Monitoramento de comandos {#monitoring-commands-}

>[!NOTE]
>
>Para listar todos os módulos, é necessário usar o **despejo nlserver** comando.

Você pode adicionar o parâmetro **-quem** para listar as conexões em andamento (banco de dados e aplicativo).

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

Outro comando útil é **monitor nlserver**. Ele lista o arquivo XML de monitoramento (obtido no cliente do Adobe Campaign ou por meio da variável **monitor.jsp** página da Web).

Você pode adicionar o parâmetro **-ausente** para listar os módulos ausentes (erro nos módulos, módulos encerrados etc.)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Isso corresponde aos módulos com inicialização automática, mas que não foram inicializados.

## Comandos de inicialização do módulo {#module-launch-commands}

A sintaxe dos módulos de inicialização ainda terá o seguinte formato:

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** corresponde ao nome da instância conforme inserido nos arquivos de configuração ou **padrão** para módulos de instância única.

## Desligar serviços {#shut-down-services}

Para interromper serviços do Adobe Campaign, use um dos seguintes comandos:

* Se você tiver acesso de raiz ou administrador:

   * No Linux:

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >A partir da versão 20.1, recomendamos usar o seguinte comando (para Linux): **systemctl stop nlserver**

   * No Windows:

      ```
      net stop nlserver6
      ```

* Caso contrário, na conta do Adobe Campaign:

   ```
   nlserver shutdown 
   ```

## Reiniciar serviços {#restart-services}

Da mesma forma, para reiniciar o Adobe Campaign, você pode usar um dos seguintes comandos:

* Se você tiver acesso de raiz ou administrador:

   * No Linux: início de /etc/init.d/nlserver6

      >[!NOTE]
      >
      >A partir da versão 20.1, recomendamos usar o seguinte comando (para Linux): **systemctl start nlserver**

   * No Windows: net start nlserver6

* Caso contrário, na conta do Adobe Campaign: **nlserver watchdog -svc -noconsole**

## O comando config {#the-config-command}

A variável **config** permite gerenciar a configuração do servidor, incluindo a reconfiguração da conexão de banco de dados.

Use o **config** comando do **nlserver** arquivo executável com o **-setdblogin** parâmetro.

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Digite a senha.

Para alterar o **interno** senha: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>Para fazer logon com a **Interno** identificador, você precisa ter definido uma senha antes. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* Em geral, em vez de modificar os arquivos de configuração manualmente, você pode usar o **config** comando
>* Para obter a lista de parâmetros, use o **-?** parâmetro: **Configuração nlserver -?**
>* No caso de um banco de dados Oracle, você não deve especificar a conta. A sintaxe será a seguinte:
>
>  nlserver config - setdblogin:Oracle:test6@dbserver
