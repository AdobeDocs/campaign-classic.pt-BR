---
title: Instalação de pacotes padrão do Campaign Classic
seo-title: Instalação de pacotes padrão do Campaign Classic
description: Instalação de pacotes padrão do Campaign Classic
seo-description: null
page-status-flag: never-activated
uuid: 1cba9487-52fc-442f-ae99-f8a2c157f25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: dd8f9adf-208c-42d9-b1a7-bfc8a690687e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 13%

---


# Installing Campaign Classic built-in packages{#installing-campaign-standard-packages}

## Sobre pacotes incorporados {#campaign-standard-packages}

Os pacotes incorporados contêm um conjunto de recursos que podem ser instalados de acordo com suas necessidades e dependendo do seu contrato. A lista completa dos pacotes integrados da Campanha está disponível abaixo.

>[!CAUTION]
>
>Você só pode instalar os pacotes correspondentes às opções mencionadas em seu contrato de licença.
>
>A instalação de um novo pacote pode afetar toda a sua plataforma: deve ser testado e validado antes da implantação final.
>
>Depois que um pacote é instalado, não é possível desinstalá-lo.

Para instalar um pacote integrado:

1. Acesse o assistente de importação do pacote do **[!UICONTROL Tools > Advanced > Package import...]** no console do cliente Adobe Campaign.
1. Selecione **[!UICONTROL Install a standard package]**.
1. Na lista do pacote, verifique os pacotes que deseja instalar.
   >[!NOTE]
   >
   >Quando um pacote está acinzentado, significa que ele já está instalado ou não é compatível com sua instância. A compatibilidade está descrita na tabela abaixo.
1. Clique em **[!UICONTROL Next]** e, em seguida, em **[!UICONTROL Start]** para começar a instalação do pacote.

   Depois que os pacotes forem instalados, a barra de progresso mostrará **100%** e você poderá ver a seguinte mensagem nos registros de instalação: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** a janela de instalação.

Os pacotes agora estão instalados.

### List of out-of-the-box Packages {#list-of-standard-packages}

A tabela a seguir lista todos os pacotes padrão com sua descrição, o tipo de instância em que eles podem ser instalados (Marketing, Mid etc.) e informações adicionais.

