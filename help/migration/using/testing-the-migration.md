---
solution: Campaign Classic
product: campaign
title: Teste da migração
description: Teste da migração
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 2%

---


# Teste da migração{#testing-the-migration}

## Procedimento geral {#general-procedure}

Dependendo da sua configuração, há várias maneiras de realizar testes de migração.

Você deve ter um ambiente de teste/desenvolvimento para realizar testes de migração. Os ambientes de desenvolvimento estão sujeitos a licença: verifique seu contrato de licença ou entre em contato com o serviço de vendas da Adobe Campaign.

1. Parem todos os desenvolvimentos em curso e levem-nos para o ambiente de produção.
1. Faça um backup do banco de dados de ambientes de desenvolvimento.
1. Pare todos os processos do Adobe Campaign na instância de desenvolvimento.
1. Faça backup do banco de dados do ambiente de produção e restaure-o como um ambiente de desenvolvimento.
1. Antes de iniciar os serviços Adobe Campaign, execute o script de cauterização **congelamentoInstance.js** que permite limpar o banco de dados de quaisquer objetos que estavam sendo executados quando o backup foi iniciado.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >O comando é iniciado por padrão no modo **seco** e lista todas as solicitações que foram executadas por esse comando, sem iniciá-las. Para executar solicitações de cauterização, use **executar** no comando.

1. Certifique-se de que seus backups estejam corretos tentando restaurá-los. Verifique se você pode acessar seu banco de dados, suas tabelas, seus dados etc.
1. Teste o procedimento de migração no ambiente de desenvolvimento.

   Os procedimentos completos estão detalhados na seção [Pré-requisitos para migração para o Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .

1. Se a migração do ambiente de desenvolvimento for bem-sucedida, você poderá migrar o ambiente de produção.

>[!IMPORTANT]
>
>Devido a alterações feitas na estrutura de dados, não é possível importar e exportar pacotes de dados entre uma plataforma v5 e uma plataforma v7.

>[!NOTE]
>
>O comando de atualização da Adobe Campaign (**pós-atualização**) permite sincronizar recursos e atualizar schemas e o banco de dados. Essa operação só pode ser realizada uma vez e somente no servidor de aplicativos. Depois de sincronizar os recursos, o comando **pós-atualização** permite detectar se a sincronização gera erros ou avisos.

## Ferramentas de migração {#migration-tools}

Várias opções permitem medir o impacto de uma migração e identificar os possíveis problemas. Essas opções devem ser executadas:

* no comando **config** :

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* ou no pós-upgrade:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>Você deve usar a **instância:`<instanceame>`** opção. Não recomendamos o uso da opção **-allinnesse** caso.

### -showCustomEntities e -showDeletedEntities {#showcustomentities-and--showdeletedentities-options}

* A opção **-showCustomEntities** exibe a lista de todos os objetos não padrão:

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   Exemplo de uma mensagem enviada:

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* A opção **-showDeletedEntities** exibe a lista de todos os objetos padrão que estão faltando no banco de dados ou no sistema de arquivos. Para cada objeto ausente, o caminho é especificado.

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   Exemplo de uma mensagem enviada:

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### Processo de verificação {#verification-process}

Integrado como padrão no comando pós-atualização, esse processo permite que você exiba avisos e erros que podem fazer a migração falhar. **Se forem exibidos erros, a migração não será executada.** Se isso acontecer, corrija todos os erros e, em seguida, start novamente a pós-atualização.

Você pode start o processo de verificação sozinho (sem migração) usando o comando:

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>Ignore todos os avisos e erros que têm o código JST-310040.

As seguintes expressões são pesquisadas (diferencia maiúsculas de minúsculas):

<table> 
 <thead> 
  <tr> 
   <th> Expressão<br /> </th> 
   <th> Código de erro<br /> </th> 
   <th> Tipo de registro<br /> </th> 
   <th> Comentários<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Esse tipo de sintaxe não é mais suportado na personalização do delivery. Consulte <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>. Caso contrário, verifique se o tipo de valor está correto.<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Esta biblioteca não deve ser usada.<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Este método de conexão não deve mais ser usado. Consulte Aplicativos <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">da Web</a>identificados.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Essa função só é suportada quando é usada no código JavaScript executado de uma zona de segurança que está no modo <strong>sessionTokenOnly</strong> .<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Error<br /> </td> 
   <td> Esse tipo de erro resulta em uma falha de migração. Consulte <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> Error<br /> </td> 
   <td> Esse tipo de erro resulta em uma falha de migração. Consulte <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>. Se você obtiver registros de erros do aplicativo da Web tipo visão geral (migração da v6.02), consulte <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Aplicação web</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

É igualmente efetuada uma verificação da coerência entre a base de dados e os schemas.

### Opção de restauração {#restoration-option}

Essa opção permite restaurar objetos predefinidos se tiverem sido modificados. Para cada objeto restaurado, um backup das alterações é armazenado na pasta selecionada:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>Recomendamos usar caminhos absolutos de pastas e manter a estrutura de árvore de pastas. Por exemplo: backupFolder\nms\srcSchema\billing.xml.

### Retomando a migração {#resuming-migration}

Se você reiniciar a pós-atualização após uma falha de migração, ela será retomada do mesmo local em que foi interrompida.
