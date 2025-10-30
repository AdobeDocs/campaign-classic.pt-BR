---
product: campaign
title: Recursos obsoletos e removidos do Campaign Classic
description: Esta página lista recursos obsoletos e removidos do Adobe Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: d60d67de-6618-4f3b-be4a-ad7633ab5645
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: ht
source-wordcount: '1658'
ht-degree: 100%

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
   <td><strong>Detalhes</strong></td>
  </tr>
  <tr>
 <td>SDK legado do Campaign (Neolane)</td>
 <td><p>O SDK do Campaign (Neolane) para aplicativos móveis foi descontinuado Também é possível usar o SDK móvel da Adobe Experience Platform configurando a extensão do Adobe Campaign na interface da coleção de dados. O SDK móvel da Adobe Experience Platform ajuda a potencializar as soluções e os serviços da Adobe Experience Cloud em seus aplicativos móveis. A configuração dos SDKs é realizada por meio da interface da coleção de dados para oferecer uma configuração flexível e integrações extensíveis baseadas em regras. Saiba como configurar o canal de aplicativo móvel na <a href="https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/push/push-settings">documentação do Campaign v8</a>.</p>
<p>Data de remoção: 31 de julho de 2025 </p>
</td>
</tr>
<tr>
 <td>Marketing social com o Facebook</td>
 <td><p>O marketing social do Facebook agora está obsoleto. É possível usar a integração com o X (anteriormente conhecido como Twitter) para publicar em redes sociais ou colaborar com a Adobe para criar um canal personalizado.</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
<tr>
 <td>ACS Connector</td>
 <td><p>O conector ACS (oferta do Prime) agora está obsoleto. Você pode usar os recursos de exportação/importação do Campaign para extrair e inserir dados em ambos os produtos.</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
 </tbody> 
</table>

## Recursos removidos {#removed-features}

Esta seção lista os recursos e funcionalidades removidos do Campaign Classic.

