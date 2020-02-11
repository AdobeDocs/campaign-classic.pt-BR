---
title: Trabalho com pacotes de dados
seo-title: Trabalho com pacotes de dados
description: Trabalho com pacotes de dados
seo-description: null
page-status-flag: never-activated
uuid: 867b2702-dbc4-4b71-a385-a2c7fd09d25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: 42867665-d0ca-486e-9110-91716c0d5c57
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Trabalho com pacotes de dados{#working-with-data-packages}

## Sobre pacotes de dados {#about-data-packages}

O Adobe Campaign permite exportar ou importar a configuração e os dados da plataforma por meio de um sistema de pacotes. Os pacotes podem conter diferentes tipos de configurações, elementos, filtrados ou não.

Os pacotes de dados permitem que entidades do banco de dados do Adobe Campaign sejam exibidas por meio de arquivos no formato XML. Cada entidade contida em um pacote é representada com todos os seus dados.

O princípio de **pacotes de dados** é exportar uma configuração de dados e integrá-la a outro sistema do Adobe Campaign. Para obter mais informações sobre como manter um conjunto consistente de pacotes de dados, consulte [technote](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_How_to_maintain_a_consistent_set_of_data_packages.pdf).

### Tipos de pacotes {#types-of-packages}

Há três tipos de pacotes exportáveis: pacotes de usuário, pacotes de plataforma e pacotes de administrador.

* **Pacote do usuário**: permite que você selecione a lista de entidades a serem exportadas. Esse tipo de pacote gerencia dependências e verifica erros.
* **Pacote de plataforma**: inclui todos os recursos técnicos adicionados (não padrão): schemas, código JavaScript, etc.

   ![](assets/ncs_datapackage_package_platform.png)

* **Pacote de administrador**: inclui todos os templates e objetos comerciais adicionados (não padrão): templates, bibliotecas, etc.

   ![](assets/ncs_datapackage_package_admin.png)

>[!CAUTION]
>
>Os tipos **plataforma** e **administrador** contêm uma lista predefinida de entidades a serem exportadas. Cada entidade está vinculada às condições de filtragem que permitem remover os recursos prontos para uso do pacote criado.

## Estrutura de dados {#data-structure}

A descrição de um pacote de dados é um documento XML estruturado que está de acordo com a gramática do schema de dados **xrk:navtree**.

Exemplo de pacote de dados:

```
<package>
  <entities schema="nms:recipient">
    <recipient email="john.smith@adobe.com" lastName="Smith" firstName="John">      
      <folder _operation="none" name="nmsRootFolder"/>      
      <company _operation="none" name="Adobe"/>
    </recipient>
  </entities>
  <entities schema="sfa:company">
    <company name="Adobe">
      location city="London" zipCode="W11 2BQ"/>
    </company>
  </entities>
</package>
```

The XML document must begin and end with the **`<package>`** element. Any **`<entities>`** elements that follow distribute the data by document type.

An **`<entities>`** element contains the data of the package in the format of the data schema entered in the **schema** attribute.

Os dados em um pacote não devem conter chaves internas incompatíveis entre as bases, como chaves geradas automaticamente (opção **autopk**).

No nosso exemplo, as associações nos links &quot;pasta&quot; e &quot;empresa&quot; foram substituídas por teclas de &quot;alto nível&quot; nas tabelas de destino:

```
<recipient>
  <folder _operation="none" name="nmsRootFolder"/>
  <company _operation="none" name="Adobe"/>
</recipient>
```

The **`operation`** attribute with the value &quot;none&quot; defines a reconciliation link.

Um pacote de dados pode ser construído manualmente a partir de qualquer editor de texto. Basta garantir que a estrutura do documento XML esteja em conformidade com o schema de dados &quot;xtk:navtree&quot;. O console do Adobe Campaign tem um módulo de importação e exportação de pacotes de dados.

## Exportação de pacotes {#exporting-packages}

### Sobre a exportação de pacotes {#about-package-export}

Os pacotes podem ser exportados de três formas diferentes:

* The **[!UICONTROL Package Export Wizard]** enables you to export a set of objects in a single package. Para obter mais informações, consulte [Exportar um conjunto de objetos em um pacote](#exporting-a-set-of-objects-in-a-package)
* A **single object** can be exported in a package directly by right-clicking on it and selecting **[!UICONTROL Actions > Export in a package]**.
* As **definições de pacote** permitem criar uma estrutura de pacote na qual você adiciona objetos que serão exportados posteriormente em um pacote. Para obter mais informações, consulte [Gerenciamento de definições de pacotes](#managing-package-definitions)

Após a exportação, é possível importar o pacote e todas as entidades adicionadas para outra instância do Campaign.

### Exportação de um conjunto de objetos em um pacote {#exporting-a-set-of-objects-in-a-package}

The package export wizard is accessible via the **[!UICONTROL Tools > Advanced > Export package...]** menu of the Adobe Campaign client console.

![](assets/ncs_datapackage_typepackage.png)

Para os três tipos de pacotes, o assistente oferece as seguintes etapas:

1. Listar as entidades a serem exportadas por tipo de documento:

   ![](assets/ncs_datapackage_export2.png)

   >[!CAUTION]
   >
   >Se você exportar uma pasta **[!UICONTROL Offer category]**, **[!UICONTROL Offer environment]** ou **[!UICONTROL Program]** digitar, nunca selecione a pasta **[!UICONTROL Plan]** xtk: **** xtk, pois pode perder alguns dados. Selecione a entidade que corresponde à pasta: **nms:offerCategory** para categorias de ofertas, **nms:offerEnv** para ambientes de ofertas, **nms:program** para programas e **nms:plan** para planos.

   O gerenciamento de listas permite adicionar ou excluir entidades para exportação da configuração. Click **[!UICONTROL Add]** to select a new entity.

   The **[!UICONTROL Detail]** button edits the selected configuration.

   >[!NOTE]
   >
   >O mecanismo de dependência controla a sequência de exportação da entidade. For more on this, refer to [Managing dependencies](#managing-dependencies).

1. A tela de configuração da entidade define o query de filtro no tipo de documento a ser extraído.

   Você deve configurar a cláusula de filtragem para extração de dados.

   ![](assets/ncs_datapackage_export4.png)

   >[!NOTE]
   >
   >O editor de query é apresentado [nesta seção](../../platform/using/about-queries-in-campaign.md).

1. Click **[!UICONTROL Next]** and select the sorting columns to order the data during extraction:

   ![](assets/ncs_datapackage_export5.png)

1. Pré-visualize os dados a serem extraídos antes de executar a exportação.

   ![](assets/ncs_datapackage_export6.png)

1. A última página do assistente de exportação de pacotes permite iniciar a exportação. The data will be stored in the file indicated in the **[!UICONTROL File]** field.

   ![](assets/ncs_datapackage_export7.png)

### Gerenciamento de dependências {#managing-dependencies}

O mecanismo de exportação permite que o Adobe Campaign rastreie os links entre os vários elementos exportados.

Esse mecanismo é definido por duas regras:

* objetos vinculados a um link com uma integridade do tipo **own** ou **owncopy** são exportados no mesmo pacote que o objeto exportado.
* objetos vinculados a um link com um tipo de integridade **neutral** ou **define** (link definido) devem ser exportados separadamente.

>[!NOTE]
>
>Os tipos de integridade vinculados a elementos do schema são definidos nesta [seção](../../configuration/using/database-mapping.md#links--relation-between-tables).

#### Exportação de uma campanha {#exporting-a-campaign}

Veja aqui um exemplo de como exportar uma campanha. A campanha de marketing a ser exportada contém uma tarefa (rótulo: &quot;MyTask&quot;) e um fluxo de trabalho (rótulo: &quot;CampaignWorkflow&quot;) em uma pasta &quot;MyWorkflow&quot; (nó: Fluxos de trabalho administrativos / de produção / técnicos / processos de campanha / MyWorkflow).

A tarefa e o workflow são exportados no mesmo pacote que a campanha desde que os schemas correspondentes sejam conectados por links com uma integridade do tipo &quot;own&quot;.

Conteúdo do pacote:

```
<?xml version='1.0'?>
<package author="Administrator (admin)" buildNumber="7974" buildVersion="6.1" img=""
label="" name="" namespace="" vendor="">
 <desc></desc>
 <version buildDate="2013-01-09 10:30:18.954Z"/>
 <entities schema="nms:operation">
  <operation duration="432000" end="2013-01-14" internalName="OP1" label="MyCampaign"
  modelName="opEmpty" start="2013-01-09">
   <controlGroup>
    <where filteringSchema=""/>
   </controlGroup>
   <seedList>
    <where filteringSchema="nms:seedMember"></where>
    <seedMember internalName="SDM1"></seedMember>
   </seedList>
   <parameter useAsset="1" useBudget="1" useControlGroup="1" useDeliveryOutline="1"
   useDocument="1" useFCPValidation="0" useSeedMember="1" useTask="1"
   useValidation="1" useWorkflow="1"></parameter>
   <fcpSeed>
    <where filteringSchema="nms:seedMember"></where>
   </fcpSeed>
   <owner _operation="none" name="admin" type="0"/>
   <program _operation="none" name="nmsOperations"/>
   <task end="2013-01-17 10:07:51.000Z" label="MyTask" name="TSK2" start="2013-01-16 10:07:51.000Z"
   status="1">
    <owner _operation="none" name="admin" type="0"/>
    <operation _operation="none" internalName="OP1"/>
    <folder _operation="none" name="nmsTask"/>
   </task>
   <workflow internalName="WKF12" label="CampaignWorkflow" modelName="newOpEmpty"
   order="8982" scenario-cs="Notification of the workflow supervisor (notifySupervisor)"
   schema="nms:recipient">
    <scenario internalName="notifySupervisor"/>
    <desc></desc>
    <folder _operation="none" name="Folder4"/>
    <operation _operation="none" internalName="OP1"/>
   </workflow>
  </operation>
 </entities>
</package>   
```

A afiliação a um tipo de pacote é definida em um schema com o atributo **@pkgAdmin e @pkgPlatform.** Esses atributos recebem uma expressão XTK que define as condições de afiliação ao pacote.

```
<element name="offerEnv" img="nms:offerEnv.png" 
template="xtk:folder" pkgAdmin="@id != 0">
```

Finalmente, o atributo **@pkgStatus** permite definir as regras de exportação para esses elementos ou atributos. Dependendo do valor do atributo, o elemento ou atributo será encontrado no pacote exportado. Os três valores possíveis para este atributo são:

* **never**: não exporta o campo ou link
* **always**: força a exportação deste campo
* **preCreate**: autoriza a criação da entidade vinculada

>[!NOTE]
>
>O valor **preCreate** é apenas admitido para eventos do tipo link. Ele autoriza criar ou apontar para uma entidade ainda não carregada no pacote exportado.

## Gerenciamento de definições de pacote {#managing-package-definitions}

### Sobre definições de pacote {#about-package-definitions}

As definições de pacote permitem criar uma estrutura de pacote na qual você adiciona entidades que serão exportadas posteriormente em um único pacote. É possível importar esse pacote e todas as entidades adicionadas para outra instância do Campaign.

**Tópicos relacionados:**

* [Criação de uma definição de pacote](#creating-a-package-definition)
* [Adição de entidades a uma definição de pacote](#adding-entities-to-a-package-definition)
* [Configuração da geração de definições de pacote](#configuring-package-definitions-generation)
* [Exportação de pacotes de uma definição de pacote](#exporting-packages-from-a-package-definition)

### Criação de uma definição de pacote {#creating-a-package-definition}

As definições do pacote podem ser acessadas no **[!UICONTROL Administration > Configuration > Package management > Package definitions]** menu.

To create a package definition, click the **[!UICONTROL New]** button, then fill in the package definition general information.

![](assets/packagedefinition_create.png)

Você pode então adicionar entidades à definição do pacote e exportá-lo para um pacote de arquivos XML.

**Tópicos relacionados:**

* [Adição de entidades a uma definição de pacote](#adding-entities-to-a-package-definition)
* [Configuração da geração de definições de pacote](#configuring-package-definitions-generation)
* [Exportação de pacotes de uma definição de pacote](#exporting-packages-from-a-package-definition)

### Adição de entidades a uma definição de pacote {#adding-entities-to-a-package-definition}

In the **[!UICONTROL Content]** tab, click the **[!UICONTROL Add]** button to select the entities to export with the package. Práticas recomendadas ao selecionar entidades são apresentadas na seção [Exportar um conjunto de objetos em um pacote](#exporting-a-set-of-objects-in-a-package) .

![](assets/packagedefinition_addentities.png)

As entidades podem ser adicionadas a uma definição de pacote diretamente da sua localização na instância. Para fazer isso, siga as etapas abaixo:

1. Clique com o botão direito do mouse na entidade desejada e selecione **[!UICONTROL Actions > Export in a package]**.

   ![](assets/packagedefinition_singleentity.png)

1. Select **[!UICONTROL Add to a package definition]**, then select the package definition to which you want to add the entity.

   ![](assets/packagedefinition_packageselection.png)

1. A entidade é adicionada à definição do pacote e será exportada com o pacote (consulte [Exportar pacotes de uma definição](#exporting-packages-from-a-package-definition)de pacote).

   ![](assets/packagedefinition_entityadded.png)

### Configuração da geração de definições de pacote {#configuring-package-definitions-generation}

Package generation can be configured from the package definition **[!UICONTROL Content]** tab. To do this, click the **[!UICONTROL Generation parameters]** link.

![](assets/packagedefinition_generationparameters.png)

* **[!UICONTROL Include the definition]**: inclui a definição usada atualmente na definição do pacote.
* **[!UICONTROL Include an installation script]**: permite que você adicione um script javascript para execução na importação do pacote. When selected, a **[!UICONTROL Script]** tab is added in the package definition screen.
* **[!UICONTROL Include default values]**: adiciona ao pacote os valores de todos os atributos das entidades.

   Essa opção não está selecionada por padrão para evitar exportações demoradas. Isso significa que os atributos das entidades com valores padrão (&#39;string vazia&#39;, &#39;0&#39; e &#39;falso&#39; se não definido de outra forma no schema) não serão adicionados ao pacote e, portanto, não serão exportados.

   >[!CAUTION]
   >
   >Desmarcar essa opção pode mesclar as versões local e importada.
   >
   >Se a instância onde o pacote for importado contiver entidades idênticas ao próprio pacote (por exemplo, com a mesma ID externa), então seus atributos não serão atualizados. Isso pode ocorrer se os atributos da instância anterior possuírem valores padrão, pois não estão incluídos no pacote.
   >
   >In that case, selecting the **[!UICONTROL Include default values]** option would prevent versions merging, as all attributes from the former instance would be exported with the package.

### Exportação de pacotes de uma definição de pacote {#exporting-packages-from-a-package-definition}

Siga as etapas abaixo para exportar um pacote de uma definição de pacote:

1. Select the package definition to export, then click the **[!UICONTROL Actions]** button and select **[!UICONTROL Export the package]**.
1. Um arquivo XML correspondente ao pacote exportado é selecionado por padrão. Ele é nomeado de acordo com o nome e o namespace da definição de pacote.
1. Once the package name and location defined, click the **[!UICONTROL Start]** button to launch the export.

   ![](assets/packagedefinition_packageexport.png)

## Importação de pacotes {#importing-packages}

### Sobre importação de pacotes {#about-package-import}

The package import wizard is accessible via the main menu **[!UICONTROL Tools > Advanced > Package import...]** of the Adobe Campaign client console.

É possível importar um pacote de uma exportação executada anteriormente, por exemplo, de outra instância do Adobe Campaign ou um pacote padrão, dependendo dos termos da sua licença.

![](assets/ncs_datapackage_import.png)

### Instalação de um pacote de um arquivo {#installing-a-package-from-a-file}

To import an existing data package, select the XML file and click **[!UICONTROL Open]**.

![](assets/ncs_datapackage_import_1.png)

O conteúdo do pacote a ser importado é exibido na seção intermediária do editor.

Clique em **[!UICONTROL Next]** e **[!UICONTROL Start]** para iniciar a importação.

![](assets/ncs_datapackage_import_2.png)

### Instalação de um pacote padrão {#installing-a-standard-package}

Os pacotes padrão são instalados quando o Adobe Campaign é configurado. Dependendo das suas permissões e do modelo de implantação, é possível importar novos pacotes padrão se adquirir novas opções ou add-ons ou se atualizar para uma nova oferta.

Consulte o contrato de licença para verificar quais pacotes você pode instalar.

Para obter mais informações sobre pacotes padrão, consulte [esta página](../../installation/using/installing-campaign-standard-packages.md).
