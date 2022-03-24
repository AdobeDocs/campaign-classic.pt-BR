---
product: campaign
title: Componentes da Web do Campaign e versão 100 em navegadores Chrome e Firefox
description: Componentes da Web do Campaign e versão 100 em navegadores Chrome e Firefox
hide: true
hidefromtoc: true
source-git-commit: 68049d1905524b644794799348bd6387b2afed0d
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# Componentes da Web do Campaign e versão 100 em navegadores Chrome e Firefox {#version-100}

## What {#what-version-100}

O Google e o Mozilla estão alertando que o Chrome e o Firefox podem quebrar alguns sites devido às próximas versões de 3 dígitos.
A alteração no número da versão de 2 para 3 dígitos pode causar alguns problemas ao visitar sites que não estão preparados para essa alteração. Algumas páginas da Web podem parar de exibir corretamente nessas novas versões do navegador.

Mozilla e Google estão testando com antecedência a compatibilidade de sites importantes. Se houver problemas com sites que não possam ser corrigidos antes que essas versões sejam lançadas, ambos terão planos de backup prontos para garantir que os sites não sejam afetados.

## Por quê {#why-version-100}

Possíveis problemas ou perda de funcionalidade no site se originam da sequência de agente do usuário que os navegadores enviam para sites que você está visitando : o agente do usuário é uma string enviada pelo navegador para o site para informar ao site qual navegador e versão você está usando, e tecnologia associada. Quando seu navegador envia uma solicitação a um site, ele se identifica com a sequência do agente do usuário antes de recuperar o conteúdo solicitado. Os dados na sequência do agente do usuário ajudam o site a fornecer o conteúdo em um formato adequado ao seu navegador. A versão do agente do usuário é incrementada para corresponder ao número de versão do navegador. Mover de 2 para 3 dígitos pode causar problemas.

## When {#when-version-100}

O Chrome v100 está definido para lançamento em **29 de março de 2022** e Firefox v100 em **3 de maio de 2022**.

## Em que {#where-version-100}

O Adobe recomenda que você teste seus aplicativos Web do Campaign, incluindo formulários web e pesquisas, e mirror pages de email, para garantir que eles ainda funcionarão bem com essas novas versões do navegador.

Essa recomendação se aplica a todas as aplicações web e, especialmente, se você tiver incluído o código JavaScript.

Você deve verificar ambos com Firefox e Chrome, dispositivos móveis e desktop.

## How {#how-version-100}

No Chrome e no Firefox Nightly, você pode configurar o navegador para relatar a versão como 100 no momento e corrigir todos os problemas encontrados.

### Firefox 100{#test-firefox-100}

Para testar suas páginas da Web com o Mozilla Firefox 100, você pode simular a alteração futura do agente de usuário em seus aplicativos Web, alterando manualmente a sequência do agente de usuário.

1. Abra o Firefox, insira `about:config` na barra de endereços e pressione enter.
1. Procurar por `general.useragent.override`.
1. Selecione &quot;String&quot; e clique no sinal de mais (+).

   ![](assets/force-user-agent-firefox.png)

1. Insira o seguinte texto no campo :

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. Clique no botão de marca de seleção azul para salvar a configuração.
1. Feche e reinicie o navegador.

Com essas configurações, o navegador envia a nova sequência de agente do usuário para sites, indicando que o navegador é o Firefox 100. Se tiver problemas com os formulários web, crie um novo relatório de erros para o Mozilla. Considere a reconstrução desses formulários web antes que essa alteração esteja amplamente disponível.

Para alterar o agente de usuário de volta para o padrão, basta voltar para `about:config` e procurar `general.useragent.override` novamente.  Quando for exibido, clique no ícone da lixeira para excluir a configuração e reinicie o navegador.

### Chrome 100{#test-chrome-100}

Para testar o agente do usuário do Google Chrome 100 em seus próprios aplicativos da Web, você pode habilitar esse teste usando as seguintes etapas:

1. Abra o Chrome, digite `chrome://flags` na barra de endereços e pressione enter.
1. Pesquisar `Force major version to 100 in User-Agent` no campo de pesquisa e ative-o conforme mostrado abaixo.

   ![](assets/force-user-agent-chrome.png)

1. Feche e reinicie o navegador.
1. Feche o `chrome://flags` tela.

Com essas configurações, o navegador envia a nova sequência de agente do usuário para sites, indicando que o navegador é o Chrome 100. Se tiver problemas com os sites visitados, crie um novo relatório de erros para o Google. Considere a reconstrução desses formulários web antes que essa alteração esteja amplamente disponível.

Para alterar o agente do usuário de volta ao seu padrão, basta seguir esse processo e alterar a configuração do sinalizador para `Default` e reinicie o navegador.
