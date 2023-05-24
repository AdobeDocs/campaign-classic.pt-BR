---
product: campaign
title: Práticas recomendadas do modelo de dados
description: Saiba como trabalhar com o modelo de dados do Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Data Model
exl-id: 9c59b89c-3542-4a17-a46f-3a1e58de0748
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '3988'
ht-degree: 1%

---

# Práticas recomendadas do modelo de dados{#data-model-best-practices}

Este documento descreve as principais recomendações ao projetar o modelo de dados do Adobe Campaign.

Para obter uma melhor compreensão das tabelas integradas do Campaign e sua interação, consulte [nesta seção](../../configuration/using/about-data-model.md) seção.

Ler [esta documentação](../../configuration/using/about-schema-reference.md) para começar a usar esquemas do Campaign. Saiba como configurar esquemas de extensão para estender o modelo de dados conceituais do banco de dados do Adobe Campaign no [este documento](../../configuration/using/about-schema-edition.md).

## Visão geral {#overview}

O sistema Adobe Campaign é extremamente flexível e pode ser estendido além da implementação inicial. No entanto, embora as possibilidades sejam infinitas, é essencial tomar decisões sábias e criar bases sólidas para começar a projetar seu modelo de dados.

Este documento fornece casos de uso comuns e práticas recomendadas para saber como arquitetar corretamente sua ferramenta Adobe Campaign.

## Arquitetura do modelo de dados {#data-model-architecture}

O Adobe Campaign é um eficiente sistema de gerenciamento de campanhas em vários canais que pode ajudar você a alinhar suas estratégias online e offline para criar experiências personalizadas de clientes.

### Abordagem centrada no cliente {#customer-centric-approach}

Embora a maioria dos provedores de serviços de email esteja se comunicando com os clientes por meio de uma abordagem centrada em listas, o Adobe Campaign depende de um banco de dados relacional para aproveitar uma visualização mais ampla dos clientes e seus atributos.

Essa abordagem centrada no cliente é mostrada no gráfico abaixo. A variável **Recipient** A tabela em cinza representa a principal tabela do cliente em torno da qual tudo está sendo criado:

![](assets/customer-centric-data-model.png)

Para acessar a descrição de cada tabela, vá para **[!UICONTROL Admin > Configuration > Data schemas]**, selecione um recurso na lista e clique no botão **[!UICONTROL Documentation]** guia.

O modelo de dados padrão do Adobe Campaign é apresentado em [este documento](../../configuration/using/data-model-description.md).

