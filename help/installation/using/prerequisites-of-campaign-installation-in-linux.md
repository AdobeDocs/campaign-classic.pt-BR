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
TQID: https://experienceleague.adobe.com/SFdh5L8-oHjpH7rIhDxOQZqw7AukXtkv3lJHZu2oTHQ
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 854
ht-degree: 3%

---

# Pré-requisitos para instalar o Campaign no Linux{#prerequisites-of-campaign-installation-in-linux}

## Pré-requisitos de software {#software-prerequisites}

Esta seção detalha as etapas preliminares de configuração necessárias antes de instalar o Adobe Campaign.

A configuração técnica e de software necessária para a instalação do Adobe Campaign está detalhada na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

Lembrando que os seguintes componentes precisam ser instalados e configurados corretamente:

* Apache, consulte a [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md),
* Java JDK e OpenJDK, consulte [Java Development Kit - JDK](../../installation/using/application-server.md#jdk),
* Bibliotecas, consulte [Bibliotecas](#libraries),
* Camadas de acesso ao banco de dados, consulte [Camadas de acesso ao banco de dados](#database-access-layers),
* LibreOffice, consulte [Instalação do LibreOffice para Debian](#installing-libreoffice-for-debian) e [Instalação do LibreOffice para CentOS](#installing-libreoffice-for-centos),
* Fontes, consulte [Fontes para estatísticas de MTA](#fonts-for-mta-statistics) e [Fontes para instâncias japonesas](#fonts-for-japanese-instances).


### Bibliotecas {#libraries}

Para instalar o Adobe Campaign no Linux, verifique se você tem as bibliotecas necessárias.

* A biblioteca C deve ser capaz de suportar o modo TLS (Thread Local Storage, Armazenamento local da thread). Esse modo está ativo na maioria dos casos, exceto com alguns kernels para os quais o suporte ao Xen foi desativado.

  Para verificar isso, você pode usar o **uname -a comando | grep xen**, por exemplo.

  Se o comando não retornar uma linha vazia, significa que a configuração está correta.

* Você deve ter o OpenSSL versão **1.0.2** ou superior.

  Para distribuições RHEL, é necessária a versão 1.0 do OpenSSL.

* Para usar o Adobe Campaign, você precisa ter a biblioteca **libicu** instalada.

### SELinux {#selinux}

Quando usado, o módulo SELinux deve ser configurado corretamente.

Para fazer isso, faça logon como root e insira o seguinte comando:

```
echo 0 >/selinux/enforce
```

Além disso, no arquivo **/etc/sysconfig/httpd**, a seguinte linha foi adicionada para fazer referência ao script de configuração do ambiente Adobe Campaign:

```
. ~neolane/nl6/env.sh
```

No RHEL e no CentOS, problemas de compatibilidade com as camadas de cliente dos bancos de dados eram observados quando o SELinux estava habilitado. Para ter certeza de que o Adobe Campaign pode operar corretamente, recomendamos desativar o SELinux.

**Aplicar o seguinte processo:**

* Edite o arquivo **/etc/selinux/config**

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

As fontes de caracteres específicos são necessárias para as instâncias japonesas para exportar os relatórios para o formato PDF.

No Debian, adicione o comando:

```
apt install fonts-ipafont
```

Para o RHEL, adicione o seguinte comando:

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

A versão piloto com suporte está detalhada na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

Verifique também a seção geral [Banco de Dados](../../installation/using/database.md).

### PostgreSQL {#postgresql}

O Adobe Campaign oferece suporte a todas as versões das bibliotecas de clientes PostgreSQL da versão 9.6: **libpq.so.5**.

O uso do PostgreSQL com Adobe Campaign também requer a instalação das bibliotecas **pgcrypto** correspondentes.

### Oracle {#oracle}

Recupere a versão da biblioteca para Debian de 64 bits, ou seja: **libclntsh.so**, **libclntsh.so.19.1**, **libclntsh.so.18.1**, **libclntsh.so.12.1**, **libclntsh.so.11.1** ou **libclntsh.so.10.1**.

Obtenha um pacote RPM de Linux na Oracle Technology Network.

>[!NOTE]
>
>Se você já tiver instalado o cliente Oracle, mas o ambiente global (por exemplo: /etc/profile) não estiver configurado corretamente, você pode adicionar informações ausentes ao script **nl6/customer.sh**. Para obter mais informações, consulte [Variáveis de ambiente](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Resolução de problemas e práticas recomendadas**

Os problemas podem ocorrer após um cliente Oracle ou uma atualização de servidor, alteração de versão ou na primeira instalação da instância.

Se você observar no console do cliente que há atrasos inesperados (uma ou mais horas) nos logs, fluxo de trabalho, último processamento, próximo processamento e assim por diante, pode haver um problema entre a biblioteca do cliente Oracle e o Oracle Server. Para evitar esses problemas

1. Certifique-se de usar o **cliente completo**.

   Vários problemas foram identificados ao usar a versão do Oracle Instant Client. Além disso, é impossível alterar o arquivo de fuso horário no cliente instantâneo.

1. Verifique se a **versão do cliente** e a **versão do servidor de banco de dados** são a **mesma**.

   A combinação de versões apesar da matriz de compatibilidade da Oracle e da recomendação para alinhar as versões de cliente e servidor é conhecida por causar problemas.

   Verifique também o valor de ORACLE_HOME para garantir que ele aponte para a versão de cliente esperada (caso haja várias versões instaladas na máquina).

1. Verifique se o cliente e o servidor usam o mesmo **arquivo de fuso horário**.

## Etapas de implementação {#implementation-steps}

As instalações do Adobe Campaign para Linux devem ser realizadas na seguinte sequência: instalação do servidor seguida de configuração da instância.

O processo de instalação é descrito neste capítulo. As etapas de instalação são as seguintes:

* Etapa 1: instalando o servidor de aplicativos, consulte [Instalando pacotes com Linux](../../installation/using/installing-packages-with-linux.md).
* Etapa 2: Integração com um servidor Web (opcional, dependendo dos componentes implantados).

Quando as etapas de instalação estiverem concluídas, você precisará configurar as instâncias, o banco de dados e o servidor. Para obter mais informações, consulte [Sobre a configuração inicial](../../installation/using/about-initial-configuration.md).
