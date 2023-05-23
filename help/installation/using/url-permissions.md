---
product: campaign
title: Configurar permissões de URL
description: Saiba como configurar permissões de URL
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 34%

---

# Configurar permissões de URL (no local){#url-permissions}



A lista padrão de URLs que podem ser chamados por códigos JavaScript (workflows, etc.) pelas instâncias do Campaign Classic é limitada. Esses são os URLs que permitem que as instâncias funcionem corretamente.

Por padrão, as instâncias não têm permissão para se conectar a URLs externos. No entanto, é possível adicionar URLs externos à lista de URLs autorizados para que sua instância possa se conectar a eles. Dessa forma, você pode conectar as instâncias do Campaign a sistemas externos, como servidores ou sites SFTP para habilitar a transferência de arquivos e/ou dados.

>[!NOTE]
>
>Este procedimento é limitado a **no local** implantações.
>
>Como um **hospedado** cliente, se você puder acessar [Painel de controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR), você pode usar a interface de autoatendimento de permissões de URL. [Saiba mais](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=pt-BR)
>
>Outro **híbrido/hospedado** os clientes precisam entrar em contato com a equipe de suporte do Adobe para adicionar IP ao incluo na lista de permissões.

Para **Híbrido** e **No local** implantações, o administrador precisa consultar um novo **urlPermission** no **serverConf.xml** arquivo.


Três modos de proteção de conexão estão disponíveis:

* **Bloqueio** lista de permissões : todos os URLs que não pertencem ao arquivo de classificação são bloqueados, com uma mensagem de erro. Este é o modo padrão depois de um pós-upgrade.
* **Permissivo**: todos os URLs fora do incluo na lista de permissões são permitidos.
* **Aviso** lista de permissões : todos os URLs que não pertencem ao arquivo são permitidos, mas o interpretador JS emite um aviso para que o administrador possa coletá-los. Esse modo adiciona mensagens de aviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Por padrão, novas implementações usam a variável **Bloqueio** modo.
>
>Como um cliente existente proveniente de uma migração, você pode usar temporariamente o **Aviso** modo. Analise o tráfego de saída antes de permitir os URLs. Depois que a lista de URLs permitidos for definida, você poderá adicionar os URLs ao incluo na lista de permissões e ativar o **Bloqueio** modo.

Para obter mais informações, consulte esta seção.

* [Documentação do Painel de controle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR)
* [Modelos de hospedagem](hosting-models.md)
* [Configuração do servidor do Campaign](configuring-campaign-server.md)
* [Parâmetros do arquivo de configuração do servidor do Campaign](the-server-configuration-file.md)
* [Lista de verificação de segurança e privacidade](get-started-security-privacy.md)
