---
solution: Campaign Classic
product: campaign
title: Versão mais recente
description: Versão mais recente do Campaign Classic Observações
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 14513d5ecbfdd5637b764c8f19bc01358e63c130
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 18%

---


# Versão mais recente{#latest-release}

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign Classic Release Candidate**.

Para obter a versão do Campaign Classic Gold Standard (build de GA mais recente), [consulte esta página](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Versão 21.1.1 - Build 9277 {#release-21-1-1-build-9277}

_22 de fevereiro de 2021_

**Aprimoramentos de segurança**

* O mecanismo de autenticação do console foi aprimorado para otimizar a segurança. (NEO-26944)



* Correção de um problema de segurança para reforçar a proteção contra situações de SSRF (Server Side Request Forgery). (NEO-28532)




**Atualizações de compatibilidade**

Os seguintes sistemas agora são compatíveis com o Campaign:

* A API Salesforce versão 49 agora é compatível ao usar a conta externa do Salesforce CRM.

**Recursos obsoletos**

O relatório **Technical Deliverability Monitoring** agora está obsoleto.

Saiba mais na [página sobre recursos obsoletos e removidos](../../rn/using/deprecated-features.md).

**Aprimoramentos**

**O Serviço de feedback de email (EFS)** é um serviço escalável que captura o feedback diretamente do MTA aprimorado, melhorando assim a precisão dos relatórios. Esse recurso está sendo lançado como um beta privado e estará progressivamente disponível para todos os clientes em versões futuras.

* Agora todas as categorias de feedback são capturadas, para oferecer relatórios completos e precisos.
* O cálculo do indicador Entregue agora se baseia no feedback em tempo real do MTA aprimorado para melhorar a precisão e a reatividade.
* O EFS soluciona o problema de atrasos de relatórios síncronos de devoluções temporárias.

Para obter mais informações consulte a [documentação detalhada](../../delivery/using/sending-with-enhanced-mta.md#efs).
Se você estiver interessado em participar deste beta privado, preencha este [formulário](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) e nós voltaremos a você.

**Outras alterações**

* A velocidade de transferência foi aprimorada para grandes logs de rastreamento usando compactação.
* O Workflow Heatmap foi aprimorado para evitar tempos limite durante a execução de workflows com várias atividades. (NEO-27423).
* Correção de um problema que poderia permitir a apresentação de uma oferta mesmo se sua data final fosse passada. O Campaign Classic agora considera todo o carimbo de data e hora da data final, em vez da data somente. (NEO-27590)



* O link do Google+ foi removido do bloco de personalização **Social network sharing links**.
* Correção de um problema após a implementação de uma correção de erro na última versão. Uma verificação foi adicionada ao nome do host ao se conectar usando SSL/TLS, o que resultou em falha dos deliveries de SMS. A verificação do nome de host foi desativada para a maioria dos protocolos, como POP3, SMS e HTTP com proxy e a verificação de certificado para a conta externa de SMS foi aprimorada com três valores (NEO29581). [Saiba mais](../../delivery/using/sms-protocol.md#skip-tls)

**Correções**

* Correção de um problema que impedia que os atalhos de teclado Tab, Enter e Escape funcionassem na nova tela de logon.
* Correção de um problema de atualização que fazia com que o nome de um workflow recém-criado fosse substituído pelo valor padrão após salvar (NEO26106).
* Correção de um problema que ocorria ao executar workflows em que um novo campo era adicionado como parte de uma atividade **Enrichment** antes de uma atividade **Delivery** usando um target mapping **External file**: campos indesejados foram adicionados ao target mapping **External file**. (NEO-27687)



* Correção de um problema que fazia com que alguns caracteres no código-fonte fossem alterados ao reabrir um aplicativo da Web criado e salvo anteriormente. (NEO-27597)



* Correção de um problema que poderia ocorrer ao atualizar para uma build, incluindo o novo mecanismo de assinatura para links de rastreamento (da Build 19.1.4 e Campaign 20.2): quando vários modelos eram associados a um evento, a atualização poderia fazer com que o modelo errado fosse selecionado ao enviar a mensagem transacional. (NEO-28326)



* Correção de um problema que fazia com que o MTA não respondesse e não processasse deliveries, a menos que fosse reiniciado. (NEO-27455)



* Correção de um problema no banco de dados MSSQL relacionado ao gerenciamento de carimbo de data e hora durante operações de carregamento em massa de uma coluna do tipo datetime.
* Correção de um problema de consulta de workflow ao usar funções Redshift xtk. Os SubDays, SubSeconds, SubMinutes e SubHours agora aceitam ambos os tipos de carimbo de data e hora Redshift (NEO24962).
* Correção de um problema que exibia uma mensagem de erro de script ao tentar visualizar um relatório com acesso Anônimo. (NEO-27081)



* Correção de um problema que poderia reduzir o uso de memória no servidor ao executar análise de delivery.
* Correção de um problema que impedia o funcionamento da instância ao tentar executar consultas complexas específicas.
* Correção de um problema que poderia impedir a execução do workflow técnico **Sincronizar páginas do Twitter** . (NEO-28634)



* Correção de um problema que poderia exibir uma mensagem de erro relacionada à função decryptPassword ao tentar publicar no Twitter usando o template de delivery **Tweet (twitter)** . (NEO-28216)



* Correção de um problema que ocorria ao usar uma atividade **Javascript** para fazer uma solicitação HTTP em um workflow. Após definir o número da porta no nome do Host, a chamada falharia com o seguinte erro (NEO29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Correção de um problema que impedia o envio de novos deliveries com a personalização dos dados de target.
* Correção de um problema em que várias falhas ocorriam na instância de marketing causando arquivos principais.
* Correção de um problema que resultava em falha do workflow **Tracking** com o seguinte erro (NEO25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Correção de um problema que ocorria ao criar e salvar um delivery dentro da guia **Targeting &amp; Workflow** de uma campanha: a visualização falharia com o seguinte erro (NEO29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Correção de um erro que ocorria ao configurar uma conta externa entre uma instância de marketing e uma instância do Adobe Campaign Standard ou uma instância de mid-sourcing do Campaign Classic e usar a opção &quot;DisableFOH2=1&quot;. Ao usar a opção &quot;DisableFOH2=1&quot; na conta externa, as conexões não eram fechadas corretamente e se acumulavam, resultando no seguinte erro (NEO26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Correção de um erro com SMS quando problemas de conexão ocorriam entre o servidor e o provedor. A conexão seria então desativada automaticamente pelo MTA filho. O Adobe Campaign Classic não tentaria se conectar a essa conexão com falha, desde que um novo filho não tivesse sido iniciado.
