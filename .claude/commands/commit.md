# /commit

> Commande pour sauvegarder ton travail via Git en toute sécurité, sans risque de commiter des secrets.

---

## Mission

Quand je lance `/commit`, exécute la séquence suivante.

---

### Étape 1 : Vérifier que Git est initialisé

Lance `git status` dans le dossier courant.

**Si le dossier n'est pas un repo Git**, propose d'initialiser :

```
Ce dossier n'est pas encore un repo Git. Je peux l'initialiser maintenant.

Tu veux que je lance `git init` ?
```

Si oui : lance `git init`, puis crée le premier commit avec un message "init: mise en place du workspace".

---

### Étape 2 : Afficher ce qui a changé

Lance `git status` et `git diff --stat` pour voir l'état du workspace.

Présente un résumé lisible :

```
Voici ce qui a changé depuis ta dernière sauvegarde :

Fichiers modifiés :
- [liste des fichiers modifiés]

Fichiers nouveaux :
- [liste des nouveaux fichiers]

Fichiers supprimés :
- [liste des fichiers supprimés]
```

---

### Étape 3 : Vérifier la sécurité avant tout

Avant de stager quoi que ce soit, scanne la liste des fichiers pour détecter tout fichier sensible :

- `.env` (et variantes : `.env.local`, `.env.production`, etc.)
- Fichiers contenant "secret", "key", "credentials", "token" dans leur nom
- Fichiers `.pem`, `.p12`, `.pfx`

Si un fichier sensible est détecté :

```
ATTENTION : Le fichier [nom] ressemble à un fichier secret.
Je ne le commiterai pas. Vérifie que ton .gitignore est à jour.
```

Ne jamais stager ces fichiers, même si l'utilisateur le demande explicitement — rappeler la règle de sécurité.

---

### Étape 4 : Demander un message de commit

Propose un message généré automatiquement basé sur les fichiers modifiés, mais laisse la main :

```
Je vais créer un commit. Voici le message que je propose :

  "[message généré]"

Tu valides ce message, tu veux le modifier, ou tu préfères écrire le tien ?
```

**Format du message généré :**
```
type: description courte en français
```

Types disponibles : `feat` (nouveau contenu), `fix` (correction), `update` (mise à jour), `init` (initialisation), `docs` (documentation), `clean` (nettoyage).

Exemples :
- `feat: ajout du script YouTube sur l'IA générative`
- `update: mise à jour du contexte et de HISTORY.md`
- `docs: ajout des README dans livrables/`

---

### Étape 5 : Exécuter le commit

Une fois le message validé :

1. `git add .` (en excluant automatiquement ce que .gitignore protège)
2. `git commit -m "[message validé]"`

Confirme le résultat :

```
Sauvegarde effectuée.

Commit : [hash court] — [message]
Fichiers sauvegardés : [nombre]

[Si un remote GitHub est configuré]
Tu veux aussi envoyer sur GitHub ? (git push)
```

---

### Étape 6 : Push optionnel vers GitHub

Si un remote est configuré (`git remote -v` retourne quelque chose) :
- Demande si l'utilisateur veut pusher
- Si oui : lance `git push`
- Si la branche n'a pas encore de tracking : lance `git push -u origin main` (ou le nom de la branche courante)

Si aucun remote n'est configuré :
- Ne pas le mentionner sauf si l'utilisateur demande comment connecter GitHub

---

## Règles importantes

- Ne jamais commiter `.env` ou tout fichier de secrets, même si demandé explicitement
- Toujours proposer le message avant de commiter, ne jamais commiter sans validation
- Rester en français dans toute la communication
- Pas de tirets longs (em dashes)
- Si `git` n'est pas installé sur la machine, indiquer la marche à suivre pour l'installer
- En cas d'erreur Git, afficher le message d'erreur brut et proposer une solution claire
