---
product: campaign
title: Configuração da plataforma
description: Configuração da plataforma
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 2%

---

# Configuração da plataforma{#configuring-your-platform}

![](../../assets/v7-only.svg)

Determinadas alterações importantes no Adobe Campaign v7 exigem uma configuração para garantir sua operação efetiva. Esses parâmetros podem ser necessários antes ou depois da migração. As alterações relacionadas e seu modo de configuração são apresentados nesta seção.

Durante a migração, a tabela **NmsRecipient** é recriada a partir da definição de schemas. Qualquer alteração feita na estrutura SQL desta tabela fora do Adobe Campaign será perdida.

Exemplo de elementos para verificar:

* Se você tiver adicionado uma coluna (ou um índice) à tabela **NmsRecipient**, mas não a tiver detalhado no esquema, isso não será salvo.
* O atributo **tablespace** recupera seus valores por padrão, em outras palavras, os definidos no assistente de implantação.
* Se você tiver adicionado uma exibição de referência à tabela NmsRecipient, deverá excluí-la antes de migrar.

Esse aviso também diz respeito aos usuários do Oracle: se você tiver adicionado a opção **usetimestamptz:1** durante uma pós-atualização (consulte [Fusos horários](../../migration/using/general-configurations.md#time-zones)), todas as tabelas contendo pelo menos um campo **date+time** serão recriadas.

## Antes da migração {#before-the-migration}

Ao migrar para o Adobe Campaign v7, os seguintes elementos devem ser configurados. Esses elementos devem ser endereçados antes de iniciar o **postupgrade**.

* Fusos horários

   Durante uma migração de uma plataforma v5.11, você deve especificar o fuso horário a ser usado durante a pós-atualização.

   Se desejar usar o modo &quot;vários fusos horários&quot;, consulte a seção [Fusos horários](../../migration/using/general-configurations.md#time-zones).

   Se você usar o Oracle como um banco de dados, verifique se os arquivos de fuso horário do Oracle foram sincronizados corretamente entre o servidor de aplicativos e o servidor de banco de dados. Para obter mais informações, consulte a seção [Oracle](../../migration/using/general-configurations.md#oracle) .

* Zonas de segurança

   Por motivos de segurança, a plataforma Adobe Campaign não está mais acessível por padrão: você deve configurar as zonas de segurança, o que requer a coleta dos endereços IP do usuário antes da migração.

   Para obter mais informações, consulte a seção [Segurança](../../migration/using/general-configurations.md#security).

* Sintaxe

   Certas sintaxes no JavaScript podem ser aceitas nas versões 5.11 e 6.02 e não mais aceitas na versão v7, devido ao uso de um novo interpretador. Para obter mais informações, consulte a seção [JavaScript](../../migration/using/general-configurations.md#javascript) .

   Da mesma forma, uma nova sintaxe é introduzida no Adobe Campaign v7 para substituir a sintaxe baseada em SQLData. Se você usar elementos de código com essa sintaxe, deverá adaptá-los. Para obter mais informações, consulte a seção [SQLData](../../migration/using/general-configurations.md#sqldata).

* Senhas

   Você deve configurar as senhas **Admin** e **Interno**. Para obter mais informações, consulte a seção [Senhas do usuário](../../migration/using/before-starting-migration.md#user-passwords) .

* Estrutura de árvore

   Ao migrar de uma plataforma v5.11, você deve reorganizar as pastas da estrutura de árvore de acordo com as normas do Adobe Campaign v6. Para obter mais informações, consulte a seção [Estrutura de árvore do Adobe Campaign v7](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) .

* Interação

   Se você usar **Interaction**, deverá excluir todas as referências de esquema 6.02 que não existem mais no v7. Para obter mais informações, consulte a seção [Interaction](../../migration/using/general-configurations.md#interaction) .

## Após a migração {#after-the-migration}

Após executar **postupgrade**, os seguintes elementos devem ser considerados e as configurações correspondentes devem ser executadas.

* Mirror pages

   O bloco de personalização da mirror page foi alterado com a v6.x. Essa nova versão melhora a segurança ao acessar essas páginas.

   Se você usou o bloco de personalização v5 em suas mensagens, a exibição da mirror page falhará. O Adobe recomenda usar o novo bloco de personalização ao inserir a mirror page em suas mensagens.

   No entanto, como solução temporária (e como as mirror pages ainda estão ativas), é possível voltar ao bloco de personalização antigo para evitar esse problema, alterando a opção **[!UICONTROL XtkAcceptOldPasswords]** e configurando-a como **[!UICONTROL 1]**. Isso não afetará o uso do novo bloco de personalização v6.x.

* Sintaxe

   Se encontrar erros relacionados à sintaxe, durante a pós-atualização, você deve ativar temporariamente a opção **allowSQLInjection** no arquivo **serverConf.xml**, pois isso dá tempo para reescrever o código. Depois que o código for adaptado, certifique-se de reativar a segurança. Para obter mais informações, consulte a seção [SQLData](../../migration/using/general-configurations.md#sqldata).

* Conflitos

   A migração é realizada por meio de uma pós-atualização e os conflitos podem aparecer em relatórios, formulários ou aplicativos da Web. Esses conflitos podem ser resolvidos do console.

   Consulte a seção [Conflito](../../migration/using/general-configurations.md#conflicts).

* Tomcat

   Se você personalizou a pasta de instalação, verifique se ela foi atualizada corretamente após a migração. Para obter mais detalhes, consulte a seção [Tomcat](../../migration/using/general-configurations.md#tomcat).

* Relatórios

   Todos os relatórios prontos para uso atualmente usam o mecanismo de renderização v6.x. Se você tiver adicionado o código JavaScript aos relatórios, alguns elementos poderão ser alterados.

   Consulte a seção [Reports](../../migration/using/general-configurations.md#reports).

* Aplicações web

   Após a pós-atualização, se tiver problemas de conexão com as aplicações Web identificadas, ative as opções **allowUserPassword** e **sessionTokenOnly** no arquivo **serverConf.xml**. Lembre-se de desativar essas duas opções. Para obter mais informações, consulte a seção [Identified web applications](../../migration/using/general-configurations.md#identified-web-applications) .

   Dependendo do tipo de aplicação web e de sua configuração, você deve executar manipulações adicionais para garantir que funcionem corretamente.

   Consulte a seção [Web applications](../../migration/using/general-configurations.md#web-applications).

   Ao migrar de uma plataforma v5.11, configurações adicionais devem ser realizadas: para obter mais informações, consulte a seção [Web applications](../../migration/using/specific-configurations-in-v5-11.md#web-applications) .

* Zonas de segurança.

   Antes de iniciar o servidor, você deve configurar as zonas de segurança. Para obter mais informações, consulte [esta seção](../../installation/using/security-zones.md) e a seção [Security](../../migration/using/general-configurations.md#security).

* Esquemas

   No Red Hat, é possível encontrar erros ao editar determinados esquemas. Para obter mais informações, consulte a seção [Red-Hat](../../migration/using/general-configurations.md#red-hat) .

* Fluxos de trabalho

   Ao migrar de uma plataforma v5.11, você deve controlar o diretório de tempo de execução dos workflows. Para obter mais informações, consulte a seção [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows) .

* Rastreamento

   Ao migrar de uma plataforma v5.11, você deve configurar o modo de rastreamento. Para obter mais informações, consulte a seção [Tracking](../../migration/using/specific-configurations-in-v5-11.md#tracking) .

* Home page

   Ao migrar de uma plataforma v6.02, você pode definir parâmetros adicionais para manter sua antiga página inicial da v6.02. Para obter mais informações, consulte [Facilidade do usuário: Página inicial e seção de navegação](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation).

* Interação

   Se você usar **Interaction**, deverá ajustar os parâmetros após a migração. Para obter mais informações, consulte a seção [Interaction](../../migration/using/general-configurations.md#interaction) .
