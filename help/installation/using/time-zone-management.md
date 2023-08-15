---
product: campaign
title: Gerenciamento de fuso horário
description: Gerenciamento de fuso horário
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
badge-v7-prem: label="no local e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 4%

---

# Gerenciamento de fuso horário{#time-zone-management}



## Princípio operacional {#operating-principle}

O Adobe Campaign permite expressar datas em função de seu fuso horário: isso permite que usuários internacionais trabalhem em vários fusos horários do mundo inteiro. Cada país que usa a mesma instância pode gerenciar a execução de campanhas, rastreamento, arquivamento etc. dependendo da hora local.

Para permitir o uso da plataforma Adobe Campaign em escala internacional, todas as datas usadas pelos sistemas devem ser vinculáveis a um fuso horário. Uma data cujo fuso horário é conhecido pode, portanto, ser importada para qualquer outro fuso horário, ou independentemente do fuso horário.

O Adobe Campaign permite armazenar datas/horas no formato UTC (Tempo universal coordenado). Quando os dados são expostos, eles são convertidos na data/hora local do operador. A conversão é executada automaticamente quando o banco de dados é configurado em UTC (consulte [Configuração](#configuration)). Se o banco de dados não estiver configurado em UTC, as informações sobre o fuso horário das datas na plataforma serão armazenadas em uma opção.

As principais funcionalidades da plataforma relacionadas ao gerenciamento de fuso horário são: dados de importação/exportação e gerenciamento de operador e fluxo de trabalho. A variável **conceito de herança** está disponível para importações/exportações ou Fluxos de trabalho. Por padrão, eles são configurados para o fuso horário do servidor de banco de dados, no entanto, você pode redefinir novos fusos horários para um fluxo de trabalho e até mesmo para uma única atividade.

**Operadores** pode modificar fusos horários durante **configuração de entrega** e podem especificar o fuso horário específico em que o delivery será executado.

>[!IMPORTANT]
>
>Se o banco de dados não gerenciar vários fusos horários, para todas as manipulações de filtragem de dados, as consultas SQL deverão ser executadas no fuso horário do servidor de banco de dados.

Cada operador do Adobe Campaign está vinculado a um fuso horário: essas informações são configuradas em seu perfil. Para obter mais informações, consulte [este documento](../../platform/using/access-management.md).

Quando a plataforma do Adobe Campaign não requer o gerenciamento de fuso horário, você pode manter um modo de armazenamento no formato local com um fuso horário vinculado específico.

## Recomendações {#recommendations}

Os fusos horários combinam várias realidades: a expressão pode descrever um intervalo de tempo constante com a data UTC, ou os horários de uma região que pode mudar os horários duas vezes por ano (horário de verão).

Por exemplo, no postgreSQL, a variável **FUSO HORÁRIO DEFINIDO &#39;Europa/Paris&#39;;** O comando levará em conta os horários de verão e inverno: a data será expressa em UTC+1 ou UTC+2, dependendo da hora do ano.

No entanto, se você usar a variável **FUSO HORÁRIO DEFINIDO 0200;** , o atraso será sempre UTC+2.

## Configuração {#configuration}

O modo de armazenamento para datas e horas é selecionado durante a criação do banco de dados (consulte [Criação de uma nova instância](#creating-a-new-instance)). No caso de uma migração, as horas vinculadas às datas são convertidas em datas e horas locais (consulte [Migração](#migration)).

Do ponto de vista técnico, há duas formas de armazenar **Data+hora** digite as informações no banco de dados:

1. Formato TIMESTAMP WITH TIMEZONE: o mecanismo de banco de dados armazena datas em UTC. Cada sessão aberta terá um fuso horário e as datas serão convertidas de acordo com ele.
1. Formato local + fuso horário local: todas as datas são armazenadas no formato local (sem gerenciamento de atraso de tempo) e um único fuso horário é atribuído a elas. O fuso horário é armazenado na variável **WdbcTimeZone** opção da instância do Adobe Campaign e pode ser alterada por meio da **[!UICONTROL Administration > Platform > Options]** menu da árvore.

>[!IMPORTANT]
>
>Esteja ciente de que essa modificação pode resultar em problemas de sincronização e consistência de dados.

### Criação de uma nova instância {#creating-a-new-instance}

Para que vários usuários internacionais trabalhem na mesma instância, é necessário configurar fusos horários ao criar a instância para gerenciar intervalos de tempo entre países. Durante a criação da instância, selecione o modo de gerenciamento de data e hora na variável **[!UICONTROL Time zone]** seção da etapa de configuração do banco de dados.

Verifique a **[!UICONTROL UTC database (date fields with time zone)]** opção para armazenar todos os dados com datas e horas no formato UTC (campos SQL e campos XML).

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Se você estiver usando **Oracle**, os arquivos de fuso horário (.dat) das camadas de cliente do Oracle devem ser compatíveis com os arquivos de fusos horários instalados no servidor.

Se o banco de dados não for UTC, você poderá selecionar um dos fusos horários oferecidos na lista suspensa. Você também pode usar o fuso horário do servidor ou selecionar a opção UTC (Tempo universal coordenado).

![](assets/install_wz_unselect_utc_option.png)

Quando a variável **[!UICONTROL UTC Database (date fields with time zone)]** for selecionada, os campos SQL serão armazenados no formato TIMESTAMP WITH TIMEZONE.

Caso contrário, eles serão armazenados no formato local e será necessário selecionar o fuso horário a ser aplicado ao banco de dados.

### Migração {#migration}

Ao migrar para uma versão anterior (sem gerenciamento de fuso horário), será necessário definir o modo de armazenamento de data no banco de dados.

Para garantir a compatibilidade com ferramentas externas que acessam o banco de dados do Adobe Campaign, a variável **Data+hora** Os campos do tipo SQL permanecem armazenados no formato local por padrão.

Os campos XML que contêm datas agora estão armazenados em UTC. Durante o carregamento, os campos que não estão no formato UTC são convertidos automaticamente usando o fuso horário dos servidores. Isso significa que todos os campos XML serão progressivamente convertidos no formato UTC.

Para usar uma instância existente, adicione o **WdbcTimeZone** e insira o fuso horário da instância.

>[!IMPORTANT]
>
>Verifique se o valor correto está configurado para a opção WdbcTimeZone: as alterações feitas posteriormente podem levar a inconsistências.

Exemplo de valores possíveis:

* Europa/Paris,
* Europa/Londres,
* América/Nova_York etc.

  Esses valores são obtidos do banco de dados tz (Olson). Para obter mais informações, consulte [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
