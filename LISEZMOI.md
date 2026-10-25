# Reporting Cargill

Appli de comptes rendus d'intervention pour Dimitri Van Calster (Cargill).
Elle remplace le fichier Excel « Reporting_Cargill » : une saisie par intervention,
regroupée par semaine et par jour, avec export PDF et envoi par mail au n+1.

## Contenu du dossier

| Fichier | Rôle |
|---|---|
| `index.html` | L'appli entière (écrans, calculs, PDF) |
| `manifest.webmanifest` | Permet de l'installer sur l'écran d'accueil du téléphone |
| `sw.js` | Garde l'appli disponible sans réseau |
| `icons/` | Icônes de l'appli |

## 1. Mettre l'appli en ligne (GitHub Pages)

1. Sur GitHub, crée un nouveau dépôt (par exemple `reporting-cargill`), en public.
2. « Add file » → « Upload files » : glisse **tout le contenu** du dossier (y compris le dossier `icons`), puis « Commit changes ».
3. « Settings » → « Pages » → Source : « Deploy from a branch », branche `main`, dossier `/ (root)` → « Save ».
4. Au bout d'une minute, l'adresse apparaît en haut de la page Pages : `https://TON-PSEUDO.github.io/reporting-cargill/`.

Le dépôt ne contient aucune donnée : les comptes rendus restent sur le téléphone de Dimitri.

## 2. L'installer sur le téléphone de Dimitri

- **iPhone (Safari)** : ouvrir l'adresse → bouton Partager → « Sur l'écran d'accueil ».
- **Android (Chrome)** : ouvrir l'adresse → menu ⋮ → « Installer l'application » (ou « Ajouter à l'écran d'accueil »).

Ensuite, dans l'appli : **Réglages** → renseigner le nom et l'adresse mail du n+1.

## 3. Utilisation au quotidien

