---
product: campaign
title: Lista de verificação de segurança e privacidade
description: Saiba mais sobre os principais elementos para verificar a segurança e a privacidade
feature: Installation, Privacy, Access Management, Privacy Tools
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
TQID: https://experienceleague.adobe.com/UvWC8wEoOcNmpLClAoF-pK8WaPNZTzoLbGaF6nwUKDw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
subfeature_v2: id: ac72e249-ebbf-4bb6-96c9-596af925419aid: ac9c0a9c-8a76-4419-bd64-9c34c5782666id: fb2a841f-c522-491f-9901-a1b939d252df
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: d095671a-1355-40aa-8b5f-06c33c68080bid: e0eb8757-182f-49f3-94a4-1587d16f5094id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 450
ht-degree: 22%

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

* **Scripting**: tente evitar instruções SQL. Use funções parametrizadas em vez de concatenação de cadeias de caracteres e evite a injeção de SQL adicionando as funções SQL a serem usadas no incluo na lista de permissões.

* **Proteger o modelo de dados**: use direitos nomeados para limitar ações do operador, adicionar filtros do sistema (sysFilter)

* **Adicionar captchas em aplicativos da Web**: saiba como adicionar captchas em suas páginas de aterrissagem e páginas de assinatura públicas.

[Leia mais](../../installation/using/scripting-coding-guidelines.md)

## Rede, banco de dados e SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Uma coisa muito importante a se verificar ao implantar um tipo de arquitetura local é a configuração de rede.

Também é fundamental que você siga a segurança do mecanismo de banco de dados.

[Leia mais](../../installation/using/network-database.md)


## Configuração do servidor

<img src="assets/do-not-localize/icon_server.svg" width="60px">

A configuração deve ser executada em todos os servidores. Os arquivos de configuração são do tipo **serverConf.xml** e **`config-<instance>.xml`**. Estes são os principais elementos que precisam ser verificados:

* **Zonas de segurança**: configure zonas de segurança para que elas levem em conta diretamente os endereços IP dos clientes de um proxy.

* **Proteção de carregamento de arquivo**: limite os tipos de arquivos que podem ser carregados no servidor do Adobe Campaign usando um novo atributo uploadAllowList. Isso pode ser usado no arquivo de configuração do servidor.

* **Retransmissão**: ajuste a configuração de retransmissão desativando as regras de retransmissão para módulos/aplicativos não usados.

* **Proteção de conexão de saída** e **Restrição de comando** (lado do servidor)

* Você também pode adicionar cabeçalhos HTTP extras, ativar checkIPConsistent, enableTLS, sessionTimeOutSec, etc. Consulte a [Documentação de configuração do servidor de campanha](../../installation/using/configuring-campaign-server.md) e a [Descrição do arquivo de configuração do servidor](../../installation/using/the-server-configuration-file.md) para obter mais informações.

[Leia mais](../../installation/using/server-configuration.md)

## Configuração do servidor da web

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Várias práticas recomendadas devem ser seguidas ao configurar o servidor Web (Apache/IIS):

* Desabilitar versão e cifras antigas do SSL
* Remover o método TRACE
* Remova o banner
* Limitar o tamanho da consulta para impedir que arquivos importantes sejam carregados

[Leia mais](../../installation/using/web-server-configuration.md)
