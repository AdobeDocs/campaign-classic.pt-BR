---
title: Recursos obsoletos e removidos do Campaign Classic
description: Esta página lista recursos obsoletos e removidos do Adobe Campaign Classic
page-status-flag: never-activated
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 48acf8cbc52a54a2dd08f0b8f29be57d4e5e006f
workflow-type: tm+mt
source-wordcount: '1621'
ht-degree: 99%

---


# Recursos descontinuados e removidos {#deprecated-and-removed-features}

A Adobe avalia constantemente os recursos do produto para identificar aqueles mais antigos que devem ser substituídos por alternativas mais modernas de forma a melhorar o valor geral do cliente, sempre considerando cuidadosamente a compatibilidade com versões anteriores. Como o Adobe Campaign Classic funciona com ferramentas de terceiros, a compatibilidade é atualizada regularmente, a fim de implementar somente as versões compatíveis. As versões que não são mais compatíveis com o Adobe Campaign Classic estão listadas abaixo e na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

Para comunicar a remoção/substituição iminente dos recursos do Campaign Classic, as seguintes regras se aplicam:

* O anúncio da descontinuação vem primeiro. Embora os recursos obsoletos ainda possam estar disponíveis e ter suporte para os usuários existentes, eles não serão aprimorados nem documentados.
* A remoção de recursos obsoletos ocorrerá na seguinte versão, o mais tardar. A data da remoção será anunciada nesta página.

Esse processo oferece aos clientes pelo menos um ciclo de lançamento para adaptar sua implementação a uma nova versão ou sucessor de um recurso obsoleto, antes da remoção.

>[!NOTE]
>As versões do Adobe Campaign e os novos recursos estão listados nas [Notas de versão](../../rn/using/latest-release.md).

## Recursos obsoletos {#deprecated-features}

Esta seção lista os recursos e funcionalidades marcados como obsoletos nas versões mais recentes do Campaign Classic.

Geralmente, os recursos que estão planejados para serem removidos em uma versão futura, primeiro são definidos como obsoletos. Esses recursos e funcionalidades não estão mais disponíveis para novos clientes do Campaign Classic ou não devem ser usados para novas implementações. Eles também foram removidos da documentação do produto.

Os clientes são aconselhados a verificar se utilizam o recurso/funcionalidade em sua implantação atual e a fazer planos para alterar sua implementação. Consulte a data de remoção para planejar suas atualizações de ambiente e projeto de acordo.

