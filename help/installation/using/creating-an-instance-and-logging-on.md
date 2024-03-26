---
product: campaign
title: Criação de uma instância e fazer logon
description: Criação de uma instância e fazer logon
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 2%

---

# Criação de uma instância e fazer logon{#creating-an-instance-and-logging-on}



Para criar uma nova instância e um banco de dados Adobe Campaign, siga o seguinte processo:

1. Criar a conexão.
1. Faça logon para criar o instância relacionado.
1. Criar e configurar o banco de dados.

>[!NOTE]
>
>Somente o **identificador interno** pode executar essas operações. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).

Quando o console do Adobe Campaign é iniciado, você acessa uma fazer logon página.

Para criar uma nova instância, siga as etapas abaixo:

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração de conexão. Esse link pode ser **[!UICONTROL New...]** ou um nome de instância existente.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Clique em **[!UICONTROL Add > Connection]** e insira o rótulo e o URL do servidor de aplicativos do Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique uma conexão com o servidor de aplicativos Adobe Campaign por meio de um URL. Use um DNS ou um alias da máquina ou seu endereço IP.

   Por exemplo, você pode usar o `https://<machine>.<domain>.com` tipo URL.

   >[!CAUTION]
   >
   >Para o URL de conexão, use apenas os seguintes caracteres: `[a-z]`, `[A-Z]`e `[0-9]` dashes (-) ou paradas completas.

1. Clique **[!UICONTROL Ok]** para confirmar as configurações: agora você pode começar com o processo instância de criação.
1. **[!UICONTROL Connection settings]** Na janela, insira a **fazer logon interna** e sua senha para se conectar ao servidor Adobe Campaign aplicativo. Depois de conectado, você acessa a criação de instância assistente para declarar uma nova instância
1. **[!UICONTROL Name]** No campo, insira o nome **da** instância. Como esse nome é usado para gerar um arquivo **de configuração com .xml** e é usado nos parâmetros da linha de comando para identificar o instância, certifique-se`<instance>` de escolher um nome curto sem caracteres especiais. Por exemplo: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   O nome da instância adicionado ao nome de domínio não deve exceder 40 caracteres. Isso permite restringir o tamanho dos cabeçalhos &quot;Message-ID&quot; e impede que as mensagens sejam consideradas spam, principalmente por ferramentas como o SpamAssassin.

1. No **[!UICONTROL DNS masks]** insira o **lista de máscaras de DNS** ao qual a instância deve ser anexada. O servidor do Adobe Campaign usa o nome do host que aparece nas solicitações HTTP para determinar qual instância deve ser acessada.

   O nome do host está entre a cadeia de caracteres **https://** e o primeiro caractere barra **/** do endereço do servidor.

   É possível definir uma lista de valores separados por vírgulas.

   O? e &#42; os caracteres podem ser usados como curingas para substituir um ou vários caracteres (DNS, porta etc.). Por instância, o **valor de demonstração&#42;** funcionará com &quot;https://demo&quot;, como funcionará com &quot;https://demo:8080&quot; e até mesmo &quot;https://demo2&quot;.

   Os nomes usados devem ser definidos no DNS. Você também pode informar a correspondência entre um nome DNS e um endereço IP no **arquivo c:/windows/system32/drivers/etc/hosts** no Windows e no **arquivo /etc/hosts** no Linux. Portanto, você deve modificar as configurações de conexão para usar esse nome de DNS no solicitar para se conectar ao instância escolhido.

   O servidor deve ser identificado por esse nome, especialmente para carregar imagens em emails.

   Além disso, o servidor deve ser capaz de se conectar a si mesmo por esse nome e, se possível, por um endereço de loopback - 127.0.0.1 -, especialmente para permitir que os relatórios sejam exportados no formato PDF.

1. No **[!UICONTROL Language]** , selecione a **idioma da instância**: inglês (EUA), inglês (Reino Unido), francês ou japonês.

   As diferenças entre inglês dos EUA e inglês do Reino Unido estão descritas em [nesta seção](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >O idioma da instância não pode ser modificado após essa etapa. As instâncias do Adobe Campaign não são multilíngues: não é possível alternar a interface de um idioma para outro.

1. Clique **[!UICONTROL Ok]** para confirmar instância declaração. Faça logoff e volte a declarar o banco de dados.

   >[!NOTE]
   >
   >A instância pode ser criada a partir da linha de comando. Para obter mais informações, consulte [Comando linhas](../../installation/using/command-lines.md).
