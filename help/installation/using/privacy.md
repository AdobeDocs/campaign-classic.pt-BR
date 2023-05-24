---
product: campaign
title: Personalização e privacidade
description: Conheça as práticas recomendadas de segurança para privacidade e personalização
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: URL Personalization, Privacy
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 14%

---

# Personalização e privacidade {#privacy}




## Personalização de URL {#url-personalization}

Ao adicionar links personalizados ao seu conteúdo, sempre evite qualquer personalização na parte do nome do host do URL para evitar possíveis brechas de segurança. Os exemplos a seguir nunca devem ser usados em todos os atributos de URL &lt;`a href="">` ou `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Recomendações

Para validar e garantir que você não esteja usando a tabela acima, execute uma query na tabela de rastreamento de URL via [Editor de consultas genéricas do Campaign](../../platform/using/steps-to-create-a-query.md) ou crie um fluxo de trabalho com critérios de filtro no [atividade de query](../../workflow/using/query.md).

Exemplo:

1. Criar um workflow e adicionar um **Query** atividade. [Saiba mais](../../workflow/using/query.md).

1. Abra o **Query** e crie um filtro no `nmsTrackingUrl` quadro seguinte:

   `source URL starts with http://<% or source URL starts with https://<%`

1. Execute o fluxo de trabalho e verifique se há resultado.

1. Em caso positivo, abra a transição de saída para a visualização da lista de URLs.

   ![](assets/privacy-query-dynamic-url.png)


### Assinatura do URL

Para melhorar a segurança, foi introduzido um mecanismo de assinatura para rastrear links em emails. Ele está disponível a partir das builds 19.1.4 (9032@3a9dc9c) e 20.2. Esse recurso é ativado por padrão.

>[!NOTE]
>
>Quando um URL assinado mal formado é clicado, esse erro é retornado: `Requested URL '…' was not found.`

