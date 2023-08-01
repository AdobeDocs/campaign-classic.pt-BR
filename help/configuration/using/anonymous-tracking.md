---
product: campaign
title: Tracking anônimo
description: Saiba como configurar o rastreamento anônimo
feature: Configuration, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Aplicável somente ao Campaign Classic v7"
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 5%

---

# Tracking anônimo{#anonymous-tracking}

O Adobe Campaign permite vincular informações de rastreamento Web coletadas a um recipient quando ele navega em seu site anonimamente. Quando um usuário navega pelas páginas marcadas do seu site, essas informações de navegação são coletadas, de modo que, uma vez clicado em um email enviado pelo Adobe Campaign, ele é identificado e as informações são vinculadas automaticamente a ele.

>[!IMPORTANT]
>
>A configuração do rastreamento anônimo em um site pode acionar a coleta de uma quantidade significativa de logs de rastreamento, afetando assim a operação do banco de dados. Configure com cuidado.\
>Os logs de rastreamento são salvos no banco de dados até que os dados de rastreamento sejam removidos. Use o assistente de implantação para configurar a frequência de limpeza. Para obter mais informações, consulte [esta seção](../../installation/using/deploying-an-instance.md#purging-data).

Para habilitar o rastreamento web anônimo na sua instância, os seguintes elementos devem ser configurados:

* A variável **trackWebVisitors** parâmetro do **redirecionamento** elemento do **serverConf.xml** o arquivo do servidor de rastreamento deve ser definido como &#39;**true**&#39;, para colocar um cookie permanente (**uuid230**) nos navegadores de usuários desconhecidos da Internet que visitam o site.
* A variável **Rastreamento web anônimo** deve ser selecionado na tela de configuração de rastreamento do assistente de implantação.

  ![](assets/webtracking_anonymous_set.png)

* Os formulários web devem ser publicados e executados no servidor de rastreamento. A opção correspondente deve ser selecionada no assistente de implantação.

  ![](assets/webtracking_publication_set_for_webapps.png)
