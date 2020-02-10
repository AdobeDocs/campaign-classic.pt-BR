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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f5062117b5cefbdd2570018f6803f114c14a3fae

---


# Instalação de pacotes padrão do Campaign Classic{#installing-campaign-standard-packages}

## Sobre pacotes padrão {#campaign-standard-packages}

Pacotes são um conjunto de recursos que podem ser instalados de acordo com suas necessidades. Eles permitirão que você adicione mais opções à sua instância.

>[!CAUTION]
>
>Você só pode instalar pacotes correspondentes às opções mencionadas no contrato de licença.
>
>Depois que um pacote é instalado, não é possível desinstalá-lo. A instalação de um novo pacote pode afetar toda a sua plataforma: deve ser testado e validado antes da implantação final.

Para instalar um pacote padrão:

1. Acesse o assistente de importação de pacote **[!UICONTROL Tools > Advanced > Package import...]** no console do cliente Adobe Campaign.
1. Select **[!UICONTROL Install a standard package]**.
1. Na lista exibida, verifique os pacotes que deseja instalar.
   >[!NOTE]
   >
   >Se um pacote estiver acinzentado, não será possível instalá-lo. Isso significa que ele já está instalado ou não é compatível com sua instância. Por exemplo, não é possível instalar o pacote da plataforma **de fornecedores** intermediários em uma instância de marketing. Você encontrará essas informações na tabela abaixo.
1. Clique em **[!UICONTROL Next]** e, em seguida, **[!UICONTROL Start]** para iniciar a instalação do pacote.

   Depois que os pacotes são instalados, a barra de progresso mostra **100%** e você pode ver a seguinte mensagem nos registros de instalação: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** a janela de instalação.

Os pacotes agora estão instalados.

### Lista de pacotes prontos para uso {#list-of-standard-packages}

A tabela a seguir lista todos os pacotes padrão com sua descrição, o tipo de instância em que eles podem ser instalados (Marketing, Mid etc.) e informações adicionais.

