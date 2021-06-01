---
product: campaign
title: Privacidade
description: Saiba mais sobre as práticas recomendadas relacionadas à privacidade.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 30%

---

# Privacidade {#privacy}

## Solicitações de Privacidade

O Adobe Campaign oferece um conjunto de ferramentas que ajuda na Conformidade da Privacidade para o GDPR e CCPA.

Consulte [esta página](../../platform/using/privacy-management.md) para obter informações gerais sobre o que é o Gerenciamento de privacidade e as etapas de implementação no Adobe Campaign. Além disso, você encontrará as práticas recomendadas e uma visão geral do processo de usuários e personas.

## Personalização de URL {#url-personalization}

Ao adicionar links personalizados ao seu conteúdo, sempre evite qualquer personalização na parte do nome do host do URL para evitar possíveis brechas de segurança. Os exemplos a seguir nunca devem ser usados em todos os atributos de URL &lt;`a href="">` ou `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Recomendações

Para validar e garantir que você não está usando acima, execute uma query na tabela de rastreamento de URL por meio do [Editor de Consulta Genérico de Campanha](../../platform/using/steps-to-create-a-query.md) ou crie um workflow com critérios de filtro na [atividade de query](../../workflow/using/query.md).

Exemplo:

1. Crie um workflow e adicione uma atividade Query . Saiba mais.

1. Abra a atividade Query e crie um filtro na tabela nmsTrackingUrl da seguinte maneira: o URL de origem começa com http://&lt;% ou o URL de origem começa com https://&lt;%.

1. Execute o fluxo de trabalho e verifique se há resultado.

1. Em caso positivo, abra a transição de saída para a visualização da lista de URLs.

<img src="assets/privacy-query-dynamic-url.png">

### Mecanismo de assinatura

Para melhorar a segurança, um novo mecanismo de assinatura para rastrear links em emails foi introduzido na Build 19.1.4 (9032@3a9dc9c) e está disponível na Build 19.1.4 (9032@3a9dc9c) e no Campaign 20.2. Essa opção é habilitada por padrão para todos os clientes.

>[!NOTE]
>
>Quando um URL assinado mal formado é clicado, ele retornará o seguinte erro: &quot;O URL solicitado &#39;... &#39; não foi encontrado.&quot;

Além disso, a partir da versão 20.2 e [!DNL Gold Standard] do Campaign, os clientes hospedados e híbridos poderão usar um aprimoramento para desativar URLs gerados em compilações anteriores. Essa opção está desabilitada por padrão. É possível entrar em contato com o [Atendimento ao cliente](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para ativar esse recurso.

Para ativar esse novo recurso, os clientes locais precisam seguir estas etapas em todos os servidores do Campaign:

1. No arquivo de configuração do servidor (serverConf.xml), altere **blockRedirectForUnsignedTrackingLink** para **true**.
1. Reinicie o serviço **nlserver**.
1. No servidor de rastreamento, reinicie o servidor da Web (apache2 em Debian, httpd em CentOS/RedHat, IIS no Windows).

Os clientes que estiverem executando em [!DNL Gold Standard] 19.1.4 podem enfrentar problemas com os deliveries de notificação por push usando o link de rastreamento ou com deliveries usando tags de âncora. Em caso positivo, o Adobe recomenda desativar o novo mecanismo de assinatura para links de rastreamento:

**Os** clientes hospedados e híbridos devem entrar em contato com o  [Atendimento ao ](https://helpx.adobe.com/br/enterprise/using/support-for-experience-cloud.html) cliente para desativar esse mecanismo.

**Os** clientes locais devem seguir a etapa abaixo:

1. No arquivo de configuração do servidor (serverConf.xml), altere **signEmailLinks** para **false**.
1. Reinicie o serviço **nlserver**.
1. No servidor de rastreamento, reinicie o servidor da Web (apache2 em Debian, httpd em CentOS/RedHat, IIS no Windows).

## Restrição de dados

Você precisa ter certeza que as senhas criptografadas não estarão acessíveis a um usuário autenticado de baixo privilégio. Para fazer isso, há duas maneiras principais: restrinja o acesso apenas a campos de senha ou à entidade inteira (é necessário um build >= 8770).

Esta restrição permite que você remova os campos de senhas, mas deixe a conta externa acessível a partir da interface para todos os usuários. Consulte [esta página](../../configuration/using/restricting-pii-view.md).

1. Vá em **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**.

1. Crie um novo **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. Escolha **[!UICONTROL External Account]** (extAccount).

1. Na última tela do assistente, você pode editar seu novo srcSchema para restringir o acesso a todos os campos de senha:

   Você pode substituir o elemento principal (`<element name="extAccount" ... >`) por:

   ```
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

   ```
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
   >Você pode substituir `$(loginId) = 0 or $(login) = 'admin'` por `hasNamedRight('admin')` para permitir que todos os usuários administradores vejam essas senhas.

## Proteção de páginas contendo PII

Recomendamos enfaticamente que os clientes locais protejam as páginas que podem conter informações pessoais, como mirror pages, aplicativos web, etc.

O objetivo desse procedimento é evitar que essas páginas sejam indexadas, evitando assim um risco potencial à segurança. Estes são alguns artigos úteis:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

Para proteger suas páginas, siga estas etapas:

1. Adicione um arquivo robots.txt na raiz do seu servidor da Web (Apache ou IIS). Aqui está o conteúdo do arquivo:

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Para IIS, consulte [esta página](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Para o Apache, você pode colocar o arquivo em **/var/www/robots.txt** (Debian).

1. Às vezes, adicionar um arquivo **robots.txt** não é suficiente em termos de segurança. Por exemplo, se outro site contiver um link para sua página, ele poderá aparecer em um resultado de pesquisa.

Além do arquivo **robots.txt**, é recomendável adicionar um cabeçalho **X-Robots-Tag**. Você pode fazer isso no Apache ou IIS e no arquivo de configuração **serverConf.xml**.

Para obter mais informações, consulte [este artigo](https://developers.google.com/search/reference/robots_meta_tag).
