---
product: campaign
title: Perguntas frequentes sobre o Campaign Classic
description: Perguntas específicas sobre arquitetura, implantação e recursos do Adobe Campaign Classic v7
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: 295e3596d9291cbcc55e2d264309141526c3806b
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 5%

---

# Perguntas frequentes sobre o Campaign Classic v7 {#campaign-classic-v7-faq}

Estas Perguntas frequentes abordam perguntas específicas sobre a arquitetura do Adobe Campaign Classic v7, modelos de implantação e recursos específicos do v7.

**Para obter respostas abrangentes a perguntas comuns sobre o Campaign** (workflows, entregas, públicos, relatórios, personalização, etc.), consulte as [**Perguntas frequentes abrangentes sobre o Campaign v8**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}, que fornecem respostas detalhadas organizadas por tópico.

## Arquitetura e implantação do Campaign Classic v7 {#v7-architecture}

### Quais são os modelos de hospedagem disponíveis no Campaign Classic v7? {#what-are-the-hosting-models-available-in-campaign-classic-v7}

O Adobe Campaign Classic v7 oferece três modelos de implantação:

* **Hospedado (Managed Services)** - Totalmente gerenciado pela Adobe na infraestrutura da Adobe
* **No local** - Instalado e gerenciado em sua própria infraestrutura
* **Híbrido** - Arquitetura de mid-sourcing com combinação de componentes de nuvem e no local

Cada modelo de implantação tem diferentes recursos e responsabilidades de gerenciamento. A disponibilidade de módulos, opções e configurações depende do tipo de implantação.

[Clique aqui para saber mais](../../installation/using/hosting-models.md) sobre modelos de hospedagem e suas diferenças.

**Observação:** o Campaign v8 está disponível exclusivamente como Managed Cloud Services. [Saiba mais sobre o Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}.

### Quais são as diferenças ao trabalhar em um ambiente no local ou hospedado? {#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

O Adobe Campaign Classic v7 vem com um conjunto de módulos e opções. A disponibilidade desses módulos e sua configuração dependem do [tipo de implantação](../../installation/using/hosting-models.md) da sua instalação: hospedada (Managed Services), híbrida ou local.

Principais diferenças:

* **No local** - Controle total sobre instalação, infraestrutura e configuração. Requer recursos internos de TI para manutenção, atualizações e segurança.
* **Hosted/Managed Services** - Infraestrutura e manutenção gerenciadas pela Adobe. Atualizações automáticas e segurança aprimorada. Acesso direto limitado ao servidor.
* **Híbrido** - Combina os benefícios de ambos os modelos. Instância de marketing hospedada pelo Adobe, execução/mid-sourcing gerenciado separadamente.

[Clique aqui para obter a matriz de recursos completos](../../installation/using/capability-matrix.md).

### Como migrar de local/híbrido para o Adobe Managed Services? {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

A migração para o Adobe Managed Services oferece melhor escalabilidade, segurança e redução das despesas gerais de TI. Geralmente, é uma etapa antes da transição para o Campaign v8.

**Pontos principais:**

* Nenhuma ferramenta de migração automatizada disponível - planejamento e execução manuais necessários
* Suporte ao Adobe Professional Services altamente recomendado
* Os benefícios incluem infraestrutura em nuvem, patches de segurança automáticos, suporte especializado e caminho mais fácil para o v8
* A migração envolve devida diligência, auditoria de ambiente, limpeza de dados, migração de preparo e transferência de produção

**Introdução**: entre em contato com o representante da Adobe para avaliar seu ambiente e desenvolver um plano de migração detalhado com a Adobe Professional Services.

Saiba mais sobre a [migração para o Managed Services](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605){target="_blank"}.

## Atualizações de build (Campaign Classic v7) {#build-upgrades-v7}

### O que é uma atualização de build no Campaign Classic v7? {#what-is-a-build-upgrade-v7}

A atualização de build ocorre quando o software Adobe Campaign Classic v7 é atualizado para o número de build seguro mais recente, permanecendo no mesmo nível de build primário/secundário. Por exemplo: Campaign Classic v7 build 9026 para Campaign v7 build 9032.

O Adobe Campaign é atualizado regularmente. Versões secundárias são lançadas com novos recursos, melhorias e correções. Além disso, as builds com correções cumulativas somente são lançadas periodicamente.

Saiba mais [nesta seção](../../rn/using/rn-overview.md).

### Como posso atualizar o Campaign Classic v7 para a versão mais recente? {#how-can-i-upgrade-campaign-classic-v7}

A Adobe Campaign Classic usa uma variedade de tecnologias para agregar valor. Essa combinação de tecnologias requer que você atualize regularmente suas instâncias do Campaign Classic v7, garantindo assim que as versões mais atualizadas estejam sendo usadas para oferecer segurança, estabilidade e melhor desempenho.

