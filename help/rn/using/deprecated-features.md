---
title: Recursos obsoletos e removidos do Campaign Classic
description: Esta página lista recursos obsoletos e removidos do Adobe Campaign Classic
page-status-flag: never-activated
uuid: null
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e46325ab8f68a0b71198aee9cf04f2b1eb97fdd3
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 67%

---


# Recursos descontinuados e removidos {#deprecated-and-removed-features}

A Adobe avalia constantemente os recursos do produto para identificar aqueles mais antigos que devem ser substituídos por alternativas mais modernas de forma a melhorar o valor geral do cliente, sempre considerando cuidadosamente a compatibilidade com versões anteriores. Como o Adobe Campaign Classic funciona com ferramentas de terceiros, a compatibilidade é atualizada regularmente, a fim de implementar somente as versões compatíveis. As versões que não são mais compatíveis com o Adobe Campaign Classic estão listadas abaixo e na matriz [Compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html).

Para comunicar a remoção/substituição iminente dos recursos do Campaign Classic, as seguintes regras se aplicam:

* O anúncio da descontinuação vem primeiro. Embora os recursos obsoletos ainda possam estar disponíveis e sejam compatíveis com os usuários existentes, eles não serão aprimorados nem documentados.
* A remoção de recursos obsoletos ocorrerá na seguinte versão, o mais tardar. A data da remoção será anunciada nesta página.

Esse processo oferece aos clientes pelo menos um ciclo de lançamento para adaptar sua implementação a uma nova versão ou sucessor de um recurso obsoleto, antes da remoção.

>[!NOTE]
>As versões do Adobe Campaign e os novos recursos estão listados nas [Notas de versão](../../rn/using/latest-release.md).

## Recursos obsoletos {#deprecated-features}

Esta seção lista os recursos e funcionalidades marcados como obsoletos nas versões mais recentes do Campaign Classic.

Geralmente, os recursos que estão planejados para serem removidos em uma versão futura são definidos como obsoletos primeiro. Esses recursos e recursos não estão mais disponíveis para novos clientes do Campaign Classic ou não devem ser usados para nenhuma nova implementação. Eles também foram removidos da documentação do produto.

Recomenda-se que os clientes examinem se utilizam o recurso/recurso em sua implantação atual e façam planos para alterar sua implementação. Consulte a data de remoção para planejar suas atualizações de ambiente e projeto de acordo.

<table> 
 <tbody> 
   <tr>
   <td><strong>Recurso</strong></td>
   <td><strong>Substituição</strong></td> 
  </tr>
   <tr>
  <td>Conectores SMS<br></td>
  <td><p> A partir da versão 20.2, os seguintes conectores SMS serão descontinuados.<p>
   <ul>
   <li>NetSize</li>
   <li>SMPP genérico (SMPP versão 3.4 com suporte para modo binário)</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>Comunicações CLX</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>Se você estiver usando um desses conectores, precisará adaptar sua implementação de acordo. <a href="../../delivery/using/sms-channel.md">Saiba mais</a></p> 
  <p>Saiba como migrar conectores herdados <a href="https://helpx.adobe.com/campaign/kb/sms-connector.html">nesta nota técnica</a>.</p>
  <p><em>Data de remoção do Público alvo: 2021</em></p>
  </td> 
 </tr>
  <tr>  
   <td>canal de fax<br></td>
   <td><p>A partir da versão 20.2, o canal de fax está obsoleto.</p> 
   <p>Se você estiver usando esse canal, precisará adaptar sua implementação de acordo. <a href="../../delivery/using/communication-channels.md">Saiba mais</a> sobre canais Campanhas.</p>
   <p><em>Data de remoção do Público alvo: 2021</em></p></td>
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
   <td>Arquivamento de e-mail baseado em arquivo<br></td>
   <td><p>A partir da versão 20.2 da Campanha, o arquivamento de e-mails baseado em arquivos não estará mais disponível. O arquivamento de emails agora está disponível por meio de um endereço de email CCO dedicado. <a href="../../installation/using/email-archiving.md">Saiba mais</a></p></td>
  </tr> 
   <tr> 
   <td>Gerenciamento de clientes potenciais</td>
   <td><p>A partir da versão de Campanha 20.2, o pacote de gerenciamento de clientes potenciais não estará mais disponível. Uma funcionalidade semelhante pode ser implementada por meio de outras atividades de fluxo de trabalho nativas e modificações no modelo de dados.</p></td>
   </tr>
   <tr>
   <td>Documentação das APIs de Campanha - arquivo jsapi.chm</td>
   <td>A partir da versão 19.1 da Campanha, as APIs da Campaign Classic estão disponíveis em uma página dedicada. If you were using the legacy jsapi.chm file, you should now refer to <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">the new online version</a>.</td>
  </tr> 
  <tr> 
   <td>Orquestração de campanha  - Marketing preditivo</td>
   <td>A partir da versão 18.10 da Campanha, os recursos de marketing preditivo não estarão mais disponíveis.</td>
  </tr> 
  <tr> 
   <td>Aplicação da Web - Microsites</td>
   <td>A partir da versão 18.10 da Campanha, os Microsites não estarão mais disponíveis. Você pode melhorar a segurança restringindo o acesso a domínios dedicados somente em arquivos de configuração de Adobe Campaign e usar URLs personalizados na Campanha usando aliases DNS. <a href="https://helpx.adobe.com/br/campaign/kb/domain-name-delegation.html">Saiba mais</a></td>
  </tr> 
  <tr> 
   <td>Notificações por push - Conector binário iOS</td>
   <td>De acordo com a recomendação da Apple, a Adobe removeu o iOS Binary Connector herdado, iniciando a versão 18.10 da Campanha. O conector baseado em HTTP/2, mais avançado e eficiente, já está disponível.</td>
  </tr> 
  <tr> 
   <td>API descriptografptString</td>
   <td><p>Starting Campaign 18.6 release, for security reasons, <em>decryptString</em> API is no longer available by default for new installations.</p> 
   <p>No contexto de uma pós-atualização para 18.6 (e posterior), essa API não é mais ativada e foi substituída pela função <em>decryptPassword. </em> <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">Saiba mais</a></p></td>
  </tr> 
   <tr> 
   <td>Canal móvel - Mensagens de push MMS e WAP</td>
   <td>A partir da Campanha 18.4, os canais MMS e Wap Push não estarão mais disponíveis. Como substituição, você pode usar os deliveries de <a href="../../delivery/using/sms-channel.md">SMS</a> e <a href="../../delivery/using/about-mobile-app-channel.md">Push</a>.</td>
  </tr> 
   <tr> 
   <td>Canal móvel - LINE v1</td>
   <td>A partir da Campanha 18.4, o pacote do LINE Connect não estará mais disponível. A Adobe recomenda usar o novo pacote de Canal LINE como substituição. <a href="../../delivery/using/line-channel.md">Saiba mais</a></td>
  </tr> 
 </tbody> 
