---
product: campaign
title: Integração em um servidor Web para Windows
description: Integração em um servidor Web para Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: 3958fff140cc9bf6c371f0c4207cafc9a27bb725
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 4%

---

# Integração em um servidor Web para Windows{#integration-into-a-web-server-for-windows}

O Adobe Campaign inclui o Apache Tomcat, que atua como ponto de entrada no servidor de aplicativos via HTTP (e SOAP).

Você pode usar esse servidor Tomcat integrado para atender às solicitações HTTP.

Nesse caso:

* a porta de escuta padrão é 8080. Para alterá-lo, consulte [esta seção](../../installation/using/configure-tomcat.md).
* Os consoles cliente se conectam usando um URL como [https:// `<computer>`:8080](https://myserver.adobe.com:8080).

No entanto, por motivos de segurança e administração, recomendamos usar um servidor Web dedicado como o principal ponto de entrada para tráfego HTTP quando o computador que está executando o Adobe Campaign é exposto na Internet e você deseja abrir o acesso ao console fora da rede.

Um servidor da Web também permite garantir a confidencialidade dos dados com o protocolo HTTPs.

Da mesma forma, você deve usar um servidor da Web quando quiser usar a funcionalidade de rastreamento, que só está disponível como um módulo de extensão de servidor da Web.

>[!NOTE]
>
>Se você não usar a funcionalidade de rastreamento, poderá executar uma instalação padrão do Apache ou IIS com um redirecionamento para o Campaign. O módulo de extensão do servidor Web de rastreamento não é necessário.

## Configuração do servidor Web IIS {#configuring-the-iis-web-server}

O procedimento de configuração de um servidor Web IIS é principalmente gráfico. Envolve o uso de um site (já criado ou com criação pendente) para acessar os recursos do servidor Adobe Campaign: Arquivos Java (.jsp), folhas de estilos (.css, .xsl), imagens (.png), DLL ISAPI para redirecionamento etc.

As seções a seguir detalham a configuração no IIS 7. A configuração do IIS8 é basicamente a mesma.

Se o servidor Web IIS ainda não estiver instalado no computador, você poderá instalá-lo por meio do menu **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]**.

No IIS 7, além dos serviços padrão, é necessário instalar as extensões ISAPI e os filtros ISAPI.

![](assets/s_ncs_install_iis7_isapi.png)

### Etapas de configuração {#configuration-steps}

Aplique as seguintes etapas de configuração:

1. Abra o IIS por meio do menu **[!UICONTROL Control panel > Administrative tools > Services]**.
1. Crie e configure o site (Adobe Campaign, por exemplo) dependendo dos parâmetros da sua rede (porta de conexão TCP, host DNS, endereço IP).

   ![](assets/s_ncs_install_iis7_add_site.png)

   Você deve especificar pelo menos o nome do site e o caminho de acesso para o diretório virtual. Como o caminho para acessar o diretório do site não é usado, você pode usar o seguinte diretório.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. Um script **VBS** permite configurar automaticamente os recursos usados pelo servidor do Adobe Campaign no diretório virtual que acabamos de criar. Para iniciá-lo, clique duas vezes no arquivo **iis_neolane_setup.vbs** localizado na pasta `[INSTALL]\conf`, onde `[INSTALL]` é o caminho para acessar a pasta de instalação do Adobe Campaign.

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >No caso de uma instalação do Windows Server 2008/IIS7, você deve estar conectado como administrador para executar o script VBS ou executar o script como administrador.

   Clique em **[!UICONTROL OK]** se o servidor da Web for usado como um servidor de redirecionamento de rastreamento, caso contrário, clique em **[!UICONTROL Cancel]**.

   Quando vários sites já estão configurados no servidor da Web, uma página intermediária é exibida para especificar a qual site a instalação se aplica: insira o número vinculado ao site e clique em **[!UICONTROL OK]**.

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   Uma mensagem de confirmação deve ser exibida:

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. Na guia **[!UICONTROL Content View]** , verifique se o site está configurado corretamente com os recursos do Adobe Campaign:

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   Se a árvore não for exibida, reinicie o IIS.

### Gerenciamento de direitos {#managing-rights}

Em seguida, você deve definir as configurações de segurança para a DLL ISAPI e para os recursos no diretório de instalação do Adobe Campaign.

Para fazer isso, siga as etapas abaixo:

1. Selecione a guia **[!UICONTROL Features View]** e clique duas vezes no link **Authentication**.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. Na guia **Diretory Security** do site, verifique se o acesso anônimo está ativado. Se necessário, clique no link **[!UICONTROL Edit]** para alterar as configurações.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Iniciar o servidor Web e testar a configuração {#launching-the-web-server-and-testing-the-configuration}

Agora você deve testar se a configuração está correta.

Para fazer isso, siga as etapas abaixo:

1. Reinicie o servidor IIS usando a linha de comando **iisreset**.

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

Também é possível verificar se a DLL da ISAPI está carregada corretamente.

Para fazer isso, siga as etapas abaixo:

1. Edite os filtros ISAPI do site do Adobe Campaign clicando no ícone **[!UICONTROL Driver mapping]**.
1. Verifique o conteúdo do filtro ISAPI:

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## Configurações adicionais {#additional-configurations}

### Alteração do limite de tamanho do arquivo de upload {#changing-the-upload-file-size-limit}

Ao configurar o servidor Web IIS, um limite de aproximadamente 28 MB é automaticamente para arquivos definidos que são carregados no servidor.

Isso pode ter um impacto no Adobe Campaign, principalmente se você quiser fazer upload de arquivos maiores que esse limite.

Por exemplo, se você usar uma atividade do tipo **Data loading (file)** em um workflow para importar um arquivo de 50 MB, um erro impedirá a execução correta do workflow.

Nesse caso, é necessário aumentar esse limite:

1. Abra o IIS por meio do menu **[!UICONTROL Start > (Control panel) > Administration tools]**.
1. No painel **Conexões**, selecione o site criado para a instalação do Adobe e clique duas vezes em **Filtragem de Solicitação** no painel principal.
1. No painel **Actions**, selecione **Edit Feature Settings** para poder editar o valor no campo **Maximum authorized content size (bytes)**.

   Por exemplo, para autorizar o upload de arquivos de 50 MB, você deve especificar um valor superior a &quot;52428800&quot; bytes.

>[!NOTE]
>
>Para obter mais informações sobre essa opção do IIS, consulte a seção &quot;Como&quot; da [documentação oficial](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits).

### Configuração da exibição da mensagem de erro http {#configuring-http-error-message-display}

Se você usar um servidor IIS versão 6.1, as mensagens de erro geradas podem ser difíceis de ler devido a um código HTML indesejado ser exibido na mensagem.

Para corrigir isso e exibir o erro corretamente, aplique a seguinte configuração:

1. Abra o IIS por meio do menu **[!UICONTROL Start > Control Panel > Administrative tools]**.
1. No painel **Conexões**, selecione o site criado para a instalação do Adobe Campaign e clique duas vezes em **Editor de configuração** no painel principal.
1. Na lista suspensa **Section**, selecione **system.webServer** > **httpErrors**.
1. Selecione o valor **PassThrough** na linha **existingResponse**.

![](assets/ins_iis_httperrors.png)
