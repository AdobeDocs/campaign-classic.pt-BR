---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 24%

---
# Reorganização da documentação do 📊 v7 - Visão geral

**Gerado**: 13/01/2026\
**Total de pastas**: 21\
**Total de arquivos**: ~1.500

&#x200B;---

## 📈 Resumo executivo

| Métrica | Contagem | Porcentagem |
|--------|-------|------------|
| 📄 **Total de arquivos** | 1.500 | 100% |
| ✅ **MANTER (específico da v7)** | 400 | 27% |
| 🗑️ **DELETE (na v8)** | 800 | 53% |
| ➡️ **MOVER (para v8)** | 200 | 13% |
| 🔍 **REVISAR (não limpar)** | 100 | 7% |

**🎯Redução estimada**: 60-75% (1.500 → 400-600 arquivos)

&#x200B;---

## Análise de pasta 📁 por prioridade

### 🟢 Prioridade 1: 100% MANTER - Recursos Somente v7

| Pasta | Arquivos | Motivo | Status do v8 | Ação |
|--------|-------|--------|-----------|--------|
| 📂 `/installation/` | 75 | Configuração no local/híbrida | Somente na nuvem no v8 | ✅ MANTER TUDO + selo |
| 📂 `/mrm/` | 5 | Gerenciamento de recursos de marketing | NÃO está no FFDA | ✅ MANTER TUDO + selo |
| 📂 `/surveys/` | 8 | Pesquisas online | NÃO está no FFDA | ✅ MANTER TUDO + selo |
| 📂 `/distributed/` | 7 | Marketing distribuído | NÃO está no FFDA | ✅ MANTER TUDO + selo |
| 📂 `/response/` | 5 | Gerenciamento de resposta | Status não claro | 🔍 VERIFIQUE E MANTENHA |
| 📂 `/migration/` | 8 | Migração v6.1 → v7 | Específico ao v7 | ✅ MANTER TUDO |
| **TOTAL** | **108** | **7%** | - | **Medalha como somente v7** |

&#x200B;---

### 🔴 Prioridade 2: 60-70% DELETE - Alta Duplicação

| Pasta | Total | MANTER | DELETE | MOVER | REVISÃO | Observações |
|--------|-------|------|--------|------|--------|-------|
| 📂 `/delivery/` | 111 | 18 (16%) | 67 (60%) | 8 (7%) | 18 (17 %) | Email/SMS/Push na v8 |
| 📂 `/workflow/` | 121 | 24 (20%) | 60 (50%) | 12 (10%) | 25 (20%) | Atividades comuns no v8 |
| 📂 `/reporting/` | 32 | 3 (10%) | 22 (70%) | 2 (6%) | 5 (14 %) | Relatórios reprojetados na v8 |
| 📂 `/platform/` | 61 | 12 (20%) | 34 (55%) | 5 (8%) | 10 (17%) | Recursos comuns no v8 |
| 📂 `/campaign/` | 11 | 2 (18 %) | 7 (64 %) | 1 (9%) | 1 (9%) | Gerenciamento de campanhas no v8 |
| **TOTAL** | **336** | **59** | **190** | **28** | **59** | **Alto potencial de redução** |

&#x200B;---

### 🟡 Prioridade 3: 30-50% MISTA - Análise Detalhada Necessária

| Pasta | Total | MANTER % | DELETE % | Observações |
|--------|-------|--------|----------|-------|
| 📂 `/configuration/` | 69 | 65% | 22% | Configurações de esquema/BD (principalmente v7) |
| 📂 `/production/` | 43 | 65% | 23% | Gerenciamento de servidor (principalmente v7) |
| 📂 `/integrations/` | 37 | 40% | 40% | Verificar disponibilidade do conector |
| 📂 `/interaction/` | 39 | 51% | 31% | Mecanismo de oferta (verificar v8) |
| 📂 `/web/` | 26 | 92% | 8% | Aplicativos da Web > Landing pages v8 |
| 📂 `/message-center/` | 16 | 60% | 30% | Mensagens transacionais |
| **TOTAL** | **230** | **~55%** | **~25%** | **Requer revisão pasta por pasta** |

&#x200B;---

## 🎯 Vitórias rápidas - Semana 1

### Exclusões de alta confiança (95-100% v8 correspondência)

| Pasta | Arquivos a serem excluídos | Impacto | Esforço |
|--------|----------------|--------|--------|
| 📂 `/delivery/` | 67 arquivos | 🔥🔥🔥 alta | 2 dias |
| 📂 `/workflow/` | 60 arquivos | 🔥🔥🔥 alta | 2 dias |
| 📂 `/reporting/` | 22 arquivos | Medium 🔥🔥 | 1 dia |
| 📂 `/platform/` | 34 arquivos | Medium 🔥🔥 | 1 dia |
| 📂 `/campaign/` | 7 arquivos | 🔥 Baixa | 0,5 dia |
| **TOTAL** | **190 arquivos** | **Redução de 53%** | **6.5 dias** |

