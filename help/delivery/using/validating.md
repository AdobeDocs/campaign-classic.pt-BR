---
title: Validação
seo-title: Validação
description: Validação
seo-description: null
page-status-flag: never-activated
uuid: e3cd96ef-4f5d-4e17-9fec-5eaa4d835cb1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
discoiquuid: c363a7cf-81a5-4c02-a021-b822eeeadd03
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '242'
ht-degree: 100%

---


# Validação{#validating}

Os conceitos globais ao validar um delivery são apresentados [nesta seção](../../delivery/using/steps-validating-the-delivery.md).

O arquivo de output de um delivery de correspondência direta é gerado durante a análise de delivery. O conteúdo do arquivo depende das colunas de output selecionadas (consulte o [Arquivo de Extração](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>A fase de análise é detalhada em [Análise de delivery](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

Durante a fase de análise, o arquivo é gerado, mas as informações relativas aos recipients (ou seja, logs do delivery) não são atualizadas. Assim, você pode cancelar esse trabalho sem correr nenhum risco.

Verifique o resultado da análise e o conteúdo do arquivo de output antes de clicar em **[!UICONTROL Confirm delivery]**. Uma mensagem de confirmação permite iniciar o delivery.

A confirmação do envio inicia a extração dos dados no arquivo especificado.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

Então, é possível fechar o assistente e examinar os logs por meio da guia **[!UICONTROL Delivery]**, acessível pelos detalhes do delivery.

É possível configurar o modo de recuperação de logs na guia **[!UICONTROL Analysis]** das propriedades de delivery.

Há dois modos:

* **[!UICONTROL Messages are considered sent after validation]** (modo padrão): neste modo de função, todos os broadlogs são atualizados quando o operador confirma o envio (seu status passa de &#39;Entrega pendente&#39; para &#39;Enviado&#39;) e o delivery é automaticamente definido como **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : esse modo permite atualizar os logs via um arquivo externo enviado pelo provedor de serviço. Nesse caso, um workflow para processar essas informações precisa ser usado para atualizar o status broadlog.

   >[!NOTE]
   >
   >Nesse caso, o status do delivery também precisa ser alterada para **[!UICONTROL Finished]** pelo usuário assim que os broadlogs forem atualizados.
