# UCE Tool

[简体中文](README.zh-CN.md) | [English](README.en.md) | [Deutsch](README.de.md) | [日本語](README.ja.md) | **Français**

UCE Tool est l'application de bureau du USB-C Explorer. Elle permet de consulter les mesures en direct, lire les E-Marker, effectuer une détection ou une capture PD, configurer le thème de l'appareil et mettre à jour son micrologiciel.

## Installation et connexion

Téléchargez le paquet Windows ou macOS adapté depuis la [page des versions](https://github.com/Asuka-019/UCE-Tool/releases/latest). Sous Windows, extrayez le paquet puis ouvrez l'application ; sur Mac, installez l'application dans le dossier Applications.

Reliez l'appareil à l'ordinateur avec un câble USB prenant en charge les données. Cliquez sur sa carte dans la barre latérale pour le connecter. Cliquez de nouveau sur la carte connectée pour le déconnecter, ou sur une autre carte pour changer d'appareil. La recherche des appareils est automatique, leur connexion ne l'est pas.

## Tableau de bord

Ouvrez le **Tableau de bord** et cliquez sur l'icône de démarrage pour afficher les mesures et les courbes. Les commandes permettent de choisir les courbes, modifier la fréquence et la durée affichée, mettre en pause ou effacer le graphique.

## E-Marker

Branchez le câble selon les indications des ports et ouvrez **E-Marker**. Cliquez sur **Lire** pour obtenir les informations du câble. La lecture continue se lance et s'arrête avec le même bouton. Avant de la démarrer, débranchez les appareils alimentés de la sortie, conformément à l'avertissement affiché.

L'onglet des enregistrements permet de consulter les résultats de la session, de les exporter vers Excel ou de les effacer. Les champs non transmis ou non reconnus sont indiqués comme inconnus.

## Détection PD

Branchez le chargeur à tester et ouvrez la **détection PD**. Démarrez la détection, lisez et confirmez l'avertissement. Les PDO et leurs résultats individuels s'affichent ; le même bouton permet d'arrêter une détection en cours. Les résultats peuvent être consultés, exportés vers Excel ou effacés.

**La tension peut augmenter pendant la détection. Débranchez les appareils alimentés de la sortie avant de commencer.**

## Analyseur PD

Branchez le circuit à tester conformément aux indications des ports. Ouvrez l'**analyseur PD** et démarrez la capture ; le même bouton permet de l'arrêter. Sélectionnez un paquet pour afficher son en-tête et ses objets de données en dessous de la liste. Faites glisser la séparation pour ajuster la taille des zones.

Le bouton CRC affiche ou masque les paquets GoodCRC. L'export Excel comprend aussi les paquets masqués.

Utilisez **Importer Excel** pour rouvrir une capture exportée par l'analyseur. Arrêtez d'abord la capture ; l'import remplace la liste actuelle.

## Configuration du thème

Utilisez les flèches pour choisir un écran de l'appareil, puis cliquez sur une zone de couleur ou sur la couleur d'arrière-plan.

- **Restaurer les valeurs par défaut** rétablit les couleurs initiales.
- **Lire depuis l'appareil** charge les couleurs actuelles.
- **Appliquer à l'appareil** applique les couleurs temporairement.
- **Enregistrer sur l'appareil** les conserve après redémarrage.

## Micrologiciel et paramètres

Ouvrez la page de mise à jour du micrologiciel, récupérez la liste des versions et choisissez celle qui correspond à votre appareil. Suivez les instructions et maintenez l'appareil connecté et alimenté jusqu'à la fin.

Les paramètres permettent de changer la langue et de consulter les informations de l'appareil ; la barre latérale permet de changer le mode clair ou sombre. Les enregistrements sont conservés pour la session en cours : exportez ceux dont vous avez besoin avant de fermer l'application. Si l'appareil est occupé, arrêtez d'abord toute autre détection ou capture.

## Informations complémentaires

### Démarrage et connexion

Les applications Windows et macOS ne nécessitent pas d'installation séparée de Python pour une utilisation normale. Sur Mac, choisissez le paquet Apple Silicon ou Intel adapté. Si macOS bloque le premier lancement, vérifiez la provenance de l'application, puis autorisez-la dans **Réglages Système → Confidentialité et sécurité**.

Reliez l'interface de données de l'appareil à l'ordinateur. Un câble de charge uniquement peut alimenter l'appareil sans permettre la communication. La barre latérale affiche le nom, une partie du numéro de série et la version APP ; le numéro complet est disponible dans les informations de l'appareil. Le mode BOOT permet la récupération du micrologiciel, mais les mesures et détections nécessitent le micrologiciel applicatif.

### Lire le tableau de bord

VBUS représente la tension, IBUS le courant et POWER la puissance. D+ / D− et CC1 / CC2 indiquent les tensions des signaux correspondants. Les courbes de tension, courant et puissance utilisent des échelles distinctes : vérifiez l'unité lors d'une comparaison. Placez le pointeur sur le graphique pour consulter les mesures ; `--` indique qu'aucune valeur n'est disponible à cet endroit.

La fréquence peut être réglée sur 1, 10 ou 50 mesures par seconde et la durée affichée sur 10, 30, 60 ou 120 secondes. La pause fige l'affichage ; la reprise continue l'acquisition. Effacer supprime l'historique affiché.

### Résultats E-Marker et PD

Les informations E-Marker disponibles dépendent du câble et du micrologiciel. La page peut afficher le type de câble, le courant nominal, la tension maximale, la vitesse de données, la version PD, TBT, EPR et la longueur ou la latence. Une longueur estimée à partir de la latence n'est pas une mesure physique. Les données E-Marker brutes figurent sous les informations du câble.

La détection PD lit les PDO annoncés par le chargeur et affiche les états de test individuels lorsque le micrologiciel les fournit. Un profil annoncé ne signifie pas automatiquement que son test a réussi. Les onglets au-dessus des résultats permettent de basculer entre résultats et historique. Si une fonction n'est pas prise en charge, utilisez un micrologiciel compatible.

Les historiques E-Marker et PD correspondent à la session en cours. Effacer les enregistrements vide la liste actuelle ; l'export Excel crée un fichier `.xlsx`. Enregistrez les résultats nécessaires avant de fermer l'application.

### Lire une capture PD

Le tableau affiche notamment le type de message, le canal SOP, l'identifiant, la direction, le nombre d'objets, la révision PD, le temps écoulé, les mesures de tension et de courant, les données brutes et les notes. Sélectionnez une ligne pour détailler l'en-tête et les champs des objets disponibles. La zone de détail défile horizontalement et verticalement lorsque nécessaire.

Attach et Detach sont des événements de connexion ; Hard Reset est un événement de réinitialisation sur la liaison PD surveillée. Lorsqu'un champ ne peut pas être interprété avec certitude, sa valeur brute peut être affichée. Pour les messages de câble, la direction indique une communication entre le port et la fiche lorsque l'émetteur exact n'est pas connu.

Le masquage GoodCRC ne change que l'affichage : les paquets masqués restent inclus dans l'export Excel.

### Couleurs et micrologiciel

Modifiez d'abord les couleurs dans l'aperçu. **Appliquer à l'appareil** permet de vérifier temporairement le résultat ; utilisez **Enregistrer sur l'appareil** pour le conserver après extinction. **Lire depuis l'appareil** remplace l'aperçu par les couleurs actuelles, tandis que la restauration des valeurs par défaut réinitialise les couleurs dans l'éditeur.

Pour mettre à jour le micrologiciel, récupérez la liste des versions, choisissez un paquet compatible et vérifiez la progression et le résultat. Ne débranchez ni l'alimentation ni le câble de données pendant l'opération. La mise à jour de l'application UCE Tool est distincte et accessible depuis le menu À propos.

### Dépannage

- **Aucun appareil affiché** : vérifiez l'alimentation, le câble de données et le port, puis reconnectez l'appareil. Cliquez sur sa carte lorsqu'elle apparaît.
- **Appareil occupé** : arrêtez toute autre lecture E-Marker, détection PD, capture ou mise à jour, puis attendez la fin de l'opération.
- **Aucun résultat E-Marker** : vérifiez le câble et son branchement. Tous les câbles ne possèdent pas d'E-Marker et certaines informations peuvent ne pas être transmises.
- **Aucun paquet visible** : vérifiez la connexion de l'appareil, le démarrage de la capture et les ports de test. Vérifiez aussi si GoodCRC est masqué.
- **Échec d'une mise à jour ou d'un export** : vérifiez l'erreur affichée, l'espace disponible, le choix du micrologiciel et la connexion, puis réessayez.
