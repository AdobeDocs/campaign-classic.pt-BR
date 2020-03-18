---
title: Uso da tabela Destinatário do Adobe Campaign Classic
description: Saiba como usar a tabela de destinatários pronta para uso no Adobe Campaign Classic ao projetar seu modelo de dados.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1336bf7ab9cce7f2ffe7d4ffa5e119851e946885

---


# Práticas recomendadas do modelo de dados{#data-model-best-practices}

Este documento descreve as principais recomendações ao projetar seu modelo de dados do Adobe Campaign.

Para obter uma melhor compreensão das tabelas integradas do Campaign e de suas interações, consulte a seção de modelo [de dados do](../../configuration/using/about-data-model.md) Campaign Classic.

Leia esta [documentação](../../configuration/using/about-schema-reference.md) para começar a usar os esquemas do Campaign. Saiba como configurar esquemas de extensão para estender o modelo de dados conceituais do banco de dados do Adobe Campaign neste [documento](../../configuration/using/about-schema-edition.md).

## Visão geral {#overview}

O sistema do Adobe Campaign é extremamente flexível e pode ser estendido além da implementação inicial. No entanto, embora as possibilidades sejam infinitas, é fundamental tomar decisões sábias e criar bases fortes para começar a projetar seu modelo de dados.

Este documento fornece casos de uso comuns e práticas recomendadas para aprender como arquitetar corretamente sua ferramenta Adobe Campaign.

## Arquitetura do modelo de dados {#data-model-architecture}

O Adobe Campaign Standard é um poderoso sistema de gerenciamento de campanhas entre canais que pode ajudá-lo a alinhar suas estratégias online e offline para criar experiências personalizadas de clientes.

### Abordagem centrada no cliente {#customer-centric-approach}

Embora a maioria dos provedores de serviços de email esteja se comunicando com os clientes por uma abordagem centrada em lista, o Adobe Campaign depende de um banco de dados relacional para aproveitar uma visão mais ampla dos clientes e seus atributos.

Esta abordagem centrada no cliente é mostrada no gráfico abaixo. A tabela **Destinatário** em cinza representa a principal tabela do cliente em torno da qual tudo está sendo criado:

![](assets/customer-centric-data-model.png)

Para acessar a descrição de cada tabela, vá para **[!UICONTROL Admin > Configuration > Data schemas]**, selecione um recurso da lista e clique na **[!UICONTROL Documentation]** guia.

O modelo de dados padrão do Adobe Campaign é apresentado neste [documento](../../configuration/using/data-model-description.md).

