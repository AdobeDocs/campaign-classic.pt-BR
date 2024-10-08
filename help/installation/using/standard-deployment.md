---
product: campaign
title: Implantação padrão
description: Implantação padrão
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 4df126fa-4a6e-46a7-af6e-1e2e97f0072e
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 5%

---

# Implantação padrão{#standard-deployment}



Para essa configuração, são necessários três computadores:

* Um servidor de aplicativos dentro da LAN para os usuários finais (preparação de campanhas, relatórios etc.),
* Dois servidores frontais na DMZ atrás de um balanceador de carga.

Os dois servidores na DMZ lidam com rastreamento, mirror pages e delivery e são redundantes para alta disponibilidade.

O servidor de aplicativos na LAN atende os usuários finais e executa todos os processos recorrentes (mecanismo de workflow). Assim, quando o pico de carga é atingido nos servidores frontais, os usuários do aplicativo não são afetados.

O servidor de banco de dados pode ser hospedado em um computador separado desses três. Caso contrário, o servidor de aplicativos e o servidor de banco de dados compartilharão o mesmo computador dentro da LAN, desde que o sistema operacional seja suportado pelo Adobe Campaign (Linux ou Windows).

A comunicação geral entre servidores e processos é realizada de acordo com o seguinte esquema:

![](assets/s_001_ncs_install_standardconfig.png)

Esse tipo de configuração pode lidar com um grande número de recipients (500.000 a 1.000.000), pois o servidor de banco de dados (e a largura de banda disponível) é o principal fator de limitação.

## Recursos {#features}

### Vantagens {#advantages}

* Funcionalidade de failover: a capacidade de alternar processos para um computador em caso de problema de hardware no outro.
* Melhor desempenho geral, já que o MTA e as funções de redirecionamento podem ser implantados em ambos os computadores atrás de um balanceador de carga. Com dois MTAs ativos e largura de banda suficiente, é possível alcançar taxas de transmissão na região de 100.000 emails por hora.

## Etapas de instalação e configuração {#installation-and-configuration-steps}

### Pré-requisitos {#prerequisites}

* JDK nos três computadores,
* Servidor Web (IIS, Apache) em ambos os frontais,
* Acesso a um servidor de banco de dados nos três computadores,
* Caixa de entrada de devolução acessível via POP3,
* Criação de dois aliases DNS:

   * a primeira exposta ao público para rastreamento e apontamento do balanceador de carga em um endereço IP virtual (VIP) e que é então distribuída aos dois servidores frontais,
   * o segundo exposto aos usuários internos para acesso pelo console e apontando para o mesmo servidor de aplicativos.

* Firewall configurado para abrir STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 para Oracle, 5432 para PostgreSQL etc.) portas. Para obter mais informações, consulte a seção [Acesso ao banco de dados](../../installation/using/network-configuration.md#database-access).

### Instalando o servidor de aplicativos {#installing-the-application-server}

Siga as etapas para instalar uma instância independente do servidor de aplicativos Adobe Campaign para a criação do banco de dados (etapa 12). Consulte [Instalando e configurando (computador único)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Como o computador não é um servidor de rastreamento, não considere a integração com o servidor Web.

Nos exemplos a seguir, os parâmetros da instância são:

* Nome da instância: **demonstração**
* Máscara DNS: **console.campaign.net&#42;** (somente para conexões de console do cliente e relatórios)
* Idioma: inglês
* Banco de dados: **campaign:demo@dbsrv**

### Instalando os dois servidores frontais {#installing-the-two-frontal-servers}

O procedimento de instalação e configuração é idêntico em ambos os computadores.

As etapas são as seguintes:

1. Instale o servidor do Adobe Campaign.

   Para obter mais informações, consulte [Pré-requisitos da instalação do Campaign no Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) e [Pré-requisitos da instalação do Campaign no Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Siga o procedimento de integração do servidor Web (IIS, Apache) descrito nas seguintes seções:

   * Para Linux: [Integração em um servidor Web para Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Para Windows: [Integração em um servidor Web para Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Crie a instância **demo**. Há duas maneiras de fazer isso:

   * Crie a instância por meio do console:

     ![](assets/install_create_new_connexion.png)

     Para obter mais informações, consulte [Criação de uma instância e logon](../../installation/using/creating-an-instance-and-logging-on.md).

     ou

   * Crie a instância usando linhas de comando:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*
     ```

     Para obter mais informações, consulte [Criação de uma instância](../../installation/using/command-lines.md#creating-an-instance).

   O nome da instância é igual ao do servidor de aplicativos.

   A conexão com o servidor com o módulo **nlserver web** (mirror pages, unsubscription) será feita a partir da URL do balanceador de carga (tracking.campaign.net).

1. Altere o **internal** para o mesmo que o servidor de aplicativos.

   Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Vincule o banco de dados à instância:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Nos arquivos **config-default.xml** e **config-demo.xml**, habilite os módulos **web**, **trackinglogd** e **mta**.

   Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Edite o arquivo **serverConf.xml** e preencha:

   * a configuração DNS do módulo MTA:

     ```
     <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
     ```

     >[!NOTE]
     >
     >O parâmetro **nameServers** é usado apenas no Windows.

     Para obter mais informações, consulte [Configurações de entrega](configure-delivery-settings.md).

   * os servidores de rastreamento redundantes nos parâmetros de redirecionamento:

     ```
     <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
     <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
     ```

     Para obter mais informações, consulte [Controle redundante](configuring-campaign-server.md#redundant-tracking).

1. Inicie o site e teste o redirecionamento da URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

   O navegador deve exibir as seguintes mensagens (dependendo do URL redirecionado pelo balanceador de carga):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   ou

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Para obter mais informações, consulte estas seções:

   * Para Linux: [Iniciar o servidor Web e testar a configuração](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Para Windows: [Iniciar o servidor Web e testar a configuração](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Inicie o servidor do Adobe Campaign.
1. No console do Adobe Campaign, conecte-se usando o login de **administrador** sem uma senha e inicie o assistente de implantação.

   Para obter mais informações, consulte [Implantando uma instância](../../installation/using/deploying-an-instance.md).

   A configuração é idêntica a uma instância independente, além da configuração do módulo de rastreamento.

1. Preencha o URL externo (o do balanceador de carga) usado para redirecionamento e os URLs internos dos dois servidores frontais.

   Para obter mais informações, consulte [Configuração de rastreamento](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >Usamos a instância existente dos dois servidores de rastreamento criados anteriormente e usamos o logon **interno**.
