---
product: campaign
title: Criação de uma instância e fazer logon
description: Criação de uma instância e fazer logon
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 5%

---

# Criação de uma instância e fazer logon{#creating-an-instance-and-logging-on}

![](../../assets/v7-only.svg)

Para criar uma nova instância e o banco de dados do Adobe Campaign, siga as etapas abaixo:

1. Crie a conexão.
1. Faça logon para criar a instância relacionada.
1. Criar e configurar o banco de dados.

>[!NOTE]
>
>Somente o identificador **interno** pode realizar essas operações. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).

Quando o console do Adobe Campaign for iniciado, você acessará uma página de logon.

Para criar uma nova instância, siga as etapas abaixo:

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração da conexão. Esse link pode ser **[!UICONTROL New...]** ou um nome de instância existente.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Clique em **[!UICONTROL Add > Connection]** e insira o rótulo e o URL do servidor de aplicativos do Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique uma conexão com o servidor de aplicativos do Adobe Campaign por meio de um URL. Use um DNS ou um alias da máquina ou seu endereço IP.

   Por exemplo, você pode usar o URL tipo [`https://<machine>.<domain>.com`](https://myserver.adobe.com).

   >[!CAUTION]
   >
   >Para o URL de conexão, use apenas os seguintes caracteres: `[a-z]`, `[A-Z]`, `[0-9]` e traços (-) ou paradas completas.

1. Clique em **[!UICONTROL Ok]** para confirmar as configurações: agora é possível começar com o processo de criação da instância.
1. Na janela **[!UICONTROL Connection settings]**, digite o login **interno** e sua senha para se conectar ao servidor de aplicativos do Adobe Campaign. Depois de conectado, você acessa o assistente de criação de instâncias para declarar uma nova instância
1. No campo **[!UICONTROL Name]**, insira o **nome da instância**. Como esse nome é usado para gerar um arquivo de configuração **config-`<instance>`.xml** e é usado nos parâmetros da linha de comando para identificar a instância, certifique-se de escolher um nome curto sem caracteres especiais. Por exemplo: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   O nome da instância adicionada ao nome de domínio não deve exceder 40 caracteres. Isso permite que você restrinja o tamanho dos cabeçalhos de &quot;ID de mensagem&quot; e impede que as mensagens sejam consideradas spam, especialmente por ferramentas como o SpamAssassin.

1. Nos campos **[!UICONTROL DNS masks]** , insira a **lista de máscaras de DNS** à qual a instância deve ser anexada. O servidor do Adobe Campaign usa o nome do host que aparece nas solicitações HTTP para determinar qual instância alcançar.

   O nome do host está contido entre a sequência **https://** e o primeiro caractere de barra **/** do endereço do servidor.

   É possível definir uma lista de valores separados por vírgulas.

   Os ? e * caracteres podem ser usados como curingas para substituir um ou vários caracteres (DNS, porta etc.). Por exemplo, o valor **demo*** funcionará com &quot;https://demo&quot;, como funcionará com &quot;https://demo:8080&quot; e até com &quot;https://demo2&quot;.

   Os nomes usados devem ser definidos no DNS. Você também pode informar a correspondência entre um nome DNS e um endereço IP no arquivo **c:/windows/system32/drivers/etc/hosts** no Windows e no arquivo **/etc/hosts** no Linux. Portanto, você deve modificar as configurações de conexão para usar esse nome DNS para se conectar à instância escolhida.

   O servidor deve ser identificado por esse nome, especialmente para carregar imagens em emails.

   Além disso, o servidor deve ser capaz de se conectar a si mesmo com esse nome e, se possível, por um endereço de loopback - 127.0.0.1 -, especialmente para permitir que os relatórios sejam exportados no formato PDF.

1. Na lista suspensa **[!UICONTROL Language]**, selecione o **idioma da instância**: Inglês (EUA), inglês (Reino Unido), francês ou japonês.

   As diferenças entre inglês americano e inglês do Reino Unido estão descritas em [this section](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >O idioma da instância não pode ser modificado após essa etapa. As instâncias do Adobe Campaign não são multilíngues: não é possível alternar a interface de um idioma para outro.

1. Clique em **[!UICONTROL Ok]** para confirmar a declaração da instância. Faça logoff e volte para declarar o banco de dados.

   >[!NOTE]
   >
   >A instância pode ser criada a partir da linha de comando. Para obter mais informações, consulte [Linhas de comando](../../installation/using/command-lines.md).
