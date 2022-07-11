---
product: campaign
title: Migrar para o novo servidor de deliverability
description: Saiba como implementar o servidor de capacidade de entrega do Campaign
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: c3b1ffcb580c7510a64115e0abbf16cb766146c5
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 24%

---

# Servidor de capacidade de entrega do Campaign {#acc-deliverability}

A partir da versão 21.1 do Campaign Classic v7, a Adobe Campaign propõe um novo servidor de deliverability que oferece alta disponibilidade e aborda problemas de conformidade com a segurança. O Campaign Classic agora sincroniza as regras de entrega, os broadlogs e o endereço de supressão de e para o novo servidor de entrega.

Como cliente do Campaign Classic, você deve implementar o novo servidor de deliverability **antes de 31 de agosto de 2022**.

>[!NOTE]
>
>Para dúvidas sobre essas alterações, consulte a seção [Perguntas frequentes](#faq)ou entre em contato [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## O que mudou?{#acc-deliverability-changes}

O Adobe está descontinuando data centers mais antigos devido a motivos de conformidade com a segurança. Os clientes do Adobe Campaign Classic precisam migrar para o novo serviço de deliverability, hospedado no Amazon Web Service (AWS).

Esse novo servidor garante uma &#x200B; de alta disponibilidade (9.9) e fornece endpoints seguros e autenticados para permitir que os servidores de campanha busquem os dados necessários: em vez de se conectar ao banco de dados para cada solicitação, o novo servidor de deliverability armazena os dados em cache para atender às solicitações, sempre que possível. Esse mecanismo melhora o tempo de resposta. &#x200B;

## Você será afetado?{#acc-deliverability-impacts}

Se o ambiente foi implementado em uma build inferior a [Campaign v7.2.1](../../rn/using/latest-release.md#release-7-2-2), você será afetado. Você precisa atualizar para o Campaign v7.2.1 (ou mais).

Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Como atualizar?{#acc-deliverability-update}

Como um **cliente hospedado**, o Adobe trabalhará com você para atualizar suas instâncias para a versão mais recente e criar o projeto no Adobe Developer Console.

Como um **cliente local/híbrido**, é necessário atualizar para uma das versões mais recentes para se beneficiar do novo servidor de deliverability. Depois que todas as instâncias forem atualizadas, você poderá [implementar a nova integração](#implementation-steps) para o servidor de capacidade de entrega do Adobe e garanta uma transição contínua.

## Etapas de implementação {#implementation-steps}

Como parte da nova integração do servidor de deliverability, o Campaign precisa se comunicar com o Adobe Shared Services por meio de uma autenticação baseada no Identity Management Service (IMS). A maneira preferida é usar o Token de gateway baseado em Adobe Developer (também chamado de Token de conta técnica ou JWT de Adobe IO).


>[!WARNING]
>
>Essas etapas só devem ser executadas por implementações híbridas e no local.

### Pré-requisitos{#prerequisites}

Antes de iniciar a implementação, verifique a configuração da instância.

1. Abra o console do cliente do Campaign e faça logon no Adobe Campaign como um Administrador.
1. Navegue até **Administração > Plataforma > Opções**.
1. Verifique a `DmRendering_cuid` o valor da opção é preenchido.

   * Se a opção estiver preenchida, você poderá iniciar a implementação.
   * Se nenhum valor for preenchido, entre em contato com [Atendimento ao cliente do Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para obter seu CUID.

      Essa opção deve ser preenchida em todas as instâncias do Campaign (MKT, MID, RT, EXEC) com o mesmo valor.

### Etapa 1: Criar/atualizar seu projeto do Adobe Developer {#adobe-io-project}

1. Acesso [Console do Adobe Developer](https://developer.adobe.com/console/home) e faça logon com o acesso do desenvolvedor de sua organização.

   >[!NOTE]
   >
   > Verifique se você está conectado ao portal correto da organização.

1. Selecione **[!UICONTROL Create new project]**.
   ![](assets/New-Project.png)


   >[!CAUTION]
   >
   >Se você já estiver usando a funcionalidade de autenticação Adobe IO JWT para outra integração, como o conector do Analytics ou os Adobe Triggers, será necessário atualizar seu projeto adicionando **API do Campaign** para esse projeto.

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
   >Você deve salvar o `config.zip` quando o prompt de download aparecer, pois não será possível baixá-lo novamente.

1. Clique em **[!UICONTROL Next]**.
1. Escolha qualquer **[!UICONTROL Product profile]** existente ou crie um novo, se necessário. Nenhuma permissão é necessária para este **[!UICONTROL Product profile]**. Para obter mais informações sobre **[!UICONTROL Product Profiles]**, consulte [esta página](https://helpx.adobe.com/br/enterprise/using/manage-developers.html).
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
>O certificado da Adobe Developer expirará após 12 meses. Você precisa gerar um novo par de chaves todo ano.

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

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. Você deve interromper e reiniciar o servidor para que a modificação seja levada em conta. Também é possível executar um `config -reload` comando.

### Etapa 3: Ativar o novo servidor de capacidade de entrega

Agora você pode habilitar o novo servidor de deliverability. Para executar isso:

1. Abra o console do cliente e faça logon no Adobe Campaign as a Administrator.
1. Navegue até **Administração > Plataforma > Opções**.
1. Acesse o `NewDeliverabilityServer_FeatureFlag` e defina o valor como `1`. Essa configuração deve ser executada em todas as instâncias do Campaign (MKT, MID, RT, EXEC).

### Etapa 4: Validar sua configuração

Para verificar se a integração é bem-sucedida, siga as etapas abaixo:


1. Abra o console do cliente e faça logon no Adobe Campaign.
1. Navegue até **Administração > Produção > Workflows técnicos**.
1. Reinicie o **Atualização para entregabilidade** (deliverabilityUpdate) . Isso deve ser executado em todas as instâncias do Campaign (MKT, MID, RT, EXEC).
1. Logs de verificação: o workflow deve ser executado sem erros.


## Perguntas frequentes {#faq}

### O que acontece se eu não atualizar meu ambiente?

Qualquer instância do Campaign não atualizada até 31 de agosto não poderá mais se conectar ao servidor de capacidade de entrega do Campaign. Como consequência, a variável **Atualização para entregabilidade** O workflow (deliverabilityUpdate) falhará. Esse workflow gerencia a atualização diária das regras MX e regras de entrada.

Se você não atualizar seu ambiente, as configurações de email deixarão de ser sincronizadas (regras de Gerenciamento MX, regras de Email de entrada, regras de Gerenciamento de domínio e regras de qualificação de devolução). Isso pode afetar sua capacidade de entrega ao longo do tempo. Se se fizer uma alteração significativa nestas regras, estas terão de ser aplicadas manualmente a partir deste ponto.

Somente para instâncias MKT [Lista de Supressões Globais](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) for afetada.

### Não posso atualizar agora. Qual é a orientação?

Se não for possível atualizar sua instância antes de 31 de agosto, é necessário desativar temporariamente o **Atualização para entregabilidade** Fluxo de trabalho (deliverabilityUpdate) até que a atualização seja concluída para que não tente sincronizar com o servidor de deliverability antigo.



Para obter mais orientações, entre em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
