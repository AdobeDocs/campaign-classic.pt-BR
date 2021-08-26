---
product: campaign
title: Configuração do SpamAssassin
description: Configuração do SpamAssassin
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 2%

---

# Configuração do SpamAssassin{#configuring-spamassassin}

![](../../assets/v7-only.svg)

>[!NOTE]
>
>Algumas configurações só podem ser executadas pelo Adobe para implantações hospedadas pelo Adobe. Por exemplo, para acessar os arquivos de configuração do servidor e da instância. Para saber mais sobre as diferentes implantações, consulte a seção [Modelos de hospedagem](../../installation/using/hosting-models.md) ou [esta página](../../installation/using/capability-matrix.md).

## Visão geral {#overview}

O SpamAssassin é um software projetado para filtrar emails indesejáveis. Junto com esse software, o Adobe Campaign pode atribuir uma pontuação aos emails e determinar se uma mensagem provavelmente será considerada indesejável antes que o delivery seja iniciado. Para isso, o SpamAssassin deve ser instalado e configurado no(s) servidor(es) de aplicativos do Adobe Campaign e requer um determinado número de módulos Perl adicionais para operar.

A implantação e integração do SpamAssassin, conforme descrito neste capítulo, são baseadas na instalação padrão do software, assim como nas regras de filtragem e pontuação, que são fornecidas pelo SpamAssassin sem quaisquer alterações ou otimizações. A atribuição de pontuação e a qualificação de mensagem se baseiam exclusivamente na configuração das opções do SpamAssassin e nas regras de filtragem. Os administradores de rede são responsáveis por adaptá-los às necessidades de sua empresa.

>[!IMPORTANT]
>
>A qualificação de emails como indesejáveis pelo SpamAssassin é baseada inteiramente em regras de filtragem e pontuação.
>
>Essas regras devem, portanto, ser atualizadas pelo menos uma vez por dia para que a instalação do SpamAssassin e sua integração no Adobe Campaign sejam totalmente funcionais e garantam a relevância das pontuações atribuídas aos seus deliveries antes de enviá-los.
>
>Esta atualização é da responsabilidade do administrador do servidor que hospeda o SpamAssassin.

O uso do SpamAssassin no Adobe Campaign fornece uma indicação sobre o possível comportamento dos servidores de e-mail que usam o SpamAssassin quando recebem e-mail enviado pelo Adobe Campaign. No entanto, é possível que os servidores de email de provedores de Internet ou servidores de email online ainda considerem as mensagens enviadas pelo Adobe Campaign como indesejáveis.

A implantação do SpamAssassin e de seus módulos no Perl requer servidores de aplicativos Adobe Campaign equipados com acesso à Internet por meio de uma conexão HTTP (fluxo TCP/80).

## Instalar em uma máquina Windows {#installing-on-a-windows-machine}

Para instalar e configurar o SpamAssassin no Windows para habilitar a integração com o Adobe Campaign, siga as etapas abaixo:

1. Instalar o SpamAssassin
1. Integrar o SpamAssassin ao Adobe Campaign

### Instalação do SpamAssassin {#installing-spamassassin}

1. Conecte-se ao [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) usando suas credenciais de usuário. Saiba mais sobre a Distribuição de software em [this page](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=pt-BR?lang=en).
1. Baixe o arquivo **Neolane Spam Assassin (Instalação do Windows) (2.0)** (neolane_spamassassin.2.0.zip).
1. Copie esse arquivo no servidor do Adobe Campaign e descompacte-o.

   >[!NOTE]
   >
   >Você pode optar por descompactar o arquivo onde quiser, desde que o caminho seja composto por qualquer um dos seguintes caracteres de expressão regular: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. O caminho de instalação não deve incluir caracteres de espaço em branco.

