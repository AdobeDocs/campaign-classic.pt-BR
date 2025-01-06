---
product: campaign
title: 'Versões [!DNL Gold Standard] '
description: Notas de versão e Matriz de compatibilidade do Campaign Classic [!DNL Gold Standard]
feature: Release Notes
role: User
level: Beginner
hidefromtoc: true
hide: true
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1774'
ht-degree: 98%

---

# Versões [!DNL Gold Standard] {#gold-standard}



Encontre nesta página as notas de versão e a matriz de compatibilidade para versões [!DNL Gold Standard].

## Notas de versão [!DNL Gold Standard] 


### Versão 12 do [!DNL Gold Standard]{#gs-12}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Obsoleto"}

_7 de setembro de 2021_

A build 9032@554dbcd inclui a seguinte correção:

* Correção de um problema que resultava em um erro 500 ao abrir o link para um aplicativo web em uma entrega de linha com rastreamento ativado.

_27 de agosto de 2021_

A build 9032@99a3894 inclui as seguintes correções:

* O recurso de assinatura de rastreamento foi aprimorado para evitar erros vinculados à forma como as ferramentas de terceiros (clientes de email, navegadores de Internet etc.) lidam com caracteres especiais. Os parâmetros de URL agora são codificados.
* Correção de um problema com seletores de data que poderia resultar na exibição de uma mensagem de erro de bloqueador por parte de um console. (NEO-36345)

### Versão 11 do [!DNL Gold Standard]{#gs-11}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Obsoleto"}

_14 de abril de 2021_

A compilação 9032@d030c36 inclui a seguinte correção:

