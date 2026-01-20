---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---
# 🚀 PROMPT DE DEMONSTRAÇÃO - Análise da documentação do v7 para v8

**Copie e cole este prompt inteiro no Cursor/ChatGPT para analisar qualquer pasta v7**

&#x200B;---

## 📋 O PROMPT (COPIAR DAQUI) ⬇️

```markdown
# Campaign v7 Documentation Analysis

Analyze the v7 documentation folder and generate a detailed Markdown report with recommendations.

---

## CONTEXT

**v7 Repository**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/`  
**v8 Repositories**:
- `/Users/florentvignes/Documents/GitHub/campaign.en/` (Campaign v8)
- `/Users/florentvignes/Documents/GitHub/campaign-web.en/` (Campaign Web UI v8)

---

## TARGET FOLDER

**Analyze this folder**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/help/delivery/using/`

*(Replace with any folder: workflow, web, platform, reporting, etc.)*

---

## FEATURE PARITY CONTEXT

### v7-Specific Features (NOT in v8 FFDA)
- **Coupons** (personalized-coupons.md)
- **MRM** (Marketing Resource Management)
- **Surveys** (online surveys)
- **Distributed Marketing**
- **Mid-sourcing** (on-premise setup)
- **SpamAssassin** (on-premise spam filtering)
- **On-premise/Hybrid** configurations

### v8 Documentation Structure
- **Campaign Web UI**: `/campaign-web.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign-web/v8/
- **Campaign v8**: `/campaign.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/

---

## OUTPUT FORMAT

Generate a complete Markdown report with this structure:

### 1. HEADER & SUMMARY
\`\`\`markdown
# 📊 v7 [Folder Name] Analysis

**Folder**: `/help/[folder]/using/`  
**Generated**: [Date]  
**Total Files**: [X]

## 📈 Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| 📄 Total Files | X | 100% |
| ✅ KEEP | X | X% |
| 🗑️ DELETE | X | X% |
| ➡️ MOVE | X | X% |
| 🔍 REVIEW | X | X% |
\`\`\`

### 2. FILE-BY-FILE ANALYSIS TABLE
\`\`\`markdown
## 📋 Complete File Analysis

### [Category Name] (X files)

| # | v7 File | v8 Match | Match % | Notes | Action |
|---|---------|----------|---------|-------|--------|
| 1 | filename.md | [v8 link](https://...) | 95% | Fully in v8 | 🗑️ DELETE |
| 2 | **filename.md** | NONE | 0% | **v7-specific** | ✅ **KEEP** |
| 3 | filename.md | [v8 link](https://...) | 70% | Migrate tips | ➡️ MOVE |

[Repeat for each category: Get Started, Email, SMS, etc.]
\`\`\`

### 3. MUST KEEP SECTION
\`\`\`markdown
## ✅ Must Keep - v7-Specific Features

| File | Reason | Badge Text |
|------|--------|------------|
| filename.md | Feature not in v8 FFDA | "This feature is not available..." |
\`\`\`

### 4. QUICK WINS SECTION
\`\`\`markdown
## 🗑️ Quick Wins - Safe to Delete Now

**[Category]** (X files):
- ✅ filename.md → 95% in v8/path
- ✅ filename.md → 90% in v8/path
\`\`\`

### 5. MIGRATION SECTION
\`\`\`markdown
## ➡️ Content to Migrate First

| v7 File | v8 Destination | Content to Migrate | Effort |
|---------|----------------|-------------------|--------|
| filename.md | /v8/path.md | Sections X, Y, Z | 2 hours |
\`\`\`

### 6. EXECUTION PLAN
\`\`\`markdown
## 🎯 Execution Plan

### Week 1: Quick Deletions
- [ ] Delete [category] files (X)
- [ ] Delete [category] files (X)
**Total**: X files deleted

### Week 2: Badging
- [ ] Badge v7-specific files (X)

### Week 3: Review
- [ ] Review partial matches (X)
\`\`\`

---

## ANALYSIS RULES

### For Each File, Determine:

1. **Match Percentage**:
   - 95-100% = Fully covered in v8 → DELETE
   - 70-90% = Mostly covered, check gaps → DELETE or MOVE
   - 40-70% = Partial coverage → REVIEW
   - 0-40% = Not in v8 → KEEP or REVIEW

2. **v7-Specific Indicators** (→ KEEP):
   - Mentions "on-premise", "hybrid", "mid-sourcing"
   - Coupons, MRM, Surveys, Distributed Marketing
   - SpamAssassin, nlserver configuration
   - Client Console specific features
   - Database schema/structure docs

3. **DELETE Criteria**:
   - Basic features (email, SMS, push creation)
   - Standard workflow activities (query, split, enrichment)
   - Common reports
   - Channel basics fully documented in v8

4. **MOVE Criteria**:
   - Troubleshooting tips not in v8
   - Best practices missing in v8
   - Advanced patterns useful for v8
   - Good examples/use cases

5. **REVIEW Criteria**:
   - Partial v8 coverage (50-70%)
   - Unclear if feature exists in v8
   - Complex mixed content

---

## IMPORTANT

- **Organize by category** (Get Started, Email, SMS, Push, etc.)
- **Include Experience League URLs** for v8 matches
- **Bold v7-specific files** that must be kept
- **Estimate match percentage** for each file
- **Provide clear reasoning** for each decision
- **Include effort estimates** for migrations

---

Generate the complete Markdown report now.
```

&#x200B;---

## 🎯 INSTRUÇÕES DE DEMONSTRAÇÃO

### Etapa 1: mostrar o prompt1. Abrir este arquivo (`DEMO-PROMPT-STANDALONE.md`)2. Role até a seção &quot;THE PROMPT&quot;3. Diga: *&quot;Este é o nosso prompt de análise automatizada&quot;*

