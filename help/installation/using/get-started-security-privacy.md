---
product: campaign
title: Introdução à segurança e privacidade
description: Saiba mais sobre os principais elementos a serem verificados em relação à segurança e privacidade.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 32%

---

# Introdução à segurança e privacidade {#get-started-security-privacy}

![](../../assets/v7-only.svg)

Esta seção apresentará os principais elementos sobre segurança e privacidade. Algumas configurações só podem ser executadas por clientes locais.

## Privacidade

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

A configuração e proteção da privacidade é um elemento essencial da otimização da segurança. Estas são algumas das práticas recomendadas relacionadas à privacidade:

* Proteja seu PII de cliente utilizando HTTPS ao invés de HTTP
* Use a restrição de visualização de informações de identificação pessoal (PII) para garantir a privacidade e impedir que os dados sejam utilizados indevidamente.
* Certifique-se de que as senhas criptografadas sejam restritas
* Proteja as páginas que podem conter informações pessoais, como mirror pages, aplicativos web, etc.

[Leia mais](../../installation/using/privacy.md)

## Gerenciamento de acesso

<img src="assets/do-not-localize/icon_access.svg" width="60px">

O gerenciamento de acesso é uma parte importante do fortalecimento da segurança. Estas são algumas das principais práticas recomendadas:

* Criar grupos de segurança suficientes
* Verifique se cada operador tem os direitos de acesso apropriados
* Evite usar o operador administrador e evite ter muitos operadores no grupo de administradores

[Leia mais](../../installation/using/access-management.md)

## Diretrizes de script e codificação

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Ao desenvolver no Adobe Campaign (fluxos de trabalho, Javascript, JSSP etc.), sempre siga estas diretrizes:

* **Scripting**: tente evitar instruções SQL. Use funções parametrizadas em vez de concatenação de strings e evite a injeção de SQL colocando as funções SQL a serem utilizadas na lista de permissões.

* **Proteger o modelo** de dados: use direitos nomeados para limitar as ações do operador, adicione filtros do sistema (sysFilter)

* **Adicionar captchas em aplicações** web: saiba como adicionar captchas em suas páginas de aterrissagem e páginas de assinatura públicas.

[Leia mais](../../installation/using/scripting-coding-guidelines.md)

## Rede, banco de dados e SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Uma coisa muito importante a se verificar ao implantar um tipo de arquitetura local é a configuração de rede.

Também é fundamental seguir a segurança do mecanismo de banco de dados.

[Leia mais](../../installation/using/network-database.md)

## Configuração do servidor

<img src="assets/do-not-localize/icon_server.svg" width="60px">

A configuração deve ser executada em todos os servidores. Os arquivos de configuração são do tipo **serverConf.xml** e **`config-<instance>.xml`**. Estes são os principais elementos que precisam ser verificados:

* **Zonas** de segurança: Configure as zonas de segurança para que elas considerem diretamente os endereços IP dos clientes de um proxy.

* **Proteção** de upload de arquivo: limite os tipos de arquivos que podem ser carregados no servidor do Adobe Campaign usando um novo atributo uploadAllowList . Isso pode ser usado no arquivo de configuração do servidor.

* **Retransmissão**: ajuste a configuração de retransmissão desativando as regras de retransmissão para módulos/aplicativos não utilizados.

* **Proteção** de conexão de saída e restrição  **de comando**  (lado do servidor)

* Você também pode adicionar cabeçalhos HTTP extras, ativar checkIPConsistent, enableTLS, sessionTimeOutSec, etc. Consulte a [documentação de configuração do servidor do Campaign](../../installation/using/configuring-campaign-server.md) e a [Descrição do arquivo de configuração do servidor](../../installation/using/the-server-configuration-file.md) para obter mais informações.

[Leia mais](../../installation/using/server-configuration.md)

## Configuração do servidor da web

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Várias práticas recomendadas devem ser seguidas ao configurar seu servidor da Web (Apache/IIS):

* Desative a versão e as cifras SSL antigas
* Remova o método TRACE
* Remova o banner
* Limite o tamanho da consulta para impedir que arquivos importantes sejam carregados

[Leia mais](../../installation/using/web-server-configuration.md)
