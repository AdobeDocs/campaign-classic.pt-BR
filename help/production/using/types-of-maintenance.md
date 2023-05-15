---
product: campaign
title: Tipos de manutenção
description: Tipos de manutenção
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---

# Tipos de manutenção{#types-of-maintenance}



## Manutenção de aplicativos {#application-maintenance}

O Adobe Campaign fornece um workflow integrado que permite agendar determinadas tarefas de manutenção do banco de dados: o **fluxo de trabalho de limpeza do banco de dados**. Esse workflow realiza as seguintes tarefas:

* supressão de registros expirados,
* exclusão de registros órfãos e reinicialização de status para objetos expirados,
* atualização das estatísticas do banco de dados.

>[!IMPORTANT]
>
>Observe que a tarefa de limpeza lida principalmente com a manutenção no nível do aplicativo, não com a manutenção no nível do RDBMS (com exceção da atualização de estatísticas). No entanto, as operações de manutenção serão necessárias no banco de dados. Mesmo se o workflow de limpeza do banco de dados for executado com êxito, isso não significa que o banco de dados esteja otimizado.

## Manutenção técnica {#technical-maintenance}

O workflow de limpeza do banco de dados não inclui nenhuma ferramenta de manutenção do banco de dados: cabe a você organizar a manutenção. Para fazer isso, é possível:

* trabalhe com o Administrador do Banco de Dados para configurar a manutenção do banco de dados com ferramentas de terceiros,
* use o mecanismo de workflow Adobe Campaign para agendar e rastrear essas atividades de manutenção.

Estes procedimentos de manutenção devem ser executados regularmente e incluir:

* reindexe tabelas atualizadas com frequência,
* compacte/reconstrua as tabelas para evitar a fragmentação.

### Cronograma de manutenção {#maintenance-schedule}

Você precisa encontrar os slots apropriados para executar essas atividades de manutenção. Eles podem afetar o desempenho do banco de dados ao executar ou até mesmo bloquear o aplicativo (devido a bloqueio).

Normalmente, essas tarefas são executadas uma vez por semana durante um período de baixa atividade que não colidem com backups, recarregamento de dados ou cálculo agregado. Alguns sistemas altamente solicitados requerem uma manutenção mais frequente.

Uma manutenção mais detalhada, como recriações completas de tabela, pode ser realizada uma vez por mês, de preferência com aplicativos totalmente interrompidos, pois o sistema não pode mais ser usado.

### Reconstrução de uma tabela {#rebuilding-a-table}

Várias estratégias estão disponíveis:

<table> 
 <thead> 
  <tr> 
   <th> Operações </th> 
   <th> Descrição </th> 
   <th> Benefícios </th> 
   <th> Desvantagens </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Desfragmentação online<br /> </td> 
   <td> A maioria dos mecanismos de banco de dados fornece métodos de desfragmentação.<br /> </td> 
   <td> Basta usar o método de desfragmentação do banco de dados. Normalmente, esses métodos tratam de problemas de integridade, bloqueando os dados durante a desfragmentação.<br /> </td> 
   <td> Dependendo do banco de dados, esses métodos de desfragmentação podem ser fornecidos como uma opção RDBMS (Oracle) e nem sempre são a maneira mais eficiente de lidar com tabelas maiores.<br /> </td> 
  </tr> 
  <tr> 
   <td> Despejar e restaurar<br /> </td> 
   <td> Despeje a tabela para um arquivo, exclua a tabela no banco de dados e restaure do despejo.<br /> </td> 
   <td> Essa é a maneira mais fácil de desfragmentar uma tabela. Também é a única solução quando o banco de dados está quase cheio.<br /> </td> 
   <td> Como a tabela é excluída e recriada, o aplicativo não pode ser deixado online, mesmo no modo somente leitura (a tabela não está disponível durante a fase de restauração).<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplicar, renomear e soltar<br /> </td> 
   <td> Isso cria uma cópia de uma tabela e seus índices, em seguida, solta o existente e renomeia a cópia para ocupar seu lugar.<br /> </td> 
   <td> Esse método é mais rápido que a primeira abordagem, pois gera menos E/S (sem cópia como arquivo e leitura desse arquivo).<br /> </td> 
   <td> Requer duas vezes a quantidade de espaço.<br /> Todos os processos ativos que gravam na tabela durante o processo devem ser interrompidos. No entanto, os processos de leitura não serão afetados, pois a tabela é trocada no último momento após a reconstrução. <br /> </td> 
  </tr> 
 </tbody> 
</table>
