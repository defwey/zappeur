# Zappeur : lecteur IPTV pour iPhone et iPad (version 0.1)

Zappeur est un lecteur, comme TiviMate : il ne fournit aucune chaîne et lit la playlist de ton fournisseur IPTV.

## Ce que fait cette première version

- **Connexion** Xtream Codes (serveur, identifiant, mot de passe) ou lien M3U. Si tu colles un lien M3U Xtream, l'appli propose de passer en mode Xtream.
- **Chaînes classées par groupe**, dans l'ordre choisi par ton fournisseur, avec une barre de raccourcis et une liste complète des groupes avec recherche.
- **Favoris** (glisser une chaîne vers la gauche), **Récents** et **recherche** de chaînes.
- **Guide TV** (XMLTV) : programme en cours avec barre de progression, programme suivant, liste des programmes à venir. Le guide est mis en cache 12 h ; les fichiers .gz sont acceptés.
- **Lecteur vidéo d'Apple** : Picture-in-Picture (il démarre tout seul quand tu quittes l'appli pendant la lecture), AirPlay, plein écran quand tu tournes le téléphone.
- **Zapping** depuis le lecteur, avec les flèches ou l'onglet « Chaînes ».
- **Plusieurs playlists** possibles, à gérer dans les Réglages.
- **Sécurité** : le mot de passe est rangé dans le trousseau iOS, jamais en clair.

## Installer l'appli sans Mac (GitHub + Sideloadly)

L'appli est compilée par GitHub sur un Mac dans le cloud (fichier `.github/workflows/build.yml`), puis installée depuis un PC avec Sideloadly. Il faut un iPhone sous iOS 16 ou plus récent.

**1. Déposer le projet sur GitHub (une seule fois)**
1. Décompresse le .zip (clic droit > « Extraire tout »).
2. Sur la page du dépôt GitHub, clique sur **Add file > Upload files**.
3. Ouvre le dossier extrait, sélectionne **tout son contenu** (Ctrl + A) et glisse-le dans la page GitHub. Glisse bien le contenu du dossier, pas le dossier lui-même : le dossier `.github` doit arriver à la racine du dépôt.
4. Clique sur **Commit changes**. La compilation démarre toute seule (onglet **Actions**, une dizaine de minutes).

**2. Récupérer l'appli**
Quand la compilation est terminée, le fichier **Zappeur.ipa** est dans **Releases** (« derniere-version »), à droite de la page du dépôt.

**3. L'installer sur l'iPhone avec Sideloadly**
1. Sur le PC, installe **iTunes** et **iCloud** depuis le site d'Apple (pas depuis le Microsoft Store), puis **Sideloadly**, uniquement depuis son site officiel **sideloadly.io**. Sur un Mac, même ancien (macOS 10.12 minimum), Sideloadly fonctionne sans iTunes.
2. Sur l'iPhone : **Réglages > Confidentialité et sécurité > Mode développeur** → activer (l'iPhone redémarre).
3. Branche l'iPhone en USB, ouvre Sideloadly, glisse **Zappeur.ipa** dans la fenêtre, saisis ton identifiant Apple et clique sur **Start**.
4. Sur l'iPhone : **Réglages > Général > VPN et gestion de l'appareil**, touche ton identifiant Apple puis **Se fier**.
5. Avec un identifiant Apple gratuit, l'appli doit être réinstallée tous les **7 jours** (refais l'étape 3).

> Sécurité : Sideloadly est un outil tiers qui demande ton identifiant Apple. Tu peux utiliser un identifiant Apple secondaire.

## Installer l'appli avec un Mac récent (Xcode)

Il te faut Xcode 16 ou plus récent (gratuit sur l'App Store du Mac) et un iPhone sous iOS 16 ou plus récent.

1. Décompresse le .zip, puis double-clique sur **Zappeur.xcodeproj** : le projet s'ouvre dans Xcode.
2. Dans Xcode, ouvre le menu **Xcode > Settings… > Accounts**, clique sur **+** puis **Apple ID**, et connecte-toi avec ton identifiant Apple. Un compte gratuit suffit.
3. Dans la colonne de gauche, clique sur **Zappeur** (l'icône bleue tout en haut). Sélectionne la cible **Zappeur**, onglet **Signing & Capabilities**. Dans **Team**, choisis ton nom suivi de « (Personal Team) ».
4. Branche l'iPhone au Mac en USB, déverrouille-le et accepte **« Se fier à cet ordinateur »**.
5. Sur l'iPhone, active le mode développeur : **Réglages > Confidentialité et sécurité > Mode développeur**. L'iPhone redémarre. L'option n'apparaît qu'une fois l'iPhone branché au Mac avec Xcode ouvert.
6. En haut de la fenêtre Xcode, choisis ton iPhone comme destination, puis clique sur **▶︎** (ou appuie sur Cmd + R).
7. Au premier lancement, iOS bloque l'appli. Va dans **Réglages > Général > VPN et gestion de l'appareil**, touche ton identifiant Apple, puis **Faire confiance**. Relance ensuite l'appli.

> **Pour un premier essai sans iPhone** : choisis un simulateur en haut de Xcode (par exemple « iPhone 16 ») et clique sur ▶︎. Tu n'as besoin d'aucun compte.

### Bon à savoir

- Avec un compte Apple **gratuit**, l'appli cesse de s'ouvrir au bout de **7 jours**. Il suffit de rebrancher l'iPhone et de cliquer à nouveau sur ▶︎ ; tes playlists et favoris sont conservés. Le programme développeur Apple (payant) supprime cette limite.
- Si Xcode indique que l'identifiant de l'appli est déjà pris, modifie le **Bundle Identifier** dans l'onglet Signing & Capabilities, par exemple en ajoutant ton prénom à la fin.
- Le guide TV d'un fournisseur peut peser plusieurs dizaines de Mo : privilégie le Wi-Fi au premier chargement.

## Limites connues (prochaines étapes possibles)

- **Formats vidéo** : pour le direct, le lecteur d'Apple ne lit que le HLS (.m3u8). L'appli convertit automatiquement les liens Xtream en HLS, ce qui couvre la plupart des fournisseurs. Les flux qui n'existent qu'en MPEG-TS ou en MKV ne passeront pas. La solution serait d'intégrer VLCKit, le moteur de VLC.
- Pas encore de grille du guide TV façon TiviMate, ni de replay, ni d'enregistrement.
- Les films et séries (VOD) sont ignorés pour l'instant.
- Pas encore de version Apple TV.

## En cas d'erreur de compilation

Fais une capture du message d'erreur affiché par Xcode (panneau de gauche, icône ⚠︎) et envoie-la : il sera corrigé.
