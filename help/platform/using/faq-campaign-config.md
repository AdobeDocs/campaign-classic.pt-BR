---
product: campaign
title: Perguntas frequentes sobre configurações do Campaign
description: Perguntas frequentes sobre o Campaign Classic
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 50bed489-2a0f-4123-a326-3d68c8295662
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 96%

---

# Perguntas frequentes sobre configurações do Campaign {#settings-faq}

![](../../assets/v7-only.svg)

Conheça as principais configurações para definir a instância do Campaign de acordo com as suas necessidades.

## Posso alterar o idioma da interface do Campaign? {#can-i-change-the-language-of-campaign-interface-}

O idioma do Campaign é selecionado ao criar a instância. Não é possível alterá-lo posteriormente. Para obter mais informações, consulte [esta seção](../../installation/using/creating-an-instance-and-logging-on.md).

A interface do usuário do Adobe Campaign está disponível em 4 idiomas: inglês, francês, alemão e japonês. Observe que o console do cliente e o servidor devem ser definidos com o mesmo idioma. Cada instância do Campaign só pode ser executada em um idioma.

Em inglês, ao instalar o Campaign, você pode selecionar inglês americano ou inglês do Reino Unido: eles diferem nos formatos de data e hora. Para obter mais informações sobre essas diferenças, consulte [esta seção](../../platform/using/adobe-campaign-workspace.md#date-and-time).

## Posso usar o Campaign Classic com outras soluções da Adobe? {#can-i-use-campaign-classic-with-other-adobe-solutions-}

É possível combinar as funcionalidades de entrega e as funcionalidades avançadas de gestão do Adobe Campaign com um conjunto de soluções criadas para ajudar a personalizar a experiência dos usuários.

Clique aqui para saber [como trabalhar com outras soluções da Adobe](../../integrations/using/about-campaign-integrations.md) e [como configurar o IMS no Campaign](../../integrations/using/about-adobe-id.md).

## Como posso configurar recursos de rastreamento na minha instância do Campaign? {#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

Como um usuário especialista, você pode configurar recursos de rastreamento em sua instância do Campaign.

[Clique aqui para saber mais](../../installation/using/deploying-an-instance.md#tracking-configuration).

## Como configurar a capacidade de entrega de emails? {#how-to-configure-email-deliverability-}

Além do [Manual de práticas recomendadas de delivery da Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR), leia as recomendações técnicas de capacidade de delivery para entender como configurar sua instância para maximizar os recursos de delivery do Campaign.

[Clique aqui para saber mais](../../delivery/using/about-deliverability.md).

## Como posso implementar a aprovação de conteúdo? {#how-can-i-implement-content-approval-}

O Campaign permite configurar processos de aprovação para as principais etapas da campanha de marketing, em modo colaborativo. Para cada campanha você pode aprovar o target, o conteúdo e os custos do delivery. Os operadores do Adobe Campaign responsáveis pela aprovação podem ser notificados por e-mail e podem aceitar ou rejeitar a aprovação por meio do console ou por meio de uma conexão com a Web.

[Clique aqui para saber mais](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries) e descobrir etapas para implementar sua aprovação de entrega de conteúdo no Campaign.

## Como posso acessar dados armazenados em um banco de dados externo? {#how-can-i-access-data-stored-in-an-external-database-}

O Adobe Campaign oferece a opção Federated Data Access (FDA) para processar informações armazenadas em um ou mais bancos de dados externos: é possível acessá-los sem alterar a estrutura dos dados do Adobe Campaign.

[Clique aqui para saber mais](../../installation/using/connecting-to-database.md).

## A quais bancos de dados externos posso conectar o Campaign? {#which-external-databases-can-i-connect-campaign-to-}

Os bancos de dados externos compatíveis com o Campaign por meio do Federated Data Access (FDA) estão listados na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

## O Adobe Campaign pode ser integrado ao LDAP? {#can-adobe-campaign-integrate-with-ldap-}

Como cliente local/híbrido, você pode integrar o Campaign Classic com seu diretório LDAP.

[Clique aqui para saber como](../../installation/using/connecting-through-ldap.md).

## Como posso configurar conectores de CRM no Campaign? {#how-can-i-set-up-crm-connectors-in-campaign-}

O Adobe Campaign fornece vários conectores de CRM para vincular sua plataforma a sistemas de terceiros. Esses conectores de CRM permitem sincronizar contatos, contas, compras, etc. Eles facilitam a integração de seu aplicativo com vários aplicativos de terceiros e corporativos.

Esses conectores permitem uma integração de dados rápida e fácil: o Adobe Campaign fornece um assistente dedicado para coletar e selecionar entre as tabelas disponíveis no CRM. Isso garante a sincronização bidirecional para assegurar que os dados estejam sempre atualizados em todos os sistemas.

Leia [Configurar conectores de CRM](../../platform/using/crm-connectors.md) para saber como sincronizar a ferramenta de CRM com o Adobe Campaign.

![](assets/do-not-localize/how-to-video.png) Assista a este vídeo de caso de uso sobre a [integração do Adobe Campaign e do Microsoft Dynamics 365](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/integrating/dynamics365-integration.html?lang=pt-BR).

## Como executar o Soft Cache Clear quando os problemas são específicos da máquina ou do usuário? {#perform-soft-cache-clear}

Se houver problemas como os novos logotipos que são refletidos corretamente, quando os dados específicos da máquina/usuário são exportados com êxito, talvez seja necessário fazer uma limpeza do Soft Cache com o Windows (Windows 7, Windows XP, Windows 10).

Depois de fazer logon, acesse o **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**. Depois disso, faça logoff e login novamente.

![](assets/faq_soft_cache.png)

Se isso ainda não ajudar, tente limpar o Hard Cache por meio da execução das etapas abaixo.

## Como executar o Hard Cache Clear quando os problemas são específicos da máquina ou do usuário? {#perform-hard-cache-clear}

Se houver problemas como os novos logotipos que são refletidos corretamente, quando os dados específicos da máquina/usuário são exportados com êxito, talvez seja necessário fazer uma limpeza do Hard Cache com o Windows (Windows 7, Windows XP, Windows 10).

1. No console do cliente, escolha **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**.

1. Faça logoff e feche o console do cliente (cliente avançado).

1. Acesse os seguintes locais de acordo com a versão do seu sistema operacional:

   * Windows 7: C:\Users\ &lt; Username > \AppData\Roaming\Neolane\NL_5\
   * Windows XP: C:\Documents and Settings\ &lt; Username > \Application Data\Neolane\NL_5

   Aqui você verá muitos arquivos xml nomeados como nlclient-config-&lt; alphanumerical value >.xml.

1. Exclua esses arquivos xml e pastas associadas.

   >[!IMPORTANT]
   >
   >Não exclua o arquivo nlclient_cnx.xml.

1. Faça logon no console do cliente.
