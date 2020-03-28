---
title: Finalidade
seo-title: Finalidade
description: Finalidade
seo-description: null
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Finalidade{#purpose}

O objetivo deste caso de uso é adicionar anexos de email em tempo real a expedições de saída.

Neste cenário, veremos como enviar emails transacionais com anexos individuais/personalizados. Os anexos não serão carregados previamente no servidor de Mensagens transacionais, mas gerado em tempo real.

Ao capturar interações ou detalhes do cliente, talvez seja necessário enviar essas informações novamente ao cliente no final do processo, por exemplo, em um arquivo PDF anexado a um email. Estas são as etapas gerais deste cenário.

1. O cliente entra no site, localiza um produto que deseja comprar.
1. O cliente seleciona o produto e personaliza algumas opções.
1. O cliente conclui a transação.
1. Um email é enviado ao cliente confirmando a transação. Não queremos enviar PII (Informações de identificação pessoal) pelo email para gerarmos um PDF seguro e o anexar ao email.
1. O cliente recebe o email e seu anexo contendo todos os dados necessários.

Nesse cenário, os anexos não são pré-criados, mas adicionados instantaneamente aos emails de saída. Isso também permite personalizar o conteúdo do anexo. Além disso, se o anexo estiver associado a uma transação (como no exemplo acima), talvez seja necessário que ele contenha dados dinâmicos gerados durante o processo do cliente. Anexar PDFs dessa maneira também otimiza a segurança como você pode criptografa-los e enviá-los por HTTPS.
