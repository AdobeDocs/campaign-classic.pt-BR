---
title: O arquivo de configuração do servidor
seo-title: O arquivo de configuração do servidor
description: O arquivo de configuração do servidor
seo-description: null
page-status-flag: never-activated
uuid: 8ef7168b-3543-4830-80b0-65a023158b3f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: da2198a3-7cef-4419-894d-e5bb51bb480c
translation-type: tm+mt
source-git-commit: 3acf2359c74a3dc4b18c8976fee14dcbaf3fa510
workflow-type: tm+mt
source-wordcount: '7852'
ht-degree: 8%

---


# O arquivo de configuração do servidor{#the-server-configuration-file}

A configuração geral do Adobe Campaign é definida no arquivo **serverConf.xml** , localizado no diretório **conf** do diretório de instalação. Esta seção lista todos os nós e parâmetros diferentes do arquivo **serverConf.xml** .

>[!NOTE]
>
>As configurações do servidor só podem ser executadas por Adobe para implantações hospedadas pelo Adobe. Para saber mais sobre as diferentes implantações, consulte a seção Modelos [de](../../installation/using/hosting-models.md) hospedagem ou [esta página](../../installation/using/capability-matrix.md). As etapas de instalação e configuração para modelos hospedados e híbridos são apresentadas nesta [seção](../../installation/using/hosted-model.md).

Os primeiros parâmetros estão dentro do nó **compartilhado** . Eles estão relacionados à instância. Eles são potencialmente usados por todos os comandos nlserver (nlserver web, nlserver wfserver etc.). As outras seções estão relacionadas a um subcomando nlserver específico.

**Parâmetros compartilhados**

