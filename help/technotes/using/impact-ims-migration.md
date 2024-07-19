---
title: Atualização da interface do Campaign após a migração IMS
description: Saiba como ativar os impactos da interface de migração do Adobe Identity Management System
exl-id: 8b13fe4d-d8d3-43b3-bbe4-c8c5574f585a
source-git-commit: 8eadea9f9cc0a44522726024bfbc825e3b4cad98
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 1%

---

# Atualização da interface do Campaign após a migração IMS {#impact-ims-migration}

Depois de [migrar os operadores técnicos do Campaign para o Developer Console](ims-migration.md) e [fazer a transição para o IMS para autenticação do usuário final](migrate-users-to-ims.md), a última etapa é habilitar a interface do usuário e as restrições de API para remover opções e recursos específicos da autenticação nativa. Esta atualização está disponível a partir do Campaign v7.4.1.

## Habilitar restrições de IMS {#ims-restrictions}

Para finalizar a migração para o Adobe Identify Management System (IMS), você deve bloquear a criação de novos usuários nativos, o logon de usuários nativos e o acesso à API para operadores nativos. Seu ambiente é então protegido e padronizado.

Como um Cloud Service gerenciado/usuário hospedado, entre em contato com a Adobe para ativar essa restrição e as atualizações associadas na interface do usuário do produto.

Como usuário no local/híbrido, siga estas etapas:

1. Navegue até a seção `<imsConfig>` do arquivo de configuração da instância.
1. Para habilitar as restrições de interface do usuário, atualize a opção `nonIMSOperatorMgmtInClientConsoleRestricted`, dentro do elemento `nonIMSOperatorMgmtInClientConsole`, para `true`, conforme abaixo:


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. Para habilitar as restrições de API, atualize a opção `disableAPI`, dentro do elemento `nonIMSAuthnAPI`, para `true`, conforme abaixo:

   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSAuthnAPI disableAPI="true">
               ...
           </nonIMSAuthnAPI>
       </imsConfig>
   </shared>
   </serverConf>
   ```

Observe que alguns operadores têm permissão para se conectar ao Adobe Campaign com uma autenticação nativa. Esses operadores técnicos são ativados por padrão e não devem ser modificados. Para permitir essa exceção, esses operadores técnicos são adicionados à lista de permissões por padrão. Você pode encontrar essa lista na seção `<imsConfig>` do arquivo de configuração da instância, na opção `allowOperator`, dentro do elemento `nonIMSAuthnAPI`.

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

Incluir na lista de permissões Se você precisar adicionar um operador ao arquivo, adicione um novo elemento `allowOperator` com o nome do operador. Por exemplo, se você deseja adicionar um novo operador com o nome `test`, atualize esta seção da seguinte maneira:

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
            <allowOperator name="test"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

## Impactos na interface do usuário {#ims-impacts}

Depois que a migração for concluída e as restrições forem aplicadas conforme descrito abaixo, as alterações a seguir serão aplicadas ao produto e à interface do usuário.

### Gerenciamento de operador {#manage-admin}

Não é mais possível criar, editar, atualizar ou excluir operadores com autenticação nativa no console do cliente.

Como consequência, essas ações foram desativadas no console do cliente.

A administração dos operadores é centralizada no Adobe Admin Console e as seguintes tarefas agora são gerenciadas exclusivamente por meio desse console. Saiba como criar usuários e atribuir permissões na [documentação do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

### Opções indisponíveis {#unavailable-migration}

Após a migração, as seguintes tarefas não estarão mais disponíveis no console do cliente:

* Use a [opção Mesclar linhas selecionadas](../../platform/using/updating-data.md#merge-data) para mesclar operadores.

* Atualize os seguintes campos para seus operadores:
   * Nome
   * Senha
   * Rótulo
   * Email

* [Redefinir a senha do Campaign](../../production/using/lost-password.md)

* Editar a fonte XML dos operadores

* Operadores duplicados.


>[!MORELIKETHIS]
>
>* [Migração de usuários finais para o IMS](migrate-users-to-ims.md)
>* [Migração de operadores técnicos para o console do Adobe Developer](ims-migration.md)
>* [notas de versão mais recentes do Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [O que é o Sistema Adobe Identity Management (IMS)](https://helpx.adobe.com/br/enterprise/using/identity.html){target="_blank"}
