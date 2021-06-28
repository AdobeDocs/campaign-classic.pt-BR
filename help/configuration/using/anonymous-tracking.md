---
product: campaign
title: Tracking anônimo
description: Tracking anônimo
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: ee3d643e4ba607b3d7ca816eabf862b867d1f3f4
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 6%

---

# Tracking anônimo{#anonymous-tracking}

O Adobe Campaign permite vincular informações de rastreamento Web coletadas a um recipient quando ele navega em seu site anonimamente. Quando um usuário navega nas páginas com tags do seu site, essas informações de navegação são coletadas, de modo que, uma vez clicadas em um email enviado pelo Adobe Campaign, elas são identificadas e as informações são vinculadas automaticamente a elas.

>[!IMPORTANT]
>
>Configurar o rastreamento anônimo em um site pode acionar a coleta de uma quantidade significativa de logs de rastreamento, afetando assim a operação do banco de dados. Configure com cuidado.\
>Os logs de rastreamento são salvos no banco de dados até que os dados de rastreamento sejam limpos. Use o assistente de implantação para configurar a frequência de limpeza. Para obter mais informações, consulte [esta seção](../../installation/using/deploying-an-instance.md#purging-data).

Para ativar o rastreamento Web anônimo em sua instância, os seguintes elementos devem ser configurados:

* O parâmetro **trackWebVisitors** do elemento **redirect** do arquivo **serverConf.xml** do servidor de rastreamento deve ser definido como &#39;**true**&#39; para colocar um cookie permanente (**uuid230**) nos navegadores de usuários desconhecidos da Internet que visitam o site.
* O modo **Rastreamento Web Anônimo** deve ser selecionado na tela de configuração de rastreamento do assistente de implantação.

   ![](assets/webtracking_anonymous_set.png)

* Os formulários web devem ser publicados e executados no servidor de rastreamento. A opção correspondente deve ser selecionada no assistente de implantação.

   ![](assets/webtracking_publication_set_for_webapps.png)