<table> 
 <thead> 
  <tr> 
   <th> Pacote </th> 
   <th> Descrição </th> 
   <th> Tipo de instância </th> 
   <th> Mais informações </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Delivery<br /> </td> 
   <td> Monitora entregas e possíveis problemas encontrados quando as mensagens são enviadas.<br /> </td> 
   <td> Todos</td> 
   <td> <a href="../../delivery/using/monitoring-a-delivery.md">Saiba mais</a></td> 
  </tr> 
  <tr> 
   <td> Campanhas de marketing (Campanha)<br /> </td> 
   <td> Define, otimiza, executa e analisa campanhas de comunicação e marketing.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../campaign/using/designing-marketing-campaigns.md">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Marketing resources (MRM)<br /> </td> 
   <td> Controla as ações de marketing em um modo colaborativo, fornecendo gerenciamento e rastreamento das tarefas, orçamentos e recursos de marketing.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../campaign/using/about-marketing-resource-management.md">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Mecanismo de oferta (interação)<br /> </td> 
   <td> Responds in real time during an interaction with a given contact (a customer or target) by making them a single or several adapted offers. <br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../interaction/using/interaction-and-offer-management.md">saiba mais</a></td> 
  </tr> 
  <tr> 
   <td> Controle do mecanismo de oferta com instância de execução<br /> </td> 
   <td> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional</td> 
  </tr> 
  <tr> 
   <td> Mecanismo de oferta para instâncias de execução<br /> </td> 
   <td> </td> 
   <td> Meio, Execução <br /> </td> 
   <td> Opcional</td> 
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Redes sociais (Marketing social) <br /> </td> 
   <td> Sincroniza o Adobe Campaign com o Twitter e o Facebook.<br /> </td> 
   <td> Todos</td> 
   <td> <a href="../../social/using/starting-workflows.md">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Controle de mensagem transacional (Centro de mensagens - Controle)<br /> </td> 
   <td> Gerencia mensagens de disparo geradas de eventos acionados de sistemas de informações.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../message-center/using/about-transactional-messaging.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Execução de mensagem transacional (Centro de Mensagens - Execução) <br /> </td> 
   <td> Garante maior disponibilidade e melhor gerenciamento de carga.<br /> </td> 
   <td> Execução<br /> </td> 
   <td> Opcional, <a href="../../message-center/using/about-transactional-messaging.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Canal LINE<br /> </td> 
   <td> Envia entregas usando o canal LINE com o Adobe Campaign,<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, obrigatório para o centro de mensagens</td> 
  </tr> 
  <tr> 
   <td> Canal de mala direta<br /> </td> 
   <td> Envia entregas usando o canal de mala direta com o Adobe Campaign.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/about-direct-mail-channel.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Canal móvel (SMS) <br /> </td> 
   <td> Envia entregas usando o canal Mobile/SMS com o Adobe Campaign.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/sms-channel.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Canal de telefone<br /> </td> 
   <td> Envia entregas usando o canal de telefone com o Adobe Campaign.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional</td> 
  </tr> 
  <tr> 
   <td> Canal de fax<br /> </td> 
   <td> Envia entregas usando o canal de fax com o Adobe Campaign.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional</td> 
  </tr> 
  <tr> 
   <td> Canal de aplicativo móvel<br /> </td> 
   <td> Usa a plataforma do Adobe Campaign para enviar notificações personalizadas para terminais iOS e Android por meio de aplicativos. <br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/about-mobile-app-channel.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Gerenciador de conteúdo<br /> </td> 
   <td> Cria boletins informativos ou site recorrentes e, em seguida, valida e publica suas mensagens.<br /> </td> 
   <td> </td> 
   <td> <a href="../../delivery/using/about-content-management.md">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Pesquisas online (Gerenciador de Pesquisas)<br /> </td> 
   <td> Cria e gerencia formulários online para adicionar ou modificar informações de perfil, assinar, cancelar a inscrição ou um formulário de inscrição em concurso.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../web/using/about-surveys.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Análise de marketing<br /> </td> 
   <td> Permite analisar e medir dados, calcular estatísticas, simplificar e otimizar a criação e o cálculo de relatórios. Além disso, você pode criar relatórios e populações-alvo. <br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../reporting/using/about-cubes.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Gestor de Resposta<br /> </td> 
   <td> Mede o sucesso e a rentabilidade de campanhas de marketing ou proposições de ofertas para todos os canais de comunicação.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../campaign/using/about-response-manager.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Acesso a dados externos (acesso a dados federados)<br /> </td> 
   <td> Provides the Federated Data Access (FDA) option in order to process information stored in one or more external databases so that you can access external data without changing the structure of Adobe Campaign data.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../workflow/using/accessing-an-external-database--fda-.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Otimização de campanha<br /> </td> 
   <td> Controla, filtra e monitora o envio de entregas para que as mensagens enviadas atendam melhor às necessidades e expectativas dos clientes, em conformidade com as políticas de comunicação da empresa. <br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../campaign/using/about-campaign-typologies.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Monitoramento da entrega (Entrega por email)<br /> </td> 
   <td> Mede o sucesso de suas campanhas atingindo a caixa de entrada dos destinatários sem saltar ou sendo marcado como spam.<br /> </td> 
   <td> Todos </td> 
   <td> Opcional, <a href="https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Gerenciamento de cupom<br /> </td> 
   <td> Cria um conjunto de cupons para adicionar às próximas ofertas de marketing.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/personalized-coupons.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Renderização da caixa de entrada (IR)<br /> </td> 
   <td> Permite que você visualize a mensagem enviada em diferentes contextos nos quais ela pode ser recebida e verifique a compatibilidade em desktops e aplicativos principais. Você precisa de uma conta de Litmus.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/about-deliverability.md#inbox-rendering">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Marketing Central/local (Marketing distribuído)<br /> </td> 
   <td> Implementa campanhas de cooperação entre entidades centrais (sede, departamentos de marketing, etc.) e entidades locais (pontos de venda, agências regionais, etc.).<br /> </td> 
   <td> Marketing </td> 
   <td> Opcional, <a href="../../campaign/using/about-distributed-marketing.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> CRM connectors<br /> </td> 
   <td> Provides various CRM connectors for linking your Adobe Campaign platform to your third-party systems.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../platform/using/crm-connectors.md">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Conectores do Web Analytics<br /> </td> 
   <td> Permite que o Adobe Campaign e o Adobe Analytics interajam pelo pacote de conectores do Web Analytics.<br /> </td> 
   <td> Marketing </td> 
   <td> Não compatível com mensagens transacionais, <a href="../../platform/using/adobe-analytics-data-connector.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Integração com o AEM<br /> </td> 
   <td> Permite que você gerencie o conteúdo de suas entregas de email, bem como seus formulários diretamente no Adobe Experience Manager, para se beneficiar das funcionalidades de edição de conteúdo do AEM e das capacidades de entrega do Adobe Campaign.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../integrations/using/about-adobe-experience-manager.md">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Integração de públicos-alvo compartilhados da Adobe Marketing Cloud<br /> </td> 
   <td> Allows you to exchange and share audiences/segments with Adobe Experience Cloud solutions and core services.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Exige IMS, <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Integração com a Adobe Marketing Cloud<br /> </td> 
   <td> Permite importar e exportar públicos-alvo/segmentos de diferentes soluções da Adobe Marketing Cloud para o Adobe Campaign. </td> 
   <td> Marketing</td> 
   <td> Opcional, <a href="../../integrations/using/configuring-ims.md#installing-the-package">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Regulamento de proteção de dados de privacidade<br /> </td> 
   <td> Contém funcionalidade adicional para ajudar projetos a se tornarem compatíveis com o RGPD no Campaign Classic.<br /> </td> 
   <td> Todos</td> 
   <td> <a href="https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Transfer to Mid-Sourcing <br /> </td> 
   <td> Detalhes da instalação e configuração de um servidor de mid-sourcing, bem como da implantação de uma instância que permite a terceiros enviar mensagens no modo de mid-sourcing.<br /> </td> 
   <td> Marketing </td> 
   <td> Opcional, <a href="../../installation/using/mid-sourcing-server.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Plataforma Mid-sourcing<br /> </td> 
   <td> Essa configuração é uma solução intermediária ideal entre uma configuração hospedada (ASP) e a internalização. Os componentes de execução voltados para o exterior são executados em um servidor de "mid-sourcing" hospedado no Adobe Campaign.<br /> </td> 
   <td> Meid-sourcing </td> 
   <td> Opcional, <a href="../../installation/using/mid-sourcing-server.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> ACS Connector<br /> </td> 
   <td> Corresponde ao Adobe Campaign v7 e ao Adobe Campaign Standard. É um recurso integrado no Campaign v7 que replica automaticamente os dados no Campaign Standard, unindo o melhor das duas aplicações. <br /> </td> 
   <td> Marketing </td> 
   <td> Opcional, <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">saiba mais</a> </td> 
  </tr> 
 </tbody> 
