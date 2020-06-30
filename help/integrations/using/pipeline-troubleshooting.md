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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 2%

---


# Solução de problemas de pipeline {#pipeline-troubleshooting}

**Falha no pipeline com o erro &quot;Nenhuma tarefa corresponde à máscara pipeline@&quot;**

A sua versão do Adobe Campaign Classic não suporta o pipeline.

1. Verifique se o elemento pipelined está presente no arquivo de configuração. Se não, significa que não é suportado.
1. Atualize para a versão 6.11 build 8705 ou posterior.

**Falha no pipeline com &#39;&#39; aurait dex comisscer par &#39;[&#39; ou &#39;{&#39; (iRc=16384)&quot;**

A opção **NmsPipeline_Config** não está definida. Na verdade é um erro de análise JSON.
Defina a configuração JSON na opção **NmsPipeline_Config**. Consulte &quot;Opção de roteamento&quot; nesta página.

**Falha no pipeline com &quot;o assunto deve ser uma organização ou cliente válido&quot;**

A configuração IMSOrgid não é válida.

1. Verifique se IMSOrgId está definido no serverConf.xml.
1. Procure um IMSOrgId vazio no arquivo de configuração da instância que possa substituir o padrão. Em caso afirmativo, remova-o.
1. Verifique se o IMSOrgId corresponde ao do cliente no Experience Cloud.

**Falha no pipeline com &quot;chave inválida&quot;**

O parâmetro @authPrivateKey do arquivo de configuração da instância está incorreto.

1. Verifique se authPrivateKey está definida.
1. Verifique se authPrivateKey: start com @, termina com = e tem cerca de 4000 caracteres.
1. Procure a chave original e verifique se ela é: no formato RSA, 4096 bits de comprimento e start com —BEGIN RSA PRIVATE KEY—.
   <br> Se necessário, recrie a chave e registre-a no Adobe Analytics. Consulte esta [seção](../../integrations/using/configuring-pipeline.md#oauth-client-creation).
1. Verifique se a chave foi codificada dentro da mesma instância que foi implantada. <br>Se necessário, refaça a codificação usando a amostra de JavaScript ou fluxo de trabalho.

**Falha no pipeline com &quot;não é possível ler o token durante a autenticação&quot;**

A chave privada tem um formato inválido.

1. Execute as etapas para criptografia de chave nesta página.
1. Verifique se a chave está criptografada na mesma instância.
1. Verifique se authPrivateKey no arquivo de configuração corresponde à chave gerada. <br>Certifique-se de usar o OpenSSL para gerar o par de chaves. Por exemplo, PuttyGen não gera o formato correto.

**Nenhum acionador é recuperado**

Quando o processo implantado está em execução e nenhum acionador é recuperado:

1. Verifique se o acionador está ativo no Analytics e está gerando eventos.
1. Verifique se o processo implantado está em execução.
1. Procure erros no log implantado.
1. Procure erros na página de status canalizada. disparador descartado, as falhas de disparo devem ser zero.
1. Verifique se o nome do acionador está configurado na **[!UICONTROL NmsPipeline_Config]** opção. Em caso de dúvida, use a opção curinga.
1. Verifique se a Analytics tem um acionador ativo e está gerando eventos. Pode haver um atraso de algumas horas após a configuração ser feita no Analytics antes de ela estar ativa.

**Eventos não estão vinculados a um cliente**

Quando alguns eventos não estão vinculados a um cliente:

1. Verifique se o fluxo de trabalho de reconciliação está em execução, se aplicável.
1. Verifique se o evento contém uma ID do cliente.
1. Faça um query na tabela do cliente usando a ID do cliente.
1. Verifique a frequência de importação do cliente. Novos clientes são importados para o Adobe Campaign com um fluxo de trabalho.

**Latência no processamento de eventos**

Quando o carimbo de data e hora do Analytics for muito mais antigo do que a data de criação do evento na Campanha.

Geralmente, um acionador pode levar de 15 a 90 minutos para iniciar uma campanha de marketing. Isso varia dependendo da implementação da coleta de dados, do carregamento no pipeline, da configuração personalizada do acionador definido e do fluxo de trabalho no Adobe Campaign.

1. Verifique se o processo implantado está em execução.
1. Procure erros em pipelined.log que possam causar tentativas. Corrija os erros, se aplicável.
1. Verifique o tamanho da fila na página de status do pipeline. Se o tamanho da fila for grande, melhore o desempenho do JS.
1. Como um atraso parece aumentar com o volume, configure os acionadores no Analytics usando menos mensagens.
Anexos

**Como usar a criptografia de chave JavaScript**

Execute um JavaScript para criptografar a chave privada. É necessário para a configuração do pipeline.

Esta é uma amostra de código que você pode usar para executar a função cryptString:

```
/*
USAGE:
  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
*/
 
function usage()
{
  return "USAGE:\n" +
    '  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js\n'
}
 
var fn = application.arg;
if( fn == "" )
  logError("Missing key file file\n" + usage());
 
//open the pem file
plaintext = loadFile(fn)
 
if( !plaintext.match(/^-----BEGIN RSA PRIVATE KEY-----/) )
  logError("File should be an rsa private key")
 
logInfo("Encrypted key:\n" + cryptString(plaintext, <xtkSecretKey>))
```

No servidor, execute o Javascript:

```
nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
```

Copie e cole a chave codificada da saída para o console.