* Correção de uma regressão do console do cliente que causava mensagens de erro persistentes na tela de conexão IMS. (NEO-34821)
* Esta build de console é necessária para manter o [acesso ao IMS](../../technotes/using/ims-updates.md).

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!CAUTION]
>
> * Se você estiver se conectando ao Campaign com sua Adobe ID, por meio do Adobe Identity Management Service (IMS), a atualização é obrigatória para o servidor do Campaign e o console do cliente poderem se conectar ao Campaign depois de **30 de junho de 2021**. [Saiba mais](../../technotes/using/ims-updates.md)
> * Esta versão inclui uma [correção de segurança](https://helpx.adobe.com/br/security/products/campaign/apsb21-04.html): a atualização agora é obrigatória para reforçar a segurança do ambiente.
> * Se estiver usando a integração de acionadores da Experience Cloud por meio da autenticação OAuth, é necessário migrar para o Adobe I/O conforme descrito [nesta página](../../integrations/using/about-triggers.md#implement). O modo de autenticação oAuth herdado do Campaign [foi removido](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) em **setembro de 2021**. Os ambientes hospedados se beneficiarão de uma extensão até **23 de fevereiro de 2022**. Como cliente no local ou híbrido, entre em contato com o Atendimento ao cliente da Adobe para estender o suporte até fevereiro de 2022. Você deve fornecer [o AppID do aplicativo OAuth](../../integrations/using/configuring-pipeline.md#step-optional) para a Adobe.
>
>Saiba mais na seção [[!DNL Gold Standard] ](../../rn/using/gold-standard.md)

_2 de março de 2021_

A compilação 9032@10c2709 inclui a seguinte correção:

* Correção de uma regressão que impedia o uso de alguns componentes do console, como o seletor de datas e o gerenciamento de imagens nas entregas. (NEO-31453, NEO-31454)

**Somente a atualização do console é obrigatória. Não é necessária nenhuma atualização do servidor.**

>[!NOTE]
>
> Conecte-se à [Distribuição de software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html) para baixar a nova versão. Saiba como propor a atualização do console para todos os usuários finais [nesta página](../../installation/using/client-console-availability-for-windows.md).

_22 de dezembro de 2020_

O build 9032@d3b452f inclui os seguintes aprimoramentos e correções:

* O protocolo de conexão foi atualizado para seguir o novo mecanismo de autenticação IMS.

* A autenticação da integração do Triggers, originalmente baseada na configuração da autenticação oAuth para acessar o pipeline, agora foi alterada e movida para o Adobe I/O. [Saiba mais](../../integrations/using/about-triggers.md#implement)

* Após o [fim do suporte para o protocolo binário herdado APNs do iOS](https://developer.apple.com/news/?id=c88acm2b), todas as instâncias que usam esse protocolo serão atualizadas para o protocolo HTTP/2 após a atualização.

* Correção de um problema de segurança para reforçar a proteção contra situações de SSRF (Server Side Request Forgery). (NEO-27777)




* Correção de um problema que resultava em falha em fluxos de trabalho ao executar uma atividade de **Enriquecimento**. (NEO-17338)

### Versão 10 do [!DNL Gold Standard]{#gs-10}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Obsoleto"}

_7 de julho de 2020_

A compilação 9032@efd8a94 inclui a seguinte correção:

Correção de um problema que impedia o funcionamento do rastreamento quando o recurso de assinatura era desabilitado. (NEO-26411)

>[!CAUTION]
>
>Recomendamos que você atualize o console do cliente com o disponível nesta versão. Consulte [esta página](../../installation/using/installing-the-client-console.md)

### Versão 9 do [!DNL Gold Standard]{#gs-9}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Obsoleto"}

_22 de junho de 2020_

A build 9032@800be2e inclui as seguintes correções:

* O conector HTTP2 para iOS foi aprimorado (atualizações de terceiros e gerenciamento de erros). (25904, NEO-, NEO-25903, NEO-25799)

As seguintes correções estão relacionadas ao mecanismo de segurança do link de rastreamento (consulte a [lista de verificação de segurança e privacidade](https://helpx.adobe.com/br/campaign/kb/acc-security.html#signature-mechanism)):

* Correção de um problema que impedia o funcionamento do rastreamento de &quot;cliques de notificação&quot; (notificações por push de iOS e Android). (NEO-25965)
* Correção de um problema que poderia impedir a abertura/clique de URLs de rastreamento ao usar determinadas versões herdadas do Outlook.  (NEO-25688)
* Correção de um problema que impedia o funcionamento do rastreamento de URLs usando fragmentos em parâmetros de personalização (tags de âncora com sinal de hashtag). (NEO-25774)
* Correção de um problema com o serviço anti-phishing. (NEO-25283)
* Correção de um problema de rastreamento ao usar fórmulas de rastreamento personalizadas específicas. (NEO-25277)





### Versão 8 do [!DNL Gold Standard]{#gs-8}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Obsoleto"}

_29 de abril de 2020_

A build 9032@3a9dc9c inclui as seguintes correções:

* A segurança no rastreamento de links no email foi aprimorada. Ela é ativada por padrão para todos os clientes. Um recurso de segurança adicional e aprimorado está disponível e pode ser ativado ao acessar o Atendimento ao cliente. Mais detalhes sobre o recurso e as etapas para clientes não hospedados para habilitá-lo podem ser encontrados na [lista de verificação de Segurança e Privacidade](https://helpx.adobe.com/br/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Se tiver problemas com notificações por push usando links de rastreamento ou entrega usando tags de âncora, recomendamos desabilitar o novo mecanismo de assinatura para links de rastreamento. O procedimento está detalhado [nesta página](https://helpx.adobe.com/br/campaign/kb/acc-security.html#signature-mechanism)

* Correção de um problema que impedia a exibição de imagens na entrega de linha. (NEO-23207)
* Correção de um problema com a atividade **Transferência de Arquivo**, que impedia que a autenticação com a chave SFTP funcionasse no Debian 9. (NEO-23183)
* Correção de um problema que poderia afetar a notificação via push quando enviada em alta frequência. (NEO-20516)
* Correção de um problema no gerenciamento de respostas de oferta que resulta em falhas no servidor da Web. (NEO-19482)
* Correção de um erro no gerenciamento do LibreOffice que impede a exportação de relatórios. (NEO-20982)
* Correção de um problema que causa um erro ao atualizar vários workflows por meio do uso de uma atividade de pesquisa.
* Melhora do gerenciamento do LibreOffice para evitar falhas na pré-visualização de email com arquivos .odt.
* Melhora no gerenciamento da conexão do Apache para evitar latência no serviço da Web.
* Melhora na exibição da tag da versão (7 dígitos) no menu **Sobre**.
* Correção de uma prevenção no gerenciamento de listas que impede a publicação de ofertas.
* Correção de uma regressão que resulta em falha do workflow de limpeza.
* Correção de uma regressão menor nos logs de workflow de limpeza.

### Versão 6 do [!DNL Gold Standard]{#gs-6}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Obsoleto"}

_9 de março de 2020_

A build 9032@19f73c5 inclui a seguinte correção:

* Correção de um problema com a conta externa que usa o FTP sobre SSL. (NEO-20498)

### Versão 5 do [!DNL Gold Standard]{#gs-5}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Obsoleto"}

_17 de dezembro de 2019_

A build 9032@d6b8062 inclui a seguinte correção:

* Correção de um problema de rastreamento nos seguintes canais de comunicação: dispositivos móveis (SMS, MMS), push (iOS, Android) e redes sociais (X, anteriormente conhecido como Twitter, Facebook). (NEO-19595)

### Versão 4 do [!DNL Gold Standard]{#gs-4}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Obsoleto"}

_11 de dezembro de 2019_

A build 9032@bc4a935 inclui a seguinte correção:

* Correção de um problema de desempenho ao enviar mensagens com um banco de dados MSSQL. (NEO-17558)

### Versão 3 do [!DNL Gold Standard]{#gs-3}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Obsoleto"}

_20 de novembro de 2019_

A build 9032@3468c7b inclui as seguintes correções:

* Correção de um problema de logon por autenticação IMS. (NEO-17312)
* Correção de um problema ao exibir relatórios cumulativos em várias entregas. (NEO-18165)
* Correção de um problema que poderia bloquear ou fazer o servidor web travar.

### Versão 2 do [!DNL Gold Standard]{#gs-2}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Obsoleto"}

_19 de setembro de 2019_

A build 9032@cee805c inclui as seguintes correções:

* Correção de um problema ao usar o Conector CRM para Salesforce. (NEO-17712)
* Correção de um problema de índice que causava problemas de desempenho ao enviar mensagens transacionais.

### Versão 19.1.4 - Build 9032{#release-19-1-4-build-9032}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Obsoleto"}

_13 de agosto de 2019_

A build inicial 19.1.4 inclui as seguintes correções:

* Correção de um problema no qual a atividade do scheduler gerava mensagens de erro indesejáveis durante a configuração do assistente. Reversão de atualização do NEO-11662. (NEO-17097)
* Correção de uma regressão causada pelo NEO-12727, que podia interromper os fluxos de trabalho quando uma atividade de teste era executada duas vezes. (NEO-16835)
* Correção de um problema que resultava em um código HTTP incorreto ser retornado (HTTP 200 OK em vez de HTTP 403 Forbidden) quando um token de sessão inválido ou expirado era usado em chamadas API. (NEO-16826)
* Correção de um problema com a chave DKIM, que não era inserida em emails, causando problemas de entrega. (NEO-16804)
* Correção de vários problemas com o agendamento de fluxos de trabalho. Os fluxos de trabalho eram agendados para serem executados uma vez por dia sem levar em consideração a configuração do programador. (NEO-16619, NEO-16426)


## Matriz de compatibilidade [!DNL Gold Standard] {#compatibility-matrix-gs}

Esta seção lista todos os sistemas e componentes compatíveis com builds 19.1 do **Adobe Campaign Classic[!DNL Gold Standard]**. Os produtos e as versões que não fazem parte dessa lista não são compatíveis com esta versão do Adobe Campaign.

>[!CAUTION]
>Salvo indicação em contrário, todas as versões secundárias são compatíveis.
>
>O Adobe Campaign Classic é compatível com todos os sistemas e ferramentas listados nesta página. À medida que versões específicas desses sistemas e ferramentas de terceiros atingem o fim da vida útil (EOL) com seus respectivos criadores, o Adobe Campaign não será mais compatível com essas versões, e elas serão removidas de nossa matriz de compatibilidade na próxima versão do produto. Verifique se você está usando as versões compatíveis dos sistemas listadas na matriz de compatibilidade para evitar problemas.
>

### Sistemas operacionais{#OperatingSystems-gs}

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
<p>9 (64 bits)</p>
<p>8 (64 bits)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 bits)</p>
<p><strong>Importante:</strong> se estiver usando o RHEL, desabilite o SELinux ou peça aos seus arquitetos que criem regras personalizadas de SELinux para verificar se um SELinux habilitado não está causando problemas nas operações do Campaign.</p>
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

### Servidores da Web{#WebServers-gs}

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
<p>2.2 para RHEL6 - CentOS 6 somente (64 bits)</p>
</td>
</tr>
</tbody>
</table>

### Ferramentas{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
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

### Servidores RDBMS{#RDBMSservers-gs}

>[!NOTE]
>
>O driver RDBMS deve corresponder à versão do servidor RDBMS.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
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
<p>Aviso: o Microsoft SQL Server não é compatível como o banco de dados principal quando o servidor do Campaign está em execução no Linux.</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>Aviso: DB2 UDB não é permitido para novas instalações.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>O PostgreSQL é o servidor de banco de dados padrão para ambientes hospedados.

### Conectores CRM{#CRMconnectors-gs}

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
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>API Soap - no local: 2007, 2015, 2016</p>
<p>API Soap - online: 2015, 2016</p>
<p>API da Web - no local e online: 365, 2016, 2016 Atualização 1</p>
</td>
</tr>
</tbody>
</table>

### Federated Data Access (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
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
</td>
</tr>
</tbody>
</table>

### Console do cliente {#ClientConsoleoperatingsystems}

`:warning:` os seguintes sistemas operacionais e navegadores são necessários para usar o Console do cliente do Campaign.

#### Sistemas operacionais

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>8</p>
<p>10 (recomendado para instâncias em japonês)</p>
</td>
</tr>
</tbody>
</table>

#### Navegador

<table>
<tbody>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>

### SDK móvel{#MobileSDK}

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
<p>iOS 9 – 14</p>
<p>com o SDK móvel build 1.0.26, compatível com as versões de 32 e 64 bits.</p>
</td>
</tr>
</tbody>
</table>

### Navegadores{#Browsers}

Os seguintes navegadores são compatíveis com o Campaign for Web Access.

<table>
<tbody>
<tr>
<td>
<p>Microsoft Edge</p>
</td>
<td>
<p>Versão mais recente</p>
</td>
</tr>
<tr>
<td>
<p>Mozilla Firefox</p>
</td>
<td>
<p>Versão mais recente</p>
</td>
</tr>
<tr>
<td>
<p>Google Chrome</p>
</td>
<td>
<p>Versão mais recente</p>
</td>
</tr>
<tr>
<td>
<p>Safari</p>
</td>
<td>
<p>Versão mais recente</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>
