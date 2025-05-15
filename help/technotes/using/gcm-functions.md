---
product: campaign
title: Novas funções baseadas em GCM
description: Novas funções baseadas em GCM
feature: Technote
exl-id: 154dee7a-a1e9-40a2-bfa5-3641382d0574
source-git-commit: b6d64f66d287dba79be5eddec48ee852c2c7740c
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 2%

---

# Funções baseadas em GCM {#new-functions}

Para melhorar a segurança, substituímos o uso do algoritmo AES (Advanced Encryption Standard) pelo modo CBC (Cipher Block Chaining) para operações criptográficas. Novas funções de criptografia foram introduzidas. Essas funções usam AES com Galois/Counter Mode (AES-GCM), fornecendo uma alternativa mais segura. Essas funções estão disponíveis no JavaScript, JSP, APIs do SOAP e esquemas XML, permitindo que os clientes façam a transição do CBC para o GCM para criptografia e descriptografia.

Esta documentação lista as funções AES-GCM recém-introduzidas e as funções baseadas em CBC que estão sendo substituídas.

Novas funções:

* [Função de API EncryptString](#encryptString-api-xtk)
* [Função de API EncryptStringWithServerPassword](#EncryptStringWithServerPassword-api-xtk)
* [função javascript encryptString](#encryptString-javascript)

Funções herdadas que podem ser usadas para o GCM:

* [Função JavaScript DecryptString](#decryptString-javascript)
* [Função javascript DecryptPassword](#decryptPassword-javascript)

[Funções obsoletas](#depracated-functions)

## Funções da API

### EncryptString {#encryptString-api-xtk}

Criptografa a cadeia de caracteres com a chave de instância usando o algoritmo AES com o modo GCM.

```
            String 
            encrypted = EncryptString (
            String       
            decrypted
            

      )
         
```

**Parâmetros**: texto descriptografado

**Valor(es) de retorno**: criptografado(s)

**Esquema**: xtk:session

**Estático**: sim

## EncryptStringWithServerPassword {#EncryptStringWithServerPassword-api-xtk}

Criptografa a cadeia de caracteres com a chave do servidor usando o algoritmo AES com o modo GCM.


```
            String 
            encrypted = EncryptStringWithServerPassword (
            String       
            decrypted
            

      )
         
```

**Parâmetros**: Descriptografados

**Valor(es) de retorno**: criptografado(s)

**Esquema**: xtk:session

**Estático**: sim

## Funções JavaScript

### encryptString() {#encryptString-javascript}

Criptografa uma cadeia de caracteres com a chave da instância ou qualquer outra chave.

```
            encryptString (str [, key
      ] [, useSalt ])
         
```

**Parâmetros**:

* str: a sequência de caracteres a ser criptografada.
* chave: a chave de criptografia AES é codificada na base 64: 256 bits se o comprimento da chave for 32; 192 bits se o comprimento da chave for 24; 128 bits se o comprimento da chave for 16 ou se nenhuma chave for especificada.
* useSalt: use um salt dos dados para criptografar. Verdadeiro por padrão.

**Valor de retorno**: retorna a cadeia de caracteres criptografada.

**Comentários**

A criptografia ocorre de acordo com o seguinte método:

* A sequência de caracteres unicode é transformada em uma sequência UTF-8.
* Um caractere de verificação é adicionado em texto cifrado no final.
* Essa string é criptografada usando o algoritmo AES no modo Galois/Counter Mode (GCM) usando salt com um vetor de inicialização de 12 bytes e uma tag de 16 bytes. Se nenhuma chave for fornecida como parâmetro, a chave da instância será usada.
* O texto codificado conterá a tag e o vetor de inicialização.
* O bloco criptografado é então convertido na base 64.

A descriptografia é realizada usando a função decryptString.

**Recursos**

Disponível em:

* Gestão de conteúdo
* Propriedades de entrega
* Mensagem de entrega
* Regra de tipologia
* Importação
* JSSP
* Método SOAP
* WebApp
* Fluxo de trabalho

### decryptString() {#decryptString-javascript}

Descriptografa uma cadeia de caracteres com a chave da instância ou qualquer outra chave. Essa função herdada pode ser usada com o GCM. Ele está obsoleto para a descriptografia de texto criptografado usando o modo AES-CBC.

```
            decryptString (str [, key
      ] [, useSalt ])
         
```

**Parâmetros**:

* str: a sequência de caracteres a ser descriptografada.
* chave: a chave de criptografia AES é codificada na base 64: 256 bits se o comprimento da chave for 32; 192 bits se o comprimento da chave for 24; 128 bits se o comprimento da chave for 16 ou se nenhuma chave for especificada.
* useSalt: use um salt dos dados para descriptografar. Verdadeiro por padrão.

**Valor de retorno**: retorna a cadeia de caracteres descriptografada.

**Aviso**: as senhas armazenadas no banco de dados (opções/contas externas) não podem mais ser descriptografadas pelo uso deste método. Para isso, use [decryptPassword](#decryptPassword-javascript).

### decryptPassword() {#decryptPassword-javascript}

Descriptografa uma senha armazenada em uma conta externa. Essa função herdada pode ser usada com o GCM. Ele está obsoleto para a descriptografia de texto criptografado usando o modo AES-CBC.

```
            decryptPassword (str)
         
```

**Parâmetros**:

* str: a sequência de caracteres a ser descriptografada.

**Valor de retorno**: retorna a senha de texto simples.

**Comentários**

Esta função não pode ser chamada em workflows, aplicativos web, relatórios ou deliveries. Ele pode ser chamado em implementações de chamada JSSP ou SOAP. Exemplo:

```
        function nms_extAccount_LogonToRemoteInstance(remoteInstanceUrl, login, encryptedPassword) {
        var cnx = null, sessionService = null;
        try
            {
                var cnx = new HttpSoapConnection(remoteInstanceUrl + '/nl/jsp/soaprouter.jsp', 'utf-8', 0);
                sessionService = new SoapService(cnx, 'xtk:session');
                sessionService.addMethod("Logon", "xtk:session#Logon",
                    ["token", "string", "login", "string", "password", "string", "parameters", "NLElement"],
                    ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
                return sessionService.Logon("", login, decryptPassword(encryptedPassword), <parameters/>);
            }
        catch( e ) {
        logError(e);
        }
        finally {
        if( sessionService ) sessionService.dispose();
        if( cnx ) cnx.dispose();
        }
        })
      
```

## Funções obsoletas {#depracated-functions}

As seguintes funções foram totalmente descontinuadas:

* cryptString
* Criptografar
* EncryptServerPassword
