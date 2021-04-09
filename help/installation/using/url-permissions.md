---
solution: Campaign Classic
product: campaign
title: Configurar permissões de URL
description: Saiba como configurar permissões de URL
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 36%

---


# Configurar permissões de URL {#url-permissions}

A lista padrão de URLs que podem ser chamados por códigos JavaScript (workflows, etc.) pelas instâncias do Campaign Classic é limitada. Esses são os URLs que permitem que as instâncias funcionem corretamente.

Por padrão, as instâncias não têm permissão para se conectar a URLs externos. No entanto, é possível adicionar URLs externos à lista de URLs autorizados para que sua instância possa se conectar a eles. Dessa forma, você pode conectar as instâncias do Campaign a sistemas externos, como servidores ou sites SFTP para habilitar a transferência de arquivos e/ou dados.

Para implantações **Hybrid** e **No local**, o administrador precisa fazer referência a um novo **urlPermission** no arquivo **serverConf.xml**.

Três modos de proteção de conexão estão disponíveis:

* **Bloqueio**: todos os URLs fora da lista de permissões são bloqueados, com uma mensagem de erro. Este é o modo padrão depois de um pós-upgrade.
* **Permissivo**: todos os URLs fora da lista de permissões são permitidos.
* **Aviso**: todos os URLs que não pertencem à lista de permissões são permitidos, mas o interpretador JS emite um aviso para que o administrador possa coletá-los. Esse modo adiciona mensagens de aviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Por padrão, novas implementações usam o modo **Bloqueio**.
>
>Como um cliente existente proveniente de uma migração, você pode usar temporariamente o modo **Aviso**. Analise o tráfego de saída antes de permitir os URLs. Após definir a lista de URLs permitidos, é possível adicionar os URLs à lista de permissões e ativar o modo **Bloqueio**.

Para obter mais informações, consulte esta seção.

* [Documentação do Painel de controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR)
* [Modelos de hospedagem](hosting-models.md)
* [Configuração do servidor do Campaign](configuring-campaign-server.md)
* [Parâmetros do arquivo de configuração do servidor do Campaign](the-server-configuration-file.md)
* [Lista de verificação de segurança e privacidade](get-started-security-privacy.md)