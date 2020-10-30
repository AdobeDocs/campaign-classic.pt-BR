---
title: Solução de problemas com o IMS
seo-title: Solução de problemas com o IMS
description: Solução de problemas com o IMS
seo-description: null
page-status-flag: never-activated
uuid: 5db95afc-8cbf-4ec3-b58f-504486fe4a40
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: e31db11a-ad8e-4fd0-bab7-0df1079231c9
translation-type: ht
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: ht
source-wordcount: '419'
ht-degree: 100%

---


# Solução de problemas com o IMS{#ims-troubleshooting}

As seguintes dicas de solução de problemas ajudarão os clientes **no local** a resolverem os problemas mais comuns que ocorrem ao usar a integração IMS. Para clientes **hospedados**, entre em contato com a Adobe.

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

Na conta externa do Campaign **Adobe Marketing Cloud**, verifique se o **[!UICONTROL IMS Server URL]** é [adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/) ou [ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/). Verifique se as instâncias de estágio e de produção apontam para o mesmo ponto final de produção IMS.

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

**Reinício do servidor**

Reinicie o servidor se alguma alteração for feita nas configurações acima na conta externa do Campaign

**Tipos de erros comuns e possíveis soluções**

* O usuário é redirecionado para a página adobe.com:

   Há um problema com a **[!UICONTROL Callback URL]**. Consulte as etapas anteriores para verificar a configuração **[!UICONTROL Callback URL]**.

* Mensagem &quot;O login não tem nenhum direito com a expressão correspondente&quot;:

   Consulte as etapas anteriores para verificar a configuração de **[!UICONTROL Association Mask]** e de grupos de operador.

* O usuário não pode acessar a página de login da Adobe id:

   Consulte as etapas anteriores para verificar a configuração do escopo.

