---
product: campaign
title: Configurar zonas de segurança
description: Saiba como configurar zonas de segurança
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: 4fd69aa28c2e9325f4738ec571a6632c42ec26b8
workflow-type: tm+mt
source-wordcount: '1460'
ht-degree: 10%

---

# Definir zonas de segurança (no local){#defining-security-zones}

![](../../assets/v7-only.svg)

Cada operador precisa ser vinculado a uma zona para fazer logon em uma instância e o IP do operador deve ser incluído nos endereços ou conjuntos de endereços definidos na zona de segurança. A configuração da zona de segurança é realizada no arquivo de configuração do servidor do Adobe Campaign.

Operators are linked to a security zone from its profile in the console, accessible in the **[!UICONTROL Administration > Access management > Operators]** node. [Saiba mais](#linking-a-security-zone-to-an-operator).

>[!NOTE]
>
>Este procedimento restringe-se a **no local** implantações.
>
>Como um **hospedado** cliente, se você puder acessar [Painel de controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR), você pode usar a interface de autoatendimento da Zona de segurança. [Saiba mais](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=pt-BR)
>
>Outras **híbrido/hospedado** Os clientes precisam entrar em contato com a equipe de suporte do Adobe para adicionar IP à.

## Criar zonas de segurança {#creating-security-zones}

Uma zona é definida por:

* um ou mais intervalos de endereços IP (IPv4 e IPv6)
* um nome técnico associado a cada intervalo de endereços IP

As zonas de segurança são interbloqueadas, o que significa que definir uma nova zona dentro de outra reduz o número de operadores que podem fazer logon nela, enquanto aumenta os direitos atribuídos a cada operador.

As zonas devem ser definidas durante a configuração do servidor, na variável **serverConf.xml** arquivo. Todos os parâmetros disponíveis no **serverConf.xml** estão listadas em [esta seção](../../installation/using/the-server-configuration-file.md).

Cada zona define direitos, como:

* Conexão HTTP em vez de HTTPS
* Exibição de erro (erros de Java, JavaScript, C++ etc.)
* Visualização de relatório e aplicativo da Web
* Autenticação via login/senha
* Modo de conexão não seguro

>[!NOTE]
>
>**Cada operador deve estar vinculado a uma zona**. Se o endereço IP do operador pertencer ao intervalo definido pela zona, o operador poderá fazer logon na instância.\
>O endereço IP do operador pode ser definido em várias zonas. Nesse caso, o operador recebe a variável **set** dos direitos disponíveis para cada zona.

O pronto para uso **serverConf.xml** O arquivo inclui três zonas: **público, VPN e LAN**.

>[!NOTE]
>
>**The out-of-the-box configuration is secure**. However, before migrating from an earlier version of Adobe Campaign, it may be necessary to temporarily reduce security in order to migrate and approve the new rules.

Exemplo de como definir uma zona no **serverConf.xml** arquivo:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" name="public">
<subNetwork label="All addresses" mask="*" name="all"/>

<securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)"
              name="vpn" showErrors="true">

  <securityZone allowDebug="true" allowEmptyPassword="true" allowHTTP="true"
                allowUserPassword="false" label="Private Network (LAN)" name="lan"
                sessionTokenOnly="true" showErrors="true">
    <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
    <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
    <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
    <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
    <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
    <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  </securityZone>

</securityZone>
</securityZone>
```

All of the rights defining a zone are as follows:

* **allowDebug**: permite que um webApp seja executado no modo &quot;debug&quot;
* **allowEmptyPassword**: autoriza uma conexão com uma instância sem uma senha
* **allowHTTP**: uma sessão pode ser criada sem usar o protocolo HTTPS
* **allowUserPassword**: o token de sessão pode ter o seguinte formulário &quot;`<login>/<password>`&quot;
* **sessionTokenOnly**: o token de segurança não é necessário no URL de conexão
* **showErrors**: os erros no lado do servidor são encaminhados e exibidos

>[!IMPORTANT]
>
>Em uma definição de zona, cada atributo com a variável **true** reduz a segurança.

Ao usar o Message Center, se houver várias instâncias de execução, será necessário criar uma zona de segurança adicional com a variável **sessionTokenOnly** atributo definido como **true**, onde apenas os endereços IP necessários devem ser adicionados. Para obter mais informações sobre configuração de instâncias, consulte [este documento](../../message-center/using/configuring-instances.md).

## Práticas recomendadas para zonas de segurança {#best-practices-for-security-zones}

Na definição do **lan** zona de segurança, é possível adicionar uma máscara de endereço IP definindo o acesso técnico. Essa adição habilitará o acesso a todas as instâncias hospedadas no servidor.

```
<securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true"
                    allowUserPassword="false" label="Private Network (LAN)" name="lan"
                    sessionTokenOnly="true" showErrors="true">
        <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
        <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
        <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
        <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
        <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
        <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  
        <!-- Customer internal IPs -->
        <subNetwork id="internalNetwork" mask="a.b.c.d/xx"/>

      </securityZone>
