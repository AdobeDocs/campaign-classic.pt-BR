---
title: Pré-requisitos da instalação do Campaign no Linux
seo-title: Pré-requisitos da instalação do Campaign no Linux
description: Pré-requisitos da instalação do Campaign no Linux
seo-description: null
page-status-flag: never-activated
uuid: 65c7af3f-ca1d-4255-b54a-6a3c83af40ae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 3e2ccb70-6c0c-435f-9c06-f3e5e40367bb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8ad1a83d40f5a841b01aaeb17fe271b44f2480dd

---


# Pré-requisitos da instalação do Campaign no Linux{#prerequisites-of-campaign-installation-in-linux}

## Pré-requisitos de software {#software-prerequisites}

Esta seção detalha as etapas de configuração preliminares necessárias antes da instalação do Adobe Campaign.

A configuração técnica e de software necessária para instalar o Adobe Campaign está detalhada na matriz [de compatibilidade](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Como lembrete, os seguintes componentes precisam ser instalados e configurados corretamente:

* Apache, consulte a matriz [de compatibilidade](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html),
* Java JDK e OpenJDK, consulte o Kit de desenvolvimento [Java - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotecas, referência às [bibliotecas](#libraries),
* camadas de acesso ao banco de dados, referência a camadas [de acesso ao](#database-access-layers)banco de dados,
* LibreOffice, consulte [Instalação do LibreOffice para Debian](#installing-libreoffice-for-debian) e [Instalação do LibreOffice para CentOS](#installing-libreoffice-for-centos),
* Fontes, consulte [Fontes para estatísticas](#fonts-for-mta-statistics) MTA e [Fontes para instâncias](#fonts-for-japanese-instances)japonesas.

>[!NOTE]
>
>Para instalar uma compilação menor ou igual a 8709 nas plataformas CentOS 7 e Debian 8, o módulo apache access_compat deve estar habilitado.

### Bibliotecas {#libraries}

Para instalar o Adobe Campaign no Linux, verifique se você tem as bibliotecas necessárias.

* A biblioteca C deve ser capaz de suportar o modo TLS (Thread Local Storage, Armazenamento de Thread Local). Esse modo está ativo na maioria dos casos, exceto em alguns kernels para os quais o suporte Xen foi desativado.

   Para verificar isso, você pode usar o **nome -a| comando grep xen** , por exemplo.

   Se o comando não retornar nada (linha vazia), isso significa que a configuração está correta.

* Você deve ter a **versão 0.9.8** ou **1.0** do OpenSSL.

   Para distribuições RHEL 7 e CentOS 6, é necessária a versão 1.0 do OpenSSL.

* Para usar o Adobe Campaign, é necessário ter a biblioteca de **libicu** instalada.

   As seguintes versões de **libicu** são compatíveis (32 bits ou 64 bits):

   * RHEL 6, SLES, CentOS 6: libicu4.2
   * RHEL 7, CentOS 7: libicu50
   * Debian 7: libicu48
   * Debian 8: libicu52
   * Debian 9: libicu57
   Para usar o Adobe Campaign, é necessário ter a biblioteca libc-ares instalada. Em RHEL/CentOS, execute o seguinte comando:

   ```
   yum install c-ares
   ```

   Em Debian:

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

Quando usado, o módulo SELinux deve ser configurado corretamente.

Para fazer isso, faça logon como raiz e insira o seguinte comando:

```
echo 0 >/selinux/enforce
```

Além disso, no arquivo **/etc/sysconfig/httpd** , a seguinte linha foi adicionada para fazer referência ao script de configuração do ambiente do Adobe Campaign:

```
. ~neolane/nl6/env.sh
```

No RHEL e no CentOS, foram observados problemas de compatibilidade com as camadas de clientes de bancos de dados quando o SELinux está ativado. Para ter certeza de que o Adobe Campaign está apto a funcionar corretamente, recomendamos desativar o SELinux.

**Aplique o seguinte processo:**

* Editar o arquivo **/etc/selinux/config**

* Modifique a linha SELINUX da seguinte forma:

```
SELINUX=disabled
```

### Fontes para estatísticas MTA {#fonts-for-mta-statistics}

Para que os relatórios sobre estatísticas MTA (nms/fra/jsp/stat.jsp) sejam exibidos corretamente, adicione fontes.

Em Debian, adicione o comando:

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

No Redhat, use o seguinte comando:

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### Fontes para instâncias em japonês {#fonts-for-japanese-instances}

Fontes de caracteres específicos são necessárias para as instâncias japonesas a fim de exportar os relatórios para o formato PDF.

Em Debian, adicione o comando:

```
aptitude install fonts-ipafont
```

Em Red Hat, adicione o comando:

```
yum install ipa-gothic-fonts ipa-mincho-fonts
```

### Instalação do LibreOffice para Debian {#installing-libreoffice-for-debian}

Para Debian, as seguintes configurações são obrigatórias:

1. Instale os seguintes pacotes padrão:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Instale as seguintes fontes (opcional, mas altamente recomendado para instâncias em japonês):

   ```
   apt-get install fonts-ipafont
   ```

### Instalando o LibreOffice para CentOS {#installing-libreoffice-for-centos}

As seguintes configurações são necessárias com o CentOS:

1. Instale os seguintes pacotes padrão:

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. Instale as seguintes fontes (opcional, mas altamente recomendado para instâncias em japonês):

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## Camadas de acesso ao banco de dados {#database-access-layers}

As camadas de acesso para o mecanismo de banco de dados que você está usando devem ser instaladas no servidor e estar acessíveis por meio da conta do Adobe Campaign. As versões e os modos de instalação podem variar dependendo do mecanismo de banco de dados usado.

A versão piloto suportada está detalhada na matriz [Compatibilidade](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Verifique também a seção [Banco de Dados](../../installation/using/database.md) geral.

### PostgreSQL {#postgresql}

O Adobe Campaign oferece suporte a todas as versões das bibliotecas de clientes PostgreSQL da versão 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** e **libpq.so.3.1**).

Usar o PostgreSQL com o Adobe Campaign também requer a instalação das bibliotecas **pgcrypto** correspondentes.

### Oracle {#oracle}

Recuperar a versão da biblioteca para Debian de 64 bits, ou seja: **libclntsh.so**, **libclntsh.so.11.1** e **libclntsh.so.10.1**.

Você pode obter um pacote RPM Linux da Oracle Technology Network.

>[!NOTE]
>
>Se você já tiver instalado o cliente Oracle, mas o ambiente global (por exemplo: /etc/profile) não está configurado corretamente, você pode adicionar informações ausentes ao script **nl6/customer.sh** Para obter mais informações, consulte as variáveis [de](../../installation/using/installing-packages-with-linux.md#environment-variables)Ambiente.

**Solução de problemas e práticas recomendadas**

Os problemas podem aparecer após um cliente Oracle ou uma atualização do servidor, alteração da versão ou na primeira instalação da instância.

Se você perceber no console do cliente que há períodos de tempo inesperados (uma ou mais horas) nos logs, no último processamento do fluxo de trabalho, no próximo processamento e assim por diante, pode haver um problema entre a biblioteca do cliente Oracle e o Oracle Server. Para evitar esses problemas

1. Certifique-se de usar o cliente **** completo.

   Vários problemas foram identificados ao usar a versão do Oracle Instant Client. Além disso, é impossível alterar o arquivo de fuso horário no cliente instantâneo.

1. Verifique se a versão **do** cliente e a versão **do servidor de** banco de dados são as **mesmas**.

   A combinação de versões apesar da matriz de compatibilidade e da recomendação da Oracle para alinhar as versões de cliente e servidor é conhecida por causar problemas.

   Verifique também o valor ORACLE_HOME para garantir que ele aponte para a versão esperada do cliente (caso várias versões estejam instaladas no computador).

1. Verifique se o cliente e o servidor usam o mesmo arquivo **de** fuso horário.

### DB2 {#db2}

A versão da biblioteca suportada é **libdb2.so**.

## Etapas de implementação {#implementation-steps}

As instalações do Adobe Campaign para Linux devem ser executadas na seguinte sequência: instalação do servidor seguida da configuração da instância.

O processo de instalação é descrito neste capítulo. As etapas de instalação são as seguintes:

* Etapa 1: Instalação do servidor de aplicativos, consulte [Instalação de pacotes com Linux](../../installation/using/installing-packages-with-linux.md).
* Etapa 2: Integração com um servidor Web (opcional, dependendo dos componentes implantados).

Quando as etapas de instalação estiverem concluídas, será necessário configurar as instâncias, o banco de dados e o servidor. For more on this, refer to [About initial configuration](../../installation/using/about-initial-configuration.md).
