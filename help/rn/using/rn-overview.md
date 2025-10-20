---
product: campaign
title: Introdução às atualizações
description: Saiba mais sobre as atualizações do Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: 7a05fdff-8f9d-4e8d-812e-0f1509db5499
source-git-commit: d56038fc8baf766667d89bb73747c20ec041124c
workflow-type: ht
source-wordcount: '894'
ht-degree: 100%

---

# Atualizações da versão {#rn-overview}

O Adobe Campaign Classic lança periodicamente atualizações de produtos que trazem novos recursos, correções de erros e melhorias de desempenho, segurança e usabilidade. Essas atualizações são lançadas como **builds de produto**. Informações detalhadas sobre cada nova build estão disponíveis nas [Notas de versão](latest-release.md).

<!--
## Product versions

For Campaign, the version naming is the following:

1. Campaign Major version are v7 and v8.
1. A Minor version is a sub-version of a Major version. For example: v7.3, v7.4.
1. A Patch version is a post-release fix. For example: v7.3.2, v7.3.3.


Aligned with this naming, Campaign has 3 types of upgrades:

1. Major Upgrades - A major upgrade is an upgrade to a new version of Adobe Campaign (ex: v7 to v8)
1. Minor Upgrades - A minor upgrade brings new features, enhancements and fixes (ex: 7.4.X to 7.5.X)
1. Patch Upgrades - A patch upgrade includes fixes only (ex: 8.5.1 to 8.5.2)
-->

## Status da versão {#rn-statuses}

Cada nova build vem com um status identificado por uma cor nas [Notas de versão](latest-release.md).

| Status | Descrição |
|---|---|
| [!BADGE Disponibilidade geral]{type=Positive} | Build estável mais recente, validada em produção e recomendada pela Adobe. |
| [!BADGE Disponibilidade limitada]{type=Informative} | implantação somente sob demanda. |
| [!BADGE Obsoleto]{type=negative} | Nenhuma implantação. Nenhuma correção de erro. As implementações atuais devem ser atualizadas. |

## Ciclo da versão {#rn-cycle}

O Adobe Campaign é atualizado regularmente. Essa frequência regular de atualizações tem como objetivo disponibilizar a você as mais recentes e melhores atualizações, além de manter seu ambiente protegido e melhorar sua experiência com nosso produto.

É por isso que acreditamos ser essencial **executar a build estável mais recente** do Adobe Campaign. Ela também garantirá que você obtenha uma melhor experiência de suporte, já que geralmente é bem mais rápido identificar, reproduzir e corrigir um problema em um build recente. Além disso, muitos problemas que você pode encontrar já foram corrigidos nos builds mais recentes.

