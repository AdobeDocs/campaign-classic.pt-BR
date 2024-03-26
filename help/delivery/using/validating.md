---
product: campaign
title: Validação
description: Validação
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Direct Mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 100%

---

# Validação{#validating}



Os conceitos globais ao validar uma entrega são apresentados [nesta seção](steps-validating-the-delivery.md).

O arquivo de output de uma entrega de correspondência direta é gerado durante a análise de entrega. O conteúdo do arquivo depende das colunas de output selecionadas (consulte o [Arquivo de Extração](defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>A fase de análise é detalhada em [Análise de entrega](steps-validating-the-delivery.md#analyzing-the-delivery).

Durante a fase de análise, o arquivo é gerado, mas as informações relativas aos destinatários (ou seja, logs da entrega) não são atualizadas. Assim, você pode cancelar esse trabalho sem correr nenhum risco.

Verifique o resultado da análise e o conteúdo do arquivo de output antes de clicar em **[!UICONTROL Confirm delivery]**. Uma mensagem de confirmação permite iniciar a entrega.

A confirmação do envio inicia a extração dos dados no arquivo especificado.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

Então, é possível fechar o assistente e examinar os logs por meio da guia **[!UICONTROL Delivery]**, acessível pelos detalhes da entrega.

É possível configurar o modo de recuperação de logs na guia **[!UICONTROL Analysis]** das propriedades de entrega.

Há dois modos:

* **[!UICONTROL Messages are considered sent after validation]** (modo padrão): neste modo de função, todos os broadlogs são atualizados quando o operador confirma o envio (seu status passa de &#39;Entrega pendente&#39; para &#39;Enviado&#39;) e o delivery é automaticamente definido como **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : esse modo permite atualizar os logs via um arquivo externo enviado pelo provedor de serviço. Nesse caso, um workflow para processar essas informações precisa ser usado para atualizar o status broadlog.

  >[!NOTE]
  >
  >Nesse caso, o status da entrega também precisa ser alterada para **[!UICONTROL Finished]** pelo usuário assim que os broadlogs forem atualizados.