**Exemplos**:
- ✅ `about-email-channel.md` → `campaign-web/v8/email`
- ✅ `sms-channel.md` → `campaign-web/v8/msg/send-sms`
- ✅ `query.md` (fluxo de trabalho) → `campaign/v8/automation/workflow/query`
- ✅ `about-workflows.md` → `campaign/v8/automation/workflow`

&#x200B;---

## 📋 Detalhamento detalhado da pasta

### 📂 Entrega (`/help/delivery/using/`) - 111 arquivos

| Categoria | Arquivos | MANTER | DELETE | MOVER | REVISÃO | Observações |
|----------|-------|------|--------|------|--------|-------|
| Introdução | 8 | 0 | 7 | 0 | 1 | Noções básicas do v8 |
| Email | 18 | 0 | 16 | 0 | 2 | Totalmente na v8 |
| SMS | 7 | 1 | 5 | 0 | 1 | Mid-sourcing = KEEP |
| Push | 9 | 0 | 8 | 0 | 1 | Totalmente na v8 |
| Correspondência direta | 4 | 0 | 4 | 0 | 0 | Na v8 |
| Personalização | 8 | 1 | 6 | 0 | 1 | Cupons = KEEP |
| Modelos | 6 | 0 | 6 | 0 | 0 | Na v8 |
| Teste AB | 11 | 0 | 10 | 0 | 1 | Na v8 |
| Monitoramento | 14 | 0 | 12 | 1 | 1 | Principalmente na v8 |
| Solução de problemas | 9 | 2 | 4 | 2 | 1 | Manter dicas no local |
| Capacidade de entrega | 8 | 3 | 4 | 0 | 1 | SpamAssassin = KEEP |
| Avançado | 9 | 11 | 5 | 5 | 8 | Misto |
| **TOTAL** | **111** | **18** | **67** | **8** | **18** | **60% pode ser excluído** |

**Deve Manter**:
- ✅ `personalized-coupons.md` - NÃO está no FFDA v8
- ✅ `sms-set-up-mid.md` - Mid-sourcing (no local)
- ✅ `spamassassin.md` - Filtragem de spam no local

**Exemplos de exclusão rápida**:
- 🗑️ `about-email-channel.md` → 95% em `campaign-web/v8/email`
- 🗑️ `creating-an-email-delivery.md` → 95% em `campaign-web/v8/email/create-email`
- 🗑️ `sms-channel.md` → 90% em `campaign-web/v8/msg/send-sms`

&#x200B;---

### 📂 Fluxo de trabalho (`/help/workflow/using/`) - 121 arquivos

| Categoria | Arquivos | MANTER | DELETE | MOVER | REVISÃO | Observações |
|----------|-------|------|--------|------|--------|-------|
| Introdução | 12 | 2 | 9 | 0 | 1 | Noções básicas do v8 |
| Direcionamento | 18 | 3 | 12 | 1 | 2 | Query/Split na v8 |
| Controle de fluxo | 15 | 2 | 10 | 1 | 2 | Comum na v8 |
| Atividades de ação | 24 | 4 | 16 | 2 | 2 | Mais na v8 |
| Atividades de evento | 8 | 1 | 6 | 0 | 1 | Na v8 |
| Atividades de MRM | 5 | 5 | 0 | 0 | 0 | NÃO está no FFDA |
| Técnico | 16 | 4 | 8 | 2 | 2 | Misto |
| Avançado | 12 | 3 | 4 | 3 | 2 | Padrões úteis |
| Casos de uso | 11 | 0 | 5 | 3 | 3 | Bons exemplos |
| **TOTAL** | **121** | **24** | **60** | **12** | **25** | **50% pode ser excluído** |

**Deve Manter**:
- ✅ Todas as atividades MRM (5 arquivos) - NÃO no v8 FFDA
- ✅ Configurações locais
- ✅ Fluxos de trabalho técnicos avançados

**Exemplos de exclusão rápida**:
- 🗑️ `query.md` → 95% em `campaign/v8/automation/workflow/query`
- 🗑️ `split.md` → 95% em `campaign/v8/automation/workflow/split`
- 🗑️ `enrichment.md` → 95% em `campaign/v8/automation/workflow/enrichment`

&#x200B;---

### 📂 Instalação (`/help/installation/using/`) - 75 arquivos

