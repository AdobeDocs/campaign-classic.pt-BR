---
product: campaign
title: Glossário para integração com o Campaign
description: Glossário para integração com o Campaign
audience: interaction
content-type: reference
topic-tags: interaction-overview
exl-id: 9e199b7c-9307-4797-bf86-7940388555bc
source-git-commit: d42389add06db74c54cb3a21813e9a832a2a288a
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 100%

---

# Glossário para integração com o Campaign{#i-glossary}

![](../../assets/v7-only.svg)

Abaixo está a definição dos elementos principais de interação.

* **Ambiente**: conjunto que inclui um catálogo de oferta e ganchos (espaços de ofertas). Você precisa criar um ambiente por targeting dimension. Há dois tipos de ambientes:

   * **Ambiente de design**: o ambiente no qual as ofertas são criadas e/ou regras de tipologia são definidas (regras que determinarão as ofertas para apresentar ou não a uma pessoa alvo). A tabela de pessoas físicas que serão alvos das ofertas e a tabela para armazenar todas as propostas de oferta também são definidas aqui. O nó **[!UICONTROL Design environment]** contém subpastas de espaço de ofertas, filtros predefinidos e categorias de ofertas. Para cada **[!UICONTROL Design environment]** existe um **[!UICONTROL Live environment]** somente leitura correspondente, gerado a partir desse mesmo **[!UICONTROL Design environment]**.
   * **Ambiente dinâmico**: ambiente vinculado a um **[!UICONTROL Design environment]**. Ele contém ofertas somente leitura cujo conteúdo e elegibilidade foram aprovados por meio do **[!UICONTROL Design environment]**. Eles devem ser marcados para serem apresentados em um site ou inseridos em uma mensagem.

* **Espaço de ofertas**: pasta que define o local onde a oferta é exposta. A definição de um espaço permite especificar o canal usado, especificar se ele pode ser usado no modo unitário (por padrão: apenas no modo de lote), criar o conteúdo da oferta usando funções de renderização e especificar a oferta dentre as ofertas apresentadas. Um espaço é uma interface entre o canal e o motor de oferta.

   >[!IMPORTANT]
   >
   >Um espaço de ofertas não é um canal de comunicação, ele coincide com um local específico de exposição no canal. Por exemplo, as ofertas expostas em um site pode ocupar dois espaços na mesma página. Nesse caso, teremos dois espaços para o mesmo canal.
   >
   >Os espaços devem ser definidos nas especificações e não devem ser modificados durante o projeto.

* **Catálogo de oferta**: conjunto de ofertas definido no Adobe Campaign que pode ser selecionado durante uma interação. O catálogo é organizado hierarquicamente com cada nó correspondente a uma categoria.
* **Categoria**: uma pasta vinculada ao catálogo de oferta em um ambiente, que organiza ofertas com base na natureza, na data de elegibilidade e no tema da aplicação. Uma categoria pode conter subcategorias, que herdam todas as características da categoria principal. As regras de elegibilidade podem ser definidas para uma categoria como compartilhada para várias ofertas.
* **Temas da aplicação**: palavras-chave definidas na categoria, que permitem filtrar ofertas quando são apresentadas a um canal de entrada ou saída, restringindo a seleção de ofertas a uma ou duas categorias.

   >[!NOTE]
   >
   >As categorias derivadas herdam os temas identificados na categoria principal.

* **Regras de elegibilidade**: restrições aplicadas a um ambiente, categoria ou oferta sobre o período de validade, público-alvo e peso. Eles permitem garantir que uma oferta esteja alinhada com o contato alvo.

   Nos ambientes, as regras de elegibilidade incluem regras de apresentação aplicadas às ofertas e às pessoas a serem públicos-alvo.

   Nas categorias, as regras de elegibilidade permitem limitar a validade da categoria no tempo, definir temas de aplicação e determinar as pessoas a serem públicos-alvo. Eles também podem receber um peso multiplicador por determinado período. Isso permite compartilhar as regras para ofertas em outras categorias e simplifica sua administração.

   Nas ofertas, as regras de elegibilidade permitem limitar a validade de ofertas no tempo e determinar as pessoas a serem públicos-alvo.

