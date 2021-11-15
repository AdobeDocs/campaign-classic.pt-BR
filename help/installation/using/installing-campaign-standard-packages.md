---
product: campaign
title: Instalação de pacotes integrados do Campaign Classic
description: Saiba como instalar pacotes incorporados do Campaign
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: 6c23dadb5b6523e17e242de43a908ca86ed7cc23
workflow-type: tm+mt
source-wordcount: '1188'
ht-degree: 16%

---

# Instalação de pacotes integrados do Campaign Classic{#installing-campaign-standard-packages}

![](../../assets/v7-only.svg)

## Sobre pacotes incorporados {#campaign-standard-packages}

Os pacotes incorporados contêm um conjunto de recursos que podem ser instalados de acordo com suas necessidades e dependendo de seu contrato. A lista completa de pacotes incorporados do Campaign está disponível abaixo.

>[!CAUTION]
>
>Você só pode instalar pacotes correspondentes às opções mencionadas no contrato de licença.
>
>A instalação de um novo pacote pode afetar toda a sua plataforma: deve ser testado e validado antes da implantação final.
>
>Depois que um pacote é instalado, não é possível desinstalá-lo.
>
>Como cliente hospedado ou híbrido, entre em contato com o Adobe para implantar um novo pacote integrado.

Para instalar um pacote incorporado:

1. Acesse o assistente de importação do pacote do **[!UICONTROL Tools > Advanced > Import package]** no console do cliente Adobe Campaign.
1. Selecione **[!UICONTROL Install a standard package]**.
1. Na lista de pacotes, verifique os pacotes que deseja instalar.
   >[!NOTE]
   >
   >Quando um pacote está esmaecido, significa que ele já está instalado ou não é compatível com sua instância. A compatibilidade é detalhada na tabela abaixo.
1. Clique em **[!UICONTROL Next]** e, em seguida, em **[!UICONTROL Start]** para começar a instalação do pacote.

   Depois que os pacotes forem instalados, a barra de progresso mostrará **100%** e você poderá ver a seguinte mensagem nos registros de instalação: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** a janela de instalação.

Os pacotes agora estão instalados.

### Lista de pacotes prontos para uso {#list-of-standard-packages}

A tabela a seguir lista todos os pacotes incorporados do Campaign.

