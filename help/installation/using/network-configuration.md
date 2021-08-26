---
product: campaign
title: Configuração de rede
description: Conheça as diretrizes de comunicação do sistema
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 3%

---

# Configuração de rede{#network-configuration}

![](../../assets/v7-only.svg)

## Comunicação entre processos {#communication-between-processes}

Alguns processos do aplicativo precisam se comunicar com outras pessoas ou acessar a LAN e a Internet. Isso significa que algumas portas TCP precisam estar abertas para esses processos.

Use a porta Apache Tomcat incorporada como prioridade (8080 por padrão) para comunicações internas entre os vários servidores de aplicativos de uma plataforma Adobe Campaign.

### Servidor de delivery {#delivery-server}

Para o servidor de entrega (**nlserver mta**), as seguintes portas devem estar abertas:

<table> 
 <tbody> 
  <tr> 
   <td> Portas<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentários<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Em qualquer lugar<br /> </td> 
   <td> Tráfego SMTP para transmissão de e-mail.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp (domínio)<br /> </td> 
   <td> Servidores DNS<br /> </td> 
   <td> Consultas DNS.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (porta padrão)<br /> </td> 
   <td> Gateway SMS<br /> </td> 
   <td> Usado para enviar tráfego de SMS para o roteador NetSize SMS [option].<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> Servidor de estatísticas<br /> </td> 
   <td> Acesso ao servidor de estatísticas.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Email de entrada {#inbound-mail}

Para o processo de recuperação de email de entrada (**nlserver inMail**), as seguintes portas devem estar abertas:

<table> 
 <tbody> 
  <tr> 
   <td> Portas<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentários<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp (pop3)<br /> </td> 
   <td> Servidor de correio interno<br /> </td> 
   <td> Tráfego POP3 para coletar mensagens de devolução.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Servidor de correio interno<br /> </td> 
   <td> Tráfego SMTP para enviar mensagens de devolução restantes que não são processadas automaticamente pelas regras predefinidas.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Servidor de aplicativos {#application-server}

Para o servidor de aplicativos (**nlserver web**), as seguintes portas devem estar abertas:

<table> 
 <tbody> 
  <tr> 
   <td> Portas<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentários<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp (http)<br /> 443/tcp (https)<br /> </td> 
   <td> Em qualquer lugar<br /> </td> 
   <td> Tráfego HTTP ou HTTPS (incluindo para a oferta de deliverability).<br /> </td> 
  </tr> 
 </tbody> 
</table>

Quando vários servidores de aplicativos de uma plataforma Adobe Campaign precisarem se comunicar, recomendamos usar a porta do servidor Apache Tomcat (por padrão: 8080) em vez da porta HTTP do servidor Web com o qual a integração do módulo de redirecionamento foi realizada. Isso significa que a porta precisa ser aberta entre esses servidores.

### Status do delivery SMS {#sms-delivery-status}

Para rastrear deliveries de SMS (**nlserver sms**), a seguinte porta deve estar aberta:

<table> 
 <tbody> 
  <tr> 
   <td> Portas<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentários<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (porta padrão)<br /> </td> 
   <td> Gateway SMS<br /> </td> 
   <td> Consulta o status da fila de delivery gerenciado pelo gateway de SMS NetSize [option].<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Cliente avançado {#rich-client}

Para o cliente avançado Adobe Campaign (**nlclient**), as seguintes portas devem estar abertas:

<table> 
 <tbody> 
  <tr> 
   <td> Portas<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentários<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p>443/tcp (https)</p><br /> </td> 
   <td> Servidor de aplicativos<br /> </td> 
   <td> Tráfego SOAP (HTTP).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Acesso ao banco de dados {#database-access}

Todos os componentes que usam o banco de dados devem poder se conectar a ele. Esse é o caso da maioria dos componentes, com exceção do servidor de redirecionamento, que pode funcionar sozinho, e do cliente Win32 fino, que usa HTTP (ou HTTPS) apenas para se comunicar com o servidor de aplicativos.

As portas padrão são as seguintes:

<table> 
 <tbody> 
  <tr> 
   <td> Tipo de banco de dados<br /> </td> 
   <td> Porta (padrão)<br /> </td> 
   <td> Destino<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> 1521/tcp<br /> </td> 
   <td> Servidor de banco de dados<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> 5432/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Microsoft SQL Server</strong><br /> </td> 
   <td> 1433/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> 50000/tcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Acesso externo {#external-access}

Além disso, certos componentes devem estar acessíveis pela Internet pública para que campanhas de email executadas diretamente do Adobe Campaign possam ser visualizadas. Isso significa que algumas portas precisam estar abertas para componentes.

### Redirecionar servidor {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> Porta de escuta<br /> </td> 
   <td> Local<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Em qualquer lugar. Cada clique em um link rastreado gera uma solicitação HTTP no servidor.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Servidor Web externo {#external-web-server}

Esse servidor hospeda formulários da Web, mirror pages, etc. As seguintes portas precisam ser abertas:

<table> 
 <tbody> 
  <tr> 
   <td> Porta de escuta<br /> </td> 
   <td> Local<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Em qualquer lugar. Necessário quando formulários Web são gerenciados diretamente da plataforma Adobe Campaign ou quando mirror pages são usadas.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Servidor de aplicativos interno (Web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> Porta de escuta<br /> </td> 
   <td> Local<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Todos os computadores executando cliente thin ou cliente avançado.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integração com o Adobe Experience Manager {#integration-with-adobe-experience-manager}

A integração entre o Adobe Campaign e o Adobe Experience Manager requer a abertura de várias portas se a instalação for &quot;no local&quot;. Para obter mais informações sobre como configurar essa integração, consulte a [documentação detalhada](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> Porta de escuta<br /> </td> 
   <td> Descrição<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> AEM conexão com Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Conexão Adobe Campaign para AEM instâncias de "criação" e "publicação". As portas a serem abertas podem ser diferentes das portas padrão, dependendo da sua configuração de AEM.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Largura de banda {#bandwidth}

Outro parâmetro principal da configuração de rede a ser levado em conta. É quase sempre de saída e muita demanda durante as transmissões de e-mail. Estes são alguns exemplos de configurações com base em nossa experiência:

* 1 Mb/s para 10.000 emails por hora (tamanho médio de 30 Kb)
* 8 a 10 Mb/s para 100.000 emails por hora (tamanho médio de 30 Kb)

Se você tiver restrições em termos de largura de banda, é possível programar campanhas para serem executadas durante a noite, quando a demanda for menor.
