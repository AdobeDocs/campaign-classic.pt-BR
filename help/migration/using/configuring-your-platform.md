---
title: Configuração da plataforma
seo-title: Configuração da plataforma
description: Configuração da plataforma
seo-description: null
page-status-flag: never-activated
uuid: e6255e4b-c9c8-4ac9-9ee3-aaa4dc9e5ecf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: 4d2e765b-750b-457f-ad55-8bd6faaa86af
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 40391fbea53757decb48fd937f5e74e8ba6fb207

---


# Configuração da plataforma{#configuring-your-platform}

Determinadas alterações importantes no Adobe Campaign v7 exigem uma configuração para garantir sua operação efetiva. Esses parâmetros podem ser necessários antes ou depois da migração. As alterações em causa e o respectivo modo de configuração são apresentados nesta seção.

Durante a migração, a tabela **NmsRecipient** é recriada a partir da definição do esquema. Qualquer alteração feita na estrutura SQL desta tabela fora do Adobe Campaign será perdida.

Exemplo de elementos a serem verificados:

* Se você tiver adicionado uma coluna (ou um índice) à tabela **NmsRecipient** , mas não a tiver detalhado no esquema, isso não será salvo.
* O atributo **tablespace** recupera seus valores por padrão, em outras palavras, os definidos no assistente de implantação.
* Se você tiver adicionado uma exibição de referência à tabela NmsRecipient, deverá excluí-la antes de migrar.