<table> 
 <thead> 
  <tr> 
   <th> Pacote </th> 
   <th> Descrição </th> 
   <th> Tipo de instância </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Delivery<br /> </td> 
   <td> Monitora deliveries e eventuais problemas encontrados quando as mensagens são enviadas. <a href="../../delivery/using/about-delivery-monitoring.md">Saiba mais</a><br /> </td> 
   <td> Todos</td> 
  </tr> 
  <tr> 
   <td> Campanhas de marketing (Campaign)<br /> </td> 
   <td> Define, otimiza, executa e analisa campanhas de comunicação e marketing. <a href="../../campaign/using/designing-marketing-campaigns.md">Saiba mais</a><br /> </td> 
   <td> Marketing</td>
  </tr> 
  <tr> 
   <td> Recursos de marketing (MRM) <br /> </td> 
   <td> Controla ações de marketing em um modo colaborativo fornecendo gerenciamento e rastreamento das tarefas, orçamentos e recursos de marketing. <a href="../../mrm/using/about-marketing-resource-management.md">Saiba mais</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Dispositivo de oferta (interação)<br /> </td> 
   <td> Responde em tempo real durante uma interação com um determinado contato (um cliente ou target), tornando-os uma única ou várias ofertas adaptadas.  Opcional. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">Saiba mais</a> <br /> </td> 
   <td> Todos<br /> </td> 
  </tr> 
  <tr> 
   <td> Controle do mecanismo de oferta com instância de execução. Opcional.<br /> </td> 
   <td> Pacote para instalar na instância de controle do mecanismo de oferta (interação). <a href="../../interaction/using/distributed-architectures.md#packages-configuration">Saiba mais</a> </td> 
   <td> Marketing<br /> </td>  
  </tr> 
  <tr> 
   <td> Mecanismo de oferta para instâncias de execução. Opcional.<br /> </td> 
   <td> Pacote para instalar em instâncias de execução do mecanismo de oferta (interação). <a href="../../interaction/using/distributed-architectures.md">Saiba mais</a> </td> 
   <td> Mid, Execução <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Redes sociais (Marketing social) <br /> </td> 
   <td> Sincroniza o Adobe Campaign com a Twitter e a Facebook. <a href="../../social/using/about-social-marketing.md">Saiba mais</a> <br /> </td> 
   <td> Todos</td> 
  </tr> 
  <tr> 
   <td> Controle de mensagens transacionais (Centro de mensagens - Controle)<br /> </td> 
   <td> Gerencia mensagens de acionador geradas por eventos acionados de sistemas de informações. Opcional. <a href="../../message-center/using/about-transactional-messaging.md">Saiba mais</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Execução de mensagens transacionais (Centro de Mensagens - Execução) <br /> </td> 
   <td> Garante maior disponibilidade e melhor gerenciamento de carga. Opcional. <a href="../../message-center/using/about-transactional-messaging.md">Saiba mais</a><br /> </td> 
   <td> Execução<br /> </td>
  </tr> 
  <tr> 
   <td> Canal LINE<br /> </td> 
   <td> Envia deliveries usando o canal LINE com o Adobe Campaign. Opcional. Mensagens transacionais (pacote do centro de mensagens) obrigatórias. <a href="../../delivery/using/line-channel.md">Saiba mais</a> <br /> </td> 
   <td> Todos<br /> </td> 
  </tr> 
  <tr> 
   <td> Canal de correspondência direta<br /> </td> 
   <td> Envia deliveries usando o canal de correspondência direta com o Adobe Campaign. Opcional. <a href="../../delivery/using/about-direct-mail-channel.md">Saiba mais</a><br /> </td> 
   <td> Todos<br /> </td>
  </tr> 
  <tr> 
   <td> Canal móvel (SMS) <br /> </td> 
   <td> Envia deliveries usando o canal Mobile/SMS com o Adobe Campaign. Opcional. <a href="../../delivery/using/sms-channel.md">Saiba mais</a> <br /> </td> 
   <td> Todos<br /> </td> 
  </tr> 
   <tr> 
   <td> Canal de telefone<br /> </td> 
   <td> Envia deliveries usando o canal de telefone com o Adobe Campaign. Usado para central de atendimento. Opcional. <a href="../../delivery/using/communication-channels.md">Saiba mais</a> <br /> </td> 
   <td> Todos<br /> </td> 
  </tr> 
  <tr> 
   <td> Canal de aplicativo móvel<br /> </td> 
   <td> Usa a plataforma Adobe Campaign para enviar notificações personalizadas para terminais iOS e Android por meio de aplicativos. Opcional. <a href="../../delivery/using/about-mobile-app-channel.md">Saiba mais</a> <br /> </td> 
   <td> Todos<br /> </td> 
  </tr> 
  <tr> 
   <td> Gerenciador de conteúdo<br /> </td> 
   <td> Cria boletins informativos ou sites recorrentes e, em seguida, valida e publica suas mensagens. <a href="../../delivery/using/about-content-management.md">Saiba mais</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Pesquisas Online (Gerenciador de Pesquisas)<br /> </td> 
   <td> Cria e gerencia formulários online para adicionar ou modificar informações de perfil, para assinar, cancelar a assinatura ou um formulário de entrada de competição. Opcional. <a href="../../surveys/using/about-surveys.md">Saiba mais</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Análise de marketing<br /> </td> 
   <td> Permite analisar e medir dados, calcular estatísticas, simplificar e otimizar a criação e o cálculo do relatório. Além disso, você pode criar relatórios e populações do target. Opcional. <a href="../../reporting/using/about-cubes.md">Saiba mais</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Gestor de Resposta<br /> </td> 
   <td> Mede o sucesso e a lucratividade das campanhas de marketing ou apresentações de ofertas para todos os canais de comunicação.  Opcional. <a href="../../response/using/about-response-manager.md">Saiba mais</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Acesso a dados externos (Federated Data Access)<br /> </td> 
   <td> Fornece a opção Federated Data Access (FDA) para processar informações armazenadas em um ou mais bancos de dados externos, para que você possa acessar dados externos sem alterar a estrutura dos dados do Adobe Campaign.  Opcional. <a href="../../workflow/using/accessing-an-external-database--fda-.md">Saiba mais</a> <br /> </td> 
   <td> Todos<br /> </td> 
  </tr> 
  <tr> 
   <td> Otimização de campanha<br /> </td> 
   <td> Controla, filtra e monitora o envio de deliveries para que as mensagens enviadas atendam melhor às necessidades e expectativas dos clientes, de acordo com as políticas de comunicação da empresa. Opcional. <a href="../../campaign-opt/using/about-campaign-typologies.md">Saiba mais</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Monitoramento da entregabilidade (Entregabilidade por email)<br /> </td> 
   <td> Mede o sucesso das campanhas em chegar à caixa de entrada dos recipients sem rejeição ou sem serem marcadas como spam. Opcional. <a href="../../delivery/using/about-deliverability.md">Saiba mais</a> <br /> </td> 
   <td> Todos </td> 
  </tr> 
  <tr> 
   <td> Gerenciamento de cupom<br /> </td> 
   <td> Cria um conjunto de cupons para adicionar a ofertas de marketing futuras. Opcional. <a href="../../delivery/using/personalized-coupons.md">Saiba mais</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Renderização da caixa de entrada (IR)<br /> </td> 
   <td> Permite que você visualize a mensagem enviada nos diferentes contextos em que ela pode ser recebida e verificar a compatibilidade nos principais desktops e aplicativos. Opcional. <a href="../../delivery/using/inbox-rendering.md">Saiba mais</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing central/local (Marketing distribuído)<br /> </td> 
   <td> Implementa campanhas cooperativas entre entidades centrais (sede, departamentos de marketing etc.) e entidades locais (pontos de vendas, agências regionais, etc.). Opcional. <a href="../../distributed/using/about-distributed-marketing.md">Saiba mais</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Conectores CRM<br /> </td> 
   <td> Fornece vários conectores CRM para vincular sua plataforma Adobe Campaign a sistemas de terceiros.  <a href="../../platform/using/crm-connectors.md">Saiba mais</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Conectores de análise da Web<br /> </td> 
   <td> Permite que o Adobe Campaign e o Adobe Analytics interajam por meio do pacote Web Analytics connectors. Não compatível com as mensagens transacionais (pacote do centro de mensagens). <a href="../../platform/using/adobe-analytics-connector.md">Saiba mais</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Integração de AEM<br /> </td> 
   <td> Permite gerenciar o conteúdo de seus deliveries de email, bem como seus formulários diretamente no Adobe Experience Manager, para se beneficiar das funcionalidades de edição de conteúdo AEM e das capacidades de delivery da Adobe Campaign. <a href="../../integrations/using/about-adobe-experience-manager.md">Saiba mais</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Integração de públicos compartilhados da Adobe Experience Cloud<br /> </td> 
   <td> Permite trocar e compartilhar públicos/segmentos com as soluções e os serviços principais da Adobe Experience Cloud. Requer IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Saiba mais</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Integração com a Adobe Experience Cloud<br /> </td> 
   <td> Permite importar e exportar públicos/segmentos de diferentes soluções da Adobe Experience Cloud para o Adobe Campaign. Opcional. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Saiba mais</a> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Regulamento de proteção de dados de privacidade<br /> </td> 
   <td> Contém funcionalidade adicional para ajudar na conformidade com a privacidade no Campaign Classic. <a href="https://helpx.adobe.com/br/campaign/kb/acc-privacy.html">Saiba mais</a> <br /> </td> 
   <td> Todos</td> 
  </tr> 
  <tr> 
   <td> Transferência para mid-sourcing <br /> </td> 
   <td> Detalha a instalação e a configuração de um servidor mid-sourcing, bem como a implantação de uma instância que permite a terceiros enviar mensagens no modo mid-sourcing. Opcional. <a href="../../installation/using/mid-sourcing-server.md">Saiba mais</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Plataforma Mid-sourcing<br /> </td> 
   <td> Essa configuração é uma solução intermediária ideal entre uma configuração hospedada (ASP) e a internalização. Os componentes de execução voltados para o exterior são executados em um servidor "mid-sourcing" hospedado na Adobe Campaign. Opcional. <a href="../../installation/using/mid-sourcing-server.md">Saiba mais</a> <br /> </td> 
   <td> Mid-sourcing </td> 
  </tr> 
  <tr> 
   <td> Suporte ao AMP<br /> </td> 
   <td> Permite usar o novo AMP interativo para formato de email e enviar emails dinâmicos. Opcional. <a href="../../delivery/using/defining-interactive-content.md">Saiba mais</a> <br /> </td> 
   <td> Todos </td> 
  </tr> 
  <tr> 
   <td> ACS Connector<br /> </td> 
   <td> Pontes Adobe Campaign v7 e Adobe Campaign Standard. É um recurso integrado no Campaign v7 que replica automaticamente os dados no Campaign Standard, unindo o melhor das duas aplicações. Opcional. <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Saiba mais</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
 </tbody> 
