---
product: campaign
title: Integração em um servidor Web para Windows
description: Integração em um servidor Web para Windows
feature: Installation, Instance Settings
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 4%

---

# Integração em um servidor Web para Windows {#integration-into-a-web-server-for-windows}

O Adobe Campaign inclui o Apache Tomcat, que atua como ponto de entrada no servidor de aplicativos via HTTP (e SOAP).

Você pode usar esse servidor Tomcat integrado para atender a solicitações HTTP.

Neste caso:

* a porta de escuta padrão é 8080. Para alterá-lo, consulte [esta seção](../../installation/using/configure-tomcat.md).
* Os consoles clientes se conectam usando uma URL como ```https:// `<computer>`:8080```.

No entanto, por motivos de segurança e administração, recomendamos usar um servidor Web dedicado como principal ponto de entrada para o tráfego HTTP quando o computador que executa o Adobe Campaign estiver exposto na Internet e você desejar abrir o acesso ao console fora da rede.

Um servidor da Web também permite garantir a confidencialidade dos dados com o protocolo HTTPs.

Da mesma forma, você deve usar um servidor Web quando quiser usar a funcionalidade de rastreamento, que está disponível somente como um módulo de extensão de servidor Web.

## Configuração do servidor Web IIS {#configuring-the-iis-web-server}

O procedimento de configuração de um servidor Web Microsoft IIS é, em sua maioria, gráfico. Envolve o uso de um site para acessar os recursos do servidor do Adobe Campaign: arquivos Java (.jsp), folhas de estilos (.css, .xsl), imagens (.png), a DLL ISAPI para redirecionamento, etc.


### Etapas de configuração {#configuration-steps}

Para integrar o Adobe Campaign ao servidor Web do Microsoft IIS, siga estas etapas:

1. Abra o Microsoft IIS.
1. Crie e configure o site (Adobe Campaign, por exemplo) dependendo dos parâmetros da sua rede (porta de conexão TCP, host DNS, endereço IP).

   Especifique pelo menos o nome do site e o caminho de acesso para o diretório virtual. Como o caminho para acessar o diretório Website não é usado, você pode usar o seguinte diretório.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. Um script **VBS** permite configurar automaticamente os recursos usados pelo servidor Adobe Campaign no diretório virtual que acabamos de criar. Para iniciá-lo, clique duas vezes no arquivo **iis_neolane_setup.vbs** localizado na pasta `[INSTALL]\conf`, onde `[INSTALL]` é o caminho para acessar a pasta de instalação do Adobe Campaign.

   >[!NOTE]
   >
   >Você deve estar conectado como administrador para executar o script do VBS ou executar o script como administrador.

   Clique em **[!UICONTROL OK]** se o servidor Web for usado como um servidor de redirecionamento de rastreamento. Caso contrário, clique em **[!UICONTROL Cancel]**.

   Quando vários sites já estiverem configurados no servidor Web, uma página intermediária será exibida para especificar a qual site a instalação se aplica: digite o número vinculado ao site e clique em **[!UICONTROL OK]**.

1. Na guia **[!UICONTROL Content View]**, verifique se o site está configurado corretamente com os recursos do Adobe Campaign:

   Se a árvore não for exibida, reinicie o Microsoft IIS.

### Gerenciamento de direitos {#managing-rights}

Em seguida, defina as configurações de segurança para a DLL ISAPI e para os recursos no diretório de instalação do Adobe Campaign.

Para fazer isso, siga as etapas abaixo:

1. Selecione a guia **[!UICONTROL Features View]** e clique duas vezes no link **Autenticação**.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. Na guia **Segurança de Diretório** do site, verifique se o acesso anônimo está habilitado. Se necessário, clique no link **[!UICONTROL Edit]** para alterar as configurações.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Iniciar o servidor Web e testar a configuração {#launching-the-web-server-and-testing-the-configuration}

Agora você deve testar se a configuração está correta.

Para fazer isso, siga o procedimento abaixo:

1. Reinicie o servidor do Microsoft IIS usando a linha de comando **iisreset**.

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

```sql
HH:MM:SS >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

Você também pode verificar se a DLL ISAPI está carregada corretamente.

Para fazer isso, siga as etapas abaixo:

1. Edite os filtros ISAPI para o site do Adobe Campaign clicando no ícone **[!UICONTROL Driver mapping]**.
1. A verificação do conteúdo do filtro ISAPI.


## Alterar o limite de tamanho do arquivo de upload {#changing-the-upload-file-size-limit}

Ao configurar o servidor Web IIS, um limite de aproximadamente 28 MB é automaticamente definido para arquivos definidos que são carregados no servidor.

Isso pode ter um impacto no Adobe Campaign, especialmente se você quiser carregar arquivos maiores que esse limite.

Por exemplo, se você usar uma atividade do tipo **Carregamento de dados (arquivo)** em um fluxo de trabalho para importar um arquivo de 50 MB, um erro impedirá que o fluxo de trabalho seja executado corretamente.

Nesse caso, você deve aumentar esse limite.

Para obter mais informações sobre esta opção do Microsoft IIS, consulte a seção &quot;Como&quot; da [documentação do Microsoft](https://learn.microsoft.com/en-us/iis/configuration/system.webServer/security/requestFiltering/requestLimits/){target="_blank"}.

