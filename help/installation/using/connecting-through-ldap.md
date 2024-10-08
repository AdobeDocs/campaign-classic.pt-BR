---
product: campaign
title: Conexão por meio do LDAP
description: Saiba como usar o LDAP para fazer logon no Campaign
feature: Installation, Instance Settings
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 1%

---

# Conexão por meio do LDAP {#connecting-through-ldap}

## Configuração do Campaign e do LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>* A configuração do LDAP só é possível para instalações locais ou híbridas.
>
>* Verifique se o sistema e as versões do openssl são compatíveis com o Campaign na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md). Versões desatualizadas podem afetar sua autenticação LDAP.
>

A configuração do LDAP é realizada no assistente de implantação. A opção **[!UICONTROL LDAP integration]** deve ser selecionada durante a primeira etapa de configuração. Consulte o [assistente de implantação](../../installation/using/deploying-an-instance.md#deployment-assistant).

A janela permite configurar a identificação de usuários do Adobe Campaign por meio do diretório LDAP especificado.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Especifique o endereço do servidor LDAP no campo **[!UICONTROL LDAP server]**. Você pode adicionar o número da porta. Por padrão, a porta usada é 389.
* Na lista suspensa, selecione o método de autenticação para usuários:

   * Senha criptografada (**md5**) - Modo padrão.

   * Senha de texto sem formatação + SSL (**TLS**) - O procedimento de autenticação inteiro (senha incluída) está criptografado. A porta segura 636 não deve ser usada neste modo: o Adobe Campaign alterna automaticamente para o modo seguro.

     Quando você usa esse modo de autenticação, no Linux, o certificado é verificado por uma biblioteca de cliente openLDAP. Recomendamos o uso de um certificado SSL válido para que o procedimento de autenticação seja criptografado. Caso contrário, as informações serão em texto simples.

     O certificado também é verificado no Windows.

   * Gerenciador de LAN do Windows NT (**NTLM**) - Autenticação proprietária do Windows. O **[!UICONTROL Unique identifier]** é usado somente para o nome de domínio.

   * Autenticação de Senha Distribuída (**DPA**) - Autenticação Proprietária do Windows. O **[!UICONTROL Unique identifier]** é usado apenas para o nome de domínio (domain.com).

   * Senha de texto sem formatação - Sem criptografia (para uso somente em fases de teste).

* Selecione o modo de autenticação do usuário: **[!UICONTROL Automatically compute the unique user identifier]** (consulte a etapa [Cálculo de Nome Diferenciado](#distinguished-name-calculation)) ou **[!UICONTROL Search the unique user identifier in the directory]** (consulte a etapa [Pesquisa de identificadores](#searching-for-identifiers)).

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
   <td> NTLM E DPA<br /> </td> 
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

## Cálculo do Nome Distinto {#distinguished-name-calculation}

Se quiser calcular os identificadores de Nome Distinto (DN), a próxima etapa do assistente de implantação permitirá configurar o modo de cálculo.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Especifique o identificador exclusivo do usuário no diretório (Nome Distinto - DN) no campo **[!UICONTROL Distinguished Name]**.

  **[!UICONTROL (login)]** será substituído pelo identificador do operador do Adobe Campaign.

  >[!CAUTION]
  >
  >A configuração **[!UICONTROL dc]** deve estar em minúsculas.

* Selecione a opção **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** para sincronizar as associações de grupo e usuário no diretório LDAP e as associações de grupo e usuário no Adobe Campaign.

  Quando você seleciona esta opção, o **[!UICONTROL Application level DN used for the search]** e o **[!UICONTROL Password of the application login]** são habilitados.

  Se você preencher esses dois campos, o Adobe Campaign se conectará ao servidor LDAP com seu próprio login e senha. Se estiverem vazios, o Adobe Campaign se conectará ao servidor anonimamente.

## Pesquisar identificadores {#searching-for-identifiers}

Se você optar por procurar um identificador, o assistente de implantação permitirá configurar a pesquisa.

* Nos campos **[!UICONTROL Application level DN used for the search]** e **[!UICONTROL Password of the application login]**, forneça o identificador e a senha com os quais o Adobe Campaign se conectará para procurar o identificador. Se estiverem vazios, o Adobe Campaign se conectará ao servidor anonimamente.
* Especifique os campos **[!UICONTROL Base identifier]** e **[!UICONTROL Search scope]** para determinar um subconjunto do diretório LDAP a partir do qual a pesquisa será iniciada.

  Selecione o modo desejado na lista suspensa:

  ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      O diretório LDAP é pesquisado na íntegra, a partir de um determinado nível.

   1. **[!UICONTROL Limited to the base]**.

      Todos os atributos são incluídos na pesquisa.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      A pesquisa é executada em todos os atributos do diretório e começando pelo primeiro nível do atributo.

* O campo **[!UICONTROL Filter]** permite especificar um elemento para refinar o escopo da pesquisa.

## Configuração de autorizações LDAP {#configuring-ldap-authorizations}

Esta janela é exibida quando você seleciona a opção **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

Você deve especificar vários parâmetros para localizar o grupo ou grupos aos quais o usuário pertence e seus direitos correspondentes, ou seja:

* o campo **[!UICONTROL Database identifier]**,
* o campo **[!UICONTROL Search scope]**,

  >[!NOTE]
  >
  >Se você optou por pesquisar o DN, é possível selecionar **[!UICONTROL Reuse the DN search parameters]** para transportar os valores selecionados para o DN e o escopo de pesquisa da tela anterior.

* o campo **[!UICONTROL Rights search filter]**, com base no logon e no nome distinto do usuário,
* o campo **[!UICONTROL Attribute containing the group or authorization name]** referente ao usuário,
* o campo **[!UICONTROL Association mask]** que habilita a extração do nome do grupo no Adobe Campaign e seus direitos associados. Você pode usar expressões regulares para procurar pelo nome.
* Selecione **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** para que o usuário receba direitos de acesso automaticamente na conexão.

Clique em **[!UICONTROL Save]** para concluir a configuração da instância.

## Gerenciamento de operadores {#managing-operators}

Depois de confirmar a configuração, você deve definir quais operadores do Adobe Campaign são gerenciados por meio do diretório LDAP.

Para usar o diretório LDAP para autenticar um operador, edite o perfil correspondente e clique no link **[!UICONTROL Edit the access parameters]**. Selecione a opção **[!UICONTROL Use LDAP for authentication]**: o campo **[!UICONTROL Password]** está esmaecido para este operador.

![](assets/s_ncs_install_operator_in_ldap.png)

## Casos de uso {#use-cases}

Esta seção fornece alguns casos de uso simples para ajudá-lo a obter as configurações mais apropriadas com base em suas necessidades.

1. Um usuário foi criado no diretório LDAP, mas não no Adobe Campaign.

   O Adobe Campaign pode ser configurado para que o usuário acesse a plataforma por meio da autenticação LDAP. O Adobe Campaign precisa controlar a validade da combinação ID/senha no diretório LDAP para que o operador possa ser criado dinamicamente no Adobe Campaign. Para fazer isso, marque a opção **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]**. Nesse caso, a sincronização de grupos também precisa ser configurada: a opção **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** precisa ser selecionada.

1. O usuário foi criado no Adobe Campaign, mas não no diretório LDAP.

   Eles não poderão fazer logon no Adobe Campaign.

1. Há um grupo no diretório LDAP que não existe no Adobe Campaign.

   Este grupo não será criado no Adobe Campaign. É necessário criar o grupo e sincronizar os grupos para habilitar uma correspondência por meio da opção **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**.

1. Existem grupos no Adobe Campaign e o diretório LDAP é ativado após o evento: os grupos de usuários no Adobe Campaign não são substituídos automaticamente pelo conteúdo de grupos LDAP. Da mesma forma, se um grupo só existir no Adobe Campaign, nenhum usuário do LDAP poderá ser adicionado a ele até que o grupo tenha sido criado e sincronizado no LDAP.

   Os grupos nunca são criados em tempo real, seja pelo Adobe Campaign ou pelo LDAP. Eles precisam ser criados individualmente, no Adobe Campaign e no diretório LDAP.

   Os nomes dos grupos no diretório LDAP precisam coincidir com os nomes dos grupos Adobe Campaign. Sua máscara de associação é definida na última etapa de configuração do assistente de implantação: Adobe Campaign_(.&#42;), por exemplo.