<table> 
 <tbody> 
   <tr>
   <td><strong>Recurso</strong></td>
   <td><strong>Substituição</strong></td>
  </tr>
  <tr>
  <td>Conectores CRM<br></td>
   <td><p>A partir da versão 20.3 do Campaign, os seguintes conectores CRM não serão mais utilizados:</p>
   <ul>
   <li>API Soap - no local: 2007, 2015, 2016</li>
   <li>API Soap - online: 2015, 2016</li>
   <li>API da Web - Microsoft Dynamics CRM On-premise: Atualização 1 de 2016, 2016</li>
   <li>API da Web - Microsoft Dynamics CRM Online: Atualização 1 de 2016, 2016</li>
   </ul>
  <p><em>Data de remoção do Target: 2021</em></p>
  </td>
 </tr>
  <tr>
  <td>Binário herdado do iOS<br></td>
  <td><p>A partir da versão 20.3 do Campaign, o conector binário herdado do iOS se tornará obsoleto.<p>
  <p> Se estiver usando este conector, precisará adaptar sua implementação adequadamente.
  <a href="https://helpx.adobe.com/br/campaign/kb/migrate-to-http2.html">Saiba mais</a></p>
  <p><em>Data de remoção do Target: 2021</em></p>
  </td>
 </tr>
   <tr>
  <td>Domínio demdex<br></td>
  <td><p> A partir da versão 20.3 do Campaign, o domínio demdex usado para importar e exportar públicos para a Adobe Experience Cloud se tornará obsoleto.<p>
  <p>Se você estiver usando o domínio demdex para suas contas externas de importação/exportação, será necessário adaptar sua implementação de forma apropriada. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Saiba mais</a></p> 
  <p><em>Data de remoção do Target: 2021</em></p>
  </td>
  <tr>
  <td>Autenticação OAuth (OAuth e JWT)<br></td>
  <td><p> A partir da versão 20.3 do Campaign, a autenticação de integração de acionadores originalmente com base na configuração de autenticação oAUTH para acesso ao pipeline agora foi alterada e movida para o Adobe I/O. <p>
  <p>Se você estiver usando acionadores de integração, precisará adaptar sua implementação adequadamente. <a href="../../integrations/using/configuring-adobe-io.md">Saiba mais</a></p> 
  <p>Para obter mais informações sobre a depreciação da Autenticação OAuth, consulte esta <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">página</a></p> 
  <p><em>Data de remoção do Target: abril de 2021</em></p>
  </td>
  </tr>
  <td>Conector SMS<br></td>
  <td><p> A partir da versão 20.2 do Campaign, os seguintes conectores SMS não serão mais utilizados.<p>
   <ul>
   <li>NetSize</li>
   <li>SMPP genérico (SMPP versão 3.4 com suporte para modo binário)</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>CLX Communications</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>Se estiver usando um desses conectores, precisará adaptar sua implementação adequadamente. <a href="../../delivery/using/sms-channel.md">Saiba mais</a></p> 
  <p>Saiba como migrar conectores herdados <a href="https://helpx.adobe.com/br/campaign/kb/sms-connector.html">nesta nota técnica</a>.</p>
  <p><em>Data de remoção do Target: 2021</em></p>
  </td> 
 </tr>
  <tr>  
   <td>Canal de fax<br></td>
   <td><p>A partir da versão 20.2 do Campaign, o canal de fax não será mais utilizado.</p> 
   <p>Se estiver usando esse canal, precisará adaptar sua implementação adequadamente. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Saiba mais</a> sobre Canais do Campaign.</p>
   <p><em>Data de remoção do Target: 2021</em></p></td>
  </tr>
 </tbody> 
</table>

## Recursos removidos {#removed-features}

