---
product: campaign
title: Migrar para a API do Adobe Analytics 2.0
description: Campaign Classic - Guia de migração de API do Adobe Analytics 2.0
feature: Technote, Analytics Integration
hide: true
source-git-commit: 64460d51b002a7821bba9c2998d9ccccab3046ad
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 1%

---

# Migrar para a API do Adobe Analytics 2.0 {#analytics-2-migration}

As APIs do Adobe Analytics 1.4 estão [atingindo o fim da vida útil](https://developer.adobe.com/analytics-apis/docs/1.4/guides/eol){target="_blank"}. O [conector do Web Analytics](../../integrations/using/gs-aa.md) que vincula a instância do Campaign à Adobe Analytics depende dessas APIs, portanto, é necessário atualizar para uma compilação que use as novas APIs do Analytics 2.0 para manter a integração em execução.

>[!CAUTION]
>
>A atualização reimporta os dois fluxos de trabalho técnicos internos que alimentam o conector, [!UICONTROL webAnalyticsSendMetrics] e [!UICONTROL webAnalyticsGetWebEvents] (consulte a [Referência de fluxos de trabalho do Web Analytics](../../workflow/using/web-analytics.md) para saber o que cada um faz). Qualquer personalização feita com base nesses fluxos de trabalho é substituída pela reimportação. Evite modificar diretamente esses fluxos de trabalho internos — crie sua personalização em um fluxo de trabalho personalizado separado; portanto, as atualizações futuras não a substituirão. A atualização também atualiza os arquivos integrados do Analytics JavaScript: se qualquer um dos workflows personalizados fizer referência a esses arquivos, eles serão interrompidos e precisarão ser adaptados ao novo código.

## Você será afetado? {#are-you-impacted}

Você será afetado se sua instância usar a conta externa [!UICONTROL Web Analytics] para qualquer um dos seguintes itens:

* Envio de indicadores e atributos de campanha de email para o Adobe Analytics como métricas.
* Envio de dados de classificação ao Adobe Analytics.
* O fluxo de remarketing (identificação de contatos convertidos após uma campanha).
* Uma conta externa do [!UICONTROL Web Analytics] que você planeja configurar pela primeira vez.

Não tem certeza de qual delas se aplica a você? Verifique quais dos workflows técnicos acima estão ativos em sua instância e revise a configuração da conta externa do [!UICONTROL Web Analytics] em [!UICONTROL Administration > Platform > External accounts] (consulte [Conta externa do Web Analytics](../../installation/using/external-accounts.md#web-analytics-external-account)).

## Como migrar {#how-to-migrate}

Se você estiver em uma instância **hospedada pela Adobe**, a Adobe lidará com o provisionamento SFTP, a lista de permissões de IP e a configuração de chaves para você como parte da atualização. Você só precisará validar seus casos de uso depois que a nova build estiver ativa.

Se você estiver em uma implantação **local ou híbrida**, siga estas etapas.

1. [Atualize seu ambiente do Campaign](../../production/using/build-upgrade.md) para uma compilação que inclua as alterações do Adobe Analytics 2.0. Você pode confirmar qual compilação está executando a partir de [!UICONTROL Help > About...] (consulte [como verificar a versão do Campaign](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)).
1. Revise quais dos casos de uso acima se aplicam à sua instância, já que a próxima etapa depende disso.
1. Se você usar o fluxo de trabalho de remarketing, o fluxo de trabalho [!UICONTROL webAnalyticsFindConverted] precisará de um canal SFTP dedicado para trocar dados com o Adobe Analytics 2.0. Configure da seguinte maneira; caso contrário, pule para a próxima etapa.
   1. Provisione um servidor SFTP para a instância usando a autenticação baseada em chave, seguindo as mesmas [práticas recomendadas para o servidor SFTP](../../platform/using/sftp-server-usage.md) que você aplicaria a qualquer outra integração SFTP externa. A Adobe fornece um [exemplo de script de configuração SFTP](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html?package=/content/software-distribution/en/details.html/content/dam/campaign/public/setup_sftp.zip){target="_blank"} para ajudar você a começar.
   1. Registre os detalhes de conexão desse servidor no Adobe Analytics executando o script fornecido com a nova build:

      ```
      nlserver javascript -instance:<instance_name> -arg:host=<sftp_host_url>#user=<sftp_user> -file <path_to_the_file>/aaremarketingLocation.js
      ```

      Exemplo:

      ```
      nlserver javascript -instance:test_mkt_stage2 -arg:host=test-mkt-stage1.campaign.adobe.com#user=test -file ./nl6/datakit/nms/eng/js/aaremarketingLocation.js
      ```

   1. Lista de permissões do Adobe Analytics no servidor SFTP, já que as exportações de remarketing só são iniciadas a partir de um conjunto fixo de intervalos IP do Adobe:
      * [Pesquise os endereços IP atuais da coleção de dados do Adobe Analytics](https://experienceleague.adobe.com/pt-br/docs/core-services/interface/data-collection/ip-addresses){target="_blank"} e adicione-os à lista de permissões do servidor SFTP. As exportações do Analytics baseadas em FTP (incluindo feeds de dados) são originárias apenas de endereços IPv4 das regiões de Londres, Oregon e Singapura.
      * [Recupere a chave pública do Adobe Analytics](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-18141){target="_blank"} e adicione-a ao arquivo `authorized_keys` no servidor SFTP para que o Analytics possa realizar a autenticação.
1. Habilite o sinalizador de recurso `FEATUREFLAG_USE_ANALYTICS_20_API` na sua instância criando ou definindo o `longvalue` da opção para `1` em [!UICONTROL xtkOption], em **[!UICONTROL Administration]> [!UICONTROL Platform] >[!UICONTROL Options]** na árvore do Campaign Explorer. Esta etapa é necessária independentemente de qual caso de uso acima se aplica a você.
1. Valide a migração exercitando cada caso de uso que se aplica à sua instância (envie uma campanha de teste, verifique se os indicadores chegam ao Analytics e confirme os dados de remarketing, se aplicável) antes de desativar qualquer conectividade antiga.

## Configuração de uma nova conta externa do Web Analytics {#setting-up-a-new-web-analytics-external-account}

O seguinte se aplica independentemente de sua instância ser hospedada pela Adobe ou no local/híbrida.

Se você estiver configurando a conta externa [!UICONTROL Web Analytics] pela primeira vez em vez de migrar uma existente, siga as [etapas de configuração da conta externa](../../installation/using/external-accounts.md#web-analytics-external-account) e o [guia de introdução do conector](../../integrations/using/gs-aa.md).

Como o Analytics 2.0 apresenta um novo tratamento de classificação, também é necessário criar um conjunto de classificações no Adobe Analytics antes que sua conta externa possa coletar os dados de classificação do conjunto de relatórios. Esta é uma nova etapa: crie-a após configurar suas Variáveis de conversão e Eventos bem-sucedidos e antes de configurar a conta externa no Campaign.

Para criar seu conjunto de classificações:

1. Na barra de menu superior do [!DNL Adobe Analytics], selecione **[!UICONTROL Components]** > **[!UICONTROL Classification sets]** e clique em **[!UICONTROL New]**.

   ![](assets/analytics-classification-set-menu.png)

1. No diálogo **[!UICONTROL Add New Classification Set]**:

   ![](assets/analytics-classification-set-dialog.png)

   * Insira um **[!UICONTROL Name]** para o conjunto de classificações.
   * Defina o **[!UICONTROL Type]** como **[!UICONTROL Primary]**.
   * Em **[!UICONTROL Job notifications]**, escolha quem deve ser notificado sobre o sucesso ou falha dos trabalhos do conjunto de classificações e forneça os endereços de email correspondentes.
   * No **[!UICONTROL Subscriptions]**, selecione seu conjunto de relatórios e a variável de conversão criada para o nome da campanha interna na etapa anterior.

1. Clique em **[!UICONTROL Save]**.

Esse conjunto de classificações será descoberto automaticamente pelo Campaign quando você configurar sua conta externa na próxima etapa. Para obter mais informações sobre conjuntos de classificações, consulte a [documentação do Adobe Analytics](https://experienceleague.adobe.com/pt-br/docs/analytics/components/classifications/sets/create-set){target="_blank"}.

## Precisa de ajuda? {#need-help}

Se você tiver problemas durante a migração, contate o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.
