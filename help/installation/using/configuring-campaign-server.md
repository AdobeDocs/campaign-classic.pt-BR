---
product: campaign
title: Configuração do servidor do Campaign
description: Configuração do servidor do Campaign
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 3%

---

# Introdução à configuração do servidor do Campaign{#gs-campaign-server-config}

![](../../assets/v7-only.svg)

Este capítulo detalha as configurações do lado do servidor que podem ser executadas para atender às suas necessidades e especificidades de ambiente.

## Restrições

Esses procedimentos são restritos a implantações **no local**/**híbridas** e exigem permissões de Administração.

Para implantações **hospedadas**, as configurações do lado do servidor podem ser configuradas somente pelo Adobe. No entanto, algumas configurações podem ser configuradas no [Painel de controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=pt-BR), como gerenciamento de lista de permissões de IP ou permissões de URL. [Saiba mais](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=pt-BR).

Para obter mais informações, consulte esta seção.

* [Documentação do Painel de controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR)
* [Modelos de hospedagem](../../installation/using/hosting-models.md)
* [Matriz de recursos no local e hospedada do Campaign Classic](../../installation/using/capability-matrix.md)

## Arquivos de configuração

Os arquivos de configuração do Campaign Classic são armazenados na pasta **conf** da pasta de instalação do Adobe Campaign. A configuração é distribuída por dois arquivos:

* **serverConf.xml**: configuração geral para todas as instâncias. Este arquivo combina os parâmetros técnicos do servidor do Adobe Campaign: eles são compartilhados por todas as instâncias. A descrição de alguns desses parâmetros é detalhada abaixo. Os diferentes nós e parâmetros e listados nesta [seção](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml**  (onde  **** instâncias é o nome da instância): configuração específica da instância. Se você compartilhar seu servidor entre várias instâncias, insira os parâmetros específicos para cada instância em seu arquivo relevante.

## Escopo de configuração

Configure ou adapte o servidor do Campaign de acordo com suas necessidades e configuração. Você pode:

* Proteja o [Identificador interno](#internal-identifier)
* Habilitar [Processos do Campaign](#enabling-processes)
* Configurar [Permissões de URL](url-permissions.md)
* Definir [Zonas de Segurança](security-zones.md)
* Configurar [Configurações do Tomcat](configure-tomcat.md)
* Personalizar [Parâmetros de entrega](configure-delivery-settings.md)
* Defina [Segurança de página dinâmica e retransmissões](#dynamic-page-security-and-relays)
* Restringir a lista de [Comandos externos permitidos](#restricting-authorized-external-commands)
* Configurar [Rastreamento redundante](#redundant-tracking)
* Gerenciar [Alta disponibilidade e afinidades de fluxo de trabalho](#high-availability-workflows-and-affinities)
* Configurar o gerenciamento de arquivos - [Saiba mais](file-res-management.md)
   * Limitar o formato de upload de arquivos
   * Habilitar acesso a recursos públicos
   * Configurar conexão proxy
* [Reinicialização automática do processo](#automatic-process-restart)


## Identificador interno {#internal-identifier}

O identificador **interno** é um logon técnico a ser usado para fins de instalação, administração e manutenção. Esse logon não está associado a uma instância.

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

Os processos do Adobe Campaign no servidor são habilitados (e desabilitados) por meio dos arquivos **config-default.xml** e **`config-<instance>.xml`**.

Para aplicar as alterações a esses arquivos, se o serviço Adobe Campaign for iniciado, você deverá executar o comando **nlserver config -reload**.

Há dois tipos de processos: várias instâncias e uma única instância.

* **várias instâncias**: um único processo é iniciado para todas as instâncias. Esse é o caso para os processos **web**, **syslogd** e **trackinglogd**.

   A ativação pode ser configurada no arquivo **config-default.xml**.

   Declaração de um servidor Adobe Campaign para acessar consoles de clientes e para redirecionamento (rastreamento):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   Neste exemplo, o arquivo é editado usando um comando **vi** no Linux. Ele pode ser editado usando qualquer editor **.txt** ou **.xml**.

* **mono-instância**: um processo é iniciado para cada instância (módulos:  **mta**,  **wfserver**,  **inMail**,  **** smand  **stat**).

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

Você pode configurar o diretório de armazenamento (**var** diretório) dos dados do Adobe Campaign (logs, downloads, redirecionamentos etc.). Para fazer isso, use a variável do sistema **XTK_VAR_DIR**:

* No Windows, indique o seguinte valor na variável do sistema **XTK_VAR_DIR**

   ```
   D:\log\AdobeCampaign
   ```

* No Linux, vá para o arquivo **customer.sh** e indique: **exportar XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Para obter mais informações, consulte [Personalizar parâmetros](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Segurança de página dinâmica e retransmissões {#dynamic-page-security-and-relays}

Por padrão, todas as páginas dinâmicas são automaticamente relacionadas ao servidor Tomcat **local** da máquina cujo módulo Web foi iniciado. Essa configuração é inserida na seção **`<url>`** da configuração de retransmissão de consulta para o arquivo **ServerConf.xml**.

Você pode retransmitir a execução da página dinâmica em um servidor **remoto**; se o módulo Web não estiver ativado no computador. Para fazer isso, você deve substituir o **localhost** pelo nome do computador remoto para JSP e JSSP, aplicações Web, relatórios e strings.

Para obter mais informações sobre os vários parâmetros disponíveis, consulte o arquivo de configuração **serverConf.xml**.

Para páginas JSP, a configuração padrão é:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

O Adobe Campaign usa as seguintes páginas JSP:

* /nl/jsp/**soaprouter.jsp**: console do cliente e conexões de serviços da Web (APIs SOAP),
* /nl/jsp/**m.jsp**: mirror pages,
* /nl/jsp/**logon.jsp**: Acesso baseado na Web a relatórios e à implantação do console do cliente,
* /nl/jsp/**s.jsp** : Utilização de marketing viral (patrocínio e redes sociais).

Os JSSPs usados para o Canal de aplicativo móvel são os seguintes:

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

Neste exemplo, o valor **`<IP_addresses>`** coincide com a lista de endereços IP (separados por vírgulas) autorizados a usar o módulo de retransmissão para essa máscara.

>[!NOTE]
>
>Os valores devem ser adaptados de acordo com a sua configuração e as suas restrições de rede, especialmente se tiverem sido desenvolvidas configurações específicas para a sua instalação.

### Gerenciar cabeçalhos HTTP {#managing-http-headers}

Por padrão, todos os cabeçalhos HTTP não são retransmitidos. Você pode adicionar cabeçalhos específicos nas respostas enviadas por retransmissão. Para fazer isso:

1. Vá para o arquivo **serverConf.xml**.
1. No nó **`<relay>`**, vá para a lista de cabeçalhos HTTP retransmitidos.
1. Adicione um elemento **`<responseheader>`** com os seguintes atributos:

   * **name**: nome do cabeçalho
   * **valor**: nome do valor.

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

No nó **exec** do arquivo de configuração do servidor, é necessário fazer referência ao arquivo criado anteriormente no atributo **blacklistFile**.

**Somente** para Linux: no arquivo de configuração do servidor, recomendamos que você especifique um usuário dedicado à execução de comandos externos para aprimorar sua configuração de segurança. Esse usuário é definido no nó **exec** do arquivo de configuração. Todos os parâmetros disponíveis no **serverConf.xml** são listados nesta [seção](../../installation/using/the-server-configuration-file.md).

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

As URLs dos servidores redundantes devem ser especificadas na configuração de redirecionamento, por meio do arquivo **serverConf.xml**.

**Exemplo:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

A propriedade **enableIf** é opcional (vazia por padrão) e permite habilitar a conexão somente se o resultado for verdadeiro. Isso permite obter uma configuração idêntica em todos os servidores de redirecionamento.

Para obter o nome do host do computador, execute o seguinte comando: **hostname -s**.



## Fluxos de trabalho e afinidades de alta disponibilidade {#high-availability-workflows-and-affinities}

Você pode configurar vários servidores de workflow (wfserver) e distribuí-los em duas ou mais máquinas. Se você escolher esse tipo de arquitetura, configure o modo de conexão dos balanceadores de carga de acordo com o acesso do Adobe Campaign.

Para acessar a partir da Web, selecione o modo **balanceador de carga** para limitar os tempos de conexão.

Se acessar por meio do console do Adobe Campaign, escolha **hash** ou **modo ip fixo**. Isso permite manter a conexão entre o cliente avançado e o servidor e impedir que uma sessão de usuário seja interrompida durante uma operação de importação ou exportação, por exemplo.

Você pode optar por forçar a execução de um workflow ou de uma atividade de workflow em uma máquina específica. Para fazer isso, é necessário definir uma ou mais afinidades para o workflow ou atividade relacionada.

1. Crie as afinidades do workflow ou da atividade inserindo-as no campo **[!UICONTROL Affinity]** .

   Você pode escolher qualquer nome de afinidade, mas não deve usar espaços ou marcas de pontuação. Se você usar servidores diferentes, especifique nomes diferentes.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   A lista suspensa contém afinidades anteriormente usadas. Ele é concluído ao longo do tempo com os diferentes valores inseridos.

1. Abra o arquivo **nl6/conf/config-`<instance>.xml`**.
1. Modifique a linha que corresponde ao módulo **[!UICONTROL wfserver]** da seguinte maneira:

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

Para fazer isso, vá para o arquivo **serverConf.xml**, localizado no repositório **conf** da sua instalação.

Cada processo configurado neste arquivo tem um atributo **processRestartTime**. Você pode modificar o valor desse atributo para adaptar o tempo de reinicialização de cada processo de acordo com suas necessidades.

>[!IMPORTANT]
>
>Não exclua este atributo. Todos os processos devem ser reiniciados todos os dias.
