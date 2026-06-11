========================================
  ANNUAIRE DU PERSONNEL - INSTRUCTIONS
========================================

FICHIERS FOURNIS
----------------
  index.html      → Application web (ouvrir dans un navigateur)
  personnel.json  → Données initiales du personnel
  README.txt      → Ce fichier

DÉPLOIEMENT SUR INTRANET (pour l'informaticien)
-------------------------------------------------
1. Copier les deux fichiers (index.html + personnel.json)
   dans le même dossier sur le serveur web :
   - Apache : /var/www/html/annuaire/
   - Nginx   : /usr/share/nginx/html/annuaire/
   - IIS     : C:\inetpub\wwwroot\annuaire\

2. Accès via navigateur :
   http://[adresse-intranet]/annuaire/

3. Aucune installation supplémentaire requise.
   Le site fonctionne sans PHP, Node.js ou base de données.

FONCTIONNEMENT DES DONNÉES
---------------------------
- Au premier chargement, les données sont lues depuis personnel.json
- Les modifications (ajout, édition, suppression) sont ensuite
  sauvegardées dans le navigateur local (localStorage)
- IMPORTANT : chaque utilisateur a ses propres données locales.
  Les modifications d'un utilisateur ne sont PAS visibles par les autres.

POUR UNE BASE DE DONNÉES PARTAGÉE (optionnel)
----------------------------------------------
Pour que tout le monde voie les mêmes données en temps réel,
il faut ajouter un backend. Options possibles :

Option A — API REST simple (recommandée)
  - Créer un petit serveur Node.js ou PHP
  - Remplacer les appels localStorage dans index.html
    par des appels fetch() vers votre API
  - Stocker les données dans MySQL ou PostgreSQL

Option B — Fichier JSON centralisé (lecture seule)
  - Mettre à jour personnel.json manuellement sur le serveur
  - Les utilisateurs verront les données à jour au rechargement
  - Les ajouts/modifications via l'interface ne seront pas partagés

PERSONNALISATION
-----------------
- Pour modifier les services disponibles : chercher "SERVICES" dans index.html
- Pour modifier les rôles disponibles : chercher "ROLES" dans index.html
- Pour changer le nom de l'hôpital : chercher "Annuaire du Personnel" dans index.html

COMPATIBILITÉ NAVIGATEURS
--------------------------
Testé et compatible avec :
  Chrome 90+, Firefox 88+, Edge 90+, Safari 14+

CONTACT
-------
Application générée avec Claude (Anthropic)
Pour toute modification, contacter votre service informatique.
