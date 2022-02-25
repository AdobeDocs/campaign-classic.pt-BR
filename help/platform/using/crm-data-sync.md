---
product: campaign
title: Sincronização de dados dos Conectores CRM
description: Gerenciar dados entre o Campaign e o CRM
feature: Salesforce Integration, Microsoft CRM Integration
exl-id: 7f9eda15-76e8-40a1-8302-004cea085778
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: ht
source-wordcount: '1536'
ht-degree: 100%

---

# Sincronizar dados entre o Campaign e o CRM {#data-synchronization}

![](../../assets/common.svg)

A sincronização de dados entre o Adobe Campaign e o CRM é realizada por meio de uma atividade dedicada de fluxo de trabalho: [conector CRM](../../workflow/using/crm-connector.md).

Por exemplo, para importar os dados do Microsoft Dynamics para o Adobe Campaign, crie o seguinte tipo de fluxo de trabalho:

![](assets/crm_connectors_msdynamics_07.png)

Esse fluxo de trabalho importa contatos por meio do Microsoft Dynamics, sincroniza com os dados existentes do Adobe Campaign, exclui os contatos duplicados e atualiza o banco de dados do Adobe Campaign.

A atividade **[!UICONTROL CRM Connector]** precisa ser configurada para sincronizar dados.

![](assets/crm_connectors_msdynamics_08.png)

Com essa atividade, você pode:

