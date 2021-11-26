# Landing page La Fabrique

## Developpement


TIPS: ce repo contient un sous-module, pour cloner simplement :
`git clone --recursive url.git`

**Lancer le projet**
```sh
yarn
yarn dev
```
## Modifier vos contenus

Le dossier `/config-yml` contient l'ensemble des contenus de la landing page.

`/config-yml/commons` : contenus requis pour la landing (header / footer / navigation)

`/config-yml/legals` : contenus relatifs aux obligations RGPD.

`/config-yml/modules` : modules complémentaires développés par la communauté, voir section suivante.

## Modifier vos images

Toutes les images du dossier `/public/assets/imgs` sont accessible ensuite sur votre landing. Dans vos fichiers yml, indiquez simplement le chemin à partir de ce dossier.

## Les modules
Les modules sont des composants de la landing que vous pouvez **activer** / **désactiver**

|  Nom du module | Fonctionnalités  | Fichier de configuration  | Spécificités 
|---|---|---|---|
| Actualités   |  <ul><li>Bloc sur la page d'accueil (derniers articles)</li><li>Page list des actualités `/actualites`</li><li>Page pour chaque actualité</li></ul> | `articles.yml`  | [Oui](#module-actualites)  |
|  Statistiques | <ul><li>Bloc KPI sur la page d'accueil</li><li>Page de statistiques `/stats`</li></ul> | `stats.yml`  | [Oui](#module-stats)  |
| Newsletter  | <ul><li>Bloc sur la page d'accueil</li></ul>  | `newsletter.yml`   |  [Oui](#module-newsletter) |
| Onboarding  | <ul><li>Bloc sur la page d'accueil</li><li>Page formulaire d'onboarding `/onboarding`</li></ul>  | `onboarding.yml`   |  [Oui](#module-onboarding) |
| Instagram  | <ul><li>Bloc feed instagram sur la page d'accueil</li></ul>  | `instagram.yml`   |  [Oui](#module-instagram) |


#### <a name="module-actualites">Actualités</a>

La propriété `articles` du fichier yml est une list, vous pouvez ajouter des articles à la suite pour les publier.

La propriété `image` doit être le nom de l'image contenue dans le dossier `/public/assets/img/articles`.

#### <a name="module-instagram">Instagram</a>

L'application a besoin d'un token instagram pour récupérer les posts et les afficher.
Ajoutez `INSTAGRAM_TOKEN=votretokenhashé` dans les sealed-secrets. (https://socialgouv.github.io/sre-tools/ pour encrypter votre token)


#### <a name="module-stats">Statistiques</a>

La propriété `page.graphs` du fichier yml est une list, vous pouvez ajouter des graphs à la suite.
Pour chaque graph, les attributs disponibles pour la propriété `type` sont :
- lineChart ([exemple](https://recharts.org/en-US/examples/SimpleLineChart))
- barChart ([exemple](https://recharts.org/en-US/examples/SimpleBarChart))


#### <a name="module-onboarding">Onboarding</a>

Le module d'onboarding contient une page avec un formulaire personnalisable.
Une requête POST est envoyée à la route spécifiée avec un payload dynamique en fonction des attributs `name` attribués au champs.


## Contribuer

Vous souhaitez créer un nouveau module dans la landing page ? Quelle belle initiative!

Afin que les autres startup puissent aussi en profiter, développez dans le sous-module git vers lequel pointe le dossier `/src`

Vous trouverez toutes les indications dans [ici dans le README](https://github.com/SocialGouv/landing-core).