Esta seção lista os recursos e funcionalidades removidos do Campaign Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Área - Recurso</strong></td>
   <td><strong>Substituição</strong></td> 
  </tr> 
   <tr> 
   <td>Autenticação do Windows NT<br></td>
   <td><p>A partir da versão 20.3 do Campaign, a autenticação do Windows NT foi removida dos métodos de autenticação disponíveis ao configurar um novo banco de dados com um Microsoft SQL Server. <a href="../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine">Saiba mais</a></p></td>
  </tr>
   <tr> 
   <td>Arquivamento de email baseado em arquivo<br></td>
   <td><p>A partir da versão 20.2 do Campaign, o arquivamento de emails baseado em arquivos não estará mais disponível. O arquivamento de emails agora está disponível por meio de um endereço de email CCO dedicado. <a href="../../installation/using/email-archiving.md">Saiba mais</a></p></td>
  </tr> 
   <tr> 
   <td>Gerenciamento de clientes potenciais</td>
   <td><p>A partir da versão 20.2 do Campaign, o pacote de Gerenciamento de clientes potenciais não estará mais disponível. Uma funcionalidade semelhante pode ser implementada por meio de outras atividades de fluxo de trabalho nativas e modificações no modelo de dados.</p></td>
   </tr>
   <tr>
   <td>Documentação das APIs do Campaign – arquivo jsapi.ch</td>
   <td>A partir da versão 19.1 do Campaign, as APIs do Campaign Classic estarão disponíveis em uma página dedicada. Se estiver usando o arquivo jsapi.chm legado, agora deverá consultar a <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">nova versão online</a>.</td>
  </tr> 
  <tr> 
   <td>Orquestração de campanha        - Marketing preditivo</td>
   <td>A partir da versão 18.10 do Campaign, os recursos de marketing preditivo não estarão mais disponíveis.</td>
  </tr> 
  <tr> 
   <td>Aplicação da Web - Microsites</td>
   <td>A partir da versão 18.10 do Campaign, os Microsites não estarão mais disponíveis. Você pode melhorar a segurança restringindo o acesso a domínios dedicados somente em arquivos de configuração do Adobe Campaign e usar URLs personalizados no Campaign usando aliases DNS. <a href="https://helpx.adobe.com/br/campaign/kb/domain-name-delegation.html">Saiba mais</a></td>
  </tr> 
  <tr> 
   <td>Notificações por push - Conector binário iOS</td>
   <td>De acordo com a recomendação da Apple, a Adobe removeu o Conector Binário do iOS herdado, iniciando na versão 18.10 do Campaign. O conector baseado em HTTP/2, mais avançado e eficiente, já está disponível.</td>
  </tr> 
  <tr> 
   <td>API decryptString</td>
   <td><p>Começando pela versão 18.6 do Campaign, por motivos de segurança, a API <em>decryptString</em> não estará mais disponível por padrão nas novas instalações.</p> 
   <p>No contexto de uma pós-atualização para 18.6 (e posterior), essa API não é mais ativada e foi substituída pela função <em>decryptPassword. </em> <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">Saiba mais</a></p></td>
  </tr> 
   <tr> 
   <td>Canal móvel - Mensagens de push MMS e WAP</td>
   <td>A partir da versão 18.4 do Campaign, os canais MMS e Wap Push não estarão mais disponíveis. Como substituição, você pode usar os deliveries de <a href="../../delivery/using/sms-channel.md">SMS</a> e <a href="../../delivery/using/about-mobile-app-channel.md">Push</a>.</td>
  </tr> 
   <tr> 
   <td>Canal móvel - LINE v1</td>
   <td>A partir da versão 18.4 do Campaign, o pacote do LINE Connect não estará mais disponível. A Adobe recomenda usar o novo pacote do Canal LINE como substituição. <a href="../../delivery/using/line-channel.md">Saiba mais</a></td>
  </tr> 
 </tbody> 
</table>

## Compatibilidade obsoleta {#deprecated-compatibility}

Os seguintes sistemas foram descontinuados para o Campaign Classic. Consulte a [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md) para atualizar para uma versão mais recente ou mover para um novo sistema antes do fim da compatibilidade.

### Versão 20.2 do Adobe Campaign {#compat-20-2-release}

A partir da versão 20.2, os conectores SMS herdados ficarão obsoletos. Consulte a [seção recursos obsoletos](#deprecated-features)

## Fim da compatibilidade do {#end-of-compatibility}

>[!CAUTION]
>
>O Adobe Campaign Classic é compatível com todos os sistemas e ferramentas listados na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md). Quando versões específicas desses sistemas e ferramentas de terceiros atingem o fim da vida útil (EOL) com seus respectivos criadores, o Adobe Campaign não é mais compatível com essas versões: elas são anunciadas como obsoletas e, em seguida, são removidas de nossa matriz de compatibilidade na versão subsequente do produto. Verifique se você está usando as versões compatíveis dos sistemas listadas na matriz de compatibilidade para evitar problemas.

### Console do cliente {#client-console-eol}

O Console do cliente do Adobe Campaign Classic não pode mais ser executado nos seguintes sistemas, pois foram descontinuados pelo editor. Os clientes que executam o Console do cliente do Campaign em uma dessas versões precisam atualizar para a versão mais recente antes da data de remoção. Consulte a [Matriz de Compatibilidade](../../rn/using/compatibility-matrix.md).

* Windows Server 2003, 2008, 2008 R2
* Windows 7, XP e Vista

>[!NOTE]
>A partir da versão 20.1 do Campaign, o Console do Cliente do Campaign Classic de 32 bits não será mais compatível com as versões mais recentes do Campaign. Você precisa usar o Console do Cliente de 64 bits.


### Sistemas operacionais {#o-s-eol}

A partir da versão 19.1, o Adobe Campaign não é mais compatível com os seguintes sistemas operacionais.