* **Arbitragem**: selecionar ofertas que serão exibidas em um ambiente (ofertas elegíveis). As classificações do princípio de arbitragem organiza as ofertas pela prioridade de acordo com os critérios definidos nas categorias, ofertas e ofertas de contexto.
* **Contato**: um contato de uma interação de entrada. Durante o processamento de chamadas do motor, o contato é associado a um targeting dimension. Há dois tipos de contatos:

   * **[!UICONTROL Identified contact]** : um contato que foi identificado voluntariamente no canal. Em interações de saída, o contato é identificado automaticamente.
   * **[!UICONTROL Anonymous contact]** : um contato que não tenha assinado voluntariamente por meio do canal, mas pode ser identificado implicitamente por meio de um cookie. Essa terminologia é usada apenas para interações de entrada.

      >[!NOTE]
      >
      >Contatos anônimos e não identificados são atribuídos ao targeting dimension do visitante.

* **Interação de saída**: chamada para o motor de interação de uma lista de contatos (usada para delivery de emails, mala direta etc.). As mesmas regras e processos são aplicados a cada contato. Esse tipo de interação geralmente é processado em modo de lote.
* **Interação de entrada**: interação seguindo uma chamada recebida gerada pela ação de um contato no canal. Esse tipo de interação geralmente é processado no modo unitário.
* **Modo de lote**: o modo de lote permite selecionar a melhor oferta para um conjunto de contatos. As regras de elegibilidade/priorização são aplicadas a todos os contatos do conjunto. Esse modo geralmente é usado para interações de saída.
* **Modo Unitário**: um único contato é processado de cada vez. Esse modo geralmente é usado para interações de entrada e mensagens transacionais.
* **Modo de identificação**: refere-se ao status de um contato.

   * **[!UICONTROL explicit]** : o contato é identificado após fazer logon na interface do canal.
   * **[!UICONTROL implicit]** : o contato foi identificado por um cookie (permanente ou de sessão). Ele pode ser processado como um contato anônimo ou identificado.
   * **[!UICONTROL anonymous]** : o contato não pode ser identificado.

* **Oferta elegível**: a oferta se encontra com as restrições definidas upstream que podem ser oferecidas de forma consistente a um público-alvo.
* **Regras de apresentação**: regras de tipologia mencionadas no ambiente de oferta, que permitem excluir algumas ofertas levando em conta o histórico de apresentações.
* **Peso**: fórmulas que permitem calcular precisamente a relevância de uma oferta para selecionar a mais relevante. Os pesos são definidos nas ofertas. Ofertas elegíveis são consideradas em ordem decrescente de peso.
* **Função de renderização**: função definida no espaço de ofertaa para construir sua representação de oferta com base nos atributos definidos na oferta. Há três modos diferentes de função de renderização: HTML, XML e texto.
* **Apresentação de oferta**: resultado da ação que consiste em apresentar uma ou várias ofertas a um contato em um determinado espaço (banner em um site, email ou SMS, por exemplo). Esse resultado é armazenado na tabela de apresentações de oferta. No entanto, não é obrigatório salvar as apresentações.
* **Simulação**: módulo que permite testar a apresentação de ofertas nos recipients alvos antes de realmente enviar as ofertas.
* **Pré-visualização**: pré-visualização da oferta como ela é exibida em sua pasta. É acessível a partir da janela de configurações de oferta ou do perfil de contato.
* **Filtros predefinidos**: regras de filtragem predefinidas podem considerar os parâmetros de oferta (por exemplo, um código de oferta). Eles podem ser reutilizados após a criação de ofertas.
* **Representação da oferta**: informações usadas pelo canal para exibir a oferta. A representação da oferta pode ser construída a partir da função de renderização do espaço em que a oferta é representada ou inserida diretamente na interface (por exemplo, no bloco HTML). Uma oferta pode ser representada por espaço.
* **Processo de transição**: um processo ativado em um ambiente identificado, responsável por direcionar a chamada a um ambiente anônimo se o contato não tiver sido identificado explicitamente e/ou implicitamente.
