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
discoiquuid: null
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be148d7cd55097b9014d2f4d3b095c65a5ca8c54
workflow-type: tm+mt
source-wordcount: '1389'
ht-degree: 98%

---


# Recursos descontinuados e removidos {#deprecated-and-removed-features}

A Adobe avalia constantemente os recursos do produto para identificar aqueles mais antigos que devem ser substituídos por alternativas mais modernas de forma a melhorar o valor geral do cliente, sempre considerando cuidadosamente a compatibilidade com versões anteriores. Como o Adobe Campaign Classic funciona com ferramentas de terceiros, a compatibilidade é atualizada regularmente, a fim de implementar somente as versões compatíveis. As versões que não são mais compatíveis com o Adobe Campaign Classic estão listadas abaixo.

Para comunicar a remoção/substituição iminente dos recursos do Campaign Classic, as seguintes regras se aplicam:

* O anúncio da descontinuação vem primeiro. Embora os recursos obsoletos ainda possam estar disponíveis para os usuários existentes, eles não serão aprimorados nem documentados.
* A remoção de recursos obsoletos ocorrerá na seguinte versão, o mais tardar. A data da remoção será anunciada nesta página.

Esse processo oferece aos clientes pelo menos um ciclo de lançamento para adaptar sua implementação a uma nova versão ou sucessor de um recurso obsoleto, antes da remoção.

>[!NOTE]
>As versões do Adobe Campaign e os novos recursos estão listados nas [Notas de versão](../../rn/using/latest-release.md).


## Recursos obsoletos {#deprecated-features}

Esta seção lista os recursos e funcionalidades marcados como obsoletos nas versões mais recentes do Campaign Classic.

Geralmente, os recursos que estão planejados para serem removidos em uma versão futura são definidos como obsoletos primeiro, com uma alternativa fornecida. Esses recursos e recursos não estão mais disponíveis para novos clientes do Campaign Classic ou não devem ser usados para nenhuma nova implementação. Eles também foram removidos da documentação do produto.

Os clientes são aconselhados a revisar se utilizam o recurso/funcionalidade em sua implantação atual e a fazer planos para alterar sua implementação para usar a alternativa fornecida. Consulte a data de remoção para planejar suas atualizações de ambiente e projeto de acordo.

