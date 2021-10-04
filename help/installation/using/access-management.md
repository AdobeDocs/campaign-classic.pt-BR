---
product: campaign
title: Gerenciamento de acesso
description: Saiba mais sobre as práticas recomendadas de gerenciamento de acesso.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 38%

---

# Gerenciamento de acesso {#access-management}

![](../../assets/v7-only.svg)

## Operador Webapp

Pronto para uso, o operador webApp é um administrador. Para melhorar a segurança, siga estas diretrizes:

* Substitua o administrador nomeado diretamente deste operador por um novo (pode ser nomeado &#39;webapp&#39;). Para obter mais informações, consulte [esta página](../../platform/using/access-management.md).

* Adicione o operador webApp em pastas (principalmente pastas de destinatários) para conceder acesso a destinatários para ler/escrever. Para obter mais informações, consulte [esta página](../../platform/using/access-management.md).

* Se estiver usando uma instância multimarca (ou multi-geo), convém dividir o acesso a aplicativos web a diferentes pastas de destinatários: Para fazer isso:

   1. Duplicar o operador webApp

   1. Digite um nome para cada duplicação. Por exemplo: webapp_brand, webapp_brand2 etc.

   1. Duplique um template de aplicativo da web para ter um template por marca e edite as propriedades para alterar o operador selecionando Usar uma conta específica.  Saiba mais [nesta página](../../web/using/defining-web-forms-properties.md).

## Grupos de segurança e operadores administrativos

Crie grupos de segurança suficientes para fornecer direitos suficientes aos seus operadores para permitir que eles façam o que precisam, e não mais.

Não use o operador administrador (ou não o compartilhe). Crie um operador por usuário físico (para ter uma auditoria/registro preciso). Adicione seus administradores recém-nomeados ao grupo de administradores. Se você não usar o operador administrador, não o exclua e não o desabilite (esse operador é usado internamente para executar o processamento). Mas você pode proibir seu [acesso ao console do cliente](../../platform/using/access-management.md) e restringir sua zona de segurança (para localhost).

Evite adicionar muitos operadores no grupo de administradores (ou com direitos nomeados de administrador). Eles são operadores muito potentes (podem executar todas as instruções SQL, executar comandos no servidor etc.).

O Adobe Campaign fornece três privilégios de alto nível por meio de [direitos nomeados](../../platform/using/access-management.md#named-rights):

* **ADMINISTRATION**  (admin): dá acesso a tudo e permite fazer tudo, ignorando todas as verificações corretas nomeadas, portanto inclui a EXECUÇÃO DO PROGRAMA (createProcess) e os direitos nomeados SQL

* **EXECUÇÃO**  DO PROGRAMA (createProcess): permite executar programas externos (no servidor)

* **SQL**: permite executar scripts SQL no banco de dados (para que possa ignorar o modelo de segurança). Observação: se você precisar executar cálculos complexos (filtragem, por exemplo), poderá solicitar ao administrador do banco de dados que crie uma função SQL e adicione-a à  de lista de permissões. Saiba mais [nesta página](../../installation/using/scripting-coding-guidelines.md).

* **Conceda-os a muito poucos (e confiáveis) operadores**
