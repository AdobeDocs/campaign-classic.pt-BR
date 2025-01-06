---
product: campaign
title: Teste da migração
description: Teste da migração
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Testes de migração{#testing-the-migration}



## Procedimento geral {#general-procedure}

Dependendo da sua configuração, há várias maneiras de realizar testes de migração.

Você deve ter um ambiente de teste/desenvolvimento para realizar testes de migração. Os ambientes Adobe Campaign estão sujeitos à licença: verifique seu contrato de licença ou entre em contato com o representante da Adobe.

1. Interrompa todos os desenvolvimentos em andamento e transfira-os para o ambiente de produção.
1. Faça um backup do banco de dados do ambiente de desenvolvimento.
1. Pare todos os processos do Adobe Campaign na instância de desenvolvimento.
1. Faça um backup do banco de dados do ambiente de produção e restaure-o como um ambiente de desenvolvimento.
1. Antes de iniciar os serviços do Adobe Campaign, execute o script de cauterização **freezeInstance.js** que permite limpar o banco de dados de todos os objetos que estavam em execução quando o backup foi iniciado.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >O comando é iniciado por padrão no modo **dry** e lista todas as solicitações que foram executadas por esse comando, sem inicializá-las. Para executar solicitações de cauterização, use **run** no comando.

1. Verifique se os backups estão corretos tentando restaurá-los. Verifique se você pode acessar o banco de dados, as tabelas, os dados etc.
1. Testar o procedimento de migração no ambiente de desenvolvimento.
1. Se a migração do ambiente de desenvolvimento tiver êxito, você poderá migrar o ambiente de produção.

>[!CAUTION]
>
>Devido a alterações feitas na estrutura de dados, não é possível importar e exportar pacotes de dados entre uma plataforma v5 e uma plataforma v7.


## Ferramentas de migração {#migration-tools}

Várias opções permitem medir o impacto de uma migração e identificar os possíveis problemas. Estas opções devem ser executadas:

* no comando **config**:

  ```
  nlserver.exe config <option> -instance:<instance-name>
  ```

* ou no pós-atualização:

  ```
  nlserver.exe config -postupgrade <option> -instance:<instance-name>
  ```

>[!NOTE]
>
>* Você deve usar a opção **-instance:`<instanceame>`**. Não recomendamos o uso da opção **-allinstances**.
>* O comando Adobe Campaign update (**postupgrade**) permite sincronizar recursos e atualizar esquemas e o banco de dados. Esta operação só pode ser executada uma vez e somente no servidor de aplicativos. Após sincronizar recursos, o comando **postupgrade** permite detectar se a sincronização gera erros ou avisos.

### Objetos não padrão ou ausentes

* A opção **-showCustomEntities** exibe a lista de todos os objetos não padrão:

  ```
  nlserver.exe config -showCustomEntities -instance:<instance-name>
  ```

  Exemplo de mensagem enviada:

  ```
  xtk_migration:opsecurity2 xtk:entity
  ```

* A opção **-showDeletedEntities** exibe a lista de todos os objetos padrão que estão ausentes no banco de dados ou no sistema de arquivos. Para cada objeto ausente, o caminho é especificado.

  ```
  nlserver.exe config -showDeletedEntities -instance:<instance-name>
  ```

  Exemplo de mensagem enviada:

  ```
  Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
  ```

### Processo de verificação {#verification-process}

Integrado como padrão no comando postupgrade, esse processo permite exibir avisos e erros que podem fazer com que a migração falhe. **Se forem exibidos erros, a migração não foi executada.** Se isso acontecer, corrija todos os erros e reinicie a pós-atualização.

Você pode iniciar o processo de verificação por conta própria (sem migração) usando o comando:

```
nlserver.exe config -postupgrade -check -instance:<instance-name>
```

>[!NOTE]
>
>Você pode ignorar todos os avisos e erros com o código JST-310040.

As seguintes expressões são pesquisadas (distinção entre maiúsculas e minúsculas):

<table> 
 <thead> 
  <tr> 
   <th> Expressão<br /> </th> 
   <th> Código de erro <br /> </th> 
   <th> Tipo de log<br /> </th> 
   <th> Comentários<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Esse tipo de sintaxe não é mais suportado na personalização da entrega. <br /> </td> 
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
   <td> Este método de conexão não deve mais ser usado.<br /> </td> 
  </tr> 
  <tr> 
   <td> nova SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Esta função só tem suporte quando é usada no código JavaScript executado de uma zona de segurança que está no modo <strong>sessionTokenOnly</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Erro<br /> </td> 
   <td> Esse tipo de erro leva a uma falha de migração.<br /> </td> 
  </tr> 
  <tr> 
   <td> crmDeploymentType="no local"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> Erro<br /> </td> 
   <td> Esse tipo de implantação não é mais suportado. O Office 365 e o tipo de implantação do conector do Microsoft CRM no local foram descontinuados. 
   </br>Se você estiver usando um desses tipos de implantação obsoletos em uma conta externa, essa conta externa deverá ser excluída e você deverá executar o comando <b>postupgrade</b>. 
   </br>Para alterar para implantação da API Web, consulte <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Aplicativos Web</a>.<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1(mscrmWorkflow/sfdcWorkflow)<br /> </td> 
   <td> PU-0008<br /> </td> 
   <td> Erro<br /> </td> 
   <td> As atividades de ação por demanda do Microsoft CRM, Salesforce, Oracle CRM não estão mais disponíveis. Para configurar a sincronização de dados entre o Adobe Campaign e um sistema CRM, você precisa usar a atividade de direcionamento <a href="../../workflow/using/crm-connector.md" target="_blank">conector do CRM</a>.<br /> </td>
  </tr> 
 </tbody> 
</table>

Também é realizada uma verificação de coerência do banco de dados e do esquema.

### Opção de restauração {#restoration-option}

Essa opção permite restaurar objetos prontos para uso se eles tiverem sido modificados. Para cada objeto restaurado, um backup das alterações é armazenado na pasta selecionada:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instance-name>
```

>[!NOTE]
>
>É altamente recomendável usar caminhos absolutos de pastas e manter a estrutura de árvore de pastas. Por exemplo: backupFolder\nms\srcSchema\billing.xml.

### Continuar a migração {#resuming-migration}

Se você reiniciar o pós-upgrade após uma falha de migração, ele será retomado do mesmo local em que foi interrompido.
