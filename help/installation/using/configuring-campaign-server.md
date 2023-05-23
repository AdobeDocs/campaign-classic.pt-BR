---
product: campaign
title: Configuração do servidor do Campaign
description: Configuração do servidor do Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 3%

---

# Introdução à configuração do servidor do Campaign{#gs-campaign-server-config}



Este capítulo detalha as configurações do lado do servidor que podem ser executadas para atender às suas necessidades e às suas especificidades de ambiente.

## Restrições

Estes procedimentos estão limitados a **no local**/**híbrido** implantações e exigem permissões de Administração.

Para **hospedado** implantações, as configurações do lado do servidor só podem ser definidas por Adobe. No entanto, algumas configurações podem ser definidas no [Painel de controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=pt-BR), como o gerenciamento de inclui na lista de permissões de IP ou permissões de URL. [Saiba mais](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=pt-BR).

Para obter mais informações, consulte esta seção.

* [Documentação do Painel de controle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR)
* [Modelos de hospedagem](../../installation/using/hosting-models.md)
* [Matriz de recursos no local e hospedada do Campaign Classic](../../installation/using/capability-matrix.md)

## Arquivos de configuração

Os arquivos de configuração de Campaign Classic são armazenados no **conf** pasta da pasta de instalação do Adobe Campaign. A configuração está distribuída em dois arquivos:

* **serverConf.xml**: configuração geral para todas as instâncias. Esse arquivo combina os parâmetros técnicos do servidor do Adobe Campaign: eles são compartilhados por todas as instâncias. A descrição de alguns desses parâmetros é apresentada abaixo. Os diferentes nós e parâmetros e listados neste [seção](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (onde **instância** é o nome da instância): configuração específica da instância. Se você compartilhar o servidor entre várias instâncias, insira os parâmetros específicos para cada instância em seu arquivo relevante.

## Escopo da configuração

Configure ou adapte o servidor do Campaign dependendo das suas necessidades e configuração. Você pode:

* Proteja o [Identificador interno](#internal-identifier)
* Ativar [Processos de campanha](#enabling-processes)
* Configurar [Permissões de URL](url-permissions.md)
* Definir [Zonas de segurança](security-zones.md)
* Configurar [Configurações do Tomcat](configure-tomcat.md)
* Personalizar [Parâmetros de entrega](configure-delivery-settings.md)
* Definir [Segurança e retransmissões de página dinâmicas](#dynamic-page-security-and-relays)
* Restringir a lista de [Comandos externos permitidos](#restricting-authorized-external-commands)
* Configurar [Rastreamento redundante](#redundant-tracking)
* Gerenciar [Alta disponibilidade e afinidades de fluxo de trabalho](#high-availability-workflows-and-affinities)
* Configurar gerenciamento de arquivos - [Saiba mais](file-res-management.md)
   * Limitar o formato de arquivos de upload
   * Habilitar acesso a recursos públicos
   * Configurar conexão Proxy
* [Reinicialização automática do processo](#automatic-process-restart)


## Identificador interno {#internal-identifier}

A variável **interno** identifier é um logon técnico que deve ser usado para fins de instalação, administração e manutenção. Este logon não está associado a uma instância.

Os operadores conectados por meio desse logon terão todos os direitos em todas as instâncias. Esse login não terá uma senha no caso de uma nova instalação. Você deve definir manualmente essa senha.

Use o seguinte comando:

```
nlserver config -internalpassword
```

As informações a seguir são exibidas. Digite e confirme a senha:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Habilitar processos {#enabling-processes}

Os processos do Adobe Campaign no servidor são ativados (e desativados) por meio da **config-default.xml** e **`config-<instance>.xml`** arquivos.

Para aplicar as alterações nesses arquivos, se o serviço Adobe Campaign for iniciado, você deverá executar o **nlserver config - reload** comando.

Há dois tipos de processos: várias instâncias e instância única.

* **várias instâncias**: um único processo é iniciado para todas as instâncias. Este é o caso para **web**, **syslogd** e **trackinglogd** processos.

   A ativação pode ser configurada no **config-default.xml** arquivo.

   Declaração de um servidor Adobe Campaign para acessar consoles clientes e para redirecionamento (rastreamento):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   Neste exemplo, o arquivo é editado usando um **vi** comando no Linux. Ele pode ser editado usando qualquer **.txt** ou **.xml** editor.

* **mono-instance**: um processo é iniciado para cada instância (módulos: **mta**, **wfserver**, **inMail**, **sms** e **stat**).

   A ativação pode ser configurada usando o arquivo de configuração da instância:

   ```
   config-<instance>.xml
   ```

   Declaração de um servidor para entrega, execução de instâncias de fluxo de trabalho e recuperação de emails devolvidos:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**Armazenamento de dados do Campaign**

Você pode configurar o diretório de armazenamento (**var** diretório) de dados do Adobe Campaign (logs, downloads, redirecionamentos etc.). Para fazer isso, use o **XTK_VAR_DIR** variável de sistema:

* No Windows, indique o seguinte valor na variável **XTK_VAR_DIR** variável de sistema

   ```
   D:\log\AdobeCampaign
   ```

* No Linux, acesse a página **customer.sh** e indique: **exportar XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Para obter mais informações, consulte [Personalizar parâmetros](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Segurança e retransmissões de página dinâmicas {#dynamic-page-security-and-relays}

Por padrão, todas as páginas dinâmicas são automaticamente relacionadas ao **local** Servidor Tomcat da máquina cujo módulo da Web foi iniciado. Essa configuração é inserida na variável **`<url>`** seção da configuração de retransmissão de consulta para o **ServerConf.xml** arquivo.

É possível retransmitir a execução da página dinâmica em uma **remoto** servidor; se o módulo Web não estiver ativado no computador. Para fazer isso, você deve substituir o **localhost** com o nome do computador remoto para JSP e JSSP, aplicações web, relatórios e strings.

Para obter mais informações sobre os vários parâmetros disponíveis, consulte **serverConf.xml** arquivo de configuração.

Para páginas JSP, a configuração padrão é:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

O Adobe Campaign usa as seguintes páginas JSP:

* /nl/jsp/**soaprouter.jsp**: console do cliente e conexões de serviços da Web (APIs SOAP),
* /nl/jsp/**m.jsp**: mirror pages,
* /nl/jsp/**logon.jsp**: acesso baseado na Web a relatórios e à implantação do console do cliente,
* /nl/jsp/**s.jsp** : Uso de marketing viral (patrocínio e redes sociais).

As JSSPs usadas para o Canal de aplicativo móvel são as seguintes:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Exemplo:**

É possível impedir conexões externas de máquinas clientes. Para fazer isso, basta restringir a execução de **soaprouter.jsp** e só autorizam a execução de mirror pages, links virais, formulários web e recursos públicos.

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

Neste exemplo, a variável **`<IP_addresses>`** O valor de coincide com a lista de endereços IP (separados por vírgulas) autorizados a usar o módulo de retransmissão para essa máscara.

>[!NOTE]
>
>Os valores devem ser adaptados de acordo com a sua configuração e as suas restrições de rede, especialmente se configurações específicas tiverem sido desenvolvidas para a sua instalação.

### Gerenciar cabeçalhos HTTP {#managing-http-headers}

Por padrão, todos os cabeçalhos HTTP não são retransmitidos. É possível adicionar cabeçalhos específicos nas respostas enviadas por retransmissão. Para fazer isso:

1. Vá para a **serverConf.xml** arquivo.
1. No **`<relay>`** vá para a lista de cabeçalhos HTTP retransmitidos.
1. Adicionar um **`<responseheader>`** elemento com os seguintes atributos:

   * **name**: nome do cabeçalho
   * **value**: nome do valor.

   Por exemplo:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Restringir comandos externos autorizados {#restricting-authorized-external-commands}

Na build 8780, os administradores técnicos podem restringir a lista de comandos externos autorizados que podem ser usados no Adobe Campaign.

Para fazer isso, é necessário criar um arquivo de texto com a lista de comandos que você deseja impedir que o use, por exemplo:

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

No **exec** do arquivo de configuração do servidor, é necessário fazer referência ao arquivo criado anteriormente na **blacklistFile** atributo.

**Somente para Linux**: no arquivo de configuração do servidor, recomendamos que você especifique um usuário dedicado à execução de comandos externos para aprimorar a configuração de segurança. Este usuário está definido na variável **exec** nó do arquivo de configuração. Todos os parâmetros disponíveis no **serverConf.xml** estão listados neste [seção](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>Se nenhum usuário for especificado, todos os comandos serão executados no contexto do usuário da instância do Adobe Campaign. O usuário deve ser diferente do usuário que está executando o Adobe Campaign.

Por exemplo:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

Este usuário precisa ser adicionado à lista sudoer do operador Adobe Campaign &#39;neolane&#39;.

>[!IMPORTANT]
>
>Você não deve usar um sudo personalizado. Um sudo padrão precisa ser instalado no sistema.


## Rastreamento redundante {#redundant-tracking}

Quando vários servidores são usados para redirecionamento, eles devem poder se comunicar entre si por meio de chamadas SOAP para compartilhar informações dos URLs a serem redirecionados. No momento da inicialização do delivery, é possível que nem todos os servidores de redirecionamento estejam disponíveis; portanto, eles podem não ter o mesmo nível de informações.

>[!NOTE]
>
>Ao usar a arquitetura padrão ou empresarial, o servidor de aplicativos principal deve estar autorizado a carregar informações de rastreamento em cada computador.

Os URLs dos servidores redundantes devem ser especificados na configuração de redirecionamento, através do **serverConf.xml** arquivo.

**Exemplo:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

A variável **enableIf** é opcional (vazio por padrão) e permite habilitar a conexão somente se o resultado for verdadeiro. Isso permite obter uma configuração idêntica em todos os servidores de redirecionamento.

Para obter o nome de host do computador, execute o seguinte comando: **hostname -s**.



## Fluxos de trabalho e afinidades de alta disponibilidade {#high-availability-workflows-and-affinities}

Você pode configurar vários servidores de workflow (wfserver) e distribuí-los em dois ou mais computadores. Se você escolher esse tipo de arquitetura, configure o modo de conexão dos balanceadores de carga de acordo com o acesso ao Adobe Campaign.

Para obter acesso pela Web, selecione a variável **balanceador de carga** para limitar os tempos de conexão.

Se acessar por meio do console Adobe Campaign, escolha **hash** ou **ip fixo** modo. Isso permite manter a conexão entre o cliente avançado e o servidor e evitar que uma sessão de usuário seja interrompida durante uma operação de importação ou exportação, por exemplo.

Você pode optar por forçar a execução de um workflow ou uma atividade de workflow em uma máquina específica. Para fazer isso, é necessário definir uma ou mais afinidades para o fluxo de trabalho ou atividade relacionada.

1. Crie as afinidades do fluxo de trabalho ou da atividade inserindo-as no **[!UICONTROL Affinity]** campo.

   Você pode escolher qualquer nome de afinidade, mas não use espaços ou sinais de pontuação. Se você usar servidores diferentes, especifique nomes diferentes.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   A lista suspensa contém afinidades usadas anteriormente. Ele é completado com o tempo com os diferentes valores inseridos.

1. Abra o **nl6/conf/config-`<instance>.xml`** arquivo.
1. Modifique a linha que corresponde ao **[!UICONTROL wfserver]** módulo da seguinte forma:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Se você definir várias afinidades, elas deverão ser separadas por vírgulas sem espaços:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   A vírgula após o nome da afinidade é necessária para a execução de workflows para os quais nenhuma afinidade é definida.

   Se desejar executar apenas workflows para os quais uma afinidade estiver definida, não adicione uma vírgula no final da lista de afinidades. Por exemplo, modifique a linha da seguinte maneira:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Reinicialização automática {#automatic-process-restart}

Por padrão, os diferentes processos do Adobe Campaign são reiniciados automaticamente às 6h (horário do servidor) todos os dias.

No entanto, você pode alterar essa configuração.

Para fazer isso, acesse o **serverConf.xml** arquivo, localizado na **conf** repositório da sua instalação.

Cada processo configurado neste arquivo tem um **processRestartTime** atributo. Você pode modificar o valor desse atributo para adaptar o tempo de reinicialização de cada processo de acordo com suas necessidades.

>[!IMPORTANT]
>
>Não exclua este atributo. Todos os processos devem ser reiniciados diariamente.
