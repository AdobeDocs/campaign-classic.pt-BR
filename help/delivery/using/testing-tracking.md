---
product: campaign
title: Testar o rastreamento de mensagens
description: Saiba como testar o rastreamento de mensagens
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: ht
source-wordcount: '256'
ht-degree: 100%

---

# Testar o rastreamento de mensagens{#testing-tracking}

![](../../assets/common.svg)

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
