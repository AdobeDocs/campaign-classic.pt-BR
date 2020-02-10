---
title: Implantação de fornecedores médios
seo-title: Implantação de fornecedores médios
description: Implantação de fornecedores médios
seo-description: null
page-status-flag: never-activated
uuid: e359c486-7ee6-4295-80fc-4c371a0ef068
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 19220d8e-9494-46b4-9aa0-4c4a729aea96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Implantação de fornecedores médios{#mid-sourcing-deployment}

Essa configuração é uma solução intermediária ideal entre uma configuração hospedada (ASP) e a internalização. Os componentes de execução voltados para o exterior são executados em um servidor de &quot;mid-sourcing&quot; hospedado no Adobe Campaign.

>[!NOTE]
>
>Para configurar esse tipo de implantação, é necessário adquirir a opção apropriada. Verifique seu contrato de licença.

A comunicação geral entre servidores e processos é realizada de acordo com o seguinte esquema:

![](assets/s_ncs_install_midsourcing.png)

* Os módulos de gerenciamento de execução e rejeição estão desativados na instância.
* O aplicativo é configurado para executar a execução de mensagens em um servidor remoto &quot;de origem média&quot; que é direcionado por meio de chamadas SOAP (via HTTP ou HTTPS).

## Recursos {#features}

### Vantagens {#advantages}

* Configuração simplificada do servidor: Não é necessário que o cliente configure módulos voltados para o exterior (mta e inMail).
* Uso limitado da largura de banda: Como a execução é executada pelo servidor de mid-sourcing, somente a largura de banda é necessária para enviar dados de personalização ao servidor de mid-sourcing.
* A alta disponibilidade não é mais um problema interno: O problema é transferido para o servidor de mid-sourcing (redirecionamento, páginas espelhadas, servidores de execução etc.).
* O banco de dados não sai da empresa: Somente os dados necessários para montar as mensagens são enviados para o servidor de mid-sourcing (HTTPS pode ser usado para isso).
* Esse tipo de implantação pode ser uma solução para arquiteturas de alto volume (muitos destinatários no banco de dados), com um throughput significativo.

### Desvantagens {#disadvantages}

* Pequeno atraso na exibição das informações de execução de mensagens e da funcionalidade de relatórios devido ao tempo necessário para obter as informações de volta do servidor de mid-sourcing.
* Pesquisas e formulários da Web permanecem na plataforma cliente.

### Equipamento recomendado {#recommended-equipment}

* Servidor de aplicativos: CPU quad-core de 2 Ghz, 4 GB de RAM, disco rígido SATA de 80 GB RAID de software.
* Servidor de banco de dados: CPUs bi-quad core de 3 GHz, RAM mínima de 4 GB, disco rígido SAS RAID 10 de 15000 RPM de hardware, número que depende do tamanho e do desempenho esperado do banco de dados.

>[!NOTE]
>
>O redirecionamento e o mid-sourcing são elementos separados, mas o servidor de rastreamento será, em geral, compartilhado com os servidores de mid-sourcing.

## Etapas de instalação e configuração {#installation-and-configuration-steps-}

### Pré-requisitos {#prerequisites}

* JDK no servidor de aplicativos.
* Acesso a um servidor de banco de dados no servidor de aplicativos.
* Firewall configurado para abrir portas HTTP (80) ou HTTPS (443) no servidor de mid-sourcing.

### Instalação e configuração (implantação de mid-sourcing) {#installing-and-configuring--mid-sourcing-deployment-}

Consulte o servidor [de](../../installation/using/mid-sourcing-server.md)Meid-sourcing.