</table>

### Pacote do Centro de mensagens {#message-center-package}

Você deve instalar canais de delivery (Email, canal móvel, canal de aplicativo móvel etc.) antes de instalar mensagens transacionais (pacote do centro de mensagens). Se você tiver iniciado um projeto do Centro de mensagens somente por email e precisar adicionar um novo canal posteriormente, siga estas etapas:

1. Instale o novo canal, por exemplo, a variável **Canal móvel**, usando o assistente de importação de pacotes ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importe o arquivo ( **[!UICONTROL Tools > Advanced > Import package > File]**) e selecione:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. No **[!UICONTROL XML data content to import]**, mantenha somente o template do delivery do Centro de mensagens correspondente ao canal relacionado. Por exemplo, se você tiver adicionado a variável **Canal móvel**, mantenha somente o **entities** elemento correspondente ao **[!UICONTROL Mobile transactional message]** Modelo (smsTriggerMessage). Se você tiver adicionado o **Canal de aplicativo móvel**, mantenha somente o **Mensagem transacional do iOS** templates (iosTriggerMessage) e **Mensagem transacional do Android** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

>[!CAUTION]
>
>Os templates de delivery do Centro de mensagens para LINE não estarão disponíveis se os pacotes do Centro de mensagens estiverem instalados antes do LINE
