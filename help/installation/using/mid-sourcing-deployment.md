---
product: campaign
title: Implantação mid-sourcing
description: Implantação mid-sourcing
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 8a4d7ef1-de5b-4aee-a527-1b74d987ba61
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 2%

---

# Implantação mid-sourcing{#mid-sourcing-deployment}



Essa configuração é uma solução intermediária ideal entre uma configuração hospedada (ASP) e a internalização. Os componentes de execução voltados para o exterior são executados em um servidor &quot;mid-sourcing&quot; hospedado na Adobe Campaign.

>[!NOTE]
>
>Para configurar esse tipo de implantação, você precisa adquirir a opção apropriada. Verifique seu contrato de licença.

A comunicação geral entre servidores e processos é realizada de acordo com o seguinte esquema:

![](assets/s_ncs_install_midsourcing.png)

* Os módulos de gerenciamento de execução e rejeição estão desativados na instância.
* O aplicativo é configurado para executar mensagens em um servidor remoto de &quot;origem intermediária&quot; orientado por chamadas SOAP (por HTTP ou HTTPS).

## Recursos {#features}

### Vantagens {#advantages}

* Configuração simplificada do servidor: não é necessário que o cliente configure módulos voltados para fora (mta e inMail).
* Uso limitado de largura de banda: como a execução é realizada pelo servidor mid-sourcing, somente a largura de banda necessária é suficiente para enviar dados de personalização para o servidor mid-sourcing.
* A alta disponibilidade não é mais um problema interno: o problema é transferido para o servidor mid-sourcing (redirecionamento, mirror pages, servidores de execução etc.).
* O banco de dados não sai da empresa: somente os dados necessários para montar as mensagens são enviados para o servidor mid-sourcing (HTTPS pode ser usado para isso).
* Esse tipo de implantação pode ser uma solução para arquiteturas de alto volume (muitos recipients no banco de dados), com uma taxa de transferência de entrega significativa.

### Desvantagens {#disadvantages}

* Pequeno atraso na visualização de informações de execução de mensagens e para a funcionalidade de relatórios devido ao tempo que leva para obter informações do servidor mid-sourcing.
* As pesquisas e os formulários web permanecem na plataforma do cliente.

### Equipamento recomendado {#recommended-equipment}

* Servidor de aplicativos: CPU quad-core de 2 Ghz, 4 GB de RAM, disco rígido SATA RAID 1 de software de 80 GB.
* Servidor de banco de dados: CPUs bi-quad core de 3 GHz, mínimo de 4 GB de RAM, disco rígido SAS RAID 10 de 15000 RPM para hardware, o número dependendo do tamanho e do desempenho esperado do banco de dados.

>[!NOTE]
>
>O redirecionamento e o mid-sourcing são elementos separados, no entanto, o servidor de rastreamento será, em geral, compartilhado com os servidores mid-sourcing.

## Etapas de instalação e configuração {#installation-and-configuration-steps-}

### Pré-requisitos {#prerequisites}

* JDK no servidor de aplicativos.
* Acesso a um servidor de banco de dados no servidor de aplicativos.
* Firewall configurado para abrir portas HTTP (80) ou HTTPS (443) para o servidor mid-sourcing.

### Instalação e configuração (implantação de mid-sourcing) {#installing-and-configuring--mid-sourcing-deployment-}

Consulte [Servidor Mid-sourcing](../../installation/using/mid-sourcing-server.md).