### Etapa 2: Copiar o prompt1. Selecione tudo, desde &quot;# Análise de documentação do Campaign v7&quot; até o fim2. Copiar para a área de transferência3. Diga: *&quot;Acabei de copiar o prompt inteiro...&quot;*

### Etapa 3: Colar e executar1. Abrir Cursor2. Cole o prompt3. Diga: *&quot;...e cole-o no Cursor&quot;*4. Pressionar Enter

### Etapa 4: Mostrar resultados1. Aguardar a geração (~30-60 segundos)2. Rolar pelo relatório gerado3. Destacar seções principais:   - Estatísticas do resumo de 📊   - 📋 Tabela arquivo por arquivo   - ✅ Deve manter a seção   - 🗑️ Vitórias rápidas   - 🎯 Plano de execução

### Etapa 5: Momento Uau1. Mostrar a visualização da marcação2. Aponte:   - *&quot;111 arquivos analisados automaticamente&quot;*   - *&quot;67 arquivos seguros para exclusão (60% de redução)&quot;*   - *&quot;18 arquivos específicos v7 identificados&quot;*   - *&quot;Concluir plano de execução com linhas do tempo&quot;*

&#x200B;---

## DICAS DE DEMONSTRAÇÃO DO 💡

### Tornar interativo&#x200B;**Pergunte ao público-alvo**: *&quot;Qual pasta devemos analisar?&quot;*- entrega ✅ (111 arquivos - impressionante)- fluxo de trabalho ✅ (121 arquivos - ainda maior)- web ✅ (26 arquivos - demonstração rápida)- relatórios ✅ (32 arquivos - rápido)

### Personalizar em tempo real&#x200B;**Mostrar flexibilidade**: alterar o caminho da pasta no prompt:

```
/help/workflow/using/  → Analyze workflows
/help/web/using/       → Analyze web apps
/help/platform/using/  → Analyze platform
```

### Realçar os principais recursos1. **Automação**: *&quot;Nenhum trabalho manual necessário&quot;*2. **Precisão**: *&quot;Usa a documentação do v8 para comparação&quot;*3. **Acionável**: *&quot;Plano pronto para executar com caixas de seleção&quot;*4. **Smart**: *&quot;Identifica automaticamente recursos específicos do v7&quot;*

### Comparação de tempo&#x200B;**Antes**: *&quot;Análise manual = 2-3 dias por pasta&quot;*\**Depois**: *&quot;Análise automatizada = 30 segundos por pasta&quot;*

**ROI**: *&quot;21 pastas × 2 dias = 42 dias → 15 minutos&quot;*

&#x200B;---

## 📊 VISUALIZAÇÃO DE SAÍDA ESPERADA

```markdown
# 📊 v7 Delivery Analysis

**Total Files**: 111

## 📈 Summary
| Metric | Count | Percentage |
|--------|-------|------------|
| ✅ KEEP | 18 | 16% |
| 🗑️ DELETE | 67 | 60% |
| ➡️ MOVE | 8 | 7% |
| 🔍 REVIEW | 18 | 17% |

## 📋 File Analysis

### 📧 Email (18 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | 🗑️ DELETE |
| 2 | creating-an-email-delivery.md | campaign-web/v8/email/create | 95% | 🗑️ DELETE |

### 📱 SMS (7 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | sms-channel.md | campaign-web/v8/msg/send-sms | 90% | 🗑️ DELETE |
| 2 | **sms-set-up-mid.md** | NONE | 0% | ✅ **KEEP** |

[... continues for all categories ...]

## ✅ Must Keep (18 files)
- **personalized-coupons.md** - Coupons not in v8 FFDA
- **sms-set-up-mid.md** - Mid-sourcing (on-prem)
- **spamassassin.md** - On-prem spam filtering

## 🗑️ Quick Wins (67 files)
Email basics, SMS, Push, Direct mail → All in v8

## 🎯 Execution Plan
Week 1: Delete 67 files (60%)
Week 2: Badge 18 files
Week 3: Review 18 files
```

&#x200B;---

## SCRIPT DE DEMONSTRAÇÃO 🎬

**Abrindo**:
> &quot;Hoje, mostrarei como automatizamos a reorganização da documentação do v7 usando IA. Isso costumava levar semanas, agora leva minutos.&quot;

**Problema**:
> &quot;Temos mais de 1.500 arquivos de documentação v7. Muitos são duplicados na v8. Precisamos identificar o que manter, excluir ou migrar.&quot;

**Solução**:
> &quot;Criamos um prompt inteligente que analisa qualquer pasta e gera recomendações acionáveis.&quot;

**Demonstração**:
> &quot;Deixe-me mostrar-lhe. Vou analisar a pasta &#39;delivery&#39; com 111 arquivos...&quot;
> 
> [Copiar prompt, colar, executar]
> 
> &quot;...e em 30 segundos, obtemos uma análise completa.&quot;

**Resultados**:
> &quot;Veja isso:
> - 67 arquivos a serem excluídos (60% de redução)
> - 18 arquivos específicos v7 identificados
> - 8 arquivos a serem migrados
> - Plano de execução completo de 3 semanas
> 
> Tudo automatizado. Tudo correto.&quot;

**Fechar**:
> &quot;Esse mesmo processo funciona para todas as 21 pastas. O que costumava levar 6 semanas agora leva 15 minutos.&quot;

&#x200B;---

## 🚀 PRONTO PARA A DEMONSTRAÇÃO.

**Somente**:
1. Abrir este arquivo
2. Copiar o prompt
3. Colar no cursor
4. Mostre a mágica ✨

**Tempo total de demonstração**: 3-5 minutos\
**Fator de Uau**: 🔥🔥🔥

