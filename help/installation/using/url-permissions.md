---
product: campaign
title: Configurar permissões de URL
description: Saiba como configurar permissões de URL
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 4fd69aa28c2e9325f4738ec571a6632c42ec26b8
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 34%

---

# Configurar permissões de URL (no local){#url-permissions}

![](../../assets/v7-only.svg)

A lista padrão de URLs que podem ser chamados por códigos JavaScript (workflows, etc.) pelas instâncias do Campaign Classic é limitada. Esses são os URLs que permitem que as instâncias funcionem corretamente.

Por padrão, as instâncias não têm permissão para se conectar a URLs externos. No entanto, é possível adicionar URLs externos à lista de URLs autorizados para que sua instância possa se conectar a eles. Dessa forma, você pode conectar as instâncias do Campaign a sistemas externos, como servidores ou sites SFTP para habilitar a transferência de arquivos e/ou dados.

>[!NOTE]
>
>Este procedimento restringe-se a **no local** implantações.
>
>Como um **hospedado** cliente, se você puder acessar [Painel de controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR), você pode usar a interface de autoatendimento de permissões de URL. [Saiba mais](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=pt-BR)
>
>Outras **híbrido/hospedado** Os clientes precisam entrar em contato com a equipe de suporte do Adobe para adicionar IP à.

Para **Híbrido** e **No local** implantações, o administrador precisa fazer referência a um novo **urlPermission** no **serverConf.xml** arquivo.


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
>Por padrão, as novas implementações usam o **Bloqueio** modo.
>
>Como um cliente existente proveniente de uma migração, você pode usar temporariamente o **Aviso** modo. Analise o tráfego de saída antes de permitir os URLs. Após definir a lista de URLs permitidos, é possível adicionar os URLs à lista de permissões e ativar o **Bloqueio** modo.

Para obter mais informações, consulte esta seção.

* [Documentação do Painel de controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [Modelos de hospedagem](hosting-models.md)
* [Configuração do servidor do Campaign](configuring-campaign-server.md)
* [Parâmetros do arquivo de configuração do servidor do Campaign](the-server-configuration-file.md)
* [Lista de verificação de segurança e privacidade](get-started-security-privacy.md)
