---
product: campaign
title: Solução de problemas com o IMS
description: Solução de problemas com o IMS
feature: Configuration
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
TQID: https://experienceleague.adobe.com/cUoMAlp8ExhammApiilFqRyrOkyyqxk1om0AifZVxb0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 501
ht-degree: 100%

---

# Solução de problemas com o IMS{#ims-troubleshooting}


As dicas de solução de problemas a seguir ajudarão os clientes **locais** e **híbridos** a resolver os problemas mais comuns que ocorrem ao usar a integração do IMS. Para clientes **hospedados**, entre em contato com a Adobe.

**Conta externa**

Só deve existir **uma** conta externa com as seguintes configurações:

* **Internal Name**: Adobe_Marketing_Cloud
* **Type**: Adobe Experience Cloud

Exclua qualquer conta externa duplicada que tenha as mesmas configurações.

**Contexto do produto**

Se a conta externa tiver um campo **Product Context**, verifique se o valor está definido como **dma_campaign_classic**

Verifique se o contexto do produto é o mesmo para o Campaign e Experience Cloud.

Por exemplo, se o **Contexto do Produto** não aparecer, o contexto padrão do produto deve ser **dma_campaign** tanto no Campaign quanto na Experience Cloud. Se o campo **Contexto do Produto** aparecer, o contexto padrão do produto deverá ser **dma_campaign_classic** tanto no Campaign quanto na Experience Cloud.

**[!UICONTROL IMS Server URL]**

Na conta externa da **Adobe Marketing Cloud** do Campaign, verifique se o **[!UICONTROL IMS Server URL]** está definido como `adobeid-na1.services.adobe.com` ou `ims-na1.adobelogin.com`. Verifique se as instâncias de estágio e de produção apontam para o mesmo ponto final de produção IMS.

**Association mask**

* Verifique se o usuário que está tentando fazer logon faz parte de um grupo de operadores no Painel Enterprise.
* Verifique se **[!UICONTROL Association Mask]** é um prefixo do nome do grupo de operadores do usuário no Painel Enterprise.
* Verifique se não há espaços em branco e erros de ortografia.
* Verifique se os nomes dos grupos de operadores no Campaign não foram alterados e respeitam a seguinte sintaxe:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Escopo**

Os escopos definidos na conta externa do Campaign devem ser um subconjunto daqueles provisionados pelo IMS.

**URL de retorno**

O **URL de retorno de chamada** deve ser adicionado à lista de permissões e iniciar por &quot;https://&quot;. Verifique se a **URL de Retorno** está vinculada à instância correspondente. Por exemplo, a instância de produção deve redirecionar para a URL de produção.

**ID do cliente e segredo**

A ID do cliente corresponde à conta externa do Campaign e a provisionada pela IMS.

Verifique se o segredo do cliente inserido está correto.

**Reiniciar o servidor**

Reinicie o servidor se alguma alteração for feita nas configurações acima na conta externa do Campaign

**Tipos de erros comuns e possíveis soluções**

* O usuário é redirecionado para a página adobe.com:

  Há um problema com a **[!UICONTROL Callback URL]**. Consulte as etapas anteriores para verificar a configuração **[!UICONTROL Callback URL]**.

* Mensagem &quot;O login não tem nenhum direito com a expressão correspondente&quot;:

  Consulte as etapas anteriores para verificar a configuração de **[!UICONTROL Association Mask]** e de grupos de operador.

* O usuário não pode acessar a página de login da Adobe id:

  Consulte as etapas anteriores para verificar a configuração do escopo.

**Problemas de cache do WebView2**

Se tiver problemas ao entrar no **[!UICONTROL Client Console]** com sua Adobe ID, tente limpar o cache local do WebView2. Na maioria dos casos, isso resolve o problema. Siga as etapas abaixo:

1. Feche o **[!UICONTROL Client Console]** e pare qualquer processo `nlclient` em execução.

1. Exclua todas as pastas `webview2` e `webview2Cache` dos seguintes locais:

   * `C:\ProgramData\Neolane\NL_5\nlclient\`
   * `C:\Users\<username>\AppData\Roaming\Neolane\NL_5\nlclient\`

1. Reinicie o **[!UICONTROL Client Console]** e faça logon com sua Adobe ID. As pastas de cache serão automaticamente recriadas na próxima inicialização.
