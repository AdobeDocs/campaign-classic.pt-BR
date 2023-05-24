---
product: campaign
title: Gerenciamento de acesso
description: Saiba mais sobre as práticas recomendadas de gerenciamento de acesso
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 38%

---

# Gerenciamento de acesso {#access-management}



## Operador Webapp

Pronto para uso, o operador webApp é um administrador. Para melhorar a segurança, siga estas diretrizes:

* Substitua o administrador nomeado diretamente deste operador por um novo (pode ser nomeado &#39;webapp&#39;). Para obter mais informações, consulte [esta página](../../platform/using/access-management.md).

* Adicione o operador webApp em pastas (principalmente pastas de destinatários) para conceder acesso a destinatários para ler/escrever. Para obter mais informações, consulte [esta página](../../platform/using/access-management.md).

* Se estiver usando uma instância multimarca (ou multi-geo), convém dividir o acesso a aplicativos web a diferentes pastas de destinatários: Para fazer isso:

   1. Duplicar o operador webApp

   1. Digite um nome para cada duplicação. Por exemplo: webapp_brand, webapp_brand2 etc.

   1. Duplique um template de aplicativo web para ter um template por marca e edite as propriedades para alterar o operador selecionando Use a specific account.  Saiba mais [nesta página](../../web/using/defining-web-forms-properties.md).

## Grupos de segurança e operadores administradores

Crie grupos de segurança suficientes para conceder direitos apenas suficientes aos seus operadores para que eles façam o que precisam, e não mais.

Não use o operador administrador (ou não o compartilhe). Crie um operador por usuário físico (para ter uma auditoria/registro preciso). Adicione seus administradores recém-nomeados ao grupo de administradores. Se você não usar o operador administrador, não o exclua e não o desabilite (esse operador é usado internamente para executar o processamento). Mas você pode banir seus [acesso ao console do cliente](../../platform/using/access-management.md) e restringir sua zona de segurança (ao host local).

Evite adicionar muitos operadores no grupo de administradores (ou com direitos nomeados de administrador). Eles são operadores muito poderosos (podem executar todas as instruções SQL, executar comandos no servidor etc.).

A Adobe Campaign oferece três privilégios de alto nível por meio de [direitos nomeados](../../platform/using/access-management.md#named-rights):

* **ADMINISTRAÇÃO** (admin): dá acesso a tudo e permite fazer tudo, ignorando todas as verificações de direitos nomeadas, portanto, inclui os direitos nomeados PROGRAM EXECUTION (createProcess) e SQL

* **EXECUÇÃO DO PROGRAMA** (createProcess): permite a execução de programas externos (no servidor)

* **SQL**: permite a execução de scripts SQL no banco de dados (para que ele possa ignorar o modelo de segurança). Lista de permissões Observação: se você precisar executar cálculos complexos (filtragem, por exemplo), peça ao administrador do banco de dados para criar uma função SQL e adicioná-la ao arquivo. Saiba mais [nesta página](../../installation/using/scripting-coding-guidelines.md).

* **Conceda-os a poucos operadores (e confiáveis)**
