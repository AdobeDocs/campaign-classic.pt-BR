---
product: campaign
title: Atualizar para o novo servidor de avaliação do delivery
description: Saiba como atualizar para o novo servidor de entrega do Campaign
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 50ef144950ca9e79b1b3acdf587ffc13e0beeec4
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 20%

---

# Atualizar para o novo servidor de avaliação do delivery {#acc-deliverability}

Iniciando [Versão v7.2.2](../../rn/using/latest-release.md#release-7-2-2), a Adobe Campaign conta com um novo servidor de entrega que oferece alta disponibilidade e aborda problemas de conformidade de segurança. O Campaign Classic agora sincroniza as regras de capacidade de entrega, broadlogs e o endereço de supressão de e para o novo servidor de capacidade de entrega. O servidor de entrega antigo será descontinuado em 31 de agosto de 2022.

Como cliente do Campaign Classic, você deve implementar o novo servidor de capacidade de entrega **antes de 31 de agosto de 2022**.

>[!NOTE]
>
>Para obter mais informações sobre essas alterações, consulte o [Perguntas frequentes](#faq), ou entre em contato com [Atendimento ao cliente Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.

## O que mudou?{#acc-deliverability-changes}

A Adobe está desativando data centers mais antigos devido a motivos de conformidade de segurança. Os clientes do Adobe Campaign Classic precisam migrar para o novo serviço de entrega, hospedado no Amazon Web Service (AWS).

Esse novo servidor garante uma alta disponibilidade (99,9)&#x200B; e fornece endpoints seguros e autenticados para permitir que os servidores de campanha busquem os dados necessários: em vez de se conectar ao banco de dados para cada solicitação, o novo servidor de capacidade de entrega armazena os dados em cache para atender às solicitações, quando possível. Esse mecanismo melhora o tempo de resposta.&#x200B;

## Você será afetado?{#acc-deliverability-impacts}

Todos os clientes foram afetados e devem atualizar para [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (ou mais) e implementar seu ambiente para se beneficiar do novo servidor de capacidade de delivery.

## Como atualizar?{#acc-deliverability-update}

Como um **cliente hospedado**, o Adobe trabalhará com você para atualizar suas instâncias para a versão mais recente e criar o projeto no Adobe Developer Console.

Como um **cliente no local/híbrido**, é necessário atualizar para [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (ou mais) para se beneficiar do novo servidor de capacidade de entrega. Depois que todas as instâncias forem atualizadas, você deverá [implementar a nova integração](#implementation-steps) para o servidor de deliverability Adobe e garantir uma transição contínua.

## Etapas de implementação {#implementation-steps}

Como parte da nova integração do servidor de entrega, o Campaign precisa se comunicar com o Adobe Shared Services por meio de uma autenticação baseada no Identity Management Service (IMS). A maneira preferida é usar o Gateway Token baseado em Adobe Developer (também chamado de Technical Account Token ou Adobe IO JWT).

>[!WARNING]
>
>Essas etapas só devem ser executadas para implementações híbridas e no local.

### Pré-requisitos{#prerequisites}

Antes de iniciar a implementação, verifique a configuração da instância.

1. Abra o console do cliente Campaign e faça logon no Adobe Campaign como administrador.
1. Navegue até **Administração > Plataforma > Opções**.
1. Verifique se `DmRendering_cuid` o valor da opção está preenchido.

   * Se a opção estiver preenchida, é possível iniciar a implementação.
   * Se nenhum valor for preenchido, entre em contato com [Atendimento ao cliente Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} para obter seu CUID.

   Essa opção deve ser preenchida em todas as instâncias do Campaign (MKT, MID, RT, EXEC) com o valor correto. Como um cliente híbrido, entre em contato com o Adobe para ter a opção definida em suas instâncias MID, RT e EXEC.

Como cliente local, você também deve verificar se uma campanha **[!UICONTROL Product profile]** O está disponível para sua organização da. Para fazer isso, siga as etapas abaixo:

1. Como Administrador, conecte-se [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}.
1. Acesse o **Produtos e serviços** seção e verificar **Adobe Campaign** está listado.
Se você não conseguir ver **Adobe Campaign** contato [Atendimento ao cliente Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} para adicioná-lo.
1. Clique em **Adobe Campaign** e selecione sua organização.
   **Cuidado**: se você tiver mais de uma organização, selecione a correta. Saiba mais sobre Organizações [nesta página](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.

1. Verifique se um **[!UICONTROL Product profile]** existe. Caso contrário, crie-o. Nenhuma permissão é necessária para este **[!UICONTROL Product profile]**.


>[!CAUTION]
>
>Como cliente local, se um firewall estiver implementado em seu lado, você deverá adicionar esse url `https://deliverability-service.adobe.io` para a sua inclui na lista de permissões. [Saiba mais](../../installation/using/url-permissions.md).


### Etapa 1: criar/atualizar seu projeto do Adobe Developer {#adobe-io-project}

1. Access [Console do Adobe Developer](https://developer.adobe.com/console/home) e faça logon com o Acesso de desenvolvedor da sua organização. Verifique se você está conectado ao portal correto da organização.
   **Cuidado**: se você tiver mais de uma organização, selecione a correta. Saiba mais sobre Organizações [nesta página](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.
1. Selecione **[!UICONTROL Create new project]**.
   ![](assets/New-Project.png)

   >[!CAUTION]
   >
   >Se você já estiver usando a funcionalidade de autenticação JWT do Adobe IO para outra integração, como conector do Analytics ou acionadores de Adobe, será necessário atualizar o projeto adicionando **API do Campaign** para esse projeto.

1. Escolha **[!UICONTROL Add API]**.
   ![](assets/Add-API.png)
1. Na janela **[!UICONTROL Add an API]**, selecione **[!UICONTROL Adobe Campaign]**.
   ![](assets/AC-API.png)
1. Se a ID do cliente estiver vazia, selecione **[!UICONTROL Generate a key pair]** para criar um par de chaves público e privado.
   ![](assets/Generate-a-key-pair.png)

   As chaves serão baixadas automaticamente com uma data de expiração padrão de 365 dias. Depois de expirar, você precisará criar um novo par de chaves e atualizar a integração no arquivo de configuração. Usando a Opção 2, você pode optar por criar e fazer upload manualmente da **[!UICONTROL Public key]** com uma data de expiração mais longa.
   ![](assets/New-key-pair.png)

   >[!CAUTION]
   >
   >Você deve salvar o `config.zip` arquivo quando o prompt de download aparecer, pois você não poderá baixá-lo novamente.

1. Clique em **[!UICONTROL Next]**.
1. Escolha qualquer **[!UICONTROL Product profile]** existente ou crie um novo, se necessário. Nenhuma permissão é necessária para este **[!UICONTROL Product profile]**. Para obter mais informações sobre **[!UICONTROL Product Profiles]**, consulte [esta página](https://helpx.adobe.com/br/enterprise/using/manage-developers.html){_blank}.
   ![](assets/Product-Profile-API.png)

   Em seguida, clique em **[!UICONTROL Save configured API]**.

1. Em seu projeto, selecione **[!UICONTROL Adobe Campaign]** e copie as seguintes informações em **[!UICONTROL Service Account (JWT)]**

   ![](assets/Config-API.png)

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

>[!CAUTION]
>
>O certificado do Adobe Developer expirará após 12 meses. Você precisa gerar um novo par de chaves todo ano.

### Etapa 2: adicionar as credenciais do projeto no Adobe Campaign {#add-credentials-campaign}

A chave privada deve ser codificada no formato base64 UTF-8.

Para fazer isso:

1. Use a chave privada gerada nas etapas acima.
1. Codifique a chave privada usando o seguinte comando: `base64 ./private.key > private.key.base64`. Isso salvará o conteúdo base64 em um novo arquivo `private.key.base64`.

   >[!NOTE]
   >
   >Às vezes, uma linha extra pode ser adicionada automaticamente ao copiar/colar a chave privada. Lembre-se de removê-la antes de codificar sua chave privada.

1. Copie o conteúdo do arquivo `private.key.base64`.
1. Faça logon via SSH em cada container em que a instância do Adobe Campaign está instalada e adicione as credenciais do Projeto no Adobe Campaign executando o comando a seguir como usuário`neolane`. Isso inserirá as credenciais **[!UICONTROL Technical Account]** no arquivo de configuração da instância.

   ```sql
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. Você deve interromper e reiniciar o servidor para que a modificação seja considerada. Você também pode executar um `config -reload` comando.

### Etapa 3: ativar o novo servidor de capacidade de entrega

Agora você pode ativar o novo servidor de capacidade de entrega. Para fazer isso:

1. Abra o console do cliente e faça logon no Adobe Campaign como Administrador.
1. Navegue até **Administração > Plataforma > Opções**.
1. Acesse o `NewDeliverabilityServer_FeatureFlag` e defina o valor como `1`. Essa configuração deve ser executada em todas as instâncias do Campaign (MKT, MID, RT, EXEC). Como um cliente híbrido, entre em contato com o Adobe para ter a opção definida em suas instâncias MID, RT e EXEC.

### Etapa 4: validar sua configuração

Para verificar se a integração foi bem-sucedida, siga as etapas abaixo:

1. Abra o console do cliente e faça logon no Adobe Campaign.
1. Navegue até **Administração > Produção > Workflows técnicos**.
1. Reinicie o **Atualizar para entregabilidade** (deliverabilityUpdate). Isso deve ser executado em todas as instâncias do Campaign (MKT, MID, RT, EXEC). Como um cliente híbrido, entre em contato com o Adobe para reiniciar o fluxo de trabalho nas instâncias MID, RT e EXEC.
1. Verificar logs: o workflow deve ser executado sem erros.

>[!CAUTION]
>
>Após a atualização, a variável **Atualização da rede seed para renderização da caixa de entrada (updateRenderingSeeds)** o workflow deve ser interrompido, pois não será mais aplicado e falhará.

## Perguntas frequentes {#faq}

### Qual é a linha do tempo da atualização?

A transição para o novo servidor de entrega, permitindo a adição desses recursos aprimorados e reforçando a segurança, começará em 22 de julho para os clientes hospedados (Campaign Managed Services). Todos os clientes hospedados serão atualizados até o final de agosto.

Os clientes no local e híbridos devem fazer a transição durante o mesmo período.

### O que acontece se eu não atualizar meu ambiente?

Qualquer instância do Campaign não atualizada até 31 de agosto não poderá mais se conectar ao servidor de avaliação do delivery do Campaign. Em consequência, a **Atualizar para entregabilidade** (deliverabilityUpdate) falhará, e isso afetará sua capacidade de delivery.

Se você não atualizar seu ambiente, as configurações de email deixarão de ser sincronizadas (regras de Gerenciamento MX, regras de Email de entrada, regras de Gerenciamento de domínio e regras de qualificação de rejeição). Isso pode afetar com o tempo sua capacidade de delivery. Se uma alteração significativa for feita nessas regras, elas terão de ser aplicadas manualmente a partir deste ponto.

Para instâncias MKT, somente [Lista de supressão global](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) é afetada.