### Versão 18.6 do Adobe Campaign {#ac-18-6-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Área</strong></td>
   <td><strong>Recurso</strong></td> 
   <td><strong>Substituição</strong></td> 
  </tr> 
   <tr> 
   <td>Segurança SDK Javascript <br> </td>
   <td>decryptString<br> </td>
   <td><p>Por motivos de segurança, a API <em>decryptString</em> não está mais disponível por padrão nas novas instalações.</p> 
   <p>No contexto de uma pós-atualização para 18.6 (e posterior), essa API não é mais ativada e foi substituída pela função <em>decryptPassword</em>.</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Versão 18.4 do Adobe Campaign {#ac-18-4-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Área</strong></td>
   <td><strong>Recurso</strong></td> 
   <td><strong>Substituição</strong></td> 
  </tr> 
   <tr> 
   <td>Arquivamento de email<br> </td>
   <td>Arquivamento baseado em arquivo<br> </td>
   <td><p>O arquivamento de emails agora está disponível por meio de um endereço de email CCO dedicado. <a href="../../installation/using/email-archiving.md">Saiba mais</a>.</p> 
   <p><em>Data de remoção do Target: Campaign versão 20.2 - junho de 2020</em></p><br> </td>
  </tr> 
   <tr> 
   <td>Gerenciamento de clientes potenciais<br> </td>
   <td>Clientes potenciais<br> </td>
   <td><p>O pacote de gerenciamento de clientes potenciais no Adobe Campaign Classic simplificou o processo de criação e manutenção de todo o ciclo de vida do gerenciamento de clientes potenciais. Uma funcionalidade semelhante pode ser implementada por meio de outras atividades de fluxo de trabalho nativas e modificações no modelo de dados.</p> 
   <p><em>Data de remoção do Target: Campaign versão 20.2 - junho de 2020</em></p><br> </td>
  </tr> 
 </tbody> 
</table>


## Compatibilidade obsoleta {#deprecated-compatibility}

### Versão 20.1 do Adobe Campaign {#compat-20-1-release}

A partir da versão 20.1 de fevereiro, o sistema a seguir está obsoleto para o Campaign Classic. A compatibilidade terminará na versão 20.2 - Junho de 2020.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Área</strong></td>
   <td><strong>Substituição</strong></td> 
  </tr> 
   <tr> 
   <td>Console do cliente do Campaign Classic 32 bits<br> </td>
   <td><p>Console do cliente do Campaign Classic 64 bits</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Versão 19.2 do Adobe Campaign  {#compat-19-2-release}

A partir da versão de outono 19.2, os seguintes sistemas operacionais serão descontinuados para o Campaign Classic. A compatibilidade terminará ao final do ano de 2020.

* Servidor da Web: Apache 2.2. [Saiba mais](https://wiki.centos.org/About/Product)
* Sistema operacional: CentOS 6. [Saiba mais](https://wiki.centos.org/About/Product)

Consulte a [Matriz de compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html) para atualizar para uma versão mais recente ou para um novo sistema.

## Recursos removidos {#removed-features}

Esta seção lista os recursos e funcionalidades removidos do Campaign Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Área - Recurso</strong></td>
   <td><strong>Substituição</strong></td> 
   <td><strong>versão</strong></td> 
  </tr> 
   <tr> 
   <td>Documentação das APIs do Campaign  - jsapi.chm file<br> </td>
   <td>As APIs do Campaign Classic agora estão disponíveis em uma página dedicada. Se estiver usando o arquivo jsapi.chm, agora deverá fazer referência <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">à nova versão online</a>.</td>
   <td>19.1</td>
  </tr> 
  <tr> 
   <td>Orquestração de campanha  - Marketing preditivo</td>
   <td>Uma grande parte dos recursos de marketing preditivo no Adobe Campaign Classic tem sido o consumo de modelos preditivos. Embora a atividade de fluxo de trabalho de marketing preditivo seja removida em uma versão futura, o Adobe Campaign continuará a oferecer suporte ao consumo e ao uso de modelos preditivos de fontes externas por meio de outras atividades de fluxo de trabalho.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Aplicação da Web - Microsites</td>
   <td>Melhore a segurança restringindo o acesso a apenas domínios dedicados nos arquivos de configuração do Adobe Campaign. Você ainda pode usar URLs personalizados no Campaign usando aliases DNS. <a href="https://helpx.adobe.com/br/campaign/kb/domain-name-delegation.html">Saiba mais</a>.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Notificações por push - Conector binário iOS<br></td>
   <td>Por recomendação da Apple, a Adobe removerá o iOS Binary Connector herdado. O conector baseado em HTTP/2, mais avançado e eficiente, já está disponível.</td>
   <td>18.10</td>
  </tr> 
   <tr> 
   <td>Canal móvel - Mensagens de push MMS e WAP</td>
   <td>Os canais de envio MMS e WAP não estão mais disponíveis. Como substituição, você pode usar os deliveries de <a href="../../delivery/using/sms-channel.md">SMS</a> e <a href="../../delivery/using/about-mobile-app-channel.md">Push</a>.</td>
   <td>18.4</td>
  </tr> 
   <tr> 
   <td>Canal móvel - LINE v1</td>
   <td>O pacote do LINE Connect não está mais disponível para instalação no Adobe Campaign Classic. A Adobe recomenda usar o novo pacote do canal LINE para enviar mensagens LINE. <a href="../../delivery/using/line-channel.md">Saiba mais</a>.</td>
   <td>18.4</td>
  </tr> 
 </tbody> 
</table>

## Fim da compatibilidade do {#end-of-compatibility}

>[!CAUTION]
>
>O Adobe Campaign Classic é compatível com todos os sistemas e ferramentas listados na [Matriz de compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html). Quando versões específicas desses sistemas e ferramentas de terceiros atingem o fim da vida útil (EOL) com seus respectivos criadores, o Adobe Campaign não é mais compatível com essas versões: elas são anunciadas como obsoletas e, em seguida, são removidas de nossa matriz de compatibilidade na versão subsequente do produto. Certifique-se de que você está usando as versões compatíveis de qualquer sistema listado na matriz de compatibilidade para evitar problemas.

### Console do cliente {#client-console-eol}

O Console do cliente do Adobe Campaign Classic não pode mais ser executado nos seguintes sistemas, pois foram descontinuados pelo editor. Os clientes que executam o Console do cliente do Campaign em uma dessas versões precisam atualizar para a versão mais recente antes da data de remoção. Consulte a [Matriz de Compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

### Sistemas operacionais {#o-s-eol}

A partir da versão 19.1, o Adobe Campaign não é mais compatível com os seguintes sistemas operacionais.

* Debian 7. [Saiba mais](https://wiki.debian.org/DebianReleases).
* RHEL 6.x. [Saiba mais](https://access.redhat.com/support/policy/updates/errata).
* Windows Server 2008. [Saiba mais](https://support.microsoft.com/pt-br/lifecycle/search/1163).
* SLES 11. [Saiba mais](https://www.suse.com/lifecycle).

### Servidores da Web {#web-server-eol}

A partir da versão do primeiro trimestre 19.1, o Adobe Campaign não é mais compatível com o seguinte servidor da Web.

* Microsoft IIS 7. [Saiba mais](https://support.microsoft.com/pt-br/lifecycle/search/810).

### Ferramentas {#tools-eol}

A partir da versão do primeiro trimestre 19.1, o Adobe Campaign não é mais compatível com as seguintes ferramentas.

* Java JDK 7. [Saiba mais](http://www.oracle.com/technetwork/java/javase/eol-135779.html).
* Libre Office 3.5/4.3/5.x, exceto quando incorporado em outra ferramenta. [Saiba mais](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases).

### Mecanismos de banco de dados {#dbe-eol}

A Adobe não oferece suporte aos seguintes mecanismos de banco de dados, pois foram descontinuados pelo editor. Os clientes que executam essas versões precisam atualizar para a versão mais recente ou mudar para outra.

Consulte a [Matriz de compatibilidade do Campaign Classic](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html) para acessar a lista de versões compatíveis.

**FEDERATED DATA ACCESS (FDA)**

A partir da versão do primeiro trimestre 19.1, o Adobe Campaign não é mais compatível com os seguintes servidores FDA.

* Oracle 11G. [Saiba mais](http://www.oracle.com/br/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 9.3. [Saiba mais](https://www.postgresql.org/support/versioning).
* MySQL 5.5. &lt;[Saiba mais](http://www.fromdual.com/support-for-mysql-from-oracle).
* DB2 9.5. [Saiba mais](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Teradata 14 - 14.1. [Saiba mais](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068).

O Campaign Classic não é compatível com os seguintes servidores no FDA (Federated Data Access — Acesso Federado a Dados).

* DB2 UDB 9.5, 9.7. A versão mais recente do DB2 é compatível com o Federated Data Access (FDA). [Saiba mais](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Oracle 9i, 10G R2. Versões mais recentes do Oracle são compatíveis com o FDA (Federated Data Access — Acesso Federado a Dados). [Saiba mais](http://www.oracle.com/br/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Versões mais recentes do PostgreSQL são compatíveis com o Federated Data Access (FDA). [Saiba mais](https://www.postgresql.org/support/versioning).
* MSSQL 2000, 2005, 2008 R2. As versões mais recentes do SQL Server são compatíveis com o FDA (Federated Data Access — Acesso a Dados Federados). [Saiba mais](https://support.microsoft.com/pt-br/lifecycle/search/1044).
* MySQL 5.1. Versões mais recentes do MySQL são compatíveis com o Federated Data Access (FDA). [Saiba mais](https://pt.wikipedia.org/wiki/InfiniDB).
* O InfiniDB chegou ao fim da vida útil. [Saiba mais](https://www.mysql.com/support).
* Teradata 13, 13.1. As versões mais recentes do Teradata são compatíveis com o Federated Data Access (FDA). [Saiba mais](https://www.info.teradata.com/download.cfm?ItemID=1007255).
* Netezza 6.02, 7.0. O Netezza chegou ao fim da vida útil. [Saiba mais](https://pt.wikipedia.org/wiki/Netezza).
* AsterData 5.0. O AsterData chegou ao fim da vida útil. [Saiba mais](https://pt.wikipedia.org/wiki/Aster_Data_Systems).
* Sybase IQ 15.2, 15.4, 15.5 e Sybase ASE 15.0. Versões mais recentes do Sybase são compatíveis com o Federated Data Access (FDA). [Saiba mais](https://sites.google.com/site/dbatipsandtricks/time-tracker).
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. O Adobe Campaign Classic ainda oferecerá suporte às versões listadas do Hadoop via HiveSQL por meio do Federated Data Acces (FDA), mas essas versões são mescladas com: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) e HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS SERVER**

O Adobe Campaign não é compatível com os seguintes servidores RDBMS:
* Oracle 10GR2, 11G
* PostgreSQL 9.0 a 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
