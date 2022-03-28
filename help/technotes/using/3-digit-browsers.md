---
product: campaign
title: Componentes da Web do Campaign e versão 100 nos navegadores Chrome Firefox e Edge
description: Componentes da Web do Campaign e versão 100 em navegadores Chrome, Firefox e Edge
exl-id: 2016279a-7b02-4399-b2ed-9a15456de816
source-git-commit: b8329e24f07ec8b3dd89f655b47699f130266008
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# A versão de 3 dígitos do navegador afeta os componentes da Web do Campaign {#version-100}

O Google e o Mozilla estão alertando que o Chrome e o Firefox podem quebrar alguns sites devido às próximas versões de 3 dígitos.

O Chrome v100 está definido para lançamento em **29 de março de 2022** e Firefox v100 em **3 de maio de 2022**.

A Microsoft lançou o Edge v100 anteriormente em março de 2022.

A alteração no número da versão de 2 para 3 dígitos pode causar alguns problemas ao visitar sites que não estão preparados para essa alteração. Algumas páginas da Web podem parar de exibir corretamente nessas novas versões do navegador.

A compatibilidade dos principais sites foi testada com antecedência. Se houver problemas com sites que não possam ser corrigidos antes que essas versões sejam lançadas, as empresas terão planos de backup prontos para garantir que os sites não sejam afetados.

Possíveis problemas ou perda de funcionalidade no site são originados na sequência de agente do usuário que os navegadores enviam para sites que você está visitando: o agente do usuário é uma string enviada pelo navegador para o site para informar ao site qual navegador e versão você está usando, e tecnologia associada. Quando seu navegador envia uma solicitação a um site, ele se identifica com a sequência do agente do usuário antes de recuperar o conteúdo solicitado. Os dados na sequência do agente do usuário ajudam o site a fornecer o conteúdo em um formato adequado ao seu navegador. A versão do agente do usuário é incrementada para corresponder ao número de versão do navegador. Mover de 2 para 3 dígitos pode causar problemas.

## Você será afetado?{#version-100-impact}

O Adobe recomenda que você teste seus aplicativos Web do Campaign, incluindo formulários web e pesquisas, para garantir que eles ainda funcionarão bem com essas novas versões do navegador.

Essa recomendação se aplica a todas as aplicações web e, especialmente, se você tiver incluído o código JavaScript.

Você deve verificar com todos os navegadores, dispositivos móveis e desktop.

## Como testar?{#version-100-test}

Você pode configurar seus navegadores para relatar a versão como 100 agora, relatar e corrigir todos os problemas que encontrar.

Com essas configurações, o navegador envia a nova sequência de agente do usuário para sites, indicando que o navegador é a v100. Se tiver problemas com os formulários web, crie um bug no editor do navegador. Considere a reconstrução desses formulários web antes que essas atualizações estejam amplamente disponíveis.

### Testar com o Firefox 100{#test-firefox-100}

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

Para alterar o agente de usuário de volta para o padrão, basta voltar para `about:config` e procurar `general.useragent.override` novamente.  Quando for exibido, clique no ícone da lixeira para excluir a configuração e reinicie o navegador.

### Teste com o Chrome 100{#test-chrome-100}

Para testar o agente do usuário do Google Chrome 100 em seus próprios aplicativos da Web, você pode habilitar esse teste usando as seguintes etapas:

1. Abra o Chrome, digite `chrome://flags` na barra de endereços e pressione enter.
1. Pesquisar `Force major version to 100 in User-Agent` no campo de pesquisa e ative-o conforme mostrado abaixo.

   ![](assets/force-user-agent-chrome.png)

1. Reinicie o navegador.
1. Feche o `chrome://flags` guia .

Para alterar o agente do usuário de volta ao seu padrão, basta seguir esse processo e alterar a configuração do sinalizador para `Default` e reinicie o navegador.


### Testar com o Microsoft Edge 100{#test-ms-edge-100}

A partir da versão 97, os proprietários de sites podem emular essa versão ativando o sinalizador de experimento  `#force-major-version-to-100` em `edge://flags`.

1. Abra o Microsoft Edge, digite `edge://flags` na barra de endereços e pressione enter.
1. Procurar por `force-major-version-to-100` e ative-o conforme mostrado abaixo.

   ![](assets/force-user-agent-edge.png)

1. Reinicie o navegador.
1. Feche o `edge://flags` guia .

Para alterar o agente do usuário de volta ao seu padrão, basta seguir esse processo e alterar a configuração do sinalizador para `Default` e reinicie o navegador.
