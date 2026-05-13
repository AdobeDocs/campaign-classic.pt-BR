---
product: campaign
title: Gerenciamento de acesso
description: Saiba mais sobre as práticas recomendadas de gerenciamento de acesso
feature: Installation, Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
TQID: https://experienceleague.adobe.com/dbC74X04V5SFr7fWOl1b0-Br-x-jjHFNvMSX9Y6M-JQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 377
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

Não use o operador administrador (ou não o compartilhe). Crie um operador por usuário físico (para ter uma auditoria/registro preciso). Adicione seus administradores recém-nomeados ao grupo de administradores. Se você não usar o operador administrador, não o exclua e não o desabilite (esse operador é usado internamente para executar o processamento). Mas você pode proibir seu [acesso ao console do cliente](../../platform/using/access-management.md) e restringir sua zona de segurança (ao host local).

Evite adicionar muitos operadores no grupo de administradores (ou com direitos nomeados de administrador). Eles são operadores muito poderosos (podem executar todas as instruções SQL, executar comandos no servidor etc.).

A Adobe Campaign fornece três privilégios de alto nível através de [direitos nomeados](../../platform/using/access-management.md#named-rights):

* **ADMINISTRATION** (admin): dá acesso a tudo e permite fazer tudo, ignorando todas as verificações de direitos nomeados; portanto, inclui os direitos nomeados PROGRAM EXECUTION (createProcess) e SQL

* **PROGRAM EXECUTION** (createProcess): permite a execução de programas externos (no servidor)

* **SQL**: permite a execução de scripts SQL no banco de dados (para que ele possa ignorar o modelo de segurança). Observação: se você precisar executar cálculos complexos (filtragem, por exemplo), peça ao administrador do banco de dados para criar uma função SQL e adicioná-la ao incluo na lista de permissões. Saiba mais [nesta página](../../installation/using/scripting-coding-guidelines.md).

* **Concedê-las a poucos operadores (e confiáveis)**