>[!NOTE]
>
>O Adobe Campaign Classic permite criar uma tabela de clientes personalizada. No entanto, na maioria dos casos, é recomendável aproveitar a tabela [](../../configuration/using/about-data-model.md#default-recipient-table) Destinatário padrão que já tem tabelas e recursos adicionais pré-criados.

### Dados do Adobe Campaign {#data-for-campaign}

Que dados devem ser enviados para o Adobe Campaign? É importante determinar os dados necessários para suas atividades de marketing.

>[!NOTE]
>
>O Adobe Campaign não é um data warehouse nem uma ferramenta de relatórios. Portanto, não tente importar todos os clientes possíveis e suas informações associadas para o Adobe Campaign, nem importe dados que serão usados apenas para criar relatórios.

Para decidir se um atributo será necessário ou não no Adobe Campaign, pergunte a si mesmo se ele se enquadra em uma dessas categorias:

* Atributo usado para **segmentação**
* Atributo usado para processos **de gerenciamento de** dados (cálculo agregado, por exemplo)
* Atributo usado para **personalização**

Se não estiver entrando em nenhum desses, é provável que você não precise desse atributo no Adobe Campaign.

### Escolha dos tipos de dados {#data-types}

Para garantir boa arquitetura e desempenho do seu sistema, siga as práticas recomendadas abaixo para configurar os dados no Adobe Campaign.

* Uma tabela grande deve ter principalmente campos numéricos e conter links para tabelas de referência (ao trabalhar com uma lista de valores).
* O atributo **expr** permite definir um atributo de esquema como um campo calculado em vez de um valor de conjunto físico em uma tabela. Isso pode permitir o acesso às informações em um formato diferente (como idade e data de nascimento, por exemplo) sem a necessidade de armazenar ambos os valores. Essa é uma boa maneira de evitar a duplicação de campos. Por exemplo, a tabela Destinatário usa uma expressão para o domínio, que já está presente no campo de email.
* No entanto, quando o cálculo da expressão é complexo, não é recomendável usar o atributo **expr** , já que o cálculo dinâmico pode afetar o desempenho de suas consultas.
* O tipo **XML** é uma boa maneira de evitar a criação de muitos campos. Mas também ocupa espaço em disco à medida que usa uma coluna CLOB no banco de dados. Também pode levar a consultas SQL complexas e afetar o desempenho.
* O comprimento de um campo de **string** deve ser sempre definido com a coluna. Por padrão, o comprimento máximo no Adobe Campaign é 255, mas a Adobe recomenda manter o campo mais curto se você já souber que o tamanho não excederá um comprimento menor.
* É aceitável ter um campo menor no Adobe Campaign do que no sistema de origem se você tiver certeza de que o tamanho no sistema de origem foi superestimado e não seria atingido. Isso pode significar uma string menor ou um número inteiro menor no Adobe Campaign.

### Escolha dos campos {#choice-of-fields}

Um campo deve ser armazenado em uma tabela se tiver uma finalidade de definição de metas ou personalização. Em outras palavras, se um campo não for usado para enviar um email personalizado ou usado como critério em uma consulta, ele ocupará espaço em disco, ao passo que não será útil.

Para instâncias híbridas e locais, o FDA (Federated Data Access, um recurso opcional que permite acessar dados externos) cobre a necessidade de adicionar um campo &quot;on-the-fly&quot; durante um processo de campanha. Você não precisa importar tudo se tiver FDA. Para obter mais informações, consulte [Sobre o acesso](../../platform/using/about-fda.md)a dados federados.

### Escolha das teclas {#choice-of-keys}

Além do **autopk** definido por padrão na maioria das tabelas, você deve considerar adicionar algumas chaves lógicas ou comerciais (número da conta, número do cliente e assim por diante). Pode ser utilizado posteriormente para importações/reconciliação ou pacotes de dados. For more on this, see [Identifiers](#identifiers).

Chaves eficientes são essenciais para o desempenho. Os tipos de dados numéricos devem sempre ser preferidos como chaves para tabelas.

Para o banco de dados SQLServer, você pode considerar o uso de &quot;índice clusterizado&quot; se o desempenho for necessário. Como a Adobe não lida com isso, é necessário criá-lo no SQL.

### Tabelas dedicadas {#dedicated-tablespaces}

O atributo tablespace no esquema permite especificar um tablespace dedicado para uma tabela.

O assistente de instalação permite que você armazene objetos por tipo (dados, temporários e índice).

Os tablespaces dedicados são melhores para particionamento, regras de segurança e permitem administração fluida e flexível, melhor otimização e desempenho.

## Identificadores {#identifiers}

Os recursos do Adobe Campaign têm três identificadores e é possível adicionar um identificador adicional.

A tabela a seguir descreve esses identificadores e sua finalidade.

| Identifier | Descrição | Práticas recomendadas |
|--- |--- |--- |
| Id | <ul><li>A ID é a chave primária física de uma tabela do Adobe Campaign. Para tabelas predefinidas, é um número gerado de 32 bits de uma sequência</li><li>Normalmente, esse identificador é exclusivo de uma instância específica do Adobe Campaign. </li><li>Uma ID gerada automaticamente pode ser visível em uma definição de esquema. Pesquise o atributo *autopk=&quot;true&quot;* .</li></ul> | <ul><li>Os identificadores gerados automaticamente não devem ser usados como referência em um fluxo de trabalho ou em uma definição de pacote.</li><li>Não se deve partir do princípio de que a id será sempre um número crescente.</li><li>A id em uma tabela predefinida é um número de 32 bits e esse tipo não deve ser alterado. Este número é extraído de uma &quot;sequência&quot; coberta na seção com o mesmo nome.</li></ul> |
| Nome (ou nome interno) | <ul><li>Essas informações são um identificador exclusivo de um registro em uma tabela. Esse valor pode ser atualizado manualmente, geralmente com um nome gerado.</li><li>Esse identificador mantém seu valor quando implantado em uma instância diferente do Adobe Campaign e não deve estar vazio.</li></ul> | <ul><li>Renomeie o nome do registro gerado pelo Adobe Campaign se o objeto for implantado de um ambiente para outro.</li><li>Quando um objeto tem um atributo de namespace (*esquema* , por exemplo), esse namespace comum será aproveitado em todos os objetos personalizados criados. Alguns namespaces reservados não devem ser usados: *nms*, *xtk*.</li><li>Quando um objeto não tem um namespace (*fluxo de trabalho* ou *entrega* , por exemplo), essa noção de namespace seria adicionada como um prefixo de um objeto de nome interno: *namespaceMyObjectName*.</li><li>Não use caracteres especiais, como o espaço &quot;&quot;, a semircoluna &quot;:&quot; ou o hífen &quot;-&quot;. Todos esses caracteres seriam substituídos por um sublinhado &quot;_&quot; (caractere permitido). Por exemplo, &quot;abc-def&quot; e &quot;abc:def&quot; seriam armazenados como &quot;abc_def&quot; e se substituiriam.</li></ul> |
| Rótulo | <ul><li>O rótulo é o identificador comercial de um objeto ou registro no Adobe Campaign.</li><li>Esse objeto permite espaços e caracteres especiais.</li><li>Não garante a unicidade de um registro.</li></ul> | <ul><li>É recomendável determinar uma estrutura para seus rótulos de objetos.</li><li>Essa é a solução mais fácil de usar para identificar um registro ou objeto para um usuário do Adobe Campaign.</li></ul> |

## Teclas internas personalizadas {#custom-internal-keys}

As chaves primárias são necessárias para cada tabela criada no Adobe Campaign.

A maioria das organizações está importando registros de sistemas externos. Embora a chave física da tabela Destinatário seja o atributo &quot;id&quot;, é possível determinar uma chave personalizada além disso.

Essa chave personalizada é a chave primária de registro real no sistema externo que alimenta o Adobe Campaign.

Quando uma tabela predefinida tiver um autopk e uma chave interna, a chave interna será definida como um índice exclusivo na tabela do banco de dados físico.

Ao criar uma tabela personalizada, você tem duas opções:
* Uma combinação de chave gerada automaticamente (id) e chave interna (personalizada). Essa opção é interessante se a chave do sistema for uma chave composta ou não for um número inteiro. Os inteiros fornecerão desempenho mais alto em tabelas grandes e unirão-se a outras tabelas.
* Usar a chave primária como a chave primária do sistema externo. Essa solução geralmente é preferida, pois simplifica a abordagem de importar e exportar dados, com uma chave consistente entre diferentes sistemas. A opção Autopk deve ser desativada se a chave for chamada de &quot;id&quot; e se espera que seja preenchida com valores externos (não gerado automaticamente).

>[!IMPORTANT]
>
>Um autopk não deve ser usado como referência em fluxos de trabalho.

## Sequências {#sequences}

A chave primária do Adobe Campaign é uma ID gerada automaticamente para todas as tabelas prontas e pode ser a mesma para tabelas personalizadas. For more on this, see [this section](#identifiers).

Esse valor é obtido do que é chamado de **sequência**, que é um objeto de banco de dados usado para gerar uma sequência numérica.

Há dois tipos de sequências:
* **Compartilhado**: mais de uma tabela escolheria a ID da mesma sequência. Isso significa que se um id &#39;X&#39; for usado por uma tabela, nenhuma outra tabela que compartilhasse a mesma sequência teria um registro com esse id &#39;X&#39;. **XtkNewId** é a sequência compartilhada padrão disponível no Adobe Campaign.
* **Dedicado**: somente uma tabela está escolhendo suas ids da sequência. O nome da sequência geralmente contém o nome da tabela.

A sequência é um valor inteiro de 32 bits, com um número máximo finito de valores disponíveis: 2,14 bilhões. Depois de atingir o valor máximo, a sequência volta para 0, para reciclar IDs. Se os dados antigos não tiverem sido removidos, o resultado será uma violação de chave exclusiva, que se torna um bloqueador para a integridade e uso da plataforma. O Adobe Campaign não conseguiria enviar comunicações (quando isso afetasse a tabela do registro de entrega) e os desempenhos seriam altamente afetados.

Portanto, um cliente enviando 6 bilhões de emails anualmente, com um período de retenção de 180 dias para seus registros, perderia as ids em 4 meses. Para evitar esse desafio, certifique-se de ter configurações de expurgação de acordo com seus volumes. For more on this, see [this section](#data-retention).

Quando uma tabela personalizada é criada no Adobe Campaign com uma chave primária como um autoPK, uma sequência dedicada personalizada deve ser associada sistematicamente a essa tabela.

Por padrão, uma sequência personalizada terá valores que variam de +1.000 a +2,1BB. Tecnicamente, é possível obter uma faixa completa de 4BB, habilitando ids negativos. Isso deve ser usado com cuidado e um id será perdido ao passar de números negativos para positivos: o registro 0 normalmente é ignorado pelo Adobe Campaign Classic em consultas SQL geradas.

**Tópicos relacionados:**
* Para obter mais informações sobre o recurso de geração **automática de** Sequência, consulte este [documento](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html).
* Para obter mais informações sobre a exaustão das sequências, assista a este [vídeo](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html).

## Índices {#indexes}

Os índices são essenciais para o desempenho. Quando você declara uma chave no esquema, a Adobe criará automaticamente um índice nos campos da chave. Você também pode declarar mais índices para consultas que não usam a chave.

A Adobe recomenda definir índices adicionais, pois pode melhorar o desempenho.

No entanto, lembre-se do seguinte:

* O uso do índice está vinculado ao seu padrão de acesso. A otimização da indexação é, muitas vezes, uma parte essencial no projeto do banco de dados e precisa ser tratada por especialistas. A adição de índices geralmente é um fluxo de trabalho iterativo anexado à manutenção do banco de dados. É feito ao longo do tempo, passo a passo, para resolver problemas de desempenho ao ocorrer.
* Os índices aumentam o tamanho geral da tabela (para armazenar o próprio índice).
* A adição de índice em colunas pode melhorar o desempenho do acesso de leitura de dados (SELECT), mas pode diminuir o desempenho do acesso de gravação de dados (UPDATE).
* Como isso afeta o desempenho durante a inserção dos dados, os índices devem ser limitados em tamanho e número.
* Não adicione índices quando não for necessário. Certifique-se de que seja obrigatório e que aumente o desempenho geral de suas consultas (teste e aprenda).
* De modo geral, um índice é eficiente se você sabe que suas consultas não trarão mais de 10% dos registros.
* Selecione cuidadosamente os índices que precisam ser definidos.
* Não remova índices nativos de tabelas predefinidas.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

## Links e cardinalidade {#links-and-cardinality}

### Links {#links}

Cuidado com a integridade &quot;própria&quot; das grandes tabelas. A exclusão de registros com tabelas largas na integridade &quot;própria&quot; pode interromper a instância. A tabela está bloqueada e as exclusões são feitas uma por uma. Portanto, é melhor usar a integridade &quot;neutra&quot; em tabelas-filho que têm grandes volumes.

Declarar um link como uma junção externa não é bom para o desempenho. O registro de id zero emula a funcionalidade de junção externa. Não é necessário declarar joins externos se o link usar o autopk.

Embora seja possível associar qualquer tabela em um fluxo de trabalho, a Adobe recomenda definir links comuns entre recursos diretamente na definição da estrutura de dados.

O link deve ser definido de acordo com os dados reais em suas tabelas. Uma definição incorreta poderia afetar os dados recuperados por meio de links, por exemplo, duplicando registros inesperadamente.

Dê um nome consistente ao seu link com o nome da tabela: o nome do link deve ajudar a entender o que é a tabela distante.

Não nomeie um link com &quot;id&quot; como sufixo. Por exemplo, nomeie-a como &quot;transaction&quot; em vez de &quot;transactionId&quot;.

Por padrão, o Adobe Campaign criará um link usando a chave primária da tabela externa. Para maior clareza, é preferível definir explicitamente a junção na definição do link.

Um índice será adicionado aos atributos usados em um link.

Os links criados por e modificados por último estão presentes em muitas tabelas. É possível desativar o índice usando o atributo noDbIndex no link, se essas informações não estiverem sendo usadas pela empresa.

### Cardinalidade {#cardinality}

Ao projetar um link, verifique se o registro de destino é único quando uma relação 1-1 for declarada. Caso contrário, a junção poderá retornar vários registros quando apenas um for esperado. Isso resulta em erros durante a preparação da entrega quando &quot;a consulta retorna mais linhas do que o esperado&quot;. Defina o nome do link com o mesmo nome do esquema de destino.

Defina um link com uma cardinalidade (1-N) no esquema do lado (1). Por exemplo, a transação Destinatário da relação (1) - (N) deve ser definida no esquema da transação.

Observe que a cardinalidade reversa de um link é (N) por padrão. É possível definir um link (1-1) adicionando o atributo revCardinality=&#39;single&#39; à definição do link.

Se o link reverso não deve estar visível para o usuário, você pode ocultá-lo com a definição do link revLink=&#39;_NONE_&#39;. Um bom caso de uso para isso é definir um link do destinatário para a última transação concluída, por exemplo. Você só precisa ver o link do destinatário para a última transação e nenhum link reverso é necessário para ficar visível da tabela de transação.

Os links que executam uma junção externa (1-0.1) devem ser usados com cuidado, pois isso afetará o desempenho do sistema.

## Retenção de dados - Limpeza e expurgação {#data-retention}

O Adobe Campaign não é um data warehouse nem uma ferramenta de relatórios. Portanto, para garantir um bom desempenho da solução Adobe Campaign, o crescimento do banco de dados deve permanecer sob controle. Para isso, seguir algumas das práticas recomendadas abaixo pode ajudar.

Por padrão, os registros de entrega e rastreamento do Adobe Campaign têm uma duração de retenção de 180 dias. Um processo de limpeza é executado para remover qualquer log anterior.

* Se desejar manter os registros por mais tempo, essa decisão deve ser tomada cuidadosamente dependendo do tamanho do banco de dados e do volume de mensagens enviadas. Como lembrete, a sequência do Adobe Campaign é um número inteiro de 32 bits.
* Recomenda-se não ter mais de 1 bilhão de registros de cada vez nessas tabelas (cerca de 50% dos 2,14 bilhões de ids disponíveis) para limitar os riscos de consumo de todas as ids disponíveis. Isso exigirá que alguns clientes reduzam a duração da retenção para menos de 180 dias.

>[!IMPORTANT]
>
>Tabelas personalizadas não são expurgadas com o processo de limpeza padrão. Embora isso não seja necessário no primeiro dia, não se esqueça de criar um processo de limpeza para suas tabelas personalizadas, pois isso pode levar a desafios de desempenho.

Existem algumas soluções para minimizar a necessidade de registros no Adobe Campaign:
* Exporte os dados em um data warehouse fora do Adobe Campaign.
* Gere valores agregados que usarão menos espaço enquanto forem suficientes para suas práticas de marketing. Por exemplo, você não precisa do histórico completo de transações do cliente no Adobe Campaign para acompanhar as últimas compras.

Você pode declarar o atributo &quot;deleteStatus&quot; em um esquema. É mais eficiente marcar o registro como excluído e, em seguida, adiar a exclusão na tarefa de limpeza.

## Desempenho {#performance}

Para garantir melhor desempenho a qualquer momento, siga as práticas recomendadas abaixo.

### Recomendações gerais {#general-recommendations}

* Evite usar operações como &quot;CONTAINS&quot; em consultas. Se você sabe o que é esperado e deseja filtrar, aplique a mesma condição com um &quot;EQUAL TO&quot; ou outros operadores de filtro específicos.
* Evite unir a campos não indexados ao mesmo tempo em que cria dados em fluxos de trabalho.
* Tente garantir que processos como importação e exportação ocorram fora do horário comercial.
* Certifique-se de que existe um calendário para todas as atividades diárias e que cumpre o calendário.
* Se um ou alguns dos processos diários falharem e se for obrigatório executá-lo no mesmo dia, verifique se não há processos conflitantes em execução quando o processo manual é iniciado, pois isso pode afetar o desempenho do sistema.
* Certifique-se de que nenhuma campanha diária seja executada durante o processo de importação ou quando qualquer processo manual for executado.
* Use uma ou várias tabelas de referência em vez de duplicar um campo em cada linha. Ao usar pares de chave/valor, é preferível escolher uma chave numérica.
* Uma string curta permanece aceitável. Caso as tabelas de referências já estejam em vigor em um sistema externo, reutilizar o mesmo facilitará a integração de dados com o Adobe Campaign.

### Relações de um para muitos {#one-to-many-relationships}

* O design de dados afeta a usabilidade e a funcionalidade. Se você projetar seu modelo de dados com muitas relações um para muitos, isso torna mais difícil para os usuários construírem uma lógica significativa no aplicativo. A lógica de filtro um para muitos pode ser difícil para comerciantes não técnicos construírem e entenderem corretamente.
* É bom ter todos os campos essenciais em uma tabela, pois facilita a criação de consultas pelos usuários. Às vezes, também é bom que o desempenho duplique alguns campos nas tabelas se puder evitar uma junção.
* Determinadas funcionalidades incorporadas não poderão fazer referência a relações one-to-many, por exemplo, fórmula de Ponderação de oferta e Entregas.

## Tabelas grandes {#large-tables}

O Adobe Campaign depende de mecanismos de banco de dados de terceiros. Dependendo do provedor, a otimização do desempenho para tabelas maiores pode exigir um design específico.

Abaixo estão algumas práticas recomendadas comuns que devem ser seguidas ao projetar seu modelo de dados usando tabelas grandes e junções complexas.

* Ao usar tabelas de destinatários personalizadas adicionais, verifique se você tem uma tabela de log dedicada para cada mapeamento de entrega.
* Reduza o número de colunas, principalmente identificando as que não são usadas.
* Otimize as relações do modelo de dados evitando junções complexas, como junções em várias condições e/ou em várias colunas.
* Para teclas de junção, sempre use dados numéricos em vez de sequências de caracteres.
* Reduza o máximo possível a profundidade da retenção de registros. Se precisar de um histórico mais profundo, você pode agregar computação e/ou manipular tabelas de log personalizadas para armazenar um histórico maior.

### Tamanho das tabelas {#size-of-tables}

O tamanho da tabela é uma combinação do número de registros e do número de colunas por registro. Ambos podem afetar o desempenho das consultas.

* Uma tabela de tamanho **** pequeno é semelhante à tabela Entrega.
* Uma tabela de tamanho **** médio é igual ao tamanho da tabela Destinatário. Ele tem um registro por cliente.
* Uma tabela **grande** é semelhante à tabela de log Amplo. Ele tem muitos registros por cliente.
Por exemplo, se seu banco de dados contém 10 milhões de destinatários, a tabela de log Amplo contém cerca de 100 a 200 milhões de mensagens e a tabela Entrega contém alguns milhares de registros.

No PostgreSQL, uma linha não deve exceder 8 KB para evitar o mecanismo [TOAST](https://wiki.postgresql.org/wiki/TOAST) . Portanto, tente reduzir ao máximo o número de colunas e o tamanho de cada linha para preservar o desempenho ideal do sistema (memória e CPU).

O número de linhas também afeta o desempenho. O banco de dados do Adobe Campaign não foi desenvolvido para armazenar dados históricos que não são usados ativamente para direcionamento ou personalização - esse é um banco de dados operacional.

Para evitar qualquer problema de desempenho relacionado ao alto número de linhas, mantenha somente os registros necessários no banco de dados. Qualquer outro registro deve ser exportado para um data warehouse de terceiros e removido do banco de dados operacional do Adobe Campaign.

Estas são algumas práticas recomendadas relacionadas ao tamanho das tabelas:

* Projete tabelas grandes com menos campos e mais dados numéricos.
* Não use um grande tipo de coluna (ex: Int64) para armazenar números pequenos como valores booleanos.
* Remova colunas não usadas da definição da tabela.
* Não mantenha dados históricos ou inativos no banco de dados do Adobe Campaign (exportação e limpeza).

Aqui está um exemplo:

![](assets/transaction-table-example.png)

Neste exemplo:
* As tabelas *Transação* e Item ** de Transação são grandes: mais de 10 milhões.
* As tabelas *Produto* e *Loja* são menores: menos de 10.000.
* A etiqueta do produto e a referência foram colocadas na tabela *Produto* .
* A tabela Item *de* Transação tem apenas um link para a tabela *Produto* , que é numérica.

<!--For more detailed best practices on how to optimize the database design for larger volumes, see [Campaign Classic Data model Best practices](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).-->