1. Vá para o arquivo no qual você descompactou o arquivo e clique duas vezes no arquivo **run_me.bat** para iniciar o script de instalação.

   Se um Shell do Windows aparecer e continuar sendo exibido por alguns segundos, aguarde até que a instalação e a atualização terminem e clique em **Enter**.

   Se o Shell do Windows não aparecer ou não for exibido antes de desaparecer instantaneamente, siga estas etapas, clique duas vezes no arquivo **portableShell.bat** para exibir um Shell do Windows e verifique se o caminho do Shell corresponde à pasta na qual o arquivo **spamassassin.zip** foi descompactado. Se esse não for o caso, acesse-o usando o comando **cd**.

   Digite **run_me.bat** e clique em **Enter** para iniciar o processo de instalação e atualização. A operação retorna um dos valores a seguir para indicar o resultado da atualização.

   * **0**: foi efetuada uma atualização.
   * **1**: Nenhuma nova atualização disponível.
   * **2**: nenhuma nova atualização disponível.
   * **3**: a atualização falhou durante a verificação anterior.
   * **4** ou mais: ocorreu um erro.

1. Para verificar se a instalação do SpamAssassin foi bem-sucedida, use o teste GTUBE (Teste Genérico para Email em Massa Não Solicitado) usando o seguinte procedimento:

   1. Crie um arquivo de texto e salve-o em **C:\TestSpamMail.txt**.
   1. Insira o seguinte conteúdo no arquivo :

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

   1. Clique duas vezes no arquivo **portableShell.bat** para exibir um Shell do Windows e inicie o seguinte comando (ou &quot;`<root>`&quot; designa a pasta criada ao descompactar o arquivo **spamassassin.zip**):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      O conteúdo desse email de teste aciona uma pontuação de 1.000 pontos pelo SpamAssassin. Isso significa que ele foi detectado como indesejável e que a instalação foi bem-sucedida e está totalmente funcional.

### Integração do SpamAssassin ao Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Edite o arquivo **`[INSTALL]/conf/serverConf.xml`**. Todos os parâmetros disponíveis no **serverConf.xml** são listados nesta [seção](../../installation/using/the-server-configuration-file.md).
1. Altere o valor do atributo **spamCheck** elements&#39; **command** no nó **Web**. Para fazer isso, execute o seguinte comando:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Todos os caminhos devem ser absolutos.

   Pare e inicie o serviço **[!UICONTROL Adobe Campaign]**.

1. Para verificar a integração do SpamAssassin no Adobe Campaign, use um teste GTBUE (Teste Genérico para Email em Massa Não Solicitado):

   Clique duas vezes no arquivo **portablesinferno.bat**. Isso aciona a exibição de um Shell do Windows. Em seguida, execute o seguinte comando:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   O conteúdo desse email de teste aciona 1.000 pontos atribuídos pelo SpamAssassin. Isso significa que ela foi detectada como indesejável e que a integração no Adobe Campaign foi bem-sucedida e está totalmente funcional.

1. Atualizar regras de filtragem e pontuação do SpamAssassin

   Para obter uma atualização inicial das regras de filtragem e pontuação, inicie **portableShell.bat** e execute o seguinte comando:

   ```
   sa-update --no-gpg
   ```

   Para executar uma atualização automática de regras de filtragem e pontuação, use o mesmo comando em uma tarefa agendada do sistema:

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

### Atualização das regras de filtro {#updating-filter-rules}

As regras de filtro podem ser atualizadas automaticamente usando a ferramenta **sa-update**. Consulte o site oficial do SpamAssassin [http://spamassassin.apache.org/](http://spamassassin.apache.org/) para obter mais informações.

No Debian, as atualizações ocorrem automaticamente a cada dia.

Se esse não for o caso (por exemplo, quando o Debian for instalado manualmente), crie um script para automatizar as atualizações da regra.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Insira esse script em **crontab** usando o seguinte comando:

```
crontab-e
```

### Otimização de desempenho {#performance-optimization}

Para melhorar o desempenho no Linux, edite o arquivo **/etc/spamassassin/local.cf** e adicione a seguinte linha no final do arquivo:

```
dns_available no
```
