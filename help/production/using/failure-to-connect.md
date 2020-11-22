---
solution: Campaign Classic
product: campaign
title: Falha ao conectar
description: Falha ao conectar
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---


# Falha ao conectar{#failure-to-connect}

Os motivos podem ser múltiplos e dependem de vários contextos.

Verifique a configuração geral das zonas de segurança.

>[!NOTE]
>
>For more on configuring security zones, refer to [this section](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Verifique as seguintes informações:

1. **Verificações de rede**

   * Você tem acesso à Internet em seu computador?

      Verifique se você pode se conectar a sites na Internet (por exemplo). Se você não conseguir se conectar, o problema está em sua máquina. Entre em contato com o administrador do sistema.

   * Você pode se conectar ao servidor que hospeda a Adobe Campaign por meio de outro serviço?

      Conecte-se ao servidor via SSH ou qualquer outro meio. Se isso não for possível, a empresa do host apresenta um problema. Entre em contato com o administrador do sistema.

1. **Verificações no lado** do servidor Web (IIS/apache/etc.)

   * O servidor Web responde?

      Conecte-se ao URL de acesso do servidor Adobe Campaign usando um navegador da Web: **http(s)://`<urlserver>`**. Se não responder, o servidor Web será interrompido no computador. Entre em contato com o administrador do sistema da empresa do host para reiniciar o serviço.

   * A Adobe Campaign foi integrada corretamente?

      Faça logon no: **http(s):// `<urlserver>`/r/test** URL. O servidor deve retornar o seguinte tipo de mensagem

      ```
      <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='<hostname>' localHost='<server>'/>
      ```

      Se você não obtiver esse resultado, verifique na configuração do servidor Web se a integração é considerada.

1. **Verificações no Adobe Campaign**

   * O módulo Adobe Campaign Web foi iniciado?

      Conecte-se ao seguinte URL: **http(s)://`<URLSERVER>`/nl/jsp/logon.jsp**

      * Se você obter um erro Java do Tomcat:

         A integração do JAVA é realizada corretamente? A Adobe Campaign requer um SUN JDK.

         Ele é integrado ao arquivo **`[path of application]`/nl6/customer.sh**

      * Se você obter uma página em branco:

         O módulo Adobe Campaign Web foi iniciado? Você deve obter:

         ```
         nlserver pdump
         HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
         [...]
         web@default (27515) - 55.2 Mb
         [...]
         ```

      * Caso contrário, reinicie usando o seguinte comando:

         ```
         nlserver start web
         ```
>[!NOTE]
>
>Se você obtiver uma resposta do seguinte tipo ao lista dos módulos Adobe Campaign: **pdump nlserver**
>HH:MM:SS > Servidor de aplicativos para Adobe Campaign Classic (compilação 7.X YY.R XXX@SHA1) de DD/MM/AAAA Sem tarefa Você deve reiniciar o aplicativo Adobe Campaign inteiro. Para fazer isso, use o seguinte comando: **nlserver watchdog -svc -noconsole **
