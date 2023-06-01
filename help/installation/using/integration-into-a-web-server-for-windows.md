---
product: campaign
title: Integração em um servidor Web para Windows
description: Integração em um servidor Web para Windows
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 5%

---

# Integração em um servidor Web para Windows{#integration-into-a-web-server-for-windows}



O Adobe Campaign inclui o Apache Tomcat, que atua como ponto de entrada no servidor de aplicativos via HTTP (e SOAP).

Você pode usar esse servidor Tomcat integrado para atender a solicitações HTTP.

Neste caso:

* a porta de escuta padrão é 8080. Para alterá-lo, consulte [nesta seção](../../installation/using/configure-tomcat.md).
* Os consoles clientes se conectam usando um URL como ```https:// `<computer>`:8080```.

No entanto, por motivos de segurança e administração, recomendamos usar um servidor Web dedicado como principal ponto de entrada para o tráfego HTTP quando o computador que executa o Adobe Campaign estiver exposto na Internet e você desejar abrir o acesso ao console fora da rede.

Um servidor da Web também permite garantir a confidencialidade dos dados com o protocolo HTTPs.

Da mesma forma, você deve usar um servidor Web quando quiser usar a funcionalidade de rastreamento, que está disponível somente como um módulo de extensão de servidor Web.

>[!NOTE]
>
>Se você não usar a funcionalidade de rastreamento, poderá executar uma instalação padrão do Apache ou do IIS com um redirecionamento para o Campaign. O módulo de extensão do servidor Web de rastreamento não é necessário.

## Configuração do servidor Web IIS {#configuring-the-iis-web-server}

O procedimento de configuração de um servidor Web IIS é, em sua maioria, gráfico. Envolve o uso de um site (já criado ou com criação pendente) para acessar os recursos do servidor do Adobe Campaign: arquivos Java (.jsp), folhas de estilos (.css, .xsl), imagens (.png), a DLL ISAPI para redirecionamento, etc.

As seções a seguir detalham a configuração no IIS 7. A configuração do IIS8 é basicamente a mesma.

Se o servidor Web IIS ainda não estiver instalado no computador, você poderá instalá-lo por meio do **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]** menu.

No IIS 7, além dos serviços padrão, você precisa instalar as extensões ISAPI e os filtros ISAPI.

![](assets/s_ncs_install_iis7_isapi.png)

### Etapas de configuração {#configuration-steps}

Aplique as seguintes etapas de configuração:

1. Abra o IIS pelo **[!UICONTROL Control panel > Administrative tools > Services]** menu.
1. Crie e configure o site (Adobe Campaign, por exemplo) dependendo dos parâmetros da sua rede (porta de conexão TCP, host DNS, endereço IP).

   ![](assets/s_ncs_install_iis7_add_site.png)

   Especifique pelo menos o nome do site e o caminho de acesso para o diretório virtual. Como o caminho para acessar o diretório Website não é usado, você pode usar o seguinte diretório.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. A **VBS** O script permite configurar automaticamente os recursos usados pelo servidor Adobe Campaign no diretório virtual que acabamos de criar. Para iniciá-lo, clique duas vezes na guia **iis_neolane_setup.vbs** arquivo localizado na `[INSTALL]\conf` pasta, onde `[INSTALL]` é o caminho para acessar a pasta de instalação do Adobe Campaign.

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >No caso de uma instalação do Windows Server 2008/IIS7, você deve estar conectado como administrador para executar o script do VBS ou executar o script como administrador.

   Clique em **[!UICONTROL OK]** se o servidor Web for usado como um servidor de redirecionamento de rastreamento, caso contrário, clique em **[!UICONTROL Cancel]**.

   Quando vários sites já estiverem configurados no servidor Web, uma página intermediária será exibida para especificar a qual site a instalação se aplica: digite o número vinculado ao site e clique em **[!UICONTROL OK]**.

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   Uma mensagem de confirmação deve ser exibida:

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. No **[!UICONTROL Content View]** verifique se o site está configurado corretamente com os recursos do Adobe Campaign:

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   Se a árvore não for exibida, reinicie o IIS.

### Gerenciamento de direitos {#managing-rights}

Em seguida, defina as configurações de segurança para a DLL ISAPI e para os recursos no diretório de instalação do Adobe Campaign.

Para fazer isso, siga as etapas abaixo:

1. Selecione o **[!UICONTROL Features View]** e clique duas vezes na guia **Autenticação** link.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. No **Segurança de Diretório** do site, verifique se o acesso anônimo está ativado. Se necessário, clique no link **[!UICONTROL Edit]** link para alterar as configurações.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Iniciar o servidor Web e testar a configuração {#launching-the-web-server-and-testing-the-configuration}

Agora você deve testar se a configuração está correta.

Para fazer isso, siga o procedimento abaixo:

1. Reinicie o servidor IIS usando o **iisreset** linha de comando.

1. Inicie o serviço Adobe Campaign e verifique se ele está em execução.

1. Teste o módulo de rastreamento inserindo o seguinte URL em um navegador da Web:

   ```
   https://<computer>/r/test
   ```

   O navegador deve exibir a seguinte resposta:

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

Para testar a presença do módulo de redirecionamento, execute a seguinte linha de comando:

```
nlserver pdump
```

Ele deve retornar as seguintes informações:

```
12:00:33 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

Você também pode verificar se a DLL ISAPI está carregada corretamente.

Para fazer isso, siga as etapas abaixo:

1. Edite os filtros ISAPI para o site do Adobe Campaign clicando no link **[!UICONTROL Driver mapping]** ícone.
1. A verificação do conteúdo do filtro ISAPI:

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## Configurações adicionais {#additional-configurations}

### Alterar o limite de tamanho do arquivo de upload {#changing-the-upload-file-size-limit}

Ao configurar o servidor Web IIS, um limite de aproximadamente 28 MB é automaticamente definido para arquivos definidos que são carregados no servidor.

Isso pode ter um impacto no Adobe Campaign, especialmente se você quiser carregar arquivos maiores que esse limite.

Por exemplo, se você usar uma variável **Carregamento de dados (arquivo)** Em um fluxo de trabalho para importar um arquivo de 50 MB, um erro impedirá que o fluxo de trabalho seja executado corretamente.

Nesse caso, você deve aumentar esse limite:

1. Abra o IIS pelo **[!UICONTROL Start > (Control panel) > Administration tools]** menu.
1. No **Conexões** selecione o site criado para a instalação do Adobe e clique duas vezes em **Filtragem de solicitação** no painel principal.
1. No **Ações** selecione **Editar configurações de recurso** para poder editar o valor no **Tamanho máximo autorizado do conteúdo (bytes)** campo.

   Por exemplo, para autorizar o upload de arquivos de 50 MB, você deve especificar um valor maior que &quot;52428800&quot; bytes.

>[!NOTE]
>
>Para obter mais informações sobre essa opção do IIS, consulte a seção &quot;Como&quot; do [documentação oficial](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits).

