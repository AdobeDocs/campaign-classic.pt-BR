---
product: campaign
title: Criação de uma instância e fazer logon
description: Criação de uma instância e fazer logon
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 0db6f107d2c161b07f42dcf7a932d319130b31e0
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 9%

---

# Criação de uma instância e fazer logon{#creating-an-instance-and-logging-on}



Para criar uma nova instância e um banco de dados Adobe Campaign, siga as etapas abaixo:

1. Crie a conexão.
1. Faça logon para criar a instância relacionada.
1. Crie e configure o banco de dados.

>[!NOTE]
>
>Somente o identificador **interno** pode realizar estas operações. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).

Quando o console Adobe Campaign é inicializado, você acessa uma página de logon.

Para criar uma nova instância, siga as etapas abaixo:

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração de conexão. Este link pode ser **[!UICONTROL New...]** ou um nome de instância existente.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Clique em **[!UICONTROL Add > Connection]** e insira o rótulo e o URL do servidor de aplicativos do Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique uma conexão com o servidor de aplicativos do Adobe Campaign por meio de um URL. Use um DNS, um alias do computador ou seu endereço IP.

   Por exemplo, você pode usar o URL do tipo `https://<machine>.<domain>.com`.

   >[!CAUTION]
   >
   >Para a URL de conexão, use apenas os seguintes caracteres: `[a-z]`, `[A-Z]`, `[0-9]` e traços (-) ou paradas completas.

1. Clique em **[!UICONTROL Ok]** para confirmar as configurações: agora você pode começar com o processo de criação da instância.
1. Na janela **[!UICONTROL Connection settings]**, digite o logon **interno** e sua senha para se conectar ao servidor de aplicativos do Adobe Campaign. Depois de conectado, você acessa o assistente de criação de instâncias para declarar uma nova instância
1. No campo **[!UICONTROL Name]**, digite o **nome da instância**. Como esse nome é usado para gerar um arquivo de configuração **config-`<instance>`.xml** e é usado nos parâmetros de linha de comando para identificar a instância, escolha um nome curto sem caracteres especiais. Por exemplo: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   O nome da instância adicionado ao nome de domínio não deve exceder 40 caracteres. Isso permite restringir o tamanho dos cabeçalhos &quot;Message-ID&quot; e impede que as mensagens sejam consideradas spam, principalmente por ferramentas como o SpamAssassin.

1. Nos campos **[!UICONTROL DNS masks]**, insira a **lista de máscaras DNS** às quais a instância deve ser anexada. O servidor do Adobe Campaign usa o nome do host que aparece nas solicitações HTTP para determinar qual instância deve ser acessada.

   O nome do host está contido entre a cadeia de caracteres **https://** e o primeiro caractere de barra **/** do endereço do servidor.

   Você pode definir uma lista de valores separados por vírgulas.

   O ? e &#42; caracteres podem ser usados como curingas para substituir um ou vários caracteres (DNS, porta, etc.). Por exemplo, o valor **demo&#42;** funcionará com &quot;https://demo&quot;, como funcionará com &quot;https://demo:8080&quot; e até mesmo &quot;https://demo2&quot;.

   Os nomes usados devem ser definidos no DNS. Você também pode informar a correspondência entre um nome DNS e um endereço IP no arquivo **c:/windows/system32/drivers/etc/hosts** no Windows e no arquivo **/etc/hosts** no Linux. Portanto, você deve modificar as configurações de conexão para usar esse nome DNS a fim de se conectar à instância escolhida.

   O servidor deve ser identificado por esse nome, especialmente para carregar imagens em emails.

   Além disso, o servidor deve ser capaz de se conectar a si mesmo por esse nome e, se possível, por um endereço de loopback - 127.0.0.1 -, especialmente para permitir que os relatórios sejam exportados no formato PDF.

1. Na lista suspensa **[!UICONTROL Language]**, selecione o **idioma da instância**: inglês (EUA), inglês (Reino Unido), francês ou japonês.

   As diferenças entre o inglês dos EUA e o inglês do Reino Unido estão descritas na [documentação do Campaign v8 (console)](.https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui).

   >[!CAUTION]
   >
   >O idioma da instância não pode ser modificado após essa etapa. As instâncias do Adobe Campaign não são multilíngues: não é possível alternar a interface de um idioma para outro.

1. Clique em **[!UICONTROL Ok]** para confirmar a declaração da instância. Faça logoff e logon novamente para declarar o banco de dados.

   >[!NOTE]
   >
   >A instância pode ser criada na linha de comando. Para obter mais informações, consulte [Linhas de comando](../../installation/using/command-lines.md).
