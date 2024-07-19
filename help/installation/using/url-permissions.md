---
product: campaign
title: Configurar permissões de URL
description: Saiba como configurar permissões de URL
feature: Installation, Instance Settings, Permissions
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 31%

---

# Configurar permissões de URL (no local){#url-permissions}



A lista padrão de URLs que podem ser chamados por códigos JavaScript (workflows, etc.) pelas instâncias do Campaign Classic é limitada. Esses são os URLs que permitem que as instâncias funcionem corretamente.

Por padrão, as instâncias não têm permissão para se conectar a URLs externos. No entanto, é possível adicionar URLs externos à lista de URLs autorizados para que sua instância possa se conectar a eles. Dessa forma, você pode conectar as instâncias do Campaign a sistemas externos, como servidores ou sites SFTP para habilitar a transferência de arquivos e/ou dados.

>[!NOTE]
>
>Este procedimento é restrito a **implantações locais**.
>
>Como cliente **hospedado**, se você puder acessar o [Painel de Controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR), poderá usar a interface de autoatendimento de permissões de URL. [Saiba mais](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=pt-BR)
>
>Outros clientes **híbridos/hospedados** precisam entrar em contato com a equipe de suporte do Adobe para adicionar IP ao incluo na lista de permissões.
>

Para implantações **Híbridas** e **No local**, o administrador precisa fazer referência a uma nova **urlPermission** no arquivo **serverConf.xml**.


Três modos de proteção de conexão estão disponíveis:

* **Bloqueio**: todas as URLs fora do arquivo de inclui na lista de permissões são bloqueadas, com uma mensagem de erro. Este é o modo padrão depois de um pós-upgrade.
* **Permissivo**: todas as URLs fora do grupo de inclui na lista de permissões são permitidas.
* **Aviso**: todas as URLs fora do arquivo de inclui na lista de permissões são permitidas, mas o interpretador JS emite um aviso para que o administrador possa coletá-las. Esse modo adiciona mensagens de aviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Por padrão, as novas implementações usam o modo **Bloqueio**.
>
>Como um cliente existente proveniente de uma migração, você pode usar temporariamente o modo **Aviso**. Analise o tráfego de saída antes de permitir os URLs. Após a definição da lista de URLs permitidos, você poderá adicionar as URLs ao incluo na lista de permissões e ativar o modo **Bloqueio**.

Para obter mais informações, consulte esta seção.

* [Documentação do Painel de controle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR)
* [Modelos de hospedagem](hosting-models.md)
* [Configuração do servidor do Campaign](configuring-campaign-server.md)
* [Parâmetros do arquivo de configuração do servidor do Campaign](the-server-configuration-file.md)
* [Lista de verificação de segurança e privacidade](get-started-security-privacy.md)
