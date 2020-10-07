---
title: Gerenciamento de fuso horário
seo-title: Gerenciamento de fuso horário
description: Gerenciamento de fuso horário
seo-description: null
page-status-flag: never-activated
uuid: b8926761-65e2-48fd-8689-2ae6b0596e72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: b9846eda-eeca-433e-b961-6dfc2aa2708b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 1%

---


# Gerenciamento de fuso horário{#time-zone-management}

## Princípio operacional {#operating-principle}

A Adobe Campaign permite que você expresse datas em função do fuso horário: isso permite que usuários internacionais trabalhem no mundo inteiro em vários fusos horários. Cada país que usa a mesma instância pode gerenciar a execução de campanhas, rastreamento, arquivamento etc. dependendo do horário local.

Para permitir o uso da plataforma Adobe Campaign em escala internacional, todas as datas usadas pelos sistemas devem estar vinculáveis a um fuso horário. Uma data cujo fuso horário é conhecido pode, portanto, ser importada para qualquer outro fuso horário, ou independentemente do fuso horário.

A Adobe Campaign permite que você armazene datas/horas no formato UTC (Tempo Universal Coordenado). Quando os dados são expostos, eles são convertidos na data/hora local do operador. A conversão é realizada automaticamente quando o banco de dados é configurado em UTC (consulte [Configuração](#configuration)). Se o banco de dados não estiver configurado em UTC, as informações sobre o fuso horário das datas na plataforma serão armazenadas em uma opção.

As principais funcionalidades da plataforma em relação ao gerenciamento de fuso horário são: importar/exportar dados e gerenciamento de operador e fluxo de trabalho. O conceito **de** herança está disponível para importações/exportações ou Workflows. Por padrão, eles são configurados para o fuso horário do servidor de banco de dados, no entanto, você pode redefinir novos fusos horários para um fluxo de trabalho e até mesmo para uma única atividade.

**Os operadores** podem modificar os fusos horários durante a configuração **do** delivery e podem especificar o fuso horário em que o delivery será executado.

>[!IMPORTANT]
>
>Se o banco de dados não gerenciar vários fusos horários, para todas as manipulações de filtragem de dados, os query SQL devem ser executados no fuso horário do servidor de banco de dados.

Cada operador Adobe Campaign está vinculado a um fuso horário: essas informações são configuradas em seus perfis. For more on this, refer to [this document](../../platform/using/access-management.md).

Quando a plataforma Adobe Campaign não requer gerenciamento de fuso horário, você pode manter um modo de armazenamento no formato local com um fuso horário vinculado específico.

## Recomendações {#recommendations}

Os fusos horários combinam várias realidades: a expressão pode descrever um desfasamento de tempo constante com a data UTC ou os horários de uma região que pode mudar de hora duas vezes por ano (horário de verão).

Por exemplo, no postSQL, o FUSO HORÁRIO **DEFINIDO &quot;Europa/Paris&quot;;** o comando levará os tempos de verão e inverno em conta: a data será expressa em UTC+1 ou UTC+2, dependendo da hora do ano.

No entanto, se utilizar o FUSO HORÁRIO **DEFINIDO 0200;** , o intervalo de tempo sempre será UTC+2.

## Configuração {#configuration}

O modo de armazenamento para datas e horas é selecionado durante a criação do banco de dados (consulte [Criação de uma nova instância](#creating-a-new-instance)). No caso de uma migração, as horas vinculadas a datas são convertidas em datas e horas locais (consulte [Migração](#migration)).

Do ponto de visualização técnico, há duas maneiras de armazenar informações de tipo de **Data+hora** no banco de dados:

1. TIMESTAMP WITH TIMEZONE format: o mecanismo de banco de dados armazena datas em UTC. Cada sessão aberta terá um fuso horário e as datas serão convertidas de acordo com ele.
1. Formato local + fuso horário local: todas as datas são armazenadas no formato local (sem gerenciamento de atraso de tempo) e um único fuso horário é atribuído a elas. O fuso horário é armazenado na opção **WdbcTimeZone** da instância do Adobe Campaign e pode ser alterado pelo **[!UICONTROL Administration > Platform > Options]** menu da árvore.

>[!IMPORTANT]
>
>Observe que essa modificação pode resultar em problemas de consistência e sincronização de dados.

### Creating a new instance {#creating-a-new-instance}

Para que vários usuários internacionais trabalhem na mesma instância, é necessário configurar os fusos horários ao criar a instância para gerenciar os intervalos de tempo entre países. Durante a criação da instância, selecione o modo de gerenciamento de data e hora na **[!UICONTROL Time zone]** seção do estágio de configuração do banco de dados.

Marque a **[!UICONTROL UTC database (date fields with time zone)]** opção para armazenar todos os dados com datas e horas no formato UTC (campos SQL e XML).

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Se você estiver usando o **Oracle**, os arquivos de fuso horário (.dat) das camadas do cliente Oracle deverão ser compatíveis com os arquivos de fuso horário instalados no servidor.

Se o banco de dados não for UTC, você poderá selecionar um dos fusos horários oferecidos na lista suspensa. Você também pode usar o fuso horário do servidor ou selecionar a opção UTC (Horário Universal Coordenado).

![](assets/install_wz_unselect_utc_option.png)

Quando a **[!UICONTROL UTC Database (date fields with time zone)]** opção é selecionada, os campos SQL são armazenados no formato TIMESTAMP WITH TIMEZONE.

Caso contrário, eles serão armazenados no formato local e será necessário selecionar o fuso horário a ser aplicado ao banco de dados.

### Migration {#migration}

Ao migrar para uma versão anterior (sem gerenciamento de fuso horário), será necessário definir o modo de armazenamento de data no banco de dados.

Para garantir a compatibilidade com ferramentas externas que acessam o banco de dados Adobe Campaign, os campos SQL do tipo **Date+time** permanecem armazenados no formato local por padrão.

Campos XML contendo datas agora são armazenados em UTC. Durante o carregamento, os campos que não estão no formato UTC são convertidos automaticamente usando o fuso horário dos servidores. Isso significa que todos os campos XML serão progressivamente convertidos em formato UTC.

Para usar uma instância existente, adicione a opção **WdbcTimeZone** e insira o fuso horário da instância.

>[!IMPORTANT]
>
>Verifique se o valor correto está configurado para a opção WdbcTimeZone: alterações efetuadas posteriormente podem levar a inconsistências.

Exemplo de valores possíveis:

* Europa/Paris,
* Europa/Londres,
* América/Nova_York, etc.

   Esses valores são obtidos do banco de dados tz (Olson). Para obter mais informações, consulte [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