</table>

### Pacote do Centro de mensagens {#message-center-package}

Para adicionar um canal de entrega (canal móvel, canal de aplicativo móvel etc.), isso deve ser realizado antes da instalação do pacote do Centro de mensagens. Se você tiver iniciado um projeto do Centro de mensagens no canal de e-mail e, no meio do projeto, decidir adicionar um novo canal, siga estas etapas:

1. Instale o canal desejado, por exemplo, o canal **** Mobile, usando o assistente de importação de pacote ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importe o arquivo ( **[!UICONTROL Tools > Advanced > Import package > File]**) e selecione:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. No **[!UICONTROL XML data content to import]**, mantenha somente o modelo de entrega do Centro de mensagens correspondente ao canal anexado. Por exemplo, se você tiver adicionado o canal **** Mobile, mantenha somente o elemento **entidades** correspondente ao modelo **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). If you have added the **Mobile App Channel**, keep only the **iOS transactional message** templates (iosTriggerMessage) and **Android transactional message** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

### Pacote LINE {#line-package}

Para poder enviar entregas usando o canal LINE com o Adobe Campaign, é necessário instalar o pacote LINE.

A instalação do pacote LINE é uma instalação padrão detalhada na seção [Importando pacotes](../../platform/using/working-with-data-packages.md#importing-packages) .

![](assets/line_config_1.png)

>[!CAUTION]
>
>Os modelos de entrega do Centro de mensagens para LINHA não estarão disponíveis se os pacotes do Centro de mensagens estiverem instalados antes da LINHA.
