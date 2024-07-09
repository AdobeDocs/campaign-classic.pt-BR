---
product: campaign
title: Perguntas frequentes sobre a migração para o Adobe Managed Services (Nuvem pública)
description: Perguntas frequentes sobre a migração do Campaign Classic para a Nuvem pública
feature: Technote, Upgrade
role: User
level: Beginner
exl-id: a9cd08b0-55c2-4405-9fb8-f0c623cd4ccb
source-git-commit: 6803b6628313db9108a191fd143dac68ee799149
workflow-type: tm+mt
source-wordcount: '2225'
ht-degree: 39%

---

# Perguntas frequentes sobre a migração para a Nuvem pública{#dc-faq}



O Adobe descomissiona o data center herdado: as instâncias do Campaign Classic devem ser transferidas para o Public Cloud Amazon Web Services (AWS). [Saiba mais sobre esta iniciativa](dc-migration.md).

Veja abaixo um conjunto de perguntas comuns sobre esse projeto, o impacto nos ambientes do Campaign e outros recursos úteis.

Para qualquer outra pergunta, entre em contato com o [Atendimento ao cliente da Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).

## Impactos na infraestrutura

![](assets/do-not-translate/database.png)

Os impactos globais no banco de dados e na infraestrutura estão listados abaixo.

* **O banco de dados vai mudar? Qual é a versão do novo banco de dados? Qual sistema operacional será usado?**

  A Adobe se reserva o direito de escolher e implantar o mecanismo de gerenciamento de banco de dados mais adequado para atender ao Adobe Campaign Service em condições ideais.

  Além disso, para preservar o melhor nível de segurança, a Adobe não fornecerá informações detalhadas relacionadas à infraestrutura.

* **Há risco de perda de dados?**

  O banco de dados será descarregado do datacenter herdado e restaurado na Nuvem pública (AWS). Quando reiniciado no novo data center, o aplicativo será retomado do estado exato em que estava antes da migração. Os usuários não notarão diferença, exceto que algumas tarefas programadas terão sido adiadas.

* **Existem diferenças no tamanho do pacote entre o data center herdado e a Nuvem pública?**

  Estamos provisionando na Nuvem pública (AWS) com novas definições de pacote com base no tamanho atual do banco de dados, tamanho do disco, etc. Por exemplo, se um cliente tiver um servidor de aplicativos em data centers herdados, poderá ter dois servidores de aplicativos na Nuvem pública (AWS) com base nas definições do pacote.

* **O número de build ou a versão do Campaign será alterado?**

  Como primeiro passo, manteremos o mesmo build do Campaign Classic com a migração.

  Em outra etapa, continuaremos a atualizar para a build mais recente do Campaign Classic GA. Para obter mais informações, consulte [esta página](../../rn/using/rn-overview.md).

* **Qual é o plano para solucionar problemas após a migração?**

  Testes abrangentes serão realizados antes da migração dos sistemas de produção. No entanto, em caso de problemas, [Atendimento ao cliente Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support) continuará a ser o principal ponto de contato. a Adobe criou uma equipe de especialistas para fornecer suporte avançado, se necessário.

## Impactos na capacidade de entrega

![](assets/do-not-translate/features.png)

Os impactos globais em IPs, listas de bloqueios, subdomínios e URLs estão listados abaixo.

