---
title: Conexão por meio do LDAP
seo-title: Conexão por meio do LDAP
description: Conexão por meio do LDAP
seo-description: null
page-status-flag: never-activated
uuid: 13a426bc-7c34-49e5-ac8e-26d830845f28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 1563db7c-ccb6-46b3-9299-67ec0aedaca0
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 2%

---


# Conexão por meio do LDAP{#connecting-through-ldap}

## Configuração de Campanha e LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>A configuração LDAP só é possível para instalações locais ou híbridas.

A configuração LDAP é realizada no assistente de implantação. A **[!UICONTROL LDAP integration]** opção deve ser selecionada durante a primeira etapa de configuração. Consulte o Assistente [de implantação](../../installation/using/deploying-an-instance.md#deployment-wizard).

A janela permite configurar a identificação de usuários do Adobe Campaign por meio do diretório LDAP especificado.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Specify the address of the LDAP server in the **[!UICONTROL LDAP server]** field. É possível adicionar o número da porta. Por padrão, a porta usada é 389.
* Na lista suspensa, selecione o método de autenticação para os usuários:

   * Senha criptografada (**md5**)

      Modo padrão.

   * Senha de texto sem formatação + SSL (**TLS**)

      Todo o procedimento de autenticação (senha incluída) é criptografado. A porta segura 636 não deve ser usada neste modo: A Adobe Campaign muda automaticamente para o modo de segurança.

      Quando você usa esse modo de autenticação, no Linux, o certificado é verificado por uma biblioteca de cliente openLDAP. Recomendamos usar um certificado SSL válido para que o procedimento de autenticação seja criptografado. Caso contrário, as informações ficarão em texto simples.

      O certificado também é verificado no Windows.

   * Gerenciador de LAN do Windows NT (**NTLM**)

      Autenticação proprietária do Windows. O **[!UICONTROL Unique identifier]** é usado apenas para o nome do domínio.

   * Autenticação de senha distribuída (**DPA**)

      Autenticação proprietária do Windows. O **[!UICONTROL Unique identifier]** é usado somente para o nome do domínio (domínio.com).

   * Senha de texto sem formatação

      Nenhuma criptografia (para uso somente em fases de teste).

* Selecione o modo de autenticação de usuário: **[!UICONTROL Automatically compute the unique user identifier]** (consulte a etapa [Cálculo](#distinguished-name-calculation)de Nome Distinto) ou **[!UICONTROL Search the unique user identifier in the directory]** (consulte a etapa [Procurando identificadores](#searching-for-identifiers)).

## Compatibilidade {#compatibility}

Os sistemas compatíveis dependem do mecanismo de autenticação selecionado. A seguir está uma matriz de compatibilidade de sistemas operacionais e servidores LDAP.

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
   <td> texto sem formatação<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Cálculo de Nome Distinto {#distinguished-name-calculation}

Se desejar calcular os identificadores de Nome Distinto (DN), a próxima etapa do assistente de implantação permite configurar o modo de cálculo.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Especifique o identificador exclusivo do usuário no diretório (Distinguished Name - DN) no **[!UICONTROL Distinguished Name]** campo.

   **[!UICONTROL (login)]** será substituído pelo identificador do operador Adobe Campaign.

   >[!CAUTION]
   >
   >A **[!UICONTROL dc]** configuração deve estar em minúsculas.

* Selecione a opção **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** para sincronizar as associações de grupo e usuário no diretório LDAP e as associações de grupo e usuário no Adobe Campaign.

   Quando você seleciona essa opção, as opções **[!UICONTROL Application level DN used for the search]** e **[!UICONTROL Password of the application login]** são ativadas.

   Se você preencher esses dois campos, a Adobe Campaign se conectará ao servidor LDAP com seu próprio logon e senha. Se estiverem vazios, a Adobe Campaign se conectará ao servidor anonimamente.

## Procurando identificadores {#searching-for-identifiers}

Se você optar por procurar um identificador, o assistente de implantação permitirá que você configure a pesquisa.

* Nos campos **[!UICONTROL Application level DN used for the search]** e **[!UICONTROL Password of the application login]** , forneça o identificador e a senha com os quais a Adobe Campaign se conectará para procurar o identificador. Se estiverem vazios, a Adobe Campaign se conectará ao servidor anonimamente.
* Especifique os campos **[!UICONTROL Base identifier]** e **[!UICONTROL Search scope]** para determinar um subconjunto do diretório LDAP a partir do qual a pesquisa será start.

   Selecione o modo desejado na lista suspensa:

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      O diretório LDAP é pesquisado na íntegra, a partir de um determinado nível.

   1. **[!UICONTROL Limited to the base]**.

      Todos os atributos são incluídos na pesquisa.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      A pesquisa é realizada em todos os atributos do diretório e a partir do primeiro nível do atributo.

* O **[!UICONTROL Filter]** campo permite especificar um elemento para refinar o escopo da pesquisa.

## Configurando autorizações LDAP {#configuring-ldap-authorizations}

Essa janela é exibida quando você seleciona a **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** opção.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

Você deve especificar vários parâmetros para localizar o grupo ou grupos aos quais o usuário pertence e seus direitos correspondentes, ou seja:

* the **[!UICONTROL Database identifier]** field,
* the **[!UICONTROL Search scope]** field,

   >[!NOTE]
   >
   >Se você optou por pesquisar o DN, poderá selecionar **[!UICONTROL Reuse the DN search parameters]** para transferir os valores selecionados para o DN e o escopo de pesquisa da tela anterior.

* o **[!UICONTROL Rights search filter]** campo, com base no logon e no nome distinto do usuário,
* o **[!UICONTROL Attribute containing the group or authorization name]** campo relativo ao utilizador,
* o **[!UICONTROL Association mask]** campo que permite a extração do nome do grupo no Adobe Campaign e seus direitos associados. Você pode usar expressões regulares para pesquisar pelo nome.
* Selecione **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** para que o usuário receba direitos de acesso automaticamente na conexão.

Clique **[!UICONTROL Save]** para concluir a configuração da instância.

## Gerenciar operadores {#managing-operators}

Depois de confirmar a configuração, você deve definir quais operadores Adobe Campaign são gerenciados pelo diretório LDAP.

Para usar o diretório LDAP para autenticar um operador, edite o perfil correspondente e clique no **[!UICONTROL Edit the access parameters]** link. Selecione a **[!UICONTROL Use LDAP for authentication]** opção: O **[!UICONTROL Password]** campo fica acinzentado para esse operador.

![](assets/s_ncs_install_operator_in_ldap.png)

## Casos de uso {#use-cases}

Esta seção fornece alguns casos de uso simples para ajudá-lo a obter as configurações mais apropriadas com base em suas necessidades.

1. Um usuário foi criado no diretório LDAP, mas não no Adobe Campaign.

   O Adobe Campaign pode ser configurado para que o usuário acesse a plataforma por meio de sua autenticação LDAP. A Adobe Campaign precisa controlar a validade da combinação ID/senha no diretório LDAP, para que o operador possa ser criado dinamicamente no Adobe Campaign. Para fazer isso, marque a opção **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]**. Nesse caso, a sincronização de grupos também precisa ser configurada: a **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** opção precisa ser selecionada.

1. O usuário foi criado no Adobe Campaign, mas não no diretório LDAP.

   Eles não poderão se conectar à Adobe Campaign.

1. Há um grupo no diretório LDAP que não existe no Adobe Campaign.

   Este grupo não será criado no Adobe Campaign. É necessário criar o grupo e sincronizar os grupos para habilitar uma correspondência por meio da **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** opção.

1. Existem grupos no Adobe Campaign e o diretório LDAP é ativado após o evento: os grupos de usuários no Adobe Campaign não são substituídos automaticamente pelo conteúdo dos grupos LDAP. Da mesma forma, se um grupo existir somente no Adobe Campaign, nenhum usuário do LDAP poderá ser adicionado a ele até que o grupo tenha sido criado e sincronizado no LDAP.

   Os grupos nunca são criados dinamicamente, seja pela Adobe Campaign ou pelo LDAP. Eles precisam ser criados individualmente, tanto no Adobe Campaign quanto no diretório LDAP.

   Os nomes dos grupos no diretório LDAP precisam coincidir com os nomes dos grupos do Adobe Campaign. A máscara de associação é definida na última etapa de configuração do assistente de implantação: Adobe Campaign_(.*), por exemplo.

