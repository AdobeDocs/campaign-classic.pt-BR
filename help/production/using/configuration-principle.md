---
product: campaign
title: Princípio de configuração
description: Princípio de configuração
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---

# Princípio de configuração{#configuration-principle}

![](../../assets/v7-only.svg)

A plataforma Adobe Campaign é baseada no conceito de instâncias, semelhante ao dos hosts virtuais usados pelo Apache. Esse modo de operação permite que você compartilhe um servidor atribuindo várias instâncias a ele. As instâncias são completamente separadas umas das outras e operam com seu próprio banco de dados e arquivo de configuração.

Para um determinado servidor, há dois elementos comuns a todas as instâncias do Adobe Campaign:

* A senha **interna**: esta é a senha do administrador geral. É comum a todas as instâncias de um servidor de aplicativos específico.

   >[!IMPORTANT]
   >
   >Para fazer logon com o identificador **Interno**, é necessário ter definido uma senha antecipadamente. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Várias configurações técnicas do servidor: essas configurações podem ser sobrecarregadas na configuração específica de uma instância.

Os arquivos de configuração são salvos no diretório **conf** do diretório de instalação. A configuração é dividida em três arquivos:

* **serverConf.xml**: configuração geral para todas as instâncias.
* **config-**`<instance>`**.xml**  (onde  **`<instance>`** é o nome da instância): configuração específica de uma instância.
* **serverConf.xml.diff**: delta entre a configuração inicial e a configuração atual. Esse arquivo é gerado automaticamente pelo aplicativo e não deve ser modificado manualmente. Ele é usado para propagar automaticamente as modificações do usuário ao atualizar uma versão de build.

Uma configuração de instância é carregada da seguinte maneira:

* O módulo carrega o arquivo **serverConf.xml** para obter os parâmetros compartilhados por todas as instâncias.
* Em seguida, ele carrega o arquivo **config-**`<instance>`**.xml**. Os valores encontrados neste arquivo têm prioridade sobre os valores contidos em **serverConf.xml**.

   Esses dois arquivos têm o mesmo formato. Qualquer valor em **serverConf.xml** pode ser sobrecarregado para uma determinada instância no arquivo **config-`<instance>`.xml**.

Esse modo operacional oferece grande flexibilidade para configurações.
