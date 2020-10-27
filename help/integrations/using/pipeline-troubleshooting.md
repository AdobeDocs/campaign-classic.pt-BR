---
title: Configuração da integração
seo-title: Configuração da integração
description: Configuração da integração
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 3e73d7c91fbe7cff7e1e31bdd788acece5806e61
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 97%

---


# Solução de problemas de pipeline {#pipeline-troubleshooting}

**Falha no pipeline com o erro &quot;Nenhuma tarefa corresponde à máscara pipeline@&lt; instância >&quot;**

A sua versão do Adobe Campaign Classic não é compatível com o pipeline.

1. Verifique se o elemento [!DNL pipelined] está presente no arquivo de configuração. Caso não esteja, significa que não é compatível.
1. Atualize para a versão 6.11 build 8705 ou posterior.

**Falha no pipeline com “ aurait dû commencer par `[` ou `{` (iRc=16384)”**

A opção **NmsPipeline_Config** não está definida. Na verdade é um erro de análise JSON.
Defina a configuração JSON na opção **NmsPipeline_Config**. Consulte &quot;Opção de roteamento&quot; nesta página.

**Falha no pipeline com &quot;o assunto deve ser uma organização ou cliente válido&quot;**

A configuração IMSOrgid não é válida.

1. Verifique se IMSOrgId está definido no serverConf.xml.
1. Procure um IMSOrgId vazio no arquivo de configuração da instância que possa substituir o padrão. Em caso afirmativo, remova-o.
1. Verifique se o IMSOrgId corresponde ao do cliente na Experience Cloud.

**Falha no pipeline com &quot;chave inválida&quot;**

O parâmetro @authPrivateKey do arquivo de configuração da instância está incorreto.

1. Verifique se a authPrivateKey está definida.
1. Verifique se a authPrivateKey: inicia com @, termina com = e tem cerca de 4000 caracteres.
1. Procure a chave original e verifique se ela tem: formato RSA, 4096 bits de comprimento e inicia com -----BEGIN RSA PRIVATE KEY-----.
   <br> Se necessário, recrie a chave e registre-a no Adobe Analytics.
1. Verifique se a chave foi codificada na mesma instância como [!DNL pipelined]. <br>Se necessário, refaça a codificação usando a amostra de JavaScript ou workflow.

**Falha no pipeline com &quot;não é possível ler o token durante a autenticação&quot;**

A chave privada tem um formato inválido.

1. Execute as etapas para criptografia de chave nesta página.
1. Verifique se a chave está criptografada na mesma instância.
1. Verifique se authPrivateKey no arquivo de configuração corresponde à chave gerada. <br>Use o OpenSSL para gerar o par de chaves. O PuttyGen, por exemplo, não gera o formato correto.

**Nenhum acionador foi recuperado**

Quando o processo [!DNL pipelined] estiver em execução e nenhum acionador for recuperado:

1. Verifique se o acionador está ativo no Analytics e está gerando eventos.
1. Verifique se o processo [!DNL pipelined] está em execução.
1. Procure erros no log de [!DNL pipelined].
1. Procure erros na página de status [!DNL pipelined]. acionadores descartados e falhas do acionador devem ser zero.
1. Verifique se o nome do acionador está configurado na opção **[!UICONTROL NmsPipeline_Config]**. Em caso de dúvida, use a opção curinga.
1. Verifique se o Analytics tem um acionador ativo e está gerando eventos. Pode haver um atraso de algumas horas até que a configuração feita no Analytics seja ativada.

**Eventos não estão vinculados a um cliente**

Quando alguns eventos não estão vinculados a um cliente:

1. Caso seja aplicável, verifique se o workflow de reconciliação está em execução.
1. Verifique se o evento contém uma ID do cliente.
1. Faça um query na tabela do cliente usando a ID do cliente.
1. Verifique a frequência de importação do cliente. Novos clientes são importados para o Adobe Campaign com um workflow.

**Latência no processamento de eventos**

Quando o carimbo de data e hora do Analytics for muito mais antigo do que a data de criação do evento no Campaign.

Geralmente, um acionador pode levar de 15 a 90 minutos para iniciar uma campanha de marketing. O tempo varia conforme a implementação da coleta de dados, o carregamento no pipeline, a configuração personalizada do acionador definido e o workflow no Adobe Campaign.

1. Verifique se o processo [!DNL pipelined] está em execução.
1. Em pipelined.log, procure erros que possam causar novas tentativas. Caso seja aplicável, corrija os erros.
1. Verifique o tamanho da fila na página de status [!DNL pipelined]. Se o tamanho da fila for grande, melhore o desempenho do JS.
1. Como o atraso parece aumentar com o volume, configure os acionadores no Analytics usando menos mensagens.
Anexos
