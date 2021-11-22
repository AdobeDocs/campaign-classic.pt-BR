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

Durante a migração, a variável **NmsRecipient** é recriada a partir da definição de schemas. Qualquer alteração feita na estrutura SQL desta tabela fora do Adobe Campaign será perdida.

Exemplo de elementos para verificar:

* Se você tiver adicionado uma coluna (ou um índice) ao **NmsRecipient** mas não a detalhou no schema, isso não será salvo.
* O **tablespace** O atributo retorna seus valores por padrão, em outras palavras, os definidos no assistente de implantação.
* Se você tiver adicionado uma exibição de referência à tabela NmsRecipient, deverá excluí-la antes de migrar.

Esse aviso também diz respeito aos usuários do Oracle: se você tiver adicionado o **usetimestamptz:1** durante uma pós-atualização (consulte [Fusos horários](../../migration/using/general-configurations.md#time-zones)), todas as tabelas contendo pelo menos uma **data+hora** são recriados.

## Antes da migração {#before-the-migration}

Ao migrar para o Adobe Campaign v7, os seguintes elementos devem ser configurados. Esses elementos devem ser abordados antes de iniciar a **pós-atualização**.

* Fusos horários

   Durante uma migração de uma plataforma v5.11, você deve especificar o fuso horário a ser usado durante a pós-atualização.

   Se quiser usar o modo &quot;multi timezone&quot;, consulte o [Fusos horários](../../migration/using/general-configurations.md#time-zones) seção.

   Se você usar o Oracle como um banco de dados, verifique se os arquivos de fuso horário do Oracle foram sincronizados corretamente entre o servidor de aplicativos e o servidor de banco de dados. Para obter mais informações, consulte [Oracle](../../migration/using/general-configurations.md#oracle) seção.

* Zonas de segurança

   Por motivos de segurança, a plataforma Adobe Campaign não está mais acessível por padrão: você deve configurar as zonas de segurança, o que requer a coleta dos endereços IP do usuário antes da migração.

   Para obter mais informações, consulte [Segurança](../../migration/using/general-configurations.md#security) seção.

* Sintaxe

   Certas sintaxes no JavaScript podem ser aceitas nas versões 5.11 e 6.02 e não mais aceitas na versão v7, devido ao uso de um novo interpretador. Para obter mais informações, consulte [JavaScript](../../migration/using/general-configurations.md#javascript) seção.

   Da mesma forma, uma nova sintaxe é introduzida no Adobe Campaign v7 para substituir a sintaxe baseada em SQLData. Se você usar elementos de código com essa sintaxe, deverá adaptá-los. Para obter mais informações, consulte [SQLData](../../migration/using/general-configurations.md#sqldata) seção.

* Senhas

   Você deve configurar o **Administrador** e **Interno** senhas. Para obter mais informações, consulte [Senhas do usuário](../../migration/using/before-starting-migration.md#user-passwords) seção.

* Estrutura de árvore

   Ao migrar de uma plataforma v5.11, você deve reorganizar as pastas da estrutura de árvore de acordo com as normas do Adobe Campaign v6. Para obter mais informações, consulte [Estrutura em árvore do Adobe Campaign v7](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) seção.

* Interação

   Se você usar **Interação**, você deve excluir todas as referências de schema 6.02 que não existem mais no v7. Para obter mais informações, consulte [Interação](../../migration/using/general-configurations.md#interaction) seção.

## Após a migração {#after-the-migration}

Depois de executar **pós-atualização**, os seguintes elementos devem ser considerados e as configurações correspondentes realizadas.

* Mirror pages

   O bloco de personalização da mirror page foi alterado com a v6.x. Essa nova versão melhora a segurança ao acessar essas páginas.

   Se você usou o bloco de personalização v5 em suas mensagens, a exibição da mirror page falhará. O Adobe recomenda usar o novo bloco de personalização ao inserir a mirror page em suas mensagens.

   No entanto, como solução temporária (e como as mirror pages ainda estão ativas), é possível voltar ao bloco de personalização antigo para evitar esse problema, alterando a opção **[!UICONTROL XtkAcceptOldPasswords]** e defina-o como **[!UICONTROL 1]**. Isso não afetará o uso do novo bloco de personalização v6.x.

* Sintaxe

   Se encontrar erros relacionados à sintaxe, durante a pós-atualização, é necessário ativar temporariamente o **allowSQLInjection** na **serverConf.xml** , pois isso dá tempo para reescrever o código. Depois que o código for adaptado, certifique-se de reativar a segurança. Para obter mais informações, consulte [SQLData](../../migration/using/general-configurations.md#sqldata) seção.

* Conflitos

   A migração é realizada por meio de uma pós-atualização e os conflitos podem aparecer em relatórios, formulários ou aplicativos da Web. Esses conflitos podem ser resolvidos do console.

   Consulte a [Conflitos](../../migration/using/general-configurations.md#conflicts) seção.

* Tomcat

   Se você personalizou a pasta de instalação, verifique se ela foi atualizada corretamente após a migração. Para obter mais detalhes, consulte a [Tomcat](../../migration/using/general-configurations.md#tomcat) seção.

* Relatórios

   Todos os relatórios prontos para uso atualmente usam o mecanismo de renderização v6.x. Se você tiver adicionado o código JavaScript aos relatórios, alguns elementos poderão ser alterados.

   Consulte o [Relatórios](../../migration/using/general-configurations.md#reports) seção.

* Aplicações web

   Após a pós-atualização, se tiver problemas de conexão com as aplicações web identificadas, ative o **allowUserPassword** e **sessionTokenOnly** nas opções da **serverConf.xml** arquivo. Lembre-se de desativar essas duas opções. Para obter mais informações, consulte [Aplicações web identificadas](../../migration/using/general-configurations.md#identified-web-applications) seção.

   Dependendo do tipo de aplicação web e de sua configuração, você deve executar manipulações adicionais para garantir que funcionem corretamente.

   Consulte a [Aplicações web](../../migration/using/general-configurations.md#web-applications) seção.

   Ao migrar de uma plataforma v5.11, configurações adicionais devem ser realizadas: para obter mais informações, consulte [Aplicações web](../../migration/using/specific-configurations-in-v5-11.md#web-applications) seção.

* Zonas de segurança.

   Antes de iniciar o servidor, você deve configurar as zonas de segurança. Para obter mais informações, consulte [esta seção](../../installation/using/security-zones.md) e [Segurança](../../migration/using/general-configurations.md#security) seção.

* Esquemas

   No Red Hat, é possível encontrar erros ao editar determinados esquemas. Para obter mais informações, consulte [Red-Hat](../../migration/using/general-configurations.md#red-hat) seção.

* Fluxos de trabalho

   Ao migrar de uma plataforma v5.11, você deve controlar o diretório de tempo de execução dos workflows. Para obter mais informações, consulte [Fluxos de trabalho](../../migration/using/specific-configurations-in-v5-11.md#workflows) seção.

* Rastreamento

   Ao migrar de uma plataforma v5.11, você deve configurar o modo de rastreamento. Para obter mais informações, consulte [Rastreamento](../../migration/using/specific-configurations-in-v5-11.md#tracking) seção.

* Home page

   Ao migrar de uma plataforma v6.02, você pode definir parâmetros adicionais para manter sua antiga página inicial da v6.02. Para obter mais informações, consulte [Facilidade de uso: Página inicial e navegação](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) seção.

* Interação

   Se você usar **Interação**, você deve ajustar os parâmetros após a migração. Para obter mais informações, consulte [Interação](../../migration/using/general-configurations.md#interaction) seção.
