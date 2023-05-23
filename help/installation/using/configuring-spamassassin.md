---
product: campaign
title: Configuração do SpamAssassin
description: Configuração do SpamAssassin
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 2%

---

# Configuração do SpamAssassin{#configuring-spamassassin}



>[!NOTE]
>
>Algumas configurações só podem ser executadas por Adobe para implantações hospedadas por Adobe. Por exemplo, para acessar os arquivos de configuração do servidor e da instância. Para saber mais sobre as diferentes implantações, consulte o [Modelos de hospedagem](../../installation/using/hosting-models.md) ou para [esta página](../../installation/using/capability-matrix.md).

## Visão geral {#overview}

O SpamAssassin é um software criado para filtrar emails indesejáveis. Em conjunto com esse software, o Adobe Campaign pode atribuir uma pontuação aos emails e determinar se uma mensagem provavelmente será considerada indesejável antes que o delivery seja iniciado. Para fazer isso, o SpamAssassin deve ser instalado e configurado no(s) servidor(es) de aplicativos do Adobe Campaign e requer um determinado número de módulos Perl adicionais para operar.

A implantação e a integração do SpamAssassin, conforme descrito neste capítulo, baseiam-se na instalação de software padrão, bem como nas regras de filtragem e pontuação, que são as fornecidas pelo SpamAssassin sem qualquer alteração ou otimização. A atribuição de pontuação e a qualificação de mensagem baseiam-se exclusivamente na configuração das opções do SpamAssassin e nas regras de filtragem. Os administradores de rede são responsáveis por adaptá-los às necessidades de sua empresa.

>[!IMPORTANT]
>
>A qualificação de emails como indesejáveis pelo SpamAssassin é baseada inteiramente nas regras de filtragem e pontuação.
>
>Portanto, essas regras precisam ser atualizadas pelo menos uma vez por dia para que sua instalação do SpamAssassin e sua integração no Adobe Campaign funcionem plenamente e para garantir a relevância das pontuações atribuídas a seus deliveries antes do envio.
>
>Essa atualização é responsabilidade do administrador do servidor que hospeda o SpamAssassin.

O uso do SpamAssassin no Adobe Campaign fornece uma indicação sobre o possível comportamento de servidores de e-mail que usam o SpamAssassin quando recebem e-mails enviados pelo Adobe Campaign. No entanto, é possível que os servidores de e-mail de provedores de Internet ou servidores de e-mail on-line ainda considerem as mensagens enviadas pelo Adobe Campaign como indesejáveis.

A implantação do SpamAssassin e seus módulos em Perl requer servidores de aplicativos Adobe Campaign equipados com acesso à Internet por meio de uma conexão HTTP (fluxo TCP/80).

## Instalando em um computador com Windows {#installing-on-a-windows-machine}

Para instalar e configurar o SpamAssassin no Windows e habilitar a integração com o Adobe Campaign, siga as etapas abaixo:

1. Instalar o SpamAssassin
1. Integrar o SpamAssassin ao Adobe Campaign

### Instalação do SpamAssassin {#installing-spamassassin}

1. Conecte-se à [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) usando suas credenciais de usuário. Saiba mais sobre a Distribuição de software em [esta página](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=pt-BR).
1. Baixe o **Neolane Spam Assassin (Instalação do Windows) (2.0)** arquivo (neolane_spamassassin.2.0.zip).
1. Copie esse arquivo no servidor do Adobe Campaign e descompacte-o.

   >[!NOTE]
   >
   >Você pode optar por descompactar o arquivo onde quiser, desde que o caminho seja composto de qualquer um dos seguintes caracteres de expressão regular: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. O caminho de instalação não deve incluir espaços em branco.

1. Vá para o arquivo em que você descompactou o arquivo e clique duas vezes na tag **run_me.bat** arquivo para iniciar o script de instalação.

   Se um Shell do Windows for exibido e continuar sendo exibido por alguns segundos, aguarde a conclusão da instalação e da atualização e clique em **Enter**.

   Se o Shell do Windows não aparecer ou não for exibido antes de desaparecer instantaneamente, siga estas etapas, clique duas vezes na guia **portableShell.bat** arquivo para exibir um Shell do Windows e verificar se o caminho do Shell corresponde à pasta na qual o **spamassassin.zip** o arquivo foi descompactado. Se esse não for o caso, acesse-o usando o **cd** comando.

   Enter **run_me.bat** e clique em **Enter** para iniciar o processo de instalação e atualização. A operação retorna um dos seguintes valores para indicar o resultado da atualização.

   * **0**: uma atualização foi realizada.
   * **1**: nenhuma atualização nova disponível.
   * **2**: nenhuma atualização nova disponível.
   * **3**: falha na atualização durante a verificação anterior.
   * **4** ou mais: ocorreu um erro.

