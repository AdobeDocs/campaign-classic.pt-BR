---
product: campaign
title: Implantação mid-sourcing
description: Implantação mid-sourcing
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 8a4d7ef1-de5b-4aee-a527-1b74d987ba61
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 2%

---

# Implantação mid-sourcing{#mid-sourcing-deployment}

![](../../assets/v7-only.svg)

Essa configuração é uma solução intermediária ideal entre uma configuração hospedada (ASP) e a internalização. Os componentes de execução voltados para o exterior são executados em um servidor &quot;mid-sourcing&quot; hospedado na Adobe Campaign.

>[!NOTE]
>
>Para configurar esse tipo de implantação, é necessário adquirir a opção apropriada. Verifique seu contrato de licença.

A comunicação geral entre servidores e processos é realizada de acordo com o seguinte schema:

![](assets/s_ncs_install_midsourcing.png)

* Os módulos de gerenciamento de execução e rejeição estão desabilitados na instância.
* O aplicativo é configurado para executar a execução de mensagens em um servidor remoto &quot;mid-sourcing&quot;, que é orientado por chamadas SOAP (via HTTP ou HTTPS).

## Recursos {#features}

### Vantagens {#advantages}

* Configuração simplificada do servidor: Não é necessário que o cliente configure módulos voltados para o exterior (mta e inMail).
* Uso limitado da largura de banda: Como a execução é realizada pelo servidor mid-sourcing, somente é necessária largura de banda suficiente para enviar dados de personalização ao servidor mid-sourcing.
* A alta disponibilidade não é mais um problema interno: O problema é transferido para o servidor mid-sourcing (redirecionamento, mirror pages, servidores de execução etc.).
* O banco de dados não sai da empresa: Somente os dados necessários para montar as mensagens são enviados ao servidor mid-sourcing (HTTPS pode ser usado para isso).
* Esse tipo de implantação pode ser uma solução para arquiteturas de alto volume (muitos recipients no banco de dados), com uma taxa de transferência de delivery significativa.

### Desvantagens {#disadvantages}

* Pequeno atraso na exibição de informações de execução de mensagens e para a funcionalidade de relatórios devido ao tempo necessário para obter informações de volta do servidor mid-sourcing.
* Pesquisas e formulários web permanecem na plataforma do cliente.

### Equipamento recomendado {#recommended-equipment}

* Servidor de aplicativos: CPU quad-core de 2 Ghz, 4 GB de RAM, disco rígido SATA de 80 GB RAID de software.
* Servidor de banco de dados: CPUs bi-quad core de 3 GHz, mínimo de 4 GB de RAM, hardware RAID 10 disco rígido SAS de 15000 RPM, número que depende do tamanho e do desempenho esperado do banco de dados.

>[!NOTE]
>
>O redirecionamento e o mid-sourcing são elementos separados, no entanto, o servidor de rastreamento será, em geral, compartilhado com os servidores de mid-sourcing.

## Etapas de instalação e configuração {#installation-and-configuration-steps-}

### Pré-requisitos {#prerequisites}

* JDK no servidor de aplicativos.
* Acesso a um servidor de banco de dados no servidor de aplicativos.
* Firewall configurado para abrir portas HTTP (80) ou HTTPS (443) no servidor mid-sourcing.

### Instalação e configuração (implantação de mid-sourcing) {#installing-and-configuring--mid-sourcing-deployment-}

Consulte [Servidor Mid-sourcing](../../installation/using/mid-sourcing-server.md).
