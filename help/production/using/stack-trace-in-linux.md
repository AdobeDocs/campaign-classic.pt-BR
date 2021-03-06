---
product: campaign
title: Rastreamento em pilha no Linux
description: Rastreamento em pilha no Linux
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 91662d6d-2177-4440-b31f-7b031bd953cb
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 11%

---

# Rastreamento em pilha no Linux{#stack-trace-in-linux}

![](../../assets/v7-only.svg)

A **rastreamento de pilha** representa um rastreamento contido em um **núcleo** digite o arquivo . Esse arquivo é gerado no caso de um erro de computador. Ele pode identificar a origem do erro.

>[!NOTE]
>
>* A **núcleo** arquivo é nomeado **núcleo.`<num>`**.
>* **gdb - O depurador GNU** deve ser instalado no computador.

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

Nesse caso, basta executar o seguinte comando ao substituir **nlserver** com o executável fornecido pela Adobe Campaign:

```
gdb nlserver <coreFile>
```

Por exemplo:

```
gdb nlserver.1823 <coreFile>
```
