---
title: '"Tag de rastreamento da Web: definição"'
seo-title: '"Tag de rastreamento da Web: definição"'
description: '"Tag de rastreamento da Web: definição"'
seo-description: null
page-status-flag: never-activated
uuid: 915ddfd8-ad1b-41ac-96ed-f7fae687c09f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: b8996508-7173-4225-95e7-b51209aae1f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3ad288bc983002da82b564e8ab3f4244c6324573

---


# Tag de rastreamento da Web: definição{#web-tracking-tag-definition}

Uma tag de rastreamento da Web é simplesmente um URL construído com os parâmetros apropriados, enviado para o servidor de redirecionamento por meio de uma consulta HTTP.

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
                              <p>Identificador de entrega e identificador do destinatário.</p> 
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
                              <p>Identificador do destinatário (útil se o cookie da sessão estiver ausente).</p> 
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
                              <p>Identificador de entrega a ser usado se não houver cookie de sessão. Este valor deve ser expresso em hexadecimal.
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
                              <p>Parâmetro usado para identificar o usuário da Internet. O formato desse parâmetro é "name=value", onde o nome é um campo do esquema do destinatário. Esse parâmetro tem prioridade sobre o identificador contido no cookie da sessão.
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

* Especificação de um campo para localizar o destinatário

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   Um destinatário cujo número de conta é 10 é enviado para a página inicial.

* Uso de uma entrega padrão

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   Um destinatário é enviado para a página inicial. Essas informações serão armazenadas na entrega com o identificador 230 (e6 no banco de dados 16), a menos que um cookie de sessão contendo um identificador de entrega seja enviado com essa consulta.

>[!NOTE]
>
>Todos os valores enviados para o servidor de redirecionamento por meio de parâmetros de URL devem ser codificados por URL. Nos exemplos fornecidos, observe que os caracteres &#39;=&#39; e &#39;|&#39; estão codificados como &#39;%3D&#39; e &#39;%7C&#39;, respectivamente.

## Métodos de transmissão de dados {#data-transmission-methods}

Os seguintes métodos são possíveis:

* Inserir o URL no atributo **&quot;src&quot;** de uma **`<img>`** tag HTML incorporada na página da Web que você deseja rastrear.
* Chamada direta para o servidor de redirecionamento quando a página da Web que você deseja rastrear for gerada.