Como cliente hospedado, você se beneficia automaticamente da atualização com a última build estável, sem realizar nenhuma ação. Saiba mais na [seção de Atualização anual](#yearly-upgrade). Ao migrar de uma build antiga, a Adobe recomenda atualizar primeiro para essa build.

## Recomendações {#rn-recommendations}

Para garantir uma configuração estável, a Adobe recomenda instalar **o mesmo build** em todos os servidores que estão sendo executados na mesma configuração de cliente.

Além disso, exceto quando mencionado o contrário nas [Notas de versão](latest-release.md), o console do cliente deve estar na **mesma build** que a instância do servidor.

Para manter sua implementação atualizada, leia os [recursos obsoletos e removidos](../../rn/using/deprecated-features.md) e as páginas sobre [matriz de compatibilidade](../../rn/using/compatibility-matrix.md) a cada nova versão.

## Processo para atualização{#process-upgrade}

Como cliente hospedado do Managed Services ou híbrido, entre em contato com o atendimento ao cliente da Adobe para atualizar seu ambiente.

Como cliente no local, você pode fazer a atualização. Para fazer isso, [baixe o build estável mais recente (GA)](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html) e atualize todos os seus ambientes.

Saiba mais sobre o [processo de atualização](../../production/using/build-upgrade.md) e consulte as [perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md).

## Atualização anual {#yearly-upgrade}

A Adobe tem o compromisso de fornecer a você a melhor experiência e valor por meio de nossas soluções de software. A organização está comprometida em garantir que você tenha acesso às versões mais recentes da tecnologia que nossas soluções utilizam para executar suas tarefas.

O Adobe Campaign Classic, especificamente, usa uma variedade de tecnologias para fornecer valor. Essa combinação de tecnologias requer que você atualize regularmente suas instâncias do Campaign Classic, garantindo assim que as versões mais atualizadas estejam sendo usadas para oferecer segurança, estabilidade e melhor desempenho.

Como usuário convidado, você se beneficiará automaticamente da atualização com o build de GA mais recente sem realizar qualquer ação. Saiba mais nas perguntas frequentes abaixo.

### Por que minha empresa precisa dessa atualização?

Como cliente hospedado, a Adobe notificará você diretamente caso identifique que sua conta precise atualizar uma ou mais tecnologias relacionadas ao Campaign Classic e atualizar sua infraestrutura para a build atual (por exemplo, da v7.2.1 para a v7.3.3) e/ou versão (da v7 para a v8).

Como um cliente no local ou híbrido executando em uma build mais antiga, a Adobe incentiva você a migrar para a build estável (GA) mais recente.

Dessa forma, sua conta ficará protegida contra vulnerabilidades, além de contar com a tecnologia de desempenho atualizada. Você também poderá fazer atualizações regulares e com mais facilidade na sua conta, que exigirão menos trabalho e intervenção manual.

### Qual é o processo e a linha do tempo dessa atualização?

A equipe da Adobe está aqui para conduzir e orientar sua organização nessa jornada.

Uma equipe dedicada de representantes de atendimento ao cliente, gerentes de produto, engenheiros e especialistas em TechOps e consultores de produto está aqui para ajudar e garantir que a experiência seja tranquila.

### Benefícios

<tr>
  <td>
      <img alt="Segurança" src="assets/do-not-localize/security.png"/>
    <div>
    <strong>Segurança avançada</strong>
    </div>
    <ul>
    <li>Uma combinação de tecnologias usadas para potencializar o Adobe Campaign Classic trabalha em conjunto para agregar valor.</li>
    <li>Todas as instâncias devem ser atualizadas para garantir a segurança.</li>
    <li>A segurança precisa de foco constante e manutenção proativa.</li>
    <li>Os riscos de segurança estão presentes e não podem ser ignorados: cada atualização do Campaign Classic melhora a segurança.</li>
    </ul>
  </td>

<td>
      <img alt="Suporte" src="assets/do-not-localize/support.png" />
    <div>
    <strong>Suporte avançado</strong>
    </div>
    <ul>
    <li>A maioria dos problemas críticos é resolvida com atualizações e pode ser evitada.</li>
    <li>Atualizações regulares ajudam a reduzir os desafios enfrentados e aumentar a eficiência.</li>
    <li>O volume de atendimento ao cliente é reduzido, permitindo resoluções mais rápidas e mais atenção aos seus problemas que não estão relacionados a atualizações.</li>
    </ul>
  </td>
</tr>

<tr>
  <td>
      <img alt="Manutenção" src="assets/do-not-localize/maintenance.png"/>
    <div>
    <strong>Manutenção e estabilidade reforçadas</strong>
    </div>
    <ul>
    <li>Com o tempo, a equipe do Adobe Campaign identifica maneiras de melhorar a estabilidade e o desempenho do produto, bem como de corrigir problemas conhecidos.</li>
    <li>A atualização permite que sua instância esteja sempre alinhada a essas melhorias, eliminando desafios comuns enfrentados por organizações que estão enfrentando um rápido crescimento e/ou complexidade em suas instâncias do Campaign Classic.</li>
    <li>As melhorias na pilha de tecnologia que alimentam o Campaign Classic se refletem nas equipes de marketing e de TI da sua organização.</li>
    </ul>
  </td>

<td>
      <img alt="Atualização da build" src="assets/do-not-localize/upgrades.png" />
    <div>
    <strong>Atualizações mais fáceis</strong>
    </a>
    </div>
    <ul>
    <li>O esforço e a complexidade de atualizar a instância do Campaign Classic aumentam com a distância entre duas versões.</li>
    <li>Quanto mais sua organização esperar, mais complexa será a atualização (e maior será a exposição a vulnerabilidades).</li>
    <li>Atualizações regulares reduzirão o tempo de inatividade da atualização e reduzirão o risco de regressão.</li>
    </ul>
  </td>
</tr>
</table>

## Recursos adicionais{#support}

* [Encontre sua versão do Campaign](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).
* [Ajuda e suporte](../../support.md)
* [Versões do Painel de controle](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=pt-BR)
* [Recursos descontinuados e removidos](../../rn/using/deprecated-features.md)
* [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md)

Para ser informado sobre novos lançamentos de soluções da Experience Cloud, inscreva-se na [Atualização prioritária de produtos da Adobe](https://www.adobe.com/br/subscription/priority-product-update.html).
