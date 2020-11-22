---
solution: Campaign Classic
product: campaign
title: Configuração de rede
description: Saiba mais sobre as diretrizes de comunicação do sistema
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 3%

---


# Configuração de rede{#network-configuration}

## Comunicação entre processos {#communication-between-processes}

Determinados processos do aplicativo precisam se comunicar com outras pessoas ou acessar a LAN e a Internet. Isso significa que algumas portas TCP precisam estar abertas para esses processos.

Use a porta Apache Tomcat integrada como prioridade (8080 por padrão) para comunicações internas entre os vários servidores de aplicativos de uma plataforma Adobe Campaign.

### Servidor delivery {#delivery-server}

Para o servidor delivery (**nlserver mta**), as seguintes portas devem estar abertas:

<table> 
 <tbody> 
  <tr> 
   <td> Portas<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentários<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Qualquer lugar<br /> </td> 
   <td> Tráfego SMTP para transmissão de email.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp (domínio)<br /> </td> 
   <td> Servidores DNS<br /> </td> 
   <td> Query DNS.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (porta padrão)<br /> </td> 
   <td> Gateway SMS<br /> </td> 
   <td> Usado para enviar tráfego SMS para o roteador NetSize SMS [opção].<br /> </td> 
  </tr> 
  <tr> 
   <td> 777/udp<br /> </td> 
   <td> Servidor de estatísticas<br /> </td> 
   <td> Acessar o servidor de estatísticas.<br /> </td> 
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
   <td> Tráfego POP3 para coletar mensagens de rejeição.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Servidor de correio interno<br /> </td> 
   <td> Tráfego SMTP para enviar mensagens de rejeição restantes que não são automaticamente processadas pelas regras predefinidas.<br /> </td> 
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
   <td> Qualquer lugar<br /> </td> 
   <td> Tráfego HTTP ou HTTPS (incluindo para a oferta de entrega).<br /> </td> 
  </tr> 
 </tbody> 
</table>

Quando vários servidores de aplicativos de uma plataforma Adobe Campaign precisarem se comunicar, recomendamos usar a porta do servidor Apache Tomcat (por padrão: 8080) em vez da porta HTTP do servidor Web com a qual a integração do módulo de redirecionamento foi realizada. Isso significa que a porta precisa estar aberta entre esses servidores.

### Status do delivery SMS {#sms-delivery-status}

Para rastrear delivery SMS (**nlserver sms**), a seguinte porta deve estar aberta:

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
   <td> Query o status da fila de delivery gerenciada pelo gateway SMS NetSize [opção].<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Cliente rico {#rich-client}

Para o cliente Adobe Campaign rich (**nlclient**), as seguintes portas devem estar abertas:

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

Todos os componentes que usam o banco de dados devem poder se conectar a ele. Esse é o caso da maioria dos componentes, com exceção do servidor de redirecionamento, que pode funcionar sozinho, e do cliente fino Win32, que usa HTTP (ou HTTPS) apenas para se comunicar com o servidor de aplicativos.

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

Além disso, certos componentes devem estar acessíveis na Internet pública para que as campanhas de e-mail executadas diretamente da Adobe Campaign possam ser visualizadas. Isso significa que algumas portas precisam estar abertas para componentes.

### Servidor de redirecionamento {#redirection-server}

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

Este servidor hospeda Formulários web, mirrores page etc. As seguintes portas precisam ser abertas:

<table> 
 <tbody> 
  <tr> 
   <td> Porta de escuta<br /> </td> 
   <td> Local<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Em qualquer lugar. Necessário quando os Formulários web são gerenciados diretamente da plataforma Adobe Campaign ou quando os mirrores page são usados.<br /> </td> 
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
   <td> Todos os computadores executando o cliente thin ou o cliente rich.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integração com a Adobe Experience Manager {#integration-with-adobe-experience-manager}

A integração entre a Adobe Campaign e a Adobe Experience Manager exige a abertura de várias portas se a instalação for &quot;no local&quot;. Para obter mais informações sobre como configurar essa integração, consulte a documentação [](../../integrations/using/about-adobe-experience-manager.md)detalhada.

<table> 
 <tbody> 
  <tr> 
   <td> Porta de escuta<br /> </td> 
   <td> Descrição<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> AEM conexão com o Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Conexão Adobe Campaign para AEM instâncias de "criação" e "publicação". As portas a serem abertas podem ser diferentes das portas padrão, dependendo da configuração AEM.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Largura de banda {#bandwidth}

Outro parâmetro chave da configuração de rede a ser considerado. É quase sempre de saída e muita demanda durante as transmissões por e-mail. Estes são alguns exemplos de configurações baseadas em nossa experiência:

* 1 MB/s para 10.000 emails por hora (tamanho médio de 30 Kb)
* 8 a 10 Mb/s para 100.000 e-mails por hora (tamanho médio de 30 Kb)

Se você tiver restrições em termos de largura de banda, é possível programar campanhas para serem executadas durante a noite quando a demanda for menor.
