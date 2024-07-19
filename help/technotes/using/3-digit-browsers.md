---
product: campaign
title: Componentes Web do Campaign e versão 100 nos navegadores Chrome Firefox e Edge
description: Componentes Web do Campaign e versão 100 em navegadores Chrome, Firefox e Edge
feature: Technote
exl-id: 2016279a-7b02-4399-b2ed-9a15456de816
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# Impactos na versão de 3 dígitos do navegador nos componentes Web do Campaign {#version-100}

A Google e a Mozilla estão avisando que o Chrome e o Firefox podem interromper alguns sites devido às próximas versões de 3 dígitos.

O Chrome v100 está definido para lançamento em **29 de março de 2022** e o Firefox v100 em **3 de maio de 2022**.

A Microsoft lançou o Edge v100 anteriormente em março de 2022.

A alteração no número da versão de 2 para 3 dígitos pode causar alguns problemas ao visitar sites que não estão preparados para essa alteração. Algumas páginas da Web podem parar de ser exibidas corretamente nessas novas versões do navegador.

A compatibilidade dos principais sites foi testada antecipadamente. Se houver problemas com sites que não possam ser corrigidos antes que essas versões sejam lançadas, as empresas têm planos de backup prontos para garantir que os sites não sejam afetados.

Possíveis problemas ou perda de funcionalidade no site se originam da sequência de agente do usuário que os navegadores enviam para os sites que você está visitando: o agente do usuário é uma sequência de caracteres enviada pelo navegador para o site para informar ao site qual navegador e versão você está usando, e tecnologia associada. Quando o navegador envia uma solicitação para um site, ele se identifica com a sequência de agente do usuário antes de recuperar o conteúdo solicitado. Os dados na sequência de agente do usuário ajudam o site a fornecer o conteúdo em um formato adequado ao seu navegador. A versão do agente do usuário é incrementada para corresponder ao número de versão do navegador. A mudança de 2 para 3 dígitos pode causar problemas.

## Você será afetado?{#version-100-impact}

A Adobe recomenda testar as aplicações Web do Campaign, incluindo formulários Web e pesquisas, para garantir que elas ainda funcionem bem com essas novas versões do navegador.

Essa recomendação se aplica a todas as aplicações web e especialmente se você incluiu o código JavaScript.

Você deve verificar em todos os navegadores, dispositivos móveis e desktop.

## Como testar?{#version-100-test}

Você pode configurar seus navegadores para relatar a versão como 100 agora e, em seguida, relatar e corrigir quaisquer problemas que encontrar.

Com essas configurações, o navegador envia a nova sequência de agente do usuário para os sites, indicando que o navegador é v100. Se você tiver problemas com seus formulários web, crie um bug para o editor do navegador. Considere reconstruir esses formulários web antes que essas atualizações estejam amplamente disponíveis.

### Teste com o Firefox 100{#test-firefox-100}

Para testar suas páginas da Web com o Mozilla Firefox 100, você pode simular a próxima alteração do agente do usuário em seus aplicativos da Web alterando manualmente a cadeia de caracteres do agente do usuário.

1. Abra o Firefox, digite `about:config` na barra de endereços e pressione Enter.
1. Pesquisar por `general.useragent.override`.
1. Selecione &#39;String&#39; e clique no sinal de mais (+).

   ![](assets/force-user-agent-firefox.png)

1. Insira o seguinte texto no campo:

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. Clique no botão de marca de seleção azul para salvar a configuração.
1. Feche e reinicie o navegador.

Para alterar o agente de usuário de volta para o padrão, basta voltar para `about:config` e procurar a configuração `general.useragent.override` novamente.  Quando for exibido, clique no ícone de lixeira para excluir a configuração e reinicie o navegador.

### Teste com o Chrome 100{#test-chrome-100}

Para testar o agente do usuário do Google Chrome 100 em seus próprios aplicativos Web, é possível habilitar esse teste usando as seguintes etapas:

1. Abra o Chrome, digite `chrome://flags` na barra de endereços e pressione Enter.
1. Pesquise `Force major version to 100 in User-Agent` no campo de pesquisa e habilite-o como mostrado abaixo.

   ![](assets/force-user-agent-chrome.png)

1. Reinicie o navegador.
1. Feche a guia `chrome://flags`.

Para alterar o agente do usuário de volta ao padrão, basta seguir esse processo e alterar a configuração do sinalizador para `Default` e reiniciar o navegador.


### Teste com o Microsoft Edge 100{#test-ms-edge-100}

A partir da v97, os proprietários de sites podem emular esta versão habilitando o sinalizador de experimento `#force-major-version-to-100` em `edge://flags`.

1. Abra o Microsoft Edge, digite `edge://flags` na barra de endereços e pressione Enter.
1. Procure pelo campo `force-major-version-to-100` e habilite-o conforme mostrado abaixo.

   ![](assets/force-user-agent-edge.png)

1. Reinicie o navegador.
1. Feche a guia `edge://flags`.

Para alterar o agente do usuário de volta ao padrão, basta seguir esse processo e alterar a configuração do sinalizador para `Default` e reiniciar o navegador.
