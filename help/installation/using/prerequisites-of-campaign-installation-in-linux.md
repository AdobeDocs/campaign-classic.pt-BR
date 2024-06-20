---
product: campaign
title: Pré-requisitos da instalação do Campaign no Linux
description: Pré-requisitos da instalação do Campaign no Linux
feature: Installation, Instance Settings
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 1%

---

# Pré-requisitos para instalar o Campaign no Linux{#prerequisites-of-campaign-installation-in-linux}

## Pré-requisitos de software {#software-prerequisites}

Esta seção detalha as etapas preliminares de configuração necessárias antes de instalar o Adobe Campaign.

A configuração técnica e de software necessária para instalar o Adobe Campaign está detalhada na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

Lembrando que os seguintes componentes precisam ser instalados e configurados corretamente:

* Apache, consulte [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md),
* Java JDK e OpenJDK, consulte [Java Development Kit - JDK](../../installation/using/application-server.md#jdk),
* Bibliotecas, consulte [Bibliotecas](#libraries),
* Camadas de acesso ao banco de dados, consulte [Camadas de acesso ao banco de dados](#database-access-layers),
* LibreOffice, consulte [Instalação do LibreOffice para Debian](#installing-libreoffice-for-debian) e [Instalação do LibreOffice para CentOS](#installing-libreoffice-for-centos),
* Fontes, consulte [Fontes para estatísticas de MTA](#fonts-for-mta-statistics) e [Fontes para instâncias japonesas](#fonts-for-japanese-instances).


### Bibliotecas {#libraries}

Para instalar Adobe Campaign no Linux, verifique se você tem a bibliotecas necessária.

* A biblioteca C deve ser capaz de suportar o modo TLS (Thread Local Storage). Esse modo está ativo na maioria dos casos, exceto com alguns kernels para os quais o suporte Xen foi desativado.

  Para verificar isso, você pode usar o comando uname -a **| grep xen** , por exemplo.

  Se o comando não retornar uma linha vazia, significa que a configuração está correta.

* É necessário ter a versão OpenSSL **1.0.2** ou superior.

  Para distribuições RHEL, é necessária a versão 1.0 do OpenSSL.

* Para usar o Adobe Campaign, você precisa ter a **libicu** biblioteca instalada.

### SELinux {#selinux}

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

### Fontes para estatísticas de MTA {#fonts-for-mta-statistics}

Para que os relatórios sobre estatísticas do MTA (nms/fra/jsp/stat.jsp) sejam exibidos corretamente, adicione fontes.

No Debian, adicione o comando:

```
apt install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Use o seguinte comando para o RHEL:

```
dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
```

### Fontes para instâncias japonesas {#fonts-for-japanese-instances}

Fontes de caracteres específicos são necessárias para as instâncias de Japonês em solicitar para exportar os relatórios para o formato PDF.

Em Debian, adicione o comando:

```
apt install fonts-ipafont
```

Para RHEL, adicione o seguinte comando:

```
dnf install epel-release # if required
dnf install vlgothic-fonts
```

### Instalação do LibreOffice para Debian {#installing-libreoffice-for-debian}

Para Debian, as seguintes configurações são necessárias:

1. Instale os seguintes pacotes padrão:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Instale as seguintes fontes (opcional, mas altamente recomendada para instâncias Japonês):

   ```
   apt-get install fonts-ipafont
   ```

### Instalação do LibreOffice para CentOS {#installing-libreoffice-for-centos}

As seguintes configurações são necessárias com o CentOS:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Camadas de acesso ao banco de dados {#database-access-layers}

As camadas de acesso para o mecanismo de banco de dados que você está usando devem ser instaladas no seu servidor e estar acessíveis por meio do Adobe Campaign conta. As versões e os modos de instalação podem variar dependendo do mecanismo de banco de dados usado.

A versão piloto compatível está detalhada no [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

Verifique também o [Banco de dados](../../installation/using/database.md) seção.

### PostgreSQL {#postgresql}

O Adobe Campaign é compatível com todas as versões das bibliotecas de clientes PostgreSQL da versão 9.6: **libpq.so.5**.

O uso do PostgreSQL com o Adobe Campaign também requer a instalação do correspondente **pgcrypto** bibliotecas.

### Oracle {#oracle}

Recupere a versão biblioteca para Debian de 64 bits, ou seja: libclntsh.so, libclntsh.so.19.1 **,** libclntsh.so.18.1 **,** libclntsh.so.12.1 **,** libclntsh.so.11.1 **ou** libclntsh.so.10.1 **.******

É possível obter um pacote de RPM do Linux da Oracle Technology Network.

>[!NOTE]
>
>Se você já tiver instalado o cliente Oracle, mas a ambiente global (para instância: /etc/perfil) não estiver configurada corretamente, você pode adicionar informações ausentes ao **script nl6/customer.sh** Para obter mais informações, consulte as [variáveis](../../installation/using/installing-packages-with-linux.md#environment-variables) Ambiente.

**Resolução de problemas e práticas recomendadas**

Os problemas podem ocorrer após um cliente do Oracle ou uma atualização do servidor, alteração de versão ou na primeira instalação da instância.

Se você observar no console do cliente que há atrasos inesperados (uma ou mais horas) nos logs, fluxo de trabalho, último processamento, próximo processamento e assim por diante, pode haver um problema entre a biblioteca do cliente Oracle e o Servidor Oracle. Para evitar esses problemas

1. Certifique-se de usar o **cliente completo**.

   Vários problemas foram identificados ao usar a versão do Oracle Instant Client. Além disso, é impossível alterar o arquivo de Fuso horário no cliente instantâneo.

1. Verifique se a versão **do** cliente e a versão **do servidor do** banco de dados são as **mesmas**.

   A combinação de versões apesar da matriz de compatibilidade do Oracle e da recomendação para alinhar as versões de cliente e servidor é conhecida por causar problemas.

   Verifique também o valor de ORACLE_HOME para certificar-se de que ele aponte para a versão de cliente esperada (caso haja várias versões instaladas na máquina).

1. Verifique se o cliente e o servidor usam o mesmo **arquivo de fuso horário**.

## Etapas de implementação {#implementation-steps}

As instalações do Adobe Campaign para Linux devem ser realizadas na seguinte sequência: instalação do servidor seguida de configuração da instância.

O processo de instalação é descrito neste capítulo. As etapas de instalação são as seguintes:

* Etapa 1: instalação do servidor de aplicativos, consulte [Instalação de pacotes com Linux](../../installation/using/installing-packages-with-linux.md).
* Etapa 2: Integração com um servidor Web (opcional, dependendo dos componentes implantados).

Quando as etapas de instalação estiverem concluídas, você precisará configurar as instâncias, o banco de dados e o servidor. Para obter mais informações, consulte [Sobre a configuração inicial](../../installation/using/about-initial-configuration.md).
