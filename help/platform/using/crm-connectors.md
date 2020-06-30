---
title: Conectores CRM
seo-title: Conectores CRM
description: Conectores CRM
seo-description: null
page-status-flag: never-activated
uuid: ef3d88a1-b0fd-4790-b6e8-63fa339ef991
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dbe9080c-66e3-4ff6-8f16-959f9748f666
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: e25560152a16865dc415ac2ffa1975808b3f6bbc
workflow-type: ht
source-wordcount: '2541'
ht-degree: 100%

---


# Conectores CRM{#crm-connectors}

## Sobre conectores CRM {#about-crm-connectors}

O Adobe Campaign fornece vários conectores de CRM para vincular sua plataforma a sistemas de terceiros. Esses conectores de CRM permitem sincronizar contatos, contas, compras, etc. Eles facilitam a integração de seu aplicativo com vários aplicativos de terceiros e corporativos.

Esses conectores permitem uma integração de dados rápida e fácil: o Adobe Campaign fornece um assistente dedicado para coletar e selecionar entre as tabelas disponíveis no CRM. Isso garante a sincronização bidirecional para assegurar que os dados estejam sempre atualizados em todos os sistemas.

>[!NOTE]
>
>Esse recurso está disponível no Adobe Campaign através dos **conectores dedicados do CRM**.

A conexão com o CRM é realizada por meio de atividades dedicadas de workflow. Essas atividades são detalhadas no capítulo apresentado [nesta seção](../../workflow/using/crm-connector.md).

### Limitações e sistemas compatíveis com o CRM {#compatible-crm-systems-and-limitations}

Os CRMs listados abaixo podem ser integrados ao Adobe Campaign.

As versões compatíveis estão detalhadas na [Matriz de compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html).

