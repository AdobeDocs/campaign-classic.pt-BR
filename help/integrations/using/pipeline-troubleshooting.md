---
product: campaign
title: Configuração da integração
description: Configuração da integração
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 9a126d16b394333163b974ad9690f7c93fb3034a
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 92%

---

# Solução de problemas de pipeline {#pipeline-troubleshooting}

**Falha no pipeline com o erro “Nenhuma atividade corresponde à máscara pipelined@&lt; instance >”**

A sua versão do Adobe Campaign Classic não é compatível com o pipeline.

1. Verifique se o elemento [!DNL pipelined] está presente no arquivo de configuração. Caso não esteja, significa que não é compatível.
1. Atualize para o Campaign 20.3 ou [!DNL Gold Standard] 11.

**Falha no pipeline com “ aurait dû commencer par `[` ou `{` (iRc=16384)”**

A opção **NmsPipeline_Config** não está definida. Na verdade é um erro de análise JSON.
Defina a configuração JSON na opção **NmsPipeline_Config**. Consulte &quot;Opção de roteamento&quot; nesta página.

**Falha no pipeline com &quot;o assunto deve ser uma organização ou cliente válido&quot;**

A configuração do identificador da organização não é válida.

1. Verifique se IMSOrgId está definido no serverConf.xml.
1. Procure um IMSOrgId vazio no arquivo de configuração da instância que possa substituir o padrão. Em caso afirmativo, remova-o.
1. Verifique se o IMSOrgId corresponde ao do cliente na Experience Cloud.

**Falha no pipeline com &quot;chave inválida&quot;**

O parâmetro @authPrivateKey do arquivo de configuração da instância está incorreto.

1. Verifique se a authPrivateKey está definida.
1. Verifique se a authPrivateKey: inicia com @, termina com = e tem cerca de 4000 caracteres.
1. Procure a chave original e verifique se ela tem: formato RSA, 4096 bits de comprimento e inicia com `-----BEGIN RSA PRIVATE KEY-----`.
   <br> Se necessário, recrie a chave e registre-a no Adobe Analytics.
1. Verifique se a chave foi codificada na mesma instância como [!DNL pipelined]. <br>Se necessário, refaça a codificação usando a amostra de JavaScript ou workflow.

**Falha no pipeline com &quot;não é possível ler o token durante a autenticação&quot;**

A chave privada tem um formato inválido.

1. Execute as etapas para criptografia de chave nesta página.
1. Verifique se a chave está criptografada na mesma instância.
1. Verifique se authPrivateKey no arquivo de configuração corresponde à chave gerada. <br>Use o OpenSSL para gerar o par de chaves. O PuttyGen, por exemplo, não gera o formato correto.

**Falha no pipeline com &quot;não é mais permitido obter o token de acesso&quot;**

Os logs devem ser os seguintes:

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

Esta mensagem de erro significa que a autenticação é configurada usando o OAuth base herdado do Omniture. Consulte a documentação [Configuração do Adobe I/O para Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) para atualizar sua autenticação.

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

**Atualização de instâncias de estágio da autenticação herdada à autenticação do Adobe IO**

Alterar a autenticação da integração na instância do estágio não afetará a configuração da instância de produção. Você pode optar por atualizar a instância do estágio, atualizar a autenticação para o Adobe IO e testar os acionadores na instância do estágio.

A instância de produção continuará a usar a autenticação herdada e não será afetada por essa alteração.
