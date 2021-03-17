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
ht-degree: 99%

---


# Versão mais recente{#latest-release}

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign Classic Release Candidate**.

Para obter a versão do Campaign Classic Gold Standard (build de GA mais recente), [consulte esta página](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Versão 21.1.1 - Compilação 9277 {#release-21-1-1-build-9277}

_22 de fevereiro de 2021_

**Aprimoramentos de segurança**

* O mecanismo de autenticação do console foi aprimorado para otimizar a segurança. (NEO-26944)
* Correção de um problema de segurança para reforçar a proteção contra problemas de SSRF (Server Side Request Forgery). (NEO-28532)

**Atualizações de compatibilidade**

Os seguintes sistemas agora são compatíveis com o Campaign:

* A API do Salesforce versão 49 agora é compatível com a utilização da conta externa do Salesforce CRM.

**Recursos obsoletos**

O relatório de **monitoramento técnico da avaliação do delivery** agora está obsoleto.

Saiba mais na [página sobre recursos obsoletos e removidos](../../rn/using/deprecated-features.md).

**Aprimoramentos**

**O EFS (Email Feedback Service, Serviço de feedback por email)** é um serviço escalável que captura diretamente o feedback do MTA aprimorado, melhorando assim a precisão dos relatórios. Esse recurso está sendo lançado como um beta privado e estará progressivamente disponível para todos os clientes em versões futuras.

* Agora todas as categorias de feedback são capturadas, para oferecer relatórios completos e precisos.
* O cálculo do indicador Entregue agora se baseia no feedback em tempo real do MTA aprimorado para melhorar a precisão e a reatividade.
* O EFS soluciona o problema de atrasos de relatórios síncronos de rejeições temporárias.

Para obter mais informações consulte a [documentação detalhada](../../delivery/using/sending-with-enhanced-mta.md#efs).
Se você estiver interessado em participar deste beta privado, preencha este [formulário](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) e nós entraremos em contato com você.

**Outras alterações**

* A velocidade de transferência foi aprimorada para grandes logs de rastreamento usando compactação.
* O mapa de calor do fluxo de trabalho foi aprimorado para evitar tempos limite ao executar workflows com várias atividades. (NEO-27423).
* Correção de um problema que permitia que uma oferta fosse apresentada mesmo se sua data final fosse no passado. Agora, o Campaign Classic considera o carimbo de data e hora completo, em vez de somente a data. (NEO-27590)
* O link do Google+ foi removido do bloco de personalização **links de compartilhamento de rede social**.
* Correção de um problema após a implementação de uma correção de erro na última versão. Uma verificação foi adicionada ao nome do host ao conectar usando SSL/TLS, o que resultava em falha de delivery de SMS. A verificação do nome do host foi desativada para a maioria dos protocolos, como POP3, SMS e HTTP com proxy, e a verificação do certificado para a conta externa SMS foi aprimorada com três valores (NEO-29581). [Saiba mais](../../delivery/using/sms-protocol.md#skip-tls)

**Correções**

* Correção de um problema que impedia que os atalhos do teclado Tab, Enter e Escape funcionassem na nova tela de logon.
* Correção de um problema de atualização que fazia com que o nome de um fluxo de trabalho recém-criado fosse substituído pelo valor padrão após o salvamento (NEO-26106).
* Correção de um problema que ocorria ao executar workflows em que um novo campo era adicionado como parte de uma atividade **Enriquecimento** antes de uma atividade **Delivery** usando um target mapping de **Arquivo externo**: campos indesejados eram adicionados ao target mapping do **Arquivo externo**. (NEO-27687)
* Correção de um problema que fazia com que alguns caracteres no código fonte fossem alterados ao ser reaberta uma aplicação web criada e salva anteriormente. (NEO-27597)
* Correção de um problema que ocorria ao atualizar para uma compilação, incluindo o novo mecanismo de assinatura para links de rastreamento (da Compilação 19.1.4 e Campaign 20.2): quando vários modelos eram associados a um evento, a atualização podia fazer com que o modelo errado fosse selecionado ao ser enviada a mensagem transacional. (NEO-28326)
* Correção de um problema que fazia com que o MTA ficasse sem resposta e não conseguisse processar deliveries, a menos que fosse reiniciado. (NEO-27455)
* Correção de um problema no banco de dados MSSQL relacionado ao gerenciamento de data e hora durante operações de carregamento em massa para uma coluna de tipo de data e hora.
* Correção de um problema de query de fluxo de trabalho ao usar funções Redshift xtk. Os SubDays, SubSeconds, SubMinutes e SubHours agora aceitam os tipos de data e hora do Redshift (NEO-24962).
* Correção de um problema que exibia uma mensagem de erro de script ao tentar a pré-visualização de um relatório com acesso Anônimo. (NEO-27081)
* Correção de um problema que podia reduzir o uso de memória no servidor durante a execução da análise do delivery.
* Correção de um problema que impedia que a instância funcionasse durante a tentativa de executar consultas complexas específicas.
* Correção de um problema que impedia a execução do fluxo de trabalho técnico **Sincronizar páginas do Twitter**. (NEO-28634)
* Correção de um problema que podia exibir uma mensagem de erro relacionada à função decryptPassword durante a tentativa de publicar no Twitter usando o template do delivery **Tweet (twitter)**. (NEO-28216)
* Correção de um problema que ocorria ao usar uma atividade **JavaScript** para fazer uma solicitação HTTP em um fluxo de trabalho. Após a definição do número da porta no nome do Host, a chamada falhará com o seguinte erro (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Correção de um problema que impedia o envio de novos deliveries com personalização de dados de target.
* Correção de um problema em que várias falhas ocorriam na instância de marketing que causava os arquivos principais.
* Correção de um problema que resultava em falha do fluxo de trabalho **Rastreamento** com o seguinte erro (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Correção de um problema que ocorria ao criar e salvar um delivery na guia **Direcionamento &amp; Fluxo de trabalho** de uma campanha: a pré-visualização falhava com o seguinte erro (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Correção de um erro que ocorria ao configurar uma conta externa entre uma instância de marketing e uma instância do Adobe Campaign Standard ou uma instância do Campaign Classic mid-sourcing e usar a opção &quot;DisableFOH2=1&quot;. Ao ser usada a opção &quot;DisableFOH2=1&quot; na conta externa, as conexões não eram fechadas corretamente e se acumulavam, resultando no seguinte erro (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Correção de um erro no SMS quando ocorriam problemas de conexão entre o servidor e o provedor. A conexão era então automaticamente desativada pelo filho do MTA. O Adobe Campaign Classic não tentava se conectar a essa conexão com falha, desde que um novo filho não tivesse sido iniciado.
