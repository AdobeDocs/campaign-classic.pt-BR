---
product: campaign
title: Sobre os modelos
description: Sobre os modelos
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Sobre os modelos{#about-templates}

A configuração do delivery pode ser salva em um template de delivery para ser reutilizada. O template pode conter uma configuração completa ou parcial do delivery.

O delivery de template pode ser executado manualmente, conforme descrito neste capítulo, ou de acordo com um evento (iniciado em um horário definido, na chegada de um arquivo etc.). Os templates de deliveries podem ser configurados por meio do nó **[!UICONTROL Resources > Templates > Delivery templates]** na árvore.

![](assets/s_user_template_list.png)

Há dois tipos de templates:

1. Templates de delivery nativo do Adobe Campaign

   Os templates nativos NÃO DEVEM ser excluídos do sistema. Eles incluem uma configuração mínima para cada canal de delivery. No entanto, o administrador pode restringir determinadas funções ou oferecer valores padrão aos usuários (rastreamento de ativação, endereços de email de remetentes etc.). Os cenários nativos aparecem em negrito na lista de templates. Eles devem ser duplicados para serem modificados.

1. Templates de delivery predefinidos

   O administrador do Adobe Campaign pode criar novos templates de delivery. Eles podem ser reutilizados por operadores (aqueles com direitos de acesso adequados) ou automaticamente por processos de servidor. Por exemplo, você pode configurar um template de delivery de email, e quando o usuário cria um delivery usando esse template, basta inserir o texto ou o conteúdo HTML e depois enviá-lo; as outras opções já foram definidas pelo administrador.

>[!NOTE]
>
>Os templates disponíveis dependem dos direitos de acesso, da sua configuração de instância e do contexto. Por exemplo, ao criar um serviço de informações, é possível vincular um template de delivery para mensagens de confirmação: você pode então acessar apenas os modelos cujo target mapping é o mapeamento de subscrição. Para obter mais informações, consulte [Selecionar um target mapping](selecting-a-target-mapping.md) e [Sobre serviços e assinaturas](about-services-and-subscriptions.md).