1. Onglet **Semaines** (du lundi au vendredi) : la semaine en cours, mise en avant ; elle change chaque lundi. Les semaines passées s'affichent avec le bouton « Voir les semaines passées ». Une semaine à venir n'apparaît que si une intervention y est datée (ou avec « Aller à une date »). Toucher un jour pour l'ouvrir (un seul jour ouvert à la fois).
2. Bouton jaune **+ Intervention** en haut (compte rendu daté d'aujourd'hui) ou « Créer nouveau compte rendu d'intervention » dans une journée. En haut du compte rendu, choisir **Avec work order** ou **Sans work order** :
   - **Avec work order** : photographier le WO ou choisir le PDF → le n° de WO, le bâtiment, la localisation et le travail demandé se remplissent automatiquement (modifiables si la lecture s'est trompée). Photo bien à plat, nette et éclairée pour un meilleur résultat. Le n° de WO est obligatoire.
   - **Sans work order** (demande reçue par SMS, téléphone ou de vive voix) : travail demandé, **à la demande de**, bâtiment et localisation, tous remplissables au micro. Une capture du SMS peut aller dans Photos.
   - **Date** au calendrier, **horaires** début/fin (ou raccourcis Journée / Matin / Après-midi). La pause déjeuner est déduite.
   - **Commentaires** : à la voix avec le bouton micro. Si la dictée n'est pas disponible, le micro du clavier du téléphone fonctionne aussi.
   - **Temps passé** : calculé d'après les horaires, modifiable dans la liste.
   - **Cumul** : additionne automatiquement toutes les interventions sur le même WO (ou la même demande). Modifiable si une partie du travail a été faite avant d'utiliser l'appli.
   - **Photos** : appareil photo ou galerie.
   - « Enregistrer + nouveau » enchaîne directement sur l'intervention suivante du même jour.
   - **État** (menu déroulant) : « À commencer », « À finaliser » s'il reste du travail, « À envoyer » quand c'est fini, ou « Envoyé » s'il a déjà été envoyé au n+1 par un autre moyen. Le WO ou la demande va directement dans le dossier correspondant.
3. Envoi au n+1 : chaque jour (bouton « Envoyer » sur la journée) ou chaque semaine (« Envoyer le reporting de la semaine »), au choix dans Réglages.
4. Onglet **Interventions** : deux grands dossiers, **Avec work order** et **Sans work order**. Chacun contient les mêmes sous-dossiers, avec leur couleur :
   - **À commencer** (bleu) : pas encore commencé.
   - **À finaliser** (rouge) : commencé ou en attente.
   - **À envoyer** (orange) : réalisé, mais au moins une intervention n'a pas encore été envoyée au n+1. Une pastille rouge indique combien il en reste.
   - **Historique → Envoyés** (vert) : réalisés et entièrement envoyés au n+1. Par défaut, l'envoi le plus récent en premier.

   Un WO ou une demande passe d'un dossier à l'autre avec le menu « État » (sur chaque compte rendu, ou « Modifier »), avec « Marquer comme réalisé », ou tout seul quand il est envoyé.

   Dans chaque dossier : recherche par mot clé, filtres (priorité, bâtiment, type de demande, date, anciens ou nouveaux ; pour les demandes, « à la demande de ») et tri (ordre alphabétique, n° ou date). Depuis une fiche : créer ou ajouter un compte rendu, l'envoyer directement, modifier ses infos, le marquer comme réalisé. « Choisir » ou « Tout envoyer » envoie plusieurs fiches dans un seul PDF.

   Dans une fiche, chaque intervention a un **rond vert** (envoyée, avec la date) ou un **rond rouge** (pas encore envoyée).

Le PDF reprend la présentation du reporting Excel actuel (date, horaires, WO, intervention, observations, temps, cumul WO, total jour et total semaine), avec les photos en annexe et **les work orders joints en fin de PDF** (désactivable dans Réglages).

Si le téléphone se met en veille pendant la saisie, le brouillon est gardé et proposé à la réouverture.

## 4. Envoi par mail

**Par défaut (rien à configurer)** : « Envoyer par mail » ouvre la liste de partage du téléphone. On choisit Gmail (ou Outlook) : le PDF, l'objet et le message sont déjà remplis, il reste à mettre l'adresse du n+1 et à envoyer.

**Envoi direct depuis Gmail (optionnel, environ 15 minutes de réglage, une seule fois)** : l'appli envoie elle-même le mail avec le PDF depuis la boîte Gmail de Dimitri, destinataire déjà rempli, en un seul bouton.

1. Aller sur https://console.cloud.google.com avec un compte Google, et créer un projet (« Reporting Cargill »).
2. **Activer l'API Gmail** : menu ☰ → « API et services » → « Bibliothèque » → chercher **Gmail API** → « Activer ».
3. **Écran de consentement** : chercher « OAuth » dans la barre du haut → « Google Auth Platform » → « Commencer » :
   - Informations sur l'application : nom « Reporting Cargill », ton adresse mail ;
   - Audience : **Externe** ;
   - Coordonnées : ton adresse mail ;
   - accepter et « Créer ».
4. Onglet **Audience** → « Utilisateurs test » → « Add users » : ajouter **l'adresse Gmail de Dimitri**. Laisser l'appli en mode « Test ».
5. Onglet **Accès aux données** (Data access) → « Ajouter ou supprimer des champs d'application » → ajouter `https://www.googleapis.com/auth/gmail.send` → « Mettre à jour » → « Enregistrer ».
6. Onglet **Clients** → « Créer un client » → type **Application Web**.
   Dans « Origines JavaScript autorisées », ajouter `https://TON-PSEUDO.github.io` (sans le nom du dépôt, sans `/` à la fin). Rien à mettre dans les URI de redirection. « Créer ».
7. Copier l'**ID client** (il finit par `.apps.googleusercontent.com`). Le code secret n'est pas utile.
8. Dans `index.html`, tout en haut du script, coller l'ID entre les guillemets :
   `googleClientId: '1234-abcd.apps.googleusercontent.com'`
   puis renvoyer `index.html` sur GitHub (« Add file » → « Upload files » → « Commit changes »).

Au premier envoi, Google affiche « Google n'a pas validé cette application » : c'est normal pour une appli personnelle en mode test. Toucher « Continuer », puis autoriser l'envoi de mails. L'appli ne demande que le droit d'**envoyer** des mails, pas de les lire.

## 5. Sauvegarde

Les données sont stockées dans le navigateur du téléphone. Si on efface les données de Safari/Chrome ou qu'on change de téléphone, elles disparaissent.
Réglages → « Sauvegarder mes données » crée un fichier (photos comprises) à garder dans Drive ou par mail ; « Restaurer une sauvegarde » le recharge.

## 6. Bon à savoir

- La première ouverture, le premier PDF et la première lecture de WO par photo ont besoin de réseau (chargement des outils). Ensuite tout fonctionne hors ligne, sauf l'envoi du mail.
- La lecture d'un WO en PDF est quasi instantanée. Par photo, compter 10 à 30 secondes selon le téléphone ; une photo nette, à plat et bien éclairée donne les meilleurs résultats.
- La lecture automatique repère les intitulés courants d'un ordre de travail (« Ordre de travail », « Poste technique », « Description », « Bât. »…). Si le format Cargill utilise d'autres intitulés, quelques lignes de `parseWO` dans `index.html` sont à ajuster.

## 7. Les 29 anciens work orders

Ils sont livrés avec l'appli, dans le fichier `anciens-wo.json`, et se rangent tout seuls au premier lancement dans Interventions → Avec work order (« À commencer », « À finaliser », « À envoyer »), avec la photo de chaque WO. Rien à faire.

Chacun a aussi sa fiche dans les semaines, à sa date :
- les 7 réalisés à la date où ils ont été faits ;
- les 22 autres à la date où le WO a été remis, avec l'état « À commencer » ou « À finaliser ».

Les horaires et le temps sont « À préciser » : Dimitri peut ouvrir chaque fiche pour les compléter ou changer la date.

Attention : le dépôt GitHub étant public, ce fichier (et les photos des WO qu'il contient) est lisible par toute personne qui connaît l'adresse.
