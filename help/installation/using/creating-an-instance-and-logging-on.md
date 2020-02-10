---
title: Criação de uma instância e logon
seo-title: Criação de uma instância e logon
description: Criação de uma instância e logon
seo-description: null
page-status-flag: never-activated
uuid: cb1620b3-f6e8-41dc-9142-ac0da65b6f8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: c7395094-c635-45ab-8455-a050f7d16b64
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Criação de uma instância e logon{#creating-an-instance-and-logging-on}

Para criar uma nova instância e o banco de dados do Adobe Campaign, aplique o seguinte processo:

1. Crie a conexão.
1. Faça logon para criar a instância relacionada.
1. Crie e configure o banco de dados.

>[!NOTE]
>
>Somente o identificador **interno** pode realizar essas operações. For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

Quando o console do Adobe Campaign é iniciado, você acessa uma página de logon.

Para criar uma nova instância, siga as etapas abaixo:

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração da conexão. Esse link pode ser **[!UICONTROL New...]** ou um nome de instância existente.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Clique **[!UICONTROL Add > Connection]** e insira o rótulo e o URL do servidor de aplicativos do Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique uma conexão com o servidor de aplicativos do Adobe Campaign por meio de um URL. Use um DNS ou um alias da máquina ou seu endereço IP.

   Por exemplo, você pode usar o [`https://<machine>.<domain>.com`](https://machine) tipo URL.

   >[!CAUTION]
   >
   >Para o URL de conexão, use apenas os seguintes caracteres: `[a-z]`, `[A-Z]``[0-9]` e traços (-) ou paradas completas.

1. Clique **[!UICONTROL Ok]** para confirmar as configurações: agora você pode começar com o processo de criação da instância.
1. Na **[!UICONTROL Connection settings]** janela, digite o logon **interno** e sua senha para se conectar ao servidor de aplicativos do Adobe Campaign. Depois de conectado, acesse o assistente de criação de instâncias para declarar uma nova instância
1. No **[!UICONTROL Name]** campo, informe o nome **da** instância. Como esse nome é usado para gerar um arquivo de configuração **config-`<instance>`.xml** e é usado nos parâmetros da linha de comando para identificar a instância, escolha um nome curto sem caracteres especiais. Por exemplo: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   O nome da instância adicionada ao nome de domínio não deve exceder 40 caracteres. Isso permite restringir o tamanho dos cabeçalhos &quot;ID da mensagem&quot; e impedir que as mensagens sejam consideradas spam, principalmente por ferramentas como o SpamAssassin.

1. Nos **[!UICONTROL DNS masks]** campos, informe a **lista de máscaras** DNS à qual a instância deve ser anexada. O servidor do Adobe Campaign usa o nome do host que aparece nas solicitações HTTP para determinar qual instância acessar.

   O nome do host está contido entre a string **https://** e o primeiro caractere de barra **/** do endereço do servidor.

   É possível definir uma lista de valores separados por vírgulas.

   O quê? e * caracteres podem ser usados como curingas para substituir um ou vários caracteres (DNS, porta etc.). Por exemplo, o valor da **demonstração*** funcionará com &quot;https://demo&quot;, assim como funcionará com &quot;https://demo:8080&quot; e até mesmo com &quot;https://demo2&quot;.

   Os nomes usados devem ser definidos no DNS. Você também pode informar a correspondência entre um nome DNS e um endereço IP no arquivo **c:/windows/system32/drivers/etc/hosts** no Windows e no arquivo **/etc/hosts** no Linux. Portanto, você deve modificar as configurações de conexão para usar esse nome DNS a fim de se conectar à instância escolhida.

   O servidor deve ser identificado por esse nome, especialmente para carregar imagens em emails.

   Além disso, o servidor deve ser capaz de se conectar a si mesmo por esse nome e, se possível, por um endereço de loopback - 127.0.0.1 -, especialmente para permitir que os relatórios sejam exportados no formato PDF.

1. Na lista **[!UICONTROL Language]** suspensa, selecione o idioma **da** instância: Inglês (EUA), inglês (Reino Unido), francês ou japonês.

   As diferenças entre o inglês dos EUA e o inglês do Reino Unido são descritas na [presente seção](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >O idioma da instância não pode ser modificado após esta etapa. As instâncias do Adobe Campaign não são multilíngues: não é possível alternar a interface de um idioma para outro.

1. Clique em **[!UICONTROL Ok]** para confirmar a declaração da instância. Faça logoff e volte a fazer logon para declarar o banco de dados.

   >[!NOTE]
   >
   >A instância pode ser criada na linha de comando. For more on this, refer to [Command lines](../../installation/using/command-lines.md).

