---
solution: Campaign Classic
product: campaign
title: Perguntas frequentes de atualização de build
description: Perguntas frequentes sobre atualizações de construção de Campanhas
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2020'
ht-degree: 20%

---


# Build Upgrade FAQ {#build-upgrade-faq}

O Adobe Campaign é atualizado regularmente. If you are familiar with our published [Release Notes](../../rn/using/rn-overview.md), you are probably aware of the fact that on the average 2/3 minor versions packed with new features, improvements and fixes are released every year. Além disso, periodicamente liberamos builds apenas com correções cumulativas. Essa cadência regular de atualizações tem como objetivo obter as mais recentes e melhores em suas mãos, mantendo seu ambiente totalmente seguro e obviamente melhorando sua experiência com nosso produto.

É importante que nossos clientes executem a versão mais recente do Adobe Campaign. Ela também permite que o Adobe ajude com muito mais eficiência caso você encontre problemas - identificar, reproduzir e corrigir um problema em uma versão antiga normalmente leva mais tempo, sem mencionar que alguns problemas que você pode encontrar podem muito bem já ter sido corrigidos em uma versão recente.

Por isso, iniciamos o programa [Gold Standard](https://helpx.adobe.com/br/campaign/kb/gold-standard.html) para trabalhar em colaboração com nossos clientes para atualizar seus ambientes de forma proativa e regular.

## O que é uma atualização de compilação?

Uma atualização de compilação é quando o software Adobe Campaign Classic é atualizado para o número de compilação seguro mais recente, mas permanece no mesmo nível de compilação principal/secundário. Por exemplo: Campaign Classic v7 build 9026 para Campaign v7 build 9032.

Saiba mais [nesta seção](../../rn/using/rn-overview.md).

## Qual é a versão mais recente do Adobe Campaign Classic?

A versão mais recente do Campaign Classic, incluindo novos recursos e documentação, está detalhada nas [notas](../../rn/using/latest-release.md)de versão mais recentes.

## Como faço para saber qual versão estou executando?

Verifique sua versão no **[!UICONTROL Help > About...]** menu no console do Adobe Campaign Client. The **[!UICONTROL About]**  box contains detailed information on the version and build you are running both for the console and the server.

Saiba mais [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## O que significa o status da build?

Desde o Campaign Classic 19.2, um status está associado a cada build 

Saiba mais [nesta seção](../../rn/using/rn-overview.md).

## Uma atualização de build é a mesma coisa que uma atualização de versão?

Não. Uma atualização de build é uma atualização incremental em determinada versão principal, enquanto que uma atualização de versão é uma alteração de uma versão principal para outra. As atualizações de build são diretas, pois normalmente não envolvem grandes alterações arquitetônicas, técnicas ou de modelo de dados.

Por outro lado, as atualizações de versão geralmente vêm com alterações técnicas significativas e, dependendo da profundidade da configuração de um determinado cliente, podem exigir alterações significativas na configuração e/ou reimplementação parcial.

Por exemplo, usando as informações do servidor da captura de tela na seção anterior:

* Uma atualização de build envolveria a mudança da build 6880 para qualquer build posterior a 6880. Por exemplo, v6.1.1 build 8222 para v6.1.1 build 8666

* Uma atualização de versão envolveria a mudança da versão 6.0.2 para qualquer versão maior que 6.0.2.  Por exemplo: v6.0.1 build 2222 to v6.1.1 build 8666

## Devo fazer backup dos meus dados antes dessas atualizações?

O Adobe fará um backup do seu sistema antes de qualquer alteração. No entanto, se houver trabalho de personalização crítico que esteja em seu sistema de não produção (servidores de desenvolvimento ou de preparo temporário), é ALTAMENTE RECOMENDADO exportar esse trabalho como um pacote antes de qualquer atualização.

Para obter mais informações, [assista a este vídeo](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

## Quando ocorrerão as atualizações?

Será oferecido aos clientes um intervalo de datas para escolher. As alterações no sistema de produção não são realizadas em feriados.

As atualizações de build podem ser feitas de segunda a quinta-feira e as sextas-feiras são usadas apenas para instâncias não relacionadas à produção.

## Quanto tempo levará a atualização da build?

O tempo necessário para executar uma atualização de build depende de vários fatores:

* O tamanho do banco de dados a ser submetido a backup ou restaurado (bancos de dados maiores requerem mais tempo para atualizar)
* O tamanho dos ambientes (muitos de nossos clientes têm vários servidores diferentes que lidam com funções específicas, com ambientes maiores que exigem mais tempo para atualizar)
* A complexidade do sistema (alguns sistemas têm serviços e conexões mais dependentes para verificação, o que exige a verificação da estabilidade e do desempenho desses sistemas)

A atualização da criação é um processo de duas etapas:

1. Preparação do sistema para atualização - Levando em consideração as especificidades do seu ambiente, essa fase leva essencialmente a uma atualização totalmente qualificada em um ambiente que não seja de produção. Depois que o ambiente atualizado tiver sido destacado de um ponto de vista técnico e funcional, a fase 2 poderá ocorrer. Esta primeira fase, dependendo dos fatores acima mencionados, pode demorar de alguns dias a algumas semanas.

1. A atualização propriamente dita - o ambiente de produção é atualizado. Esta fase é normalmente realizada em poucas horas. Para ambientes muito complexos, é esperado um tempo de inatividade mais longo. No evento que algo dá errado, uma estratégia de reversão é definida e pode ser executada.

For more information, [refer to this document](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html).

## Quais recursos são necessários para a atualização de build?

O processo de atualização de build requer os seguintes recursos:

* Adobe Architect - Para as arquiteturas hospedadas ou de mensagens em nuvem/híbridas, o arquiteto deve coordenar-se com o Atendimento ao cliente.
* Gerenciador de projetos - hospedado: a equipe de hospedagem fará uma parceria com a equipe de Atendimento ao cliente e o cliente para coordenar a linha do tempo de atualização para todas as instâncias.
* Administrador da Adobe Campaign - hospedado: a equipe de hospedagem realiza a atualização.
* Operador do Adobe Campaign\usuário de marketing - O operador executa testes em instâncias de desenvolvimento, teste e produção.

## Como posso me preparar para a atualização de build?

Em seus sistemas de desenvolvimento e armazenamento temporário, exporte qualquer trabalho que seja crítico e deva ser preservado. Para obter mais informações, [assista a este vídeo](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

Atualize seu conhecimento dos workflows e delivery de caminho críticos desenvolvidos em seus livros de execução (ou pela equipe/parceiro de consultoria), analisando a documentação fornecida à sua equipe no final da implementação.

Identifique tempos de tráfego baixos ou de baixo volume que seriam ideais para janelas de manutenção, pois gerarão o menor impacto nos negócios.

Review our [build upgrade checklist below](#check-list) and your test plans and ensure that resources who can perform these tests are available within 24– 48 hrs. da conclusão de uma atualização.

For more information, [refer to this document](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html).

## As atualizações de build podem ser realizadas à noite ou fora do horário comercial?

As atualizações podem ser realizadas fora do horário. É sempre recomendável atualizar o ambiente durante o horário comercial, quando nenhum usuário comercial estiver conectado à instância.

## Quais são os custos associados a uma atualização de build?

Não há custo para instalar a atualização de build para clientes hospedados. Se houver desenvolvimentos personalizados no sistema, o Cliente precisará identificar os recursos necessários para testar esses desenvolvimentos após a atualização e corrigir quaisquer problemas encontrados com esses desenvolvimentos personalizados.

## Haverá acesso à instância durante o processo de atualização?

Não. O servidor é desligado durante uma atualização para garantir que a integridade dos dados seja preservada enquanto o produto é atualizado. Depois de concluído, ele é reiniciado e todos os serviços são reiniciados.

## Os e-mails continuarão a ser enviados do Centro de mensagens durante o processo de atualização?

Quando a atualização ocorrer para o Centro de mensagens (RT), não enviará emails da instância. Observe que todos os processos que são interrompidos quando um sistema de Campanha é desligado são automaticamente reiniciados quando o sistema é reiniciado. Isso inclui delivery ativos ou programados, rastreamento e cálculos de métricas para delivery enviados anteriormente.

## Os workflows continuarão em execução e enviarão os delivery?

Não. Durante a atualização de build, o fluxo de trabalho e os serviços de e-mail são interrompidos. Isso significa que os workflows não serão executados e os delivery não serão enviados. Eles serão reiniciados assim que o sistema for reiniciado. No entanto, o Adobe recomenda que todos os workflows de caminho críticos sejam verificados após uma atualização para garantir que eles estejam em execução e em bom estado de funcionamento.

## Meus links de rastreamento ainda funcionam durante a atualização?

Os links de rastreamento funcionarão durante a atualização. Não é possível enviar novos emails durante a atualização, mas os links de rastreamento incluídos em emails já enviados estarão operacionais.

## Eu preciso estar disponível durante o processo de atualização de build?

Sim. Os clientes devem fornecer ao Adobe um ponto de contato disponível durante ou imediatamente após a atualização da instância de produção.  O Adobe entrará em contato com esta pessoa por e-mail, a menos que outros acordos sejam feitos. Isso garantirá uma transição suave e a validação imediata de tarefas críticas. A Adobe entrará em contato com o cliente assim que a atualização de build for concluída para confirmação.

## Preciso atualizar o console do cliente?

Sim. O console do cliente deve estar na mesma build ou em uma build mais recente que a instância do servidor. Depois que a atualização for concluída, o console do cliente deverá solicitar a atualização para a build mais recente para garantir que permaneça alinhado com a build do servidor.

## O que é plano de reversão? Os backups dos meus dados são mantidos?

O plano de reversão serve para restaurar o sistema com o backup mais recente disponível. Os backups são armazenados por 7 dias para clientes do data center e por 14 dias para clientes no Amazon Web Service (AWS).

## Quanto tempo levará para reverter?

Depende do tamanho do backup do banco de dados. O tempo médio de conclusão é de 4 horas.

## Que tipos de testes são realizados no meu sistema após a atualização?

Consulte a lista de verificação de atualização da [compilação abaixo](#check-list).

## Que tipo de teste devo fazer após a atualização?

Os ambientes de desenvolvimento e de estágio são atualizados em sequência ou em conjunto, mas é necessário fazer logoff antes de atualizar a instância de produção. Isso permite que cada cliente realize testes minuciosos antes de desconectar quaisquer alterações na produção.

Consulte a lista de verificação de atualização de [compilação de lista abaixo](#check-list). Os clientes devem executar testes semelhantes, bem como outros que possam precisar para o ambiente.

## Com que frequência preciso executar uma atualização de build?

A fim de garantir o desempenho, a disponibilidade e a segurança ideais do sistema, o Adobe fará uma parceria com os clientes para garantir que os sistemas sejam atualizados pelo menos uma vez por ano.

## Haverá um desligamento para uma atualização de build?

Sim. O servidor é desligado durante uma atualização para garantir que a integridade dos dados seja preservada enquanto o produto é atualizado. Depois de concluído, ele é reiniciado e todos os serviços são reiniciados.

## Com quem devo entrar em contato para abrir o tíquete de atualização de build?

Se você enfrentar problemas após uma atualização de criação, entre em contato com o Atendimento [ao cliente da](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)Adobe. O Atendimento ao cliente agendará as datas de criação e abrirá tíquetes relacionados à atualização da compilação.

Saiba mais sobre as opções de [Ajuda e suporte para o Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)

## Criar lista de verificação de atualização {#check-list}

### Lista de verificação de pós-atualização do servidor de mensagens em nuvem

1. Enviar um delivery de teste
   1. Validar os logs do delivery e o fluxo de trabalho relacionado
   1. Validar os logs de rastreamento que são atualizados
   1. Validar links de mirror page e rastreamento
1. Confirmar se todos os workflows técnicos estão no estado iniciado
1. Verifique se todos os processos também estão ativos

### Lista de verificação pós atualização do servidor de marketing

* Você pode fazer login no servidor? Verifique se o Console do cliente da Campanha está funcionando sem nenhum pop-up de erro/aviso.
* Certifique-se de usar a mesma versão do console da versão de compilação após a atualização.
* Você tem algum aplicativo da Web que insira dados no banco de dados de Campanha? Em caso afirmativo, execute-os e verifique se eles podem inserir novos registros por meio da API.
* Você pode enviar um email de teste com êxito? Crie um novo delivery usando um modelo conhecido, envie-o para um recipient de teste, verifique a personalização, desfaça o vínculo, mirror page todo o trabalho.
* Todos os seus workflows de caminho críticos estão em execução? Verifique workflows, abra o journal do fluxo de trabalho e verifique se não há erros.
* Todas as pastas estão presentes, visíveis e acessíveis? Navegue por pastas diferentes e verifique.
todo o conteúdo é exibido e está presente.
* Seus delivery estão passando com o fuso horário correto?

   * Verificar a data de criação e a data de modificação com o carimbo de data e hora e o fuso horário
   * Verifique se a execução do scheduler funciona em um fluxo de trabalho no horário especificado
   * Procure a lista de workflows que estão em estado PAUSED e FAILED. Start e monitore-os
   * Executar teste AB para um cenário
   * Testar notificações por push junto com a funcionalidade de rastreamento para deep links
   * Testar envio de SMS
   * Se você tiver algum FDA externo conectado, teste se os dados estão sendo enviados de ambas as maneiras
   * Se você usar integrações como Adobe Campaign-Adobe Experience Manager, Adobe Campaign-Adobe Analytics, teste se elas ainda funcionam como antes

**Consulte também**

* [Atualização de uma build](../../production/using/build-upgrade.md)
* [Notas de versão do Campaign Classic ](../../rn/using/rn-overview.md)
* [Opções de ajuda e suporte para Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Programa Gold Standard](https://helpx.adobe.com/br/campaign/kb/gold-standard.html)