---
product: campaign
title: Ações em relatórios
description: Ações em relatórios
feature: Reporting, Monitoring
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
TQID: https://experienceleague.adobe.com/ds9tKPie-3bcx7H-4tyN2Naq4SgX1ZXJavXvMTYVu8A
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: c309ee4e-82e4-4f7e-b608-ef345678c34e
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47id: cfda811a-e413-43a4-adf0-7370888f5cfcid: afe938ea-bc18-44a4-a3fb-03e1031466cb
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 554
ht-degree: 100%

---

# Ações em relatórios{#actions-on-reports}



Quando estiver exibindo um relatório, a barra de ferramentas permite executar determinado número de ações. Veja os detalhes abaixo.

![](assets/s_ncs_advuser_report_wizard_2.png)

A barra de ferramentas permite exportar, imprimir, arquivar ou exibir o relatório em um navegador da Web por exemplo.

![](assets/s_ncs_advuser_report_wizard_04.png)

## Exportar um relatório {#exporting-a-report}

Selecione o formato que deseja usar para exportar a partir da lista suspensa. (.xls, .pdf ou .ods).

![](assets/s_ncs_advuser_report_wizard_06.png)

Quando um relatório contém várias páginas, é preciso repetir a operação para cada página.

É possível configurar o relatório na exibição do formato PDF, Excel ou OpenOffice. Abra o explorer do Adobe Campaign e selecione o relatório em questão.

Acesse as opções de exportação por meio das atividades **[!UICONTROL Page]** do relatório, na guia **[!UICONTROL Advanced]**.

Altere as configurações de **[!UICONTROL Paper]** e **[!UICONTROL Margins]** para atender às suas necessidades. Também é possível autorizar a exportação de uma página somente em formato PDF. Para fazer isso, desmarque a opção **[!UICONTROL Activate OpenOffice/Microsoft Excel export]**.

![](assets/s_ncs_advuser_report_wizard_021.png)

### Exportar para o Microsoft Excel {#exporting-into-microsoft-excel}

Para relatórios do tipo **[!UICONTROL List with group]** destinados a serem exportados para o Excel, as seguintes recomendações e limitações se aplicam:

* Esses relatórios não devem conter linhas vazias.

  ![](assets/export_limitations_remove_empty_line.png)

* A legenda da lista deve estar oculta.

  ![](assets/export_limitations_hide_label.png)

* Os relatórios não precisam usar formatação específica definida no nível da célula. É preferível usar **[!UICONTROL Form rendering]** para definir o formato das células na tabela. O **[!UICONTROL Form rendering]** pode ser acessado via **[!UICONTROL Administration > Configuration > Form rendering]**.
* Não é recomendável inserir conteúdo HTML.
* Se um relatório contiver vários elementos de tabela, gráfico, etc., eles serão exportados um abaixo do outro.
* É possível forçar a quebra de linhas nas células: essa configuração será mantida no Excel. Para obter mais informações, consulte [esta seção](../../reporting/using/creating-a-table.md#defining-cell-format).

### Adiar a exportação {#postpone-the-export}

É possível adiar a exportação de um relatório, por exemplo, para aguardar chamadas assíncronas. Para fazer isso, digite o seguinte parâmetro no script de inicialização da página:

```
document.nl_waitBeforeRender = true;
```

Para ativar a exportação e começar a converter em um PDF, use a função **document.nl_renderToPdf()** sem nenhum parâmetro.

### Alocação de memória {#memory-allocation}

Ao exportar determinados relatórios grandes, erros de alocação de memória podem ocorrer.

Em determinadas instâncias, o valor padrão **maxMB** (**SKMS** para instâncias hospedadas) do JavaScript indicado no arquivo de configuração **serverConf.xml** é definido como 64 MB. Se encontrar erros de memória insuficiente ao exportar um relatório, talvez seja recomendado aumentar esse número para 512 MB:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

Para aplicar alterações feitas na configuração, o serviço **nlserver** precisa ser reiniciado.

Para saber mais sobre o arquivo **serverConf.xml**, consulte [esta seção](../../production/using/configuration-principle.md).

Para saber mais sobre o serviço **nlserver**, consulte [esta seção](../../production/using/administration.md).

## Imprimir um relatório {#printing-a-report}

É possível imprimir seu relatório: para fazer isso, clique no ícone da impressora: isso abre a caixa de diálogo.

Para obter um resultado melhor, edite as opções de impressão do Explorer e selecione **[!UICONTROL Print background colors and images]**.

![](assets/s_ncs_advuser_report_print_options.png)

## Criar arquivos de relatórios {#creating-report-archives}

O arquivamento de um relatório permite criar um modo de exibição do relatório em vários períodos, por exemplo, para mostrar as estatísticas de determinado período.

Para criar um arquivo, abra o relatório indicado e clique no ícone apropriado.

![](assets/s_ncs_advuser_report_wizard_07.png)

Para exibir ou ocultar arquivos existentes, clique no ícone show/hide.

![](assets/s_ncs_advuser_report_history_06.png)

As datas de arquivamento são exibidas sob o ícone show/hide. Clique no arquivo para exibi-lo.

![](assets/s_ncs_advuser_report_history_04.png)

É possível excluir um arquivo de relatórios. Para fazer isso, vá para o nó do Adobe Campaign onde seus relatórios estão armazenados. Clique na guia **[!UICONTROL Archives]**, selecione aquele que desejar excluir e clique em **[!UICONTROL Delete]**.

![](assets/s_ncs_advuser_report_history_01.png)
