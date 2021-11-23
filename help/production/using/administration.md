---
product: campaign
title: Administração
description: Administração
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# Administração{#administration}

![](../../assets/v7-only.svg)

Inicialização automática dos módulos Adobe Campaign (**web**, **mta**, **wfserver**, etc.) é fornecida pelo **nlserver** servidor.

A instalação do Adobe Campaign configura automaticamente a máquina para que a função **nlserver** O serviço é iniciado durante a sequência de inicialização.

Os seguintes comandos são usados para iniciar e encerrar o serviço Adobe Campaign manualmente:

* No Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* No Linux (como raiz):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>A partir da versão 20.1, recomendamos usar o seguinte comando (para Linux): **systemctl start nlserver** / **systemctl stop nlserver**

Esta é uma lista dos comandos de administração usuais acessíveis no Linux (como **Adobe Campaign**):

* Exibir todos os módulos Adobe Campaign iniciados: **/etc/init.d/nlserver6 pdump** ou **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >Adicionar a **-who** para **pdump** permite coletar informações sobre conexões atuais (usuários e processos).\
   >O **/etc/init.d/nlserver6 status** (sem o parâmetro &quot;-who&quot;) retornará:
   >
   >    * 0 se todos os processos estiverem sendo executados.
   >    * 1 se um processo estiver ausente.
   >    * 2 se nenhum processo estiver sendo executado.
   >    * outro valor se houver um erro.


* Iniciar/parar um módulo de várias instâncias ou de mono-instâncias (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

   **nlserver start`<module>[@<instance>]`**

   **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

   Também é possível usar a variável **reinicialização do nlserver`<module>[@<instance>]`** para reiniciar um módulo.

   Exemplo:

   **Web de início do nlserver**

   **nlserver start mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver stop web -immediate**

   **Web de reinicialização do nlserver**

   >[!NOTE]
   >
   >* Se a instância não for especificada, a instância &quot;padrão&quot; será usada.
   >* Em caso de emergência, utilize o **-imediato** opção para forçar uma interrupção imediata do processo (equivalente ao comando Unix) **kill -9**).
   >* Use o **-noconsole** para garantir que o módulo iniciado não exibirá nada no console. Seus registros serão gravados no disco por meio do **syslogd** módulo.
   >* Use o **-verbose** para exibir informações adicionais sobre ações do processo.
   >
   >   Exemplo:
   >
   >   **nlserver restart web -verbose**
   >
   >   **nlserver start mta@myinstance -verbose**
   >
   >   Essa opção adiciona logs adicionais. Recomendamos iniciar os processos novamente sem o **-verbose** após encontrar as informações desejadas, para evitar sobrecarga de logs.


* Inicie todos os processos do Adobe Campaign (equivalente à inicialização do **nlserver6** serviço):

   **nlserver watchdog -noconsole**

* Desligue todos os processos do Adobe Campaign (equivalente a desligar o **nlserver6** serviço):

   **desligamento do nlserver**

* Recarregue o **nlserver web** configuração do módulo (e do módulo de extensão do servidor da Web, quando aplicável) quando a variável **serverConf.xml** e **config-`<instance>  .xml </instance>`** os arquivos foram editados.

   **nlserver config -reload**

   >[!NOTE]
   >
   >Algumas alterações de configuração não são consideradas dinamicamente; O Adobe Campaign deve ser desligado e reiniciado.
