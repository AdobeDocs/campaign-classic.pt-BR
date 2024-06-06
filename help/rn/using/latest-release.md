---
product: campaign
title: Versão mais recente
description: Notas de versão mais recentes do Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 8fec4d038eddaa3c5a2aade1b619f2543453d4de
workflow-type: ht
source-wordcount: '352'
ht-degree: 100%

---

# Versão mais recente{#latest-release}

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign v7**. Cada nova build vem com um status que é materializado por uma cor. Saiba mais sobre os status de build do Campaign Classic v7 [nesta página](rn-overview.md).

## Versão 7.3.5 - Build 9368 {#release-7-3-5}

[!BADGE Disponibilidade geral]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=pt-BR#rn-statuses" tooltip="Disponibilidade geral"}


_5 de dezembro de 2023_


### Aprimoramentos de segurança {#release-7-3-5-security}


* Com o Campaign Classic v7.3.5, o processo de autenticação foi aprimorado e protegido. Os operadores técnicos agora devem usar o Adobe Identity Management System (IMS) para se conectarem ao Campaign. Saiba como migrar as contas técnicas já existentes nesta [nota técnica](../../technotes/using/ims-migration.md).

* Além disso, como parte do esforço para aprimorar a segurança e o processo de autenticação, o Adobe Campaign recomenda migrar o modo de autenticação do usuário final da autenticação nativa de logon/senha para o Adobe Identity Management System (IMS). Saiba como migrar operadores [nesta nota técnica](../../technotes/using/migrate-users-to-ims.md).

* Agora, quando um formulário web tem o status **Publicação pendente**, ele não é publicado automaticamente. Para evitar problemas de segurança, é necessário publicá-lo antes de ele se tornar **Online** e ficar acessível por meio do URL do formulário web em um navegador da web. [Leia mais](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### Correções {#release-7-3-5-patches}

* Correção de um problema com o uso de dados de um banco de dados do Google Big Query ao atualizar dados em um banco de dados da Oracle: todas as chaves foram definidas como `0` na tabela temporária do workflow. (NEO-65091)
* Correção de um problema que causava a falha de execução de um workflow quando duas consultas em um banco de dados do Google Big Query eram combinadas em uma atividade de workflow de **União**. (NEO-63705)
* Correção de um problema que causava a solicitação de uma nova autenticação ao clicar no botão `Back` em um relatório do Campaign. (NEO-65087)
* Correção de um erro no workflow de Limpeza de banco de dados que acontecia quando uma entrega era excluída antes de suas provas de entrega. (NEO-48114)
* Correção de um problema de conexão com o Console do cliente: atualizações recentes na verificação TLS estavam causando um erro de conexão. (NEO-50488)
* Correção de um problema com a autenticação de Proxy HTTP depois da pós-atualização do Campaign para a versão 7.3.1. As solicitações HTTP em workflows do Campaign estavam falhando com `error 407 – proxy auth required is returned`. (NEO-49624)
* Correção de uma falha intermitente com descriptografia GPG nas atividades de workflow de **Script**. A mensagem de erro associada era: `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

