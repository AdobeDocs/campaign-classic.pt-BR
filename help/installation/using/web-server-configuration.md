---
product: campaign
title: Configuração do servidor da web
description: Saiba mais sobre as principais práticas recomendadas de configuração do servidor da Web.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 4%

---

# Configuração do servidor da web {#web-server-configuration}

![](../../assets/v7-only.svg)

Abaixo você encontrará algumas das principais práticas recomendadas relacionadas à configuração do servidor da Web (Apache/IIS).

* Alterar páginas de erro padrão.

* Desative a versão e as cifras SSL antigas:

   **No Apache**, edite /etc/apache2/mods-available/ssl.conf. Aqui está um exemplo:

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite ALTO:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **No IIS** (consulte o [documentação](https://support.microsoft.com/en-us/kb/245030)), execute a seguinte configuração:

   * Adicionar subchave de registro em HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Para habilitar o sistema a usar os protocolos que não serão negociados por padrão (como TLS 1.2), altere os dados do valor DWORD do valor DisabledByDefault para 0x0 nas seguintes chaves do Registro nas **Protocolos** chave:

      SCHANNEL\Protocolos\TLS 1.2\Cliente

      SCHANNEL\Protocolos\TLS 1.2\Servidor
   **Desativar SSL x.0**

   SCHANNEL\Protocolos\SSL 3.0\Cliente: DisabledByDefault: DWORD (32 bits) Valor para 1

   SCHANNEL\Protocolos\SSL 3.0\Servidor: Ativado: DWORD (32 bits) Valor para 0

* Remova o **TRACE** método :

   **No Apache**, edite em /etc/apache2/conf.d/security: TraceEnable **Desligado**

   **No IIS** (consulte o [documentação](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), execute a seguinte configuração:

   * Certifique-se de que **Solicitar Filtragem** o serviço ou recurso de função está instalado.
   * No **Solicitar Filtragem** , clique na guia verbos HTTP e, em seguida, clique em Negar verbo. No painel Ações, digite TRACE na caixa de diálogo aberta.

* Remova o banner:

   **No Apache**, edite /etc/apache2/conf.d/security:

   * ServerSignature **Desligado**
   * ServerTokens **Prod**

   **No IIS**, execute a seguinte configuração:

   * Instalar **URLScan**.
   * Edite o **Urlscan.ini** arquivo a ter **RemoveServerHeader=1**


* Limite o tamanho da consulta para impedir que arquivos importantes sejam carregados:

   **No Apache**, adicione o **LimitRequestBody** diretiva (tamanho em bytes) no / diretório.

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **No IIS** (consulte o [documentação](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), defina a variável **maxAllowedContentLength** (comprimento máximo permitido do conteúdo) nas opções de filtragem de conteúdo.

Tópicos relacionados:

* [Visão geral da conformidade com o Adobe Marketing Cloud](https://experienceleague.adobe.com/docs/core-services/assets/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Visão geral da segurança no Adobe Campaign](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf) (PDF)