</table>

## Compatibilidade obsoleta {#deprecated-compatibility}

Os seguintes sistemas estão obsoletos para o Campaign Classic. Please refer to the [Compatibility matrix](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html) to upgrade to a newer version or move to a new system before the compatibility ends.

### Versão 20.2 do Adobe Campaign {#compat-20-2-release}

A partir da versão 20.2, o sistema a seguir está obsoleto para o Campaign Classic. A compatibilidade terminará na versão 20.3 - setembro de 2020.

* Console do cliente: Windows 7
* Conectores SMS herdados (consulte a seção Recursos obsoletos abaixo)

### Versão 19.2 do Adobe Campaign  {#compat-19-2-release}

A partir da versão 19.2, os seguintes sistemas operacionais serão descontinuados para o Campaign Classic. A compatibilidade terminará ao final do ano de 2020.

* Servidor Web: Apache 2.2.
* Sistema operacional: CentOS 6.

Consulte a [Matriz de compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html) para atualizar para uma versão mais recente ou para um novo sistema.

## Fim da compatibilidade do {#end-of-compatibility}

>[!CAUTION]
>
>O Adobe Campaign Classic é compatível com todos os sistemas e ferramentas listados na [Matriz de compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html). Quando versões específicas desses sistemas e ferramentas de terceiros atingem o fim da vida útil (EOL) com seus respectivos criadores, o Adobe Campaign não é mais compatível com essas versões: elas são anunciadas como obsoletas e, em seguida, são removidas de nossa matriz de compatibilidade na versão subsequente do produto. Certifique-se de que você está usando as versões compatíveis de qualquer sistema listado na matriz de compatibilidade para evitar problemas.

### Console do cliente {#client-console-eol}

O Console do cliente do Adobe Campaign Classic não pode mais ser executado nos seguintes sistemas, pois foram descontinuados pelo editor. Os clientes que executam o Console do cliente do Campaign em uma dessas versões precisam atualizar para a versão mais recente antes da data de remoção. Consulte a [Matriz de Compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

>[!NOTE]
>A partir da versão Campaign 20.1, o Campaign Classic Client Console 32 bits não é mais compatível com as versões mais recentes da Campanha. Você precisa usar o console do cliente de 64 bits.


### Sistemas operacionais {#o-s-eol}

A partir da versão 19.1, o Adobe Campaign não é mais compatível com os seguintes sistemas operacionais.

* Debian 7. [Saiba mais](https://wiki.debian.org/DebianReleases)
* RHEL 6.x. [Saiba mais](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008. [Saiba mais](https://support.microsoft.com/pt-br/lifecycle/search/1163)
* SLES 11. [Saiba mais](https://www.suse.com/lifecycle)

### Servidores da Web {#web-server-eol}

A partir da versão do primeiro trimestre 19.1, o Adobe Campaign não é mais compatível com o seguinte servidor da Web.

* Microsoft IIS 7. [Saiba mais](https://support.microsoft.com/pt-br/lifecycle/search/810)

### Ferramentas {#tools-eol}

A partir da versão do primeiro trimestre 19.1, o Adobe Campaign não é mais compatível com as seguintes ferramentas.

* Java JDK 7. [Saiba mais](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5/4.3/5.x, exceto quando incorporado em outra ferramenta. [Saiba mais](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Mecanismos de banco de dados {#dbe-eol}

A Adobe não oferece suporte aos seguintes mecanismos de banco de dados, pois foram descontinuados pelo editor. Os clientes que executam essas versões precisam atualizar para a versão mais recente ou mudar para outra.

Consulte a [Matriz de compatibilidade do Campaign Classic](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html) para acessar a lista de versões compatíveis.

**FEDERATED DATA ACCESS (FDA)**

A partir da versão do primeiro trimestre 19.1, o Adobe Campaign não é mais compatível com os seguintes servidores FDA.

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