* [autenticação](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [javaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [módulo](#module)
* [monitoramento](#monitoring)
* [ooconsole](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [xtkJobs](#xtkjobs)

**Outros parâmetros**

* [arquivamento](#archiving)
* [inMail](#inmail)
* [interativo](#interactiond)
* [mta](#mta)
* [nmac](#nmac)
* [tubulação](#pipelined)
* [reparação](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [stat](#stat)
* [syslogd](#syslogd)
* [tracking](#tracking)
* [trackinglogd](#trackinglogd)
* [web](#web)
* [wfserver](#wfserver)

## authentication {#authentication}

Estes são os diferentes parâmetros do nó de **autenticação** :

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> checkIPConsistent<br /> </td> 
   <td> Ative a verificação de endereço IP.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> Modo de identificação padrão.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'nl'<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> Tempo limite de sessões longas em segundos.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> Tempo limite do token de segurança em segundos.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> Duração do cache: cache de informações da sessão em segundos.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> Tempo limite da sessão em segundos.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

Estes são os diferentes parâmetros do nó **authentication > XTK** :

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> internalPassword<br /> </td> 
   <td> Senha da conta interna.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> Zona de segurança da conta interna: zona autorizada para a conta interna.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

Estes são os diferentes parâmetros do nó **dataStore** . É aqui que as fontes de dados do servidor são definidas.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportDirectory<br /> </td> 
   <td> Diretório de exportação: caminho do diretório de destino para os dados exportados.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxedDirectory<br /> </td> 
   <td> Diretórios com caixa de proteção extra: outros caminhos a serem adicionados na caixa de proteção (separados por vírgulas).<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '/home/customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Atraso de expiração do cache de formulários: tempo limite em segundos após o qual uma entrada de cache é invalidada. O significa que as entradas de cache são atualizadas somente no momento da publicação.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> hosts<br /> </td> 
   <td> Máscaras de DNS: lista de máscaras de DNS que esta instância serve (separadas por vírgulas, podem usar * e ? padrões).<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> ativityCacheTimeToLive<br /> </td> 
   <td> Atraso de expiração do cache JSSP de interação: tempo limite em segundos após o qual uma entrada de cache é invalidada. Um valor negativo significa que o cache é sempre invalidado. '0', valores vazios ou inválidos são considerados como 60.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Idioma da instância (lista discriminada). Os valores possíveis são 'fr_FR' (Français), 'en_GB' (inglês (Reino Unido), 'en_US' (inglês (EUA)), 'de_DE' (Deutsch) e 'ja_JP' (japonês).<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> Carregar pasta: caminho do diretório de destino para os dados carregados.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> Arquivos autorizados a serem baixados separados por ','. A string deve ser uma expressão java regular e válida. Consulte <a href="../../installation/using/configuring-campaign-server.md#limiting-uploadable-files" target="_blank">Limitação de arquivos</a>carregáveis.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> Guardar segredos no Cofre: use o Hashicorp Vault.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> Caminho secreto no Cofre<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '/v1/secret/campanha/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> Caminho local do arquivo que contém o token de cofre. $(HOME) pode ser usado neste caminho (mas não em outras variáveis env).<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> URL do Hashicorp Vault <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> Período de validade do cache de visualização: tempo limite em segundos após o qual uma entrada de cache é invalidada. Um valor negativo significa que o cache é sempre invalidado. '0', valores vazios ou inválidos são considerados como 60.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> XPath do diretório de trabalho.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> workingDirectory : XPath do diretório de trabalho. Padrão: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/espaço de trabalho/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

Estes são os diferentes parâmetros do nó **dataStore > proxyAdjust** . Os URLs que correspondem à expressão normal são regenerados com base no URL definido em urlBase.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> urlBase<br /> </td> 
   <td> Base a ser usada ao gerar URLs externos. Ex: https://server.domain.com<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Expressão regular para corresponder a URLs. Ex: http://server\.lan\.net.*<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

Estes são os diferentes parâmetros do nó **dataStore > dataSource** .

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome da fonte de dados<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> padrão<br /> </td> 
  </tr> 
 </tbody> 
</table>

No nó **dataStore > dataSource > dbcnx** , defina as configurações de conexão:

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NChar<br /> </td> 
   <td> Armazenamento Unicode<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Espaço de trabalho<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> criptografado<br /> </td> 
   <td> Senha criptografada<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Account<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Password<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> fornecedor<br /> </td> 
   <td> Tipo (lista discriminada). Os valores possíveis são 'Oracle', 'MSSQL' (Microsoft SQL Server), 'PostgreSQL' (PostgreSQL, Greenplum), 'Teradata', 'DB2', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA' (SAP HANA), 'RedShift' (Amazon Redshift), 'ODBC' (ODBC BC (Sybase ASE, Sybase IQ), "Relay" (relé HTTP para banco de dados remoto).<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> server<br /> </td> 
   <td> Server<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> timezone<br /> </td> 
   <td> Fuso horário: consulte Gerenciamento <a href="../../installation/using/time-zone-management.md" target="_blank">de fuso horário</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> Unicode data in the database<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> Campos de data com fuso horário: consulte Gerenciamento <a href="../../installation/using/time-zone-management.md" target="_blank">de fuso horário</a>.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

No nó **dataStore > dataSource > sqlParams** , configure os parâmetros SQL:

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> funcPrefix<br /> </td> 
   <td> Prefixo da função<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
 </tbody> 
</table>

No nó **dataStore > dataSource > pool** , configure os parâmetros do pool de conexões associadas:

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> liveTestDelaySec<br /> </td> 
   <td> Atraso entre as verificações de validade da conexão.<br /> </td> 
   <td> Curto<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> Número de conexões gratuitas mantidas no pool.<br /> </td> 
   <td> Curto<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> Número máximo de conexões permitidas antes de recusar uma nova conexão. Veja esta <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">nota técnica</a>.<br /> </td> 
   <td> Curto<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> Tempo máximo de inatividade da conexão. 0 significa valor padrão.<br /> </td> 
   <td> Curto<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

Estes são os diferentes parâmetros do nó **dataStore > VirtualDir** . Esta é a configuração do diretório virtual para o mapeamento de diretório real.

Para obter informações adicionais, consulte [Gerenciamento de recursos públicos](../../installation/using/configuring-campaign-server.md#managing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome do diretório virtual <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> caminho<br /> </td> 
   <td> Caminho completo do diretório real<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
 </tbody> 
</table>

Esta é a configuração padrão:

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

Estes são os diferentes parâmetros do nó **dataStore > preprocessCommand** . Esses são os comandos autorizados para o pré-processamento da atividade de fluxo de trabalho &#39;Carregar arquivo&#39;.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> comando<br /> </td> 
   <td> Linha de comando <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Rótulo da linha de comando<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome da linha de comando<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
 </tbody> 
</table>

Esta é a configuração padrão:

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

Estes são os diferentes parâmetros do nó **dnsConfig** (configuração DNS).

For additional information, refer to this [section](../../installation/using/configuring-campaign-server.md).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Nome do domínio: nome de domínio padrão. Usado pelo comando SMTP HELO. Por padrão, usa os parâmetros de rede da primeira interface de rede declarada no Windows; ou analisa o file/etc/resolv.conf em Linux (domínio ou entrada de pesquisa). <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> Servidor DNS: lista separada por vírgulas de servidores de nomes de domínio (DNS). Consulte a nota abaixo.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> retry<br /> </td> 
   <td> Número de tentativas para um query DNS.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Tempo limite em milissegundos para um query DNS.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Observação sobre **nameSevers**: por padrão, usa a rede
>parâmetros da primeira interface de rede declarada no Windows
>não definido no UNIX. Define os servidores de nomes de domínio (DNS)
>usado pelo MTA para obter a declaração do Mail Exchanger para
>um domínio.
>
>Se esse valor não estiver definido, o MTA busca essas informações na configuração de rede do host. Se vários DNS forem possíveis, os diferentes endereços DNS devem ser separados por vírgula (por exemplo: 212.155.207.1.212.155.207.2). Se o servidor do delivery tiver várias interfaces de rede, a lista DNS usada pelo MTA será a primeira. Nesse caso, recomendamos especificar o parâmetro **nameServer** para evitar qualquer ambiguidade.

>[!CAUTION]
>
>Se a configuração do host da rede usar DHCP, o MTA não encontrará a lista DNS fornecida pelo DHCP. Nesse caso, recomendamos especificar a lista DNS nos parâmetros de rede do painel de controle do Windows.

## exec {#exec}

Estes são os diferentes parâmetros do nó **exec** (execução de comando).

Para obter informações adicionais, consulte [Restrição de comandos](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)externos autorizados.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> blacklistFile<br /> </td> 
   <td> Caminho para o arquivo que contém os comandos a serem adicionados à lista de permissões. <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> user<br /> </td> 
   <td> Executar comandos como um usuário diferente.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

Estes são os diferentes parâmetros do nó **htmlToPdf** . Esta é a configuração do serviço para converter páginas da Web em documentos PDF.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> comando<br /> </td> 
   <td> Linha de comando para executar a conversão (no modo 'outro').<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> Max. número de processos de conversão permitidos por vez em uma máquina.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> mode<br /> </td> 
   <td> Ferramenta a a ser usada para a conversão. Os valores possíveis são: phantomjs, wkhtmltopdf, outros, desativados<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Tempo limite para uma conversão: tempo máximo de conversão em segundos. Além desse limite, o processo de conversão é interrompido e um erro é gerado.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> verboso<br /> </td> 
   <td> Modo detalhado: start no modo detalhado para diagnosticar possíveis erros.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Atraso ao aguardar um processo: em segundos, quando todos os processos são usados ao mesmo tempo e ao aguardar a liberação de um processo. Se esse atraso for excedido, a conversão será interrompida e um erro será gerado. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Exemplo para phantomjs:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## javaScript {#javascript}

Estes são os diferentes parâmetros do nó **javaScript** . Esta é a configuração do interpretador JavaScript.

Para obter informações adicionais, consulte a documentação [do](../../reporting/using/actions-on-reports.md#memory-allocation) Relatórios e esta [nota técnica](https://helpx.adobe.com/campaign/kb/out-of-memory-error-in-js-code-activity-in-workflows.html).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxMB<br /> </td> 
   <td> Tamanho máximo em megabytes antes de executar o coletor de lixo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> Tamanho de cada bloco da pilha em quilos de octetos. Este é um parâmetro de ajuste de gerenciamento de memória que a maioria dos usuários não deve ajustar. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

Estes são os diferentes parâmetros do nó **mailExchanger** . Esta é a configuração do servidor SMTP.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> mxAddress<br /> </td> 
   <td> Servidor SMTP: Endereço IP do servidor SMTP para transferência de e-mails.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> Porta TCP do servidor SMTP usada para a transferência de E-mail.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## module {#module}

Estes são os diferentes parâmetros do nó do **módulo** . Esta é a configuração do módulo de restrições do namespace xtk.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> defaultNameSpace<br /> </td> 
   <td> Namespace padrão usada ao criar uma nova entidade.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## monitoring {#monitoring}

Estes são os diferentes parâmetros do nó de **monitoramento** . Esta é a configuração do serviço de monitoramento.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPrepareJobsSec<br /> </td> 
   <td> Tempo máximo de preparação: duração em segundos após a qual uma ação do delivery não deve mais estar em preparação.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> Script Unix executado pelo serviço de monitoramento.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> Script do Windows a ser executado pelo serviço de monitoramento.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconsole {#ooconv}

Estes são os diferentes parâmetros do nó **oconsole** . Esta é a configuração do servidor de conversão de documentos.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxConversions<br /> </td> 
   <td> Número máximo de conversões que um servidor OpenOffice tem permissão para executar. Além desse número, o servidor será reiniciado.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> Tempo de inatividade máximo do servidor OpenOffice antes do fechamento forçado.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> Intervalo de portas nas quais os servidores OpenOffice estão ouvindo.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL do servidor de conversão de documentos.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Estes são os diferentes parâmetros do nó **proxyConfig** . Esta é a configuração dos parâmetros de proxy.

Para obter informações adicionais, consulte a configuração [de conexão](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)proxy.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabled<br /> </td> 
   <td> Use um servidor proxy.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> substituição<br /> </td> 
   <td> Exceções: lista de endereços para os quais os parâmetros de proxy devem ser ignorados.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> Servidor proxy exclusivo: use a mesma configuração para todos os tipos de proxy.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Proxy HTTP / proxy seguro {#http-proxy---secure-proxy-}

No nó proxy **proxyConfig > Proxy HTTP / proxy** seguro, configure os seguintes parâmetros.

Para obter informações adicionais, consulte a configuração [de conexão](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)proxy.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Endereço do servidor proxy<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Logon para a conexão com o servidor proxy<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Senha para a conexão com o servidor proxy<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Porta do servidor proxy<br /> </td> 
   <td> Curto<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

Estes são os diferentes parâmetros do nó **threadPool** .

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxThreadCount<br /> </td> 
   <td> Número máximo de threads no pool. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

Estes são os diferentes parâmetros do nó **urlPermission** . Esta é a lista de URLs que o código Javascript pode acessar.

Lista de domínios e expressões regulares especificando se um URL encontrado no código Javascript pode ou não ser usado pelo servidor Adobe Campaign.

Se o URL não puder ser encontrado, a ação padrão será executada, de acordo com o modo padrão especificado.

Para obter informações adicionais, consulte Proteção [de conexão de](../../installation/using/configuring-campaign-server.md#url-permissions)saída.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> ação<br /> </td> 
   <td> Ação padrão se o URL não estiver na lista autorizada (lista discriminada). Os valores possíveis são "ignorar" (autorizar sem mensagem de aviso, isso requer desativar a proteção), "avisar" (autorizar e emitir uma mensagem de aviso) e "negar" (proibir acesso ao URL).<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> negar<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> Depuração do rastreamento do mecanismo de seleção de URL: emite mensagens adicionais durante o processo de verificação de URL.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### url {#url}

Para cada URL, adicione um nó **url** com os seguintes parâmetros:

Para obter informações adicionais, consulte Proteção [de conexão de](../../installation/using/configuring-campaign-server.md#url-permissions)saída.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dnsSuffix<br /> </td> 
   <td> Nome do domínio, ou domínio pai, afetado pelo URL: todo ou parte do domínio do URL para verificar, para acelerar a verificação. O URL só será verificado em relação à expressão regular se seu domínio contiver dsnSuffix.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Expressão regular para refinar a validação de URLs pertencentes a este domínio: expressão regular que o URL deve verificar, caso corresponda a dnsSuffix.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
 </tbody> 
</table>

Se um registro atender **dnsSuffix** , mas não **urlRegEx**, o registro a seguir será examinado.

Por exemplo, para autorizar o acesso a todos os URLs do domínio business.com, podemos definir dois registros:

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.*&quot;

e

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.*&quot;

Esta é a configuração padrão:

```
<url dnsSuffix="api.omniture.com" urlRegEx="https://api.omniture.com/genesis/i/3.1.*"   />
<url dnsSuffix="omniture.com" urlRegEx="https://api[1-5].omniture.com/genesis/i/3.1.*"  />
<url dnsSuffix="marketing.adobe.com"                     urlRegEx="https://.*"                                    />
<url dnsSuffix="fcm.googleapis.com"                      urlRegEx="https://fcm.googleapis.com/fcm/send.*"       />
<url dnsSuffix="graph.facebook.com"                      urlRegEx="https://.*"                                    />
<url dnsSuffix="api.line.me"                             urlRegEx="https://api.line.me/.*"                      />
<url dnsSuffix="api.twitter.com"                         urlRegEx="https://api.twitter.com/1.1.*"              />
<url dnsSuffix="adobeid-na1.services.adobe.com"          urlRegEx="https://.*"                                    />
<url dnsSuffix="adobeid-na1-stg1.services.adobe.com"     urlRegEx="https://.*"                                    />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/jssp/dm/renderingSeed.jssp" />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/nl/jsp/soaprouter.jsp" />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

Estes são os diferentes parâmetros do nó **xtkJobs** . Esta é a configuração dos trabalhos do servidor.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Período de atualização do status da memória do processamento do servidor (em ms).<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## archiving {#archiving}

Estes são os diferentes parâmetros do nó de **arquivamento** . Esta é a configuração das operações de arquivamento executadas em segundo plano.

Para obter informações adicionais, consulte [Ativação do arquivamento de e-mails (no local)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> acquisitionLimit<br /> </td> 
   <td> Número de EMLs a serem processados ao mesmo tempo<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archiveType<br /> </td> 
   <td> Estratégia de arquivamento de mensagens enviadas (lista discriminada). Os valores possíveis são "0" (sem arquivamento) e "1" (transfere o arquivamento de mensagens enviadas para um servidor SMTP).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parâmetros de start<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Start automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> Tamanho de um arquivo compactado: número máximo de arquivos em um arquivo compactado.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> Formato de compactação usado durante o arquivamento (lista discriminada). Os valores possíveis são '0' (sem compactação) e '1' (compacte as mensagens enviadas usando o formato zip).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> Atraso antes do arquivamento automático de emails não processados: número de dias antes do arquivamento de emails não processados.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID do JavaScript a ser executado ao iniciar o processo.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memória: alerta sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Aviso de consumo de memória: aviso sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Atraso (em segundos) entre cada evento de atualização.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora do dia em que o processo é reiniciado automaticamente. Consulte Reinicialização <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">automática do processo</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> Número de dias antes que emails não processados sejam excluídos.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridade no start. Os módulos de baixa prioridade são iniciados pela primeira vez e parados pela última vez. O módulo syslogd deve, portanto, ter a prioridade 0.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> Arquivamento do destino do público alvo<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> Ativar suporte ao SMTPS: ativa o delivery de emails no modo de segurança (STARTTLS/SMTPS) quando suportado pelo servidor remoto.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> Número de conexões com o servidor SMTP de arquivamento.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> Lista separada por vírgulas de nomes DNS ou endereços IP de retransmissores SMTP a serem usados. <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> Porta IP do servidor SMTP.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

Estes são os diferentes parâmetros do nó **inMail** . Esta é a configuração do módulo de gerenciamento de email de entrada.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parâmetros de start<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Start automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> Verifique o nome da instância: se verdadeiro, o nome da instância do Adobe Campaign contido nos cabeçalhos da ID da mensagem deve ser o mesmo da instância atual. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> Endereço de encaminhamento: endereço de transferência de email padrão não processado por uma regra. <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> Endereço para erros: endereço padrão usado para transferir e-mails inválidos (codificação MIME inválida). <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> Ignorar tamanho da mensagem: é usada para ignorar o tamanho de uma mensagem retornada por servidores POP3. Nesse caso, o módulo espera um '.' no final das mensagens. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Período de leitura da mensagem: frequência de sondagem da fila de mensagens.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID do JavaScript a ser executado ao iniciar o processo.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> Número máximo de registros a atualizar: define o número máximo de mensagens de log a serem mantidas na memória antes de atualizar o banco de dados.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> Número máximo de mensagens a serem lidas durante a sessão POP3.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memória: alerta sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Aviso de consumo de memória: aviso sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Duração da sessão: duração máxima da sessão de processamento de mensagens.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> Período de sondagem POP3<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> Tamanho da fila de mensagens de leitura<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> Tempo limite de comunicação com o servidor POP3. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora do dia em que o processo é reiniciado automaticamente. Consulte Reinicialização <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">automática do processo</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> Frequência de recarregamento de banco de dados de contas a serem pesquisadas.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridade no start. Os módulos de baixa prioridade são iniciados pela primeira vez e parados pela última vez. O módulo syslogd deve, portanto, ter a prioridade 0.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

No nó **inMail > msgDump** , configure os seguintes parâmetros. Esta é a configuração do despejo de mensagens processadas.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> depósito<br /> </td> 
   <td> Salve todas as mensagens de entrada no formato de texto. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> Caminho de despejo da mensagem.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interativo {#interactiond}

Estes são os diferentes parâmetros do nó **interativo** . Esta é a configuração do daemon de gravação para eventos de interação de entrada.

Para obter informações adicionais, consulte [Interação - buffer](../../installation/using/interaction---data-buffer.md)de dados.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parâmetros de start<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Start automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Max. número de caracteres armazenados na memória compartilhada para dados de chamada.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID do JavaScript a ser executado ao iniciar o processo<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memória: alerta sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Aviso de consumo de memória: aviso sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max. número de eventos armazenados na memória compartilhada.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> Número máximo de ofertas elegíveis classificadas logo após as proposições, a serem armazenadas para fins estatísticos.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora do dia em que o processo é reiniciado automaticamente. Consulte Reinicialização <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">automática do processo</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridade no start. Os módulos de baixa prioridade são iniciados pela primeira vez e parados pela última vez. O módulo syslogd deve, portanto, ter a prioridade 0.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> Duração da agregação em segundos para as estatísticas do tempo de resposta. 0 significa que o armazenamento estatístico foi desativado.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max. número de caracteres armazenados na memória compartilhada para identificar indivíduos.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

Estes são os diferentes parâmetros do nó **mta** . Esta é a configuração dos agentes do delivery.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parâmetros de start<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '-tracefilter:nlmta' <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Start automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> Salvar caminho de e-mails enviados: se não estiver vazio, o caminho onde todos os arquivos de origem de emails enviados serão salvos. <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> Diretório de despejo:Se não estiver vazio, copie envelopes MIME de mensagens de email enviadas neste diretório. Usado para solução de problemas. <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> Atraso nos registros de query DNS: tempo em milissegundos para exibir os registros.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Frequência das estatísticas de erros: tempo entre a produção de estatísticas e o armazenamento na base de dados. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID do JavaScript a ser executado ao iniciar o processo.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> Gere estatísticas de erros e armazene-as no banco de dados.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Exibir nível de mensagens de log. Nível de gravidade dos registros escritos no banco de dados. As mensagens de log geradas pelo MTA nem sempre são gravadas no banco de dados. Com esse parâmetro, você pode definir o nível a partir do qual uma mensagem deve ser gravada no banco de dados. Se você definir o nível 2, as mensagens dos níveis 1 e 0 também serão gravadas, enquanto se você definir o nível 1, somente as mensagens dos níveis 1 e 0 serão gravadas. Os valores possíveis são: 0 (erros), 1 (aviso), 2 (informações)<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Tamanho máximo de memória (em MB) que um processo mta pode usar. Acima desse limite, o processo é reiniciado para que a memória usada seja liberada para o sistema.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memória: alerta sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Aviso de consumo de memória: aviso sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Limite de conexão a ser considerado. As estatísticas de erro não são geradas para um determinado caminho se o número total de conexões para o período especificado por errorPeriodSec for estritamente inferior ao limite.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Limite de erro a ter em conta: as estatísticas de erro não são geradas para um determinado caminho se o número total de erros para o período especificado por errorPeriodSec for estritamente inferior ao limite.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Limite de mensagem a ser considerado. As estatísticas de erro não são geradas para um determinado caminho se o número total de mensagens enviadas para o período especificado por errorPeriodSec for estritamente inferior ao limite.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Retransmissão de notificação: HostName:Porta usada para retransmitir notificações.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora do dia em que o processo é reiniciado automaticamente. Consulte Reinicialização <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">automática do processo</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> Atraso antes de e-mails arquivados serem excluídos: número de dias antes de e-mails arquivados no diretório especificado em dataLogPath serem removidos.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> Repetir mensagens perdidas: partes dos delivery serão experimentadas novamente se o processo da criança estiver morto.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridade no start. Os módulos de baixa prioridade são iniciados pela primeira vez e parados pela última vez. O módulo syslogd deve, portanto, ter a prioridade 0.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> Ative o mecanismo de assinatura. Isso melhora a segurança no rastreamento de links no email.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Endereço do servidor de estatísticas do delivery, fornecido como &lt;dns ou ip&gt; <code>[</code>: 
     &lt;porta&gt; <code>]</code>. Consulte <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Coordenadas do servidor</a>de estatísticas. 
      <br /> 
     </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> Se não estiver definida, a porta padrão será 7777.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> Habilitar TLS por domínio: ativa o TLS configurável pelo MX (requer um servidor de estatísticas atualizado).<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> Versão do protocolo usada: versão do protocolo de comunicação (1 para um servidor v5.11 e 6.0.2, 2 para um servidor v6.1).<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> Se não estiver definido, a versão mais recente será usada. <br /> </td> 
  </tr> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> Se definido como "true", sua instância está usando o MTA <a href="https://helpx.adobe.com/br/campaign/kb/acc-campaign-enhanced-mta.html" target="_blank">aprimorado</a>.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Modo de verificação: ativa o modo de verificação (sem transmissão física de mensagens; utilizados para simulações e ensaios).<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> Diretório de trabalho: local dos arquivos temporários usados pelo MTA para se comunicar com seus processos filhos.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> Campo X-Mailer: valor do campo 'X-Mailer' no cabeçalho de email SMTP.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

No nó de **cache** , configure os seguintes parâmetros. Esta é a configuração do cache de arquivos local.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPeriodSec<br /> </td> 
   <td> Reciclado após: período, expresso em segundos, após o qual o arquivo é automaticamente excluído do cache para recuperar o armazenamento.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Tamanho máximo do cache (Mb).<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Frequência de expurgação: período em segundos entre execuções do mecanismo de expurgação do cache.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relé {#relay}

No nó **mta > relay** , configure os seguintes parâmetros. Esta é a configuração do servidor de correio para o delivery de mensagens.

Para obter informações adicionais, consulte relé [SMTP](../../installation/using/configuring-campaign-server.md#smtp-relay).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Lista separada por vírgulas de nomes DNS ou endereços IP de retransmissores SMTP a serem usados. <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Porta IP do servidor SMTP.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### principal {#master}

No nó **mta > principal** , configure os seguintes parâmetros. Esta é a configuração do servidor principal.

For additional information, refer to this [section](../../installation/using/configuring-campaign-server.md#mta-child-processes).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Frequência de sondagem do banco de dados dos trabalhos a serem entregues. Esse valor indica a frequência de polling do banco de dados (em segundos). Para obter a lista de trabalhos esperando pelo delivery, o MTA consulta o banco de dados regularmente. Quando não há trabalho em espera, o período de pesquisa é definido por esse valor. Caso contrário, se um trabalho tiver sido transferido para um servidor filho, a duração da pesquisa será automaticamente reduzida para um segundo para que um novo trabalho possa ser processado novamente assim que possível, isto é, assim que um servidor filho estiver disponível novamente. Isso não significa que o query do banco de dados será feito a cada segundo até que um servidor filho esteja disponível novamente. Na verdade, o acesso a um banco de dados só é feito quando pelo menos um servidor filho estiver disponível.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Período de espera após uma falha de conexão com o banco de dados. Uma falha de conexão de banco de dados é normalmente causada pelo próprio servidor de banco de dados. O servidor também pode ser interrompido para fins de manutenção, por exemplo. O parâmetro DataBaseRetryDelay define a duração entre duas tentativas de conexão em caso de falha de conexão de banco de dados.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Período de validade para o cache de chaves privadas (DomainKeys). As chaves privadas usadas para assinar emails seguindo a recomendação DomainKeys (http://antispam.yahoo.com/domainkeys) são armazenadas como opções no banco de dados. O parâmetro domainKeysReloadPeriodSec define quantos segundos o MTA pode manter essas chaves em um cache. Após esse atraso, todas as chaves devem ser recarregadas do banco de dados.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Número máximo de servidores secundários. Representa o número máximo de servidores em execução. É recomendável limitar esse número a uma compatibilidade ótima com os recursos de memória do servidor. Isso pode ser verificado durante um delivery. A memória usada não deve exceder um terço da memória física disponível, caso contrário a troca será usada. Consulte Processos <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">secundários</a>MTA.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Número mínimo de servidores secundários. O MTA tenta manter pelo menos esse número de servidores em execução. Se houver menos, ele reiniciará novos servidores a cada segundo até que esse valor seja atingido.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Número de servidores filho no start. O número de servidores secundários é monitorizado dinamicamente; quando o MTA é start, ele cria quantos servidores filho forem indicados por esse valor. Normalmente, os servidores filhos não podem ser iniciados mais rápido que um servidor por segundo para salvar os recursos do host. No entanto, quando o MTA é start, essa limitação é ignorada para que os servidores filho estejam disponíveis o mais rápido possível.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### criança {#child}

No nó **mta > filho** , configure os seguintes parâmetros. Esta é a configuração de servidores filhos.

Para obter informações adicionais, consulte Otimização [de envio de](../../installation/using/email-deliverability.md#email-sending-optimization)email.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> extraArgs<br /> </td> 
   <td> Argumentos opcionais da linha de comando <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> Tempo limite até que os servidores filho inativos sejam interrompidos. Se um servidor filho tiver um tempo ocioso maior que esse parâmetro, ele se matará automaticamente para liberar os recursos do host.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Tempo máximo de retenção de mensagens. Se uma mensagem preparada não pôde ser enviada devido à limitação ou não pôde se conectar ao MTA do público alvo, a mensagem será abandonada e será processada na próxima tentativa.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Maximum of parallel Http requests to the FCM initiated by each child server.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Contagem máxima de mensagens por servidor filho. Cada filho do MTA processa esse número de mensagens e morre. É importante especificar um número que permita que os vazamentos de memória ou de recursos no MTA sejam inofensivos (normalmente, alguns milhares). Mesmo que não haja vazamentos de memória conhecidos no código MTA, os mecanismos JavaScript e XSL incorporados não são totalmente confiáveis.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> Mensagens pendentes: número máximo de mensagens que aguardam a entrega da memória. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Tamanho máximo de memória (em MB) que um processo filho pode usar. Acima desse limite, o processo é interrompido para que a memória usada seja liberada no sistema. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> Tempo limite (em segundos) após o qual uma conexão SOAP para um conector de delivery é abandonada.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> Sempre start com o MX de prioridade mais alta.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Número máximo de tentativas consecutivas quando retomadas.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

No nó **mta > filho > smtp** , configure os seguintes parâmetros. Esta é a configuração das sessões SMTP.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enableTLS<br /> </td> 
   <td> Ativa o delivery de emails no modo de segurança (STARTTLS/SMTPS) quando suportado pelo servidor remoto.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> Tempo limite da sessão inativa. Esse parâmetro só é usado se a sessão for reutilizada para transmitir várias mensagens a um determinado domínio. Quando o MTA tiver concluído a transmissão da mensagem, a sessão SMTP que usou não será fechada sistematicamente. Se uma mensagem estiver pronta para ser enviada para esse mesmo domínio, a mesma sessão SMTP será reutilizada e é por isso que a sessão não é fechada automaticamente. O parâmetro IdleSessionTimeout permite definir o tempo durante o qual uma sessão SMTP pode permanecer ativa aguardando outra mensagem. Depois que a duração tiver expirado, a sessão será automaticamente fechada.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> Atraso inicial antes de tentar a conexão novamente. Esse atraso é duplicado sempre que a conexão falha.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> Número máximo de sessões SMTP por servidor filho. Para enviar uma mensagem, o MTA inicializa uma conexão SMTP com o recipient MTA. O número máximo de sessões SMTP simultâneas e ativas para um determinado servidor filho é limitado por esse valor. Se você multiplicar esse valor por maxSpareServers, você obterá o número máximo de mensagens que podem ser processadas simultaneamente por um determinado servidor filho.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

No nó **mta > filho > smtp > IPAffinity** , configure os seguintes parâmetros. Esta é a configuração do gerenciamento do afinidade com endereços IP para tráfego SMTP de saída otimizado.

Para obter informações adicionais, consulte a [Lista de endereços IP para usar](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) e [gerenciar o tráfego SMTP de saída com o afinidade](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Nome do domínio: nome de domínio local vinculado ao endereço IP. Usado ao emitir um comando SMTP HELO.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome lógico: nomes vinculados à afinidade pelos usuários. Os nomes são separados por ponto-e-vírgula;<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
 </tbody> 
</table>

No nó **mta > filho > smtp > IP** , configure os seguintes parâmetros.

Para obter informações adicionais, consulte a [Lista de endereços IP a serem usados](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Endereço físico associado. Por exemplo: "192.168.0.1"<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> ID de endereço público associado. Usado como uma chave para o servidor de estatísticas. Deve ser numérico. See this <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">section</a>.<br /> </td> 
   <td> Longo<br /> </td> 
  </tr> 
  <tr> 
   <td> peso<br /> </td> 
   <td> Especifica a frequência de uso para esse IP, em relação a outros IPs (pesos maiores levam a frequências mais altas).<br /> </td> 
   <td> Longo<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> Lista separada por vírgulas de máscaras de domínio a serem incluídas.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> Lista separada por vírgulas de máscaras de domínio a serem excluídas.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> Nome do computador vinculado ao endereço IP. Usado ao emitir um comando SMTP HELO.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

Estes são os diferentes parâmetros do nó **nmac** . Esta é a configuração de delivery de notificação por push.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> useHTTPProxy<br /> </td> 
   <td> Use o proxy HTTP definido em shared/proxyHTTP. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relé {#relay-1}

Estes são os diferentes parâmetros do nó **nmac > relay** . Isso configura o uso de um relé para o delivery de mensagem (conector ios http2).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Endereço DNS ou nome do relé a ser usado. <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Porta de retransmissão<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> Cadeia de certificados (arquivo PEM). Útil ao usar um servidor modelo.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## tubulação {#pipelined}

Estes são os diferentes parâmetros do nó **pipeline** . Esta é a configuração do módulo de processamento do evento para o Pipeline Services.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> appName<br /> </td> 
   <td> Nome do aplicativo gerado na conexão do Desenvolvedor quando a chave pública é salva. <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parâmetros de start<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> URL para obter um token de gateway.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> Chave privada para obter tokens (criptografada em AES com a opção XtkKey).<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Start automático <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> Desativar autenticação: conecte-se aos serviços de pipeline sem autenticação. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> URL para descobrir o URL dos serviços de pipeline.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Período de salvamento do status: frequência em que as informações internas do processo são salvas em um arquivo. Inativo se 0. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> URL de escuta: forçar o URL de escuta dos serviços de pipeline. <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID do JavaScript a ser executado ao iniciar o processo.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memória: alerta sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Aviso de consumo de memória: aviso sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Porta do servidor de status: A porta do servidor HTTP permite que você query o status do processo. Inativo se 0.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> O ponteiro será armazenado no banco de dados toda vez que esse número de mensagens for processado.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> Atraso antes do ponteiro ser armazenado: o ponteiro será armazenado no banco de dados pelo menos uma vez durante esse período (útil em caso de pouca atividade).<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora do dia em que o processo é reiniciado automaticamente. Consulte Reinicialização <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">automática do processo</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> Número de threads para processamento de eventos com um conector JavaScript personalizado.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> Número de threads para processamento de eventos.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> Atraso entre o processamento se houver uma falha.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> Abandonar após este período: abandone o evento se o processamento ainda estiver falhando após esse período.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridade no start. Os módulos de baixa prioridade são iniciados pela primeira vez e parados pela última vez. O módulo syslogd deve, portanto, ter a prioridade 0.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## reparação {#repair}

Estes são os diferentes parâmetros do nó de **reparo** . Esta é a configuração do módulo de reparo do banco de dados.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> restoreActionDelayMin<br /> </td> 
   <td> Módulo de reparo de ações de delivery: atraso (em minutos) após o qual as ações de delivery podem ser processadas pelo módulo de reparo. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

Estes são os diferentes parâmetros do nó **securityZone** .

Para obter informações adicionais, consulte [Definição de zonas](../../installation/using/configuring-campaign-server.md#defining-security-zones)de segurança.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> allowDebug<br /> </td> 
   <td> Autorize o modo de depuração para Aplicação web.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> Autorize o usuário a usar o aplicativo sem uma senha.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> Autorize o uso de HTTP para logon de operador.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> Autorize o uso de SQLDATA no expressão.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> Autorizar tokens de sessão de usuário/senha.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Rótulo<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome interno<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> Não use o token de segurança.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> Exibir detalhes do erro<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

Esta é a configuração padrão:

```
<securityZone allowDebug="false" allowHTTP="false" allowSQLInjection="false" label="Public Network" name="public">
  <subNetwork name="all" label="All addresses" mask="*" proxy="127.0.0.1, ::1"/>

  <securityZone allowDebug="true" allowHTTP="false" allowSQLInjection="false" label="Private Network (VPN)"
                name="vpn" showErrors="true">

    <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" allowUserPassword="false"
                  allowSQLInjection="false" label="Private Network (LAN)" name="lan" sessionTokenOnly="true"
                  showErrors="true">
      <subNetwork name="lan1" label="Lan 1" mask="192.168.0.0/16" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan2" label="Lan 2" mask="172.16.0.0/12" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan3" label="Lan 3" mask="10.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost" label="Localhost" mask="127.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6"  label="Lan (IPv6)" mask="fc00::/7" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6b" label="Lan (IPv6)" mask="fe80::/10" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost6" label="Localhost (IPv6)" mask="::1/128" proxy="127.0.0.1, ::1"/>
    </securityZone>

  </securityZone>
</securityZone>
```

### subNetwork {#subnetwork}

Estes são os diferentes parâmetros do nó **securityZone > subNetwork** .

Para obter informações adicionais, consulte [Definição de zonas](../../installation/using/configuring-campaign-server.md#defining-security-zones)de segurança.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> label<br /> </td> 
   <td> Rótulo<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> máscara<br /> </td> 
   <td> Máscara ou endereço<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome interno<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> proxy<br /> </td> 
   <td> Máscara ou endereço do proxy (reverso) usado por essa subrede para acessar a instância. Nesse caso, o cabeçalho "X-Forwarded-For" será testado em vez deste proxy.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

Estes são os diferentes parâmetros do nó **sms** . Esta é a configuração do módulo de gerenciamento SMS de entrada.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parâmetros de start<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Start automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> Número máximo de dias de arquivos de trabalho mantidos pelo conector SMPP.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Tamanho máximo em MB dos arquivos de trabalho SMPP.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID do JavaScript a ser executado ao iniciar o processo.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> Recorrência do quadro de continuidade da sessão: máx. período em segundos entre dois quadros para notificar que a sessão de recebimento ainda está ativada.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memória: alerta sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Aviso de consumo de memória: aviso sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Frequência de pesquisa: Período de pesquisa da conta SMS.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora do dia em que o processo é reiniciado automaticamente. Consulte Reinicialização <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">automática do processo</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> Frequência de recarregamento da conta: frequência de recarregamento do banco de dados das contas a serem pesquisadas.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridade no start. Os módulos de baixa prioridade são iniciados pela primeira vez e parados pela última vez. O módulo syslogd deve, portanto, ter a prioridade 0.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> Número de segundos atrasados para o processamento SR: somente SRs com uma data de recuperação anterior à hora atual, menos a duração em segundos fornecida por srReadDelay. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Tempo limite da comunicação com o gateway SMS.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

Estes são os diferentes parâmetros do nó **sms > netsize** .

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> netsizeConnectionTimeout<br /> </td> 
   <td> Tempo limite em segundos ao estabelecer uma conexão com Netsize.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

Estes são os diferentes parâmetros do nó **stat** . Esta é a configuração do módulo de estatísticas MTA.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parâmetros de start<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Start automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID do JavaScript a ser executado ao iniciar o processo.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memória: alerta sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Aviso de consumo de memória: aviso sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Porta de escuta do servidor. See this <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">section</a>.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora do dia em que o processo é reiniciado automaticamente. Consulte Reinicialização <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">automática do processo</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridade no start. Os módulos de baixa prioridade são iniciados pela primeira vez e parados pela última vez. O módulo syslogd deve, portanto, ter a prioridade 0.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

Estes são os diferentes parâmetros do nó **syslogd** . Esta é a configuração do módulo Gerenciamento de registros.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parâmetros de start<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Start automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID do JavaScript a ser executado ao iniciar o processo.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> Tamanho máximo em Mb para um arquivo de log. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> Número máximo de arquivos logins.log a serem mantidos. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memória: alerta sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Aviso de consumo de memória: aviso sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora do dia em que o processo é reiniciado automaticamente. Consulte Reinicialização <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">automática do processo</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridade no start. Os módulos de baixa prioridade são iniciados pela primeira vez e parados pela última vez. O módulo syslogd deve, portanto, ter a prioridade 0.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## tracking {#tracking}

Estes são os diferentes parâmetros do nó de **rastreamento** . Esta é a configuração do servidor de rastreamento.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parâmetros de start<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Start automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> Desative URLs malformados gerados de compilações anteriores.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> ConsolidationPeriodSec<br /> </td> 
   <td> Período de consolidação<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> Desduplicar aberturas: remova logs de rastreamento abertos do duplicado para limitar os efeitos das pré-visualizações de email em leitores de email como o Outlook.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Ignorar até X% dos erros: não atualize os indicadores de rastreamento, desde que a proporção de journais que ainda não foram considerados não atinja esse valor. <br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> Atualizar indicadores de erro: duração máxima antes da recomposição dos indicadores de erro.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> Calcular indicadores durante: a duração após a data de validade de um delivery, após a qual os indicadores consolidados deixam de ser calculados.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID do JavaScript a ser executado ao iniciar o processo <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> Número de registros solicitados por chamada para o servidor de rastreamento remoto.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memória: alerta sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Aviso de consumo de memória: aviso sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> Chave de API para a Integração do Endpoint Service do Phishbowl. Isso protege o redirecionamento de URLs malformados gerados de construções mais antigas. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Endpoint para a integração do Endpoint Service do Phishbowl. Isso protege o redirecionamento de URLs malformados gerados de construções mais antigas.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora do dia em que o processo é reiniciado automaticamente. Consulte Reinicialização <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">automática do processo</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridade no start. Os módulos de baixa prioridade são iniciados pela primeira vez e parados pela última vez. O módulo syslogd deve, portanto, ter a prioridade 0.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Ignorar até X% do rastreamento: não atualize os indicadores de rastreamento, desde que a proporção de journais que ainda não foram considerados não atinja esse valor.<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Atualizar indicadores de rastreamento: duração máxima antes de os indicadores de rastreamento serem recomendados.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Tamanho do cache do identificador do navegador.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

Estes são os diferentes parâmetros do nó **trackinglogd** . Esta é a configuração do daemon de gravação do log de rastreamento.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parâmetros de start<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Start automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID do JavaScript a ser executado ao iniciar o processo <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> Máximo de tentativas de escrita: número máximo de arquivos que podem ser criados em caso de falha de gravação em arquivos de log.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Tamanho máximo do log: espaço máximo usado pelos logs no disco (em MB). Não pode ser inferior a 100 MB. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memória: alerta sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Aviso de consumo de memória: aviso sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Contagem máxima de log: número máximo de registros armazenados na memória compartilhada. Não pode ser menor que 10000. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora do dia em que o processo é reiniciado automaticamente. Consulte Reinicialização <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">automática do processo</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Número de registros antes da remoção: número de registros inseridos antes de iniciar a remoção de arquivos de log. Não pode ser inferior a 50000.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridade no start. Os módulos de baixa prioridade são iniciados pela primeira vez e parados pela última vez. O módulo syslogd deve, portanto, ter a prioridade 0.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> Número máximo de caracteres salvos na memória compartilhada para parâmetros de rastreamento da Web adicionais.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

Estes são os diferentes parâmetros do nó **da Web** . Esta é a configuração do Módulo Web.

For additional information, refer to this [section](../../installation/using/configuring-campaign-server.md#default-port-for-tomcat).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> JVMOoptions<br /> </td> 
   <td> As opções da JVM foram passadas como uma string.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThreads<br /> </td> 
   <td> Maximum number of threads.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> Número mínimo de threads.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parâmetros de start<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Start automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Porta de controle de escuta Tomcat: consulte <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Configuração do Tomcat</a>.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Porta de escuta HTTP Tomcat: consulte <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Configuração do Tomcat</a>.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID do JavaScript a ser executado ao iniciar o processo.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> Tamanho da fila para chamadas de SubmitDelivery: número máximo de chamadas SOAP SubmitDelivery que podem ser enfileiradas.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memória: alerta sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Aviso de consumo de memória: aviso relativo à quantidade de RAM consumida (em MB) por um determinado processo<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Retransmissão de notificação: HostName:Porta que habilita o relé de notificações.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora do dia em que o processo é reiniciado automaticamente. Consulte Reinicialização <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">automática do processo</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridade no start. Os módulos de baixa prioridade são iniciados pela primeira vez e parados pela última vez. O módulo syslogd deve, portanto, ter a prioridade 0.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> Start o roteador SOAP no modo de módulo.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

Estes são os diferentes parâmetros do nó **web > jsp** . Essa é a configuração dos parâmetros usados pelos JSPs.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debug<br /> </td> 
   <td> Execução do JSP no modo de depuração ou não.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> Pasta de download: caminho de download dos programas de instalação para os consoles cliente.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> Caminho do arquivo .fo.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> URL do roteador SOAP (http://myserver/xxx, http://jni ou mailto:xxx).<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

O nó **web > jsp > classpath** contém a lista de todos os caminhos de classe a serem usados ao iniciar o JVM. Esta é a configuração padrão:

```
'$(XTK_INSTALL_DIR)/tomcat-7/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-7/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/el-api.jar
          $(XTK_INSTALL_DIR)/java/lib/log4j-1.2.11.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat7-websocket.jar
          $(XTK_INSTALL_DIR)/java/lib/pdfbox-2.0.4.jar
          $(XTK_INSTALL_DIR)/java/lib/FontBox-0.1.0.jar
          $(XTK_INSTALL_DIR)/java/lib/AGJavaEndpoint.22.jar
          $(XTK_INSTALL_DIR)/java/lib/NSGConstants.jar
          $(XTK_INSTALL_DIR)/java/lib/smpp.jar
          $(XTK_INSTALL_DIR)/java/lib/nlweb.jar
          $(XTK_INSTALL_DIR)/java/lib/jcaptcha-all.jar
          $(XTK_INSTALL_DIR)/java/lib/apns-1.0.0.Beta6-jar-with-dependencies.jar
          $(XTK_INSTALL_DIR)/java/lib/commons-collections-3.2.2.jar
          $(XTK_INSTALL_DIR)/java/lib/jcommon-1.0.16.jar
          $(XTK_INSTALL_DIR)/java/lib/jfreechart-1.0.13.jar
          $(XTK_INSTALL_DIR)/java/lib/barcode4j-light.jar
          $(XTK_INSTALL_DIR)/java/lib/zxing.jar
          $(XTK_INSTALL_DIR)/java/lib/raztec.jar
          $(XTK_INSTALL_DIR)/java/lib/gson-2.7.jar
          $(XTK_INSTALL_DIR)/java/lib/alpn-api-1.1.3.v20160715.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-all-4.1.6.Final.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-tcnative-boringssl-static-1.1.33.Fork22.jar
          $(XTK_INSTALL_DIR)/java/lib/pushy-0.8.1.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-api-1.7.21.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-simple-1.7.21.jar'
```

### jssp {#jssp}

Estes são os diferentes parâmetros do nó **web > jssp** . Essa é a configuração dos parâmetros usados pelos JSSPs.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> collectsGarbageAfterRequest<br /> </td> 
   <td> Ativa o coletor de lixo do contexto JavaScript após cada query.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Número máximo de páginas servidas por um contexto JavaScript. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

O nó **web > jsp > classpath** contém a lista de todos os caminhos de classe a serem usados ao iniciar o JVM.

### relé {#relay-2}

Estes são os diferentes parâmetros do nó **web > relay** . Esta é a configuração do relay para solicitações HTTP entre duas zonas.

For additional information, refer to this [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debugRelay<br /> </td> 
   <td> Start o módulo de retransmissão HTTP no servidor Web no modo de depuração.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> Caracteres proibidos (Domínio): lista de caracteres proibidos na seção 'autoridade' de um URI.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> Caracteres proibidos (Caminho): lista de caracteres proibidos na seção 'path' de um URI.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> Valor da opção do módulo 'mod_dir': lista de arquivos a serem usados durante um query em uma pasta.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> Start do módulo HTTP relay.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> Start o módulo de retransmissão HTTP no servidor Web. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Tempo de espera antes de excluir o url banido.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Adicione um nó **web > relé > url** para cada URL para retransmitir (a ordem de inserção define a prioridade) com os seguintes parâmetros.

Para obter informações adicionais, consulte Segurança de página [dinâmica e relés](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) e [seção](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IPMask<br /> </td> 
   <td> IPs autorizados: lista separada por vírgulas de endereços IP de origem permitido usar o relé para essa máscara.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> negar<br /> </td> 
   <td> Negar acesso a esses URLs (retornar um erro HTTP 403)<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> Alias DNS para retransmitir: lista separada por vírgulas de máscaras de alias DNS para retransmissão (ex: '*.adobe.com').<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> O acesso HTTP é autorizado independentemente da zona de segurança (como webApps). <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> Adicionar host original: use o cabeçalho HTTP 'Host' da solicitação original ao reproduzir.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> Adicionar caminho de URL inicial: anexe o caminho completo dos URLs para retransmitir ao URL da página do público alvo. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> status<br /> </td> 
   <td> Status de sincronização de um recurso público (lista discriminada). Os valores possíveis são "normal" (execução normal), "blacklist" (url adicionado à lista de bloqueios em caso de erro 404) e "spare" (upload de arquivo no servidor sobressalente, se houver).<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> URL da página do público alvo: consulte <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Configuração do Tomcat</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Tempo máximo de execução (em segundos) da solicitação sendo retransmitida.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> Máscara de URLs para retransmissão (por exemplo: '/nl*', '*.jsp').<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Esta é a configuração padrão:

```
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true"
     status="normal" targetUrl="http://localhost:7781" timeout="" urlPath="/pipelined/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/view/*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="*ooconv.jsp*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/res/*.jsp*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/sc.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/interactionProposal.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/zoneJson.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/barcode.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/captcha.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/webForm.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/xtk/jsp/zoneinfo.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/facebookCallback.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/m.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/s.jsp"/>

<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nms/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/xtk/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nl/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="*.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="true" urlPath="/webApp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/report/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/jssp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/strings/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/interaction/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/barcode/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/lineImage/*"/>

<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/favicon.*"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.md"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.png"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.jpg"/>
```

Adicione um nó **web > relay > responseHeader** para cada cabeçalho HTTP para adicionar às respostas encaminhadas ao relé.

Para obter informações adicionais, consulte [Gerenciamento de cabeçalhos](../../installation/using/configuring-campaign-server.md#managing-http-headers)HTTP.

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome do cabeçalho<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
  <tr> 
   <td> value<br /> </td> 
   <td> Valor do cabeçalho <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
 </tbody> 
</table>

Esta é a configuração padrão:

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### redirecionamento {#redirection}

Estes são os diferentes parâmetros do nó **web > redirecionamento** . Esta é a configuração do módulo de redirecionamento.

For additional information, refer to this [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IMSOrgId<br /> </td> 
   <td> Identificador da organização IMS: identificador de organização único na Adobe Marketing Cloud, usado especialmente para o serviço VisitorID e o SSO IMS. <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Valor que descreve a política usada para cookies permanentes (em conformidade com o formato P3P Compact Policy). <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 'CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Lista separada por vírgulas de domínios a serem configurados para indicar explicitamente seu domínio para definir cookie. <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Identificador de banco de dados associado à instância de rastreamento.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Contagem de registros por chamada: número de registros retornados por padrão após uma chamada do método GetTrackingLogs.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> Página para redirecionamentos expirados: URL da página da Web usada por padrão pelo servidor de redirecionamento quando o redirecionamento de uma ação de delivery expira.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> Contagem máxima de trabalhos: número máximo de ações de delivery no cache. Não pode ser inferior a 50. <br /> </td> 
   <td> Longo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirects<br /> </td> 
   <td> Start do serviço de redirecionamento.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectsInModule<br /> </td> 
   <td> Start o serviço de redirecionamento no modo de módulo.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Rastreamento web: criação de logs para as páginas visitadas pelos usuários desconhecidos. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> Senha usada pelo servidor de redirecionamento.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Estes são os diferentes parâmetros do nó **web > redirecionamento > spareServer** .

Para obter informações adicionais, consulte Rastreamento [redundante](../../installation/using/configuring-campaign-server.md#redundant-tracking).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabledIf<br /> </td> 
   <td> Tomado em consideração se: o servidor de rastreamento será considerado se a expressão retornar true. <br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> id<br /> </td> 
   <td> Nome<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL do servidor de redirecionamento extra<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

Estes são os diferentes parâmetros do nó **web > spamCheck** . Esta é a configuração dos parâmetros de avaliação de pontuação antisspam de email.

Para obter informações adicionais, consulte [Configurando o SpamAssassin](../../installation/using/configuring-spamassassin.md).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> comando<br /> </td> 
   <td> Comando para executar para avaliar a pontuação antisspam de um email (por exemplo, 'perl spamcheck.pl').<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

Estes são os diferentes parâmetros do nó **wfserver** . Esta é a configuração do processo de fluxo de trabalho.

Para obter informações adicionais, consulte workflows e afinidades de [alta disponibilidade](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parâmetro </th> 
   <th> Descrição </th> 
   <th> Tipo </th> 
   <th> Valor padrão </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> affinity<br /> </td> 
   <td> Afinidade<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parâmetros de start<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Start automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Período<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID do JavaScript a ser executado ao iniciar o processo.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memória: alerta sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Aviso de consumo de memória: aviso sobre a quantidade de RAM consumida (em Mb) por um determinado processo.<br /> </td> 
   <td> Longo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Retransmissão de notificação: HostName:Porta que habilita o relé de notificações.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora do dia em que o processo é reiniciado automaticamente. Consulte Reinicialização <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">automática do processo</a>.<br /> </td> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridade no start. Os módulos de baixa prioridade são iniciados pela primeira vez e parados pela última vez. O módulo syslogd deve, portanto, ter a prioridade 0.<br /> </td> 
   <td> Curto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

