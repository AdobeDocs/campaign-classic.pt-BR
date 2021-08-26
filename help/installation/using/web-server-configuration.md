---
product: campaign
title: Configuração do servidor da web
description: Saiba mais sobre as principais práticas recomendadas de configuração do servidor da Web.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 4%

---

# Configuração do servidor da web {#web-server-configuration}

![](../../assets/v7-only.svg)

Abaixo você encontrará algumas das principais práticas recomendadas relacionadas à configuração do servidor da Web (Apache/IIS).

* Alterar páginas de erro padrão.

* Desative a versão e as cifras SSL antigas:

   **No Apache**, edite /etc/apache2/mods-available/ssl.conf. Aqui está um exemplo:

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **No IIS**  (consulte a  [documentação](https://support.microsoft.com/en-us/kb/245030)), execute a seguinte configuração:

   * Adicionar subchave de registro em HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Para permitir que o sistema use os protocolos que não serão negociados por padrão (como TLS 1.2), altere os dados do valor DWORD do valor DisabledByDefault para 0x0 nas seguintes chaves do Registro na chave **Protocolos**:

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **Desativar SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: DWORD (32 bits) Valor para 1

   SCHANNEL\Protocols\SSL 3.0\Server: Ativado: DWORD (32 bits) Valor para 0

* Remova o método **TRACE**:

   **No Apache**, edite em /etc/apache2/conf.d/security: TraceEnable  **Off**

   **No IIS**  (consulte a  [documentação](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), execute a seguinte configuração:

   * Certifique-se de que o serviço ou recurso de função **Filtragem de Solicitação** está instalado.
   * No painel **Filtragem de solicitação**, clique na guia verbos HTTP e, em seguida, clique em Negar verbo. No painel Ações, digite TRACE na caixa de diálogo aberta.

* Remova o banner:

   **No Apache**, edite /etc/apache2/conf.d/security:

   * ServerSignature **Off**
   * ServerTokens **Prod**

   **No IIS**, execute a seguinte configuração:

   * Instale **URLScan**.
   * Edite o arquivo **Urlscan.ini** para ter **RemoveServerHeader=1**


* Limite o tamanho da consulta para impedir que arquivos importantes sejam carregados:

   **No Apache**, adicione a diretiva  **** LimitRequestBodypolicy (tamanho em bytes) no diretório / .

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **No IIS**  (consulte a  [documentação](http://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), defina o  **maxAllowedContentLength**  (comprimento máximo permitido do conteúdo) nas opções de filtragem de conteúdo.

Tópicos relacionados:

* [Visão geral](https://marketing.adobe.com/resources/help/en_US/xref/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf)  da conformidade com o Adobe Marketing Cloud (PDF)
* [Visão geral](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf)  da Segurança do Adobe Campaign (PDF)
