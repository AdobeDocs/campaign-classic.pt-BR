---
title: Sobre os modelos
seo-title: Sobre os modelos
description: Sobre os modelos
seo-description: null
page-status-flag: never-activated
uuid: 13b5ad3a-aded-43b8-ae4d-c23aa7bc17bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: 22e289d0-c33c-4daa-a893-b292e523f30b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 96%

---


# Sobre os modelos{#about-templates}

A configuração do delivery pode ser salva em um template de delivery para ser reutilizada. O template pode conter uma configuração completa ou parcial do delivery.

O delivery de template pode ser executado manualmente, conforme descrito neste capítulo, ou de acordo com um evento (iniciado em um horário definido, na chegada de um arquivo etc.). Delivery templates can be configured via the **[!UICONTROL Resources > Templates > Delivery templates]** node in the tree.

![](assets/s_user_template_list.png)

Há dois tipos de templates:

1. Templates de delivery nativo do Adobe Campaign

   Os templates nativos NÃO DEVEM ser excluídos do sistema. Eles incluem uma configuração mínima para cada canal de delivery. No entanto, o administrador pode restringir determinadas funções ou oferecer valores padrão aos usuários (rastreamento de ativação, endereços de email de remetentes etc.). Os cenários nativos aparecem em negrito na lista de templates. Eles devem ser duplicados para serem modificados.

1. Templates de delivery predefinidos

   O administrador do Adobe Campaign pode criar novos templates de delivery. Eles podem ser reutilizados por operadores (aqueles com direitos de acesso adequados) ou automaticamente por processos de servidor. Por exemplo, você pode configurar um template de delivery de email, e quando o usuário cria um delivery usando esse template, basta inserir o texto ou o conteúdo HTML e depois enviá-lo; as outras opções já foram definidas pelo administrador.

>[!NOTE]
>
>Os templates disponíveis dependem dos direitos de acesso, da sua configuração de instância e do contexto. Por exemplo, ao criar um serviço de informações, é possível vincular um template de delivery para mensagens de confirmação: você pode então acessar apenas os modelos cujo target mapping é o mapeamento de subscrição. Para obter mais informações, consulte [Seleção de target mapping](../../delivery/using/selecting-a-target-mapping.md) e [Sobre serviços e assinaturas](../../delivery/using/about-services-and-subscriptions.md).
