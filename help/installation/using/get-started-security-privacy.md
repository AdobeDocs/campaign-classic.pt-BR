---
product: campaign
title: Lista de verificação de segurança e privacidade
description: Saiba mais sobre os principais elementos para verificar a segurança e a privacidade
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 24%

---

# Lista de verificação de segurança e privacidade{#get-started-security-privacy}



Esta seção apresenta os principais elementos para verificar a segurança e a privacidade. Algumas configurações só podem ser executadas por clientes locais.

## Privacidade

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

A configuração e a proteção da privacidade são um elemento essencial da otimização da segurança. Estas são algumas das práticas recomendadas a serem seguidas em relação à privacidade:

* Proteja seu PII de cliente utilizando HTTPS ao invés de HTTP
* Use a restrição de visualização de informações de identificação pessoal (PII) para garantir a privacidade e impedir que os dados sejam utilizados indevidamente.
* Certifique-se de que as senhas criptografadas sejam restritas
* Proteja as páginas que podem conter informações pessoais, como mirror pages, aplicativos web, etc.

[Leia mais](../../installation/using/privacy.md)

## Gerenciamento de acesso

<img src="assets/do-not-localize/icon_access.svg" width="60px">

O gerenciamento de acesso é uma parte importante do fortalecimento da segurança. Estas são algumas das principais práticas recomendadas do:

* Criar grupos de segurança suficientes
* Verifique se cada operador tem os direitos de acesso apropriados
* Evite usar o operador administrador e evite ter muitos operadores no grupo de administradores

[Leia mais](../../installation/using/access-management.md)

## Diretrizes de script e codificação

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Ao desenvolver no Adobe Campaign (workflows, Javascript, JSSP etc.), sempre siga estas diretrizes:

* **Script** lista de permissões : tente evitar instruções SQL. Use funções parametrizadas em vez de concatenação de strings e evite a injeção de SQL adicionando as funções SQL a serem usadas no arquivo de pesquisa.

* **Proteger o modelo de dados**: usar direitos nomeados para limitar as ações do operador, adicionar filtros do sistema (sysFilter)

* **Adicionar captchas em aplicações web**: saiba como adicionar captchas nas páginas de aterrissagem e páginas de assinatura públicas.

[Leia mais](../../installation/using/scripting-coding-guidelines.md)

## Rede, banco de dados e SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Uma coisa muito importante a se verificar ao implantar um tipo de arquitetura local é a configuração de rede.

Também é fundamental que você siga a segurança do mecanismo de banco de dados.

[Leia mais](../../installation/using/network-database.md)

>[!CAUTION]
>
>A partir de 14 de julho de 2021, qualquer sistema cliente que não seja compatível com o protocolo TLS 1.2 perderá o acesso a todos os produtos e serviços da Adobe. Verifique se todos os sistemas de usuários e clientes são compatíveis com TLS 1.2 antes dessa data. [Saiba mais](https://helpx.adobe.com/x-productkb/multi/eol-tls-support.html)

## Configuração do servidor

<img src="assets/do-not-localize/icon_server.svg" width="60px">

A configuração deve ser executada em todos os servidores. Os arquivos de configuração são do tipo **serverConf.xml** e **`config-<instance>.xml`**. Estes são os principais elementos que precisam ser verificados:

* **Zonas de segurança**: configure zonas de segurança para que elas considerem diretamente os endereços IP dos clientes de um proxy.

* **Proteção de upload de arquivo**: limite os tipos de arquivos que podem ser carregados no servidor do Adobe Campaign usando um novo atributo uploadAllowList. Isso pode ser usado no arquivo de configuração do servidor.

* **Retransmissão**: ajuste a configuração de retransmissão desativando as regras de retransmissão para módulos/aplicativos não utilizados.

* **Proteção de conexão de saída** e **Restrição de comando** (lado do servidor)

* Você também pode adicionar cabeçalhos HTTP extras, ativar checkIPConsistent, enableTLS, sessionTimeOutSec, etc. Consulte a [Documentação de configuração do servidor do Campaign](../../installation/using/configuring-campaign-server.md) e a variável [Descrição do arquivo de configuração do servidor](../../installation/using/the-server-configuration-file.md) para obter mais informações.

[Leia mais](../../installation/using/server-configuration.md)

## Configuração do servidor da web

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Várias práticas recomendadas devem ser seguidas ao configurar o servidor Web (Apache/IIS):

* Desabilitar versão e cifras antigas do SSL
* Remova o método TRACE
* Remova o banner
* Limitar o tamanho da consulta para impedir que arquivos importantes sejam carregados

[Leia mais](../../installation/using/web-server-configuration.md)
