---
title: Administração
seo-title: Administração
description: Administração
seo-description: null
page-status-flag: never-activated
uuid: 376efec1-1647-43b4-b72f-2603214c7cc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 860be8be-f28c-4836-b4fb-e91c6a4616c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# Administração{#administration}

Inicialização automática dos módulos do Adobe Campaign (**web**, **mta**, **wfserver** etc.) é fornecido pelo servidor **nlserver** .

A instalação do Adobe Campaign configura automaticamente a máquina para que o serviço **nlserver** seja iniciado durante a sequência de inicialização.

Os seguintes comandos são usados para iniciar e encerrar o serviço Adobe Campaign manualmente:

* No Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* No Linux (como raiz):

   * **/etc/init.dção do/nlserver6**
   * **/etc/init.dção de/nlserver6**

Esta é uma lista dos comandos de administração comuns acessíveis no Linux (como o **Adobe Campaign**):

* Exibir todos os módulos do Adobe Campaign iniciados: **/etc/init.d/nlserver6 pdump** ou **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >Adicionar o parâmetro **-who** ao comando **pdump** permite coletar informações sobre conexões atuais (usuários e processos).\
   >O comando de status **** /etc/init.d/nlserver6 (sem o parâmetro &quot;-who&quot;) retornará:
   >
   >    * 0 se todos os processos estiverem sendo executados.
   >    * 1 se um processo estiver faltando.
   >    * 2 se nenhum processo estiver sendo executado.
   >    * outro valor se houver um erro.


* Inicie/pare um módulo de várias instâncias ou mono-instâncias (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver******, inmail):

   **início do nlserver`<module>[@<instance>]`**

   **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

   Você também pode usar o comando **nlserver restart`<module>[@<instance>]`**para reiniciar um módulo.

   Exemplo:

   **Web de início do servidor**

   **nlserver start mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver stop web - imediato**

   **Web de reinicialização do nlserver**

   >[!NOTE]

   >* Se a instância não for especificada, a instância &quot;padrão&quot; será usada.
   >    
   >    
   >    * Em caso de emergência, use a opção **-imediata** para forçar uma interrupção imediata do processo (equivalente ao comando Unix **kill -9**).
   * Use a opção **-noconsole** para garantir que o módulo iniciado não exiba nada no console. Seus registros serão gravados no disco por meio do módulo **syslogd** .
   * Use a opção **-detalhado** para exibir informações adicionais sobre ações do processo.


      Exemplo:


      **nlserver restart web -verbose**


      **nlserver start mta@myinstance - verbose**


      Essa opção adiciona outros logs. Recomendamos iniciar os processos novamente sem a opção **-verbose** depois que você encontrar as informações desejadas, para evitar sobrecarregar os logs.


* Inicie todos os processos do Adobe Campaign (equivalente à inicialização do serviço **nlserver6** ):

   **nlserver watchdog -noconsole**

* Desligue todos os processos do Adobe Campaign (equivalente a desligar o serviço **nlserver6** ):

   **desligamento do nlserver**

* Recarregue a configuração do módulo da Web **do** nlserver (e o módulo de extensão do servidor da Web, quando aplicável) quando os arquivos **serverConf.xml** e **config-`<instance>  .xml </instance>`**tiverem sido editados.

   **nlserver config -reload**

   >[!NOTE]
   Algumas alterações de configuração não são tomadas em consideração de forma dinâmica; O Adobe Campaign deve ser encerrado e reiniciado.

