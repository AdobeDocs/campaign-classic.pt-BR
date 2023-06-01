---
product: campaign
title: Localizar versão do Tomcat no Adobe Campaign
description: Saiba como descobrir a versão atual do servlet Web Tomcat incorporado usado em uma instância do Adobe Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Localizar versão do Tomcat{#locate-tomcat-version}



O Adobe Campaign usa um **servlet web incorporado chamado Apache Tomcat** para processar solicitações HTTP/HTTPS entre o aplicativo e qualquer interface externa (incluindo o Console do cliente, links de URL rastreados, chamadas SOAP e outros). Geralmente, há um servidor Web externo (geralmente o IIS ou Apache) na frente disso para qualquer instância do Adobe Campaign voltada para o exterior.

Siga o procedimento abaixo para descobrir a versão exata do Tomcat usada em uma **instância do Campaign Classic no local** para ajudar a solucionar problemas.

## Tomcat usado no Adobe Campaign

O Tomcat é executado no Java e requer que o JDK esteja instalado. Para obter mais informações, consulte Java Development Kit (JDK) no [Matriz de compatibilidade do Campaign](../../rn/using/compatibility-matrix.md) seção.

O Tomcat usado no Adobe Campaign é uma versão incorporada personalizada que não usa todos os recursos da versão completa e geralmente disponível do Tomcat, e pode não sofrer todas as vulnerabilidades da versão completa. O Tomcat também não deve ser exposto à Internet externa, e qualquer instância do Adobe Campaign que for exposta deve ter um servidor Web externo (IIS, Apache, etc.) na frente do Tomcat para protegê-lo.

As versões novas ou atualizadas das versões incorporadas do Tomcat são lançadas apenas com novas builds do próprio Adobe Campaign e não como patches separados fora das builds do Adobe Campaign.

## Como localizar a versão do Tomcat incorporado

Para localizar a versão do Tomcat incorporado em uma instância do Adobe Campaign, siga as etapas abaixo.

>[!NOTE]
>
>Você deve ter acesso aos arquivos no servidor do Adobe Campaign que precisam ser verificados. O procedimento descrito abaixo aplica-se apenas a **modelos de hospedagem no local**.

1. Navegue até a *\tomcat-7\lib* subpasta na pasta de instalação do Adobe Campaign (por exemplo, *Arquivos C:\Program\ [Pasta_instalação]* no Windows ou */usr/local/neolane/nl6* no Linux).

1. Copie o arquivo *catalina.jar* para uma pasta temporária externa (por exemplo, sua área de trabalho) e renomeie a extensão de .jar para .zip.

1. Descompacte o arquivo copiado. Ele resultará em muitas subpastas e arquivos.

1. Nos arquivos/pastas descompactados, abra ou leia o seguinte arquivo contido usando um editor de texto: *org/apache/catalina/util/ServerInfo.properties*. Talvez seja necessário adicionar uma extensão .txt para facilitar a abertura com um editor de texto.

1. Depois de concluído, se estiver em um computador servidor, exclua os arquivos temporários criados.

Como exemplo, a variável *ServerInfo.properties* arquivo para Adobe Campaign conterá as seguintes informações, indicando que o Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.build=MM DD YYY HH:MM:SS*

Depois de estabelecer a versão exata do Tomcat usada em uma instância específica, ela pode ajudá-lo a solucionar problemas relacionados ao Tomcat.

>[!NOTE]
>
>A versão principal do Tomcat incorporado só é atualizada quando a versão principal do Adobe Campaign é alterada (embora as versões mais antigas possam não ser mais oficialmente compatíveis, as informações podem ser úteis, pois alguns clientes ainda podem estar executando essas versões).

