---
solution: Campaign Classic
product: campaign
title: Configuração do servidor
description: Saiba mais sobre as práticas recomendadas de configuração do servidor.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 564eaedb09282c85593f638617baded0a63494a0
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 39%

---


# Configuração do servidor {#server-configuration}

## Configuração de zonas de segurança

A partir da build 8977, a Interface do Usuário de autoatendimento das zonas de segurança não está mais disponível. Se você não estiver hospedado no AWS, entre em contato com a equipe de suporte da Adobe para adicionar IPs à lista de permissões. Caso contrário, a adição de IP à lista de permissões deve ser executada no [Painel de controle](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).

Para verificar se sua instância está hospedada no AWS, siga as etapas detalhadas em [this page](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

>[!NOTE]
> 
>O Painel de controle do Campaign é acessível a todos os usuários administradores. As etapas para conceder acesso de Administrador a um usuário estão detalhadas [nesta seção](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel).
>
>Observe que sua instância deve ser hospedada no AWS e atualizada com a build mais recente do [Gold Standard](../../rn/using/gs-overview.md) ou a build mais recente do GA (21.1)](../../rn/using/latest-release.md). [ Saiba como verificar sua versão em [this section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


* Certifique-se de que seu proxy reverso não seja permitido na sub-rede. Se for o caso, o tráfego **all** será detectado como proveniente deste IP local, então será confiável.

* Minimize o uso de sessionTokenOnly=&quot;true&quot;:

   * Aviso: Se este atributo for definido como true, o operador poderá ser exposto a um **ataque CRSF**.
   * Além disso, o cookie sessionToken não é definido com um sinalizador httpOnly, portanto, algum código javascript do lado do cliente pode lê-lo.
   * No entanto, o Centro de Mensagens em várias células de execução precisa de sessionTokenOnly: crie uma nova zona de segurança com sessionTokenOnly definido como &quot;true&quot; e adicione **somente o(s) IP(s) necessário(s)** nessa zona.

* Quando possível, defina todos allowHTTP, showErrors como false (não para localhost) e verifique-os.

   * allowHTTP = &quot;false&quot;: força os operadores a usar HTTPS
   * showErrors = &quot;false&quot;: oculta erros técnicos (incluindo os SQL). Impede a exibição de informações demais, mas reduz a capacidade do profissional de marketing resolver erros (sem solicitar mais informações de um administrador)

* Defina allowDebug como true somente nos IPs usados pelos usuários/administradores de marketing que precisam criar pesquisas (na pré-visualização, na verdade), aplicativos da Web e relatórios. Esse sinalizador permite que esses IPs obtenham regras de retransmissão exibidas e os executa.

* Nunca defina allowEmptyPassword, allowUserPassword, allowSQLInjection como true. Estes atributos estão aqui apenas para permitir uma fácil migração das versões 5 e 6.0:

   * **** Os operadores allowEmptyPasswordlets têm uma senha vazia. Se este for o seu caso, notifique todos os seus operadores para eles definirem uma senha com um prazo. Depois que esse prazo expirar, altere esse atributo para false.

   * **** Os operadores allowUserPasswordlets enviam suas credenciais como parâmetros (para que sejam registrados por apache/IIS/proxy). Esse recurso foi usado anteriormente para simplificar o uso da API. Você pode verificar em seu guia (ou na especificação) se alguns aplicativos de terceiros usam isso. Em caso positivo, é necessário notificá-los para alterar a maneira como eles usam nossa API e, assim que possível, remover esse recurso.

   * **** allowSQLInjection permite que o usuário realize injeções de SQL usando uma sintaxe antiga. Assim que possível, execute as correções descritas em [this page](../../migration/using/general-configurations.md) para poder definir este atributo como false. É possível usar /nl/jsp/ping.jsp?zones=true para verificar a configuração de sua zona de segurança. Esta página exibe o status ativo das medidas de segurança (calculadas com esses sinalizadores de segurança) para o IP atual.

* HttpOnly cookie/useSecurityToken: consulte o sinalizador **sessionTokenOnly** .

* Minimizar IPs adicionados à lista de permissões: adicionamos os 3 intervalos para redes privadas em zonas de segurança, de modo rápido e prático. É improvável usar todos esses endereços IP. Então mantenha apenas os que você precisa.

* Atualize o operador interno/webApp para estar acessível somente no host local.

## Proteção de upload de arquivo

Verifique com os usuários operacionais que tipo de arquivos eles enviam ao servidor usando a interface nlclient/web. Como lembrete, as necessidades de negócios podem ser:

* imagens (jpg, gif, png, ...)
* conteúdo (zip, html, css...)
* ativos de marketing (doc, xls, pdf, psd, tiff, ...)
* anexo de email (doc, pdf, ...)
* ETL (txt, csv, guia, ...)
* etc.

Adicione todos eles em serverConf/shared/datastore/@uploadAllowlist (expressão Java regular válida). Saiba mais [nesta página](../../installation/using/configuring-campaign-server.md#limiting-uploadable-files).

O Adobe Campaign não restringe o tamanho do arquivo. Mas você pode fazê-lo configurando o IIS/Apache. Saiba mais [nesta seção](../../installation/using/web-server-configuration.md).

## Retransmissão

Consulte [esta página](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) para obter mais informações.

Por padrão, todas as páginas dinâmicas são automaticamente retransmitidas para o servidor Tomcat local da máquina cujo módulo da Web foi iniciado. É possível optar por não retransmitir alguns deles. Se alguns módulos do Adobe Campaign não estiverem sendo usados (como aplicação Web, interação, algum jsp), podem ser removidos das regras de retransmissão. 

Pronto para uso, forçamos a capacidade de exibir recursos do usuário final usando http (httpAllowed=&quot;true&quot;). Como estas páginas podem mostrar algum PII (como conteúdo de email, endereço), cupons de resgate, ofertas, você deverá forçar novamente o HTTPS nesses caminhos.

Se você estiver usando nomes de host diferentes (um público e um para operadores), também poderá impedir a retransmissão de alguns recursos necessários pelos operadores sobre o nome DNS público.

## Proteção de conexão de saída

A lista padrão de URLs que podem ser chamados por códigos JavaScript (workflows, etc.) é limitada. Para permitir uma nova URL, o administrador precisa referenciá-la no arquivo [serverConf.xml](../../installation/using/the-server-configuration-file.md).

Existem três modos de proteção de conexão:

* **Bloqueio** : todos os URLs fora da lista de permissões são bloqueados, com uma mensagem de erro. Este é o modo padrão depois de um pós-upgrade.
* **Permissivo** : todos os URLs fora da lista de permissões são permitidos.
* **Aviso** : todos os URLs não na lista de permissões são permitidos, mas o interpretador JS emite um aviso, para que o administrador possa coletá-los. Esse modo adiciona mensagens de aviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

Novos clientes usarão o modo de bloqueio. Se eles quiserem permitir um novo URL, precisam contatar o administrador para incluí-lo na lista de permissões.

Os clientes existentes provenientes de uma migração podem usar o modo de aviso por algum tempo. Enquanto isso, eles precisam analisar o tráfego de saída antes de autorizar os URLS.

## Restrição de comando (lado do servidor)

Vários comandos estão incluídos na lista negra e não podem ser executados usando a função execCommand. Uma segurança extra é fornecida por um usuário Unix dedicado para executar comandos externos. Para instalações hospedadas, essa restrição é aplicada automaticamente. Para instalações locais, você pode configurar manualmente essa restrição seguindo as instruções de [this page](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). Além disso, as atividades de workflow **[!UICONTROL Script]** e **[!UICONTROL External task]** não estão disponíveis (instâncias recém-instaladas).

## Outras configurações

Você pode adicionar cabeçalhos HTTP extras para todas as páginas (para obter mais informações, consulte [esta página](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* Você pode adicionar alguns cabeçalhos adicionais, como HSTS, X-FRAME-OPTIONS, CSP...
* Você precisa testá-los em um ambiente de teste antes de aplicá-los na produção.

   >[!IMPORTANT]
   >
   >O Adobe Campaign pode ser interrompido adicionando determinados cabeçalhos.

O Adobe Campaign permite definir uma senha simples no elemento `<dbcnx .../>` . Não use esse recurso.

Por padrão, o Adobe Campaign não coloca uma sessão em um IP específico, mas você pode ativá-lo para impedir que a sessão seja roubada. Para fazer isso, no arquivo [serverConf.xml](../../installation/using/the-server-configuration-file.md), defina o atributo checkIPConsistent como **true** no nó `<authentication>`.

Por padrão, o MTA do Adobe Campaign não usa uma conexão segura para enviar conteúdo ao servidor SMTP. Esse recurso deve ser habilitado (pode reduzir a velocidade de entrega). Para fazer isso, defina **enableTLS** para **true** no nó `<smtp ...>`.

Você pode reduzir a duração de uma sessão no nó de autenticação (atributo sessionTimeOutSec).
