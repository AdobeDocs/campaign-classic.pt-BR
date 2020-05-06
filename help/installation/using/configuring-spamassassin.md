---
title: Configuração do SpamAssassin
seo-title: Configuração do SpamAssassin
description: Configuração do SpamAssassin
seo-description: null
page-status-flag: never-activated
uuid: 327548c0-d621-4417-9fc9-b0bf30251dc0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: aa37bdc6-0f85-4eca-859f-e8b15083cfb5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fcedad248169f53e716f2bd8b1b141fbf1f4d189
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 1%

---


# Configuração do SpamAssassin{#configuring-spamassassin}

>[!NOTE]
>
>Algumas configurações só podem ser executadas pela Adobe para implantações hospedadas pela Adobe. Por exemplo, para acessar os arquivos de configuração do servidor e da instância. Para saber mais sobre as diferentes implantações, consulte a seção Modelos [de](../../installation/using/hosting-models.md) hospedagem ou [este artigo](https://helpx.adobe.com/br/campaign/kb/acc-on-prem-vs-hosted.html).

## Visão geral {#overview}

O SpamAssassin é um software projetado para filtrar e-mails indesejáveis. Em conjunto com este software, o Adobe Campaign pode atribuir uma pontuação aos e-mails e determinar se uma mensagem é provavelmente considerada indesejável antes de o delivery ser iniciado. Para isso, o SpamAssassin deve ser instalado e configurado nos servidores de aplicativos do Adobe Campaign e requer um certo número de módulos Perl adicionais para operar.

A implantação e a integração do SpamAssassin, conforme descrito neste capítulo, são baseadas na instalação padrão do software, assim como nas regras de filtragem e pontuação, que são fornecidas pelo SpamAssassin sem qualquer alteração ou otimização. A atribuição de pontuação e a qualificação de mensagem se baseiam exclusivamente na configuração das opções do SpamAssassin e nas regras de filtragem. Os administradores de rede são responsáveis por adaptá-los às suas necessidades de empresa.

>[!IMPORTANT]
>
>A qualificação de emails como indesejados pelo SpamAssassin é baseada inteiramente em regras de filtragem e pontuação.
>
>Essas regras devem, portanto, ser atualizadas pelo menos uma vez por dia para que sua instalação do SpamAssassin e sua integração no Adobe Campaign estejam totalmente funcionais e para garantir a relevância das pontuações atribuídas aos delivery antes do envio.
>
>Esta atualização é da responsabilidade do administrador do servidor que hospeda o SpamAssassin.

O uso do SpamAssassin no Adobe Campaign fornece uma indicação sobre o possível comportamento dos servidores de e-mail que usam o SpamAssassin quando recebem e-mail enviado pelo Adobe Campaign. No entanto, é possível que os servidores de correio dos fornecedores de Internet ou dos servidores de correio eletrônico em linha ainda considerem indesejável as mensagens enviadas pela Adobe Campaign.

A implantação do SpamAssassin e de seus módulos em Perl requer servidores de aplicativos Adobe Campaign equipados com acesso à Internet por uma conexão HTTP (fluxo TCP/80).

## Instalação em uma máquina Windows {#installing-on-a-windows-machine}

Para instalar e configurar o SpamAssassin no Windows para habilitar a integração com o Adobe Campaign, aplique as seguintes etapas:

1. Instalar o SpamAssassin
1. Integrar o SpamAssassin ao Adobe Campaign

### Instalação do SpamAssassin {#installing-spamassassin}

1. Conecte-se ao portal [da](http://support.neolane.net) Extranet usando suas credenciais de usuário.
1. Vá para o Centro **de** download e navegue na página para encontrar a seção **Ferramentas** .
1. Baixe o arquivo **Spam Assassin (Windows Installation) (1.0)** .
1. Copie esse arquivo no servidor Adobe Campaign e depois descompacte-o.

   >[!NOTE]
   >
   >Você pode optar por descompactar o arquivo onde desejar, desde que o caminho seja composto de qualquer um dos seguintes caracteres de expressão comuns: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. O caminho de instalação não deve incluir nenhum caractere de espaço em branco.

1. Vá para o arquivo no qual você descompactou o arquivo e clique no duplo no arquivo **run_me.bat** para iniciar o script de instalação.

   Se um Shell do Windows for exibido e continuar sendo exibido por alguns segundos, aguarde até que a instalação e a atualização sejam concluídas e clique em **Enter**.

   Se o Shell do Windows não aparecer ou não for exibido antes de desaparecer instantaneamente, siga estas etapas, clique com o duplo no arquivo **portableShell.bat** para exibir um Shell do Windows e verifique se o caminho do Shell corresponde à pasta na qual o arquivo **spamkiller.zip** foi descompactado. Se esse não for o caso, acesse-o usando o comando **cd** .

   Digite **run_me.bat** e clique em **Enter** para start do processo de instalação e atualização. A operação retorna um dos valores a seguir para indicar o resultado da atualização.

   * **0**: foi efetuada uma atualização.
   * **1**: Nenhuma nova atualização disponível.
   * **2**: nenhuma nova atualização disponível.
   * **3**: falha na atualização durante a verificação anterior.
   * **4** ou mais: ocorreu um erro.

1. Para verificar se a instalação do SpamAssassin foi bem-sucedida, use o teste GTUBE (Teste genérico para email em massa não solicitado) usando o seguinte procedimento:

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

   1. Duplo-clique no arquivo **portableShell.bat** para exibir um Shell do Windows e depois inicie o seguinte comando (ou &quot;`<root>`&quot; designa a pasta criada ao descompactar o arquivo **spamkiller.zip** ):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      O conteúdo deste email de teste aciona uma pontuação de 1.000 pontos pelo SpamAssassin. Isso significa que foi detectado como indesejável e que a instalação foi bem-sucedida e está totalmente funcional.

### Integração do SpamAssassin no Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Edite o **`[INSTALL]/conf/serverConf.xml`** arquivo. Todos os parâmetros disponíveis no **serverConf.xml** estão listados nesta [seção](../../installation/using/the-server-configuration-file.md).
1. Altere o valor do atributo de **comando** dos elementos **spamCheck** no nó **Web** . Para fazer isso, execute o seguinte comando:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Todos os caminhos devem ser absolutos.

   Pare e start o **[!UICONTROL Adobe Campaign]** serviço.

1. Para verificar a integração do SpamAssassin no Adobe Campaign, use um teste GTBUE (Teste genérico para e-mail em massa não solicitado):

   Clique com o Duplo no arquivo **portablesinfere.bat** . Isso aciona a exibição de uma Shell do Windows. Em seguida, execute o seguinte comando:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   O conteúdo deste email de teste aciona 1.000 pontos atribuídos pelo SpamAssassin. Isso significa que foi detectada como indesejável e que a integração na Adobe Campaign foi bem-sucedida e está totalmente funcional.

1. Atualizar regras de filtragem e pontuação do SpamAssassin

   Para obter uma atualização inicial das regras de filtragem e pontuação, o start **portableShell.bat** e execute o seguinte comando:

   ```
   sa-update --no-gpg
   ```

   Para executar uma atualização automática das regras de filtragem e pontuação, use este mesmo comando em uma tarefa programada do sistema:

   ```
   sa-update --no-gpg
   ```

## Instalação em uma máquina Linux {#installing-on-a-linux-machine}

### Etapas de instalação no Debian {#installation-steps-in-debian}

* Se necessário, instale o Perl e o SpamAssassin usando o seguinte comando:

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* No arquivo **serverConf.xml** (disponível em `/usr/local/[INSTALL]/nl6/conf/`), altere a linha **spamCheck** da seguinte maneira:

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### Etapas de instalação no RHEL/CentOS {#installation-steps-in-rhel-centos}

Se necessário, instale o Perl e recupere os pacotes usando o CPAN:

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

As regras de filtro podem ser atualizadas automaticamente usando a ferramenta **sa-update** . Consulte o site oficial do SpamAssassin [http://spamassassin.apache.org/](http://spamassassin.apache.org/) para obter mais informações.

Em Debian, as atualizações ocorrem automaticamente todos os dias.

Se esse não for o caso (por exemplo, quando Debian é instalado manualmente), crie um script para automatizar as atualizações de regras.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Insira esse script na **crontab** usando o seguinte comando:

```
crontab-e
```

### Otimização do desempenho {#performance-optimization}

Para melhorar o desempenho no Linux, edite o arquivo **/etc/spamassassin/local.cf** e adicione a seguinte linha ao final do arquivo:

```
dns_available no
```

