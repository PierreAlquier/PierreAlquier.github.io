# Mettre à jour le site

Tout le contenu est dans le dossier **`_data/`**, un fichier par rubrique. Pour mettre le site à jour, vous modifiez le fichier concerné, vous faites `commit` + `push`, et GitHub Pages reconstruit le site tout seul en une ou deux minutes. Vous n'avez pas besoin de toucher au HTML.

| Fichier | Ce qu'il contient | Où ça apparaît |
|---|---|---|
| `_data/publications.yml` | livres, preprints, articles, thèses, divers | Publications + aperçu sur l'accueil |
| `_data/talks.yml` | exposés à venir et passés | Talks + accueil |
| `_data/students.yml` | doctorants actuels, anciens, mémoires de master | PhD students + accueil |
| `_data/service.yml` | responsabilités en cours et passées | Service + accueil |
| `_data/software.yml` | paquets R / Python | Software + accueil |
| `_data/teaching.yml` | cours, par année universitaire | Teaching + accueil |
| `_data/birds.yml` | espèces et photos de Singapour | Birds + accueil |
| `_data/birds_tokyo.yml` | hérons de Tokyo | page cachée `birds2.html`, accessible par un lien depuis Birds |
| `_data/career.yml`, `_data/training.yml` | carrière, diplômes | accueil |
| `_data/profile.yml` | nom, titre, phrase d'accroche, photo, bureau, e-mails, Bluesky | accueil |
| `_data/links.yml` | Google Scholar, ORCID… (`academic`) et réseaux sociaux (`social`) | Publications / accueil |
| `_data/nav.yml` | les onglets du menu | partout |

## Exemples

**Ajouter un article** : en haut de `publications.yml` (l'ordre du fichier est l'ordre d'affichage), copiez une entrée existante et modifiez-la :

```yaml
- type: paper
  title: Titre de l'article
  authors: '[G. Wolfer](https://geo-wolfer.gitlab.io), P. Alquier'
  venue: Bernoulli
  year: 2027
  status: to appear
  url: https://doi.org/10.xxxx/xxxxx
  details: 'Available on arXiv:[2402.10506](https://arxiv.org/abs/2402.10506).'
```

- `type` : `paper` (journaux et conférences, regroupés par année), `preprint`, `book`, `edited book`, `thesis` ou `misc`.
- Seuls `type` et `title` sont obligatoires : supprimez les lignes dont vous n'avez pas besoin.
- Quand un preprint est accepté, changez `type: preprint` en `type: paper` et ajoutez `venue`.

**Ajouter un exposé** : en haut de la liste `past:` (ou `upcoming:`) de `talks.yml` :

```yaml
- date: 2026/12/05
  text: 'Talk: ["Titre"](slides/fichier.pdf), [Nom du workshop](https://...), Lieu.'
  photos:
  - src: photos_moi/photo.jpg
```

Pour faire passer un exposé de « à venir » à « passé », coupez-collez l'entrée.

**Nouvelle année d'enseignement** : ajoutez un bloc en haut de `teaching.yml` :

```yaml
- year: 2027–2028
  courses:
  - institution: ESSEC
    course: '[Master DSBA](https://...) - Sequential Prediction and Optimization'
```

## Trois règles à connaître (format YAML)

1. **L'indentation compte** : deux espaces, jamais de tabulation. Copiez une entrée existante, c'est le plus sûr.
2. **Mettez le texte entre apostrophes** `'...'` dès qu'il contient `: ` (deux-points suivi d'un espace), qu'il commence par `[`, `*`, `"` ou `#`. Pour écrire une apostrophe à l'intérieur, doublez-la : `'Tsybakov''s 70th birthday'`. Dans le doute, mettez toujours des apostrophes.
3. **Les liens** s'écrivent `[texte](adresse)`, l'italique `*texte*` et le gras `**texte**`.

Si le site ne se met pas à jour après un `push`, regardez l'onglet **Actions** du dépôt GitHub : le message d'erreur indique le fichier et la ligne en cause (presque toujours une apostrophe ou une indentation).

## Le reste

- Mise en page : `_layouts/default.html` (en-tête et menu), une page `.html` par onglet, des petits gabarits dans `_includes/`.
- Couleurs et polices : en haut de `assets/site.css`.
- Les anciennes adresses `cv.html`, `packages.html` et `teachings.html` redirigent vers les nouvelles pages, pour que les liens existants continuent de marcher.
- Les fichiers `papers/`, `slides/`, `photos_moi/`, `photos_birds_2/`, `photos_birds/`, `notebooks/` sont inchangés. L'ancien `style.css` ne sert plus, vous pouvez le supprimer.