```

Recomendamos definir intervalos de endereço IP diretamente no arquivo de configuração dedicado à instância para operadores que acessam apenas uma instância específica.

In the **`config-<instance>.xml`** file:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## Subredes e proxies numa zona de segurança {#sub-networks-and-proxies-in-a-security-zone}

O **proxy** pode ser usado em um **subNetwork** elemento para especificar o uso de proxy em uma zona de segurança.

Quando um proxy é referenciado e uma conexão é inserida por meio desse proxy (visível por meio do cabeçalho HTTP X-Forwarded-For), a zona verificada é a dos clientes do proxy e não a do proxy.

>[!IMPORTANT]
>
>Se um proxy estiver configurado e for possível substituí-lo (ou se não existir), o endereço IP que será testado poderá ser falsificado.
>
>Além disso, os relés agora são gerados como proxies. Portanto, você pode adicionar o endereço IP 127.0.0.1 à lista de proxies na configuração da sua zona de segurança.
>
>Por exemplo: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

Vários casos podem ocorrer:

* Uma sub-rede é referenciada diretamente na zona de segurança e nenhum proxy está configurado: os usuários da sub-rede podem se conectar diretamente ao servidor do Adobe Campaign.

   ![](assets/8101_proxy1.png)

* Um proxy é especificado para uma sub-rede na zona de segurança: os usuários dessa sub-rede podem acessar o servidor do Adobe Campaign por meio desse proxy.

   ![](assets/8101_proxy2.png)

* Um proxy está incluído em uma sub-rede de zona de segurança: os usuários que têm acesso por meio desse proxy, independentemente de sua origem, podem acessar o servidor do Adobe Campaign.

   ![](assets/8101_proxy3.png)

Os endereços IP dos proxies que provavelmente acessarão o servidor do Adobe Campaign devem ser inseridos em **`<subnetwork>`** e a sub-rede de primeiro nível **`<subnetwork name="all"/>`**. Por exemplo, aqui para um proxy cujo endereço IP é 10.131.146.102:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" 
                      name="public">
    <subNetwork label="All addresses" mask="*" name="all"
                      proxy="10.131.146.102,127.0.0.1, ::1"/>

    <securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)" 
                      name="vpn" showErrors="true">
        <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" 
                      allowUserPassword="false" label="Private Network (LAN)" 
                      name="lan" sessionTokenOnly="true" showErrors="true">
            <subNetwork label="Lan proxy" mask="10.131.193.182" name="lan3" 
                      proxy="10.131.146.102,127.0.0.1, ::1"/>
            <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" 
                      proxy="127.0.0.1, ::1"/>

        </securityZone>
    </securityZone>
</securityZone>
```

## Vincular uma zona de segurança a um operador {#linking-a-security-zone-to-an-operator}

Depois que as zonas forem definidas, cada operador deve estar vinculado a uma delas para poder fazer logon em uma instância e o endereço IP do operador deve ser incluído nos endereços ou no intervalo de endereços referenciados na zona.

A configuração técnica das zonas é realizada no arquivo de configuração do Servidor do Campaign: **serverConf.xml**.

Prior to this, you must start by configuring the out-of-the-box **[!UICONTROL Security zone]** enumeration to link a label to the internal name of the zone defined in the **serverConf.xml** file.

Essa configuração é feita no explorador do Campaign:

1. Clique no nó **[!UICONTROL Administration > Platform > Enumerations]**.
1. Selecione o **[!UICONTROL Security zone (securityZone)]** enumeração do sistema.

   ![](assets/enum_securityzone.png)