* **Salesforce.com**

   Consulte [esta seção](#example-for-salesforce-com) para saber como configurar a conexão com o Salesforce.com.

   >[!CAUTION]
   >
   >Ao conectar o Adobe Campaign com Salesforce.com, as limitações são:
   >
   >    
   >    
   >    * As instâncias de produção de teste são compatíveis.
   >    * As regras de atribuição são compatíveis.
   >    * Várias enumerações de seleção não são compatíveis com o Adobe Campaign.


* **Oracle On Demand**

   Consulte [esta seção](#example-for-oracle-on-demand) para saber como configurar a conexão com o Oracle On Demand.

   >[!CAUTION]
   >
   >Ao conectar o Adobe Campaign com Oracle On Demand, as limitações são:
   >
   >    
   >    
   >    * O Adobe Campaign pode sincronizar qualquer objeto disponível nos templates padrão do Oracle On Demand. Se você tiver adicionado tabelas personalizadas no Oracle On Demand, elas não serão recuperadas no Adobe Campaign.
   >    * A versão da API v1.0 permite classificar ou filtrar dados durante uma query, mas não permite que você faça ambos simultaneamente.
   >    * Os dados enviados pelo Oracle On Demand não contêm informações de fuso horário.
   >    * Várias enumerações de seleção não são compatíveis com o Adobe Campaign.


* **MS Dynamics CRM** e **MS Dynamics Online**

   Consulte [esta seção](#example-for-microsoft-dynamics) para saber como configurar a conexão com o Microsoft Dynamics.

   Saiba mais sobre os casos de uso da integração do Adobe Campaign e do Microsoft Dynamics [neste vídeo](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html).

   >[!CAUTION]
   >
   >Ao conectar o Adobe Campaign com o Microsoft Dynamics, as limitações são:
   >
   >    
   >    
   >    * A instalação de plug-ins pode alterar o comportamento do CRM, o que pode levar a problemas de compatibilidade com o Adobe Campaign.
   >    * Várias enumerações de seleção não são compatíveis com o Adobe Campaign.


## Como configurar a conexão {#setting-up-the-connection}

Para usar os conectores CRM no Adobe Campaign, siga as etapas abaixo:

1. Crie a conta externa
1. Colete as tabelas do CRM
1. Sincronize as enumerações
1. Crie o workflow de sincronização

>[!NOTE]
>
>Os conectores CRM funcionam somente com uma URL segura (https).

### Exemplo para Salesforce.com {#example-for-salesforce-com}

Para configurar o conector do **Salesforce.com** com o Adobe Campaign, siga as etapas abaixo:

1. Crie uma nova conta externa através do nó **[!UICONTROL Administration > Platform > External accounts]** da árvore do Adobe Campaign.
1. Execute o assistente de configuração para gerar as tabelas de CRM disponíveis.

   ![](assets/crm_connectors_sfdc_wz.png)

   O assistente de configuração permite coletar tabelas e criar o schema correspondente.

   Clique em **[!UICONTROL Start]** para iniciar a execução.

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Para aprovar a configuração, você precisa fazer logoff e voltar ao console do Adobe Campaign.

1. Verifique o schema gerado no Adobe Campaign no nó **[!UICONTROL Administration > Configuration > Data schemas]**.

   ![](assets/crm_connectors_sfdc_table.png)

1. Após a criação do schema, você pode sincronizar enumerações automaticamente usando o CRM para o Adobe Campaign.

   Para fazer isso, clique no link **[!UICONTROL Synchronizing enumerations...]** e selecione a lista discriminada do Adobe Campaign que corresponde à lista discriminada do CRM.

   É possível substituir todos os valores de uma lista discriminada do Adobe Campaign pelos valores do CRM: para fazer isso, selecione **[!UICONTROL Yes]** na coluna **[!UICONTROL Replace]**.

   ![](assets/crm_connectors_sfdc_enum.png)

   Clique em **[!UICONTROL Next]** e depois em **[!UICONTROL Start]** para começar a importar a lista.

1. Verifique os valores importados no menu **[!UICONTROL Administration > Platform > Enumerations]**.

   ![](assets/crm_connectors_sfdc_exe.png)

1. Para importar dados do Salesforce ou exportar dados do Adobe Campaign para o Salesforce, você precisa criar um fluxo de trabalho e usar a atividade **[!UICONTROL CRM connector]**.

   ![](assets/crm_connectors_sfdc_wf.png)

### Exemplo para Oracle On Demand {#example-for-oracle-on-demand}

Para configurar o conector **Oracle On Demand** para trabalhar com o Adobe Campaign, siga as etapas abaixo:

1. Crie uma nova conta externa através do nó **[!UICONTROL Administration > Platform > External accounts]** da árvore do Adobe Campaign.

   ![](assets/crm_connectors_ood_1.png)

1. Abra o assistente de configuração: o Adobe Campaign mostra automaticamente as tabelas do modelo de dados Oracle. Selecione as tabelas que deseja coletar.

   ![](assets/crm_connectors_ood_2.png)

1. Clique em **[!UICONTROL Next]** para começar a criar o schema correspondente.

   O schema de dados correspondente se torna disponível no Adobe Campaign.

   ![](assets/crm_connectors_ood_3.png)

1. Inicie a sincronização de enumerações entre o Adobe Campaign e o Oracle On Demand.

   ![](assets/crm_connectors_ood_4.png)

1. Para importar dados do Oracle On Demand para o Adobe Campaign, crie o seguinte tipo de workflow:

   ![](assets/crm_connectors_ood_5.png)

   Esse workflow importa contatos por meio do Oracle On Demand, sincroniza com os dados existentes do Adobe Campaign, exclui os contatos duplicados e atualiza o banco de dados do Adobe Campaign.

   A atividade **[!UICONTROL CRM Connector]** precisa ser configurada como mostrado aqui:

   ![](assets/crm_connectors_ood_6.png)

1. Para exportar dados do Adobe Campaign para o Oracle On Demand, crie o seguinte workflow:

   ![](assets/crm_connectors_ood_7.png)

   Esse workflow coleta os dados relevantes usando queries, e depois os exporta para a tabela de contatos do Oracle On Demand.

### Exemplo do Microsoft Dynamics {#example-for-microsoft-dynamics}

Para configurar o conector do Microsoft Dynamics para trabalhar com o Adobe Campaign, siga as etapas abaixo:

1. Crie uma nova conta externa através do nó **[!UICONTROL Administration > Platform > External accounts]** da árvore do Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_01_4.png)

1. Selecione **Deployment type**: **[!UICONTROL On-premise]**, **[!UICONTROL Office 365]** ou **[!UICONTROL Web API]** dependendo do conector que você deseja configurar.

   O Adobe Campaign Classic oferece suporte à interface REST do Dynamics 365 com protocolo OAuth para autenticação.

   Se você selecionar uma implantação **[!UICONTROL WebAPI]**, precisará registrar um aplicativo no diretório do Azure e obter a **clientId** do diretório do Azure. Esse registro é detalhado [nesta página](https://msdn.microsoft.com/en-us/library/mt622431.aspx).

   >[!NOTE]
   >
   >O parâmetro redirectURL não é exigido pelo Adobe Campaign Classic.

   O valor **clientId** é usado com o nome de usuário/senha para buscar o token portador usando a senha de tipo concessão. Isso é chamado de **Resource Owner Password Credentials Grant**. Para obter mais informações, consulte [esta página](https://blogs.msdn.microsoft.com/wushuai/2016/09/25/resource-owner-password-credentials-grant-in-azure-ad-oauth/).

   ![](assets/crm_connectors_msdynamics_01_3.png)

   Para obter mais informações sobre compatibilidade de versões do CRM, consulte a [Matriz de Compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html).

1. Abra o assistente de configuração. O Adobe Campaign detecta automaticamente as tabelas do template de dados do Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Selecione as tabelas a serem recuperadas.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Clique em **[!UICONTROL Next]** e comece a criar o schema correspondente.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Para aprovar a configuração, você deve se desconectar/reconectar ao console do Adobe Campaign.

   O schema de dados correspondente se torna disponível no Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Inicie a sincronização de enumerações entre o Adobe Campaign e o Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

1. Para importar os dados do Microsoft Dynamics para o Adobe Campaign, crie o seguinte tipo de workflow:

   ![](assets/crm_connectors_msdynamics_07.png)

   Esse workflow importa contatos por meio do Microsoft Dynamics, sincroniza com os dados existentes do Adobe Campaign, exclui os contatos duplicados e atualiza o banco de dados do Adobe Campaign.

   A atividade **[!UICONTROL CRM Connector]** precisa ser configurada conforme abaixo:

   ![](assets/crm_connectors_msdynamics_08.png)

## Sincronização de dados {#data-synchronization}

A sincronização entre o Adobe Campaign e o CRM é realizada por meio de uma atividade dedicada de fluxo de trabalho: [CRM connector](../../workflow/using/crm-connector.md).

Essa atividade permite:

* Importar do CRM (consulte [Importar do CRM](#importing-from-the-crm)),
* Exportar para o CRM (consulte [Exportar para o CRM](#exporting-to-the-crm)),
* Importar objetos excluídos no CRM (consulte [Importar objetos excluídos no CRM](#importing-objects-deleted-in-the-crm)),
* Excluir objetos no CRM (consulte [Excluir objetos no CRM](#deleting-objects-in-the-crm)).

![](assets/crm_task_select_op.png)

Selecione a conta externa que corresponde ao CRM que você deseja configurar a sincronização, e depois selecione o objeto a ser sincronizado (contas, oportunidades, clientes potencias, contatos, etc.).

![](assets/crm_task_select_obj.png)

A configuração dessa atividade depende do processo a ser executado. Várias configurações são detalhadas abaixo.

### Importação do CRM {#importing-from-the-crm}

Para importar dados através do CRM no Adobe Campaign, você precisa criar o seguinte tipo de workflow:

![](assets/crm_wf_import.png)

Para uma atividade de importação, as etapas de configuração da atividade do **Conector CRM** são:

1. Selecione uma operação **[!UICONTROL Import from the CRM]**.
1. Vá até a lista suspensa **[!UICONTROL Remote object]** e selecione o objeto relacionado ao processo. Esse objeto coincide com uma das tabelas criadas no Adobe Campaign durante a configuração do conector.
1. Vá até a seção **[!UICONTROL Remote fields]** e insira os campos que serão importados.

   Para adicionar um campo, clique no botão **[!UICONTROL Add]** na barra de ferramentas e, em seguida, clique no ícone **[!UICONTROL Edit expression]**.

   ![](assets/crm_task_import_add_field.png)

   Se necessário, altere o formato dos dados através da lista suspensa das colunas **[!UICONTROL Conversion]**. Os possíveis tipos de conversão são detalhados em [Formato dos dados](#data-format).

   >[!CAUTION]
   >
   >O identificador do registro no CRM é obrigatório para vincular objetos no CRM e no Adobe Campaign. Ele é adicionado automaticamente quando a caixa é aprovada.
   >
   >A última data de modificação no lado do CRM também é obrigatória para importações de dados incrementais.

1. Você também pode filtrar os dados a serem importados com base nas suas necessidades. Para fazer isso, clique em **[!UICONTROL Edit the filter...]**.

   No exemplo a seguir, o Adobe Campaign só importará contatos nos quais algumas atividades foram registradas desde 1º de novembro de 2012.

   ![](assets/crm_task_import_filter.png)

   >[!CAUTION]
   >
   >As limitações vinculadas aos modos do filtro de dados são detalhadas em [Filtros de dados](#filtering-data).

1. A opção **[!UICONTROL Use automatic index...]** permite gerenciar automaticamente a sincronização de objetos incrementais entre o CRM e o Adobe Campaign, dependendo da data e da última modificação.

   Para obter mais informações, consulte [Gerenciamento de variáveis](#variable-management).

#### Gerenciamento de variáveis {#variable-management}

Habilitar a opção **[!UICONTROL Automatic index]** permite coletar apenas objetos modificados desde a última importação.

![](assets/crm_task_import_option.png)

A data da última sincronização é armazenada em uma opção especificada na janela de configuração, por padrão: **LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**.

>[!NOTE]
>
>Essa nota se aplica somente à atividade genérica **[!UICONTROL CRM Connector]**. Para outras atividades do CRM, o processo é automático.
>
>Essa opção deve ser criada e preenchida manualmente em **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Deve ser uma opção de texto e seu valor precisa corresponder ao seguinte formato: **aaaa/MM/dd hh:mm:ss**.
> 
>Você precisa atualizar essa opção manualmente para qualquer outra importação.

É possível especificar o campo do CRM remoto que será levado em consideração para identificar as alterações mais recentes.

Por padrão, os seguintes campos são usados (na ordem especificada):

* Para o Microsoft Dynamics: **modifiedon**,
* Para o Oracle On Demand: **LastUpdates**, **ModifiedDate**, **LastLoggedIn**,
* Para o Salesforce.com: **LastModifiedDate**, **SystemModamp**.

A ativação da opção **[!UICONTROL Automatic index]** gera três variáveis que podem ser usadas no fluxo de trabalho de sincronização por meio de uma atividade do tipo **[!UICONTROL JavaScript code]**. Essas atividades são:

* **vars.crmOptionName**: representa o nome da opção que contém a data de última importação.
* **vars.crmStartImport**: representa a data de início (incluída) da última recuperação de dados.
* **vars.crmEndDate**: representa a data final (excluída) da última recuperação de dados.

   >[!NOTE]
   >
   >Essas datas são mostradas no seguinte formato: **aaaa/MM/dd hh:mm:ss**.

#### Filtrar dados {#filtering-data}

Para garantir uma operação eficiente com os vários CRMs, os filtros precisam ser criados com as seguintes regras:

* Cada nível de filtragem só pode usar um tipo de operador.
* O operador AND NOT não é suportado.
* Comparações podem dizer respeito somente a valores nulos (tipo &quot;está vazio&quot;/&quot;não está vazio&quot;) ou números. Isso significa que o valor (coluna à direita) é avaliado e o resultado dessa avaliação deve ser um número. Portanto, as comparações do tipo JOIN não são compatíveis.
* O valor contido na coluna à direita é avaliado em JavaScript.
* Não há suporte para comparações JOIN.
* A expressão na coluna à esquerda deve ser um campo. Ele não pode ser uma combinação de várias expressões, um número, etc.

Por exemplo, as condições de filtragem a seguir NÃO serão válidas para uma importação de CRM, pois o operador OR é colocado no mesmo nível que os operadores AND:

* O operador OR é colocado no mesmo nível que os operadores AND
* As comparações são realizadas em cadeias de texto.

![](assets/crm_import_wrong_filter.png)

#### Ordenar por {#order-by}

No Microsoft Dynamics e no Salesforce.com, você pode classificar os campos remotos a serem importados em ordem crescente ou decrescente.

Para fazer isso, clique no link **[!UICONTROL Order by]** e adicione as colunas à lista.

A ordem das colunas na lista é a ordem de classificação:

![](assets/crm_import_order.png)

#### Identificação de registro {#record-identification}

Em vez de importar elementos incluídos (e possivelmente filtrados) no CRM, você pode usar uma população calculada anteriormente no workflow.

Para fazer isso, selecione a opção **[!UICONTROL Use the population calculated upstream]** e especifique o campo que contém o identificador remoto.

Em seguida, selecione os campos da população de entrada que deseja importar, conforme mostrado abaixo:

![](assets/crm_wf_import_calculated_population.png)

### Como exportar para o CRM {#exporting-to-the-crm}

A exportação de dados do Adobe Campaign para o CRM permite copiar todo o conteúdo para um banco de dados do CRM.

Para exportar dados para o CRM, você precisa criar o seguinte tipo de workflow:

![](assets/crm_export_diagram.png)

Para uma exportação, aplique a seguinte configuração à atividade do **Conector CRM** :

1. Selecione uma operação **[!UICONTROL Export to CRM]**.
1. Vá até a lista suspensa **[!UICONTROL Remote object]** e selecione o objeto relacionado ao processo. Esse objeto coincide com uma das tabelas criadas no Adobe Campaign durante a configuração do conector.

   >[!CAUTION]
   >
   >A função de exportação da atividade **Conectores CRM** pode inserir ou atualizar campos no lado do CRM. Para habilitar atualizações de campo no CRM, você precisa especificar a chave primária da tabela remota. Se a chave estiver faltando, os dados serão inseridos (ao invés de serem atualizados).

1. Na seção **[!UICONTROL Mapping]**, especifique os campos que serão exportados e o mapeamento no CRM.

   ![](assets/crm_export_config.png)

   Para adicionar um campo, clique no botão **[!UICONTROL Add]** na barra de ferramentas e, em seguida, clique no ícone **[!UICONTROL Edit expression]**.

   >[!NOTE]
   >
   >Para determinado campo, se nenhuma correspondência for definida no lado do CRM, os valores não poderão ser atualizados: eles são inseridos diretamente no CRM.

   Se necessário, altere o formato dos dados através da lista suspensa das colunas **[!UICONTROL Conversion]**. Os possíveis tipos de conversão são detalhados em [Formato dos dados](#data-format).

   >[!NOTE]
   >
   >A lista de registros a serem exportados e o resultado da exportação são salvas em um arquivo temporário que permanece acessível até que o workflow seja concluído ou reiniciado. Isso permite que você inicie o processo novamente em caso de erro, sem correr o risco de exportar o mesmo registro várias vezes ou perder dados.

### Configurações adicionais {#additional-configurations}

#### Formato dos dados {#data-format}

É possível converter o formato dos dados de forma instantânea ao importá-los para o CRM.

Para fazer isso, selecione a conversão a ser aplicada na coluna correspondente.

![](assets/crm_task_import.png)

O modo **[!UICONTROL Default]** aplica conversão automática de dados, que na maioria dos casos é igual a copiar/colar os dados. No entanto, o gerenciamento de fuso horário é aplicado.

Outras conversões possíveis são:

* **[!UICONTROL Date only]**: esse modo exclui os campos do tipo Data + Hora.
* **[!UICONTROL Without time offset]**: esse modo cancela o gerenciamento de fuso horário aplicado no modo padrão.
* **[!UICONTROL Copy/Paste]**: esse modo usa dados brutos como cadeias de caracteres (sem conversão).

#### Processamento de erros {#error-processing}

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

A transição **[!UICONTROL Reject]** de saída permite que você acesse o schema de saída que contém as colunas específicas relevantes para mensagens e códigos de erro. Essas colunas são:

* Para o Oracle On Demand: **errorLogFilename** (nome do arquivo de log no lado do Oracle), **errorCode** (código de erro), **errorSymbol** (símbolo de erro, diferente de código de erro), **errorMessage** (descrição do contexto do erro).
* Para o Salesforce.com: **errorSymbol** (símbolo de erro, diferente do código de erro), **errorMessage** (descrição do contexto de erro).

### Importação de objetos excluídos no CRM {#importing-objects-deleted-in-the-crm}

Para habilitar a configuração de um processo extenso de sincronização de dados, você pode importar objetos excluídos do CRM para o Adobe Campaign.

Para fazer isso, siga as etapas abaixo:

1. Selecione uma operação **[!UICONTROL Import objects deleted in the CRM]**.
1. Vá até a lista suspensa **[!UICONTROL Remote object]** e selecione o objeto relacionado ao processo. Esse objeto coincide com uma das tabelas criadas no Adobe Campaign durante a configuração do conector.
1. Especifique o período de exclusão que será considerado nos campos **[!UICONTROL Start date]** e **[!UICONTROL End date]**. Essas datas serão incluídas no período.

   ![](assets/crm_import_deleted_obj.png)

   >[!CAUTION]
   >
   >O período de exclusão do elemento deve coincidir com as limitações específicas do CRM. Isso significa que para o Salesforce.com, por exemplo, elementos excluídos há mais de 30 dias não podem ser recuperados.

### Exclusão de objetos no CRM {#deleting-objects-in-the-crm}

Para excluir objetos no lado do CRM, você precisa especificar a chave primária dos elementos remotos a serem excluídos.

![](assets/crm_delete_in_crm.png)

A guia **[!UICONTROL Behavior]** permite habilitar o processamento de rejeições. Essa opção gera uma segunda transição de saída para a atividade **[!UICONTROL CRM connector]**. Para obter mais informações, consulte [Processamento de erros](#error-processing).

>[!NOTE]
>
>Mesmo quando a opção **[!UICONTROL Process rejects]** está desabilitada, um aviso é gerado para cada coluna rejeitada.

