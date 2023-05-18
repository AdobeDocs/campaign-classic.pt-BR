---
product: campaign
title: Perguntas frequentes sobre atualização de build
description: Perguntas frequentes sobre atualizações de build do Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 85e2135d-a1a3-44f0-a4f9-de38db5c8726
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Perguntas frequentes sobre atualização de build {#build-upgrade-faq}



O Adobe Campaign é atualizado regularmente. Se você conhece as [Notas de versão](../../rn/using/rn-overview.md) publicadas, provavelmente sabe que a cada ano são lançadas em média 2/3 das versões secundárias, repletas de novos recursos, melhorias e correções. Além disso, periodicamente liberamos builds apenas com correções cumulativas. Essa frequência regular de atualizações tem como objetivo fazer com que você tenha disponível as atualizações melhores e mais recentes, além de manter seu ambiente totalmente protegido e de melhorar obviamente sua experiência com nosso produto.

É imprescindível que nossos clientes executem a versão mais recente do Adobe Campaign. Isso também nos permite ajudar com muito mais eficiência em caso de problemas. Identificar, reproduzir e corrigir um problema em uma build antiga geralmente leva mais tempo, sem mencionar que alguns problemas que você pode encontrar podem muito bem já terem sido corrigidos em uma nova versão da build.

Como usuário hospedado, você se beneficia automaticamente da atualização anual do Campaign com a versão estável mais recente, sem precisar de nenhuma ação. Clientes locais e híbridos também podem se beneficiar dessa versão. Se você migrar de uma compilação antiga, recomendamos atualizar primeiro para essa versão. [Saiba mais](../../rn/using/rn-overview.md).

## O que é uma atualização de build?

A atualização de build acontece quando o software do Adobe Campaign Classic é atualizado para o número de build seguro mais recente, permanecendo no mesmo nível de build principal/secundário. Por exemplo: Campaign Classic v7 build 9026 para Campaign v7 build 9032.

Saiba mais [nesta seção](../../rn/using/rn-overview.md).

## Qual é a versão mais recente do Adobe Campaign Classic?

A versão mais recente do Campaign Classic, incluindo novos recursos e documentação, está detalhada nas [Notas de versão](../../rn/using/latest-release.md) mais recentes.

## Como faço para saber qual versão estou executando?

Verifique sua versão no menu **[!UICONTROL Help > About...]** no console do Adobe Campaign Client. A caixa **[!UICONTROL About]** contém informações detalhadas sobre a versão e a build que você está executando, para o console e para o servidor.

Saiba mais [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## O que significa o status da build?

Desde o Campaign Classic 19.2, um status está associado a cada build 

Saiba mais [nesta seção](../../rn/using/rn-overview.md).

## Uma atualização de build é a mesma coisa que uma atualização de versão?

Não. Uma atualização de build é uma atualização incremental em determinada versão principal, enquanto que uma atualização de versão é uma alteração de uma versão principal para outra. As atualizações de build são diretas, pois normalmente não envolvem grandes alterações arquitetônicas, técnicas ou de modelo de dados.

Por outro lado, as atualizações de versão geralmente vêm com alterações técnicas significativas e, dependendo da profundidade da configuração de um determinado cliente, podem exigir alterações significativas na configuração e/ou reimplementação parcial.

Por exemplo, usando as informações do servidor da captura de tela na seção anterior:

* Uma atualização de build envolveria a mudança da build 6880 para qualquer build posterior a 6880. Por exemplo, v6.1.1 build 8222 para v6.1.1 build 8666

* Uma atualização de versão envolveria a mudança da versão 6.0.2 para qualquer versão mais recente que 6.0.2. Por exemplo: v6.0.1 build 2222 para v6.1.1 build 8666

## Devo fazer backup dos meus dados antes dessas atualizações?

A Adobe fará um backup do seu sistema antes de qualquer alteração. No entanto, se houver trabalho de personalização crítico que esteja em seu sistema de não produção (servidores de desenvolvimento ou de preparo temporário), é ALTAMENTE RECOMENDADO exportar esse trabalho como um pacote antes de qualquer atualização.

![](assets/do-not-localize/how-to-video.png) Para obter mais informações, [assista a este vídeo tutorial](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

## Quando ocorrerão as atualizações?

Será oferecido aos clientes um intervalo de datas para escolher. As alterações no sistema de produção não são realizadas em feriados.

As atualizações de build podem ser feitas de segunda a quinta-feira e as sextas-feiras são usadas apenas para instâncias não relacionadas à produção.

## Quanto tempo levará a atualização da build?

O tempo necessário para executar uma atualização de build depende de vários fatores:

* O tamanho do banco de dados a ser submetido a backup ou restaurado (a atualização de bancos de dados maiores requerem mais tempo)
* O tamanho dos ambientes (muitos de nossos clientes têm vários servidores diferentes que lidam com funções específicas, com ambientes maiores que exigem mais tempo para serem atualizados)
* A complexidade do sistema (alguns sistemas têm serviços e conexões mais dependentes para verificação, o que exige a verificação da estabilidade e do desempenho desses sistemas)

A atualização da build é um processo que se dá em duas etapas:

1. Preparação do sistema para atualização – levando em consideração as especificidades do seu ambiente, essa fase leva essencialmente a uma atualização totalmente qualificada em um ambiente que não seja de produção. Depois que o ambiente atualizado tiver sido destacado de um ponto de vista técnico e funcional, poderá ocorrer a fase 2. Esta primeira fase, dependendo dos fatores acima mencionados, pode demorar de alguns dias até algumas semanas.

1. A atualização propriamente dita – o ambiente de produção é atualizado. Esta fase é normalmente realizada em poucas horas. Para ambientes muito complexos é esperado um tempo de inatividade mais longo. Caso algo dê errado, uma estratégia de reversão é definida e pode ser executada.

Para saber mais, [consulte este documento](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html).

## Quais recursos são necessários para a atualização de build?

O processo de atualização de build requer os seguintes recursos:

* Adobe Architect – para as arquiteturas hospedadas ou de mensagens em nuvem/híbridas, o arquiteto deve entrar em contato com o Atendimento ao cliente.
* Gerenciador de projetos – hospedado: a equipe de hospedagem fará uma parceria com a equipe de Atendimento ao cliente e o cliente para coordenar a linha do tempo de atualização para todas as instâncias.
* Administrador do Adobe Campaign – hospedado: a equipe de hospedagem realiza a atualização.
* Operador do Adobe Campaign\usuário de marketing – o operador executa testes em instâncias de desenvolvimento, teste e produção.

## Como posso me preparar para a atualização de build?

Exporte qualquer trabalho que seja crítico e deva ser preservado em seus sistemas de desenvolvimento e armazenamento temporário. Para obter mais informações, [assista a este vídeo tutorial](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

Atualize seu conhecimento dos workflows e delivery de caminho críticos desenvolvidos em seus livros de execução (ou pela equipe/parceiro de consultoria), analisando a documentação fornecida à sua equipe ao final da implementação.

Identifique tempos de tráfego baixos ou de baixo volume que seriam ideais para janelas de manutenção, pois gerarão menor impacto nos negócios.

Revise nossa [lista de verificação de atualização de build abaixo](#check-list) e seus planos de teste e verifique se os recursos que podem executar esses testes estão disponíveis dentro de 24 a 48 horas da conclusão de uma atualização.

Para saber mais, [consulte este documento](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html).

## As atualizações de build podem ser realizadas à noite ou fora do horário comercial?

As atualizações podem ser realizadas fora do horário. É sempre recomendável atualizar o ambiente fora do horário comercial, quando nenhum usuário comercial estiver conectado à instância.

## Quais são os custos associados a uma atualização de build?

Não há custo para instalar a atualização de build para clientes hospedados. Se houver desenvolvimentos personalizados no sistema, o cliente precisará identificar os recursos necessários para testá-los após a atualização e corrigir quaisquer problemas neles encontrados.

## Haverá acesso à instância durante o processo de atualização?

Não. O servidor é desligado durante uma atualização para garantir que a integridade dos dados seja preservada enquanto o produto é atualizado. Depois de concluído, ele é reiniciado e todos os serviços são retomados.

## Os emails continuarão a ser enviados a partir do centro de mensagens durante o processo de atualização?

Quando ocorrer a atualização pelo centro de mensagens (RT), não serão enviados emails da instância. Observe que todos os processos interrompidos quando um sistema do Campaign é desligado são automaticamente retomados quando o sistema é reiniciado. Isso inclui deliveries ativos ou programados, e rastreamento e cálculos de métricas para deliveries enviados anteriormente.

## Os workflows continuarão em execução e enviarão os deliveries?

Não. Durante a atualização da build, o fluxo de trabalho e os serviços de email são interrompidos. Significa que os workflows não serão executados e os deliveries não serão enviados. Eles serão retomados assim que o sistema for reiniciado. No entanto, a Adobe recomenda que todos os workflows de caminho críticos sejam verificados após uma atualização para garantir que eles estejam em execução e em bom estado de funcionamento.

## Meus links de rastreamento ainda funcionam durante a atualização?

O rastreamento de links em emails que já foram enviados não funcionará durante a atualização porque todos os servidores serão interrompidos. Eles estarão operacionais novamente após a conclusão da atualização e a reinicialização dos servidores.

## Eu preciso estar disponível durante o processo de atualização de build?

Sim. Os clientes devem fornecer a Adobe um ponto de contato disponível durante ou imediatamente após a atualização da instância de produção.  A Adobe entrará em contato com esta pessoa por email, a menos que sejam feitos outros acordos. Isso garantirá uma transição tranquila e a validação imediata de tarefas essenciais. A Adobe entrará em contato com o cliente assim que a atualização de build for concluída para confirmação.

## Preciso atualizar o console do cliente?

Sim. O console do cliente deve estar na mesma build da instância do servidor. Depois que a atualização for concluída, o console do cliente deverá solicitar a atualização para a build mais recente para garantir que permaneça alinhado com a build do servidor.

## O que é plano de reversão? Os backups dos meus dados são mantidos?

O plano de reversão serve para restaurar o sistema com o backup mais recente disponível. Os backups são armazenados por 7 dias para clientes do data center e por 14 dias para clientes no Amazon Web Service (AWS).

## Quanto tempo levará para reverter?

Depende do tamanho do backup do banco de dados. O tempo médio de conclusão é de 4 horas.

## Que tipos de testes são realizados no meu sistema após a atualização?

Consulte abaixo a [lista de verificação de atualização de build](#check-list).

## Que tipo de teste devo fazer após a atualização?

Os ambientes de desenvolvimento e de estágio são atualizados em sequência ou em conjunto, mas é necessário fazer logoff antes de atualizar a instância de produção. Isso permite que cada cliente realize testes minuciosos antes de desconectar quaisquer alterações na produção.

Consulte abaixo a [lista de verificação de atualização de build](#check-list). Os clientes devem executar testes semelhantes, bem como outros que possam ser necessários ao ambiente.

## Com que frequência preciso executar uma atualização de build?

A fim de garantir o desempenho, a disponibilidade e a segurança ideais do sistema, a Adobe fará uma parceria com os clientes para garantir que os sistemas sejam atualizados pelo menos uma vez por ano.

## Haverá um desligamento para uma atualização de build?

Sim. O servidor é desligado durante uma atualização para garantir que a integridade dos dados seja preservada enquanto o produto é atualizado. Depois de concluído, ele é reiniciado e todos os serviços são retomados.

## Com quem devo entrar em contato para abrir o tíquete de atualização de build?

Se você enfrentar problemas após uma atualização de build, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). O Atendimento ao cliente agendará as datas de criação e abrirá tíquetes relacionados à atualização da build.

Saiba mais sobre as [opções de Ajuda e Suporte para o Campaign Classic](../../support.md)

## Lista de verificação de atualização de build {#check-list}

### Lista de verificação de pós-atualização do servidor de mensagens em nuvem

1. Enviar um delivery de teste
   1. Validar os logs do delivery e o workflow relacionado
   1. Validar se os logs de rastreamento estão atualizados
   1. Validar links de mirror page e rastreamento
1. Confirmar se todos os workflows técnicos estão no estado inicial
1. Verificar se todos os processos também estão ativos

### Lista de verificação pós atualização do servidor de marketing

* Você pode fazer login no servidor? Verifique se o console do cliente do Campaign está funcionando sem nenhum pop-up de erro/aviso.
* Use a mesma versão do console que a versão de build após a atualização.
* Você tem algum aplicativo da web que insira dados no banco de dados do Campaign? Em caso afirmativo, execute-os e
verifique se eles podem inserir novos registros por meio da API.
* Você pode enviar um email de teste com êxito? Crie um novo delivery usando um modelo conhecido, envie-o para
um recipient de teste, verifique a personalização, desfaça o vínculo, aplique mirror page a todo o trabalho.
* Todos os seus workflows de caminho críticos estão em execução? Verifique os workflows, abra o journal do workflow e verifique se há erros.
* Todas as pastas estão presentes, visíveis e acessíveis? Navegue por pastas diferentes e verifique se
todo o conteúdo é exibido e está presente.
* Seus deliveries estão com o fuso horário correto?

   * Verifique a data de criação e a data de modificação com o registro de data e hora e o fuso horário
   * Verifique se a execução do scheduler funciona em um workflow no horário especificado
   * Procure a lista de workflows que apresentam status PAUSED e FAILED. Inicie-os e monitore-os
   * Execute o teste AB para um cenário
   * Teste notificações por push junto com a funcionalidade de rastreamento para deep links
   * Teste de envio de SMS
   * Se você tiver algum FDA externo conectado, teste se os dados estão sendo enviados de ambas as maneiras
   * Se você usar integrações como Adobe Campaign-Adobe Experience Manager, Adobe Campaign-Adobe Analytics, verifique se elas estão funcionando.

**Consulte também**

* [Atualização de uma build](../../production/using/build-upgrade.md)
* [Notas de versão do Campaign Classic](../../rn/using/rn-overview.md)
* [Opções de ajuda e suporte para o Campaign Classic](../../support.md)
* [Programa de atualização anual](../../rn/using/rn-overview.md#yearly-upgrade)
