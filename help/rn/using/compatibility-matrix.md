---
solution: Campaign Classic
product: campaign
title: Matriz de compatibilidade
description: Matriz de compatibilidade do Campaign Classic
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: ff3d18b104a8dba7cd813aa698f9c27b4e25e244
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 85%

---


# Matriz de compatibilidade{#compatibility-matrix}

This document lists all systems and components supported for [the latest build](../../rn/using/latest-release.md) of **Adobe Campaign Classic**. Os produtos e as versões que não estão nessa lista não são compatíveis com o Adobe Campaign.

Se você for um usuário Gold Standard, consulte a matriz [Gold Standard Compatibility](../../rn/using/compatibility-matrix-gs.md).

## Observações importantes{#important-notes}

Salvo indicação em contrário, todas as versões secundárias são compatíveis.

In its [latest build](../../rn/using/latest-release.md), Adobe Campaign Classic is compatible with all the systems and tools listed in this page. À medida que versões específicas desses sistemas e ferramentas de terceiros atingem o fim da vida útil (EOL) com seus respectivos criadores, o Adobe Campaign não será mais compatível com essas versões, e elas serão removidas de nossa matriz de compatibilidade na versão subsequente do produto. Verifique se você está usando as versões compatíveis dos sistemas listadas na matriz de compatibilidade para evitar problemas.

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
<p>8.x (64 bits)</p>
<p>7.x (64 bits)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>10 (64 bits)</p>
<p>9 (64 bits)</p>
<p>8 (64 bits)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x (64 bits)</p>
<p>7.x (64 bits)</p>
<p><strong>Importante:</strong> se você estiver usando o RHEL, deve desativar o SELinux ou fazer com que seus arquitetos gravem regras personalizadas de SELinux para verificar se um SELinux habilitado não está causando problemas nas operações do Campaign.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

## Servidores da Web{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 no Windows Server 2016</p>
<p>8.5 no Windows Server 2012 R2</p>
<p>8.0 no Windows Server 2012 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 para RHEL7 - CentOS 7, Debian 8/9, Windows (64 bits)</p>
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
<p>O aplicativo foi aprovado para o Java Development Kit (JDK) desenvolvido pela Oracle e para OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6 (e versões anteriores, se incorporadas ao seu sistema)</p>
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

## Servidores RDBMS{#RDBMSservers}

>[!NOTE]
>
>O driver RDBMS deve corresponder à versão do servidor RDBMS.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g     R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>Observação: você também pode usar o Amazon RDS para PostgreSQL com as versões especificadas acima.</p>
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
<p>Aviso: o Microsoft SQL Server não é compatível como o banco de dados principal quando o servidor do Campaign estiver em execução no Linux. <a href="https://docs.adobe.com/content/help/pt-BR/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">Saiba mais</a>.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>O PostgreSQL é o servidor de banco de dados padrão para ambientes hospedados.

## Conectores CRM{#CRMconnectors}

<table>
<tbody>
<tr>
<td>API do conector Salesforce</td>
<td>
<p>API versão 37</p>
</td>
</tr>
<tr>
<td>API SFDC</td>
<td>
<p>API versão 21</p>
<p>API versão 15</p>
</td>
</tr>
<tr><td>API Oracle On Demand</td>
<td>
<p>API de serviços da Web v1.0</p>
</td>
</tr>
<tr>
<td>MS Dynamics</td>
<td>
<p>API da Web: Dynamics 365 On-premise e Online</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

<table>
<tbody>
<tr>
<td>Análise do Microsoft Azure Synapse</td>
<td> </td>
</tr>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g    </p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 e SP2</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>versão 1 SPS 12</p>
</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
</tr>
</tbody>
</table>

## Sistemas operacionais do console do cliente{#ClientConsoleoperatingsystems}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>8</p>
<p>10 (recomendado para instâncias em japonês)</p>
</td>
</tr>
</tbody>
</table>

## Mobile SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x, 8.x, 9.0</p>
<p>com o SDK móvel build 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 14</p>
<p>com o SDK móvel build 1.0.26, compatível com as versões de 32 e 64 bits.</p>
</td>
</tr>
</tbody>
</table>

## Navegadores{#Browsers}

Para os seguintes navegadores, a versão mais recente é suportada: Microsoft Edge, Mozilla Firefox, Google Chrome, Safari.

O Internet Explorer 11 é compatível.

## Veja mais aqui{#Morelikethis}

* [Notas de versão do Campaign Classic](../../rn/using/latest-release.md)
* [Guia de instalação](../../installation/using/general-architecture.md)
* [Recursos e sistemas obsoletos](../../rn/using/deprecated-features.md)
* [Criar procedimento de atualização](../../production/using/build-upgrade.md)