Este aviso também diz respeito aos usuários Oracle: se você tiver adicionado a opção **usetimestamptz:1** durante uma pós-atualização (consulte Fusos [](../../migration/using/general-configurations.md#time-zones)horários), todas as tabelas que contêm pelo menos um campo **date+time** serão recriadas.

## Antes da migração {#before-the-migration}

Ao migrar para o Adobe Campaign v7, os seguintes elementos devem ser configurados. Esses elementos devem ser abordados antes de iniciar a **pós-atualização**.

* Fusos horários

   Durante uma migração de uma plataforma v5.11, você deve especificar o fuso horário a ser usado durante a pós-atualização.

   Se quiser usar o modo &quot;vários fusos horários&quot;, consulte a seção [Fusos horários](../../migration/using/general-configurations.md#time-zones) .

   Se você usar o Oracle como um banco de dados, verifique se os arquivos de fuso horário Oracle foram sincronizados corretamente entre o servidor de aplicativos e o servidor de banco de dados. For more on this, refer to the [Oracle](../../migration/using/general-configurations.md#oracle) section.

* Zonas de segurança

   Por motivos de segurança, a plataforma do Adobe Campaign não está mais acessível por padrão: você deve configurar as zonas de segurança, que exigem a coleta dos endereços IP do usuário antes da migração.

   For more information, refer to the [Security](../../migration/using/general-configurations.md#security) section.

* Sintaxe

   Certas sintaxes no JavaScript podem ser aceitas nas versões 5.11 e 6.02 e não mais aceitas na versão v7, devido ao uso de um novo intérprete. For more information, refer to the [JavaScript](../../migration/using/general-configurations.md#javascript) section.

   Da mesma forma, uma nova sintaxe é introduzida no Adobe Campaign v7 para substituir a sintaxe baseada em SQLData. Se você usar elementos de código com essa sintaxe, será necessário adaptá-los. For more information, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* Senhas

   Você deve configurar as senhas **Admin** e **Internal** . For more information, refer to the [User passwords](../../migration/using/before-starting-migration.md#user-passwords) section.

* Estrutura das árvores

   Ao migrar de uma plataforma v5.11, você deve reorganizar as pastas de estrutura em árvore de acordo com as normas do Adobe Campaign v6. Para obter mais informações, consulte a seção de estrutura [em árvore do](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) Adobe Campaign v7.

* Interação

   Se você usar a **Interação**, deverá excluir todas as referências de esquema 6.02 que não existem mais na v7. For more information, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

## Após a migração {#after-the-migration}

Após executar o **pós-upgrade**, os seguintes elementos devem ser levados em conta e as configurações correspondentes executadas.

* Páginas de espelhamento

   O bloco de personalização da página espelhada foi alterado com a v6.x. Esta nova versão melhora a segurança ao acessar essas páginas.

   Se você usou o bloco de personalização v5 em suas mensagens, a exibição da página espelhada falhará. A Adobe recomenda usar o novo bloco de personalização ao inserir a página espelhada em suas mensagens.

   No entanto, como uma solução temporária (e como as páginas espelhadas ainda estão ativas), você pode voltar ao bloco de personalização antigo para evitar esse problema alterando a opção **[!UICONTROL XtkAcceptOldPasswords]** e definindo-a como **[!UICONTROL 1]**. Isso não afetará o uso do novo bloco de personalização v6.x.

* Sintaxe

   Se você encontrar erros relacionados à sintaxe, durante a pós-atualização, é necessário ativar temporariamente a opção **allowSQLInjection** no arquivo **serverConf.xml** , pois isso dá tempo para reescrever o código. Depois que o código for adaptado, reative a segurança. For more on this, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* Conflitos

   A migração é realizada por meio de uma pós-atualização e os conflitos podem aparecer em relatórios, formulários ou aplicativos da Web. Esses conflitos podem ser resolvidos no console.

   Consulte a seção [Conflitos](../../migration/using/general-configurations.md#conflicts) .

* Tomcat

   Se você personalizou a pasta de instalação, verifique se ela foi atualizada corretamente após a migração. Para obter mais detalhes, consulte a seção [Tomcat](../../migration/using/general-configurations.md#tomcat) .

* Relatórios

   Todos os relatórios predefinidos usam atualmente o mecanismo de renderização v6.x. Se você tiver adicionado o código JavaScript aos relatórios, alguns elementos poderão ser alterados.

   Consulte a seção [Relatórios](../../migration/using/general-configurations.md#reports) .

* Aplicações web

   Após a pós-atualização, se você tiver problemas de conexão com seus aplicativos Web identificados, ative as opções **allowUserPassword** e **sessionTokenOnly** no arquivo **serverConf.xml** . Lembre-se de desativar essas duas opções. Para obter mais informações, consulte a seção Aplicativos [da Web](../../migration/using/general-configurations.md#identified-web-applications) identificados.

   Dependendo do tipo de aplicativos da Web e de suas configurações, é necessário realizar manipulações adicionais para garantir que funcionem corretamente.

   Consulte a seção Aplicativos [da](../../migration/using/general-configurations.md#web-applications) Web.

   Ao migrar de uma plataforma v5.11, configurações adicionais devem ser realizadas: para obter mais informações, consulte a seção Aplicativos [da](../../migration/using/specific-configurations-in-v5-11.md#web-applications) Web.

* Zonas de segurança.

   Antes de iniciar o servidor, configure as zonas de segurança. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#defining-security-zones) e a seção [Segurança](../../migration/using/general-configurations.md#security) .

* Esquemas

   No Red Hat, você pode encontrar erros ao editar certos esquemas. For more on this, refer to the [Red-Hat](../../migration/using/general-configurations.md#red-hat) section.

* Fluxos de trabalho

   Ao migrar de uma plataforma v5.11, você deve controlar o diretório de tempo de execução dos fluxos de trabalho. For more on this, refer to the [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows) section.

* Rastreamento

   Ao migrar de uma plataforma v5.11, você deve configurar o modo de rastreamento. For more on this, refer to the [Tracking](../../migration/using/specific-configurations-in-v5-11.md#tracking) section.

* Home page

   Ao migrar de uma plataforma v6.02, você pode definir parâmetros adicionais para manter sua antiga página inicial da v6.02. Para obter mais informações, consulte a seção [Amizade do usuário: Página inicial e seção de navegação](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) .

* Interação

   Se você usar a **Interação**, deverá ajustar quaisquer parâmetros após a migração. For more on this, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

