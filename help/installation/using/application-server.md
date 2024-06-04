---
product: campaign
title: Servidor de aplicativos
description: Servidor de aplicativos
feature: Installation
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 7e1c3b256cf43232e49d9daa0bf44d1e114b565b
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 3%

---

# Servidor de aplicativos{#application-server}

As camadas de acesso ao banco de dados necessárias devem ser instaladas no servidor e acessíveis pela conta do Adobe Campaign.

## Java Development Kit - JDK {#java-development-kit---jdk}

O Java Development Kit, ou JDK, é um kit de desenvolvimento de software. É o componente fundamental que permite o desenvolvimento de aplicações Java e applets Java.

O gerador dinâmico de páginas da Web usa a tecnologia JSP 1.2. Para isso, um mecanismo Tomcat (do Apache) é incluído no aplicativo. Ele requer um Java Development Kit (JDK), instalado em todos os servidores nos quais o aplicativo do Adobe Campaign está instalado.

Você deve primeiro instalar um JDK nos computadores em que deseja executar o servidor de aplicativos do Adobe Campaign (**nlserver web** processo) porque incorpora um contêiner de servlet, o Apache Tomcat, usado para gerar páginas dinâmicas da Web (relatórios, formulários Web etc.).

O aplicativo foi aprovado para o Java Development Kit (JDK) desenvolvido pelo Oracle e para **OpenJDK**.

As versões compatíveis estão detalhadas no Campaign [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).


### Recomendações

Ao instalar e atualizar seu Java Development Kit, siga as seguintes recomendações:

* O Java Development Kit pode ser instalado usando a versão apropriada do JDK já usada por outros aplicativos na máquina.

* Ao instalar o JDK, a integração com os navegadores da Web não é necessária.

* Em máquinas que executam apenas agentes de entrega (**mta nlserver** ) ou o servidor de workflow (**nlserver wfserver** processo), não é necessário instalar um JDK.

* Para preservar o desempenho operacional da plataforma e garantir a compatibilidade com a versão instalada, você deve desativar as funções de atualização automática do JDK no Windows e no Linux.

* Ao atualizar a versão do Java, primeiro é necessário desinstalar a versão anterior. Ambas as versões do Java instaladas na mesma máquina podem causar conflitos.

  Como cliente local, você pode verificar o `LD_LIBRARY_PATH` [variável de ambiente](installing-packages-with-linux.md#environment-variables) está definido como a versão mais recente (por exemplo, java11). Se estiver definido como uma versão anterior (por exemplo, Java8), então ele precisa ser atualizado. Para o JDK 11, o caminho para localizar as bibliotecas do JDK é `/usr/lib/jvm/java-11-openjdk-amd64/lib`.


### Etapas de instalação

O Java Development Kit é específico da plataforma: são necessários instaladores separados para cada sistema operacional.

Para baixar o JDK, conecte-se [Site do Oracle](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"}.

>[!CAUTION]
>
> Certifique-se de baixar um Java Development Kit (JDK), não um Java Runtime Environment (JRE).


Para instalar o JDSL em um ambiente Linux, a Adobe recomenda usar um gerenciador de pacotes.

Para Debian, use o seguinte comando:

```sql
aptitude install openjdk-8-jdk
```

Para o RHEL, use o seguinte comando:

```sql
yum install java-1.8.0-openjdk
```


## OpenSSL {#openssl}

No Linux, o OpenSSL deve estar instalado. O Adobe Campaign oferece suporte ao OpenSSL versão 1.0.2 ou superior.

## Exportar relatórios {#exporting-reports}

Você pode usar o Adobe Campaign para exportar relatórios para o Microsoft Excel e o Adobe PDF.

* Para o formato do Microsoft Excel, o Adobe Campaign depende de **LibreOffice**.

* Para o formato Adobe PDF, o Adobe Campaign usa o **JSfantasma** conversor. O PhantomJs está incluído no pacote de fábrica e o LibreOffice deve ser instalado nos computadores em que o servidor de aplicativos Adobe Campaign é executado (**nlserver web** processo).

>[!NOTE]
>
>No Linux, será necessário adicionar fontes. Para obter mais informações, consulte [Fontes para estatísticas de MTA](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

O SpamAssassin permite atribuir uma pontuação a emails para determinar se uma mensagem corre o risco de ser considerada indesejável pelas ferramentas antisspam usadas na recepção. A instalação é opcional.

A qualificação de emails como indesejáveis pelo SpamAssassin é baseada inteiramente nas regras de filtragem e pontuação. Portanto, essas regras precisam ser atualizadas pelo menos uma vez por dia para que sua instalação do SpamAssassin e sua integração no Adobe Campaign funcionem plenamente e para garantir a relevância das pontuações atribuídas a seus deliveries antes do envio. Essa atualização é responsabilidade do administrador do servidor que hospeda o SpamAssassin.

A versão mínima com suporte é: **3.4**

O SpamAssassin requer um acesso HTTP à Internet (tcp/80).

Os estágios de instalação e configuração do SpamAssassin são apresentados em [Configuração do SpamAssassin](../../installation/using/configuring-spamassassin.md).
