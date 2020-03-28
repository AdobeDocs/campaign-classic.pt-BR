---
title: Testar o rastreamento
seo-title: Testar o rastreamento
description: Testar o rastreamento
seo-description: null
page-status-flag: never-activated
uuid: 76d84ab4-b632-4498-96a1-ce9c773ec125
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 4ed23249-4ecf-4e57-91b3-6fae1387bd6a
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Testar o rastreamento{#testing-tracking}

É possível testar o rastreamento em páginas de espelhamento, registros de email e links. Para fazer isso:

1. Crie um novo delivery de email que será usado para teste.
1. Especifique o usuário que receberá o email. Como esse usuário terá de abrir o email e clicar nos links que ele contém, verifique se foi selecionado um endereço de recipiente de teste de controle.
1. Adicione um bloco de personalização de página espelhada (MirrorPage) no conteúdo de email.
1. Envie a entrega contendo um link para a página espelho.
1. Depois de receber o email, abra-o e clique no link da página espelho.
1. Depois de ser redirecionado corretamente para a página espelho, acesse a pasta **Administration > Technical workflows** e abra o workflow **Tracking**.
1. Inicie o fluxo de trabalho, clique com o botão direito do mouse na atividade **Scheduler** e selecione **Execute pending task now**.
1. Aguarde 30 segundos e selecione a guia **Audit.** Verifique se pelo menos um registro de log de rastreamento é encontrado.

   Clique em **Refresh** se não visualizar novos logs.

1. Vá para a página de perfil do recipiente utilizado para o teste e selecione a guia **Tracking.** Alguns registros devem aparecer com o valor **Mirror Page** na coluna **Type**.

   >[!NOTE]
   >
   >A página de perfil do recipient está localizada na pasta **Profiles and Targets > Recipients** por padrão.

   Para verificar o rastreamento do log de email, procure os valores **Open** e **[!UICONTROL Email click]** na coluna **Type**.

   Se os logs abertos não forem exibidos, acesse o delivery e as **Properties** para garantir que as opções **Active tracking** e **[!UICONTROL Opens tracking]** estão habilitadas.

