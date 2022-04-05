---
product: campaign
title: Configuração do servidor do Campaign
description: Configuração do servidor do Campaign
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 294309239bc476669e9e017c27bd1b51a0bdaf8c
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 3%

---

# Introdução à configuração do servidor do Campaign{#gs-campaign-server-config}

![](../../assets/v7-only.svg)

Este capítulo detalha as configurações do lado do servidor que podem ser executadas para atender às suas necessidades e especificidades de ambiente.

## Restrições

Estes procedimentos limitam-se a: **no local**/**híbrido** implantações e requer permissões de administração.

Para **hospedado** implantações, configurações do lado do servidor podem ser configuradas somente pelo Adobe. No entanto, algumas configurações podem ser configuradas no [Painel de controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=pt-BR), como gerenciamento de lista de permissões de IP ou permissões de URL. [Saiba mais](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=pt-BR).

Para obter mais informações, consulte esta seção.

* [Documentação do Painel de controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR)
* [Modelos de hospedagem](../../installation/using/hosting-models.md)
* [Matriz de recursos no local e hospedada do Campaign Classic](../../installation/using/capability-matrix.md)

## Arquivos de configuração

Os arquivos de configuração do Campaign Classic são armazenados no **conf** pasta da pasta de instalação do Adobe Campaign. A configuração é distribuída por dois arquivos:

* **serverConf.xml**: configuração geral para todas as instâncias. Este arquivo combina os parâmetros técnicos do servidor do Adobe Campaign: eles são compartilhados por todas as instâncias. A descrição de alguns desses parâmetros é detalhada abaixo. Os diferentes nós e parâmetros e listados neste [seção](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** em que **instância** é o nome da instância): configuração específica da instância. Se você compartilhar seu servidor entre várias instâncias, insira os parâmetros específicos para cada instância em seu arquivo relevante.

## Escopo de configuração

Configure ou adapte o servidor do Campaign de acordo com suas necessidades e configuração. Você pode:

* Proteja o [Identificador interno](#internal-identifier)
* Habilitar [Processos de campanha](#enabling-processes)
* Configurar [Permissões de URL](url-permissions.md)
* Definir [Zonas de segurança](security-zones.md)
* Configurar [Configurações do Tomcat](configure-tomcat.md)
* Personalizar [Parâmetros de delivery](configure-delivery-settings.md)
* Definir [Segurança de página dinâmica e retransmissões](#dynamic-page-security-and-relays)
* Restringir a lista de [Comandos externos permitidos](#restricting-authorized-external-commands)
* Configurar [Rastreamento redundante](#redundant-tracking)
* Gerenciar [Alta disponibilidade e afinidades de fluxo de trabalho](#high-availability-workflows-and-affinities)
* Configurar o gerenciamento de arquivos - [Saiba mais](file-res-management.md)
   * Limitar o formato de upload de arquivos
   * Habilitar acesso a recursos públicos
   * Configurar conexão proxy
* [Reinicialização automática do processo](#automatic-process-restart)


## Identificador interno {#internal-identifier}

O **interno** identificador é um login técnico a ser usado para fins de instalação, administração e manutenção. Esse logon não está associado a uma instância.

Os operadores conectados usando esse logon terão todos os direitos em todas as instâncias. Este logon não terá uma senha no caso de uma nova instalação. Você deve definir essa senha manualmente.

Use o seguinte comando:

```
nlserver config -internalpassword
```

As seguintes informações são exibidas. Digite e confirme a senha:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Ativar processos {#enabling-processes}

Os processos do Adobe Campaign no servidor são habilitados (e desabilitados) por meio da variável **config-default.xml** e **`config-<instance>.xml`** arquivos.

Para aplicar as alterações a esses arquivos, se o serviço Adobe Campaign for iniciado, execute o **nlserver config -reload** comando.

Há dois tipos de processos: várias instâncias e uma única instância.

* **várias instâncias**: um único processo é iniciado para todas as instâncias. É o caso para **web**, **syslogd** e **trackinglogd** processos.

   A ativação pode ser configurada no **config-default.xml** arquivo.

   Declaração de um servidor Adobe Campaign para acessar consoles de clientes e para redirecionamento (rastreamento):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   Neste exemplo, o arquivo é editado usando um **vi** no Linux. Ele pode ser editado usando qualquer **.txt** ou **.xml** editor.

* **mono-instance**: um processo é iniciado para cada instância (módulos: **mta**, **wfserver**, **inMail**, **sms** e **stat**).

   A ativação pode ser configurada usando o arquivo de configuração da instância:

   ```
   config-<instance>.xml
   ```

   Declarando um servidor para entrega, executando instâncias de fluxo de trabalho e recuperando emails de devolução:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**Armazenamento de dados da campanha**

Você pode configurar o diretório de armazenamento (**var** diretório) dos dados do Adobe Campaign (logs, downloads, redirecionamentos etc.). Para fazer isso, use o **XTK_VAR_DIR** variável do sistema:

* No Windows, indique o seguinte valor na variável **XTK_VAR_DIR** variável do sistema

   ```
   D:\log\AdobeCampaign
   ```

* No Linux, acesse o **customer.sh** e indicar: **exportar XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Para obter mais informações, consulte [Personalizar parâmetros](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Segurança de página dinâmica e retransmissões {#dynamic-page-security-and-relays}

Por padrão, todas as páginas dinâmicas são automaticamente relacionadas ao **local** Servidor Tomcat da máquina cujo módulo Web foi iniciado. Essa configuração é inserida na variável **`<url>`** seção da configuração de retransmissão de query para **ServerConf.xml** arquivo.

Você pode retransmitir a execução da página dinâmica em um **remoto** servidor; se o módulo Web não estiver ativado no computador. Para fazer isso, é necessário substituir a variável **localhost** com o nome do computador remoto para JSP e JSSP, aplicações Web, relatórios e strings.

Para obter mais informações sobre os vários parâmetros disponíveis, consulte **serverConf.xml** arquivo de configuração.

Para páginas JSP, a configuração padrão é:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

O Adobe Campaign usa as seguintes páginas JSP:

* /nl/jsp/**soaprouter.jsp**: console do cliente e conexões de serviços da Web (APIs SOAP),
* /nl/jsp/**m.jsp**: mirror pages,
* /nl/jsp/**logon.jsp**: Acesso baseado na Web a relatórios e à implantação do console do cliente,
* /nl/jsp/**s.jsp** : Utilização de marketing viral (patrocínio e redes sociais).

Os JSSPs usados para o canal do aplicativo Mobile são os seguintes:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Exemplo:**

É possível evitar conexões de máquina cliente de fora. Para fazer isso, basta restringir a execução de **soaprouter.jsp** e autorizar apenas a execução de mirror pages, links virais, formulários web e recursos públicos.

Os parâmetros são os seguintes:

```
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/> 
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="m.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="s.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="webForm.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/webApp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/jssp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/strings/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/interaction/pub*"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/>
```

Neste exemplo, a variável **`<IP_addresses>`** coincide com a lista de endereços IP (separados por vírgulas) autorizados a usar o módulo de retransmissão para essa máscara.

>[!NOTE]
>
>Os valores devem ser adaptados de acordo com a sua configuração e as suas restrições de rede, especialmente se tiverem sido desenvolvidas configurações específicas para a sua instalação.

### Gerenciar cabeçalhos HTTP {#managing-http-headers}

Por padrão, todos os cabeçalhos HTTP não são retransmitidos. Você pode adicionar cabeçalhos específicos nas respostas enviadas por retransmissão. Para fazer isso:

1. Vá para o **serverConf.xml** arquivo.
1. No **`<relay>`** , vá para a lista de cabeçalhos HTTP retransmitidos.
1. Adicione um **`<responseheader>`** elemento com os seguintes atributos:

   * **name**: nome do cabeçalho
   * **value**: nome do valor.

   Por exemplo:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Restringir comandos externos autorizados {#restricting-authorized-external-commands}

A partir do build 8780, os administradores técnicos podem restringir a lista de comandos externos autorizados que podem ser usados no Adobe Campaign.

Para fazer isso, é necessário criar um arquivo de texto com a lista de comandos que você deseja impedir de usar, por exemplo:

```
ln
dd
openssl
curl
wget
python
python3
perl
ruby
sh
```

>[!IMPORTANT]
>
>Esta lista não é exaustiva.

No **exec** do arquivo de configuração do servidor, é necessário fazer referência ao arquivo criado anteriormente no **blacklistFile** atributo.

**Somente para Linux**: no arquivo de configuração do servidor, recomendamos que você especifique um usuário dedicado à execução de comandos externos para aprimorar sua configuração de segurança. Esse usuário é definido na variável **exec** nó do arquivo de configuração. Todos os parâmetros disponíveis no **serverConf.xml** estão listadas neste [seção](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>Se nenhum usuário for especificado, todos os comandos serão executados no contexto de usuário da instância do Adobe Campaign. O usuário deve ser diferente do usuário que executa o Adobe Campaign.

Por exemplo:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

Esse usuário precisa ser adicionado à lista de subdomínios do operador &quot;neolane&quot; do Adobe Campaign.

>[!IMPORTANT]
>
>Você não deve usar um sudo personalizado. É necessário instalar um sudo padrão no sistema.


## Rastreamento redundante {#redundant-tracking}

Quando vários servidores são usados para redirecionamento, eles devem ser capazes de se comunicar entre si por meio de chamadas SOAP para compartilhar informações dos URLs a serem redirecionados. No momento da inicialização do delivery, é possível que nem todos os servidores de redirecionamento estejam disponíveis; por conseguinte, podem não ter o mesmo nível de informação.

>[!NOTE]
>
>Ao usar a arquitetura padrão ou empresarial, o servidor de aplicativos principal deve ser autorizado a carregar informações de rastreamento em cada computador.

Os URLs dos servidores redundantes devem ser especificados na configuração de redirecionamento, por meio da variável **serverConf.xml** arquivo.

**Exemplo:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

O **enableIf** é opcional (vazio por padrão) e permite habilitar a conexão somente se o resultado for verdadeiro. Isso permite obter uma configuração idêntica em todos os servidores de redirecionamento.

Para obter o nome do host do computador, execute o seguinte comando: **hostname -s**.



## Fluxos de trabalho e afinidades de alta disponibilidade {#high-availability-workflows-and-affinities}

Você pode configurar vários servidores de workflow (wfserver) e distribuí-los em duas ou mais máquinas. Se você escolher esse tipo de arquitetura, configure o modo de conexão dos balanceadores de carga de acordo com o acesso do Adobe Campaign.

Para obter acesso na Web, selecione o **balanceador de carga** para limitar os tempos de conexão.

Se acessar por meio do console do Adobe Campaign, escolha **hash** ou **ponta aderente** modo. Isso permite manter a conexão entre o cliente avançado e o servidor e impedir que uma sessão de usuário seja interrompida durante uma operação de importação ou exportação, por exemplo.

Você pode optar por forçar a execução de um workflow ou de uma atividade de workflow em uma máquina específica. Para fazer isso, é necessário definir uma ou mais afinidades para o workflow ou atividade relacionada.

1. Crie as afinidades do workflow ou da atividade ao inseri-las no **[!UICONTROL Affinity]** campo.

   Você pode escolher qualquer nome de afinidade, mas não deve usar espaços ou marcas de pontuação. Se você usar servidores diferentes, especifique nomes diferentes.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   A lista suspensa contém afinidades anteriormente usadas. Ele é concluído ao longo do tempo com os diferentes valores inseridos.

1. Abra o **nl6/conf/config-`<instance>.xml`** arquivo.
1. Modifique a linha que corresponde à variável **[!UICONTROL wfserver]** módulo como segue:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Se você definir várias afinidades, elas devem ser separadas por vírgulas sem espaços:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   A vírgula que segue o nome da afinidade é necessária para a execução de workflows para os quais nenhuma afinidade é definida.

   Se quiser executar apenas workflows para os quais uma afinidade é definida, não adicione uma vírgula no final da lista de suas afinidades. Por exemplo, modifique a linha da seguinte maneira:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Reinicialização automática {#automatic-process-restart}

Por padrão, os diferentes processos do Adobe Campaign são reiniciados automaticamente às 6:00 (hora do servidor) todos os dias.

No entanto, é possível alterar essa configuração.

Para fazer isso, acesse o **serverConf.xml** , localizado na **conf** repositório da sua instalação.

Cada processo configurado neste arquivo tem uma **processRestartTime** atributo. Você pode modificar o valor desse atributo para adaptar o tempo de reinicialização de cada processo de acordo com suas necessidades.

>[!IMPORTANT]
>
>Não exclua este atributo. Todos os processos devem ser reiniciados todos os dias.