<table> 
 <thead> 
  <tr> 
   <th> Embalagem </th> 
   <th> Descrição </th> 
   <th> Tipo de instância </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Delivery<br /> </td> 
   <td> Monitora delivery e possíveis problemas encontrados quando as mensagens são enviadas. <a href="../../delivery/using/monitoring-a-delivery.md">Saiba mais</a><br /> </td> 
   <td> Todos</td> 
  </tr> 
  <tr> 
   <td> Campanhas de marketing (Campanha)<br /> </td> 
   <td> Define, otimiza, executa e analisa campanhas de comunicação e marketing. <a href="../../campaign/using/designing-marketing-campaigns.md">Saiba mais</a><br /> </td> 
   <td> Marketing</td>
  </tr> 
  <tr> 
   <td> Marketing resources (MRM)<br /> </td> 
   <td> Controla as ações de marketing em um modo colaborativo, fornecendo gerenciamento e rastreamento de tarefas, orçamentos e recursos de marketing. <a href="../../campaign/using/about-marketing-resource-management.md">Saiba mais</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> motor de oferta (interação)<br /> </td> 
   <td> Responde em tempo real durante uma interação com um determinado contato (um cliente ou público alvo), tornando-os uma única ou várias ofertas adaptadas.  Opcional. <a href="../../interaction/using/interaction-and-offer-management.md">Saiba mais</a> <br /> </td> 
   <td> Todos<br /> </td> 
  </tr> 
  <tr> 
   <td> Controlo do motor de oferta com instância de execução. Opcional.<br /> </td> 
   <td> </td> 
   <td> Marketing<br /> </td>  
  </tr> 
  <tr> 
   <td> Mecanismo de oferta para instância de execução. Opcional.<br /> </td> 
   <td> </td> 
   <td> Meio, Execução <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Redes sociais (Marketing social) <br /> </td> 
   <td> Sincroniza o Adobe Campaign com o Twitter e o Facebook. <a href="../../social/using/about-social-marketing.md">Saiba mais</a> <br /> </td> 
   <td> Todos</td> 
  </tr> 
  <tr> 
   <td> Controle de mensagens transacionais (Centro de mensagens - Controle)<br /> </td> 
   <td> Gerencia mensagens de disparo geradas a partir de eventos acionados a partir de sistemas de informações. Opcional. <a href="../../message-center/using/about-transactional-messaging.md">Saiba mais</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Execução de mensagens transacionais (Centro de Mensagens - Execução) <br /> </td> 
   <td> Garante maior disponibilidade e melhor gerenciamento de carga. Opcional. <a href="../../message-center/using/about-transactional-messaging.md">Saiba mais</a><br /> </td> 
   <td> Execução<br /> </td>
  </tr> 
  <tr> 
   <td> Canal LINE<br /> </td> 
   <td> Envia delivery usando o canal LINE com a Adobe Campaign. Opcional. Mensagens transacionais (pacote do centro de mensagens) obrigatórias. <a href="../../delivery/using/line-channel.md">Saiba mais</a> <br /> </td> 
   <td> Todos<br /> </td> 
  </tr> 
  <tr> 
   <td> Direct Mail channel<br /> </td> 
   <td> Envia delivery usando o canal de mala direta com a Adobe Campaign. Opcional. <a href="../../delivery/using/about-direct-mail-channel.md">Saiba mais</a><br /> </td> 
   <td> Todos<br /> </td>
  </tr> 
  <tr> 
   <td> Canal móvel (SMS) <br /> </td> 
   <td> Envia delivery usando o canal Mobile/SMS com o Adobe Campaign. Opcional. <a href="../../delivery/using/sms-channel.md">Saiba mais</a> <br /> </td> 
   <td> Todos<br /> </td> 
  </tr> 
  <tr> 
   <td> Canal de aplicativo móvel<br /> </td> 
   <td> Usa a plataforma Adobe Campaign para enviar notificações personalizadas para terminais iOS e Android por meio de aplicativos. Opcional. <a href="../../delivery/using/about-mobile-app-channel.md">Saiba mais</a> <br /> </td> 
   <td> Todos<br /> </td> 
  </tr> 
  <tr> 
   <td> Gerenciador de conteúdo<br /> </td> 
   <td> Cria boletins informativos ou site recorrentes e, em seguida, valida e publica suas mensagens. <a href="../../delivery/using/about-content-management.md">Saiba mais</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Pesquisas on-line (Gerenciador de Pesquisas)<br /> </td> 
   <td> Cria e gerencia formulários online para adicionar ou modificar informações do perfil, assinar, cancelar a inscrição ou um formulário de inscrição em concurso. Opcional. <a href="../../web/using/about-surveys.md">Saiba mais</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Análise de marketing<br /> </td> 
   <td> Permite analisar e medir dados, calcular estatísticas, simplificar e otimizar a criação e o cálculo de relatórios. Além disso, é possível criar relatórios e populações de públicos alvos. Opcional. <a href="../../reporting/using/about-cubes.md">Saiba mais</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Gestor de Resposta<br /> </td> 
   <td> Mede o sucesso e a rentabilidade de campanhas de marketing ou apresentações da oferta para todos os canais de comunicação.  Opcional. <a href="../../campaign/using/about-response-manager.md">Saiba mais</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Acesso a dados externos (Federated Data Acces)<br /> </td> 
   <td> Fornece a opção Federated Data Acces (FDA) para processar informações armazenadas em um ou mais bancos de dados externos, de modo que você possa acessar dados externos sem alterar a estrutura dos dados da Adobe Campaign.  Opcional. <a href="../../workflow/using/accessing-an-external-database--fda-.md">Saiba mais</a> <br /> </td> 
   <td> Todos<br /> </td> 
  </tr> 
  <tr> 
   <td> Otimização de campanha<br /> </td> 
   <td> Controla, filtros e monitora o envio de delivery para que as mensagens enviadas atendam melhor às necessidades e expectativas dos clientes, em conformidade com as políticas de comunicação de empresa. Opcional. <a href="../../campaign/using/about-campaign-typologies.md">Saiba mais</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Monitoramento da entregabilidade (Entregabilidade por email)<br /> </td> 
   <td> Mede o sucesso de suas campanhas ao chegar à caixa de entrada de seus recipient sem saltar ou ser marcado como spam. Opcional. <a href="../../delivery/using/about-deliverability.md">Saiba mais</a> <br /> </td> 
   <td> Todos </td> 
  </tr> 
  <tr> 
   <td> Gerenciamento de cupom<br /> </td> 
   <td> Cria um conjunto de cupons para adicionar às próximas ofertas de marketing. Opcional. <a href="../../delivery/using/personalized-coupons.md">Saiba mais</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Renderização da caixa de entrada (IR)<br /> </td> 
   <td> Permite que você pré-visualização a mensagem enviada nos diferentes contextos em que ela pode ser recebida e verifique a compatibilidade em desktops e aplicativos principais. Opcional. <a href="../../delivery/using/inbox-rendering.md">Saiba mais</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Central/local (Marketing distribuído)<br /> </td> 
   <td> Implementa campanhas cooperativas entre entidades centrais (sede, departamentos de marketing etc.) e entidades Locais (pontos de venda, agências regionais, etc.). Opcional. <a href="../../campaign/using/about-distributed-marketing.md">Saiba mais</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Conectores CRM<br /> </td> 
   <td> Fornece vários conectores CRM para vincular sua plataforma Adobe Campaign a sistemas de terceiros.  <a href="../../platform/using/crm-connectors.md">Saiba mais</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Conectores do Web Analytics<br /> </td> 
   <td> Permite que a Adobe Campaign e a Adobe Analytics interajam pelo pacote de conectores do Web Analytics. Não compatível com mensagens transacionais (pacote do centro de mensagens). <a href="../../platform/using/adobe-analytics-data-connector.md">Saiba mais</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> integração AEM<br /> </td> 
   <td> Permite que você gerencie o conteúdo de seus delivery de e-mail, bem como seus formulários diretamente no Adobe Experience Manager, para se beneficiar das funcionalidades de edição de conteúdo AEM bem como das capacidades do delivery Adobe Campaign. <a href="../../integrations/using/about-adobe-experience-manager.md">Saiba mais</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Integração Adobe Marketing Cloud Shared Audiência<br /> </td> 
   <td> Permite trocar e compartilhar audiências/segmentos com as soluções Adobe Experience Cloud e os principais serviços. Requer IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Saiba mais</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Integração com a Adobe Marketing Cloud<br /> </td> 
   <td> Permite importar e exportar audiências/segmentos de diferentes soluções Adobe Marketing Cloud para o Adobe Campaign. Opcional. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Saiba mais</a> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Regulamento de proteção de dados de privacidade<br /> </td> 
   <td> Contém funcionalidade adicional para ajudar com sua conformidade com privacidade no Campaign Classic. <a href="https://helpx.adobe.com/br/campaign/kb/acc-privacy.html">Saiba mais</a> <br /> </td> 
   <td> Todos</td> 
  </tr> 
  <tr> 
   <td> Transfer to Mid-Sourcing <br /> </td> 
   <td> Detalhes da instalação e configuração de um servidor mid-sourcing, bem como a implantação de uma instância que permite que terceiros enviem mensagens no modo mid-sourcing. Opcional. <a href="../../installation/using/mid-sourcing-server.md">Saiba mais</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Plataforma Mid-sourcing<br /> </td> 
   <td> Essa configuração é uma solução intermediária ideal entre uma configuração hospedada (ASP) e a internalização. Os componentes de execução voltados para o exterior são executados em um servidor "mid-sourcing" hospedado na Adobe Campaign. Opcional. <a href="../../installation/using/mid-sourcing-server.md">Saiba mais</a> <br /> </td> 
   <td> Mid-sourcing </td> 
  </tr> 
  <tr> 
   <td> ACS Connector<br /> </td> 
   <td> Pontes Adobe Campaign v7 e Adobe Campaign Standard. É um recurso integrado no Campaign v7 que replica automaticamente os dados no Campaign Standard, unindo o melhor das duas aplicações. Opcional. <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Saiba mais</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
 </tbody> 
</table>

### Pacote do Centro de mensagens {#message-center-package}

Você deve instalar canais de delivery (Email, canal móvel, canal de aplicativo móvel etc.) antes de instalar as mensagens transacionais (pacote do centro de mensagens). Se você tiver iniciado um projeto do Centro de mensagens somente por email e precisar adicionar um novo canal depois, siga estas etapas:

1. Install the new channel, for example the **Mobile channel**, using the package import wizard ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importe o arquivo ( **[!UICONTROL Tools > Advanced > Import package > File]**) e selecione:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. No **[!UICONTROL XML data content to import]**, mantenha somente o template do delivery do Centro de mensagens correspondente ao canal relacionado. For example, if you have added the **Mobile channel**, keep only the **entities** element corresponding to the **[!UICONTROL Mobile transactional message]** (smsTriggerMessage) template. If you have added the **Mobile App Channel**, keep only the **iOS transactional message** templates (iosTriggerMessage) and **Android transactional message** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

>[!CAUTION]
>
>Os templates do delivery do centro de mensagens para LINHA não estarão disponíveis se os pacotes do centro de mensagens estiverem instalados antes da LINHA