>[!NOTE]
>
>O Adobe Campaign Classic permite criar uma tabela de cliente personalizada. No entanto, na maioria dos casos, é recomendável aproveitar o padrão [Tabela de destinatários](../../configuration/using/about-data-model.md#default-recipient-table) que já tem tabelas e recursos adicionais pré-criados.

### Dados para o Adobe Campaign {#data-for-campaign}

Quais dados devem ser enviados para o Adobe Campaign? É essencial determinar os dados necessários para suas atividades de marketing.

>[!NOTE]
>
>O Adobe Campaign não é um data warehouse nem uma ferramenta de relatórios. Portanto, não tente importar todos os clientes possíveis e suas informações associadas para o Adobe Campaign, ou importe dados que serão usados apenas para criar relatórios.

Para decidir se um atributo seria necessário ou não no Adobe Campaign, pergunte se ele se enquadra em uma destas categorias:

* Atributo usado para **segmentação**
* Atributo usado para **processos de gerenciamento de dados** (cálculo agregado por exemplo)
* Atributo usado para **personalização**

Se não estiver se encaixando em nenhum desses, você provavelmente não precisará desse atributo no Adobe Campaign.

### Escolha dos tipos de dados {#data-types}

Para garantir uma boa arquitetura e desempenho do sistema, siga as práticas recomendadas abaixo para configurar dados no Adobe Campaign.

* Uma tabela grande deve ter principalmente campos numéricos e conter links para tabelas de referência (ao trabalhar com lista de valores).
* A variável **expr** attribute permite definir um atributo de esquema como um campo calculado em vez de um valor de conjunto físico em uma tabela. Isso pode permitir o acesso às informações em um formato diferente (como idade e data de nascimento, por exemplo), sem a necessidade de armazenar ambos os valores. Essa é uma boa maneira de evitar campos duplicados. Por exemplo, a tabela Recipient usa uma expressão para o domínio, que já está presente no campo email.
* No entanto, quando o cálculo da expressão é complexo, não é recomendável usar o **expr** o atributo como cálculo instantâneo pode afetar o desempenho das consultas.
* A variável **XML** O tipo é uma boa maneira de evitar a criação de muitos campos. Mas também ocupa espaço em disco, pois usa uma coluna CLOB no banco de dados. Ela também pode levar a consultas SQL complexas e afetar o desempenho.
* O comprimento de um **string** deve ser sempre definido com a coluna. Por padrão, o comprimento máximo no Adobe Campaign é de 255, mas o Adobe recomenda manter o campo mais curto, se você já souber que o tamanho não excederá um comprimento mais curto.
* É aceitável ter um campo mais curto no Adobe Campaign do que no sistema de origem se você tiver certeza de que o tamanho no sistema de origem foi superestimado e não seria atingido. Isso pode significar uma string menor ou um inteiro menor no Adobe Campaign.

### Escolha de campos {#choice-of-fields}

Um campo deve ser armazenado em uma tabela se tiver um propósito de direcionamento ou personalização. Em outras palavras, se um campo não é usado para enviar um email personalizado ou usado como critério em um query, ele ocupa espaço em disco, enquanto é inútil.

Para instâncias híbridas e no local, o FDA (Federated Data Access, um recurso opcional que permite acessar dados externos) aborda a necessidade de adicionar um campo &quot;instantaneamente&quot; durante um processo de campanha. Não é necessário importar tudo se você tiver o FDA. Para obter mais informações, consulte [Sobre o Federated Data Access](../../installation/using/about-fda.md).

### Escolha de teclas {#choice-of-keys}

Além do **autopk** definida por padrão na maioria das tabelas, você deve considerar adicionar algumas chaves lógicas ou de negócios (número da conta, número do cliente e assim por diante). Ele pode ser usado posteriormente para importações/reconciliação ou pacotes de dados. Para obter mais informações, consulte [Identificadores](#identifiers).

Chaves eficientes são essenciais para o desempenho. Os tipos de dados numéricos devem sempre ser preferidos como chaves para tabelas.

Para o banco de dados do SQLServer, você pode considerar o uso de &quot;índice clusterizado&quot; se o desempenho for necessário. Como o Adobe não lida com isso, é necessário criá-lo em SQL.

### Tablespaces dedicados {#dedicated-tablespaces}

O atributo de tablespace no esquema permite especificar um tablespace dedicado para uma tabela.

O assistente de instalação permite armazenar objetos por tipo (dados, temporário e índice).

Os tablespaces dedicados são melhores para particionamento, regras de segurança e permitem administração fluida e flexível, melhor otimização e desempenho.

## Identificadores {#identifiers}

Os recursos do Adobe Campaign têm três identificadores e é possível adicionar um identificador adicional.

A tabela a seguir descreve esses identificadores e sua finalidade.

| Identifier | Descrição | Práticas recomendadas |
|--- |--- |--- |
| ID | <ul><li>A id é a chave primária física de uma tabela do Adobe Campaign. Para tabelas prontas para uso, é um número gerado de 32 bits de uma sequência</li><li>Normalmente, esse identificador é exclusivo de uma instância específica do Adobe Campaign. </li><li>Uma ID gerada automaticamente pode ser visível em uma definição de esquema. Pesquise o *autopk=&quot;true&quot;* atributo.</li></ul> | <ul><li>Identificadores gerados automaticamente não devem ser usados como referência em um fluxo de trabalho ou em uma definição de pacote.</li><li>Não se deve supor que a ID sempre será um número crescente.</li><li>A ID em uma tabela pronta para uso é um número de 32 bits e esse tipo não deve ser alterado. Esse número é retirado de uma &quot;sequência&quot; abordada na seção com o mesmo nome.</li></ul> |
| Nome (ou nome interno) | <ul><li>Essas informações são um identificador exclusivo de um registro em uma tabela. Esse valor pode ser atualizado manualmente, geralmente com um nome gerado.</li><li>Esse identificador mantém seu valor quando implantado em uma instância diferente do Adobe Campaign e não deve estar vazio.</li></ul> | <ul><li>Renomeie o nome do registro gerado pelo Adobe Campaign se o objeto deve ser implantado de um ambiente para outro.</li><li>Quando um objeto tem um atributo de namespace (*schema* por exemplo), esse namespace comum será aproveitado em todos os objetos personalizados criados. Alguns namespaces reservados não devem ser usados: *nms*, *xtk*, *nl*, *ncl*, *crm*, *xxl*.</li><li>Quando um objeto não tem namespace (*fluxo de trabalho* ou *delivery* por exemplo), essa noção de namespace seria adicionada como um prefixo de um objeto de nome interno: *namespaceMyObjectName*.</li><li>Não use caracteres especiais como espaço &quot;&quot;, ponto e vírgula &quot;:&quot; ou hífen &quot;-&quot;. Todos esses caracteres seriam substituídos por um sublinhado &quot;_&quot; (caractere permitido). Por exemplo, &quot;abc-def&quot; e &quot;abc:def&quot; seriam armazenados como &quot;abc_def&quot; e se substituiriam.</li></ul> |
| Rótulo | <ul><li>O rótulo é o identificador comercial de um objeto ou registro no Adobe Campaign.</li><li>Esse objeto permite espaços e caracteres especiais.</li><li>Isso não garante a exclusividade de um registro.</li></ul> | <ul><li>É recomendável determinar uma estrutura para seus rótulos de objeto.</li><li>Essa é a solução mais simples para identificar um registro ou objeto para um usuário do Adobe Campaign.</li></ul> |

## Chaves internas personalizadas {#custom-internal-keys}

As chaves primárias são necessárias para cada tabela criada no Adobe Campaign.

A maioria das organizações está importando registros de sistemas externos. Embora a chave física da tabela Recipient seja o atributo &quot;id&quot;, é possível determinar uma chave personalizada além disso.

Essa chave personalizada é a chave primária de registro real no sistema externo que alimenta o Adobe Campaign.

Quando uma tabela pronta para uso tiver uma chave automática e uma chave interna, a chave interna será definida como um índice exclusivo na tabela do banco de dados física.

Ao criar uma tabela personalizada, você tem duas opções:
* Uma combinação de chave gerada automaticamente (id) e chave interna (personalizada). Essa opção é interessante se a chave do sistema for uma chave composta ou não for um inteiro. Inteiros fornecerão maiores desempenhos em tabelas grandes e juntando-se a outras tabelas.
* Usar a chave primária como a chave primária do sistema externo. Essa solução geralmente é preferida, pois simplifica a abordagem de importar e exportar dados, com uma chave consistente entre sistemas diferentes. O Autopk deve ser desativado se o nome da chave for &quot;id&quot; e se esperar que seja preenchido com valores externos (não gerado automaticamente).

>[!IMPORTANT]
>
>Um autopk não deve ser usado como referência em fluxos de trabalho.

## Sequências {#sequences}

A chave primária do Adobe Campaign é uma ID gerada automaticamente para todas as tabelas predefinidas e pode ser a mesma para tabelas personalizadas. Para obter mais informações, consulte [esta seção](#identifiers).

Esse valor é obtido do que é chamado de **sequência**, que é um objeto de banco de dados usado para gerar uma sequência numérica.

Há dois tipos de sequências:
* **Compartilhado**: mais de uma tabela escolheria a ID na mesma sequência. Isso significa que se um id &quot;X&quot; for usado por uma tabela, nenhuma outra tabela que compartilhe a mesma sequência terá um registro com esse id &quot;X&quot;. **XtkNewId** é a sequência compartilhada padrão disponível no Adobe Campaign.
* **Dedicado**: somente uma tabela está selecionando suas ids da sequência. O nome da sequência normalmente conteria o nome da tabela.

>[!IMPORTANT]
>
>A sequência é um valor inteiro de 32 bits, com um número máximo finito de valores disponíveis: 2,14 bilhões. Depois de atingir o valor máximo, a sequência volta para 0, para reciclar ids.
>
>Se os dados antigos não tiverem sido removidos, o resultado será uma violação de chave exclusiva, que se torna um bloqueador para a integridade e o uso da plataforma. O Adobe Campaign não poderia enviar comunicações (quando isso afeta a tabela de logs do delivery) e o desempenho seria altamente afetado.

Portanto, um cliente que enviasse 6 bilhões de emails anualmente com um período de retenção de 180 dias para seus registros ficaria sem ids em quatro meses. Para evitar esse desafio, certifique-se de ter configurações de limpeza de acordo com seus volumes. Para obter mais informações, consulte [esta seção](#data-retention).

Quando uma tabela personalizada está sendo criada no Adobe Campaign com uma chave primária como um autoPK, uma sequência dedicada personalizada deve ser sistematicamente associada a essa tabela.

Por padrão, uma sequência personalizada terá valores que variam de +1.000 a +2,1BB. Tecnicamente, é possível obter uma gama completa de 4BB habilitando ids negativas. Isso deve ser usado com cuidado e uma ID será perdida ao passar de números negativos para positivos: o registro 0 normalmente é ignorado pelo Adobe Campaign em consultas SQL geradas.

Para saber mais sobre a exaustão das sequências, assista [este vídeo](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html).

## Índices {#indexes}

Os índices são essenciais para o desempenho. Quando você declarar uma chave no esquema, o Adobe criará automaticamente um índice nos campos da chave. Você também pode declarar mais índices para consultas que não usam a chave.

A Adobe recomenda definir índices adicionais, pois pode melhorar o desempenho.

No entanto, lembre-se do seguinte:

* O uso do índice está vinculado ao seu padrão de acesso. A otimização da indexação geralmente é uma parte essencial no design do banco de dados e deve ser tratada por especialistas. A adição de índices geralmente é um fluxo de trabalho iterativo anexado à manutenção do banco de dados. Isso é feito ao longo do tempo, passo a passo, para solucionar problemas de desempenho ao ocorrer.
* Os índices aumentam o tamanho geral da tabela (para armazenar o próprio índice).
* Adicionar índice em colunas pode melhorar o desempenho do acesso de leitura de dados (SELECT), mas pode diminuir o desempenho do acesso de gravação de dados (UPDATE).
* Como isso afeta o desempenho durante a inserção de dados, os índices devem ser limitados em tamanho e número.
* Não adicione índices quando não for necessário. Verifique se isso é necessário e aumenta o desempenho geral de suas consultas (testar e aprender).
* De modo geral, um índice é eficiente se você souber que as consultas não trarão mais de 10% dos registros de volta.
* Selecione cuidadosamente os índices que precisam ser definidos.
* Não remova índices nativos de tabelas prontas para uso.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

### Exemplo

O gerenciamento de índices pode se tornar muito complexo, portanto, é importante entender como eles funcionam. Para ilustrar essa complexidade, vamos ver um exemplo básico, como pesquisar destinatários filtrando o nome e o sobrenome. Para fazer isso:
1. Vá para a pasta que lista todos os destinatários no banco de dados. Para obter mais informações, consulte [Gerenciamento de perfis](../../platform/using/managing-profiles.md).
1. Clique com o botão direito do mouse no **[!UICONTROL First name]** campo.
1. Selecione **[!UICONTROL Filter on this field]**.

   ![](assets/data-model-index-example.png)

1. Repita essa operação para o **[!UICONTROL Last name]** campo.

Os dois filtros correspondentes são adicionados na parte superior da tela.

![](assets/data-model-index-search.png)

Agora você pode executar a filtragem de pesquisa no **[!UICONTROL First name]** e **[!UICONTROL Last name]** de acordo com as várias condições de filtro.

Agora, para acelerar a pesquisa nesses filtros, é possível adicionar índices. Mas quais índices devem ser usados?

>[!NOTE]
>
>Este exemplo se aplica a clientes hospedados que usam um banco de dados PostgreSQL.

A tabela a seguir mostra em quais casos os três índices descritos abaixo são usados ou não, de acordo com o padrão de acesso exibido na primeira coluna.

| Critérios de pesquisa | Índice 1 (Nome + Sobrenome) | Índice 2 (apenas nome) | Índice 3 (somente sobrenome) | Comentários |
|--- |--- |--- |--- |--- |
| Nome igual a &quot;Johnny&quot; | Usado | Usado | Não usado | Como o nome está na primeira posição no índice 1, ele será usado mesmo assim: não há necessidade de adicionar um critério sobre o sobrenome. |
| O nome é igual a &quot;Johnny&quot; E o sobrenome é igual a &quot;Smith&quot; | Usado | Não usado | Não usado | Como ambos os atributos são pesquisados na mesma consulta, somente o índice que combina ambos os atributos será usado. |
| O sobrenome é igual a &quot;Smith&quot; | Não usado | Não usado | Usado | A ordem dos atributos no índice é levada em conta. Se você não corresponder a essa ordem, o índice pode não ser usado. |
| O nome começa com &quot;João&quot; | Usado | Usado | Não usado | &quot;Pesquisa à esquerda&quot; habilitará os índices. |
| O nome termina com &quot;nny&quot; | Não usado | Não usado | Não usado | &quot;Pesquisa direta&quot; desativará os índices e uma verificação completa será executada. Alguns tipos de índice específicos podem lidar com esse caso de uso, mas não estão disponíveis por padrão no Adobe Campaign. |
| O nome contém &quot;John&quot; | Não usado | Não usado | Não usado | É uma combinação de pesquisas &quot;esquerda&quot; e &quot;direita&quot;. Por causa deste último, ele desativará os índices e uma verificação completa será executada. |
| O nome é igual a &quot;john&quot; | Não usado | Não usado | Não usado | Os índices fazem distinção entre maiúsculas e minúsculas. Para não diferenciar maiúsculas de minúsculas, você deve criar um índice específico que inclua uma função SQL como &quot;upper(firstname)&quot;. Você deve fazer o mesmo com outras transformações de dados, como &quot;unaccent(firstname)&quot;. |

## Links e cardinalidade {#links-and-cardinality}

### Links {#links}

Cuidado com a integridade &quot;própria&quot; em tabelas grandes. A exclusão de registros que têm tabelas amplas em &quot;própria&quot; integridade pode interromper a instância. A tabela é bloqueada e as exclusões são feitas uma por uma. Portanto, é melhor usar a integridade &quot;neutra&quot; em tabelas secundárias com grandes volumes.

Declarar um link como uma associação externa não é bom para o desempenho. O registro de id zero emula a funcionalidade de associação externa. Não é necessário declarar junções externas se o link usar o autopk.

Embora seja possível unir qualquer tabela em um fluxo de trabalho, o Adobe recomenda definir links comuns entre os recursos diretamente na definição da estrutura de dados.

O link deve ser definido em alinhamento com os dados reais nas tabelas. Uma definição incorreta poderia afetar os dados recuperados por meio de links, por exemplo, registros duplicados inesperadamente.

Nomeie o link de forma consistente com o nome da tabela: o nome do link deve ajudar a entender o que é a tabela distante.

Não nomeie um link com &quot;id&quot; como sufixo. Por exemplo, nomeie-o como &quot;transaction&quot; em vez de &quot;transactionId&quot;.

Por padrão, o Adobe Campaign criará um link usando a chave primária da tabela externa. Para maior clareza, é preferível definir explicitamente a associação na definição do link.

Um índice será adicionado aos atributos usados em um link.

Os links criado por e modificado por último estão presentes em muitas tabelas. É possível desativar o índice usando o atributo noDbIndex no link, se essas informações não estiverem sendo usadas pela empresa.

### Cardinalidade {#cardinality}

Ao projetar um link, verifique se o registro do target é exclusivo quando uma relação 1-1 for declarada. Caso contrário, a associação poderá retornar vários registros quando somente um for esperado. Isso resulta em erros durante a preparação do delivery quando &quot;a consulta retorna mais linhas do que o esperado&quot;. Defina o nome do link com o mesmo nome do schema de destino.

Defina um link com uma cardinalidade (1-N) no esquema no lado (1). Por exemplo, a relação Destinatário (1) - (N) Transação deve ser definida no schema da transação.

Observe que uma cardinalidade reversa de um link é (N) por padrão. É possível definir um link (1-1) adicionando o atributo revCardinality=&#39;single&#39; à definição do link.

Se o link reverso não deve estar visível para o usuário, você pode ocultá-lo com a definição de link revLink=&#39;_NENHUM_&#39;. Um bom caso de uso para isso é definir um link do recipient para a última transação concluída, por exemplo. Você só precisa ver o link do recipient para a última transação e nenhum link reverso é necessário para estar visível na tabela de transações.

Os links que executam uma associação externa (1-0..1) devem ser usados com cuidado, pois afetarão o desempenho do sistema.

## Retenção de dados - limpeza e limpeza {#data-retention}

O Adobe Campaign não é um data warehouse nem uma ferramenta de relatórios. Portanto, para garantir um bom desempenho da solução Adobe Campaign, o crescimento do banco de dados deve permanecer sob controle. Para isso, seguir algumas das práticas recomendadas abaixo pode ajudar.

Por padrão, os logs de entrega e rastreamento do Adobe Campaign têm uma duração de retenção de 180 dias. Um processo de limpeza é executado para remover qualquer log mais antigo que isso.

* Se quiser manter os logs por mais tempo, essa decisão deverá ser tomada com cuidado, dependendo do tamanho do banco de dados e do volume de mensagens enviadas. Como lembrete, a sequência Adobe Campaign é um inteiro de 32 bits.
* É recomendável não ter mais de 1 bilhão de registros por vez nessas tabelas (cerca de 50% dos 2,14 bilhões de ids disponíveis) para limitar os riscos de consumir todas as ids disponíveis. Isso exigirá que alguns clientes reduzam a duração da retenção para menos de 180 dias.

Saiba mais sobre a retenção de dados no [Diretrizes de privacidade e segurança do Campaign](../../platform/using/privacy-and-recommendations.md).

Saiba mais sobre o workflow de limpeza do banco de dados do Campaign [nesta seção](../../production/using/database-cleanup-workflow.md).

>[!IMPORTANT]
>
>As tabelas personalizadas não são removidas com o processo de limpeza padrão. Embora isso possa não ser necessário no primeiro dia, não se esqueça de criar um processo de limpeza para suas tabelas personalizadas, pois isso pode levar a desafios de desempenho.

Existem algumas soluções para minimizar a necessidade de registros no Adobe Campaign:
* Exporte os dados em um data warehouse para fora do Adobe Campaign.
* Gere valores agregados que usarão menos espaço enquanto forem suficientes para suas práticas de marketing. Por exemplo, você não precisa do histórico completo de transações do cliente no Adobe Campaign para rastrear as últimas compras.

Você pode declarar o atributo &quot;deleteStatus&quot; em um esquema. É mais eficiente marcar o registro como excluído e, em seguida, adiar a exclusão na tarefa de limpeza.

## Desempenho {#performance}

Para garantir um melhor desempenho a qualquer momento, siga as práticas recomendadas abaixo.

### Recomendações gerais {#general-recommendations}

* Evite usar operações como &quot;CONTAINS&quot; em consultas. Se você souber o que é esperado e quiser ser filtrado, aplique a mesma condição com um &quot;IGUAL A&quot; ou outros operadores de filtro específicos.
* Evite ingressar em campos não indexados ao criar dados em workflows.
* Tente e certifique-se de que processos como importação e exportação ocorram fora do horário comercial.
* Verifique se há uma programação para todas as atividades diárias e siga a programação.
* Se um ou alguns dos processos diários falharem e for obrigatório executá-los no mesmo dia, verifique se não há processos conflitantes em execução quando o processo manual for iniciado, pois isso pode afetar o desempenho do sistema.
* Certifique-se de que nenhuma das campanhas diárias seja executada durante o processo de importação ou quando qualquer processo manual for executado.
* Use uma ou várias tabelas de referência em vez de duplicar um campo em cada linha. Ao usar pares chave/valor, é preferível escolher uma chave numérica.
* Uma sequência curta permanece aceitável. Caso as tabelas de referência já estejam em vigor em um sistema externo, reutilizar o mesmo facilitará a integração de dados com o Adobe Campaign.

### Relacionamentos um para muitos {#one-to-many-relationships}

* O design de dados afeta a usabilidade e a funcionalidade. Se você projetar seu modelo de dados com várias relações um para muitos, será mais difícil para os usuários criar uma lógica significativa no aplicativo. A lógica de filtro de um para muitos pode ser difícil para profissionais de marketing não técnicos criarem e compreenderem corretamente.
* É bom ter todos os campos essenciais em uma tabela porque facilita a criação de consultas pelos usuários. Às vezes, também é bom que o desempenho duplique alguns campos em tabelas se puder evitar uma associação.
* Certas funcionalidades integradas não poderão fazer referência a relações um para muitos, por exemplo, fórmula de Ponderação da oferta e Entregas.

## Tabelas grandes {#large-tables}

O Adobe Campaign depende de mecanismos de banco de dados de terceiros. Dependendo do provedor, a otimização do desempenho para tabelas maiores pode exigir um design específico.

Abaixo estão algumas práticas recomendadas comuns que devem ser seguidas ao projetar seu modelo de dados usando tabelas grandes e associações complexas.

* Ao usar tabelas de recipients personalizadas adicionais, verifique se você tem uma tabela de log dedicada para cada mapeamento de delivery.
* Reduza o número de colunas, principalmente identificando aquelas que não são usadas.
* Otimize as relações do modelo de dados evitando associações complexas, como associações em várias condições e/ou colunas.
* Para chaves de junção, sempre use dados numéricos em vez de cadeias de caracteres.
* Reduza o máximo possível a profundidade da retenção de registros. Se precisar de um histórico mais profundo, você poderá agregar o cálculo e/ou manipular tabelas de log personalizadas para armazenar um histórico maior.

### Tamanho das tabelas {#size-of-tables}

O tamanho da tabela é uma combinação do número de registros e do número de colunas por registro. Ambos podem afetar o desempenho das consultas.

* A **tamanho pequeno** é semelhante à tabela Delivery.
* A **tamanho médio** for igual ao tamanho da tabela Recipient. Ele tem um registro por cliente.
* A **tamanho grande** A tabela é semelhante à tabela Broad log. Ele tem muitos registros por cliente.
Por exemplo, se o banco de dados contiver 10 milhões de recipients, a tabela Broad log conterá de 100 a 200 milhões de mensagens e a tabela Delivery conterá alguns milhares de registros.

No PostgreSQL, uma linha não deve exceder 8 KB para evitar [TORRADA](https://wiki.postgresql.org/wiki/TOAST) mecanismo. Portanto, tente reduzir o máximo possível o número de colunas e o tamanho de cada linha para preservar o desempenho ideal do sistema (memória e CPU).

O número de linhas também afeta o desempenho. O banco de dados do Adobe Campaign não foi projetado para armazenar dados históricos que não são usados ativamente para fins de direcionamento ou personalização. Este é um banco de dados operacional.

Para evitar qualquer problema de desempenho relacionado ao alto número de linhas, mantenha apenas os registros necessários no banco de dados. Qualquer outro registro deve ser exportado para um data warehouse de terceiros e removido do banco de dados operacional do Adobe Campaign.

Estas são algumas das práticas recomendadas relacionadas ao tamanho das tabelas:

* Crie tabelas grandes com menos campos e mais dados numéricos.
* Não use o tipo de coluna de número grande (por exemplo: Int64) para armazenar números pequenos como valores booleanos.
* Remover colunas não usadas da definição de tabela.
* Não mantenha dados históricos ou inativos no banco de dados do Adobe Campaign (exportar e limpar).

Aqui está um exemplo:

![](assets/transaction-table-example.png)

Neste exemplo:
* A variável *Transação* e *Item da Transação* as mesas são grandes: mais de 10 milhões.
* A variável *Produto* e *Loja* as tabelas são menores: menos de 10.000.
* O rótulo e a referência do produto foram colocados no *Produto* tabela.
* A variável *Item da Transação* A tabela tem apenas um link para o *Produto* tabela, que é numérica.
