---
product: campaign
title: Trabalho com modelos de entrega
description: Introdução a modelos de entrega
feature: Delivery Templates
role: User
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: 446062946b64c9a4d065b6a56d263914cbe628f8
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 79%

---

# Trabalho com modelos de entrega {#about-templates}

A configuração da entrega pode ser salva em um template de entrega para ser reutilizada. O template pode conter uma configuração completa ou parcial da entrega.

![](assets/s_user_template_list.png)

Há dois tipos de templates:

1. Modelos de entrega nativos do Adobe Campaign - Os modelos nativos NÃO DEVEM ser excluídos do sistema. Eles incluem uma configuração mínima para cada canal de entrega. No entanto, o administrador pode restringir determinadas funções ou oferecer valores padrão aos usuários (rastreamento de ativação, endereços de email de remetentes etc.). Os cenários nativos aparecem em negrito na lista de templates. Eles devem ser duplicados para serem modificados.

1. Modelos de entrega predefinidos - O administrador do Adobe Campaign pode criar novos modelos de entrega. Eles podem ser reutilizados por operadores (aqueles com direitos de acesso adequados) ou automaticamente por processos de servidor. Por exemplo, você pode configurar um modelo de entrega de email e, quando os usuários criarem uma entrega usando esse modelo, bastará inserir o texto ou o conteúdo HTML e depois enviá-lo; as outras opções já terão sido definidas pelo administrador.


Saiba como criar e usar modelos de entrega na [documentação do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/create-templates){target="_blank"}.