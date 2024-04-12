---
product: campaign
title: Princípio de configuração
description: Princípio de configuração
feature: Monitoring, Configuration
badge-v7-prem: label="No local e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 8%

---

# Princípio de configuração{#configuration-principle}



A plataforma Adobe Campaign é baseada no conceito de instâncias, semelhante ao de hosts virtuais usados pelo Apache. Esse modo de operação permite que você compartilhe um servidor atribuindo várias instâncias a ele. As instâncias são completamente separadas umas das outras e operam com seu próprio banco de dados e arquivo de configuração.

Para um determinado servidor, há dois elementos comuns a todas as instâncias do Adobe Campaign:

* A variável **interno** senha: esta é a senha do administrador geral. É comum a todas as instâncias de um determinado servidor de aplicativos.

  >[!IMPORTANT]
  >
  >Para fazer logon com a **Interno** identificador, você precisa ter definido uma senha antes. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Várias configurações técnicas de servidor: essas configurações podem ser sobrecarregadas na configuração específica de uma instância.

Os arquivos de configuração são salvos na variável **conf** diretório de instalação. A configuração é dividida em três arquivos:

* **serverConf.xml**: configuração geral para todas as instâncias.
* **config-**`<instance>`**.xml** (onde **`<instance>`** é o nome da instância ): configuração específica de uma instância.
* **serverConf.xml.diff**: delta entre a configuração inicial e a configuração atual. Esse arquivo é gerado automaticamente pelo aplicativo e não deve ser modificado manualmente. É usado para propagar automaticamente as modificações do usuário ao atualizar uma versão de build.

Uma configuração de instância é carregada da seguinte maneira:

* O módulo carrega o **serverConf.xml** para obter os parâmetros compartilhados por todas as instâncias.
* Em seguida, carrega o **config-**`<instance>`**.xml** arquivo. Os valores encontrados neste arquivo têm prioridade sobre os valores contidos em **serverConf.xml**.

  Esses dois arquivos têm o mesmo formato. Qualquer valor em **serverConf.xml** pode ser sobrecarregado para uma determinada instância no **config-`<instance>`.xml** arquivo.

Esse modo operacional oferece grande flexibilidade para configurações.
