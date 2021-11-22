---
product: campaign
title: '"Tag de rastreamento Web: definição"'
description: '"Tag de rastreamento Web: definição"'
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 4%

---

# Tag de rastreamento Web: definição{#web-tracking-tag-definition}

![](../../assets/v7-only.svg)

Uma tag de rastreamento Web é simplesmente um URL construído com os parâmetros apropriados, enviado para o servidor de redirecionamento por meio de uma consulta HTTP.

## Formato dos dados a enviar {#format-of-the-data-to-be-sent}

O formato de um URL de rastreamento Web é o seguinte: **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>O número aleatório adicionado ao URL evita problemas causados por navegadores que armazenam páginas da Web em cache.

A tabela a seguir fornece uma lista de parâmetros especiais compatíveis com o servidor de redirecionamento.

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
                              <p>Identificador de delivery e identificador de recipient.</p> 
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
                              <p>Identificador de destinatário (útil se o cookie de sessão estiver ausente).</p> 
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
                              <p>Identificador de delivery a ser usado se não houver cookie de sessão. Esse valor deve ser expresso em hexadecimal.
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

**Alguns URLs de rastreamento Web**

* Visite uma página de identificador &quot;inicial&quot;

   **https://myserver.adobe.com/r/9862?tagid=home**

* Coleta de dados de volume de negócios

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* Especificação de um campo para localizar o recipient

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   Um recipient cujo número de conta é 10 é enviado para a página inicial.

* Uso de um delivery padrão

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   Um recipient é enviado para a página inicial. Essas informações serão armazenadas no delivery com o identificador 230 (e6 no banco de dados 16), a menos que um cookie de sessão que contenha um identificador de delivery seja enviado com esse query.

>[!NOTE]
>
>Todos os valores enviados para o servidor de redirecionamento por meio de parâmetros de URL devem ser codificados por URL. Nos exemplos fornecidos, observe que os caracteres &#39;=&#39; e &#39;|&#39; estão codificados como &#39;%3D&#39; e &#39;%7C&#39;, respectivamente.

## Métodos de transmissão de dados {#data-transmission-methods}

Os seguintes métodos são possíveis:

* Inserir o URL no **&quot;src&quot;** atributo de um HTML **`<img>`** tag incorporada na página da Web que você deseja rastrear.
* Chamada direta para o servidor de redirecionamento quando a página da Web que você deseja rastrear for gerada.
