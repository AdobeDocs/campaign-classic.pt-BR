---
solution: Campaign Classic
product: campaign
title: Administração
description: Administração
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---


# Administração{#administration}

Inicialização automática dos módulos Adobe Campaign (**Web**, **mta**, **wfserver** etc.) é fornecido pelo servidor **nlserver** .

A instalação do Adobe Campaign configura automaticamente o computador para que o serviço **nlserver** seja start durante a sequência de inicialização.

Os comandos a seguir são usados para start e desligar o serviço Adobe Campaign manualmente:

* No Windows:

   * **start net nlserver6**
   * **net stop nlserver6**

* No Linux (como raiz):

   * **start /etc/init.d/nlserver6**
   * **/etc/init.dção de/nlserver6**

>[!NOTE]
>
>A partir do 20.1, recomendamos usar o seguinte comando (para Linux): **start system ctl nlserver** / **system ctl stop nlserver**

Esta é uma lista dos comandos de administração comuns acessíveis no Linux (como o **Adobe Campaign**):

* Exibir todos os módulos Adobe Campaign iniciados: **/etc/init.d/nlserver6 pdump** ou **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >Adicionar o parâmetro **-who** ao comando **pdump** permite coletar informações sobre conexões atuais (usuários e processos).\
   >O comando de status **** /etc/init.d/nlserver6 (sem o parâmetro &quot;-who&quot;) retornará:
   >
   >    * 0 se todos os processos estiverem sendo executados.
   >    * 1 se um processo estiver faltando.
   >    * 2 se nenhum processo estiver sendo executado.
   >    * outro valor se houver um erro.


* Start/parada de um módulo de várias instâncias ou mono-instâncias (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver******, inmail):

   **start nlserver`<module>[@<instance>]`**

   **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

   Você também pode usar o comando **nlserver restart`<module>[@<instance>]`** para reiniciar um módulo.

   Exemplo:

   **start nlserver web**

   **start nlserver mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver stop web - imediato**

   **Web de reinicialização do nlserver**

   >[!NOTE]
   > 
   >    * Se a instância não for especificada, a instância &quot;padrão&quot; será usada.
   >    * Em evento de uma emergência, use a opção **-imediata** para forçar uma interrupção imediata do processo (equivalente ao comando Unix **kill -9**).
   >    * Use a opção **-noconsole** para garantir que o módulo iniciado não exiba nada no console. Seus registros serão gravados no disco por meio do módulo **syslogd** .
   >    * Use a opção **-detalhado** para exibir informações adicionais sobre ações do processo.

      >    
      >      
      Exemplo:
      >    
      >      
      **nlserver restart web -verbose**
      >    
      >      
      **start nlserver mta@myinstance - verbose**
      >    
      >      
      Essa opção adiciona outros logs. Recomendamos iniciar os processos novamente sem a opção **-verbose** depois que você encontrar as informações desejadas, para evitar sobrecarregar os logs.


* Start todos os processos do Adobe Campaign (equivalente à inicialização do serviço **nlserver6** ):

   **nlserver watchdog -noconsole**

* Desligue todos os processos do Adobe Campaign (equivalente a desligar o serviço **nlserver6** ):

   **desligamento do nlserver**

* Recarregue a configuração do módulo da Web **do** nlserver (e o módulo de extensão do servidor da Web, quando aplicável) quando os arquivos **serverConf.xml** e **config-`<instance>  .xml </instance>`** tiverem sido editados.

   **nlserver config -reload**

   >[!NOTE]
   >
   >Algumas alterações de configuração não são tomadas em consideração de forma dinâmica; O Adobe Campaign deve ser desligado e reiniciado.

