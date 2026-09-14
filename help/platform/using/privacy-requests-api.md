<?xml version="1.0" encoding="UTF-8"?>
<xliff xmlns="urn:oasis:names:tc:xliff:document:1.2" xmlns:okp="okapi-framework:xliff-extensions" xmlns:its="http://www.w3.org/2005/11/its" xmlns:itsxlf="http://www.w3.org/ns/its-xliff/" version="1.2" its:version="2.0">
<file original="help/platform/using/privacy-requests-api.md.mdnouisc" source-language="en-US" target-language="en-XX" datatype="x-text/markdown">
<body>
<trans-unit id="tu17" xml:space="preserve">
<source xml:lang="en-US">https://experienceleague.adobe.com/pt-br/tools/campaign-api</source>
<target xml:lang="en-XX">https://experienceleague.adobe.com/pt-br/tools/campaign-api</target>
</trans-unit>
<trans-unit id="tu1" restype="x-YAML_METADATA_HEADER_VALUE" xml:space="preserve">
<source xml:lang="en-US">Automatic Privacy request process</source>
<target xml:lang="en-XX">Processo automático de solicitação de privacidade</target>
</trans-unit>
<trans-unit id="tu2" restype="x-YAML_METADATA_HEADER_VALUE" xml:space="preserve">
<source xml:lang="en-US">Learn how to setup an automatic Privacy request process</source>
<target xml:lang="en-XX">Saiba como configurar um processo automático de solicitação de privacidade</target>
</trans-unit>
<trans-unit id="tu3" xml:space="preserve">
<source xml:lang="en-US">Automatic Privacy request process</source>
<target xml:lang="en-XX">Processo automático de solicitação de privacidade</target>
</trans-unit>
<trans-unit id="tu4" xml:space="preserve">
<source xml:lang="en-US">Adobe Campaign provides an <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>API<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> which allows you to setup an automatic Privacy request process.</source>
<target xml:lang="en-XX">O Adobe Campaign fornece uma <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>API<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> que permite configurar um processo automático de solicitação de acesso a dados pessoais.</target>
</trans-unit>
<trans-unit id="tu5" xml:space="preserve">
<source xml:lang="en-US">With the API, the general Privacy process is the same as <ph id="1" ctype="x-LINK">[</ph>using the interface<ph id="2" ctype="x-LINK">](privacy-requests-ui.md)</ph>. The only difference is the creation of the Privacy request. Instead of creating the request in Adobe Campaign, a POST containing the request information is sent to Campaign. For every request, a new entry is added in the <ph id="3" ctype="x-STRONG_EMPHASIS">**[!UICONTROL Privacy Requests]**</ph> screen. The Privacy technical workflows then process the request, the same way as for a request added using the interface.</source>
<target xml:lang="en-XX">Com a API, o processo de privacidade geral é o mesmo que o <ph id="1" ctype="x-LINK">[</ph>utilizado com a interface<ph id="2" ctype="x-LINK">](privacy-requests-ui.md)</ph>. A única diferença é a criação da solicitação de acesso a dados pessoais. Em vez de criar a solicitação no Adobe Campaign, um POST contendo as informações da solicitação é enviado para o Campaign. Para cada solicitação, uma nova entrada é adicionada na tela <ph id="3" ctype="x-STRONG_EMPHASIS">**[!UICONTROL Privacy Requests]**</ph>. Os fluxos de trabalho técnicos de privacidade processam a solicitação, da mesma forma que uma solicitação adicionada usando a interface.</target>
</trans-unit>
<trans-unit id="tu6" xml:space="preserve">
<source xml:lang="en-US">If you're using the API to submit Privacy requests, we recommend that you leave the <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>2-step process<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> activated for the first Delete requests, in order to test the returned data. When your tests are finished, you can deactivate the 2-step process so that the Delete request process can run automatically.</source>
<target xml:lang="en-XX">Se você estiver usando a API para enviar solicitação de acesso a dados pessoais, recomendamos que ative o <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>processo de duas etapas<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> durante as primeiras solicitações de exclusão para testar os dados retornados. Após a conclusão dos testes, o processo de duas etapas pode ser desativado para que o processo de solicitação de exclusão possa ser executado automaticamente.</target>
</trans-unit>
<trans-unit id="tu7" xml:space="preserve">
<source xml:lang="en-US">The <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL CreateRequestByName]**</ph> JS API is defined as follows.</source>
<target xml:lang="en-XX">A API JS <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL CreateRequestByName]**</ph> é definida da seguinte maneira.</target>
</trans-unit>
<trans-unit id="tu8" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></target>
</trans-unit>
<trans-unit id="tu9" xml:space="preserve">
<source xml:lang="en-US">If you were using the <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>gdprRequest<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> API, you can still use it but it is recommended to use the new <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>privacyRequest<ph id="4" ctype="x-STRONG_EMPHASIS">**</ph> API.</source>
<target xml:lang="en-XX">Se você estava usando a API <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>gdprRequest<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, ainda é possível usá-la, mas é recomendável usar a nova API <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>privacyRequest<ph id="4" ctype="x-STRONG_EMPHASIS">**</ph> .</target>
</trans-unit>
<trans-unit id="tu10" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!IMPORTANT">[!IMPORTANT]</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!IMPORTANT">[!IMPORTANT]</ph></target>
</trans-unit>
<trans-unit id="tu11" xml:space="preserve">
<source xml:lang="en-US">The <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL Privacy Data Right]**</ph> named right is required to use the API.</source>
<target xml:lang="en-XX">O direito nomeado <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL Privacy Data Right]**</ph> é necessário para usar a API.</target>
</trans-unit>
<trans-unit id="tu12" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></target>
</trans-unit>
<trans-unit id="tu13" xml:space="preserve">
<source xml:lang="en-US">The 'regulation' field is only available if you are using Campaign Classic 20.2 (build 9178+).</source>
<target xml:lang="en-XX">O campo "Regulation" só estará disponível no Campaign Classic 20.2 (build 9178+).</target>
</trans-unit>
<trans-unit id="tu14" xml:space="preserve">
<source xml:lang="en-US">If you are migrating to 20.2 and if you were already using the API, you must add the ‘regulation’ field as shown above. If you are using a previous build, you can continue to use the API without the ‘regulation’ field.</source>
<target xml:lang="en-XX">Se você estiver migrando para a versão 20.2 e já estiver usando a API, precisará adicionar o campo "regulation", como mostrado acima. Se você estiver usando uma build anterior, poderá continuar a usar a API sem o campo "regulation".</target>
</trans-unit>
<trans-unit id="tu15" xml:space="preserve">
<source xml:lang="en-US">Invoking the API externally</source>
<target xml:lang="en-XX">Chamada de API externamente</target>
</trans-unit>
<trans-unit id="tu16" xml:space="preserve">
<source xml:lang="en-US">Here is an example of how you can invoke the API externally (authentication via the API and details about the Privacy API specifically). For more information on the Privacy API, consult the <ph id="1" ctype="x-LINK">&lbrack;</ph>API documentation<ph id="2" ctype="x-LINK">[#$tu17]</ph>. You can also consult the <ph id="3" ctype="x-LINK">[</ph>Web service calls documentation<ph id="4" ctype="x-LINK">](../../configuration/using/web-service-calls.md)</ph>.</source>
<target xml:lang="en-XX">Este é um exemplo de como chamar a API externamente (autenticação por meio da API e detalhes específicos sobre a API de privacidade). Para obter mais informações sobre a API de privacidade, consulte a <ph id="1" ctype="x-LINK">&lbrack;</ph>documentação da API<ph id="2" ctype="x-LINK">[#$tu17]</ph>. Você também pode consultar a <ph id="3" ctype="x-LINK">[</ph>documentação de chamadas de serviço da web<ph id="4" ctype="x-LINK">](../../configuration/using/web-service-calls.md)</ph>.</target>
</trans-unit>
<trans-unit id="tu18" xml:space="preserve">
<source xml:lang="en-US">First of all, you need to perform the authentication via the API:</source>
<target xml:lang="en-XX">Primeiro, é necessário executar a autenticação por meio da API:</target>
</trans-unit>
<trans-unit id="tu19" xml:space="preserve">
<source xml:lang="en-US">Download the <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>xtk<ph id="2" ctype="x-inline-directive">:session**</ph> WSDL via this url: <ph id="4" ctype="x-STRONG_EMPHASIS">**`&lt;server url>`</ph>/nl/jsp/schemawsdl.jsp?schema=xtk<ph id="6" ctype="x-inline-directive">:session**</ph>.</source>
<target xml:lang="en-XX">Baixe o WSDL <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>xtk<ph id="2" ctype="x-inline-directive">:session**</ph> por meio deste URL: <ph id="4" ctype="x-STRONG_EMPHASIS">**`&lt;server url>`</ph>/nl/jsp/schemawsdl.jsp?schema=xtk<ph id="6" ctype="x-inline-directive">:session**</ph>.</target>
</trans-unit>
<trans-unit id="tu20" xml:space="preserve">
<source xml:lang="en-US">Use the "Logon" method and pass in a username and password as parameters in the request. You will get a response containing a session token. Here is an example using SoapUI.</source>
<target xml:lang="en-XX">Use o método "Logon" e forneça um nome de usuário e senha como parâmetros na solicitação. Você receberá uma resposta contendo um token de sessão. Veja um exemplo de utilização de SoapUI.</target>
</trans-unit>
<trans-unit id="tu21" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-IMAGE">![](assets/do-not-localize/privacy-api.png)</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-IMAGE">![](assets/do-not-localize/privacy-api.png)</ph></target>
</trans-unit>
<trans-unit id="tu22" xml:space="preserve">
<source xml:lang="en-US">Use the returned Session Token as the authentication for all subsequence API calls. It expires after 24 hours.</source>
<target xml:lang="en-XX">Use o token de sessão retornado como autenticação para todas as chamadas de API subsequentes. Ela expira após 24 horas.</target>
</trans-unit>
<trans-unit id="tu23" xml:space="preserve">
<source xml:lang="en-US">Then invoke the Privacy API:</source>
<target xml:lang="en-XX">Em seguida, chame a API de privacidade:</target>
</trans-unit>
<trans-unit id="tu24" xml:space="preserve">
<source xml:lang="en-US">Download the WSDL from this URL: <ph id="1" ctype="x-STRONG_EMPHASIS">**`&lt;server url>`</ph>/nl/jsp/schemawsdl.jsp?schema=nms<ph id="3" ctype="x-inline-directive">:privacyRequest**</ph>.</source>
<target xml:lang="en-XX">Baixe o WSDL por meio deste URL: <ph id="1" ctype="x-STRONG_EMPHASIS">**`&lt;server url>`</ph>/nl/jsp/schemawsdl.jsp?schema=nms<ph id="3" ctype="x-inline-directive">:privacyRequest**</ph>.</target>
</trans-unit>
<trans-unit id="tu25" xml:space="preserve">
<source xml:lang="en-US">Use <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL CreateRequestByName]**</ph> to create a specific Privacy request.</source>
<target xml:lang="en-XX">Use <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL CreateRequestByName]**</ph> para criar uma solicitação específica de acesso a dados pessoais.</target>
</trans-unit>
<trans-unit id="tu26" xml:space="preserve">
<source xml:lang="en-US">Here is an example using the <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL CreateRequestByName]**</ph>. Note how we use the session token provided above as authentication. The response is the ID of the created request.</source>
<target xml:lang="en-XX">Veja um exemplo de uso de <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL CreateRequestByName]**</ph>. Observe como usamos o token de sessão fornecido acima como autenticação. A resposta é a ID da solicitação criada.</target>
</trans-unit>
<trans-unit id="tu27" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-IMAGE">![](assets/do-not-localize/privacy-api-2.png)</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-IMAGE">![](assets/do-not-localize/privacy-api-2.png)</ph></target>
</trans-unit>
<trans-unit id="tu28" xml:space="preserve">
<source xml:lang="en-US">To help you perform the steps above, consider the following:</source>
<target xml:lang="en-XX">Para ajudar você a executar as etapas acima, considere o seguinte:</target>
</trans-unit>
<trans-unit id="tu29" xml:space="preserve">
<source xml:lang="en-US">You can use a <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>queryDef<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> on the <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>nms<ph id="4" ctype="x-inline-directive">:gdprRequest**</ph> schema to check the status of the Access request.</source>
<target xml:lang="en-XX">Você pode usar uma <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>queryDef<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> no esquema <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>nms<ph id="4" ctype="x-inline-directive">:gdprRequest**</ph> para verificar o status da solicitação de acesso.</target>
</trans-unit>
<trans-unit id="tu30" xml:space="preserve">
<source xml:lang="en-US">You can use a <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>queryDef<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> on the <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>nms<ph id="4" ctype="x-inline-directive">:gdprRequestData**</ph> schema to get the result of the Access request.</source>
<target xml:lang="en-XX">Você pode usar uma <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>queryDef<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> no esquema <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>nms<ph id="4" ctype="x-inline-directive">:gdprRequestData**</ph> para obter o resultado da solicitação de acesso.</target>
</trans-unit>
<trans-unit id="tu31" xml:space="preserve">
<source xml:lang="en-US">To be able to download the XML file from <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>"$(serverUrl)'/nms/gdpr.jssp?id='@id"<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, you must be logged in and accessing it from an IP that is included in the allowlist. To do this, create a web application allowing you to access the file generated by the JSSP.</source>
<target xml:lang="en-XX">Para baixar o arquivo XML a partir de <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>"$(serverUrl)'/nms/gdpr.jssp?id='@id"<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, é preciso estar conectado e acessá-lo a partir de um IP incluso na lista de permissões. Para fazer isso, crie um aplicativo web que permita acessar o arquivo gerado pelo JSSP.</target>
</trans-unit>
<trans-unit id="tu32" xml:space="preserve">
<source xml:lang="en-US">Invoking the API from a JS</source>
<target xml:lang="en-XX">Chamar a API a partir de um JS</target>
</trans-unit>
<trans-unit id="tu33" xml:space="preserve">
<source xml:lang="en-US">Here is an example of how you can invoke the API from a JS within Campaign Classic.</source>
<target xml:lang="en-XX">Este é um exemplo de como você pode chamar a API a partir de um JS dentro do Campaign Classic.</target>
</trans-unit>
<trans-unit id="tu34" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></target>
</trans-unit>
<trans-unit id="tu35" xml:space="preserve">
<source xml:lang="en-US">The 'regulation' field is only available if you are using Campaign Classic 20.2 (build 9178+).</source>
<target xml:lang="en-XX">O campo “Regulation” só estará disponível no Campaign Classic 20.2 (build 9178+).</target>
</trans-unit>
<trans-unit id="tu36" xml:space="preserve">
<source xml:lang="en-US">If you are migrating to 20.2 and if you were already using the API, you must add the ‘regulation’ field. If you are using a previous build, you can continue to use the API without the ‘regulation’ field.</source>
<target xml:lang="en-XX">Se você estiver migrando para a versão 20.2 e já estiver usando a API, precisará adicionar o campo “regulation”. Se você estiver usando uma build anterior, poderá continuar a usar a API sem o campo “regulation”.</target>
</trans-unit>
<trans-unit id="tu37" xml:space="preserve">
<source xml:lang="en-US">If you are <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>using a previous build (with GDPR package)<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, you can continue to use the API without the ‘regulation’ field as shown below:</source>
<target xml:lang="en-XX">Se você estiver <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>usando uma build anterior (com o pacote RGPD)<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> é possível continuar a usar a API sem o campo “regulation”, como mostrado abaixo:</target>
</trans-unit>
<trans-unit id="tu38" xml:space="preserve">
<source xml:lang="en-US">If you are <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>migrating to 20.2<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> and if you were already using the API, you must add the ‘regulation’ field as shown below:</source>
<target xml:lang="en-XX">Se você estiver <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>migrando para a versão 20.2<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> e já estiver usando a API, será preciso adicionar o campo “regulation”, como mostrado abaixo:</target>
</trans-unit>
<trans-unit id="tu39" xml:space="preserve">
<source xml:lang="en-US">If you are <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>using Campaign Classic 20.2 (build 9178+) or above<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, the 'regulation' field is optional, as shown below:</source>
<target xml:lang="en-XX">Se você estiver <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>usando o Campaign Classic 20.2 (build 9178+) ou superior<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, o campo “regulation” é opcional, como mostrado abaixo:</target>
</trans-unit>
</body>
</file>
</xliff>