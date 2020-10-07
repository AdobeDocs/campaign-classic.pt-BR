---
title: Servidor de aplicativos
seo-title: Servidor de aplicativos
description: Servidor de aplicativos
seo-description: null
page-status-flag: never-activated
uuid: 837c6a5c-53a4-4d1b-a084-9cf77e7a0eee
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 7a9e028c-255d-4aad-9827-d19f9a7897b2
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 3%

---


# Servidor de aplicativos{#application-server}

As camadas de acesso ao banco de dados necessárias devem ser instaladas no servidor e acessíveis a partir da conta da Adobe Campaign.

## Java Development Kit - JDK {#java-development-kit---jdk}

O gerador dinâmico de páginas da Web usa a tecnologia JSP 1.2. Para isso, um mecanismo Tomcat (do Apache) é incluído no aplicativo. Ele requer um Java Development Kit (JDK), instalado em todos os servidores nos quais o aplicativo Adobe Campaign está instalado.

Primeiro, você deve instalar um JDK nos computadores nos quais deseja executar o servidor de aplicativos Adobe Campaign (processo Web **do** nlserver) porque ele incorpora um container de servlet, o Apache Tomcat, usado para gerar páginas da Web dinâmicas (relatórios, Formulários web etc.).

The application has been approved for the Java Development Kit (JDK) developed by Oracle as well as for **OpenJDK**.

The supported versions are detailed in the [Compatibility matrix](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html).

>[!NOTE]
>
>Ele pode ser instalado usando a versão apropriada do JDK já usada por outros aplicativos na máquina.
>  
>Ao instalar, você não é obrigado a realizar a integração com os navegadores da Web.
>
>Em uma máquina que executa apenas agentes de delivery (processo **nlserver mta** ) ou o servidor de fluxo de trabalho (processo **nlserver wfserver** ), a instalação de um JDK não é necessária.

Para baixar o Java JDK, conecte-se a: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Aviso: você deve baixar um JDK, não um JRE.**

>[!CAUTION]
>
>Para preservar o desempenho de operação da plataforma e garantir a compatibilidade com a versão instalada, você deve desativar as funções de atualização automática do JDK no Windows e no Linux.

Para instalar o JDSL em um ambiente Linux, é preferível usar um gerenciador de pacote.

Em Debian 8 e 9, use o seguinte comando:

```
aptitude install openjdk-8-jdk
```

Para RHEL 7, use o seguinte comando:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

No Linux, o OpenSSL deve estar instalado. As versões suportadas pelo Adobe Campaign são **OpenSSL 1.0.1** e **OpenSSL 0.9.8**. As subversões 0.9.8g a 0.9.8o são aceitas.

## Exportação de relatórios {#exporting-reports}

O Adobe Campaign permite exportar relatórios da plataforma no formato Microsoft Excel e Adobe PDF. Para o formato do Microsoft Excel, a Adobe Campaign usa o **LibreOffice**. Para o formato Adobe PDF, a Adobe Campaign usa o conversor **PhantomJS** . O PhantomJs está incluído no pacote de fábrica e o LibreOffice deve estar instalado nas máquinas nas quais o servidor de aplicativos Adobe Campaign é executado (processo web **do** nlserver).

>[!NOTE]
>
>Para Linux, será necessário adicionar fontes. Para obter mais informações, consulte [Fontes para estatísticas](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)MTA.

## SpamAssassin {#spamassassin}

O SpamAssassin permite que você atribua uma pontuação a emails para determinar se uma mensagem corre o risco de ser considerada indesejável pelas ferramentas antisspam usadas na recepção. A instalação é opcional.

A qualificação de emails como indesejados pelo SpamAssassin é baseada inteiramente em regras de filtragem e pontuação. Essas regras devem, portanto, ser atualizadas pelo menos uma vez por dia para que sua instalação do SpamAssassin e sua integração à Adobe Campaign estejam totalmente funcionais e para garantir a relevância das pontuações atribuídas aos delivery antes do envio. Esta atualização é da responsabilidade do administrador do servidor que hospeda o SpamAssassin.

A versão mínima suportada é: **3,4**

O SpamAssassin requer um acesso HTTP à Internet (tcp/80).

As etapas de instalação e configuração do SpamAssassin são apresentadas em [Configuração do SpamAssassin](../../installation/using/configuring-spamassassin.md).
