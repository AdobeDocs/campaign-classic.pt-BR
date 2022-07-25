---
product: campaign
title: Carregamento de dados (arquivo)
description: Saiba mais sobre a atividade de workflow de carregamento de dados (arquivo)
feature: Workflows, Data Management Activity
exl-id: a380e486-a40c-4bf6-b7f4-7dcd76c34085
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '1052'
ht-degree: 100%

---

# Carregamento de dados (arquivo){#data-loading-file}

![](../../assets/v7-only.svg)

## Uso {#use}

A atividade **[!UICONTROL Data loading (File)]** permite acessar uma fonte de dados externos diretamente e usá-la no Adobe Campaign. De fato, todos os dados necessários para operações de target nem sempre são encontrados no banco de dados do Adobe Campaign: ele pode ser disponibilizado em arquivos externos.

O arquivo a ser carregado pode ser especificado pela transição ou calculado durante a execução dessa atividade. Por exemplo, pode ser a lista de 10 produtos favoritos de um cliente cujas compras são gerenciadas em um banco de dados externo.

A seção superior da janela de configuração dessa atividade permite definir o formato de arquivo. Para fazer isso, use um arquivo de exemplo com o mesmo formato do arquivo a ser importado. Este arquivo pode ser armazenado no local ou no servidor.

>[!CAUTION]
>
>Somente os arquivos de estrutura simples são suportados (por exemplo, CSV, TXT e etc.). Não é recomendável usar o formato XML.

![](assets/s_advuser_wf_etl_file.png)

Você pode definir um pré-processamento a ser executado durante a importação do arquivo, por exemplo, para não precisar descompactar o arquivo no servidor (e, portanto, economizar espaço para o arquivo descompactado), e incluir a descompactação no processamento de arquivo. Selecione a opção **[!UICONTROL Pre-process the file]** e escolha uma das três opções: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) ou **[!UICONTROL Decrypt]** (gpg).

![](assets/preprocessing-dataloading.png)

Para mais informações, consulte esta seção: [Descompactar ou descriptografar um arquivo antes do processamento](../../platform/using/unzip-decrypt.md).

## Definição do formato de arquivo {#defining-the-file-format}

Quando você carrega um arquivo, o formato da coluna é automaticamente detectado com os parâmetros padrão para cada tipo de dados. Você pode modificar esses parâmetros padrão para especificar os processos específicos a serem aplicados aos seus dados, principalmente quando há um erro ou um valor vazio.

Para fazer isso, selecione **[!UICONTROL Click here to change the file format...]** na janela principal da atividade **[!UICONTROL Data loading (file)]**. A janela de detalhes do formato será aberta.

![](assets/file_loading_columns_format.png)

Em seguida, você pode modificar a formatação geral do arquivo, bem como a formatação de cada coluna.

A formatação geral do arquivo permite definir a maneira como as colunas serão reconhecidas (codificação do arquivo, separadores usados, etc.).

A formatação de coluna permite definir o processamento de valor de cada coluna:

* **[!UICONTROL Ignore column]**: não processa essa coluna durante o carregamento de dados.
* **[!UICONTROL Data type]**: especifica o tipo de dados esperado para cada coluna.
* **[!UICONTROL Allow NULLs]**: especifica como gerenciar valores vazios.

   * **[!UICONTROL Adobe Campaign default]**: gera um erro apenas para os campos numéricos, caso contrário, insere um valor NULL.
   * **[!UICONTROL Empty value allowed]**: autoriza valores vazios. O valor NULL é então inserido.
   * **[!UICONTROL Always populated]**: gera um erro se um valor estiver vazio.

* **[!UICONTROL Length]**: especifica o número máximo de caracteres para o tipo de dados da **cadeia de caracteres**.
* **[!UICONTROL Format]**: define o formato de data e hora.
* **[!UICONTROL Data transformation]**: define se um processo de ocorrência de caractere precisa ser aplicado em uma **cadeia de caracteres**.

   * **[!UICONTROL None]**: a cadeia de caracteres importada não é modificada.
   * **[!UICONTROL First letter in upper case]**: a primeira letra de cada palavra da cadeia de caracteres começa com maiúscula.
   * **[!UICONTROL Upper case]**: todos os caracteres na cadeia de caracteres estão em maiúsculas.
   * **[!UICONTROL Lower case]**: todos os caracteres na cadeia de caracteres estão em minúsculas.

