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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 89%

---


# Gerenciamento de direitos{#managing-rights}

Se não forem Administradores, os operadores do Adobe Campaign precisam de direitos de acesso para criar, executar ou modificar workflows.

Em geral, os operadores que atuam com workflows precisam acessar os arquivos que contêm os dados usados durante as várias atividades (recipients, lista de recipients, subscrições, deliveries, etc.) e possivelmente seus arquivos secundários.

Eles também devem ser mapeados com os direitos nomeados que coincidam com as ações executadas pelos workflows que eles afetarão (importação do recipient, acesso à arquivos, fusão, execução de script SQL, etc.).

Para obter mais informações sobre gerenciamento de operadores e permissões, consulte esta [seção](../../platform/using/access-management.md).

## Grupos de operadores {#operator-groups}

Os seguintes grupos de operadores estão associados ao workflow:

* O grupo **[!UICONTROL Workflow execution]** permite controlar a execução e a aprovação de workflows para construção de target: o direito nomeado WORKFLOW é mapeado para os operadores deste grupo. É necessário para todas as ações em workflows, além de direitos de acesso aos arquivos de dados. Por padrão, o grupo **[!UICONTROL Workflow execution]** tem acesso somente leitura de arquivos padrão de workflows para construção de target e templates de workflow. Os operadores neste grupo também têm acesso de leitura e gravação para o arquivo de aprovação pendente.
* The **[!UICONTROL Workflow supervisors]** group lets operators manage workflow approvals.
* The **[!UICONTROL Operation Managers]** group to access campaign workflows.

## Direitos nomeados {#named-rights}

Somente o direito nomeado WORKFLOW é específico para workflows: permite criar, iniciar e parar workflows. Os direitos de leitura no arquivo de workflow são necessários para que o direito nomeado seja aplicável. For targeting workflows, the reading right on the **[!UICONTROL Profiles and Targets]** file is necessary.

## Conta de execução de workflow {#workflow-execution-account}

Você pode configurar a conta de execução a ser usada no nível de template de workflow. A conta de execução permite mapear autorizações para o workflow diretamente, independentemente do operador do Adobe Campaign iniciando a execução. Por padrão, cada workflow é executado com os direitos do operador que o iniciou.

Para mapear uma conta de execução a um workflow, vá para a lista de templates de workflow e clique com o botão direito do mouse no template vinculado ao workflow. Choose **[!UICONTROL Action > Change execution account...]** then select the account to be used.