<table> 
 <tbody>
  <tr> 
   <td><strong>Recurso</strong></td>
   <td><strong>Detalhes</strong></td>
  <tr>  
      <tr>
  <td>Conector de dados do Adobe Analytics<br></td>
   <td><p>O Conector de dados do Adobe Analytics foi removido em 17 de agosto de 2022. Ele foi descontinuado na versão 21.1.3 do Campaign.</p>
   <p>Se estiver usando este conector, precisará adaptar sua implementação adequadamente. <a href="../../integrations/using/gs-aa.md">Saiba mais</a></p>
  </td>
 </tr>
    <tr>
  <td>Relatório de monitoramento técnico da avaliação da entrega<br></td>
   <td><p>O Relatório de monitoramento técnico da avaliação da entrega não está mais disponível. Ele foi descontinuado na versão 21.1.3 do Campaign.</p>
   <!--p>If needed, you can receive this report daily by email until the feature removal date. To request it, open a specific <a href="https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html">Support Case</a> and specify the name of the instance and the email address(es) to send the report to.</p--> 
  </td>
 </tr>
  <tr>
  <td>Autenticação OAuth (OAuth e JWT)<br></td>
  <td><p> A autenticação da integração de acionadores para acessar o pipeline (originalmente baseada na configuração de autenticação OAuth) foi alterada e movida para o Adobe I/O. Este modo de autenticação foi descontinuado no Campaign 20.3.<p>
  <p>Se você estava usando a integração do Triggers, saiba como adaptar sua implementação <a href="../../integrations/using/about-triggers.md#implement">nesta página</a>.</p> 
  <p>Para obter mais informações sobre a depreciação da Autenticação OAuth, consulte esta <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">página</a></p> 
  <!--p><em>Target removal date: October 20, 2021. Hosted environments benefit from an extension until May 25, 2022. </em></p-->
  </td>
  </tr>
   <td>Relatórios<br></td>
   <td><p>Após o encerramento da vida útil do Adobe Flash Player, o relatório de medição e o mecanismo de renderização de gráfico não estarão mais disponíveis. <a href="../../reporting/using/creating-a-new-report.md">Saiba mais</a></p>
  </tr>
  <tr>  
   <td>Canal de fax<br></td>
   <td><p>A partir da versão 21.1.3 do Campaign, o Canal de fax não estará mais disponível. <a href="https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=pt-BR" target="_blank">Saiba mais na documentação do Campaign v8</a></p>
  </tr>
  <tr>
  <td>Domínio demdex<br></td>
  <td><p> A partir da versão 21.1.3 do Campaign, o domínio demdex usado para importar e exportar públicos-alvos para a Adobe Experience Cloud se tornará obsoleto. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Saiba mais</a></p> 
  </td>
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
   <td>A partir da versão 19.1 do Campaign, as APIs do Campaign Classic estarão disponíveis em uma página dedicada. Se estiver usando o arquivo jsapi.chm legado, agora deverá consultar a <a href="https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=pt-BR">nova versão online</a>.</td>
  </tr> 
  <tr> 
   <td>Orquestração de campanha – Marketing preditivo</td>
   <td>A partir da versão 18.10 do Campaign, os recursos de marketing preditivo não estarão mais disponíveis.</td>
  </tr> 
  <tr> 
   <td>Aplicativos da web - Microsites</td>
   <td>A partir da versão 18.10 do Campaign, os Microsites não estarão mais disponíveis. Você pode melhorar a segurança restringindo o acesso somente a domínios dedicados em arquivos de configuração do Adobe Campaign e usando URLs personalizados no Campaign por meio de aliases DNS.</td>
  </tr> 
  <tr> 
   <td>Notificações por push - Conector binário iOS</td>
   <td>De acordo com a recomendação da Apple, a Adobe removeu o Conector Binário do iOS herdado, iniciando na versão 18.10 do Campaign. O conector baseado em HTTP/2, mais avançado e eficiente, já está disponível.</td>
  </tr> 
  <tr> 
   <td>API decryptString</td>
   <td><p>Começando pela versão 18.6 do Campaign, por motivos de segurança, a API <em>decryptString</em> não estará mais disponível por padrão nas novas instalações.</p> 
   <p>No contexto de uma pós-atualização para 18.6 (e posterior), essa API não é mais ativada e foi substituída pela função <em>decryptPassword. </em> <a href="https://experienceleague.adobe.com/developer/campaign-api/api/f-decryptPassword.html?hl=decrypt">Saiba mais</a></p></td>
  </tr> 
   <tr> 
   <td>Canal móvel - Mensagens de push MMS e WAP</td>
   <td>A partir da versão 18.4 do Campaign, os canais MMS e Wap Push não estarão mais disponíveis. Como substituição, você pode usar as entregas de <a href="../../delivery/using/sms-channel.md">SMS</a> e <a href="../../delivery/using/about-mobile-app-channel.md">Push</a>.</td>
  </tr> 
   <tr> 
   <td>Canal móvel - LINE v1</td>
   <td>A partir da versão 18.4 do Campaign, o pacote do LINE Connect não estará mais disponível. A Adobe recomenda usar o novo pacote do Canal LINE como substituição. <a href="../../delivery/using/line-channel.md">Saiba mais</a></td>
  </tr>
 </tbody> 
</table>

<!--## Deprecated compatibility {#deprecated-compatibility}

The following systems are deprecated for Campaign Classic. Please refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md) to upgrade to a newer version or move to a new system before the compatibility ends.-->

## Fim da compatibilidade {#end-of-compatibility}

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

* A partir da versão 7.3.1, o Adobe Campaign não será mais compatível com Windows 8 e Windows Server 2012.

