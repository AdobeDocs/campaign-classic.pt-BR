---
product: campaign
title: Administração
description: Administração
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# Administração{#administration}



Inicialização automática dos módulos do Adobe Campaign (**web**, **mta**, **wfserver**, etc.) é fornecido pela **nlserver** servidor.

A instalação do Adobe Campaign configura automaticamente o computador para que o **nlserver** o serviço é iniciado durante a sequência de inicialização.

Os seguintes comandos são usados para iniciar e desligar o serviço Adobe Campaign manualmente:

* No Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* No Linux (como raiz):

   * **/etc/init.d/nlserver6 iniciar**
   * **parada de /etc/init.d/nlserver6**

>[!NOTE]
>
>A partir da versão 20.1, recomendamos usar o seguinte comando (para Linux): **systemctl start nlserver** / **systemctl stop nlserver**

Esta é uma lista dos comandos administrativos usuais acessíveis no Linux (como **Adobe Campaign**):

* Exibir todos os módulos Adobe Campaign iniciados: **despejo /etc/init.d/nlserver6** ou **Status /etc/init.d/nlserver6**

   >[!NOTE]
   >
   >Adicionar o **-quem** parâmetro para o **despejo** permite coletar informações sobre conexões atuais (usuários e processos).\
   >A variável **Status /etc/init.d/nlserver6** (sem o parâmetro &quot;-who&quot;) retornará:
   >
   >    * 0 se todos os processos estiverem sendo executados.
   >    * 1 se um processo estiver ausente.
   >    * 2 se nenhum processo estiver sendo executado.
   >    * outro valor se houver um erro.


* Iniciar/parar um módulo de várias instâncias ou de instâncias mono (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

   **nlserver start`<module>[@<instance>]`**

   **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

   Você também pode usar a variável **reinicialização do nlserver`<module>[@<instance>]`** comando para reiniciar um módulo.

   Exemplo:

   **nlserver start web**

   **nlserver start mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver stop web -immediate**

   **Web de reinicialização do nlserver**

   >[!NOTE]
   >
   >* Se a instância não for especificada, a instância &quot;padrão&quot; será usada.
   >* Em caso de emergência, utilizar o **-immediate** opção para forçar uma parada imediata no processo (equivalente ao comando Unix **kill - 9**).
   >* Use o **-noconsole** opção para garantir que o módulo iniciado não exibirá nada no console. Seus registros serão gravados no disco por meio do **syslogd** módulo.
   >* Use o **-verboso** opção para exibir informações adicionais sobre ações do processo.

      >
      >   Exemplo:
      >
      >   **nlserver restart web - verbose**
      >
      >   **nlserver start mta@myinstance -verbose**
      >
      >   Essa opção adiciona logs adicionais. Recomendamos iniciar os processos novamente sem o **-verboso** depois de encontrar as informações desejadas, para evitar sobrecarga de logs.


* Inicie todos os processos do Adobe Campaign (equivalente a iniciar o **nlserver6** serviço):

   **nlserver watchdog -noconsole**

* Encerre todos os processos do Adobe Campaign (equivalente a encerrar o **nlserver6** serviço):

   **desligamento do nlserver**

* Recarregue o **nlserver web** (e o módulo de extensão do servidor Web, quando aplicável) quando a variável **serverConf.xml** e **config-`<instance>  .xml </instance>`** arquivos foram editados.

   **nlserver config - reload**

   >[!NOTE]
   >
   >Algumas alterações de configuração não são consideradas dinamicamente; o Adobe Campaign deve ser encerrado e depois reiniciado.
