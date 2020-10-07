---
title: Princípio de configuração
seo-title: Princípio de configuração
description: Princípio de configuração
seo-description: null
page-status-flag: never-activated
uuid: 6315d526-b820-46ab-96c7-e64e101c6a7d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: d08ff769-da93-4f86-8802-f0fb5b051ece
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 5%

---


# Princípio de configuração{#configuration-principle}

A plataforma Adobe Campaign baseia-se no conceito de instâncias, semelhante ao dos hosts virtuais usados pelo Apache. Esse modo de operação permite que você compartilhe um servidor atribuindo várias instâncias a ele. As instâncias são completamente separadas umas das outras e operam com seu próprio banco de dados e arquivo de configuração.

Para um determinado servidor, há dois elementos comuns a todas as instâncias do Adobe Campaign:

* A senha **interna** : esta é a senha do administrador geral. É comum a todas as instâncias de um servidor de aplicativos específico.

   >[!CAUTION]
   >
   >Para fazer logon com o identificador **Interno** , é necessário ter definido uma senha previamente. Para obter mais informações, consulte [esta seção](../../installation/using/campaign-server-configuration.md#internal-identifier).

* Várias configurações técnicas de servidor: essas configurações podem ser sobrecarregadas na configuração específica de uma instância.

Os arquivos de configuração são salvos no diretório **conf** do diretório de instalação. A configuração é dividida em três arquivos:

* **serverConf.xml**: configuração geral para todas as instâncias.
* **config-**`<instance>`**.xml** (onde **`<instance>`** é o nome da instância): configuração específica de uma instância.
* **serverConf.xml.diff**: entre a configuração inicial e a atual. Esse arquivo é gerado automaticamente pelo aplicativo e não deve ser modificado manualmente. É usado para propagar automaticamente as modificações do usuário ao atualizar uma versão de compilação.

Uma configuração de instância é carregada da seguinte maneira:

* O módulo carrega o arquivo **serverConf.xml** para obter os parâmetros compartilhados por todas as instâncias.
* Em seguida, ele carrega o arquivo **config-**`<instance>`**.xml** . Os valores encontrados neste arquivo têm prioridade sobre os valores contidos em **serverConf.xml**.

   Esses dois arquivos têm o mesmo formato. Qualquer valor em **serverConf.xml** pode ser sobrecarregado para uma determinada instância no arquivo **config-`<instance>`.xml** .

Este modo operacional oferece grande flexibilidade para configurações.