| Categoria | Arquivos | Ação | Observações |
|----------|-------|--------|-------|
| Instalação do servidor | 18 | ✅ MANTER | Somente no local |
| Configuração do Banco de Dados | 12 | ✅ MANTER | Somente no local |
| Configuração | 15 | ✅ MANTER | nlserver etc. |
| Rede | 8 | ✅ MANTER | Zonas de segurança |
| Integração | 10 | ✅ MANTER | LDAP, etc. |
| Solução de problemas | 8 | ✅ MANTER | Problemas no local |
| Documentação genérica | 4 | DELETE 🗑️ | Guia de início no v8 |
| **TOTAL** | **75** | **71 MANUTENÇÃO/4 DELETE** | **95% específico do v7** |

**Motivo**: v8 é somente nuvem, todos os documentos de configuração locais são específicos do v7.

&#x200B;---

### 📂 Web (`/help/web/using/`) - 26 arquivos

| Categoria | Arquivos | MANTER | DELETE | Observações |
|----------|-------|------|--------|-------|
| Aplicativos Web | 14 | 14 | 0 | Recursos avançados não estão na v8 |
| Formulários web | 8 | 8 | 0 | Mais de páginas de aterrissagem v8 |
| Páginas de destino | 2 | 0 | 2 | Páginas básicas no v8 |
| Editor HTML | 2 | 2 | 0 | Diferente da v8 |
| **TOTAL** | **26** | **24** | **2** | **92% específico do v7** |

**Motivo**: v7 tem estrutura completa de Aplicativos Web e v8 simplificou Páginas de Aterrissagem.

&#x200B;---

## Plano de ação ✅

### Semana 1: Exclusões de Alto Impacto- [ ] `/delivery/`: Excluir 67 arquivos (email, SMS, noções básicas de push)- [ ] `/workflow/`: Excluir 60 arquivos (atividades comuns)- [ ] `/reporting/`: Excluir 22 arquivos (relatórios padrão)- [ ] `/platform/`: Excluir 34 arquivos (recursos comuns)- [ ] `/campaign/`: Excluir 7 arquivos (gerenciamento de campanha)- **Total**: 190 arquivos excluídos (13% de redução)

### Semana 2: emblema específico do v7- [ ] `/installation/`: Arquivos de selo 71 como &quot;v7 somente no local&quot;- [ ] `/mrm/`: Arquivos de selo 5 como &quot;Não disponível no v8 FFDA&quot;- [ ] `/surveys/`: Arquivos de selo 8 como &quot;Não disponível no v8 FFDA&quot;- [ ] `/distributed/`: Arquivos de selo 7 como &quot;Não disponível no v8 FFDA&quot;- [ ] `/web/`: Marcar 24 arquivos como &quot;Aplicativos Web v7&quot;- **Total**: 115 arquivos com medalha

### Semana 3: migração de conteúdo- [ ] Migrar dicas de solução de problemas do `/delivery/` para o v8- [ ] Migrar práticas recomendadas de fluxo de trabalho para v8- [ ] Migrar padrões avançados do `/platform/` para v8- **Total**: 40 arquivos migrados e excluídos

### Semana 4: Revisão Manual- [ ] Revisar `/configuration/` conteúdo misto- [ ] Revise a disponibilidade do conector `/integrations/`- [ ] Revisão `/interaction/` cobertura do mecanismo de oferta- [ ] Revisar o status do recurso `/response/`- **Total**: 50 arquivos revisados e decididos

&#x200B;---

## 📊 Resultados esperados

| Fase | Arquivos afetados | % cumulativa |
|-------|----------------|--------------|
| Semana 1: Exclusões | 190 | 13% |
| Semana 2: Insígnia | 115 | 20% |
| Semana 3: Migração | 40 | 23% |
| Semana 4: Revisão | 50 | 26% |
| **TOTAL** | **395** | **26% processado** |

**Restante**: ~1.100 arquivos para processar nas fases subsequentes

**Meta final**: 1.500 → 400-600 arquivos (redução de 60-73%)

&#x200B;---

## 🎯 Métricas de sucesso

| Métrica | Target | Status |
|--------|--------|--------|
| Arquivos excluídos | 800+ (53%) | ⏳ pendente(s) |
| Arquivos com selo | Mais de 200 (13%) | ⏳ pendente(s) |
| Arquivos migrados | Mais de 200 (13%) | ⏳ pendente(s) |
| Links quebrados | 0 | ⏳ pendente(s) |
| Aprovação da parte interessada | ✅ | ⏳ pendente(s) |

&#x200B;---

**Última atualização**: 13/01/2026\
**Próxima revisão**: após a semana 1 da execução

