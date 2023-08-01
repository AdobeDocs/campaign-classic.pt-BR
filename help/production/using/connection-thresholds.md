---
product: campaign
title: Limites de conexão
description: Limites de conexão
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Aplicável somente ao Campaign Classic v7"
badge-v7-prem: label="no local e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 12%

---

# Limites de conexão{#connection-thresholds}



Para servidores com muita carga, o limite de conexão pode ser excedido. Em qualquer caso, é útil descobrir o porquê.

Há três limites diferentes:

* A variável **Limite de conexão com a Web**, configurado no servidor Web. Para modificá-lo, entre em contato com o administrador do sistema.

* A variável **limite de conexão de banco de dados**. Para modificá-lo, contate o administrador do banco de dados.

* A variável **Limite de conexão do Adobe Campaign**, disponível em dois lugares:

   * **Tomcat** lado: todas as consultas que chegam de fato ao cliente Adobe Campaign Tomcat.

     Esse limite é configurado na variável **nl6/tomcat-8/conf/server.xml** arquivo. A variável **maxThreads** attribute permite aumentar o limite do número de queries processadas de cada vez. Pode ser alterado para 250, por exemplo.

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

     Esse limite está configurado no arquivo **nl6/conf/serverConf.xml**. A variável **maxCnx** atributo localizado em **pool de fontes de dados** permite aumentar o limite de consultas processadas simultaneamente.

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