1. Para verificar se a instalação do SpamAssassin foi bem-sucedida, use o teste GTUBE (Teste genérico para e-mail em massa não solicitado) usando o seguinte procedimento:

   1. Crie um arquivo de texto e salve-o em **C:\TestSpamMail.txt**.
   1. Insira o seguinte conteúdo no arquivo:

      ```
      Subject: Test Spam Mail (GTUBE)
      Message-ID: <1010101@example.net>
      Date: MM-DD-YY
      From: Sender <sender@example.net>
      To: Recipient <recipient@example.net>
      Precedence: junk
      MIME-Version: 1.0
      Content-Type: text/plain; charset=us-ascii
      Content-Transfer-Encoding: 7bit
      
      XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
      ```

   1. Clique duas vezes na guia **portableShell.bat** para exibir um Shell do Windows, inicie o seguinte comando (ou &quot;`<root>`&quot; designa a pasta criada ao descompactar o  **spamassassin.zip** arquivo):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      O conteúdo desse email de teste aciona uma pontuação de 1.000 pontos pelo SpamAssassin. Isso significa que foi detectado como indesejável e que a instalação foi bem-sucedida e está totalmente funcional.

### Integração do SpamAssassin ao Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Edite o **`[INSTALL]/conf/serverConf.xml`** arquivo. Todos os parâmetros disponíveis no **serverConf.xml** estão listados neste [seção](../../installation/using/the-server-configuration-file.md).
1. Altere o valor de **spamCheck** elementos&#39; **comando** atributo no **Web** nó. Para fazer isso, execute o seguinte comando:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Todos os caminhos devem ser absolutos.

   Pare e inicie o **[!UICONTROL Adobe Campaign]** serviço.

1. Para verificar a integração do SpamAssassin no Adobe Campaign, use um teste GTBUE (Teste genérico para emails em massa não solicitados):

   Clique duas vezes na guia **portableshell.bat** arquivo. Isso aciona a exibição de um Shell do Windows. Em seguida, execute o seguinte comando:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   O conteúdo deste email de teste aciona 1.000 pontos atribuídos pelo SpamAssassin. Isso significa que foi detectado como indesejável e que a integração no Adobe Campaign foi bem-sucedida e está totalmente funcional.

1. Atualizar regras de pontuação e filtragem do SpamAssassin

   Para obter uma atualização inicial das regras de filtragem e pontuação, comece **portableShell.bat** e execute o seguinte comando:

   ```
   sa-update --no-gpg
   ```

   Para executar uma atualização automática de regras de filtragem e pontuação, use este mesmo comando em uma tarefa do sistema programada:

   ```
   sa-update --no-gpg
   ```

## Instalando em uma máquina Linux {#installing-on-a-linux-machine}

### Etapas de instalação no Debian {#installation-steps-in-debian}

* Se necessário, instale o Perl e o SpamAssassin usando o seguinte comando:

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* No **serverConf.xml** arquivo (disponível em `/usr/local/[INSTALL]/nl6/conf/`), altere o **spamCheck** seguinte linha:

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### Etapas de instalação no RHEL/CentOS {#installation-steps-in-rhel-centos}

Se necessário, instale o Perl e recupere os pacotes usando CPAN:

```
cpan Digest::SHA1
cpan HTML::Parser
cpan Net::DNS
cpan Mail::SPF 
cpan XML::LibXML
cpan XML::Writer
cpan Mail::SpamAssassin
```

### Atualizando regras de filtro {#updating-filter-rules}

As regras de filtro podem ser atualizadas automaticamente usando o **sa-update** ferramenta. Consulte o site oficial do SpamAssassin [https://spamassassin.apache.org/](https://spamassassin.apache.org/) para obter mais informações.

No Debian, as atualizações ocorrem automaticamente todos os dias.

Se esse não for o caso (por exemplo, quando o Debian for instalado manualmente), crie um script para automatizar as atualizações de regras.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Inserir este script em **crontab** usando o seguinte comando:

```
crontab-e
```

### Otimização do desempenho {#performance-optimization}

Para melhorar o desempenho no Linux, edite o **/etc/spamassassin/local.cf** e adicione a seguinte linha no final do arquivo:

```
dns_available no
```
