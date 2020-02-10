---
title: Gerenciamento de direitos
seo-title: Gerenciamento de direitos
description: Gerenciamento de direitos
seo-description: null
page-status-flag: never-activated
uuid: 07039fec-c957-4548-acc7-22dc7827a54b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f78603e9-f6ff-4ebe-941b-b3fbd1924b71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Gerenciamento de direitos{#managing-rights}

Se não forem Administradores, os operadores do Adobe Campaign precisam de direitos de acesso para criar, executar ou modificar workflows.

Em geral, os operadores que atuam com workflows precisam acessar os arquivos que contêm os dados usados durante as várias atividades (recipients, lista de recipients, subscrições, deliveries, etc.) e possivelmente seus arquivos secundários.

Eles também devem ser mapeados com os direitos nomeados que coincidam com as ações executadas pelos workflows que eles afetarão (importação do recipient, acesso à arquivos, fusão, execução de script SQL, etc.).

Para obter mais informações sobre gerenciamento de operadores e permissões, consulte esta [seção](../../platform/using/access-management.md).

## Grupos de operadores {#operator-groups}

Os seguintes grupos de operadores estão associados ao workflow:

* The **[!UICONTROL Workflow execution]** group lets you control the execution and approval of targeting workflows: the WORKFLOW named right is mapped to this group&#39;s operators. É necessário para todas as ações em workflows, além de direitos de acesso aos arquivos de dados. By default, the **[!UICONTROL Workflow execution]** group has read-only access to standard targeting workflow files and workflow templates. Os operadores neste grupo também têm acesso de leitura e gravação para o arquivo de aprovação pendente.
* The **[!UICONTROL Workflow supervisors]** group lets operators manage workflow approvals.
* O **[!UICONTROL Operation Managers]** grupo para acessar os fluxos de trabalho da campanha.

## Direitos nomeados {#named-rights}

Somente o direito nomeado WORKFLOW é específico para workflows: permite criar, iniciar e parar workflows. Os direitos de leitura no arquivo de workflow são necessários para que o direito nomeado seja aplicável. For targeting workflows, the reading right on the **[!UICONTROL Profiles and Targets]** file is necessary.

## Conta de execução de workflow {#workflow-execution-account}

Você pode configurar a conta de execução a ser usada no nível de template de workflow. A conta de execução permite mapear autorizações para o workflow diretamente, independentemente do operador do Adobe Campaign iniciando a execução. Por padrão, cada workflow é executado com os direitos do operador que o iniciou.

Para mapear uma conta de execução a um workflow, vá para a lista de templates de workflow e clique com o botão direito do mouse no template vinculado ao workflow. Escolha **[!UICONTROL Action > Change execution account...]** e selecione a conta a ser usada.
