---
product: campaign
title: Tracking anônimo
description: Saiba como configurar o rastreamento anônimo
feature: Configuration, Instance Settings
role: Developer
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
TQID: 'https://experienceleague.adobe.com/jQ4x9zONaJacdqaNqRL--oeMUAyn53Rk-u3jOvKv-20'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 5%
---
# Tracking anônimo{#anonymous-tracking}

O Adobe Campaign permite vincular informações de rastreamento Web coletadas a um recipient quando ele navega em seu site anonimamente. Quando um usuário navega pelas páginas marcadas do seu site, essas informações de navegação são coletadas, de modo que, uma vez clicado em um email enviado pelo Adobe Campaign, ele é identificado e as informações são vinculadas automaticamente a ele.

>[!IMPORTANT]
>
>A configuração do rastreamento anônimo em um site pode acionar a coleta de uma quantidade significativa de logs de rastreamento, afetando assim a operação do banco de dados. Configure com cuidado.\
>Os logs de rastreamento são salvos no banco de dados até que os dados de rastreamento sejam removidos. Use o assistente de implantação para configurar a frequência de limpeza. Para obter mais informações, consulte [esta seção](../../installation/using/deploying-an-instance.md#purging-data).

Para habilitar o rastreamento web anônimo na sua instância, os seguintes elementos devem ser configurados:

* O parâmetro **trackWebVisitors** do elemento **redirection** do arquivo **serverConf.xml** do servidor de rastreamento deve ser definido como &#39;**true**&#39; para colocar um cookie permanente (**uuid230**) nos navegadores de usuários desconhecidos da Internet que visitam o site.
* O modo **Rastreamento web anônimo** deve ser selecionado na tela de configuração de rastreamento do assistente de implantação.

  ![](assets/webtracking_anonymous_set.png)

* Os formulários web devem ser publicados e executados no servidor de rastreamento. A opção correspondente deve ser selecionada no assistente de implantação.

  ![](assets/webtracking_publication_set_for_webapps.png)
