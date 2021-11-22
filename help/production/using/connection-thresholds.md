---
product: campaign
title: Limites de conexão
description: Limites de conexão
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# Limites de conexão{#connection-thresholds}

![](../../assets/v7-only.svg)

Para servidores muito carregados, o limite de conexão pode ser excedido. Seja como for, é útil descobrir porquê.

Há três limites diferentes:

* O **Limite da conexão Web**, configurado no servidor da Web. Para modificá-lo, entre em contato com o administrador do sistema.

* O **limite de conexão de banco de dados**. Para modificá-lo, entre em contato com o administrador do banco de dados.

* O **Limite de conexão do Adobe Campaign**, disponíveis em dois lugares:

   * **Tomcat** lado: todas as consultas que chegaram no cliente Adobe Campaign Tomcat.

      Esse limite é configurado na variável **nl6/tomcat-8/conf/server.xml** arquivo. O **maxThreads** permite aumentar o limite do número de queries processados de cada vez. Ele pode ser alterado para 250, por exemplo.

      ```
      <Connector protocol="HTTP/1.1" port="8080"
                     maxThreads="75"
                     minSpareThreads="5"
                     enableLookups="true" redirectPort="8443"
                     acceptCount="100" connectionTimeout="20000"
                     disableUploadTimeout="true" />
          <Engine name="Tomcat-Standalone" defaultHost="localhost">
            <Host name="localhost" appBase="./"
                  unpackWARs="true" autoDeploy="true">
      ```

   * **Banco de dados**: conjunto de todas as conexões abertas ao mesmo tempo no banco de dados por um processo.

      Esse limite é configurado no arquivo **nl6/conf/serverConf.xml**. O **maxCnx** atributo localizado em **pool de origens de dados** permite aumentar o limite de consultas processadas simultaneamente.

      ```
          <!-- Data source
               -->
            <dataSource name="default">
              <dbcnx NChar="" bulkCopyUtility="" dbSchema="" encrypted="" login="" password="" provider="" server="" timezone="" unicodeData="" useTimestampTZ=""/>
              <sqlParams funcPrefix="">
                <postConnectSQL/>
              </sqlParams>
              <pool aliveTestDelaySec="600" freeCnx="0" maxCnx="90" maxIdleDelaySec="1200"/>
            </dataSource>
      ```
