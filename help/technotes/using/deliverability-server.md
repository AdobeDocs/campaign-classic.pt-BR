---
product: campaign
title: Atualizar para o novo servidor de avaliação do delivery
description: Saiba como atualizar para o novo servidor de entrega do Campaign
feature: Technote, Deliverability
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 19b40f0b827c4b5b7b6484fe4953aebe61d00d1d
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 16%

---

# Atualizar para o novo servidor de avaliação do delivery {#acc-deliverability}

A partir da [v7.2.2 versão](../../rn/using/latest-release.md#release-7-2-2), a Adobe Campaign conta com um novo servidor de entrega que oferece alta disponibilidade e resolve problemas de conformidade de segurança. O Campaign Classic agora sincroniza as regras de capacidade de entrega, broadlogs e o endereço de supressão de e para o novo servidor de capacidade de entrega. O servidor de entrega antigo será descontinuado em 31 de agosto de 2022.

Como cliente do Campaign Classic, você deve implementar o novo servidor de avaliação de entrega **antes de 31 de agosto de 2022**.

>[!NOTE]
>
>Para obter mais informações sobre essas alterações, consulte as [Perguntas frequentes](#faq) ou entre em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.
>

## O que mudou?{#acc-deliverability-changes}

A Adobe está desativando data centers mais antigos devido a motivos de conformidade de segurança. Os clientes do Adobe Campaign Classic precisam migrar para o novo serviço de entrega, hospedado no Amazon Web Service (AWS).

Esse novo servidor garante uma alta disponibilidade (99,9)&#x200B; e fornece endpoints seguros e autenticados para permitir que os servidores de campanha busquem os dados necessários: em vez de se conectar ao banco de dados para cada solicitação, o novo servidor de capacidade de entrega armazena os dados em cache para atender às solicitações, quando possível. Esse mecanismo melhora o tempo de resposta.&#x200B;

## Você será afetado?{#acc-deliverability-impacts}

Todos os clientes foram afetados e devem atualizar para o [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (ou mais) e implementar seu ambiente para se beneficiarem do novo servidor de avaliação de entrega.

## Como atualizar?{#acc-deliverability-update}

Como **cliente hospedado**, o Adobe trabalhará com você para atualizar sua(s) instância(s) para a versão mais recente e criar o projeto no Adobe Developer Console.

Como **cliente local/híbrido**, você precisa atualizar para o [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (ou mais) para se beneficiar do novo servidor de avaliação de entrega. Depois que todas as instâncias forem atualizadas, você deverá [implementar a nova integração](#implementation-steps) para o servidor de entrega do Adobe e garantir uma transição contínua.

## Etapas de implementação {#implementation-steps}

>[!WARNING]
>
>Essas etapas só devem ser executadas para implementações híbridas e no local.

Como parte da nova integração do servidor de entrega, o Campaign precisa se comunicar com o Adobe Shared Services por meio de uma autenticação baseada no Identity Management Service (IMS). A maneira preferida é usar o Gateway Token baseado em Adobe Developer (também chamado de Technical Account Token ou Adobe IO JWT).

>[!AVAILABILITY]
>
> A credencial de conta de serviço (JWT) está sendo descontinuada pela Adobe. As integrações do Campaign com soluções e aplicativos Adobe agora devem usar a credencial de servidor para servidor OAuth. </br>
>
> * Se você implementou integrações de entrada com o Campaign, é necessário migrar a conta técnica conforme detalhado [nesta documentação](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). As credenciais da Conta de Serviço (JWT) existentes continuarão a funcionar até 27 de janeiro de 2025. </br>
>
> * Se você tiver implementado integrações de saída, como a integração do Campaign com o Analytics ou a integração dos acionadores da Experience Cloud, elas continuarão a funcionar até 27 de janeiro de 2025. No entanto, antes dessa data, você deve atualizar o ambiente do Campaign para a v7.4.1 e migrar sua conta técnica para o OAuth. 

### Pré-requisitos{#prerequisites}

Antes de iniciar a implementação, verifique a configuração da instância.

1. Abra o console do cliente Campaign e faça logon no Adobe Campaign como administrador.
1. Navegue até **Administração > Plataforma > Opções**.
1. Verifique se o valor da opção `DmRendering_cuid` está preenchido.

   * Se a opção estiver preenchida, é possível iniciar a implementação.
   * Se nenhum valor for preenchido, entre em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} para obter seu CUID.

   Essa opção deve ser preenchida em todas as instâncias do Campaign (MKT, MID, RT, EXEC) com o valor correto. Como um cliente híbrido, entre em contato com o Adobe para ter a opção definida em suas instâncias MID, RT e EXEC.

Como cliente local, você também deve verificar se uma Campanha **[!UICONTROL Product profile]** está disponível para sua Organização. Para fazer isso, siga as etapas abaixo:

1. Como Administrador, conecte-se ao [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}.
1. Acesse a seção **Produtos e Serviços** e verifique se o **Adobe Campaign** está listado.
Se você não conseguir ver o **Adobe Campaign**, entre em contato com o [Adobe Customer Care](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} para adicioná-lo.
1. Clique em **Adobe Campaign** e selecione sua Organização.
   **Atenção**: se você tiver mais de uma organização, certifique-se de selecionar a correta. Saiba mais sobre as Organizações [nesta página](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.

1. Verifique se **[!UICONTROL Product profile]** existe. Caso contrário, crie-o. Nenhuma permissão é necessária para este **[!UICONTROL Product profile]**.


>[!CAUTION]
>
>Como cliente local, se um firewall estiver implementado da sua parte, você deverá adicionar esta url `https://deliverability-service.adobe.io` à sua inclui na lista de permissões. [Saiba mais](../../installation/using/url-permissions.md).


### Etapa 1: criar/atualizar o projeto do Adobe Developer {#adobe-io-project}

Para continuar com a configuração do conector do Adobe Analytics, acesse o Adobe Developer Console e crie um projeto OAuth de “servidor para servidor”.

Consulte [esta página](../../integrations/using/oauth-technical-account.md#oauth-service) para obter a documentação detalhada.

### Etapa 2: adicionar as credenciais do projeto no Adobe Campaign {#add-credentials-campaign}

Siga as etapas detalhadas [nesta página](../../integrations/using/oauth-technical-account.md#add-credentials) para adicionar suas credenciais do projeto OAuth no Adobe Campaign.

### Etapa 3: validar sua configuração

Para verificar se a integração foi bem-sucedida, siga as etapas abaixo:

1. Abra o console do cliente e faça logon no Adobe Campaign.
1. Navegue até **Administração > Produção > Workflows técnicos**.
1. Reinicie o fluxo de trabalho **Atualizar para capacidade de entrega** (deliverabilityUpdate). Isso deve ser executado em todas as instâncias do Campaign (MKT, MID, RT, EXEC). Como um cliente híbrido, entre em contato com o Adobe para reiniciar o fluxo de trabalho nas instâncias MID, RT e EXEC.
1. Verificar logs: o workflow deve ser executado sem erros.

>[!CAUTION]
>
>Após a atualização, a **Rede de propagação de Atualização para Renderização da Caixa de Entrada (updateRenderingSeeds)** do fluxo de trabalho deve ser interrompida, pois não será mais aplicada e falhará.

## Perguntas frequentes {#faq}

### Qual é a linha do tempo da atualização?

A transição para o novo servidor de entrega, permitindo a adição desses recursos aprimorados e reforçando a segurança, começará em 22 de julho para os clientes hospedados (Campaign Managed Services). Todos os clientes hospedados serão atualizados até o final de agosto.

Os clientes no local e híbridos devem fazer a transição durante o mesmo período.

### O que acontece se eu não atualizar meu ambiente?

Qualquer instância do Campaign não atualizada até 31 de agosto não poderá mais se conectar ao servidor de avaliação do delivery do Campaign. Como consequência, o fluxo de trabalho **Atualizar para capacidade de entrega** (deliverabilityUpdate) falhará, e sua capacidade de entrega será afetada.

Se você não atualizar seu ambiente, as configurações de email deixarão de ser sincronizadas (regras de Gerenciamento MX, regras de Email de entrada, regras de Gerenciamento de domínio e regras de qualificação de rejeição). Isso pode afetar com o tempo sua capacidade de delivery. Se uma alteração significativa for feita nessas regras, elas terão de ser aplicadas manualmente a partir deste ponto.

Para instâncias MKT, somente [Lista de Supressão Global](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) é afetada.
