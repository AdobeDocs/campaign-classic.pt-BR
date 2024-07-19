---
product: campaign
title: Configuração de segurança do servidor
description: Saiba mais sobre as práticas recomendadas de configuração do servidor
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 37%

---

# Configurações de segurança do servidor {#server-configuration}

## Proteção de upload de arquivo

Verifique com os usuários operacionais que tipo de arquivos eles enviam ao servidor usando o Console do cliente do Campaign ou a interface da Web. Lembrando que as necessidades da empresa podem ser:

* imagens (jpg, gif, png etc.)
* conteúdo (zip, html, css ...)
* ativos de marketing (doc, xls, pdf, psd, tiff, ...)
* anexo de email (doc, pdf, ...)
* ETL (txt, csv, guia, ...)
* etc.

Adicione todos eles em serverConf/shared/datastore/@uploadAllowlist (expressão Java regular válida). Saiba mais [nesta página](../../installation/using/file-res-management.md).

O Adobe Campaign não restringe o tamanho do arquivo. Mas você pode fazê-lo configurando o IIS/Apache. Saiba mais [nesta seção](../../installation/using/web-server-configuration.md).

## Retransmissão

Consulte [esta página](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) para obter mais informações.

Por padrão, todas as páginas dinâmicas são automaticamente retransmitidas para o servidor Tomcat local da máquina cujo módulo da Web foi iniciado. É possível optar por não retransmitir alguns deles. Se alguns módulos do Adobe Campaign não estiverem sendo usados (como aplicação Web, interação, algum jsp), podem ser removidos das regras de retransmissão. 

Pronto para uso, forçamos a capacidade de exibir recursos do usuário final usando http (httpAllowed=&quot;true&quot;). Como estas páginas podem mostrar algum PII (como conteúdo de email, endereço), cupons de resgate, ofertas, você deverá forçar novamente o HTTPS nesses caminhos.

Se você estiver usando nomes de host diferentes (um público e um para operadores), também poderá impedir o relé de alguns recursos necessários pelos operadores sobre o nome DNS público.

## Proteção de conexão de saída

A lista padrão de URLs que podem ser chamados por códigos JavaScript (workflows, etc.) é limitada. Para permitir uma nova URL, o administrador precisa referenciá-la no [arquivo serverConf.xml](../../installation/using/the-server-configuration-file.md).

Existem três modos de proteção de conexão:

* **Bloqueio**: todas as URLs fora do arquivo de inclui na lista de permissões são bloqueadas, com uma mensagem de erro. Este é o modo padrão depois de um pós-upgrade.
* **Permissivo**: todas as URLs fora do grupo de inclui na lista de permissões são permitidas.
* **Aviso**: todas as URLs que não estão na inclui na lista de permissões são permitidas, mas o interpretador JS emite um aviso para que o administrador possa coletá-las. Esse modo adiciona mensagens de aviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

Novos clientes usarão o modo de bloqueio. Se ele quiser permitir um novo URL, será necessário entrar em contato com o administrador para adicioná-lo ao arquivo de inclui na lista de permissões.

Os clientes existentes provenientes de uma migração podem usar o modo de aviso por algum tempo. Enquanto isso, é necessário analisar o tráfego de saída antes de autorizar os URLS.

## Restrição de comando (lado do servidor)

Vários comandos estão incluídos no incluo na lista de bloqueios e não podem ser executados usando a função execCommand. Uma segurança extra é fornecida por um usuário Unix dedicado para executar comandos externos. Para instalações hospedadas, essa restrição é aplicada automaticamente. Para instalações locais, você pode configurar manualmente essa restrição seguindo as instruções de [esta página](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). Além disso, as atividades de fluxo de trabalho **[!UICONTROL Script]** e **[!UICONTROL External task]** não estão disponíveis (instâncias recém-instaladas).

## Outras configurações

Você pode adicionar cabeçalhos HTTP extras para todas as páginas (para obter mais informações, consulte [esta página](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* Você pode adicionar alguns cabeçalhos adicionais, como HSTS, X-FRAME-OPTIONS, CSP...
* Você precisa testá-los em um ambiente de teste antes de aplicá-los na produção.

  >[!IMPORTANT]
  >
  >O Adobe Campaign pode ser interrompido adicionando determinados cabeçalhos.

O Adobe Campaign permite definir uma senha simples no elemento `<dbcnx .../>`. Não use este recurso.

Por padrão, o Adobe Campaign não coloca uma sessão em um IP específico, mas você pode ativá-lo para impedir que a sessão seja roubada. Para fazer isso, defina no [arquivo serverConf.xml](../../installation/using/the-server-configuration-file.md) o atributo checkIPConsistent como **true** no nó `<authentication>`.

Por padrão, o MTA do Adobe Campaign não usa uma conexão segura para enviar conteúdo ao servidor SMTP. Esse recurso deve ser habilitado (pode reduzir a velocidade de entrega). Para fazer isso, defina **enableTLS** como **true** no nó `<smtp ...>`.

Você pode reduzir o tempo de vida de uma sessão no nó de autenticação (atributo sessionTimeOutSec).
