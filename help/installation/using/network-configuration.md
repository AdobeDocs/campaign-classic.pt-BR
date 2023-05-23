---
product: campaign
title: Configuração de rede
description: Saiba mais sobre as diretrizes de comunicação do sistema
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 5%

---

# Configuração de rede{#network-configuration}



## Comunicação entre processos {#communication-between-processes}

Determinados processos do aplicativo precisam se comunicar com outros ou acessar a LAN e a Internet. Isso significa que algumas portas TCP precisam estar abertas para esses processos.

Use a porta Apache Tomcat incorporada como uma prioridade (8080 por padrão) para comunicações internas entre os vários servidores de aplicativos de uma plataforma Adobe Campaign.

### Servidor de entrega {#delivery-server}

Para o servidor de entrega (**mta nlserver**), as seguintes portas devem estar abertas:

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
   <td> Tráfego SMTP para transmissão de email.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp (domínio)<br /> </td> 
   <td> Servidores DNS<br /> </td> 
   <td> Consultas DNS.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (porta padrão)<br /> </td> 
   <td> Gateway de SMS<br /> </td> 
   <td> Usado para enviar tráfego SMS para o roteador SMS NetSize [opção].<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> Servidor de estatísticas<br /> </td> 
   <td> Acesso ao servidor de estatísticas.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Email de entrada {#inbound-mail}

Para o processo de recuperação de e-mails de entrada (**nlserver inMail**), as seguintes portas devem estar abertas:

<table> 
 <tbody> 
  <tr> 
   <td> Portas<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentários<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp (pop3)<br /> </td> 
   <td> Servidor de email interno<br /> </td> 
   <td> Tráfego POP3 para coletar mensagens de devolução.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Servidor de email interno<br /> </td> 
   <td> Tráfego SMTP para enviar mensagens de rejeição restantes que não são processadas automaticamente pelas regras predefinidas.<br /> </td> 
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
   <td> Tráfego HTTP ou HTTPS (incluindo para a oferta de capacidade de delivery).<br /> </td> 
  </tr> 
 </tbody> 
</table>

Quando vários servidores de aplicativos de uma plataforma Adobe Campaign precisam se comunicar, recomendamos usar a porta do servidor Apache Tomcat (por padrão: 8080) em vez da porta HTTP do servidor Web com a qual a integração do módulo de redirecionamento foi realizada. Isso significa que a porta precisa estar aberta entre esses servidores.

### Status de entrega do SMS {#sms-delivery-status}

Para rastrear deliveries de SMS (**sms nlserver**), a seguinte porta deve estar aberta:

<table> 
 <tbody> 
  <tr> 
   <td> Portas<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentários<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (porta padrão)<br /> </td> 
   <td> Gateway de SMS<br /> </td> 
   <td> Consulta o status da fila de entrega gerenciado pelo gateway de SMS NetSize [opção].<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Cliente avançado {#rich-client}

Para o cliente avançado do Adobe Campaign (**nlclient**), as seguintes portas devem estar abertas:

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
   <td> tráfego SOAP (HTTP).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Acesso ao banco de dados {#database-access}

Todos os componentes que usam o banco de dados devem poder se conectar a ele. Esse é o caso da maioria dos componentes, com exceção do servidor de redirecionamento, que pode funcionar sozinho, e do cliente Win32 thin, que usa HTTP (ou HTTPS) somente para se comunicar com o servidor de aplicativos.

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

Além disso, determinados componentes devem estar acessíveis pela Internet pública para que as campanhas de email executadas diretamente no Adobe Campaign possam ser visualizadas. Isso significa que algumas portas precisam estar abertas para componentes.

### Servidor de redirecionamento {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> Porta de escuta<br /> </td> 
   <td> Localização<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Em qualquer lugar. Cada clique em um link rastreado gera uma solicitação HTTP no servidor.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Servidor Web externo {#external-web-server}

Esse servidor hospeda formulários web, mirror pages etc. As seguintes portas precisam estar abertas:

<table> 
 <tbody> 
  <tr> 
   <td> Porta de escuta<br /> </td> 
   <td> Localização<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Em qualquer lugar. Necessário quando os formulários web são gerenciados diretamente da plataforma do Adobe Campaign ou quando as mirror pages são usadas.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Servidor de aplicativos interno (Web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> Porta de escuta<br /> </td> 
   <td> Localização<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Todos os computadores que executam o thin client ou rich client.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integração com o Adobe Experience Manager {#integration-with-adobe-experience-manager}

A integração entre o Adobe Campaign e o Adobe Experience Manager exige a abertura de várias portas se a instalação estiver &quot;no local&quot;. Para obter mais informações sobre como configurar essa integração, consulte [documentação detalhada](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> Porta de escuta<br /> </td> 
   <td> Descrição<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> Conexão AEM com o Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Conexão do Adobe Campaign com instâncias de "criação" e "publicação" do AEM. As portas a serem abertas podem ser diferentes das portas padrão, dependendo da configuração do AEM.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Largura de banda {#bandwidth}

Outro parâmetro importante da configuração de rede a ser considerado. É quase sempre de saída e muito demanda durante transmissões por email. Estes são alguns exemplos de configurações com base em nossa experiência:

* 1 Mb/s para 10.000 emails por hora (tamanho médio de 30 Kb)
* 8 a 10 Mb/s para 100.000 emails por hora (tamanho médio de 30 Kb)

Se você tiver restrições em termos de largura de banda, é possível agendar campanhas para serem executadas durante a noite quando a demanda for menor.
