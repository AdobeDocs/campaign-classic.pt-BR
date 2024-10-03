---
product: campaign
title: Matriz de compatibilidade do Campaign Classic
description: Matriz de compatibilidade do Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: 728848eab059fc669c241346a2ff1feebd79222c
workflow-type: ht
source-wordcount: '843'
ht-degree: 100%

---

# Matriz de compatibilidade {#compatibility-matrix}

A [build mais recente](../../rn/using/latest-release.md) do Adobe Campaign Classic v7 fornece compatibilidade com todos os sistemas e ferramentas listados nesta página. À medida que versões específicas desses sistemas e ferramentas de terceiros atingem o fim da vida útil (EOL) com seus respectivos criadores, o Adobe Campaign não será mais compatível com essas versões, e elas serão removidas de nossa matriz de compatibilidade na próxima versão do produto. Para evitar problemas, verifique se você está usando as versões compatíveis dos sistemas listadas na matriz de compatibilidade. Para saber mais sobre itens obsoletos, visite [esta página](../../rn/using/deprecated-features.md).

Salvo indicação em contrário, todas as versões secundárias são compatíveis.

>[!CAUTION]
>
>Esta matriz é atualizada periodicamente com a adição de novos sistemas e ferramentas compatíveis e a remoção de itens obsoletos.

## Sistemas operacionais {#OperatingSystems}

Como cliente local/híbrido, será necessário instalar o Adobe Campaign em um dos sistemas operacionais listados abaixo. Saiba mais sobre as etapas de instalação do Campaign Classic v7 [nesta página](../../installation/using/application-server.md).

