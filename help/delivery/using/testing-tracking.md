---
product: campaign
title: Testar o rastreamento de mensagens
description: Saiba como testar o rastreamento de mensagens
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Monitoring
role: User
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 100%

---

# Testar o rastreamento de mensagens{#testing-tracking}

É possível testar o rastreamento em mirror pages, registros de email e links. Para fazer isso:

1. Crie uma nova entrega de email que será usada para teste.
1. Especifique o usuário que receberá o email. Como esse usuário terá de abrir o email e clicar nos links que ele contém, verifique se foi selecionado um endereço de destinatárioe de teste de controle.
1. Adicione um bloco de personalização de mirror page (MirrorPage) no conteúdo de email.
1. Envie a entrega contendo um link para a mirror page.
1. Depois de receber o email, abra-o e clique no link da mirror page.
1. Depois de ser redirecionado corretamente para a mirror page, acesse a pasta **Administration > Technical workflows** e abra o workflow **Tracking**.
1. Inicie o fluxo de trabalho, clique com o botão direito do mouse na atividade **Scheduler** e selecione **Execute pending task now**.
1. Aguarde 30 segundos e selecione a guia **Audit.** Verifique se pelo menos um registro de log de rastreamento é encontrado.

   Clique em **Refresh** se não visualizar novos logs.

1. Vá para a página de perfil do destinatárioe utilizado para o teste e selecione a guia **Tracking.** Alguns registros devem aparecer com o valor **Mirror Page** na coluna **Type**.

   >[!NOTE]
   >
   >A página de perfil do destinatário está localizada na pasta **Profiles and Targets > Recipients** por padrão.

   Para verificar o rastreamento do log de email, procure os valores **Open** e **[!UICONTROL Email click]** na coluna **Type**.

   Se os logs abertos não forem exibidos, acesse a entrega e as **Properties** para garantir que as opções **Active tracking** e **[!UICONTROL Opens tracking]** estão habilitadas.
