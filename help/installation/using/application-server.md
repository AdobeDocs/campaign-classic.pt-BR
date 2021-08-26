---
product: campaign
title: Servidor de aplicativos
description: Servidor de aplicativos
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 1%

---

# Servidor de aplicativos{#application-server}

![](../../assets/v7-only.svg)

As camadas de acesso ao banco de dados necessárias devem ser instaladas no servidor e acessíveis a partir da conta do Adobe Campaign.

## Java Development Kit - JDK {#java-development-kit---jdk}

O gerador dinâmico de página da Web usa a tecnologia JSP 1.2. Para isso, um mecanismo Tomcat (do Apache) é incluído no aplicativo. Ele requer um Java Development Kit (JDK), instalado em todos os servidores nos quais o aplicativo Adobe Campaign está instalado.

Primeiro, você deve instalar um JDK nos computadores em que deseja executar o servidor de aplicativos do Adobe Campaign (**nlserver web** process) porque ele incorpora um contêiner de servlet, o Apache Tomcat, usado para gerar páginas da Web dinâmicas (relatórios, formulários da Web etc).

O aplicativo foi aprovado para o Java Development Kit (JDK) desenvolvido pelo Oracle e para **OpenJDK**.

As versões compatíveis são detalhadas em Campaign [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>Ele pode ser instalado usando a versão adequada do JDK já usada por outros aplicativos na máquina.
>  
>Ao instalar o, você não é obrigado a executar a integração com os navegadores da Web.
>
>Em uma máquina que executa apenas agentes de delivery (processo **nlserver mta**) ou o servidor de workflow (processo **nlserver wfserver**), a instalação de um JDK não é necessária.

Para baixar o Java JDK, conecte-se a: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Aviso: você deve baixar um JDK, não um JRE.**

>[!CAUTION]
>
>Para preservar o desempenho da operação da plataforma e garantir a compatibilidade com a versão instalada, você deve desativar as funções de atualização automática do JDK no Windows e Linux.

Para instalar o JDSL em um ambiente Linux, é preferível usar um gerenciador de pacotes.

Em Debian 8 e 9, use o seguinte comando:

```
aptitude install openjdk-8-jdk
```

Para RHEL 7, use o seguinte comando:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

No Linux, o OpenSSL deve ser instalado. As versões compatíveis com o Adobe Campaign são **OpenSSL 1.0.1** e **OpenSSL 0.9.8**. As subversões 0.9.8g a 0.9.8o são aceitas.

## Exportação de relatórios {#exporting-reports}

O Adobe Campaign permite exportar relatórios da plataforma no formato Microsoft Excel e Adobe PDF. Para o formato do Microsoft Excel, o Adobe Campaign usa **LibreOffice**. Para o formato Adobe PDF, o Adobe Campaign usa o conversor **PhantomJS**. O PhantomJs está incluído no pacote de fábrica e o LibreOffice deve ser instalado na(s) máquina(s) na(s) qual(is) o servidor de aplicativos do Adobe Campaign é executado(s) (**nlserver web** processo).

>[!NOTE]
>
>Para Linux, será necessário adicionar fontes. Para obter mais informações, consulte [Fontes para estatísticas MTA](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

O SpamAssassin permite atribuir uma pontuação a emails para determinar se uma mensagem corre o risco de ser considerada indesejável por ferramentas antisspam usadas no recebimento. A instalação é opcional.

A qualificação de emails como indesejáveis pelo SpamAssassin é baseada inteiramente em regras de filtragem e pontuação. Essas regras devem, portanto, ser atualizadas pelo menos uma vez por dia para que a instalação do SpamAssassin e sua integração no Adobe Campaign sejam totalmente funcionais e garantam a relevância das pontuações atribuídas aos seus deliveries antes de enviá-los. Esta atualização é da responsabilidade do administrador do servidor que hospeda o SpamAssassin.

A versão mínima compatível é: **3.4**

O SpamAssassin requer um acesso HTTP à Internet (tcp/80).

As etapas de instalação e configuração do SpamAssassin são apresentadas em [Configuração do SpamAssassin](../../installation/using/configuring-spamassassin.md).
