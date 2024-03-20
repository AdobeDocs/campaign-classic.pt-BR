---
product: campaign
title: Matriz de compatibilidade do Campaign Classic
description: Matriz de compatibilidade do Campaign Classic
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: 3e771d9a18c083bee8239b95d1d68d63928217c2
workflow-type: ht
source-wordcount: '764'
ht-degree: 100%

---

# Matriz de compatibilidade{#compatibility-matrix}



Este documento lista todos os sistemas e componentes compatíveis com [a última compilação](../../rn/using/latest-release.md) do **Adobe Campaign Classic v7**. Os produtos e as versões que não estão nessa lista não são compatíveis com o Adobe Campaign.

Se você for um usuário do [!DNL Gold Standard], consulte a Matriz de compatibilidade do [[!DNL Gold Standard] ](../../rn/using/gold-standard.md#compatibility-matrix-gs).

## Observações importantes{#important-notes}

Salvo indicação em contrário, todas as versões secundárias são compatíveis.

A [última build](../../rn/using/latest-release.md) do Adobe Campaign Classic é compatível com todos os sistemas e ferramentas listados nesta página. À medida que versões específicas desses sistemas e ferramentas de terceiros atingem o fim da vida útil (EOL) com seus respectivos criadores, o Adobe Campaign não será mais compatível com essas versões, e elas serão removidas de nossa matriz de compatibilidade na versão subsequente do produto. Verifique se você está usando as versões compatíveis dos sistemas listadas na matriz de compatibilidade para evitar problemas.

Para saber mais sobre itens obsoletos, visite [esta página](../../rn/using/deprecated-features.md).

>[!CAUTION]
>
>Essa matriz é atualizada regularmente, onde novos itens compatíveis são adicionados e itens obsoletos são removidos.

## Sistemas operacionais{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>7.x</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11 (a partir do Campaign v7.3)</p>
<p>10</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x</p>
<p>7.x</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2019 (a partir do Campaign v7.2)</p>
<p>2016</p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>Se estiver usando o RHEL, desabilite o SELinux ou peça para seus arquitetos criarem regras personalizadas de SELinux para verificar se um SELinux habilitado não está causando problemas nas operações do Campaign.

## Servidores da Web{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 no Windows Server 2016 e 2019</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 para RHEL7 - CentOS 7, Debian 8/9, Windows</p>
</td>
</tr>
</tbody>
</table>

## Ferramentas{#Tools}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>11</p>
<p>9</p>
<p>8</p>
<p>O Campaign é compatível com o Java Development Kit (JDK) desenvolvido pela Oracle e com o OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>7 (e versões anteriores, se incorporadas ao seu sistema)</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

## Sistema de gerenciamento de banco de dados relacional (RDBMS){#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x (a partir do Campaign v7.3.2)</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p><strong>Observação:</strong> você também pode usar o Amazon RDS para PostgreSQL com as versões especificadas acima.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1 e SP2</p>
<p><strong>Importante:</strong> o Microsoft SQL Server não é compatível como banco de dados principal quando o servidor do Campaign está em execução no Linux. <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/installing-campaign-in-linux/prerequisites-of-campaign-installation-in-linux.html?lang=pt-BR#database-access-layers">Saiba mais</a>.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* O driver RDBMS deve corresponder à versão do servidor RDBMS.
>
>* O PostgreSQL é o RDBMS para ambientes hospedados.

## Conectores CRM{#CRMconnectors}

Os sistemas de gerenciamento de relacionamento com o cliente (CRM) compatíveis com o Adobe Campaign estão listados abaixo. [Saiba mais](../../platform/using/crm-connectors.md) sobre conectores CRM do Campaign.

<table>
<tbody>
<tr>
<td>API do conector Salesforce</td>
<td>
<p>API versão 49</p>
</td>
</tr>
<tr>
<td>Conector do Microsoft Dynamics</td>
<td>
<p>API da Web</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

Os bancos de dados externos compatíveis com o [módulo Federated Data Access](../../installation/using/about-fda.md) do Adobe Campaign estão listados abaixo. A compatibilidade depende do seu [modelo de hospedagem](../../installation/using/hosting-models.md).

Os ambientes **Managed Services** (hospedado), **Híbrido** e **No local** podem conectar o Campaign aos seguintes sistemas de banco de dados externos:

<table>
<tbody>
<td><strong>Sistema de banco de dados</strong></td>
<td><strong>Versão do banco de dados</strong></td>
<td><strong>Versão do Campaign</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>No mínimo v7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>No mínimo 7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>No mínimo v7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>No mínimo 7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>No mínimo v7.0 19.1.4</td>
</tr>
</tbody>
</table>

Além disso, os ambientes **Híbrido** e **No local** também podem conectar o Campaign aos seguintes sistemas de banco de dados externos: Esses sistemas são **incompatíveis** com ambientes (hospedados) do Campaign **Managed Services**.

<table>
<tbody>
<td><strong>Sistema de banco de dados</strong></td>
<td><strong>Versão do banco de dados</strong></td>
<td><strong>Versão do Campaign</strong></td>
<tr>
<td>Análise do Microsoft Azure Synapse</td>
<td> </td>
<td>No mínimo v7.0 19.1.4</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>No mínimo v7.3 </p>
<p>No mínimo v7.0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
<td>No mínimo v7.0</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g  </p>
</td>
<td>
<p>No mínimo v7.0</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>versão 1 SPS 12</p>
</td>
<td>No mínimo v7.0</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 e SP2</p>
</td>
<td>No mínimo v7.0</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td>No mínimo v7.0</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (última versão)</p>
</td>
<td>No mínimo v7.0</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td>No mínimo v7.0</td>
</tr>
</tbody>
</table>



## Console do cliente {#ClientConsoleoperatingsystems}

Os sistemas operacionais e navegadores a seguir são **necessários** para usar o [Console do cliente do Campaign](../../installation/using/installing-the-client-console.md).

### Sistemas operacionais

<table>
<tbody>
<td><strong>Sistema</strong></td>
<td><strong>Versão do sistema operacional</strong></td>
<td><strong>Versão do Campaign</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>No mínimo v7.3 </p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>No mínimo v7.2.1 </p>
<p></p>
<p></p>
</tbody>
</table>

### Microsoft WebView2 Runtime

A versão mais recente do WebView2 Runtime do Microsoft Edge é obrigatória para o console do cliente do Campaign.

Baixe o Microsoft Edge WebView2 no [Site do desenvolvedor Microsoft](https://www.adobe.com/go/acc-ms-webview2-runtime-download).


## SDK móvel{#MobileSDK}

Você pode usar o Campaign para [enviar notificações por push](../../delivery/using/about-mobile-app-channel.md) nos sistemas operacionais listados abaixo, usando o [SDK móvel](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md) associado.

Você também pode usar o SDK móvel da Adobe Experience Platform configurando a extensão do Adobe Campaign na interface da coleção de dados.

<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>12 (a partir do Campaign v7.3), 9.0, 8.x, 7.x</p>
<p>com o SDK móvel build 1.1.1</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 – 15</p>
<p>com o SDK móvel build 1.0.26, compatível com as versões de 32 e 64 bits. O iOS 15 é compatível a partir do Campaign v7.3</p>
</td>
</tr>
</tbody>
</table>

## Navegadores{#Browsers}

Os seguintes navegadores, em suas versões mais recentes, são compatíveis com o Campaign para [Acesso da web](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



## Mais itens semelhantes{#Morelikethis}

* [Notas de versão do Campaign Classic](../../rn/using/latest-release.md)
* [Arquitetura geral do Campaign](../../installation/using/general-architecture.md)
* [Recomendações para dimensionamento de hardware](../../technotes/using/hardware-sizing.md)
* [Recursos e sistemas obsoletos](../../rn/using/deprecated-features.md)
* [Criar procedimento de atualização](../../production/using/build-upgrade.md)
