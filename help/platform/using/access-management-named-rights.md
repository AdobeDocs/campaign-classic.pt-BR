---
product: campaign
title: Usar direitos nomeados para configurar permissões
description: Saiba como usar direitos nomeados para configurar permissões
badge: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 100%

---

# Usar direitos nomeados para configurar permissões{#named-rights}

>[!NOTE]
>
>Esta página se aplica somente a operadores conectados ao Campaign com autenticação nativa. Para a autenticação do Adobe IMS, consulte [esta documentação](https://helpx.adobe.com/br/enterprise/using/manage-permissions-and-roles.html).

Por padrão, o Adobe Campaign propõe um conjunto de direitos nomeados que permitem definir as autorizações atribuídas aos operadores e grupos de operadores. Esses direitos podem ser editados no nó **[!UICONTROL Administration > Access management > Named rights]** da árvore.

![](assets/s_ncs_admin_named_rights.png)

Esses direitos são os seguintes:

* **[!UICONTROL ADMINISTRATION]**: operadores com o direito **[!UICONTROL ADMINISTRATION]** têm acesso total na instância. Os usuários administradores podem executar/criar/editar/excluir qualquer objeto, como workflow, entrega, scripts etc.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: é possível definir várias etapas de aprovação em workflows e entregas para garantir que o estado atual tenha sido aprovado por um operador ou grupo atribuído. Os usuários com o direito **[!UICONTROL APPROVAL ADMINISTRATION]** podem definir etapas de aprovação e também atribuir um operador ou grupo de operadores que devem aprovar essas etapas.

* **[!UICONTROL CENTRAL]**: direito de gerenciamento central (marketing distribuído).

* **[!UICONTROL DELETE FOLDER]**: direito de excluir pastas. Com esse direito, os usuários podem excluir pastas da visualização do explorer.

* **[!UICONTROL EDIT FOLDERS]**: direito de alterar as propriedades da pasta, como nome interno, rótulo, imagem associada, pedido de subpastas etc.

* **[!UICONTROL EXPORT]**: os usuários podem exportar dados de suas instâncias do Adobe Campaign para um arquivo no servidor ou computador local usando a atividade de workflow **[!UICONTROL EXPORT]**.

* **[!UICONTROL FILES ACCESS]**: direito de ler e gravar o acesso de arquivos por meio de um script que pode ser gravado na atividade de workflow **[!UICONTROL JavaScript]** para arquivos de leitura/gravação em um servidor.

* **[!UICONTROL IMPORT]**: direito de importação de dados genéricos. **[!UICONTROL IMPORT]** permite importar dados para qualquer outra tabela, enquanto o direito **[!UICONTROL RECIPIENT IMPORT]** permite importar somente para a tabela do destinatário.

* **[!UICONTROL INSERT FOLDERS]**: direito de inserir pastas. Os usuários com o direito **[!UICONTROL INSERT FOLDERS]** podem criar novas pastas na árvore de pastas na visualização do explorer.

* **[!UICONTROL LOCAL]**: direito para gerenciamento local (marketing distribuído).

* **[!UICONTROL MERGE]**: direito de unir os registros selecionados em um. Se houver destinatários duplicados, o direito **[!UICONTROL MERGE]** permitirá que o usuário selecione os duplicados e os mescle em um destinatário primário.

* **[!UICONTROL PREPARE DELIVERIES]**: direito de criar, editar e salvar uma entrega. Os usuários com o direito **[!UICONTROL PREPARE DELIVERIES]** também podem iniciar o processo de análise da entrega.

* **[!UICONTROL PRIVACY DATA RIGHT]**: direito de coletar e excluir dados de privacidade. Para obter mais informações, consulte esta [página](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html).

* **[!UICONTROL PROGRAM EXECUTION]**: direito de executar comandos em várias linguagens de programação.

* **[!UICONTROL RECIPIENT IMPORT]**: direito de importar destinatários. Os usuários com o direito **[!UICONTROL RECIPIENT IMPORT]** podem importar um arquivo local para a tabela do destinatário.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Direito de executar qualquer comando SQL diretamente no banco de dados.

* **[!UICONTROL START DELIVERIES]**: Direito de aprovar entregas anteriormente analisadas. Após a análise, a entrega pausará em várias etapas de aprovação e precisará ser aprovada para retomar. Os usuários com o direito **[!UICONTROL START DELIVERIES]** podem aprovar entregas.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: direito de escrever seus próprios scripts SQL usando a atividade de gerenciamento de dados SQL, para criar e preencher tabelas de trabalho (consulte [esta seção](../../workflow/using/sql-data-management.md)).

* **[!UICONTROL WORKFLOW]**: direito de executar workflows. Sem esse direito, os usuários não podem iniciar, parar ou reiniciar workflows.

* **[!UICONTROL WEBAPP]**: direito de usar aplicações web.

>[!NOTE]
>
>Essa lista pode variar dependendo dos complementos instalados na plataforma.

## Acessar matriz de direitos {#access-rights-matrix}

Os grupos padrão e os direitos nomeados permitem que os operadores acessem determinadas pastas na hierarquia de navegação e concedam permissões de leitura, gravação e exclusão.

A matriz de direitos de acesso do Adobe Campaign está disponível [aqui](/help/platform/using/assets/access-rights-matrix.pdf).

[![imagem](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=pt-BR)