* CentOS 6 [Saiba mais](https://wiki.centos.org/Download)
* Debian 7. [Saiba mais](https://wiki.debian.org/DebianReleases)
* RHEL 6.x. [Saiba mais](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008. [Saiba mais](https://support.microsoft.com/pt-br/lifecycle/search/1163)
* SLES 11. [Saiba mais](https://www.suse.com/lifecycle)

### Servidores da Web {#web-server-eol}

A partir da versão do primeiro trimestre 19.1, o Adobe Campaign não é mais compatível com o seguinte servidor da Web.

* Apache 2.2. [Saiba mais](https://httpd.apache.org/)
* Microsoft IIS 7. [Saiba mais](https://support.microsoft.com/pt-br/lifecycle/search/810)

### Ferramentas {#tools-eol}

A partir da versão do primeiro trimestre 19.1, o Adobe Campaign não é mais compatível com as seguintes ferramentas.

* Java JDK 7. [Saiba mais](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5/4.3/5.x, exceto quando incorporado em outra ferramenta. [Saiba mais](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Mecanismos de banco de dados {#dbe-eol}

A Adobe não oferece suporte aos seguintes mecanismos de banco de dados, pois foram descontinuados pelo editor. Os clientes que executam essas versões precisam atualizar para a versão mais recente ou mudar para outra.

Consulte a [Matriz de compatibilidade do Campaign ](../../rn/using/compatibility-matrix.md) para acessar a lista de versões compatíveis.

**FEDERATED DATA ACCESS (FDA)** 

A partir da versão 20.2, o Adobe Campaign não é mais compatível com o seguinte servidor FDA:

* DB2 UDB 10.5

A partir da versão do primeiro trimestre 19.1, o Adobe Campaign não é mais compatível com os seguintes servidores FDA:

* PostgreSQL 9.3. [Saiba mais](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [Saiba mais](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [Saiba mais](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 - 14.1. [Saiba mais](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

O Campaign Classic não é compatível com os seguintes servidores no FDA (Federated Data Access — Acesso Federado a Dados).

* DB2 UDB 9.5, 9.7. A versão mais recente do DB2 é compatível com o Federated Data Access (FDA). [Saiba mais](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i, 10G R2. Versões mais recentes do Oracle são compatíveis com o FDA (Federated Data Access — Acesso Federado a Dados). [Saiba mais](http://www.oracle.com/br/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Versões mais recentes do PostgreSQL são compatíveis com o Federated Data Access (FDA). [Saiba mais](https://www.postgresql.org/support/versioning)
* MSSQL 2000, 2005, 2008 R2. As versões mais recentes do SQL Server são compatíveis com o FDA (Federated Data Access — Acesso a Dados Federados). [Saiba mais](https://support.microsoft.com/pt-br/lifecycle/search/1044)
* MySQL 5.1. Versões mais recentes do MySQL são compatíveis com o Federated Data Access (FDA). [Saiba mais](https://pt.wikipedia.org/wiki/InfiniDB)
* O InfiniDB chegou ao fim da vida útil. [Saiba mais](https://www.mysql.com/support)
* Teradata 13, 13.1. As versões mais recentes do Teradata são compatíveis com o Federated Data Access (FDA). [Saiba mais](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02, 7.0. O Netezza chegou ao fim da vida útil. [Saiba mais](https://pt.wikipedia.org/wiki/Netezza)
* AsterData 5.0. O AsterData chegou ao fim da vida útil. [Saiba mais](https://pt.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2, 15.4, 15.5 e Sybase ASE 15.0. Versões mais recentes do Sybase são compatíveis com o Federated Data Access (FDA). [Saiba mais](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. O Adobe Campaign Classic ainda oferecerá suporte às versões listadas do Hadoop via HiveSQL por meio do Federated Data Acces (FDA), mas essas versões são mescladas com: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) e HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS SERVER**

O Adobe Campaign não é compatível com os seguintes servidores RDBMS:
* Oracle 10GR2
* PostgreSQL 9.0 a 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
