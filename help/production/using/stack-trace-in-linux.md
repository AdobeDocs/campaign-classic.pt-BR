---
solution: Campaign Classic
product: campaign
title: Rastreamento em pilha no Linux
description: Rastreamento em pilha no Linux
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 11%

---


# Rastreamento em pilha no Linux{#stack-trace-in-linux}

Um rastreamento **de** pilha representa um rastreamento contido em um arquivo do tipo **principal** . Esse arquivo é gerado no evento de um erro de computador. Ele pode identificar a origem do erro.

>[!NOTE]
>
>* Um arquivo **principal** é chamado de **núcleo.`<num>`**.
>* **gdb - O Depurador** GNU deve estar instalado no computador.

>



O suporte técnico da Adobe Campaign pode solicitar esse rastreamento **da** pilha. Para obtê-lo, insira os seguintes comandos no Linux:

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

O suporte técnico da Adobe Campaign pode solicitar que você execute esse comando usando um executável específico (a ser fornecido por nós).

Nesse caso, basta executar o seguinte comando substituindo o **nlserver** pelo executável fornecido pela Adobe Campaign:

```
gdb nlserver <coreFile>
```

Por exemplo:

```
gdb nlserver.1823 <coreFile>
```

