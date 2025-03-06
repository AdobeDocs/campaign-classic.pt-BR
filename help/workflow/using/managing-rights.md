---
product: campaign
title: Gerenciar permissões de fluxo de trabalho
description: Saiba como gerenciar permissões de fluxo de trabalho
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 100%

---

# Gerenciar permissões de fluxo de trabalho{#managing-rights}



Se não forem Administradores, os operadores do Adobe Campaign precisam de direitos de acesso para criar, executar ou modificar workflows.

Em geral, os operadores que atuam com workflows precisam acessar os arquivos que contêm os dados usados durante as várias atividades (destinatários, lista de destinatários, subscrições, entregas, etc.) e possivelmente seus arquivos secundários.

Eles também devem ser mapeados com os direitos nomeados que coincidam com as ações executadas pelos workflows que eles afetarão (importação do destinatário, acesso à arquivos, fusão, execução de script SQL, etc.).

Para obter mais informações sobre gerenciamento de operadores e permissões, consulte esta [seção](../../platform/using/access-management.md).

## Grupos de operadores {#operator-groups-wf}

Os seguintes grupos de operadores estão associados ao fluxo de trabalho:

* O grupo **[!UICONTROL Workflow execution]** permite controlar a execução e a aprovação de workflows para construção de target: o direito nomeado WORKFLOW é mapeado para os operadores deste grupo. É necessário para todas as ações em workflows, além de direitos de acesso aos arquivos de dados. Por padrão, o grupo **[!UICONTROL Workflow execution]** tem acesso somente leitura de arquivos padrão de workflows para construção de target e templates de workflow. Os operadores neste grupo também têm acesso de leitura e gravação para o arquivo de aprovação pendente.
* O grupo **[!UICONTROL Workflow supervisors]** permite que os operadores gerenciem aprovações de workflow.
* O grupo **[!UICONTROL Operation Managers]** permite acessar workflows da campanha.

## Direitos nomeados {#named-rights}

Somente o direito nomeado WORKFLOW é específico para workflows: permite criar, iniciar e parar workflows. Os direitos de leitura no arquivo de workflow são necessários para que o direito nomeado seja aplicável. Para workflows para construção do target, é necessário a leitura no arquivo **[!UICONTROL Profiles and Targets]**.

## Conta de execução de fluxo de trabalho {#workflow-execution-account}

Você pode configurar a conta de execução a ser usada no nível de template de workflow. A conta de execução permite mapear autorizações para o workflow diretamente, independentemente do operador do Adobe Campaign iniciando a execução. Por padrão, cada workflow é executado com os direitos do operador que o iniciou.

Para mapear uma conta de execução a um workflow, vá para a lista de templates de workflow e clique com o botão direito do mouse no template vinculado ao workflow. Escolha **[!UICONTROL Action > Change execution account...]** e depois selecione a conta que será usada.
