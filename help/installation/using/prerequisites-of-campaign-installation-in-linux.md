---
product: campaign
title: Pré-requisitos da instalação do Campaign no Linux
description: Pré-requisitos da instalação do Campaign no Linux
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 1%

---

# Pré-requisitos para instalar o Campaign no Linux{#prerequisites-of-campaign-installation-in-linux}

![](../../assets/v7-only.svg)

## Pré-requisitos de software {#software-prerequisites}

Esta seção detalha as etapas preliminares necessárias antes da instalação do Adobe Campaign.

A configuração técnica e de software necessária para instalar o Adobe Campaign está detalhada no [Matriz de Compatibilidade](../../rn/using/compatibility-matrix.md).

Como lembrete, os seguintes componentes precisam ser instalados e configurados corretamente:

* Apache, consulte [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md),
* Java JDK e OpenJDK, consulte [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotecas, consulte [Bibliotecas](#libraries),
* Camadas de acesso ao banco de dados, consulte [Camadas de acesso ao banco de dados](#database-access-layers),
* LibreOffice, consulte [Instalando o LibreOffice para Debian](#installing-libreoffice-for-debian) e [Instalando o LibreOffice para CentOS](#installing-libreoffice-for-centos),
* Fontes, consulte [Fontes para estatísticas MTA](#fonts-for-mta-statistics) e [Fontes para instâncias japonesas](#fonts-for-japanese-instances).

>[!NOTE]
>
>Para instalar uma build menor ou igual a 8709 em plataformas CentOS 7 e Debian 8, o módulo apache access_compat deve estar habilitado.

### Bibliotecas {#libraries}

Para instalar o Adobe Campaign no Linux, verifique se você tem as bibliotecas necessárias.

* A Biblioteca C deve ser capaz de suportar o modo TLS (Thread Local Storage). Esse modo está ativo na maioria dos casos, exceto em alguns kernels para os quais o suporte ao Xen foi desativado.

   Para verificar isso, você pode usar o **uname -a | grep xen** por exemplo.

   Se o comando não retornar nada (linha vazia), significa que a configuração está correta.

* Você deve ter **versão 0.9.8** ou **1.0** de OpenSSL.

   Para distribuições RHEL 7, é necessária a versão 1.0 do OpenSSL.

* Para usar o Adobe Campaign, você precisa ter a biblioteca **libicu** instalada.

   As seguintes versões de **libicu** são compatíveis (32 bits ou 64 bits):

   * RHEL 7, CentOS 7: libicu50
   * Debian 8: libicu52
   * Debian 9: libicu57

   Para usar o Adobe Campaign, é necessário ter a biblioteca libc-ares instalada. Em RHEL/CentOS, execute o seguinte comando:

   ```
   yum install c-ares
   ```

   No Debian:

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

Quando usado, o módulo SELinux deve ser configurado corretamente.

Para fazer isso, faça logon como root e insira o seguinte comando:

```
echo 0 >/selinux/enforce
```

Além disso, no arquivo **/etc/sysconfig/httpd**, a linha a seguir foi adicionada para fazer referência ao script de configuração de ambiente do Adobe Campaign:

```
. ~neolane/nl6/env.sh
```

No RHEL e no CentOS, foram observados problemas de compatibilidade com as camadas de clientes de bancos de dados quando o SELinux está ativado. Para garantir que o Adobe Campaign possa operar corretamente, recomendamos desativar o SELinux.

**Aplique o seguinte processo:**

* Edite o arquivo **/etc/selinux/config**

* Modifique a linha SELINUX da seguinte maneira:

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

### Fontes para instâncias japonesas {#fonts-for-japanese-instances}

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

Para Debian, as seguintes configurações são necessárias:

1. Instale os seguintes pacotes padrão:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Instale as seguintes fontes (opcional, mas altamente recomendado para instâncias em japonês):

   ```
   apt-get install fonts-ipafont
   ```

### Instalação do LibreOffice para CentOS {#installing-libreoffice-for-centos}

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

As camadas de acesso do mecanismo de banco de dados que você está usando devem ser instaladas no servidor e acessíveis pela conta do Adobe Campaign. As versões e os modos de instalação podem variar dependendo do mecanismo de banco de dados usado.

A versão piloto suportada está detalhada na [Matriz de Compatibilidade](../../rn/using/compatibility-matrix.md).

Verifique também a seção geral [Database](../../installation/using/database.md).

### PostgreSQL {#postgresql}

O Adobe Campaign suporta todas as versões das bibliotecas de clientes PostgreSQL da versão 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** e **libpq.so.3.1**).

O uso do PostgreSQL com Adobe Campaign também requer a instalação das bibliotecas **pgcrypto** correspondentes.

### Oracle {#oracle}

Recupere a versão da biblioteca para o Debian de 64 bits, ou seja: **libclntsh.so**, **libclntsh.so.11.1** e **libclntsh.so.10.1**.

Você pode obter um pacote RPM de Linux da Rede de tecnologia de Oracle.

>[!NOTE]
>
>Se você já tiver instalado o cliente Oracle, mas o ambiente global (por exemplo: /etc/profile) não estiver configurado corretamente, você pode adicionar informações ausentes ao script **nl6/customer.sh** Para obter mais informações, consulte [Variáveis de ambiente](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Resolução de problemas e práticas recomendadas**

Os problemas podem aparecer após um cliente do Oracle ou uma atualização do servidor, alteração da versão ou na primeira instalação da instância.

Se você observar no console do cliente que há atrasos inesperados (uma ou mais horas) nos logs, no último processamento do fluxo de trabalho, no próximo processamento e assim por diante, pode haver um problema entre a biblioteca do cliente Oracle e o Servidor Oracle. Para evitar esses problemas

1. Certifique-se de usar o **cliente completo**.

   Vários problemas foram identificados ao usar a versão do Oracle Instant Client. Além disso, é impossível alterar o arquivo de Fuso horário no cliente instantâneo.

1. Certifique-se de que a **versão do cliente** e a **versão do servidor de banco de dados** sejam as **mesmas**.

   A mistura de versões, apesar da matriz de compatibilidade do Oracle e da recomendação para alinhar as versões do cliente e do servidor, é conhecida por causar problemas.

   Verifique também o valor ORACLE_HOME para garantir que ele aponte para a versão do cliente esperada (caso várias versões estejam instaladas na máquina).

1. Certifique-se de que o cliente e o servidor usam o mesmo **arquivo de fuso horário**.

### DB2 {#db2}

A versão da biblioteca compatível é **libdb2.so**.

## Etapas de implementação {#implementation-steps}

As instalações Adobe Campaign para Linux devem ser executadas na seguinte sequência: instalação do servidor seguida pela configuração da instância.

O processo de instalação é descrito neste capítulo. As etapas de instalação são as seguintes:

* Etapa 1: Instalando o servidor de aplicativos, consulte [Instalação de pacotes com Linux](../../installation/using/installing-packages-with-linux.md).
* Etapa 2: Integração com um servidor da Web (opcional, dependendo dos componentes implantados).

Depois que as etapas de instalação forem concluídas, será necessário configurar as instâncias, o banco de dados e o servidor. Para obter mais informações, consulte [Sobre a configuração inicial](../../installation/using/about-initial-configuration.md).
