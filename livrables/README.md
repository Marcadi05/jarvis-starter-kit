# Livrables

Ce dossier contient **tout ce que Claude produit pour toi**. Rien n'y est mis manuellement — c'est la sortie du travail.

---

## Règle d'or

| Rôle | Emplacement |
|------|-------------|
| **Inputs** — documents que tu fournis (briefs, specs, exports, screenshots) | `context/import/` |
| **Outputs** — ce que Claude produit pour toi | `livrables/<thème>/` |

---

## Structure des sous-dossiers

```
livrables/
├── sites-web/       Sites et landing pages (HTML, Next.js, etc.)
├── applications/    Outils, scripts, automatisations
├── youtube/         Briefs vidéos, scripts, hooks, calendrier éditorial
├── cabinet/         Livrables pour le cabinet de conseil Chatflow
└── ecole/           Livrables pour l'Apreneur Académie
```

---

## Convention de nommage

```
AAAA-MM-JJ_nom-du-projet_version.ext
```

**Exemples :**
- `2026-06-04_landing-chatflow-v1.html`
- `2026-06-04_script-youtube-hook-ia_v2.md`
- `2026-06-04_programme-module3-academie.pdf`

**Règles :**
- Date ISO au début (permet le tri chronologique automatique)
- Kebab-case (tout en minuscules, tirets à la place des espaces)
- Version explicite si plusieurs itérations (`v1`, `v2`, `final`)
- Pas d'espaces, pas d'accents dans les noms de fichiers

---

## Workflow type

1. Tu déposes ton brief ou tes documents dans `context/import/`
2. Tu décris la tâche à Claude
3. Claude produit le livrable et le place dans le bon sous-dossier avec la convention de nommage
