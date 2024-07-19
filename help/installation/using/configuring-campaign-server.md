---
product: campaign
title: Configuração do servidor do Campaign
description: Configuração do servidor do Campaign
feature: Installation, Instance Settings
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '1569'
ht-degree: 2%

---

# Introdução à configuração do servidor do Campaign{#gs-campaign-server-config}



Este capítulo detalha as configurações do lado do servidor que podem ser executadas para atender às suas necessidades e às suas especificidades de ambiente.

## Restrições

Estes procedimentos são restritos a **implantações locais**/**híbridas** e exigem permissões de Administração.

Para implantações **hospedadas**, as configurações do lado do servidor podem ser definidas somente por Adobe. No entanto, algumas configurações podem ser definidas no [Painel de Controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=pt-BR), como gerenciamento de inclui na lista de permissões IP ou permissões de URL. [Saiba mais](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=pt-BR).

Para obter mais informações, consulte esta seção.

* [Documentação do Painel de controle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR)
* [Modelos de hospedagem](../../installation/using/hosting-models.md)
* [Matriz de recursos no local e hospedada do Campaign Classic](../../installation/using/capability-matrix.md)

## Arquivos de configuração

Os arquivos de configuração de Campaign Classic são armazenados na pasta **conf** da pasta de instalação do Adobe Campaign. A configuração está distribuída em dois arquivos:

* **serverConf.xml**: configuração geral para todas as instâncias. Esse arquivo combina os parâmetros técnicos do servidor do Adobe Campaign: eles são compartilhados por todas as instâncias. A descrição de alguns desses parâmetros é apresentada abaixo. Os diferentes nós e parâmetros e listados nesta [seção](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (onde **instance** é o nome da instância): configuração específica da instância. Se você compartilhar o servidor entre várias instâncias, insira os parâmetros específicos para cada instância em seu arquivo relevante.

## Escopo da configuração

Configure ou adapte o servidor do Campaign dependendo das suas necessidades e configuração. Você pode:

* Proteger o [Identificador interno](#internal-identifier)
* Habilitar [processos do Campaign](#enabling-processes)
* Configurar [Permissões de URL](url-permissions.md)
* Definir [Zonas de Segurança](security-zones.md)
* Definir [configurações do Tomcat](configure-tomcat.md)
* Personalizar [Parâmetros de entrega](configure-delivery-settings.md)
* Definir [Segurança e retransmissões de página dinâmicas](#dynamic-page-security-and-relays)
* Restringir a lista de [Comandos externos permitidos](#restricting-authorized-external-commands)
* Configurar [Acompanhamento redundante](#redundant-tracking)
* Gerenciar [Alta disponibilidade e afinidades de fluxo de trabalho](#high-availability-workflows-and-affinities)
* Configurar gerenciamento de arquivos - [Saiba mais](file-res-management.md)
   * Limitar o formato de arquivos de upload
   * Habilitar acesso a recursos públicos
   * Configurar conexão Proxy
* [Reinicialização automática do processo](#automatic-process-restart)


## Identificador interno {#internal-identifier}

O identificador **interno** é um logon técnico a ser usado para fins de instalação, administração e manutenção. Este logon não está associado a uma instância.

Os operadores conectados por meio desse logon terão todos os direitos em todas as instâncias. Esse login não terá uma senha no caso de uma nova instalação. Você deve definir manualmente essa senha.

Use o seguinte comando:

```sql
nlserver config -internalpassword
```

As informações a seguir são exibidas. Digite e confirme a senha:

```sql
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Habilitar processos {#enabling-processes}

Os processos do Adobe Campaign no servidor são habilitados (e desabilitados) por meio dos arquivos **config-default.xml** e **`config-<instance>.xml`**.

Para aplicar as alterações nesses arquivos, se o serviço Adobe Campaign for iniciado, você deverá executar o comando **nlserver config -reload**.

Há dois tipos de processos: várias instâncias e instância única.

* **várias instâncias**: um único processo foi iniciado para todas as instâncias. Este é o caso para os processos **web**, **syslogd** e **trackinglogd**.

  A habilitação pode ser configurada no arquivo **config-default.xml**.

  Declaração de um servidor Adobe Campaign para acessar consoles clientes e para redirecionamento (rastreamento):

  ```
  vi nl6/conf/config-default.xml
  <web args="-tomcat" autoStart="true"/>  
  <!-- to start if the machine is also a redirection server -->  
  <trackinglogd autoStart="true"/>
  ```

  Neste exemplo, o arquivo é editado usando um comando **vi** no Linux. Ele pode ser editado com qualquer editor de **.txt** ou **.xml**.

* **mono-instance**: um processo foi iniciado para cada instância (módulos: **mta**, **wfserver**, **inMail**, **sms** e **stat**).

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

**Armazenamento de dados da campanha**

Você pode configurar o diretório de armazenamento (**var** diretório) dos dados do Adobe Campaign (logs, downloads, redirecionamentos, etc.). Para fazer isso, use a variável de sistema **XTK_VAR_DIR**:

* No Windows, indique o seguinte valor na variável de sistema **XTK_VAR_DIR**

  ```
  D:\log\AdobeCampaign
  ```

* No Linux, vá para o arquivo **customer.sh** e indique: **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

  Para obter mais informações, consulte [Personalizar parâmetros](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Segurança e retransmissões de página dinâmicas {#dynamic-page-security-and-relays}

Por padrão, todas as páginas dinâmicas são automaticamente relacionadas ao servidor Tomcat **local** da máquina cujo módulo da Web foi iniciado. Essa configuração é inserida na seção **`<url>`** da configuração de retransmissão de consulta para o arquivo **ServerConf.xml**.

Você pode retransmitir a execução da página dinâmica em um servidor **remoto**; se o módulo Web não estiver ativado no computador. Para fazer isso, você deve substituir o **localhost** pelo nome do computador remoto para JSP e JSSP, aplicativos Web, relatórios e cadeias de caracteres.

Para obter mais informações sobre os vários parâmetros disponíveis, consulte o arquivo de configuração **serverConf.xml**.

Para páginas JSP, a configuração padrão é:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

O Adobe Campaign usa as seguintes páginas JSP:

* /nl/jsp/**soaprouter.jsp**: console do cliente e conexões de serviços da Web (APIs SOAP),
* /nl/jsp/**m.jsp**: mirror pages,
* /nl/jsp/**logon.jsp**: acesso baseado na Web a relatórios e à implantação do console do cliente,
* /nl/jsp/**s.jsp** : usando marketing viral (patrocínio e redes sociais).

As JSSPs usadas para o Canal de aplicativo móvel são as seguintes:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Exemplo:**

É possível impedir conexões externas de máquinas clientes. Para fazer isso, basta restringir a execução do **soaprouter.jsp** e autorizar apenas a execução de mirror pages, links virais, formulários web e recursos públicos.

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

Neste exemplo, o valor **`<IP_addresses>`** coincide com a lista de endereços IP (separados por vírgulas) autorizados a usar o módulo de retransmissão para esta máscara.

>[!NOTE]
>
>Os valores devem ser adaptados de acordo com a sua configuração e as suas restrições de rede, especialmente se configurações específicas tiverem sido desenvolvidas para a sua instalação.

### Gerenciar cabeçalhos HTTP {#managing-http-headers}

Por padrão, todos os cabeçalhos HTTP não são retransmitidos. É possível adicionar cabeçalhos específicos nas respostas enviadas por retransmissão. Para fazer isso:

1. Vá para o arquivo **serverConf.xml**.
1. No nó **`<relay>`**, vá para a lista de cabeçalhos HTTP retransmitidos.
1. Adicione um elemento **`<responseheader>`** com os seguintes atributos:

   * **nome**: nome do cabeçalho
   * **valor**: nome do valor.

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

No nó **exec** do arquivo de configuração do servidor, você precisa fazer referência ao arquivo criado anteriormente no atributo **blacklistFile**.

**Somente para Linux**: no arquivo de configuração do servidor, recomendamos que você especifique um usuário dedicado à execução de comandos externos para aprimorar sua configuração de segurança. Este usuário está definido no nó **exec** do arquivo de configuração. Todos os parâmetros disponíveis no **serverConf.xml** estão listados nesta [seção](../../installation/using/the-server-configuration-file.md).

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

As URLs dos servidores redundantes devem ser especificadas na configuração de redirecionamento, por meio do arquivo **serverConf.xml**.

**Exemplo:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

A propriedade **enableIf** é opcional (vazia por padrão) e permite habilitar a conexão somente se o resultado for verdadeiro. Isso permite obter uma configuração idêntica em todos os servidores de redirecionamento.

Para obter o nome de host do computador, execute o seguinte comando: **hostname -s**.



## Fluxos de trabalho e afinidades de alta disponibilidade {#high-availability-workflows-and-affinities}

Você pode configurar vários servidores de workflow (wfserver) e distribuí-los em dois ou mais computadores. Se você escolher esse tipo de arquitetura, configure o modo de conexão dos balanceadores de carga de acordo com o acesso ao Adobe Campaign.

Para obter acesso da Web, selecione o modo **balanceador de carga** para limitar os tempos de conexão.

Se estiver acessando pelo console do Adobe Campaign, escolha o modo **hash** ou **ip fixo**. Isso permite manter a conexão entre o cliente avançado e o servidor e evitar que uma sessão de usuário seja interrompida durante uma operação de importação ou exportação, por exemplo.

Você pode optar por forçar a execução de um workflow ou uma atividade de workflow em uma máquina específica. Para fazer isso, é necessário definir uma ou mais afinidades para o fluxo de trabalho ou atividade relacionada.

1. Crie as afinidades do fluxo de trabalho ou da atividade inserindo-as no campo **[!UICONTROL Affinity]**.

   Você pode escolher qualquer nome de afinidade, mas não use espaços ou sinais de pontuação. Se você usar servidores diferentes, especifique nomes diferentes.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   A lista suspensa contém afinidades usadas anteriormente. Ele é completado com o tempo com os diferentes valores inseridos.

1. Abra o arquivo **nl6/conf/config-`<instance>.xml`**.
1. Modifique a linha que corresponde ao módulo **[!UICONTROL wfserver]** da seguinte maneira:

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

Para fazer isso, vá para o arquivo **serverConf.xml**, localizado no repositório **conf** da sua instalação.

Cada processo configurado neste arquivo tem um atributo **processRestartTime**. Você pode modificar o valor desse atributo para adaptar o tempo de reinicialização de cada processo de acordo com suas necessidades.

>[!IMPORTANT]
>
>Não exclua este atributo. Todos os processos devem ser reiniciados diariamente.