**Para clientes hospedados:** você se beneficia automaticamente da atualização anual do Campaign com a versão estável mais recente. O Adobe gerencia o processo de atualização e coordena o tempo com você.

**Para clientes locais/híbridos:** Você é responsável por executar as atualizações. A Adobe recomenda que a atualização seja feita pelo menos uma vez por ano.

[Leia esta seção](../../production/using/build-upgrade.md) para saber como atualizar seu ambiente e leia as [Perguntas frequentes sobre atualização de compilação](../../platform/using/faq-build-upgrade.md) para obter perguntas detalhadas sobre este tópico específico.

### Qual é a versão mais recente do Adobe Campaign Classic v7? {#what-is-the-latest-version-v7}

A versão mais recente do Campaign Classic v7, incluindo novos recursos e documentação, está detalhada nas [Notas de versão](../../rn/using/latest-release.md) mais recentes.

### Como sei qual versão do Campaign Classic v7 estou executando? {#how-do-i-know-which-version-v7}

Verifique sua versão e número de compilação no menu **[!UICONTROL Help > About...]** no console do Cliente Adobe Campaign. A caixa **[!UICONTROL About]** contém informações detalhadas sobre a versão e a compilação que você está executando para o console e para o servidor.

Saiba mais [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

### Uma atualização de build é igual a uma atualização de versão? {#is-build-upgrade-same-as-version-upgrade}

Não. Uma atualização de build é uma atualização incremental em determinada versão principal, enquanto que uma atualização de versão é uma alteração de uma versão principal para outra. As atualizações de build são diretas e normalmente não envolvem grandes alterações arquitetônicas, técnicas ou de modelo de dados.

As atualizações de versão (por exemplo, v7 para v8) geralmente vêm com alterações técnicas significativas e podem exigir alterações de configuração ou reimplementação parcial, dependendo das personalizações.

## Configuração do Campaign Classic v7 {#v7-configuration}

### Posso alterar o idioma da interface do Campaign Classic v7? {#can-i-change-language-v7}

O idioma do Campaign Classic v7 é selecionado ao criar a instância. **Não é possível alterá-lo posteriormente.**

A interface do usuário do Adobe Campaign v7 está disponível em 4 idiomas: inglês, francês, alemão e japonês. O console do cliente e o servidor devem ser definidos com o mesmo idioma. Cada instância do Campaign Classic v7 só pode ser executada em um idioma.

Em inglês, ao instalar o Campaign v7, você pode selecionar inglês americano ou inglês do Reino Unido: eles diferem nos formatos de data e hora.

[Saiba mais nesta seção](../../installation/using/creating-an-instance-and-logging-on.md).

**Observação:** a interface do usuário da Web do Campaign v8 permite que os usuários alterem o idioma da interface de maneira independente. [Saiba mais](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html#language-pref){target="_blank"}.

### Como posso configurar zonas de segurança no Campaign Classic v7? {#how-can-i-configure-security-zones-v7}

A interface de autoatendimento de zonas de segurança pode ser usada para gerenciar entradas na configuração de zona de segurança de VPN de uma implantação do Adobe Campaign Classic v7. Isso é relevante principalmente para implantações locais e híbridas.

Leia [esta seção](../../installation/using/security-zones.md) para saber mais sobre zonas de segurança no Campaign v7.

[Clique aqui para saber mais](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/security-zones.html?lang=pt-BR#installing-campaign-classic){target="_blank"} sobre a interface do usuário de autoatendimento da Zona de Segurança.

**Observação:** clientes hospedados/Managed Services devem contatar a Adobe para configurar zonas de segurança.

### O Adobe Campaign Classic v7 pode ser integrado ao LDAP? {#can-campaign-classic-integrate-with-ldap}

Sim. Como um **cliente local/híbrido**, você pode integrar o Campaign Classic v7 ao seu diretório LDAP para autenticação centralizada e gerenciamento de usuários.

Essa integração permite:

* Usuários para autenticar em seu diretório LDAP corporativo
* Gerenciamento centralizado de usuários e direitos
* Sincronização automática de grupos de usuários e permissões
* Recursos de logon único

[Clique aqui para saber como](../../installation/using/connecting-through-ldap.md) configurar a integração LDAP no Campaign Classic v7.

**Observação:** a integração de LDAP está disponível para implantações locais e híbridas. Os clientes hospedados usam o Adobe IMS para autenticação.

### Quais são as práticas recomendadas de segurança para implantações locais? {#security-best-practices-on-premise}

As implantações locais e híbridas exigem configuração de segurança adicional e fortalecimento em comparação aos ambientes hospedados.

**Principais áreas de segurança:**

* Segurança de rede e configuração de firewall
* Acesso e segurança do banco de dados
* Fortalecimento do sistema operacional
* Permissões de arquivo e controles de acesso
* Configuração de zonas de segurança
* Criptografia (dados em repouso e em trânsito)
* Gerenciamento de acesso do usuário
* Patches de segurança regulares
* Logs e monitoramento de auditoria

Leia a [Lista de verificação de configuração de segurança](https://helpx.adobe.com/campaign/kb/acc-security.html){target="_blank"} para descobrir os principais elementos sobre esse assunto e com relação à proteção para implantações locais.

### Como limpar o cache do console do cliente? {#how-do-i-clear-console-cache}

Limpar o cache do console do cliente do Campaign resolve muitos problemas comuns de exibição e funcionalidade. O cache armazena arquivos de configuração locais que às vezes podem se tornar corrompidos ou desatualizados.

**Quando limpar o cache:**

* Os novos elementos de marca não são exibidos corretamente
* Falha inesperada nas funções de exportação/importação
* Elementos de interface não atualizados após alterações de configuração
* Problemas de desempenho ou resposta lenta do console
* Depois de atualizar para uma nova versão do console do cliente

**Como limpar o cache:**

1. **Limpeza de Soft Cache (tente isso primeiro):**
   * Abra o console do cliente do Campaign
   * Ir para o menu **[!UICONTROL File]**
   * Selecionar **[!UICONTROL Clear the local cache...]**
   * Confirmar a ação quando solicitado
   * Reinicie o console do cliente

2. **Limpeza do Hard Cache (se a limpeza flexível não resolver o problema):**
   * Execute a limpeza do Soft Cache primeiro
   * Faça logoff e feche o console do cliente completamente
   * Navegue até:
      * Windows 7/10: `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
      * Windows XP: `C:\Documents and Settings\<Username>\Application Data\Neolane\NL_5\`
   * Excluir todos os arquivos XML nomeados como `nlclient-config-<alphanumerical value>.xml` e pastas associadas
   * **Importante:** NÃO excluir o arquivo `nlclient_cnx.xml`
   * Reiniciar console do cliente

Saiba mais em [Documentação do console do cliente do Campaign](../../platform/using/launching-adobe-campaign.md).

## Obtendo ajuda {#getting-help}

### Onde posso encontrar mais informações sobre o Campaign Classic v7? {#where-to-find-more-info-v7}

**Documentação e recursos:**

* [Documentação do Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=pt-BR){target="_blank"} - Documentação completa
* [Notas de versão do Campaign Classic v7](../../rn/using/latest-release.md) - Informações mais recentes da versão
* [Matriz de Compatibilidade do Campaign Classic](../../rn/using/compatibility-matrix.md) - Sistemas e versões com suporte
* [Tutoriais do Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR){target="_blank"} - Tutoriais em vídeo

**Para perguntas comuns sobre o Campaign:**

Consulte as [**Perguntas frequentes abrangentes sobre o Campaign v8**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}, que fornecem respostas detalhadas sobre:

* Introdução ao Campaign
* Perfis e públicos-alvos
* Design e entrega de mensagens
* Fluxos de trabalho e automação
* Relatórios e análises
* Configurações e definições do Campaign
* Recursos do desenvolvedor
* Privacidade e conformidade

**Comunidade e suporte:**

* [Fóruns da comunidade do Campaign](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"}
* [Suporte da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}
* [Painel de Controle (clientes hospedados)](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR){target="_blank"}

### Devo migrar do Campaign Classic v7 para o Campaign v8? {#should-i-migrate-to-v8}

O Campaign v8 é a plataforma estratégica da Adobe, ideal para organizações que precisam de campanhas de alto volume, interface do usuário moderna da Web, benefícios nativos da nuvem e suporte de longo prazo. O Campaign Classic v7 chegará ao fim do suporte nos próximos anos.

**Considere migrar para o Campaign v8 se:**

* Lidar com grandes volumes de dados ou enfrentar problemas de desempenho
* Deseja reduzir as despesas gerais de TI e o gerenciamento de infraestrutura (v8 é somente Managed Cloud Services)
* Necessidade de integração moderna entre a interface e o Adobe Experience Platform
* Quer tecnologia que não se torna obsoleta com atualizações automáticas
* No momento, estão em serviços hospedados/gerenciados (caminho de migração mais fácil)

**Considerações importantes:**

* O Campaign v8 está disponível exclusivamente como Managed Cloud Services (sem opções locais/híbridas)
* Requer planejamento para migração de personalizações e integrações
* A arquitetura FFDA traz desempenho, mas requer algumas adaptações de fluxo de trabalho/API

**Próximas etapas:** Entre em contato com seu representante da Adobe para avaliar a disponibilidade da migração e acessar as ferramentas de migração.

Saiba mais:

* [Visão geral do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}
* [Transição do Campaign Classic v7 para o v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/v7-to-v8.html){target="_blank"}
* [Perguntas frequentes abrangentes sobre o Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}

**Para obter respostas detalhadas a perguntas comuns do Campaign sobre fluxos de trabalho, entregas, públicos, relatórios, personalização e muito mais**, visite as [Perguntas frequentes abrangentes sobre o Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}.
