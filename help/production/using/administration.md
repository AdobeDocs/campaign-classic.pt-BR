---
product: campaign
title: Administração
description: Administração
feature: Monitoring
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: b7dedddc080d1ea8db700fabc9ee03238b3706cc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 3%

---

# Administração{#administration}

Inicialização automática dos módulos do Adobe Campaign (**web**, **mta**, **wfserver**, etc.) é fornecido pelo servidor **nlserver**.

A instalação do Adobe Campaign configura automaticamente o computador para que o serviço **nlserver** seja inicializado durante a sequência de inicialização.

Os seguintes comandos são usados para iniciar e desligar o serviço Adobe Campaign manualmente:

* No Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* No Linux (como raiz):

   * **/etc/init.d/nlserver6 início**
   * **/etc/init.d/nlserver6 parada**

>[!NOTE]
>
>A partir da versão 20.1, é recomendável usar o seguinte comando (para Linux): **systemctl start nlserver** / **systemctl stop nlserver**

Esta é uma lista dos comandos de administração habituais acessíveis no Linux (como **Adobe Campaign**):

* Exibir todos os módulos do Adobe Campaign iniciados: **/etc/init.d/nlserver6 despejo** ou **/etc/init.d/nlserver6 status**

  >[!NOTE]
  >
  >Adicionar o parâmetro **-who** ao comando **pdump** permite coletar informações sobre as conexões atuais (usuários e processos).\
  >O comando **/etc/init.d/nlserver6 status** (sem o parâmetro &quot;-who&quot;) retornará:
  >
  >    * 0 se todos os processos estiverem sendo executados.
  >    * 1 se um processo estiver ausente.
  >    * 2 se nenhum processo estiver sendo executado.
  >    * outro valor se houver um erro.
  >

* Iniciar/parar um módulo de várias instâncias ou de instâncias mono (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

  **ninício do servidor`<module>[@<instance>]`**

  **nparada do servidor`<module>[@<instance>][-immediate][-noconsole]`**

  Você também pode usar o comando **nlserver restart`<module>[@<instance>]`** para reiniciar um módulo.

  Exemplo:

  **nlserver iniciar Web**

  **nlserver start mta@my_instance**

  **nlserver parar syslogd**

  **nlserver parar wfserver@my_instance**

  **nlserver parar web -immediate**

  **nlserver reiniciar Web**

  >[!NOTE]
  >
  >* Se a instância não for especificada, a instância &quot;padrão&quot; será usada.
  >* No caso de uma emergência, use a opção **-immediate** para forçar uma parada imediata no processo (equivalente ao comando Unix **kill -9**).
  >* Use a opção **-noconsole** para garantir que o módulo iniciado não exibirá nada no console. Seus logs serão gravados no disco por meio do módulo **syslogd**.
  >* Use a opção **-verbose** para exibir informações adicionais sobre ações do processo.
  >
  >   Exemplo:
  >
  >   **nlserver reiniciar web -verbose**
  >
  >   **nlserver start mta@myinstance -verbose**
  >
  >   Essa opção adiciona logs adicionais. Recomendamos iniciar os processos novamente sem a opção **-verbose** depois de encontrar as informações desejadas, para evitar sobrecarga de logs.

* Inicie todos os processos do Adobe Campaign (equivalente a inicializar o serviço **nlserver6**):

  **nlserver watchdog -noconsole**

* Desligue todos os processos do Adobe Campaign (equivalente a desligar o serviço **nlserver6**):

  **ndesligamento do servidor**

* Recarregue a configuração do módulo da Web **nlserver** (e o módulo de extensão do servidor Web, quando aplicável) quando os arquivos **serverConf.xml** e **config-`<instance>  .xml </instance>`** tiverem sido editados.

  **nlserver config -reload**

  >[!NOTE]
  >
  >Algumas alterações de configuração não são consideradas dinamicamente; o Adobe Campaign deve ser encerrado e depois reiniciado.
