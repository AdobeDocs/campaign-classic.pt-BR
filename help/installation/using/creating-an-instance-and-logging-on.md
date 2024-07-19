---
product: campaign
title: Criação de uma instância e fazer logon
description: Criação de uma instância e fazer logon
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 1%

---

# Criação de uma instância e fazer logon{#creating-an-instance-and-logging-on}



Para criar uma nova instância e um banco de dados Adobe Campaign, siga as etapas abaixo:

1. Crie a conexão.
1. Faça logon para criar a instância relacionada.
1. Crie e configure o banco de dados.

>[!NOTE]
>
>Somente o **identificador interno** pode realizar essas operações. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).

Quando o console do Adobe Campaign é iniciado, você acessa uma página de logon.

Para criar uma nova instância, siga as etapas abaixo:

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração de conexão. Este link pode ser **[!UICONTROL New...]** ou um nome de instância existente.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Clique em **[!UICONTROL Add > Connection]** e insira o rótulo e a URL do servidor de aplicativos do Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique uma conexão com o servidor de aplicativos Adobe Campaign por meio de um URL. Use um DNS ou um alias da máquina, ou seu endereço IP.

   Por exemplo, você pode usar o URL do tipo `https://<machine>.<domain>.com`.

   >[!CAUTION]
   >
   >Para o URL de conexão, use somente os seguintes caracteres: `[a-z]`e `[A-Z]``[0-9]` traços (-) ou paradas completas.

1. Clique **[!UICONTROL Ok]** para confirmar as configurações: agora é possível começar com o processo de criação da instância.
1. **[!UICONTROL Connection settings]** Na janela, insira o **logon interno** e sua senha para se conectar ao servidor de aplicativos do Adobe Campaign. Depois de conectado, você acessa o assistente de criação de ocorrência para declarar uma nova instância
1. **[!UICONTROL Name]** No campo, digite o nome **da** instância. Como esse nome é usado para gerar uma configuração de arquivo **de configuração .xml** e é usado nos parâmetros de linha de comando para identificar a instância, certifique-se`<instance>` de escolher um nome curto sem caracteres especiais. Por exemplo: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   O nome da instância adicionada ao nome do domínio não deve exceder 40 caracteres. Isso permite restringir o tamanho dos cabeçalhos de &quot;ID da mensagem&quot; e impede que as mensagens sejam consideradas como spam, particularmente por ferramentas como SpamAssassin.

1. **[!UICONTROL DNS masks]** Nos campos, insira a **lista de máscaras** DNS às quais a instância deve ser anexada. O servidor do Adobe Campaign usa o nome do host que aparece nas solicitações HTTP para determinar qual instância deve ser acessada.

   O nome do host está contido entre a cadeia de caracteres **https://** e o primeiro caractere de barra **/** do endereço do servidor.

   Você pode definir uma lista de valores separados por vírgulas.

   O ? e &#42; os caracteres podem ser usados como caracteres curingas para substituir um ou vários caracteres (DNS, porta etc.). Por exemplo, o **valor de demonstração&#42;** funcionará com &quot;https://demo&quot;, como fará com &quot;https://demo:8080&quot; e até &quot;https://demo2&quot;.

   Os nomes usados devem ser definidos em seu DNS. Também é possível informar a correspondência entre um nome DNS e um endereço IP no **arquivo c:/windows/system32/drivers/etc/hosts** no Windows e no **arquivo /etc/hosts** no Linux. Portanto, você deve modificar as configurações de conexão para usar esse nome DNS para conectar-se à instância escolhida.

   O servidor deve ser identificado por esse nome, principalmente para carregar imagens em emails.

   Além disso, o servidor deve ser capaz de se conectar a ele mesmo por esse nome e, se possível, por um endereço de loopback - 127.0.0.1 - particularmente para permitir que os relatórios sejam exportados no formato PDF.

1. **[!UICONTROL Language]** Na lista suspensa, selecione o idioma **da** instância: inglês (EUA), inglês (Reino Unido), francês ou japonês.

   As diferenças entre inglês americano e inglês do Reino Unido estão descritas em [esta seção](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >O idioma da instância não pode ser modificado após essa etapa. As instâncias do Adobe Campaign não são multilíngues: não é possível alternar a interface de um idioma para outro.

1. Clique em **[!UICONTROL Ok]** para confirmar a declaração da instância. Faça logoff e logon novamente para declarar o banco de dados.

   >[!NOTE]
   >
   >A instância pode ser criada na linha de comando. Para saber mais sobre isso, consulte as [linhas](../../installation/using/command-lines.md) de Comando.