<table> 
<tbody> 
<td><strong>Sistema operacional</strong></td>
<td><strong>Versão do sistema operacional</strong></td>
<td><strong>Versão mínima do Campaign</strong></td>
<tr> 
<td>CentOs</td>
<td>
<p>7.x</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>Red Hat Enterprise Linux (RHEL)</td>
<td>
<p>9.x</p>
<p>8.x</p>
<p>7.x</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4</p>
<p>v7.2</p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>Se estiver usando o RHEL, desabilite o [SELinux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#selinux) ou solicite à equipe de arquitetura que crie regras personalizadas para garantir que um SELinux habilitado não esteja causando problemas nas operações do Campaign.

## Servidores da Web {#WebServers}

Como cliente local/híbrido, dependendo do sistema operacional, será necessário integrar o Campaign a um dos servidores Web listados abaixo. Saiba mais sobre as etapas de configuração de servidores Web [nesta página](../../installation/using/integration-into-a-web-server-for-windows.md) (para Windows) e [nesta página](../../installation/using/integration-into-a-web-server-for-linux.md) (para Linux).

<table>
<tbody>
<td><strong>Servidor da web</strong></td>
<td><strong>Versão do servidor da web</strong></td>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10,0</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2,4</p>
</td>
</tr>
</tbody>
</table>

## Ferramentas {#Tools}

Como cliente local/híbrido, é necessário instalar e configurar as ferramentas listadas abaixo. [Saiba mais](../../installation/using/application-server.md).

<table>
<tbody>
<td><strong>Ferramenta</strong></td>
<td><strong>Versão</strong></td>
<td><strong>Versão mínima do Campaign</strong></td>
<tr>
<td><p>Java Development Kit (JDK)</p>
<p>Saiba mais <a href="../../installation/using/application-server.md#jdk" target="_blank">nesta página</a>.</p>
</td>
<td>
<p>11</p>
<p>9</p>
<p>8</p>
<p></p>
</td>
<td>
<p>obrigatório a partir da v7.4.1</p>
<p>até a v7.4.1</p>
<p>até a v7.4.1</p>
</tr>
<tr>
<td><p>Libre Office</p></td>
<td>
<p>7 (e versões anteriores, se incorporadas ao seu sistema)</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td><p>SpamAssassin</p></td>
<td>
<p>3.4.x</p>
</td>
<td>
<p></p>
</td>
</tbody>
</table>

## Sistema de gerenciamento de banco de dados relacional (RDBMS) {#RDBMSservers}

Como cliente local/híbrido, é necessário instalar e configurar um dos bancos de dados listados abaixo. [Saiba mais](../../installation/using/creating-and-configuring-the-database.md).


<table>
<tbody>
<td><strong>Sistema de banco de dados</strong></td>
<td><strong>Versão do banco de dados</strong></td>
<td><strong>Versão mínima do Campaign</strong></td>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>
<p>v7.3.2</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Microsoft SQL Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* O driver RDBMS deve corresponder à versão do servidor RDBMS.
>
>* O Microsoft SQL Server não é compatível como banco de dados principal quando o servidor do Campaign está em execução no Linux. [Saiba mais](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).
>
>* Também é possível usar o Amazon RDS para PostgreSQL com as versões especificadas acima.
>
>* PostgreSQL é o RDBMS para ambientes de serviços em nuvem hospedados/gerenciados.


## Conectores CRM {#CRMconnectors}

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
<td><strong>Versão mínima do Campaign</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>v7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>v7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>v7.0 19.1.4 </td>
</tr>
</tbody>
</table>

Além disso, os ambientes **Híbrido** e **No local** também podem conectar o Campaign aos seguintes sistemas de banco de dados externos: Esses sistemas são **incompatíveis** com ambientes (hospedados) do Campaign **Managed Services**.

<table>
<tbody>
<td><strong>Sistema de banco de dados</strong></td>
<td><strong>Versão do banco de dados</strong></td>
<td><strong>Versão mínima do Campaign</strong></td>
<tr>
<td>Análise do Microsoft Azure Synapse</td>
<td> </td>
<td></td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>v7.2</p>
</td>
<td></td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g  </p>
</td>
<td>
<p>v7.4</p>
<p></p>
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
<td></td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2022 (a partir do Campaign v7.4)</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 e SP2</p>
</td>
<td></td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td></td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (última versão)</p>
</td>
<td></td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td></td>
</tr>
</tbody>
</table>


## Console do cliente {#ClientOS}

Os sistemas operacionais e navegadores a seguir são **necessários** para usar o [Console do cliente do Campaign](../../installation/using/installing-the-client-console.md).

### Sistemas operacionais

<table>
<tbody>
<td><strong>Sistema</strong></td>
<td><strong>Versão do sistema operacional</strong></td>
<td><strong>Versão mínima do Campaign</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4.1</p>
<p>v7.2.1</p>
<p></p>
</tbody>
</table>

### Microsoft WebView2 Runtime {#webview}

A versão mais recente do WebView2 Runtime do Microsoft Edge é obrigatória para o console do cliente do Campaign.

Baixe o Microsoft Edge WebView2 no [Site do desenvolvedor Microsoft](https://www.adobe.com/go/acc-ms-webview2-runtime-download).


## SDK móvel {#MobileSDK}

É possível usar o Campaign para [enviar notificações por push](../../delivery/using/about-mobile-app-channel.md) por meio do SDK móvel da Adobe Experience Platform configurando a extensão do Adobe Campaign na interface da coleção de dados.

O SDK do Campaign foi [descontinuado](deprecated-features.md) a partir do Campaign v7.4. Para garantir uma transição descomplicada da implementação existente para o SDK móvel da AEP, ainda é possível usá-lo nos sistemas operacionais listados abaixo<!--, using the associated [mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)-->.


<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>7 - 14</p>
<p>com o SDK móvel build 1.1.1.</p>
<p>O Android 13 e 14 são compatíveis a partir do Campaign v7.4.</p>
<p>O Android 12 é compatível a partir do Campaign v7.3</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 – 17</p>
<p>com o SDK móvel build 1.0.26.</p>
<p>O Apple iOS 15 é compatível a partir do Campaign v7.3. </p>
<p>O Apple iOS 16 e 17 são compatíveis a partir do Campaign v7.4.</p>
</td>
</tr>
</tbody>
</table>

## Navegadores {#Browsers}

Os seguintes navegadores, em suas versões mais recentes, são compatíveis com o Campaign para [Acesso da web](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



>[!MORELIKETHIS]
>
>* [Notas de versão do Campaign Classic](../../rn/using/latest-release.md)
>* [Arquitetura geral do Campaign](../../installation/using/general-architecture.md)
>* [Recomendações de dimensionamento de hardware](../../technotes/using/hardware-sizing.md)
>* [Recursos e sistemas obsoletos](../../rn/using/deprecated-features.md)
>* [Criar procedimento de atualização](../../production/using/build-upgrade.md)
