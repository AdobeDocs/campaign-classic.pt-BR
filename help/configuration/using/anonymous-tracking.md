---
title: Rastreamento anônimo
seo-title: Rastreamento anônimo
description: Rastreamento anônimo
seo-description: null
page-status-flag: never-activated
uuid: 21ba3657-eabf-4228-9fc0-e72712bf8fe7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 2d2c6ae9-4dba-4b82-a25e-eda65a49572d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Rastreamento anônimo{#anonymous-tracking}

O Adobe Campaign permite que você vincule informações coletadas de rastreamento da Web a um destinatário quando ele navegar no site anonimamente. Quando um usuário navega nas páginas marcadas do seu site, essas informações de navegação são coletadas, de modo que, uma vez clicadas em um email enviado pelo Adobe Campaign, elas são identificadas e as informações são vinculadas automaticamente a elas.

>[!IMPORTANT]
>
>Configurar o rastreamento anônimo em um site pode acionar a coleta de uma quantidade significativa de logs de rastreamento, afetando assim a operação do banco de dados. Configure-o com cuidado.\
>Os logs de rastreamento são salvos no banco de dados até que os dados de rastreamento sejam removidos. Use o assistente de implantação para configurar a frequência de expurgação. Para obter mais informações, consulte [esta seção](../../installation/using/deploying-an-instance.md#purging-data).

Para habilitar o rastreamento da Web anônimo em sua instância, os seguintes elementos devem ser configurados:

* O parâmetro **trackWebVisitors** do elemento de **redirecionamento** do arquivo **serverConf.xml** do servidor de rastreamento deve ser definido como &#39;**true**&#39;, para colocar um cookie permanente (**uuid230**) nos navegadores de usuários desconhecidos da Internet que visitam o site.
* O modo **Anonymous Web Tracking** deve ser selecionado na tela de configuração de rastreamento do assistente de implantação.

   ![](assets/webtracking_anonymous_set.png)

* Formulários da Web e pesquisas devem ser publicados e executados no servidor de rastreamento. A opção correspondente deve ser selecionada no assistente de implantação.

   ![](assets/webtracking_publication_set_for_webapps.png)