Além disso, você pode usar um aprimoramento para desativar URLs gerados em builds anteriores. Esse recurso está desativado por padrão. Você pode entrar em contato com [Atendimento ao cliente](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para ativar esse recurso.

Se estiver executando na build 19.1.4, você poderá enfrentar problemas com deliveries de notificação por push usando links de rastreamento ou deliveries usando tags âncora. Em caso afirmativo, recomendamos que você desative a assinatura do URL.

Cloud Services Como cliente do Campaign hospedado, gerenciado ou híbrido, você deve entrar em contato com [Atendimento ao cliente](https://helpx.adobe.com/br/enterprise/using/support-for-experience-cloud.html) para desativar a assinatura do URL.

Se você estiver executando o Campaign em uma arquitetura híbrida, antes de habilitar a assinatura do URL, verifique se a instância hospedada do mid-sourcing foi atualizada da seguinte maneira:

* Primeiro, a instância de marketing no local
* Em seguida, atualize para a mesma versão que a instância de marketing local ou para uma versão ligeiramente superior

Caso contrário, alguns destes problemas poderão ocorrer:

* Antes que a instância mid-sourcing seja atualizada, os URLs são enviados sem assinatura por meio dessa instância.
* Depois que a instância mid-sourcing for atualizada e a assinatura do URL for ativada em ambas as instâncias, os URLs enviados anteriormente sem assinatura serão rejeitados. O motivo é que uma assinatura é solicitada pelos arquivos de rastreamento que foram fornecidos pela instância de marketing.

Para desativar URLs gerados em builds anteriores, siga estas etapas em todos os servidores do Campaign ao mesmo tempo:

1. No arquivo de configuração do servidor (`serverConf.xml`), altere o **blockRedirectForUnsignedTrackingLink** opção para **true**.
1. Reinicie o `nlserver` serviço.
1. No `tracking` servidor, reinicie o `web` (apache2 no Debian, httpd no CentOS/RedHat, IIS no Windows).

Para habilitar a assinatura do URL, siga estas etapas em todos os servidores do Campaign ao mesmo tempo:

1. No arquivo de configuração do servidor (`serverConf.xml`), alteração **signEmailLinks** opção, para **true**.
1. Reinicie o serviço **nlserver**.
1. No `tracking` servidor, reinicie o `web` (apache2 no Debian, httpd no CentOS/RedHat, IIS no Windows).

## Restrição de dados

Certifique-se de que as senhas criptografadas não estejam acessíveis a um usuário autenticado de baixo privilégio. Para fazer isso, restrinja o acesso somente aos campos de senha ou à entidade inteira (precisa de uma build >= 8770).

Esta restrição permite que você remova os campos de senhas, mas deixe a conta externa acessível a partir da interface para todos os usuários. [Saiba mais](../../configuration/using/restricting-pii-view.md).

Para fazer isso, siga as etapas abaixo:

1. Navegue até o **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** pasta do explorador do Campaign.

1. Criar um esquema de dados, como um **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. Escolher **[!UICONTROL External Account]** (extAccount).

1. Na última tela do assistente, edite seu novo &quot;srcSchema&quot; para restringir o acesso a todos os campos de senha:

   Você pode substituir o elemento principal (`<element name="extAccount" ... >`) por:

   ```sql
   <element name="extAccount">
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
       <element name="s3Account">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
       </element>
       <element name="wapPush">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
       <element name="mms">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
   </element>
   ```

   Então, seu srcSchema estendido pode se parecer com:

   ```sql
   <srcSchema _cs="External Accounts (cus)" created="2017-05-12 07:53:49.691Z" createdBy-id="0"
               desc="Definition of external accounts (Email, SMS...) used by the modules"
               entitySchema="xtk:srcSchema" extendedSchema="nms:extAccount" img="" label="External Accounts"
               labelSingular="External account" lastModified="2017-05-12 08:33:49.365Z"
               mappingType="sql" md5="E9BB0CD6A4375F500027C86EA854E101" modifiedBy-id="0"
               name="extAccount" namespace="cus" xtkschema="xtk:srcSchema">
       <createdBy _cs="Administrator (admin)"/>
       <modifiedBy _cs="Administrator (admin)"/>
       <element name="extAccount">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
           <element name="s3Account">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
           </element>
           <element name="wapPush">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
           <element name="mms">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
       </element>
   </srcSchema>    
   ```

   >[!NOTE]
   >
   >Você pode substituir `$(loginId) = 0 or $(login) = 'admin'` com `hasNamedRight('admin')` para permitir que todos os usuários com direitos administrativos vejam essas senhas.

## Páginas do Protect com PI

Recomendamos enfaticamente que os clientes locais protejam as páginas que podem conter informações pessoais (PIs), como mirror pages, aplicativos web, etc.

O objetivo desse procedimento é impedir que essas páginas sejam indexadas, evitando assim um possível risco de segurança. Estes são alguns artigos úteis:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

Para proteger suas páginas, siga estas etapas:

1. Adicionar um `robots.txt` arquivo na raiz do servidor Web (Apache ou IIS). Este é o conteúdo do arquivo:

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Para o IIS, consulte [esta página](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Para o Apache, você pode colocar o arquivo em **/var/www/robots.txt** (Debian).

1. Às vezes, adicionar um **robôs.txt** o arquivo não é suficiente em termos de segurança. Por exemplo, se outro site contiver um link para sua página, ele poderá aparecer em um resultado de pesquisa.

   Além do **robôs.txt** arquivo, aconselha-se adicionar um **X-Robots-Tag** cabeçalho. Você pode fazer isso no Apache ou IIS e no **serverConf.xml** arquivo de configuração.

   Para obter mais informações, consulte [este artigo](https://developers.google.com/search/reference/robots_meta_tag).


## Solicitações de Privacidade

Consulte [esta página](../../platform/using/privacy-management.md) para obter informações gerais sobre o que é a Gestão de privacidade e quais são as etapas de implementação no Adobe Campaign. Além disso, você encontrará as práticas recomendadas e uma visão geral do processo de usuários e personas.
