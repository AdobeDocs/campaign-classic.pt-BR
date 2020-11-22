---
solution: Campaign Classic
product: campaign
title: '"Tag de rastreamento Web: definição"'
description: '"Tag de rastreamento Web: definição"'
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 4%

---


# Tag de rastreamento Web: definição{#web-tracking-tag-definition}

Um tag de rastreamento da Web é simplesmente um URL construído com os parâmetros apropriados, enviado para o servidor de redirecionamento por meio de um query HTTP.

## Formato dos dados a enviar {#format-of-the-data-to-be-sent}

O formato de um URL de rastreamento da Web é o seguinte: **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>O número aleatório adicionado ao URL evita problemas causados por navegadores que armazenam páginas da Web em cache.

A tabela a seguir fornece uma lista de parâmetros especiais suportados pelo servidor de redirecionamento.

<table>
                     <thead>
                        <tr>
                           <th>Nome</th>
                           <th>Tipo</th>
                           <th>Descrição</th> 
                        </tr> 
                     </thead>
                     <tbody>
                        <tr>
                           <td>
                              <p>ID</p> 
                           </td>
                           <td>
                              <p>Cookie da sessão</p> 
                           </td>
                           <td>
                              <p>Identificador do delivery e identificador do recipient.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>uuid230</p> 
                           </td>
                           <td>
                              <p>Cookie permanente</p> 
                           </td>
                           <td>
                              <p>Identificador do recipient (útil se o cookie da sessão estiver ausente).</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>tagid</p> 
                           </td>
                           <td>
                              <p>Parâmetro de URL</p> 
                           </td>
                           <td>
                              <p>Identificador da página da Web rastreada: este é o único parâmetro obrigatório.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>jobid</p> 
                           </td>
                           <td>
                              <p>Parâmetro de URL</p> 
                           </td>
                           <td>
                              <p>Identificador de delivery a ser usado se não houver cookie de sessão. Este valor deve ser expresso em hexadecimal.
                              </p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>rcpid</p> 
                           </td>
                           <td>
                              <p>Parâmetro de URL</p> 
                           </td>
                           <td>
                              <p>Parâmetro usado para identificar o usuário da Internet. O formato desse parâmetro é "name=value", onde o nome é um campo do schema do recipient. Esse parâmetro tem prioridade sobre o identificador contido no cookie da sessão.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**Alguns URLs de rastreamento da Web**

* Visite uma página de identificação &quot;inicial&quot;

   **https://myserver.adobe.com/r/9862?tagid=home**

* Coleta de dados de volume de negócios

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* Especificação de um campo para localizar o recipient

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   Um recipient cujo número de conta é 10 é enviado ao home page.

* Uso de um delivery padrão

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   Um recipient é enviado ao home page. Essas informações serão armazenadas no delivery com o identificador 230 (e6 no banco de dados 16), a menos que um cookie de sessão contendo um identificador de delivery seja enviado com esse query.

>[!NOTE]
>
>Todos os valores enviados para o servidor de redirecionamento por meio de parâmetros de URL devem ser codificados por URL. Nos exemplos fornecidos, observe que os caracteres &#39;=&#39; e &#39;|&#39; estão codificados como &#39;%3D&#39; e &#39;%7C&#39;, respectivamente.

## Métodos de transmissão de dados {#data-transmission-methods}

Os seguintes métodos são possíveis:

* Inserir o URL no atributo **&quot;src&quot;** de uma **`<img>`** tag HTML incorporada na página da Web que você deseja rastrear.
* Chamada direta para o servidor de redirecionamento quando a página da Web que você deseja rastrear for gerada.