* **Como o IP na inclui na lista de permissões será tratado? Os clientes precisarão adicionar novos endereços IP ao para incluir na lista de permissões o tráfego de entrada do Campaign?**

  O endereço IP dos servidores da Adobe será alterado. Portanto, talvez os clientes precisem adicionar esses novos endereços IP no incluir na lista de permissões em seus sistemas.

  [Saiba mais](#config) sobre IP no incluo na lista de permissões.

* **Incluir na lista de permissões Como lidaremos com a porta adicionada ao arquivo de pesquisa para acesso SFTP/FTP?**

  Incluir na lista de permissões A configuração SFTP + IP no arquivo também será transferida do data center herdado para a Nuvem pública (AWS). Nenhuma ação esperada do cliente.

* **Estamos alterando os IPs?**

  O endereço IP dos servidores da Adobe será alterado. Portanto, talvez os clientes precisem adicionar esses novos endereços IP ao incluir na lista de permissões em seus sistemas.

  [Saiba mais](#config) sobre IP no incluo na lista de permissões.

* **Como a delegação de subdomínios será tratada?**

  Os subdomínios existentes serão transferidos do data center herdado para a Nuvem pública (AWS). Esta parte será gerenciada pela equipe da Adobe Deliverability como parte do processo de migração.

  >[!NOTE]
  >
  >O compromisso da equipe de avaliação do delivery é baseado no contrato, e os clientes devem entrar em contato com o representante da Adobe para obter informações relacionadas ao compromisso de avaliação do delivery.

  A Adobe orientará o cliente nos testes necessários para garantir que a configuração esteja funcionando a todo vapor nos novos servidores da Nuvem pública (AWS) após a migração.

* **A migração produzirá novos URLs para rastreamento, recursos e aplicações Web?**

  Não, preservaremos os URLs existentes.

* **Haverá uma alteração no subdomínio de Neolane.net para campaign.adobe.com?**

  Ambos `neolane.net` e `campaign.adobe.com` estarão em vigor após a migração. Para simplificar: redirecionaremos o neolane.net para novas instâncias na Nuvem pública (AWS), portanto, nenhuma alteração será necessária para o cliente.

* **Qual é o plano para o aquecimento de IP?**

  Primeiramente, a equipe de Entregabilidade do Adobe avaliará o status da capacidade de entrega da plataforma e recomendará um plano para a mudança para os novos IPs

  Nenhum aquecimento será necessário após a migração. Pode tratar-se de uma exceção e, nesse caso, [Atendimento ao cliente Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support) entrará em contato com os clientes.

  No entanto, o plano é tornar essa operação transparente para a empresa, diferentemente do aumento inicial realizado durante a ativação.

  Quando a migração for concluída, a instância do Campaign terá IPs de envio totalmente diferentes. Como uma questão de garantir uma transição sem problemas, a Adobe implementará um aumento dos novos IPs de envio, alternando gradativamente o tráfego dos IPs antigos para os novos.

* **Estamos transferindo o URL na inclui na lista de permissões?**

  Sim, isso é armazenado no arquivo de configuração do servidor que será copiado da origem para a nova instância.

* **Qual deve ser o impacto no subdomínio delegado que usamos para marcar nossa comunicação?**

  Os subdomínios usados para comunicação de marketing permanecem os mesmos. No entanto, dependendo da implementação, são necessárias ações do lado do cliente:
   * No caso de delegação de subdomínio para Adobe (padrão), o Adobe cuida de todas as alterações e garante uma transição contínua.
   * No caso de configuração CNAME (exceção), o cliente é solicitado a implementar alterações, em coordenação com o Adobe.

## Impactos na configuração e na conectividade

![](assets/do-not-translate/maintenance.png)

### Observação sobre IP na inclui na lista de permissões{#config}

A migração para a Nuvem pública virá com novos IPs para servidores de aplicativos do Adobe Campaign, para que a alteração do IP tenha impactos na conectividade entre os servidores da Adobe e seus sistemas de informação.

![](assets/migration.png)

Vamos considerar os dois casos:

* Tráfego de entrada: todas as atividades de rede iniciadas de seus sistemas ou de terceiros para os servidores da Adobe Campaign. A configuração será gerenciada pela Adobe e copiada da nuvem herdada para a pública durante a migração. Em seguida, a conectividade para o tráfego de entrada será preservada como ocorre, após a migração, e nenhuma ação será esperada do lado do cliente

* Tráfego de saída: todas as atividades de rede iniciadas pelos servidores do Adobe Campaign para o seu Sistema de informações ou qualquer outra empresa (por exemplo: provedor SMS). Dependendo das políticas de segurança em vigor em sua organização, as alterações de IPs podem exigir a operação de inclui na lista de permissões do seu Sistema de informações ou de terceiros

### Impactos globais

Os impactos globais na configuração, na conectividade com outros sistemas e produtos, nas APIs e no fuso horário estão listados abaixo.

* **A migração afetará a conectividade com contas externas?**

  Sim. Integrações de terceiros, provedores de SMS, por exemplo, devem adicionar novos endereços IP de servidores de aplicativos Adobe Campaign ao incluo na lista de permissões.

* **A migração afetará a conectividade com o Adobe Analytics usando o conector Genesis? Incluir na lista de permissões E quanto à adição de endereços IP do Campaign ao arquivo no lado do Adobe Analytics?**

  Os endereços IP dos servidores de aplicativos do Adobe Campaign serão alterados. Essa etapa será realizada pelo Atendimento ao cliente da Adobe após a migração.

* **A migração afetará a conectividade com outras soluções de Adobe (AEM, Target etc.)?**

  As integrações são uma combinação de endereços IP declarados no arquivo de inclui na lista de permissões e na configuração da conta do serviço da Web. Isso será de responsabilidade do Atendimento ao cliente Adobe.

  Na inclui na lista de permissões, haverá endereços IP que serão necessários na solução externa, pois o IP dos servidores de aplicativos será alterado. Essas informações serão fornecidas. Outras partes da integração são baseadas no IMS e devem funcionar como estão.

* **E quanto ao cliente que não está anexado à ID da organização para integração do IMS?**

  Os clientes que não têm IMS receberão um: uma ID da organização será atribuída à instância.

* **As configurações de várias marcas são afetadas pela migração?**

  Assim que o subdomínio e todas as configurações relacionadas forem transferidos/redirecionados corretamente do data center herdado para a Nuvem pública (AWS), não deve haver impacto.

* **A conectividade da API é afetada pela migração?**

  O endereço IP dos servidores da Adobe será alterado. Portanto, talvez os clientes precisem adicionar esses novos endereços IP ao incluir na lista de permissões em seus sistemas.

  [Saiba mais](#config) sobre IP na inclui na lista de permissões.

* **Asseguraremos que todos os parâmetros de configuração de memória do JavaScript estejam definidos corretamente após a migração?**

  Copiaremos a configuração da instância do data center herdado para a Nuvem pública (AWS), de modo que esses valores serão preservados após a migração.

* **Existe algum risco de acesso a determinadas extensões de arquivo?**

  O cliente pode querer permitir que os arquivos de fonte sejam carregados na pasta de recursos públicos. Essa configuração é feita na versão atual `config-<instance>.xml` arquivo. Ela será copiada com os arquivos de configuração.

* **O fuso horário está mudando no novo servidor? O cliente poderá manter seu fuso horário atual?**

  Pode mudar de acordo com a localização dos novos servidores. No entanto, o cliente poderá manter o fuso horário atual.

  [Saiba mais](../../workflow/using/managing-time-zones.md) sobre o gerenciamento de fuso horário no Adobe Campaign Classic v7.


## Segurança e permissões

![](assets/do-not-translate/security.png)

Com essa migração para a Nuvem pública (AWS), os ambientes do cliente serão mantidos atualizados com todos os requisitos de segurança necessários. Isso inclui :

* Os patches mais recentes de sistema operacional e segurança periodicamente
* Isolamento da infraestrutura por cliente
* A segurança gerenciada e as revisões de auditoria para oferecer suporte à infraestrutura em nuvem, como balanceadores de carga, regras de segurança de rede e criptografia de armazenamento.

Os impactos em permissões, certificados e acesso SFTP estão listados abaixo.

* **Vamos mover todos os certificados para os novos servidores?**

  Sim, todos os certificados serão movidos como parte dessa migração.

* **Precisamos solicitar novas chaves de acesso STP ao cliente?**

  Não, o Adobe copiará as chaves de acesso SFTP como estão no novo servidor.

* **Como as permissões SFTP são tratadas?**

  Estamos garantindo que novos servidores SFTP, usuários, diretórios e arquivos tenham exatamente os mesmos níveis de permissão.

* **Se a conexão SFTP não puder ser estabelecida, qual será a solução alternativa/plano para manter o cliente em operação?**

  Incluir na lista de permissões O único problema de conectividade que pode surgir está relacionado à consulta do cliente. O cliente deve adicionar esse teste em um ambiente que não seja de produção para garantir que funcione, antes de migrar para a produção.

* **Existem configurações de inclui na lista de permissões específicas do data center que precisam ser transferidas?**

  Não, não há nenhuma configuração de inclui na lista de permissões específica do data center para gerenciar.

* **Estamos garantindo que scripts personalizados sejam executados com êxito no novo ambiente?**

  A implementação do cliente pode usar scripts personalizados (Perl/Shell/Python/Java Script) em fluxos de trabalho para manipular arquivos e pastas, por exemplo.

  Na instância hospedada, os scripts são executados somente pelo mecanismo do JavaScript. Essas implementações específicas podem causar falhas de segurança e problemas após a atualização. Elas não são compatíveis.

* **Com a integração do IMS, ele funcionará como está em uma nova instância ou será necessária uma atualização de configuração adicional?**

  Como mantemos os mesmos nomes de DNS, ele deve funcionar como está após a migração.


## Execução da migração

![](assets/do-not-translate/upgrades.png)

Os impactos globais durante a migração estão listados abaixo.

* **Precisamos planejar a interrupção da atividade de Marketing durante a migração?**

  A Adobe recomenda desacelerar e, idealmente, pausar todas as execuções pouco antes do desligamento do aplicativo no data center herdado: entregas e fluxos de trabalho. Isso facilitará a reinicialização no Servidor na nuvem (AWS), pois os processos terão tempo para pausar &quot;normalmente&quot; e salvar qualquer estado de execução em andamento.

* **Esperamos tempo de inatividade do serviço da Adobe Campaign?**

  A migração terá um tempo de inatividade inevitável da plataforma. O objetivo deste plano é orientar para minimizar esse tempo de inatividade.

  A transferência de dados entre data centers é parte do processo que impacta o tempo de inatividade. Os dados são armazenados de duas formas:

   * De longe o mais importante, o banco de dados
   * Arquivos no servidor de aplicativos (importações e exportações de dados)

  A redução do tamanho do banco de dados é da maior importância para acelerar a transferência de dados. Sugestões:

   * Reduza os períodos de retenção dos dados históricos (registros de entrega, registros de rastreamento, etc.)
   * Excluir registros inúteis em outras tabelas (entregas, destinatários, tabelas personalizadas)

* **Qual é o tempo de inatividade estimado para migrar uma instância?**

  O tempo de inatividade depende totalmente do tamanho do banco de dados do cliente e do armazenamento de arquivos SFTP. Entre em contato com o Atendimento ao cliente para obter uma duração estimada.

* **E as mensagens enviadas do servidor herdado? Os links sempre estarão acessíveis?**

  Enquanto a migração estiver em execução, somente um serviço permanecerá funcional: redirecionamento de links de email. Todos os destinatários poderão acessar a página de aterrissagem quando clicarem em um email. No entanto, esses cliques não serão rastreados, portanto, as taxas de clique para as entregas que foram iniciadas pouco antes da migração serão menores do que o normal.

* **E os ambientes de mid-sourcing/RT?**

  Mid-sourcing e RT são tratados como qualquer outra infraestrutura hospedada.

* **Em que ordem as migrações serão realizadas?**

  Os ambientes serão migrados na seguinte ordem:

   1. Ambientes de desenvolvimento
   1. Ambientes de preparo
   1. Ambientes de produção
   1. Ambientes de RT
   1. Ambientes de mid-sourcing

* **O que é plano de reversão?**

  O plano de reversão é retornar o DNS e redefinir o banco de dados de origem como leitura e gravação de somente leitura. Eventualmente teremos automação para isso.

* **Depois da migração, ainda podemos acessar instâncias antigas?**

  Quando a migração do aplicativo estiver concluída, não haverá plano para executar os processos novamente no data center herdado. Esperamos que todos os dados no data center herdado possam ser apagados, exceto para fins de backup temporário, até que os processos de backup programados sejam executados na Nuvem pública (AWS).

* **Quanto tempo de teste será permitido para cada instância após a migração para a Nuvem pública?**

  Dependendo da complexidade do cliente, será necessário um tempo de Bake de pelo menos uma semana entre as migrações do ambiente de Preparo e do ambiente de Produção.

* **Incluir na lista de permissões Quem lidará com a adição de novos IPs ao arquivo?**

  A equipe de Atendimento ao cliente do Adobe cuidará de garantir que o cliente e terceiros possam acessar o novo sistema, adicionando os novos IPs ao incluo na lista de permissões.

## Suporte e outros links úteis{#support}

* [Migração para o Adobe Managed Services (Nuvem pública)](dc-migration.md)
* [Atualização anual do Campaign](../../rn/using/rn-overview.md#yeary-upgrade)
* [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md)
