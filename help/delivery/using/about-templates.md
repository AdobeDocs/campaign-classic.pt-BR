---
product: campaign
title: Sobre modelos
description: Introdução a modelos de entrega
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Delivery Templates
role: User
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 100%

---

# Sobre modelos{#about-templates}

A configuração da entrega pode ser salva em um template de entrega para ser reutilizada. O template pode conter uma configuração completa ou parcial da entrega.

O template da entrega pode ser executado manualmente, conforme descrito neste capítulo, ou de acordo com um evento (iniciado em um horário definido, na chegada de um arquivo etc.). Os templates de entregas podem ser configurados por meio do nó **[!UICONTROL Resources > Templates > Delivery templates]** na árvore.

![](assets/s_user_template_list.png)

Há dois tipos de templates:

1. Templates de entrega nativo do Adobe Campaign

   Os templates nativos NÃO DEVEM ser excluídos do sistema. Eles incluem uma configuração mínima para cada canal de entrega. No entanto, o administrador pode restringir determinadas funções ou oferecer valores padrão aos usuários (rastreamento de ativação, endereços de email de remetentes etc.). Os cenários nativos aparecem em negrito na lista de templates. Eles devem ser duplicados para serem modificados.

1. Templates de entrega predefinidos

   O administrador do Adobe Campaign pode criar novos templates de entrega. Eles podem ser reutilizados por operadores (aqueles com direitos de acesso adequados) ou automaticamente por processos de servidor. Por exemplo, você pode configurar um modelo de entrega de email e, quando os usuários criarem uma entrega usando esse modelo, bastará inserir o texto ou o conteúdo HTML e depois enviá-lo; as outras opções já terão sido definidas pelo administrador.

>[!NOTE]
>
>Os templates disponíveis dependem dos direitos de acesso, da sua configuração de instância e do contexto. Por exemplo, ao criar um serviço de informações, é possível vincular um template de entrega para mensagens de confirmação: você pode então acessar apenas os modelos cujo target mapping é o mapeamento de subscrição. Para obter mais informações, consulte [Selecionar um target mapping](selecting-a-target-mapping.md) e [Serviços e subscrições](about-services-and-subscriptions.md).