* A partir da versão 22.1, o Adobe Campaign não será mais compatível com o CentOs 8.x (64 bits). O Linux CentOS 8 atingiu o fim da vida útil (EOL) em 31 de dezembro de 2021. [Saiba mais](https://www.centos.org/centos-linux-eol/).

  Se você estava usando esse sistema operacional, adapte sua implementação de acordo. O CentOS 7.x (64 bits) e o RHEL 8.x/7.x (64 bits) ainda são compatíveis.

* A partir da versão 21.1.3, o Adobe Campaign não será mais compatível com o Debian 8.

* A partir da versão 19.1, o Adobe Campaign não será mais compatível com os seguintes sistemas operacionais.

   * CentOS 6. [Saiba mais](https://wiki.centos.org/Download)
   * Debian 7. [Saiba mais](https://wiki.debian.org/DebianReleases)
   * RHEL 6.x. [Saiba mais](https://access.redhat.com/support/policy/updates/errata)
   * Windows Server 2008. [Saiba mais](https://support.microsoft.com/pt-br/lifecycle/search/1163)
   * SLES 11. [Saiba mais](https://www.suse.com/lifecycle)

### Servidores da Web {#web-server-eol}

A partir da versão 19.1, o Adobe Campaign não é mais compatível com o seguinte servidor da Web.

* Apache 2.2. [Saiba mais](https://httpd.apache.org/)
* Microsoft IIS 7. [Saiba mais](https://support.microsoft.com/en-us/lifecycle/search/810)

### Ferramentas {#tools-eol}

A partir da versão do primeiro trimestre 19.1, o Adobe Campaign não é mais compatível com as seguintes ferramentas.

* Java JDK 7. [Saiba mais](https://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5/4.3/5.x, exceto quando incorporado em outra ferramenta. [Saiba mais](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Mecanismos de banco de dados {#dbe-eol}

A Adobe não oferece suporte aos seguintes mecanismos de banco de dados, pois foram descontinuados pelo editor. Os clientes que executam essas versões precisam atualizar para a versão mais recente ou mudar para outra.

Consulte a [Matriz de compatibilidade do Campaign ](../../rn/using/compatibility-matrix.md) para acessar a lista de versões compatíveis.

**FEDERATED DATA ACCESS (FDA)** 

A partir da versão 20.2, o Adobe Campaign não é mais compatível com o seguinte servidor FDA:

* DB2 UDB 10.5

A partir da versão do primeiro trimestre 19.1, o Adobe Campaign não é mais compatível com os seguintes servidores FDA:

* PostgreSQL 9.3.
* MySQL 5.5.
* DB2 9.5.
* Teradata 14 – 14.1.

O Campaign Classic não é compatível com os seguintes servidores no Federated Data Access (FDA). Use versões ou sistemas mais recentes.

* DB2 UDB 9.5, 9.7.
* Oracle 9i, 10G R2.
* As versões do PostgreSQL até a 9.6 chegaram ao fim da vida útil.
* MSSQL 2000, 2005, 2008 R2.
* MySQL 5.1.
* O InfiniDB chegou ao fim da vida útil.
* Teradata 13, 13.1.
* Netezza 6.02, 7.0. O Netezza chegou ao fim da vida útil.
* AsterData 5.0. O AsterData chegou ao fim da vida útil.
* Sybase IQ 15.2, 15.4, 15.5 e Sybase ASE 15.0.
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. O Adobe Campaign Classic ainda oferecerá suporte às versões listadas do Hadoop via HiveSQL por meio do Federated Data Access (FDA), mas essas versões foram mescladas com: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) e HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**SERVIDOR RDBMS**

A partir da versão 19.1, o Adobe Campaign não será mais compatível com os seguintes servidores RDBMS:

* Oracle 10GR2
* PostgreSQL 9.0 a 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7

As versões do PostgreSQL até a versão 9.6 chegaram ao fim da vida útil. Portanto, não são compatíveis com o Adobe Campaign.

### Conectores SMS {#sms-eol}

A partir da versão 20.2, os conectores SMS herdados ficarão obsoletos. O Adobe Campaign não é compatível com:

* SMPP genérico (SMPP versão 3.4 com suporte para modo binário)
* Sybase365 (SAP SMS 365)
* CLX Communications
* Tele2
* O2
* iOS

### Conectores CRM {#crm-connectors}

A partir da versão 21.1 do Campaign, os seguintes conectores de CRM não serão mais utilizados com o Campaign:

* API Soap - no local: 2007, 2015, 2016
* API Soap - online: 2015, 2016
* API da web – Microsoft Dynamics CRM 2016
* API da web – Microsoft Dynamics CRM 2016 atualização 1
* API Oracle por demanda
