# Cadencio — vitrine et démo

Version publique avec 40 clients fictifs. Les essais restent dans le navigateur : aucun compte réel, aucune base de données, aucun appel à une IA et aucun paiement.

Le code du site se trouve dans `public/`. Il est indépendant du prototype connecté et n’a pas besoin d’un autre dépôt pour fonctionner. Le retour coach est préparé dans `public/demo/coach-return.js` : le bouton « Préparer mon retour » produit un message du coach au client, propose des questions et préserve les brouillons existants. Le coach relit et adapte son texte avant de le publier dans l’aperçu local.

## Publication automatique sur le Worker existant

Dans Cloudflare, relier ce dépôt au Worker **cadencio** avec Workers Builds :

- Branche de production : `main`
- Répertoire racine : `/`
- Commande de build : `npm run build`
- Commande de déploiement : `npm run deploy`
- Version de Node.js : 22 ou ultérieure

La configuration du Worker est dans `wrangler.json`. Les fichiers publiés sont dans `public/`. Aucun jeton Cloudflare ni fichier de secrets ne doit être ajouté au dépôt. Cloudflare gère les autorisations de son propre déploiement.

Une fois le dépôt relié au Worker existant, les changements de la branche de production déclenchent une mise à jour à la même adresse : https://cadencio.cadencio.workers.dev/

Documentation : https://developers.cloudflare.com/workers/ci-cd/builds/

## Essai local

Avec Node.js 22 ou ultérieure :

```sh
npm ci
npm run build
npm run preview
```

Le projet ne contient que la vitrine et la démonstration publique. Utiliser uniquement des données et documents de test.
