---
product: campaign
title: Localizar a versão do Tomcat no Adobe Campaign
description: Saiba como descobrir a versão atual do servlet Web Tomcat incorporado usado em uma instância do Adobe Campaign.
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Localizar versão do Tomcat{#locate-tomcat-version}

![](../../assets/v7-only.svg)

O Adobe Campaign usa um **servlet da Web incorporado chamado Apache Tomcat** para processar solicitações HTTP/HTTPS entre o aplicativo e qualquer interface externa (incluindo Console do cliente, links de URL rastreados, chamadas SOAP e outras). Geralmente, há um servidor da Web externo (geralmente IIS ou Apache) na frente disso para qualquer instância do Adobe Campaign voltada para o exterior.

Siga o procedimento abaixo para descobrir a versão exata do Tomcat usada em uma **instância do Campaign Classic no local** para ajudar a solucionar problemas.

## Tomcat usado no Adobe Campaign

O Tomcat é executado no Java e requer que o JDK seja instalado. Para obter mais informações, consulte Java Development Kit (JDK) na seção [Matriz de compatibilidade de campanha](../../rn/using/compatibility-matrix.md) .

O Tomcat usado no Adobe Campaign é uma versão incorporada personalizada que não usa todos os recursos da versão completa geralmente disponível do Tomcat e pode não sofrer todas as vulnerabilidades da versão completa. O Tomcat também não deve ser exposto à Internet externa, e quaisquer instâncias do Adobe Campaign expostas devem ter um servidor da Web externo (IIS, Apache etc.) na frente do Tomcat para protegê-lo.

Versões novas ou atualizadas das versões incorporadas do Tomcat só são lançadas com novas builds do próprio Adobe Campaign e não como patches separados fora das builds do Adobe Campaign.

## Como localizar a versão do Tomcat incorporado

Para localizar a versão do Tomcat incorporado em uma instância do Adobe Campaign, siga as etapas abaixo.

>[!NOTE]
>
>Você deve ter acesso aos arquivos no servidor do Adobe Campaign que precisa verificar. O procedimento descrito abaixo se aplica somente a **modelos de hospedagem local**.

1. Navegue até a subpasta *\tomcat-7\lib* dentro da pasta de instalação do Adobe Campaign (por exemplo, *C:\Program Files\ [Installation_folder]* no Windows ou */usr/local/neolane/nl6* no Linux).

   Se você estiver executando uma versão mais antiga do Adobe Campaign usando o Tomcat v6, use *\tomcat-6\lib*.

1. Copie o arquivo *catalina.jar* para uma pasta temporária externa (por exemplo, sua área de trabalho) e renomeie a extensão de .jar para .zip.

1. Descompacte o arquivo copiado. Isso resultará em muitas subpastas e arquivos.

1. Em arquivos/pastas descompactados, abra ou leia o seguinte arquivo contido usando um editor de texto: *org/apache/catalina/util/ServerInfo.properties*. Talvez seja necessário adicionar uma extensão .txt para facilitar a abertura com um editor de texto.

1. Depois de concluído, se estiver em uma máquina de servidor, exclua os arquivos temporários criados.

Como exemplo, o arquivo *ServerInfo.properties* para Adobe Campaign conterá as seguintes informações, indicando Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.build=MM DD AAAA :MM:HSS*

Depois de estabelecer a versão exata do Tomcat usada em uma instância específica, ela poderá ajudá-lo a solucionar problemas relacionados ao Tomcat.

>[!NOTE]
>
>A versão principal do Tomcat incorporado só é atualizada quando a versão principal do Adobe Campaign é alterada (embora as versões mais antigas possam não ter mais suporte oficial, as informações podem ser úteis, pois alguns clientes ainda podem estar executando essas versões).
>
>Por exemplo, o Adobe Campaign v6.02 sempre usará o Tomcat v6.x.