* **[!UICONTROL White space management]**: especifica se determinados espaços precisam ser ignorados em uma cadeia de caracteres. O valor **[!UICONTROL Ignore spaces]** permite somente espaços no início e no final de uma cadeia de caracteres a ser ignorada.
* **[!UICONTROL Error processings]**: define o comportamento se um erro for encontrado.

   * **[!UICONTROL Ignore the value]**: o valor é ignorado. Um aviso é gerado no log de execução do fluxo de trabalho.
   * **[!UICONTROL Reject line]**: a linha inteira não é processada.
   * **[!UICONTROL Use a default value in case of error]**: substitui o valor que causa o erro por um valor padrão, definido no campo **[!UICONTROL Default value]**.
   * **[!UICONTROL Reject the line when there is no remapping value]**: a linha inteira só será processada se um tiver sido definido para o valor errado (consulte a opção **[!UICONTROL Mapping]** Mapping abaixo).
   * **[!UICONTROL Use a default value in case the value is not remapped]**: substitui o valor que causa o erro por um valor padrão, definido no campo **[!UICONTROL Default value]**, a menos que um tenha sido definido para o valor incorreto (consulte a opção **[!UICONTROL Mapping]** Mapping abaixo).

* **[!UICONTROL Default value]**: especifica o valor padrão de acordo com o processamento de erros escolhido.
* **[!UICONTROL Mapping]**: esse campo está disponível apenas na configuração de detalhe da coluna (acessada por um clique duplo ou através das opções à direita da lista de colunas). Isso transforma determinados valores ao serem importados. Por exemplo, você pode transformar &quot;três&quot; em &quot;3&quot;.

## Exemplo: coleta de dados e seu carregamento no banco de dados {#example--collecting-data-and-loading-it-in-the-database}

O exemplo a seguir permite coletar um arquivo no servidor todos os dias, carregar seu conteúdo e atualizar os dados no banco de dados, dependendo das informações que ele contém. O arquivo a ser coletado contém informações sobre clientes que podem ter comprado (cerca de 3.000 euros), pediram reembolso em uma compra ou visitaram a loja sem adquirir nada. Dependendo dessas informações, vários processos serão aplicados ao seu perfil no banco de dados.

![](assets/s_advuser_load_file_sample_0.png)

1. O coletor de arquivos permite recuperar arquivos armazenados em um diretório, dependendo da frequência fornecida.

   A guia **[!UICONTROL Directory]** contém informações sobre os arquivos a serem recuperados. Em nosso exemplo, todos os arquivos no formato de texto cujos nomes contêm a palavra &#39;clientes&#39; e que são armazenados no diretório tmp/Adobe/Data/files do servidor serão recuperados.

   O uso de **[!UICONTROL File collector]** é detalhado na seção [File collector](file-collector.md).

   ![](assets/s_advuser_load_file_sample_1.png)

   A guia **[!UICONTROL Schedule]** permite agendar a execução do coletor, ou seja, especificar a frequência com que a presença desses arquivos será verificada.

   Aqui, queremos acionar o coletor todo dia útil às 9:00 PM.

   ![](assets/s_advuser_load_file_sample_2.png)

   Para fazer isso, clique no botão **[!UICONTROL Change...]** localizado na seção inferior direita da ferramenta de edição e configure a programação.

   Para obter mais informações, consulte [Scheduler](scheduler.md).

1. Em seguida, configure a atividade de carregamento de dados (arquivo) para indicar como os arquivos coletados devem ser lidos. Para fazer isso, selecione um arquivo de exemplo com a mesma estrutura dos arquivos a serem carregados.

   ![](assets/s_advuser_load_file_sample_3.png)

   Aqui, o arquivo contém cinco colunas:

   * a primeira coluna contém um código que coincide com o evento: compra (cerca de 3.000 euros), nenhuma compra ou reembolso em uma ou mais compras.
   * as quatro colunas seguintes contêm o nome, sobrenome, email e número da conta do cliente.

   A configuração de formato do arquivo a ser carregado coincide com aquela definida durante uma importação de dados no Adobe Campaign. Para obter mais informações, consulte esta [seção](../../platform/using/executing-import-jobs.md#step-2---source-file-selection).

1. Na atividade de Split, especifique os subconjuntos a serem criados, de acordo com o valor da coluna **Evento**.

   A atividade de Split é detalhada na seção.

   ![](assets/s_advuser_load_file_sample_4.png)

   Para cada subconjunto, especifique um dos valores na coluna **Evento**.

   ![](assets/s_advuser_load_file_sample_5.png)

   A atividade **[!UICONTROL Split]** conterá as seguintes informações:

   ![](assets/s_advuser_load_file_sample_6.png)

1. Então especifique os processos a serem executados para cada tipo de público. No nosso exemplo, vamos **[!UICONTROL Update the data]** no banco de dados. Para fazer isso, posicione uma atividade **[!UICONTROL Update data]** no final de cada transição de saída da atividade Split.

   A atividade **[!UICONTROL Update data]** está detalhada na seção [Update data](update-data.md).
