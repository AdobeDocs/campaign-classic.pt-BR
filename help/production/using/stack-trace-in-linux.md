---
product: campaign
title: Rastreamento em pilha no Linux
description: Rastreamento em pilha no Linux
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
badge-v7-prem: label="No local e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 91662d6d-2177-4440-b31f-7b031bd953cb
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 22%

---

# Rastreamento em pilha no Linux{#stack-trace-in-linux}



A **rastreamento de pilha** representa um rastreamento contido em um **core** arquivo de tipo. Esse arquivo é gerado no caso de um erro de computador. Ele pode identificar a origem do erro.

>[!NOTE]
>
>* A **core** o arquivo é nomeado **principal.`<num>`**.
>* **gdb - O depurador GNU** deve estar instalado no computador.
>

O suporte técnico da Adobe Campaign pode solicitar isso **rastreamento de pilha**. Para obtê-lo, insira os seguintes comandos no Linux:

```
su - neolane
gdb nlserver <coreFile>
//You get lots of output but the stack trace (or Back trace) can be obtained with : 
(gdb) bt
// and forward all the output : 
#0 0x0836c189 in ObjectValue::SetPropertyTarget ()
#1 0x082623b3 in CXtkScriptProperty::VDeclareProperties ()
#2 0x0826a835 in CXtkScriptContext::OnGetProperty ()
#3 0x08370b3d in JavaScriptGetProperty ()
#4 0x557b8aa7 in js_Interpret () from /usr/local/neolane/nl6/lib/libmozjs.so
#5 0x557afb97 in js_Execute () from /usr/local/neolane/nl6/lib/libmozjs.so
#6 0x5578921f in JS_ExecuteScript () from /usr/local/neolane/nl6/lib/libmozjs.so
#7 0x08370468 in JavaScriptSource::Evaluate ()
#8 0x0848fa03 in JSTDeliveryContext::ProcessScript ()
#9 0x0848fcb6 in JSTDeliveryContext::ProcessTemplate ()
#10 0x08460d2b in CDeliveryToolbox::CreateMailMessage ()
#11 0x080d51fe in CMtaQueue::PrepareMessages ()
#12 0x080d2b07 in CMtaQueue::Prepare ()
#13 0x080dca38 in CMtaChild::OnRun ()
#14 0x0814792c in ThreadStartRoutine ()
#15 0x55575b63 in start_thread () from /lib/tls/libpthread.so.0
#16 0x5565918a in clone () from /lib/tls/libc.so.6
```

O suporte técnico da Adobe Campaign pode solicitar que você execute este comando usando um executável específico (a ser fornecido por nós).

Nesse caso, basta executar o seguinte comando substituindo **nlserver** com o executável fornecido pela Adobe Campaign:

```
gdb nlserver <coreFile>
```

Por exemplo:

```
gdb nlserver.1823 <coreFile>
```
