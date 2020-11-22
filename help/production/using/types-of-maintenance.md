---
solution: Campaign Classic
product: campaign
title: Tipos de manutenção
description: Tipos de manutenção
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---


# Tipos de manutenção{#types-of-maintenance}

## Manutenção de aplicativos {#application-maintenance}

A Adobe Campaign fornece um fluxo de trabalho integrado que permite agendar determinadas tarefas de manutenção do banco de dados: o fluxo de trabalho **de limpeza do** banco de dados. Esse fluxo de trabalho realiza as seguintes tarefas:

* supressão de registros expirados,
* supressão de registros órfãos e reinicialização do estado para objetos expirados,
* atualização das estatísticas do banco de dados.

>[!IMPORTANT]
>
>Observe que a tarefa de limpeza lida principalmente com a manutenção do nível do aplicativo, não com a manutenção do nível RDBMS (com exceção da atualização de estatísticas). No entanto, serão necessárias operações de manutenção na base de dados. Mesmo se o fluxo de trabalho de limpeza do banco de dados for executado com êxito, isso não significa que o banco de dados esteja otimizado.

## Manutenção técnica {#technical-maintenance}

O fluxo de trabalho de limpeza do banco de dados não inclui nenhuma ferramenta de manutenção do banco de dados: cabe a você organizar a manutenção. Para fazer isso, você pode:

* trabalhe com o Administrador do Banco de Dados para configurar a manutenção do banco de dados com ferramentas de terceiros,
* use o motor de workflow Adobe Campaign para agendar e rastrear essas atividades de manutenção.

Estes procedimentos de manutenção devem ser efetuados regularmente e incluir:

* reindexar tabelas atualizadas com frequência,
* compacte/recrie as tabelas para evitar a fragmentação.

### Programação de manutenção {#maintenance-schedule}

Você precisa encontrar os slots apropriados para executar essas atividades de manutenção. Eles podem afetar muito o desempenho do banco de dados ao executar ou mesmo bloquear o aplicativo (devido a bloqueio).

Normalmente, essas tarefas são executadas uma vez por semana durante um período de baixa atividade que não colidem com backups, recarregamento de dados ou cálculo de agregação. Alguns sistemas altamente solicitados requerem uma manutenção mais frequente.

Uma manutenção mais detalhada, como reconstruções completas de tabelas, pode ser realizada uma vez por mês, de preferência com aplicativos totalmente parados, já que o sistema não pode ser utilizado de qualquer forma.

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
   <td> Basta usar o método de desfragmentação do banco de dados. Esses métodos geralmente cuidam dos problemas de integridade bloqueando os dados durante a desfragmentação.<br /> </td> 
   <td> Dependendo do banco de dados, esses métodos de desfragmentação podem ser fornecidos como uma opção RDBMS (Oracle) e nem sempre são a maneira mais eficiente de lidar com tabelas maiores.<br /> </td> 
  </tr> 
  <tr> 
   <td> Despejar e restaurar<br /> </td> 
   <td> Despeje a tabela para um arquivo, exclua a tabela no banco de dados e restaure do despejo.<br /> </td> 
   <td> Esta é a maneira mais fácil de desfragmentar uma mesa. Também é a única solução quando o banco de dados está quase cheio.<br /> </td> 
   <td> Como a tabela é excluída e recriada, o aplicativo não pode ser deixado on-line, mesmo no modo somente leitura (a tabela não está disponível durante a fase de restauração).<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplicado, renomear e soltar<br /> </td> 
   <td> Isso cria uma cópia de uma tabela e seus índices, em seguida, solta a existente e renomeia a cópia para que ela ocupe seu lugar.<br /> </td> 
   <td> Esse método é mais rápido que a primeira abordagem, pois gera menos E/S (nenhuma cópia como um arquivo e leitura desse arquivo).<br /> </td> 
   <td> Requer o dobro de espaço.<br /> Todos os processos ativos que gravam na tabela durante o processo devem ser interrompidos. No entanto, os processos de leitura não serão afetados, uma vez que a tabela é trocada no último momento após a reconstrução. <br /> </td> 
  </tr> 
 </tbody> 
</table>

