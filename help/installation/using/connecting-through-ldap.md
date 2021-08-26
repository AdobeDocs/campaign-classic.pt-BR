---
product: campaign
title: Conexão por meio do LDAP
description: 'Saiba como usar o LDAP para fazer logon no Campaign '
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 1%

---

# Conexão por meio do LDAP{#connecting-through-ldap}

![](../../assets/v7-only.svg)

## Configuração do Campaign e LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>A configuração LDAP só é possível para instalações locais ou híbridas.

A configuração LDAP é realizada no assistente de implantação. A opção **[!UICONTROL LDAP integration]** deve ser selecionada durante a primeira etapa de configuração. Consulte [Assistente de implantação](../../installation/using/deploying-an-instance.md#deployment-wizard).

A janela permite configurar a identificação de usuários do Adobe Campaign por meio do diretório LDAP especificado.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Especifique o endereço do servidor LDAP no campo **[!UICONTROL LDAP server]**. Você pode adicionar o número da porta. Por padrão, a porta usada é 389.
* Na lista suspensa, selecione o método de autenticação para os usuários:

   * Senha criptografada (**md5**)

      Modo padrão.

   * Senha de texto sem formatação + SSL (**TLS**)

      Todo o procedimento de autenticação (senha incluída) é criptografado. A porta segura 636 não deve ser usada neste modo: O Adobe Campaign muda automaticamente para o modo de segurança.

      Quando você usa esse modo de autenticação, no Linux, o certificado é verificado por uma biblioteca de clientes openLDAP. Recomendamos usar um certificado SSL válido para que o procedimento de autenticação seja criptografado. Caso contrário, as informações estarão em texto simples.

      O certificado também é verificado no Windows.

   * Gerenciador de LAN do Windows NT (**NTLM**)

      Autenticação proprietária do Windows. O **[!UICONTROL Unique identifier]** é usado somente para o nome de domínio.

   * Autenticação de senha distribuída (**DPA**)

      Autenticação proprietária do Windows. O **[!UICONTROL Unique identifier]** é usado somente para o nome de domínio (domain.com).

   * Senha de texto sem formatação

      Nenhuma criptografia (para uso somente em fases de teste).

* Selecione o modo de autenticação de usuário: **[!UICONTROL Automatically compute the unique user identifier]** (consulte a etapa [Cálculo de Nome Distinto](#distinguished-name-calculation)) ou **[!UICONTROL Search the unique user identifier in the directory]** (consulte a etapa [Procurando identificadores](#searching-for-identifiers)).

## Compatibilidade {#compatibility}

Os sistemas compatíveis dependem do mecanismo de autenticação selecionado. Veja a seguir uma matriz de compatibilidade de sistemas operacionais e servidores LDAP.

<table> 
 <thead> 
  <tr> 
   <th> </th> 
   <th> OpenLDAP<br /> </th> 
   <th> Ative Diretory<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> md5<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM e DPA<br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> texto simples<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Cálculo de Nome Distinto {#distinguished-name-calculation}

Se quiser calcular os identificadores de Nome Distinto (DN), a próxima etapa do assistente de implantação permite configurar o modo de cálculo.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Especifique o identificador exclusivo do usuário no diretório (Distinguished Name - DN) no campo **[!UICONTROL Distinguished Name]**.

   **[!UICONTROL (login)]** será substituído pelo identificador do operador do Adobe Campaign.

   >[!CAUTION]
   >
   >A configuração **[!UICONTROL dc]** deve estar em minúsculas.

* Selecione a opção **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** para sincronizar as associações de grupo e usuário no diretório LDAP e o grupo e associações de usuário no Adobe Campaign.

   Ao selecionar essa opção, os **[!UICONTROL Application level DN used for the search]** e **[!UICONTROL Password of the application login]** são ativados.

   Se você preencher esses dois campos, o Adobe Campaign se conectará ao servidor LDAP com seu próprio logon e senha. Se estiverem vazios, o Adobe Campaign se conectará ao servidor anonimamente.

## Pesquisar identificadores {#searching-for-identifiers}

Se você optar por pesquisar um identificador, o assistente de implantação permitirá configurar a pesquisa.

* Nos campos **[!UICONTROL Application level DN used for the search]** e **[!UICONTROL Password of the application login]**, forneça o identificador e a senha com os quais o Adobe Campaign se conectará para procurar o identificador. Se estiverem vazios, o Adobe Campaign se conectará ao servidor anonimamente.
* Especifique os campos **[!UICONTROL Base identifier]** e **[!UICONTROL Search scope]** para determinar um subconjunto do diretório LDAP a partir do qual a pesquisa será iniciada.

   Selecione o modo necessário na lista suspensa:

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      O diretório LDAP é totalmente pesquisado, começando por um determinado nível.

   1. **[!UICONTROL Limited to the base]**.

      Todos os atributos são incluídos na pesquisa.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      A pesquisa é executada em todos os atributos do diretório e a partir do primeiro nível do atributo.

* O campo **[!UICONTROL Filter]** permite especificar um elemento para refinar o escopo da pesquisa.

## Configuração de autorizações LDAP {#configuring-ldap-authorizations}

Essa janela é exibida quando você seleciona a opção **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

Você deve especificar vários parâmetros para localizar o grupo ou grupos aos quais o usuário pertence e seus direitos correspondentes, ou seja:

* o campo **[!UICONTROL Database identifier]**,
* o campo **[!UICONTROL Search scope]**,

   >[!NOTE]
   >
   >Se você optou por pesquisar o DN, é possível selecionar **[!UICONTROL Reuse the DN search parameters]** para transferir os valores selecionados para o DN e o escopo de pesquisa da tela anterior.

* o campo **[!UICONTROL Rights search filter]**, com base no logon e no nome distinto do usuário,
* o campo **[!UICONTROL Attribute containing the group or authorization name]** referente ao usuário,
* o campo **[!UICONTROL Association mask]** que permite a extração do nome do grupo no Adobe Campaign e seus direitos associados. Você pode usar expressões regulares para pesquisar o nome.
* Selecione **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** para que o usuário receba direitos de acesso automaticamente na conexão.

Clique em **[!UICONTROL Save]** para concluir a configuração da instância.

## Gerenciamento de operadores {#managing-operators}

Depois de confirmar a configuração, você deve definir quais operadores do Adobe Campaign são gerenciados por meio do diretório LDAP.

Para usar o diretório LDAP para autenticar um operador, edite o perfil correspondente e clique no link **[!UICONTROL Edit the access parameters]**. Selecione a opção **[!UICONTROL Use LDAP for authentication]**: O campo **[!UICONTROL Password]** fica esmaecido para esse operador.

![](assets/s_ncs_install_operator_in_ldap.png)

## Casos de uso {#use-cases}

Esta seção fornece alguns casos de uso simples para ajudar você a alcançar as configurações mais apropriadas com base em suas necessidades.

1. Um usuário foi criado no diretório LDAP, mas não no Adobe Campaign.

   O Adobe Campaign pode ser configurado para que o usuário acesse a plataforma por meio de sua autenticação LDAP. O Adobe Campaign precisa ser capaz de controlar a validade da combinação de ID/senha no diretório LDAP, para que o operador possa ser criado imediatamente no Adobe Campaign. Para fazer isso, marque a opção **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]**. Nesse caso, a sincronização de grupo também precisa ser configurada: a opção **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** precisa ser selecionada.

1. O usuário foi criado no Adobe Campaign, mas não no diretório LDAP.

   Eles não poderão fazer logon no Adobe Campaign.

1. Há um grupo no diretório LDAP que não existe no Adobe Campaign.

   Esse grupo não será criado no Adobe Campaign. É necessário criar o grupo e sincronizar os grupos para habilitar uma correspondência por meio da opção **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**.

1. Existem grupos no Adobe Campaign e o diretório LDAP é ativado após o evento: os grupos de usuários no Adobe Campaign não são substituídos automaticamente pelo conteúdo dos grupos LDAP. Da mesma forma, se um grupo existir apenas no Adobe Campaign, nenhum usuário LDAP poderá ser adicionado a ele até que o grupo tenha sido criado e sincronizado no LDAP.

   Os grupos nunca são criados em tempo real, seja pelo Adobe Campaign ou pelo LDAP. Eles precisam ser criados individualmente, tanto no Adobe Campaign quanto no diretório LDAP.

   Os nomes dos grupos no diretório LDAP precisam coincidir com os nomes dos grupos do Adobe Campaign. A máscara de associação é definida no último estágio de configuração do assistente de implantação: Adobe Campaign_(.*), por exemplo.
