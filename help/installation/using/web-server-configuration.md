---
product: campaign
title: Configuração do servidor da web
description: Saiba mais sobre as principais práticas recomendadas de configuração do servidor Web
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 4%

---

# Configuração do servidor da web {#web-server-configuration}



Abaixo, você encontrará algumas das principais práticas recomendadas relacionadas à configuração do servidor da Web (Apache/IIS).

* Alterar páginas de erro padrão.

* Desabilitar versão e cifras antigas do SSL:

   **No Apache**, edite /etc/apache2/mods-available/ssl.conf. Aqui está um exemplo:

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * ALTA do SSLCipherSuite:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **No IIS** (consulte a [documentação](https://support.microsoft.com/en-us/kb/245030)), execute a seguinte configuração:

   * Adicionar subchave de registro em HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Para habilitar o sistema a usar os protocolos que não serão negociados por padrão (como o TLS 1.2), altere os dados do valor DWORD do valor DisabledByDefault para 0x0 nas seguintes chaves do Registro sob o **Protocolos** chave:

      SCHANNEL\Protocolos\TLS 1.2\Cliente

      SCHANNEL\Protocolos\TLS 1.2\Servidor
   **Desativar SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: Valor DWORD (32 bits) para 1

   SCHANNEL\Protocols\SSL 3.0\Server: Habilitado: Valor DWORD (32 bits) para 0

* Remova o **TRACE** método:

   **No Apache**, edite em /etc/apache2/conf.d/security: TraceEnable **Desligado**

   **No IIS** (consulte a [documentação](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), execute a seguinte configuração:

   * Verifique se **Filtragem de solicitação** serviço de função ou recurso instalado.
   * No **Filtragem de solicitação** clique na guia verbos de HTTP e, em seguida, clique em Negar verbo. No painel Ações, digite TRACE na caixa de diálogo aberta.

* Remova o banner:

   **No Apache**, edite /etc/apache2/conf.d/security:

   * AssinaturaDoServidor **Desligado**
   * ServerTokens **Prod**

   **No IIS**, execute a seguinte configuração:

   * Instalar **URLScan**.
   * Edite o **Urlscan.ini** arquivo a ter **RemoveServerHeader=1**


* Limite o tamanho da consulta para impedir que arquivos importantes sejam carregados:

   **No Apache**, adicione o **LimitRequestBody** diretiva (tamanho em bytes) no diretório /.

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **No IIS** (consulte a [documentação](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), defina o **maxAllowedContentLength** (comprimento máximo do conteúdo permitido) nas opções de filtragem de conteúdo.

Tópicos relacionados:

* [Visão geral de conformidade da Adobe Marketing Cloud](https://experienceleague.adobe.com/docs/core-services/assets/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Visão geral da Segurança do Adobe Campaign](https://www.adobe.com/content/dam/cc/en/security/pdfs/ADB-CampaignSecurity-WP.pdf) (PDF)
