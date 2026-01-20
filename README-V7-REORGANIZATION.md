---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---
# Kit de reorganização da documentação do 📚 v7

**2 prompts para análise e organizador la doc v7 → v8**

&#x200B;---

## 📁 Fichiers

### 🔍 Prompts (Instruções)

| Fichier | Descrição | Output |
|---------|-------------|--------|
| `PROMPT-1-OVERVIEW-ALL-FOLDERS.md` | Vue d&#39;ensemble de TOUS les folders v7 | `v7-reorganization-overview.md` |
| `PROMPT-2-DETAILED-FOLDER.md` | Analisar correspondência de % avec da pasta détaillée d&#39;UN | `[folder]-detailed-analysis.md` |

&#x200B;---

## Utilização de 🚀

### 1️⃣ Vue d&#39;Ensemble (tous les folders)

```bash
# 1. Ouvrir le prompt
open PROMPT-1-OVERVIEW-ALL-FOLDERS.md

# 2. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 3. Coller dans Cursor/ChatGPT
# 4. Obtenir : v7-reorganization-overview.md
```

**Génère** :
- 📊 Resumo executivo (estatísticas globais)
- 📁 Analisar as 21 pastas do des
- 🎯 Matrice de priorization
- ✅ itens de ação
- ⚠️ Riscos
- 📈 Métricas

**Alvo** : ~50-60 páginas Markdown

&#x200B;---

### 2️⃣ a pasta Analyze Détaillée d&#39;un

```bash
# 1. Ouvrir le prompt
open PROMPT-2-DETAILED-FOLDER.md

# 2. Modifier la ligne :
📁 **Analyze**: /Users/.../help/delivery/using/

# 3. Remplacer par le folder souhaité :
# - /help/delivery/using/
# - /help/workflow/using/
# - /help/web/using/
# - etc.

# 4. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 5. Coller dans Cursor/ChatGPT
# 6. Obtenir : [folder]-detailed-analysis.md
```

**Génère** :
- 📊 Status da pasta
- 📋 Tableau détaillé organisé comme Experience League
- 🔗 Cliques do Liens (v7 + Experience League)
- 📈 Jusqu&#39;à 3 combina com v8 par fichier avec %
- 📄 Recapitulação de arquivo par file
- 🎯 Plano de reorganização
- ✅ Caixas de seleção para rastreamento

**Alvo** : ~30-40 páginas Markdown

&#x200B;---

## 📊 Exemplo de saída

### Prompt 1 (visão geral)

```markdown
# 📊 v7 Documentation Reorganization Overview

**Total Files**: 1,500
**KEEP**: 400 (27%)
**DELETE**: 800 (53%)
**MOVE**: 200 (13%)
**REVIEW**: 100 (7%)

## 📁 Folder Analysis

### 🟢 100% KEEP - v7-Only Content
| Folder | Files | Reason |
|--------|-------|--------|
| /installation/ | 75 | On-premise setup |
| /mrm/ | 5 | Not in v8 FFDA |
...
```

### Prompt 2 (Pasta detalhada)

```markdown
# 📊 v7 Folder Analysis: Delivery

**Total Files**: 111

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | Notes | Action |
|---|---------|------------|---|------------|---|-------|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | - | - | Fully in v8 | 🗑️ DELETE |
| 9 | sms-set-up-mid.md | NONE | 0% | - | - | Mid-sourcing (on-prem) | ✅ KEEP |
...
```

&#x200B;---

## 🎯 Fluxo de trabalho recomendado

### Semana 1 : Vue d&#39;ensemble1. Exécuter **Prompt 1** → Obtenir `v7-reorganization-overview.md`2. Identificador les folders prioritaires3. Partes interessadas do Partager avec

### Semaine 2-4 : Analisar détaillée1. Prioridade de pasta do cartão de memória:   - Exécuter **Prompt 2**   - Obtenir `[folder]-detailed-analysis.md`   - Valider les Decisions   - Iniciador menos ações

### Semaine 5+ : Execução1. Supprimer les fichiers identifiés (DELETE)2. Badger les fichiers somente v7 (KEEP)3. Migrer le contenu manquant (MOVER)4. Revisor les cas ambigus (AVALIAÇÃO)

&#x200B;---

## 💡 Dicas

### Despejar menos prompts- ✅ Copiadora/coleira l&#39;intégralité du prompt- ✅ Formato le do modificador Ne pass- ✅ Segmento do adaptador le chemin du folder (Prompt 2)

### Despejar menos saídas- 📝 Output en Markdown (pas HTML)- 🔗 Automáticas de linhas de cliques- ✅ Caixas de seleção para rastreamento- 📊 Estatísticas definidas pourcentages- 🎨 Emojis et icônes

### Pour l&#39;analyze- 🎯 pastas do Commerce par les gros (entrega, fluxo de trabalho)- ⚡ Prioriser les quick wins (95-100% de correspondência)- 🔍 Manual do revisor les cas ambigus (&lt;70% de correspondência)- ✅ Valider avec SME avant supressão maciça

&#x200B;---

## ⚠️ Importante

### Avant de supprimer1. ✅ Vérifier l&#39;équivalent v82. ✅ Vérifier qu&#39;il n&#39;y a pas de contenu v7-specific3. ✅ Metros à hora `redirects.csv`4. ✅ Valider avec un expert (pour les premiers)

### Pour les fichiers somente v71. ✅ Ajouter un badge au début du fichier2. ✅ Expliquer pourquoi c&#39;est somente v73. ✅ Limitações do Lien vers v8

&#x200B;---

## Suporte do 🆘

**Perguntas** ?
- Prompt ne fonctionne pas → Vérifier les chemins des repos
- Output trop long → Demander un currsumé
- Besoin d&#39;aide → Ping l&#39;équipe doc

&#x200B;---

**Dernière mise à jour** : 13/01/2026

