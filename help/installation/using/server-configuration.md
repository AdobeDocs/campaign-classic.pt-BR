---
product: campaign
title: Configuração de segurança do servidor
description: Saiba mais sobre as práticas recomendadas de configuração do servidor
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: e55fff99fd5dec8da998310dc7026c1a506abadc
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 38%

---

# Configurações de segurança do servidor {#server-configuration}

![](../../assets/v7-only.svg)

## Proteção de upload de arquivo

Verifique com usuários operacionais que tipo de arquivos eles fazem upload para o servidor usando o Console do Cliente do Campaign ou a interface da Web. Como lembrete, as necessidades de negócios podem ser:

* imagens (jpg, gif, png, ...)
* conteúdo (zip, html, css...)
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

Se você estiver usando nomes de host diferentes (um público e um para operadores), também poderá impedir a retransmissão de alguns recursos necessários pelos operadores sobre o nome DNS público.

## Proteção de conexão de saída

A lista padrão de URLs que podem ser chamados por códigos JavaScript (workflows, etc.) é limitada. Para permitir um novo URL, o administrador precisa referenciá-lo no [arquivo serverConf.xml](../../installation/using/the-server-configuration-file.md).

Existem três modos de proteção de conexão:

* **Bloqueio** : todos os URLs fora da lista de permissões são bloqueados, com uma mensagem de erro. Este é o modo padrão depois de um pós-upgrade.
* **Permissivo** : todos os URLs fora da lista de permissões são permitidos.
* **Aviso** : todos os URLs que não estão na lista de permissões são permitidos, mas o interpretador JS emite um aviso, para que o administrador possa coletá-los. Esse modo adiciona mensagens de aviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

Novos clientes usarão o modo de bloqueio. Se eles quiserem permitir um novo URL, eles precisam entrar em contato com o administrador para adicioná-lo à  de lista de permissões.

Os clientes existentes provenientes de uma migração podem usar o modo de aviso por algum tempo. Enquanto isso, eles precisam analisar o tráfego de saída antes de autorizar os URLS.

## Restrição de comando (lado do servidor)

Vários comandos estão incluídos na  de lista de bloqueios e não podem ser executados usando a função execCommand. Uma segurança extra é fornecida por um usuário Unix dedicado para executar comandos externos. Para instalações hospedadas, essa restrição é aplicada automaticamente. Para instalações no local, você pode configurar manualmente essa restrição seguindo as instruções de [esta página](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). Além disso, **[!UICONTROL Script]** e **[!UICONTROL External task]** as atividades do workflow não estão disponíveis (instâncias recém-instaladas).

## Outras configurações

Você pode adicionar cabeçalhos HTTP extras para todas as páginas (para obter mais informações, consulte [esta página](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* Você pode adicionar alguns cabeçalhos adicionais, como HSTS, X-FRAME-OPTIONS, CSP...
* Você precisa testá-los em um ambiente de teste antes de aplicá-los na produção.

   >[!IMPORTANT]
   >
   >O Adobe Campaign pode ser interrompido adicionando determinados cabeçalhos.

O Adobe Campaign permite que você defina uma senha simples no `<dbcnx .../>` elemento. Não use esse recurso.

Por padrão, o Adobe Campaign não coloca uma sessão em um IP específico, mas você pode ativá-lo para impedir que a sessão seja roubada. Para fazer isso, no [arquivo serverConf.xml](../../installation/using/the-server-configuration-file.md), defina o atributo checkIPConsistent como **true** no `<authentication>` nó .

Por padrão, o MTA do Adobe Campaign não usa uma conexão segura para enviar conteúdo ao servidor SMTP. Esse recurso deve ser habilitado (pode reduzir a velocidade de entrega). Para fazer isso, defina **enableTLS** para **true** no `<smtp ...>` nó .

Você pode reduzir a duração de uma sessão no nó de autenticação (atributo sessionTimeOutSec).
