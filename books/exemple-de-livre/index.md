---
title: Exemple de livre
description: Description simple de ce livre
excerpt: '"Extrait du livre."'
author: Nom de l'auteur
refChapters:
 - /exemple-de-livre/chapitres/1-chapitre-un/
 - books/exemple-de-livre/chapitres/1-chapitre-un/index.md
 - exemple-de-livre/chapitres/1-chapitre-un/1-1-chapitre-un-partie-un
 - exemple-de-livre/chapitres/1-chapitre-un/1-2-chapitre-un-partie-deux
 - books/exemple-de-livre/chapitres/1-chapitre-un/1-2-chapitre-un-partie-deux.md
---

*Exemple de livre*

# Exemple de livre 

Description détaillé de ce livre

## Gestion des chemins

Livre sans chapitres : 

```
book
 nom-du-livre
  index.md
  nom-de-la-page.md
```

Glob de pages : `book/**/*.md` 

- url : `book/nom-du-livre`
  repertoire : `book/nom-du-livre/index.md`
- url : `book/nom-du-livre/nom-de-la-page`
  repertoire : `book/nom-du-livre/nom-de-la-page.md`

Livre avec des chapitres :

```
book
  nom-du-livre
    index.md
    glossaire.md
    chapitre-1
      index.md
      page-1.md
      page-2
        index.md
        page-2-1
        page-2-3
        
```

Glob de livre : `book/*/index.md`
Glob de pages : `book/*/**/*.md` 
Glob de chapitres : `book/*/**/*.md` (on fonctionnel)

Note : un Glob de chapitre n'est pas forcément nécessaire, comme il est nécessaire d'avoir
un algorithme pour traiter les données avant affichage, exploiter cet algo pour simplifier 
la définition des données et determiner les chapitres à partir de leurs chemin (`*/chapitre-*/` ou `**/chapitres-/*` pour des sous-chapitres), ou à partir
d'un maqueur de layout dans le front-matter. Par exemple, un sommaire pourrais être automatiquement généré
si le repertoire possède un fichier `index.md`

Si le glob pattern ne fonctionne pas, tenter un truc
du genre `book/*/chapitre-*/*.md`

Considérer également, l'ajout de référence via l'API server.

- url : `book/nom-du-livre`
  repertoire : `book/nom-du-livre/index.md`
- url : `book/nom-du-livre/glossaire`
  repertoire : `book/nom-du-livre/glossaire.md`
- url : `book/nom-du-livre/chapitre-1/`
  repertoire : `book/nom-du-livre/chapitre-1/index.md`
- url : `book/nom-du-livre/chapitre-1/page-1`
  repertoire : `book/nom-du-livre/chapitre-1/page-1.md`

Autre solutions : 
 - Utiliser les jointure via méta
 - Générer des jointures via l'API du serveurs (relation automatique)
