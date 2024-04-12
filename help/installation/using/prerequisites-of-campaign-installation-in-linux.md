---
product: campaign
title: Pré-requisitos da instalação do Campaign no Linux
description: Pré-requisitos da instalação do Campaign no Linux
feature: Installation, Instance Settings
badge-v7-prem: label="No local e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 1%

---

# Pré-requisitos para instalar o Campaign no Linux{#prerequisites-of-campaign-installation-in-linux}



## Pré-requisitos de software {#software-prerequisites}

Esta seção detalha as etapas preliminares de configuração necessárias antes de instalar o Adobe Campaign.

A configuração técnica e de software necessária para instalar o Adobe Campaign está detalhada na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

Lembrando que os seguintes componentes precisam ser instalados e configurados corretamente:

* Apache, consulte Compatibilidade [matriz](../../rn/using/compatibility-matrix.md),
* Java JDK e OpenJDK, consulte [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotecas, consulte [Bibliotecas](#libraries),
* Camadas de acesso ao banco de dados, consulte camadas](#database-access-layers) de acesso ao [Banco de dados,
* LibreOffice, consulte [Instalação do LibreOffice para Debian](#installing-libreoffice-for-debian) e [Instalação do LibreOffice para CentOS](#installing-libreoffice-for-centos),
* Fontes, consulte [Fontes para estatísticas de MTA](#fonts-for-mta-statistics) e [Fontes para instâncias japonesas](#fonts-for-japanese-instances).

>[!NOTE]
>
>Para instalar uma build inferior ou igual a 8709 nas plataformas CentOS 7 e Debian 8, o módulo apache access_compat deve estar habilitado.

### Bibliotecas {#libraries}

Para instalar o Adobe Campaign no Linux, verifique se você tem as bibliotecas necessárias.

* A biblioteca C deve ser capaz de suportar o modo TLS (Thread Local Storage). Esse modo está ativo na maioria dos casos, exceto com alguns kernels para os quais o suporte Xen foi desativado.

  Para verificar isso, você pode usar o comando uname -a **| grep xen** , por exemplo.

  Se o comando não retornar nada (linha vazia), significa que a configuração está correta.

* É necessário ter a versão OpenSSL **1.0.2** ou superior.

  Para distribuições RHEL 7/8, é necessária a versão 1.0 do OpenSSL.

* Para usar o Adobe Campaign, você precisa ter a **libicu** biblioteca instalada.

  As seguintes versões de **libicu** são compatíveis (32 ou 64 bits):

   * RHEL 7/8, CentOS 7: libicu50
   * Debian 8: libicu52
   * Debian 9: libicu57

  Para usar o Adobe Campaign, você precisa ter a biblioteca libc-ares instalada. No RHEL/CentOS, execute o seguinte comando:

  ```
  yum install c-ares
  ```

  No Debian:

  ```
  aptitude install libc-ares2
  ```

### Selinux {#selinux}

Quando usada, a módulo do SELinux deve ser configurada corretamente.

Para fazer isso, faça logon como root e insira o seguinte comando:

```
echo 0 >/selinux/enforce
```

Além disso, no **/etc/sysconfig/httpd** , a seguinte linha foi adicionada para fazer referência ao script de configuração do ambiente Adobe Campaign:

```
. ~neolane/nl6/env.sh
```

No RHEL e no CentOS, problemas de compatibilidade com as camadas de cliente dos bancos de dados eram observados quando o SELinux estava habilitado. Para ter certeza de que o Adobe Campaign pode operar corretamente, recomendamos desativar o SELinux.

**Aplique o seguinte processo:**

* Editar o arquivo **/etc/selinux/config**

* Modifique a linha SELINUX da seguinte maneira:

```
SELINUX=disabled
```

### Fontes para estatísticas do MTA {#fonts-for-mta-statistics}

Em solicitar para que relatórios de estatísticas MTA (nms/fra/jsp/stat.jsp) sejam exibidos corretamente, adicione fontes.

Em Debian, adicione o comando:

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Em Redhat, use o seguinte comando:

* Para CentOS/RHEL 7:

  ```
  yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
  ```

* Para o RHEL 8:

  ```
  dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
  ```

### Fontes para instâncias japonesas {#fonts-for-japanese-instances}

As fontes de caracteres específicos são necessárias para as instâncias japonesas para exportar os relatórios para o formato PDF.

No Debian, adicione o comando:

```
aptitude install fonts-ipafont
```

Na Red Hat, adicione o comando:

* Para RHEL 7:

  ```
  yum install ipa-gothic-fonts ipa-mincho-fonts
  ```

* Para RHEL 8:

  ```
  dnf install vlgothic-fonts
  ```

### Instalação do LibreOffice para Debian {#installing-libreoffice-for-debian}

Para Debian, as seguintes configurações são necessárias:

1. Instale os seguintes pacotes padrão:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Instale as seguintes fontes (opcional, mas altamente recomendado para instâncias japonesas):

   ```
   apt-get install fonts-ipafont
   ```

### Instalação do LibreOffice para CentOS {#installing-libreoffice-for-centos}

As seguintes configurações são necessárias com o CentOS:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Camadas de acesso ao banco de dados {#database-access-layers}

As camadas de acesso do mecanismo de banco de dados que você está usando devem estar instaladas no servidor e acessíveis por meio da conta do Adobe Campaign. As versões e os modos de instalação podem variar dependendo do mecanismo de banco de dados usado.

A versão piloto compatível está detalhada no [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

Verifique também o [Banco de dados](../../installation/using/database.md) seção.

### PostgreSQL {#postgresql}

O Adobe Campaign é compatível com todas as versões das bibliotecas de clientes PostgreSQL da versão 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** e **libpq.so.3.1**).

O uso do PostgreSQL com o Adobe Campaign também requer a instalação do correspondente **pgcrypto** bibliotecas.

### Oracle {#oracle}

Recupere a versão da biblioteca para Debian de 64 bits, ou seja: **libclntsh.so**, **libclntsh.so.11.1** e **libclntsh.so.10.1**.

Obtenha um pacote RPM de Linux na Oracle Technology Network.

>[!NOTE]
>
>Se você já tiver instalado o cliente do Oracle, mas o ambiente global (por exemplo: /etc/profile) não estiver configurado corretamente, você poderá adicionar as informações ausentes à **nl6/customer.sh** script Para obter mais informações, consulte [Variáveis de ambiente](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Resolução de problemas e práticas recomendadas**

Os problemas podem aparecer após um cliente Oracle ou uma atualização do servidor, alteração de versão ou na primeira instalação do instância.

Se você perceber no console do cliente que há atrasos de tempo inesperados (uma ou mais horas) em logs, fluxo de Trabalho último processamento, próximo processamento e assim por diante, pode haver uma problema entre os biblioteca do cliente Oracle e do Oracle Server. Para evitar esses problemas

1. Certifique-se de usar o **cliente completo**.

   Vários problemas foram identificados ao usar a versão do Oracle Instant Client. Além disso, é impossível alterar o arquivo de fuso horário no cliente instantâneo.

1. Certifique-se de que a variável **versão do cliente** e a variável **versão do servidor de banco de dados** são as **igual**.

   A combinação de versões apesar da matriz de compatibilidade do Oracle e da recomendação para alinhar as versões de cliente e servidor é conhecida por causar problemas.

   Verifique também ORACLE_HOME valor para garantir que ele aponte para a versão de cliente esperada (caso várias versões estejam instaladas na máquina).

1. Certifique-se de que o cliente e o servidor usem o mesmo **arquivo** de fuso horário.

### DB2 {#db2}

A versão biblioteca suportada é **libdb2.so**.

## Etapas de implementação {#implementation-steps}

As instalações do Adobe Campaign para Linux devem ser realizadas na seguinte sequência: instalação do servidor seguida de configuração da instância.

O processo de instalação é descrito neste capítulo. As etapas de instalação são as seguintes:

* Etapa 1: instalação do servidor de aplicativos, consulte [Instalação de pacotes com Linux](../../installation/using/installing-packages-with-linux.md).
* Etapa 2: Integração com um servidor Web (opcional, dependendo dos componentes implantados).

Quando as etapas de instalação estiverem concluídas, você precisará configurar as instâncias, o banco de dados e o servidor. Para obter mais informações, consulte [Sobre a configuração inicial](../../installation/using/about-initial-configuration.md).
