---
product: campaign
title: Servidor de aplicativos
description: Servidor de aplicativos
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 1%

---

# Servidor de aplicativos{#application-server}



As camadas de acesso ao banco de dados necessárias devem ser instaladas no servidor e acessíveis pela conta do Adobe Campaign.

## Java Development Kit - JDK {#java-development-kit---jdk}

O gerador dinâmico de páginas da Web usa a tecnologia JSP 1.2. Para isso, um mecanismo Tomcat (do Apache) é incluído no aplicativo. Ele requer um Java Development Kit (JDK), instalado em todos os servidores nos quais o aplicativo do Adobe Campaign está instalado.

Você deve primeiro instalar um JDK nos computadores em que deseja executar o servidor de aplicativos do Adobe Campaign (**nlserver web** processo) porque incorpora um contêiner de servlet, o Apache Tomcat, usado para gerar páginas dinâmicas da Web (relatórios, formulários Web etc.).

O aplicativo foi aprovado para o Java Development Kit (JDK) desenvolvido pelo Oracle e para **OpenJDK**.

As versões compatíveis estão detalhadas no Campaign [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>Ele pode ser instalado usando a versão apropriada do JDK já usada por outros aplicativos na máquina.
>  
>Ao instalar o, não é necessário executar a integração com os navegadores da Web.
>
>Em máquinas que executam apenas agentes de entrega (**mta nlserver** ) ou o servidor de workflow (**nlserver wfserver** processo), a instalação de um JDK não é necessária.

Para baixar o JDK do Java, conecte-se a: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Aviso: você deve baixar um JDK, não um JRE.**

>[!CAUTION]
>
>Para preservar o desempenho operacional da plataforma e garantir a compatibilidade com a versão instalada, você deve desativar as funções de atualização automática do JDK no Windows e no Linux.

Para instalar o JDSL em um ambiente Linux, é preferível usar um gerenciador de pacotes.

No Debian 8 e 9, use o seguinte comando:

```
aptitude install openjdk-8-jdk
```

Para o RHEL 7, use o seguinte comando:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

No Linux, o OpenSSL deve estar instalado. O Adobe Campaign oferece suporte ao OpenSSL versão 1.0.2 ou superior.

## Exportação de relatórios {#exporting-reports}

O Adobe Campaign permite exportar relatórios da plataforma no formato Microsoft Excel e Adobe PDF. No formato do Microsoft Excel, o Adobe Campaign usa **LibreOffice**. Para o formato Adobe PDF, o Adobe Campaign usa o **JSfantasma** conversor. O PhantomJs está incluído no pacote de fábrica e o LibreOffice deve ser instalado nos computadores em que o servidor de aplicativos Adobe Campaign é executado (**nlserver web** processo).

>[!NOTE]
>
>No Linux, será necessário adicionar fontes. Para obter mais informações, consulte [Fontes para estatísticas de MTA](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

O SpamAssassin permite atribuir uma pontuação a emails para determinar se uma mensagem corre o risco de ser considerada indesejável pelas ferramentas antisspam usadas na recepção. A instalação é opcional.

A qualificação de emails como indesejáveis pelo SpamAssassin é baseada inteiramente nas regras de filtragem e pontuação. Portanto, essas regras precisam ser atualizadas pelo menos uma vez por dia para que sua instalação do SpamAssassin e sua integração no Adobe Campaign funcionem plenamente e para garantir a relevância das pontuações atribuídas a seus deliveries antes do envio. Essa atualização é responsabilidade do administrador do servidor que hospeda o SpamAssassin.

A versão mínima com suporte é: **3.4**

O SpamAssassin requer um acesso HTTP à Internet (tcp/80).

Os estágios de instalação e configuração do SpamAssassin são apresentados em [Configuração do SpamAssassin](../../installation/using/configuring-spamassassin.md).