* Importar do CRM - [Saiba mais](#importing-from-the-crm)
* Exportar para o CRM - [Saiba mais](#exporting-to-the-crm)
* Importar objetos excluídos no CRM - [Saiba mais](#importing-objects-deleted-in-the-crm)
* Excluir objetos no CRM - [Saiba mais](#deleting-objects-in-the-crm)

![](assets/crm_task_select_op.png)

Selecione a conta externa que corresponde ao CRM que você deseja configurar a sincronização, e depois selecione o objeto a ser sincronizado: contas, oportunidades, clientes potencias, contatos, etc.

![](assets/crm_task_select_obj.png)

A configuração dessa atividade depende do processo a ser executado. Várias configurações são detalhadas abaixo.

## Importar do CRM {#importing-from-the-crm}

Para importar dados por meio do CRM no Adobe Campaign, você precisa criar o seguinte tipo de fluxo de trabalho:

![](assets/crm_wf_import.png)

Para uma atividade de importação, as etapas de configuração da atividade do **[!UICONTROL CRM Connector]** são:

1. Selecione uma operação **[!UICONTROL Import from the CRM]**.
1. Vá até a lista suspensa **[!UICONTROL Remote object]** e selecione o objeto relacionado ao processo. Esse objeto coincide com uma das tabelas criadas no Adobe Campaign durante a configuração do conector.
1. Vá até a seção **[!UICONTROL Remote fields]** e insira os campos que serão importados.

   Para adicionar um campo, clique no botão **[!UICONTROL Add]** na barra de ferramentas e, em seguida, clique no ícone **[!UICONTROL Edit expression]**.

   ![](assets/crm_task_import_add_field.png)

   Se necessário, altere o formato dos dados através da lista suspensa das colunas **[!UICONTROL Conversion]**. Os possíveis tipos de conversão são detalhados em [Formato dos dados](#data-format).

   >[!IMPORTANT]
   >
   >O identificador do registro no CRM é obrigatório para vincular objetos no CRM e no Adobe Campaign. Ele é adicionado automaticamente quando a caixa é aprovada.
   >
   >A última data de modificação no lado do CRM também é obrigatória para importações de dados incrementais.

1. Você também pode filtrar os dados a serem importados com base nas suas necessidades. Para fazer isso, clique em **[!UICONTROL Edit the filter...]**.

   No exemplo a seguir, o Adobe Campaign só importará contatos nos quais algumas atividades foram registradas desde 1º de novembro de 2012.

   ![](assets/crm_task_import_filter.png)

   >[!IMPORTANT]
   >
   >As limitações vinculadas aos modos do filtro de dados são detalhadas em [Filtros de dados](#filtering-data).

1. A opção **[!UICONTROL Use automatic index...]** permite gerenciar automaticamente a sincronização de objetos incrementais entre o CRM e o Adobe Campaign, dependendo da data e da última modificação.

   Para obter mais informações, consulte [Gerenciamento de variáveis](#variable-management).

### Gerenciar variáveis {#variable-management}

Habilite a opção **[!UICONTROL Automatic index]** para coletar apenas objetos modificados desde a última importação.

![](assets/crm_task_import_option.png)

A data da última sincronização é armazenada em uma opção especificada na janela de configuração, por padrão: **LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**.

>[!NOTE]
>
>Essa nota se aplica somente à atividade genérica **[!UICONTROL CRM Connector]**. Para outras atividades do CRM, o processo é automático.
>
>Essa opção deve ser criada e preenchida manualmente em **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Deve ser uma opção de texto e seu valor deve corresponder ao seguinte formato: **aaaa/MM/dd hh:mm:ss**.
> 
>Você precisa atualizar essa opção manualmente para qualquer outra importação.

É possível especificar o campo do CRM remoto que será levado em consideração para identificar as alterações mais recentes.

Por padrão, os seguintes campos são usados (na ordem especificada):

* Para o Microsoft Dynamics: **modifiedon**,
* Para o Salesforce.com: **LastModifiedDate**, **SystemModstamp**.

A ativação da opção **[!UICONTROL Automatic index]** gera três variáveis que podem ser usadas no fluxo de trabalho de sincronização por meio de uma atividade do tipo **[!UICONTROL JavaScript code]**. Essas atividades são:

* **vars.crmOptionName**: representa o nome da opção que contém a data de última importação.
* **vars.crmStartImport**: representa a data de início (incluída) da última recuperação de dados.
* **vars.crmEndDate**: representa a data final (excluída) da última recuperação de dados.

   >[!NOTE]
   >
   >Essas datas são mostradas no seguinte formato: **aaaa/MM/dd hh:mm:ss**.

### Filtrar dados {#filtering-data}

Para garantir uma operação eficiente com os vários CRMs, os filtros precisam ser criados com as seguintes regras:

* Cada nível de filtragem só pode usar um tipo de operador.
* O operador AND NOT não é suportado.
* Comparações podem dizer respeito somente a valores nulos (tipo &quot;está vazio&quot;/&quot;não está vazio&quot;) ou números. Isso significa que o valor (coluna à direita) é avaliado e o resultado dessa avaliação deve ser um número. Portanto, as comparações do tipo JOIN não são compatíveis.
* O valor contido na coluna à direita é avaliado em JavaScript.
* Não há suporte para comparações JOIN.
* A expressão na coluna à esquerda deve ser um campo. Ele não pode ser uma combinação de várias expressões, um número, etc.

Por exemplo, as condições de filtragem a seguir NÃO serão válidas para uma importação de CRM, pois o operador OR é colocado no mesmo nível que os operadores AND:

* O operador OR é colocado no mesmo nível que os operadores AND
* As comparações são realizadas em cadeias de texto

![](assets/crm_import_wrong_filter.png)

### Ordenar por {#order-by}

No Microsoft Dynamics e no Salesforce.com, você pode classificar os campos remotos a serem importados em ordem crescente ou decrescente.

Para fazer isso, clique no link **[!UICONTROL Order by]** e adicione as colunas à lista.

A ordem das colunas na lista é a ordem de classificação:

![](assets/crm_import_order.png)

### Identificação de registro {#record-identification}

Em vez de importar elementos incluídos (e possivelmente filtrados) no CRM, você pode usar uma população calculada previamente no workflow.

Para fazer isso, selecione a opção **[!UICONTROL Use the population calculated upstream]** e especifique o campo que contém o identificador remoto.

Em seguida, selecione os campos da população de entrada que deseja importar, conforme mostrado abaixo:

![](assets/crm_wf_import_calculated_population.png)

## Como exportar para o CRM {#exporting-to-the-crm}

A exportação de dados do Adobe Campaign para o CRM permite copiar todo o conteúdo para um banco de dados do CRM.

Para exportar dados para o CRM, você precisa criar o seguinte tipo de workflow:

![](assets/crm_export_diagram.png)

Para uma exportação, aplique a seguinte configuração à atividade do **[!UICONTROL CRM Connector]**:

1. Selecione uma operação **[!UICONTROL Export to CRM]**.
1. Vá até a lista suspensa **[!UICONTROL Remote object]** e selecione o objeto relacionado ao processo. Esse objeto coincide com uma das tabelas criadas no Adobe Campaign durante a configuração do conector.

   >[!IMPORTANT]
   >
   >A função de exportação da atividade do **[!UICONTROL CRM Connector]** pode inserir ou atualizar campos no lado do CRM. Para habilitar atualizações de campo no CRM, você precisa especificar a chave primária da tabela remota. Se a chave estiver faltando, os dados serão inseridos (ao invés de serem atualizados).

1. Marque a opção **[!UICONTROL Export in Batches]** se precisar de exportações mais rápidas.

   ![](assets/crm_export_config_2.png)

1. Na seção **[!UICONTROL Mapping]**, clique em **[!UICONTROL New]** para especificar os campos que serão exportados e o mapeamento deles no CRM.

   ![](assets/crm_export_config.png)

   Para adicionar um campo, clique no botão **[!UICONTROL Add]** na barra de ferramentas e, em seguida, clique no ícone **[!UICONTROL Edit expression]**.

   >[!NOTE]
   >
   >Para determinado campo, se nenhuma correspondência for definida no lado do CRM, os valores não poderão ser atualizados: eles são inseridos diretamente no CRM.

   Se necessário, altere o formato dos dados através da lista suspensa das colunas **[!UICONTROL Conversion]**. Os possíveis tipos de conversão são detalhados em [Formato dos dados](#data-format).

   >[!NOTE]
   >
   >A lista de registros a serem exportados e o resultado da exportação são salvas em um arquivo temporário que permanece acessível até que o workflow seja concluído ou reiniciado. Isso permite que você inicie o processo novamente em caso de erro, sem correr o risco de exportar o mesmo registro várias vezes ou perder dados.

## Configurações adicionais {#additional-configurations}

### Formato dos dados {#data-format}

É possível converter o formato dos dados de forma instantânea ao importá-los para o CRM.

Para fazer isso, selecione a conversão a ser aplicada na coluna correspondente.

![](assets/crm_task_import.png)

O modo **[!UICONTROL Default]** aplica conversão automática de dados, que na maioria dos casos é igual a copiar/colar os dados. No entanto, o gerenciamento de fuso horário é aplicado.

Outras conversões possíveis são:

* **[!UICONTROL Date only]**: esse modo exclui os campos do tipo Data + Hora.
* **[!UICONTROL Without time offset]**: esse modo cancela o gerenciamento de fuso horário aplicado no modo padrão.
* **[!UICONTROL Copy/Paste]**: esse modo usa dados brutos como cadeias de caracteres (sem conversão).

### Processamento de erros {#error-processing}

Dentro da estrutura de importações ou exportações de dados, é possível aplicar um processo específico a erros e rejeições. Para fazer isso, selecione as opções **[!UICONTROL Process rejects]** e **[!UICONTROL Process errors]** na guia **[!UICONTROL Behavior]**.

![](assets/crm_export_options.png)

Essas opções colocam as transições de saída correspondentes.

![](assets/crm_export_transitions.png)

Em seguida, coloque as atividades relevantes aos processos que deseja aplicar.

Para processar erros, por exemplo, você pode adicionar uma caixa de espera e agendar novas tentativas.

As rejeições são coletadas com o código de erro e a mensagem relacionada, isso significa que é possível configurar o rastreamento de rejeições para otimizar o processo de sincronização.

>[!NOTE]
>
>Mesmo quando a opção **[!UICONTROL Process rejects]** não está habilitada, um aviso é gerado para cada coluna rejeitada com um código de erro e uma mensagem.

A transição **[!UICONTROL Reject]** de saída permite que você acesse o schema de saída que contém as colunas específicas relevantes para mensagens e códigos de erro. Para o Salesforce.com, essa coluna é **errorSymbol** (símbolo de erro, diferente do código de erro), **errorMessage** (descrição do contexto de erro).

## Importar objetos excluídos no CRM {#importing-objects-deleted-in-the-crm}

Para habilitar a configuração de um processo extenso de sincronização de dados, você pode importar objetos excluídos do CRM para o Adobe Campaign.

Para fazer isso, siga as etapas abaixo:

1. Selecione uma operação **[!UICONTROL Import objects deleted in the CRM]**.
1. Vá até a lista suspensa **[!UICONTROL Remote object]** e selecione o objeto relacionado ao processo. Esse objeto coincide com uma das tabelas criadas no Adobe Campaign durante a configuração do conector.
1. Especifique o período de exclusão que será considerado nos campos **[!UICONTROL Start date]** e **[!UICONTROL End date]**. Essas datas serão incluídas no período.

   ![](assets/crm_import_deleted_obj.png)

   >[!IMPORTANT]
   >
   >O período de exclusão do elemento deve coincidir com as limitações específicas do CRM. Isso significa que para o Salesforce.com, por exemplo, elementos excluídos há mais de 30 dias não podem ser recuperados.

## Excluir objetos no CRM {#deleting-objects-in-the-crm}

Para excluir objetos no lado do CRM, você precisa especificar a chave primária dos elementos remotos que serão excluídos.

![](assets/crm_delete_in_crm.png)

A guia **[!UICONTROL Behavior]** permite habilitar o processamento de rejeições. Essa opção gera uma segunda transição de saída para a atividade **[!UICONTROL CRM connector]**. Para obter mais informações, consulte [Processamento de erros](#error-processing).

>[!NOTE]
>
>Mesmo quando a opção **[!UICONTROL Process rejects]** está desabilitada, um aviso é gerado para cada coluna rejeitada.