1. Para cada zona de segurança definida no arquivo de configuração do servidor, clique no botão **[!UICONTROL Add]** botão.
1. No **[!UICONTROL Internal name]** , digite o nome da zona definida no campo **serverConf.xml** arquivo. It corresponds to the **@name** attribute of the `<securityzone>`  element. Insira o rótulo vinculado ao nome interno na  **Rótulo** campo.

   ![](assets/enum_addsecurityvalue.png)

1. Clique em OK e salve as modificações.

Depois que as zonas forem definidas e a variável **[!UICONTROL Security zone]** for configurada, será necessário vincular cada operador a uma zona de segurança:

1. Clique no nó **[!UICONTROL Administration > Access management > Operators]**.
1. Select the operator whom you want to link a security zone to, and click the **[!UICONTROL Edit]** tab.
1. Acesse a guia **[!UICONTROL Access rights]** e clique no link **[!UICONTROL Edit access parameters...]**.

   ![](assets/zone_operator.png)

1. Selecione uma zona no **[!UICONTROL Authorized connection zone]** lista suspensa

   ![](assets/zone_operator_selection.png)

1. Clique em **[!UICONTROL OK]** e salve as modificações para aplicar essas alterações.



## Recomendações

* Certifique-se de que seu proxy reverso não seja permitido na sub-rede. Se for esse o caso, **all** o tráfego será detectado como proveniente deste IP local, então será confiável.

* Minimize o uso de sessionTokenOnly=&quot;true&quot;:

   * Aviso: Se este atributo for definido como true, o operador poderá ser exposto a um **Ataque CRSF**.
   * Além disso, o cookie sessionToken não é definido com um sinalizador httpOnly, portanto, algum código JavaScript do lado do cliente pode lê-lo.
   * No entanto, o Centro de Mensagens em várias células de execução precisa de sessionTokenOnly: crie uma nova zona de segurança com sessionTokenOnly definido como &quot;true&quot; e adicione **somente o(s) IP(s) necessário(s)** nesta zona.

* Quando possível, defina todos allowHTTP, showErrors como false (não para localhost) e verifique-os.

   * allowHTTP = &quot;false&quot;: força os operadores a usar HTTPS
   * showErrors = &quot;false&quot;: oculta erros técnicos (incluindo os SQL). Impede a exibição de informações demais, mas reduz a capacidade do profissional de marketing resolver erros (sem solicitar mais informações de um administrador)

* Defina allowDebug como true somente nos IPs usados pelos usuários/administradores de marketing que precisam criar pesquisas (na pré-visualização, na verdade), aplicativos da Web e relatórios. Esse sinalizador permite que esses IPs obtenham regras de retransmissão exibidas e os executa.

* Nunca defina allowEmptyPassword, allowUserPassword, allowSQLInjection como true. Estes atributos estão aqui apenas para permitir uma fácil migração das versões 5 e 6.0:

   * **allowEmptyPassword** permite que os operadores tenham uma senha vazia. Se este for o seu caso, notifique todos os seus operadores para eles definirem uma senha com um prazo. Once this deadline has passed, change this attribute to false.

   * **allowUserPassword** lets operators send their credentials as parameters (so they will be logged by apache/IIS/proxy). Esse recurso foi usado anteriormente para simplificar o uso da API. Você pode verificar em seu guia (ou na especificação) se alguns aplicativos de terceiros usam isso. If so, you have to notify them to change the way they use our API and as soon as possible remove this feature.

   * **allowSQLInjection** permite que o usuário execute injeções de SQL usando uma sintaxe antiga. As soon as possible carry out the corrections described in [this page](../../migration/using/general-configurations.md) to be able to set this attribute to false. É possível usar /nl/jsp/ping.jsp?zones=true para verificar a configuração de sua zona de segurança. Esta página exibe o status ativo das medidas de segurança (calculadas com esses sinalizadores de segurança) para o IP atual.

* HttpOnly cookie/useSecurityToken: consulte **sessionTokenOnly** sinalizador.

* Minimize os IPs adicionados à lista de permissões: Imediatamente, em zonas de segurança, adicionamos os 3 intervalos para redes privadas. É improvável usar todos esses endereços IP. Então mantenha apenas os que você precisa.

* Atualize o operador interno/webApp para estar acessível somente no host local.
