---
product: campaign
title: Teste da migração
description: Teste da migração
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 59a2bc62b4c03ef0702cb57bd9dc808e7d0b444b
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 3%

---

# Testes de migração{#testing-the-migration}

![](../../assets/v7-only.svg)

## Procedimento geral {#general-procedure}

Dependendo da sua configuração, há várias maneiras de realizar testes de migração.

Você deve ter um ambiente de teste/desenvolvimento para realizar testes de migração. Os ambientes Adobe Campaign estão sujeitos a licença: verifique seu contrato de licença ou entre em contato com seu representante de Adobe.

1. Pare todos os desenvolvimentos em andamento e transfira-os para o ambiente de produção.
1. Faça um backup do banco de dados do ambiente de desenvolvimento.
1. Pare todos os processos do Adobe Campaign na instância de desenvolvimento.
1. Faça um backup do banco de dados do ambiente de produção e o restaure como um ambiente de desenvolvimento.
1. Antes de iniciar os serviços da Adobe Campaign, execute o **freezeInstance.js** script de cauterização que permite limpar o banco de dados de quaisquer objetos que estavam sendo executados quando o backup foi iniciado.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >O comando é iniciado por padrão em **seco** e lista todas as solicitações que foram executadas por esse comando, sem iniciá-las. Para executar solicitações de cauterização, use **executar** no comando.

1. Certifique-se de que os backups estejam corretos tentando restaurá-los. Certifique-se de acessar o banco de dados, as tabelas, os dados etc.
1. Teste o procedimento de migração no ambiente de desenvolvimento.
1. Se a migração do ambiente de desenvolvimento for bem-sucedida, você poderá migrar o ambiente de produção.

>[!CAUTION]
>
>Devido a alterações feitas na estrutura de dados, a importação e exportação de pacotes de dados não é possível entre uma plataforma v5 e uma plataforma v7.


## Ferramentas de migração {#migration-tools}

Várias opções permitem medir o impacto de uma migração e identificar os possíveis problemas. Essas opções devem ser executadas:

* no **configuração** comando:

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* ou na pós-atualização:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>* Você deve usar o **-instance:`<instanceame>`** opção. Não recomendamos usar o **-allinâncias** opção.
>* O comando de atualização do Adobe Campaign (**pós-atualização**) permite sincronizar recursos e atualizar schemas e o banco de dados. Essa operação só pode ser executada uma vez e somente no servidor de aplicativos. Depois de sincronizar os recursos, a variável **pós-atualização** permite detectar se a sincronização gera erros ou avisos.


### Objetos não padrão ou ausentes

* O **-showCustomEntities** exibe a lista de todos os objetos não padrão:

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   Exemplo de mensagem enviada:

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* O **-showDeletedEntities** exibe a lista de todos os objetos padrão que estão ausentes no banco de dados ou no sistema de arquivos. Para cada objeto ausente, o caminho é especificado.

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   Exemplo de mensagem enviada:

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### Processo de verificação {#verification-process}

Integrado como padrão no comando pós-atualização, esse processo permite exibir avisos e erros que podem causar falha na migração. **Se forem exibidos erros, a migração não será executada.** Se isso acontecer, corrija todos os erros e reinicie o postupgrade.

Você pode iniciar o processo de verificação sozinho (sem migração) usando o comando:

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>Você pode ignorar todos os avisos e erros com o código JST-310040.

As seguintes expressões são pesquisadas (diferencia maiúsculas de minúsculas):

<table> 
 <thead> 
  <tr> 
   <th> Expressão<br /> </th> 
   <th> Código de erro<br /> </th> 
   <th> Tipo de log<br /> </th> 
   <th> Comentários<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Esse tipo de sintaxe não é mais compatível na personalização de delivery. Consulte <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>. Caso contrário, verifique se o tipo de valor está correto.<br /> </td> 
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
   <td> Este método de conexão não deve mais ser usado. Consulte <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">Aplicações web identificadas</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> novo SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Essa função só é compatível quando usada no código JavaScript executado de uma zona de segurança que esteja em <strong>sessionTokenOnly</strong> modo.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Erro<br /> </td> 
   <td> Esse tipo de erro gera uma falha de migração. Consulte <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> Erro<br /> </td> 
   <td> Esse tipo de erro gera uma falha de migração. Consulte <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>. Se você obtiver logs de erro de aplicativos web do tipo visão geral (migração da v6.02), consulte <a href="../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11" target="_blank">Configurar Campanha</a>.<br /> </td> 
  </tr>
  <tr> 
   <td> crmDeploymentType="onpremise"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> Erro<br /> </td> 
   <td> Esse tipo de implantação não é mais compatível. O Office 365 e o tipo de implantação do conector do Microsoft CRM no local foram descontinuados. 
   </br>Se estiver usando um desses tipos de implantação obsoletos em uma conta externa, essa conta externa deverá ser excluída e você deverá executar a variável <b>pós-atualização</b> comando. 
   </br>Para alterar para implantação da API da Web, consulte <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Aplicações web</a>.<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1(mscrmWorkflow/sfdcWorkflow)<br /> </td> 
   <td> PU-0008<br /> </td> 
   <td> Erro<br /> </td> 
   <td> As atividades de ação do Microsoft CRM, Salesforce e Oracle CRM On Demand não estão mais disponíveis. Para configurar a sincronização de dados entre o Adobe Campaign e um sistema CRM, é necessário usar o <a href="../../workflow/using/crm-connector.md" target="_blank">Conector CRM</a> atividade de direcionamento.<br /> </td>
  </tr> 
 </tbody> 
</table>

Também é realizada uma verificação de coerência de banco de dados e esquema.

### Opção de restauração {#restoration-option}

Essa opção permite restaurar objetos prontos se tiverem sido modificados. Para cada objeto restaurado, um backup das alterações é armazenado na pasta selecionada:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>É altamente recomendável usar caminhos de pasta absolutos e manter a estrutura de árvore de pastas. Por exemplo: backupFolder\nms\srcSchema\billing.xml.

### Retomar a migração {#resuming-migration}

Se você reiniciar o pós-atualização após uma falha de migração, ele será retomado do mesmo local em que foi interrompido.
