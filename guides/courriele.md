# Archives courriel et ePADD
Les formats de courrier électronique nécessitent un traitement supplémentaire, car ils contiennent souvent des informations sensibles ou personnelles et, en tant que format, sont difficiles d'accès pour les utilisateurs. [ePADD](https://www.epaddproject.org/), développé par les bibliothèques de l'université Stanford, permet à l'archiviste chargé du traitement de faire des recherches dans les courriers électroniques, de restreindre les documents éventuellement sensibles, de créer des copies d'accès et de conservation et de fournir une interface d'accès conviviale à l’utilisateur.


Une documentation complète sur ePADD se trouve dans leur [guide de l'utilisateur (2023)](https://docs.google.com/document/d/1PWzKyonRdogAChtHOQs-CVjCTMuQi00pLsHZRJateKw/edit?tab=t.0) et dans le [forum communautaire](https://groups.google.com/g/epaddusers).


ePADD peut être téléchargé [ici](https://www.epaddproject.org/using-epadd/download-and-install), et les instructions d'installation se trouvent dans le [guide de l'utilisateur](https://www.epaddproject.org/using-epadd/user-guide). Le CCA recommande d'installer ePADD dans les environnements Mac ou Windows.


Cette documentation est à jour à partir de la version 10 d'ePADD (janvier 2023).

* [Formats de courriel](#formats)
* [Module d'importation et d'évaluation](#importation)
* [Module de traitement](#traitement)
* [Module de livraison](#livraison)

<a name="formats"></a>
## Formats de courriel
ePADD fonctionne avec des comptes de courrier électronique en direct (y compris IMAP) et des archives de courrier électronique au format MBOX. Si vos archives de courrier électronique sont dans un format différent, elles devront être converties en utilisant [Emailchemy](https://weirdkid.com/emailchemy/), un convertisseur de format de courrier électronique situé sur la station de travail d'imagerie CD. Notez que l'utilitaire en ligne de commande readpst n'est pas recommandé.


Pour utiliser Emailchemy :


1. Confirmez que les paramètres suivants sont sélectionnés dans Emailchemy, sous Outils > Options > :
   * Général, cochez :
      * Dédupliquer les messages lors de la conversion
      * Effacement automatique de la mémoire du duplicateur après les conversions
   * Fichiers / Dossiers, cochez :
      * Conserver la structure des dossiers
      * Autoriser les caractères non anglais dans les nouveaux noms de fichiers et de dossiers
      * Remplacer les caractères de noms de fichiers interdits par un tiret
   * Journalisation, cochez :
      * Rédiger un journal de conversion
      * Utiliser l'emplacement par défaut du fichier journal
      * Enregistrer les sommes de contrôle du fichier source avant et après la conversion
   * En-têtes, cochez :
      * Respect strict de la norme RFC-2822 pour l'analyse syntaxique
      * Préserver les champs optionnels d'extension et d'en-tête définis par l'utilisateur
      * Normaliser les dates
   * Outlook (Win), cochez :
      * Enregistrer le texte du message crypté en pièce jointe
      * Traduire une adresse électronique de type Exchange en adresse de type Internet (SMTP)
      * Extraire tous les types d'objets de message
2. À l'aide de l'assistant de conversion de courrier électronique, choisissez votre type de fichier source et cliquez sur suivant.
3. Sur l'écran suivant, trouvez le fichier ou le dossier contenant vos fichiers d'archives de courrier électronique. **Si vous pointez vers un dossier, les fichiers doivent se trouver dans un seul répertoire.** Emailchemy ne se répète pas. Cliquez sur suivant.
4. Assurez-vous que la case "filtrer les messages en double" est cochée, et que toutes les autres sont décochées. Cliquez sur convertir. Cela peut prendre un certain temps.
5. Trouvez le fichier journal créé lors de la conversion et enregistrez-le. Il sera éventuellement inclus dans vos métadonnées au niveau SIP.

<a name="importation"></a>
## Module d'importation et d'évaluation
NOTE : Avant d'importer de nouvelles archives dans ePADD, assurez-vous que l'utilisateur précédent a correctement nettoyé [ePADD de sa session](https://github.com/CCA-Public/manuel-archives-numeriques/blob/master/guides/courriele.md#nettoyer-epadd).


Le module d'évaluation est l'écran de démarrage par défaut après le lancement de ePADD. L'évaluation est destinée à être utilisée par le donateur pour effectuer un premier examen et une restriction de son propre courrier électronique. Notamment, l'indicateur "Ne pas transférer" supprime les courriels, ce qui empêche leur transfert vers le module de traitement.


Dans le cas particulier du CCA, le module d'évaluation est utilisé par son importateur, car les donateurs n'examinent généralement pas leurs propres documents. Un examen et une restriction supplémentaires auront lieu dans le module de traitement. Pour importer vos fichiers MBOX dans ePADD :
1. Lancez ePADD en cliquant sur epadd.exe. Par défaut, ePADD fonctionne avec 4 Go de mémoire vive, mais une mémoire vive supplémentaire peut être nécessaire pour les collections plus importantes. Si c'est le cas, téléchargez epadd-standalone.jar, et lancez ePADD en utilisant le code ci-dessous, où # indique la quantité de RAM (en Go) que vous souhaitez allouer. 8 Go sont généralement suffisants.
```java -Xmx#g -jar /file/path/to/epadd-standalone.jar```
2. Cliquez sur "Importer" en haut du navigateur ePADD.
3. Saisissez autant de métadonnées que possible. Elles peuvent être ajoutées et modifiées dans le module de traitement.
4. Pointez ePADD vers les courriels à traiter :
   1. Pour les comptes de courrier électronique publics (par exemple, Google, Yahoo), entrez l'adresse électronique et le mot de passe du compte. (Notez qu'au moment où nous écrivons ces lignes, nous n'avons pas pu tester cette fonctionnalité).
   2. Pour les comptes IMAP privés (par exemple, les boîtes de réception Outlook du CCA), entrez le serveur IMAP, l'adresse électronique et le mot de passe du compte. Vous devrez peut-être contacter le donateur ou son fournisseur informatique pour accéder à son serveur.
   3. Pour les fichiers MBOX, sélectionnez le répertoire où se trouvent les fichiers MBOX. Les fichiers doivent se trouver dans un seul répertoire. Vous pouvez également saisir le nom de la source du courrier électronique, qui est un champ facultatif.
5. Cliquez sur continuer. L'écran suivant chargera tous les fichiers MBOX ou les dossiers IMAP à l'endroit indiqué. Cela peut prendre un certain temps. Cochez la case située à côté du dossier approprié et cliquez sur Continuer. (Il n'est pas nécessaire de remplir la plage de dates).
6. ePADD fonctionnera pour lire les fichiers sélectionnés. Cela peut prendre un certain temps. Lorsque ce processus est terminé, ePADD affiche les courriels dans le module d'évaluation.
Étant donné que le module d'évaluation n'offre aucune fonctionnalité unique et que le cas d'utilisation du CCA ne prévoit pas d'examen par les donateurs, l'étape suivante consiste à exporter le courriel du module d'évaluation vers le module de traitement. Pour ce faire :
7. Cliquez sur l'onglet Exporter en haut de l'écran.
8. Sous "Exporter des messages et des pièces jointes", cliquez sur Parcourir, et choisissez C:/Utilisateurs/utilisateur. Cliquez sur Exporter (PAS "Exporter vers MBOX"). Cela peut prendre un certain temps. Il sera enregistré comme "archive ePADD de (nom du créateur de l'archive)". Ce dossier est maintenant prêt à être importé dans le module de traitement.

<a name="traitement"></a>
## Module de traitement
L'archiviste peut commencer à examiner, restreindre et attribuer des métadonnées dans le module de traitement. Pour ce faire :


1. Passez ePADD au module de traitement en cliquant sur le point d'interrogation bleu dans le coin supérieur droit. Cliquez sur "ePADD Mode". Choisissez "PROCESSING" dans le menu déroulant.
2. Ajoutez vos archives en cliquant sur l'onglet "Ajouter". A côté de "Dossier d'accès", cliquez sur "Parcourir" et choisissez le "Dossier d'archivage du (créateur d'archives)" créé dans le module précédent. Remplissez autant de métadonnées que possible. Vous pourrez y revenir ultérieurement. Cliquez sur "Importer l'adhésion". Cela peut prendre un certain temps.


### L'onglet Parcourir
Lorsque ePADD a fini d'importer l'acquisition, l'archiviste peut commencer à traiter les documents à partir de l'écran "Browse" qui ressemble à ceci :


![Capture d'écran de l'onglet "Browse" de l'ePADD](https://raw.githubusercontent.com/CCA-Public/digital-archives-manual/master/media/photos/epadd_screenshot.JPG)


La majeure partie de ce traitement consiste à examiner le courrier électronique pour s'assurer qu'il est conforme au champ d'application et qu'il ne contient pas de matériel sensible. Lors de l'examen du courrier électronique, l'onglet "Étiquettes" peut être utilisé pour restreindre le matériel. Les étiquettes "collent" lorsque les archives sont exportées vers le module suivant. Les drapeaux "Cleared for Release" et "Reviewed" sont exportés avec leurs étiquettes, et les courriels marqués "Do Not Transfer" ne sont pas déplacés vers le module suivant, ce qui a pour effet de les restreindre/supprimer de la copie de préservation et d'accès. Il est également possible de programmer la restriction temporaire des courriels ; voir le [guide de l'utilisateur](https://www.epaddproject.org/using-epadd/user-guide) pour plus d'informations.


![Capture d'écran d'étiquettes d'ePADD](https://raw.githubusercontent.com/CCA-Public/digital-archives-manual/master/media/photos/epadd_labels.JPG)


**TOUT AU LONG DE CE PROCESSUS, VOUS DEVEZ SAUVEGARDER VOTRE TRAVAIL, EN UTILISANT L'ONGLET "SAUVEGARDER" EN HAUT DE L'ÉCRAN**. Vos modifications ne seront pas conservées tant que vous n'aurez pas sauvegardé l'archive.
Le processus de révision ne doit pas nécessairement se dérouler dans un ordre particulier. ePADD fournit les outils suivants :
1. *Correspondants* : Une liste de toutes les adresses électroniques (de, vers, de, mentionnées) dans les archives, et la meilleure estimation de ePADD sur le nom du contact et les autres adresses électroniques.
   1. Modifiez la liste des correspondants pour associer correctement les contacts à leurs adresses électroniques.
   2. Parcourir les correspondants et étiqueter les e-mails pour les correspondants hors champ (par exemple, les amis et les membres de la famille) comme "Ne pas transférer". Lorsque le module de traitement est exporté, il réindexera la liste des correspondants afin qu'aucun des correspondants hors champ ne soit inclus dans la copie finale.
2. *Personnes entités* : Une liste de toutes les personnes reconnues par ePADD.
3. *Autres entités* : Une liste de tous les lieux et noms de sociétés reconnus par ePADD.
4. *Vue par dossier* : Tous les courriers électroniques triés par dossier (par exemple, Boîte de réception, Envoyé, Brouillons).
   1. Déterminez si tous les dossiers font partie de la collection.
   2. Examinez les dossiers "Éléments supprimés" pour déterminer s'ils doivent être conservés.
5. *Pièces jointes aux images* : Une galerie de toutes les images jointes aux courriels.
6. *Autres pièces jointes* : Tous les autres types de fichiers joints aux courriels, disponibles en téléchargement.
7. *Recherche dans le lexique* : Recherche de mots-clés basée sur des lexiques définis pour identifier les matériaux sensibles. Un [lexique CCA](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/cca_lexicon) a été créé sur la base des lexiques ePADD existants afin d’identifier les mots sensibles pertinents pour le cas d'utilisation CCA. Un [lexique allemand](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/german_lexicon) et un [lexique français](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/french_lexicon.txt) ont été développés pour fournir des fonctionnalités linguistiques supplémentaires (limitées). Notez que ces lexiques doivent être considérés en version bêta, et que tous les lexiques doivent être considérés à la lumière du contexte particulier d'une collection.
   1. Utilisez la recherche dans les lexiques pour identifier les documents potentiellement sensibles et hors de portée. Les lexiques peuvent être ajoutés manuellement ou installés directement ; voir le [fichier ReadMe du lexique](https://docs.google.com/document/d/1RWU1kXUPa1kEf5_mEaNP_veQ8IX-Sw1J0mBJ8rRhS3Q/edit) et le [guide de l'utilisateur](https://www.epaddproject.org/using-epadd/user-guide) pour plus d'informations.
8. *Étiquettes* : Résumé des étiquettes utilisées. De nouvelles étiquettes peuvent être ajoutées ici si nécessaire.
9. *Données* : Journal d'importation.
   1. S'assurer qu'il n'y a pas eu d'erreurs d'importation majeures.


### L'onglet Recherche
En plus de l'utilisation des lexiques, l'onglet Recherche permet la recherche par mot-clé. Vous pouvez l’utiliser si vous remarquez que des courriers électroniques hors du champ d'application ne sont pas signalés par la recherche dans les lexiques. Par exemple, dans le fonds AP195, la créatrice des archives a utilisé son courrier électronique personnel pour trouver un nouvel appartement. Aucun des mots pertinents n'a été repéré par les lexiques, et des termes de recherche par mot-clé comme "loyer", "bail" et "appartement" ont permis de filtrer ce matériel.

### L'onglet Autorités
L'onglet Autorités peut être utilisé pour attribuer des noms d'autorités de LCNAF, VIAF, FAST et Wikipédia. Les pratiques descriptives actuelles du CCA n'impliquent pas d'analyse approfondie du sujet ; cependant, l'attribution d'autorités à ce stade pourrait être utile pour une description et un accès ultérieurs, notamment pour remplir le champ "Noms" pour la description au niveau du fichier.


### Exportation vers le module de livraison
Lorsque vous avez terminé de consulter tous les courriels, vous pouvez les exporter vers les modules ePADD suivants, Discovery et Delivery. Pour ce faire :

1. Cliquez sur l'onglet Exporter en haut de l'écran.
2. Sous "Exporter les messages et les pièces jointes", cliquez sur Parcourir, et choisissez C:/Utilisateurs/utilisateur. Cliquez sur Exporter (PAS "Exporter vers MBOX"). Cela peut prendre un certain temps. Cela permettra d'enregistrer deux dossiers de module : "ePADD archive of (archive creator) - delivery" et "ePADD archive of (archive creator) - discovery". Le dossier "Discovery" n'est pas utilisé au CCA et peut être supprimé.
3. Vous pouvez également exporter uniquement les pièces jointes aux courriels, ou les fichiers CSV des autorités assignées ou les lignes d'objet des courriels en fonction des besoins de traitement d'une collection particulière ; ces options sont également disponibles sur cet écran. Notez qu'ils exporteront TOUT ce qui se trouve dans le module d'évaluation, y compris les documents marqués "Ne pas transférer".
Notez que le fichier MBOX final ne doit pas être exporté du module d'évaluation, car il comprendra tous les documents à diffusion restreinte.

<a name="livraison"></a>
## Module de livraison
Le module de livraison est l'interface d'accès destinée aux chercheurs. Il est également utilisé pour créer une copie de préservation finale des fichiers. Il peut être ouvert dans l'onglet "mode ePADD", comme pour les autres modules. Pour lancer le module de livraison :


1. Déplacer le fichier "Archive of (Archive Creator) Delivery module" (exporté depuis le module d'évaluation) vers un dossier intitulé "epadd-delivery" dans C:/Users/user
2. Lancer ePADD.
3. Cliquez sur l'engrenage dans le coin supérieur droit et sélectionnez "ePADD Mode". Dans le menu déroulant, choisissez "LIVRAISON".
Afin d'exporter une copie de préservation au format MBOX :


1. Naviguez jusqu'à l'onglet "Recherche".
2. Sans rien saisir dans la barre de recherche, cliquez sur "Recherche". Ceci devrait retourner tous les courriels de la collection.
3. Cliquez sur le bouton "Exporter ces messages au format MBOX" (la flèche vers le bas). ePADD préparera votre fichier MBOX. Cela peut prendre un certain temps.

![Screenshot of Export button](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/epadd_export.JPG)


4. Sur l'écran suivant, cliquez sur "Télécharger le fichier MBOX". Cela peut prendre un certain temps et échoue souvent. Il est recommandé d'utiliser Internet Explorer pour cette étape.
5. Ce MBOX est prêt à être empaqueté dans un SIP à l'aide de [SIP Creator](https://github.com/CCA-Public/sipcreator). Une fois le SIP intégré, veillez à inclure votre rapport Emailchemy, ainsi que tout rapport CSV supplémentaire, dans le dossier des métadonnées de votre SIP.


Pour l'AP195, les fichiers originaux et le module d'évaluation ont été conservés, puisque la technologie de traitement du courrier électronique et les workflows s'améliorent rapidement. Il est possible que nous voulions revenir à ces fichiers tels qu'ils étaient à l'origine au moment où la restriction sera levée. Ces fichiers ont été regroupés dans leur propre SIP et leur accès est restreint.


### Quitter le module de livraison
Une fois dans le module de livraison ePADD, vous ne pouvez pas facilement revenir aux modules précédents. Ceci est mis en place afin d'éviter que les chercheurs n'interfèrent avec les collections en cours (c’est le cas pour le module de découverte.) Pour revenir aux modules précédents :


1. Notez quel hôte local ePADD utilise, en consultant l'URL de votre navigateur. (Il s'agit généralement de 9099.)
2. Fermez tous les onglets ePADD de votre navigateur.
3. Lancez le terminal et exécutez la commande suivante, où localhost est remplacé par le numéro noté à l'étape 1
```netstat –ano |findstr :localhost```
4. Cela permettra de restituer un certain nombre de valeurs. Cherchez l'endroit où il est indiqué "LISTENING" et notez le chiffre qui s'y trouve. Ce numéro est appelé un identificateur de processus, ou PID.
5. Exécutez la commande suivante dans le terminal, en remplaçant le PID par le numéro noté à l'étape 4 :
```tskill PID```
6. Relancer ePADD. Il démarrera par défaut dans le module d'évaluation.
Il est également possible de se déconnecter du poste de travail et de se reconnecter.

## Accès au courrier électronique
Afin de permettre l'accès à ces fichiers, le fichier MBOX du SIP peut être réimporté dans ePADD et passer par chaque phase d'exportation vers le module Delivery. Le chercheur peut utiliser le module Delivery pour naviguer dans les archives de courrier électronique en utilisant un grand nombre des mêmes outils que ceux dont disposait l'archiviste pendant le traitement. Il peut marquer et annoter des documents, comme dans les modules d'évaluation et de livraison. Il peut également enregistrer et télécharger une version annotée des archives de courrier électronique pour son usage personnel.


Les fichiers MBOX peuvent également être ouverts à l'aide d'autres outils de messagerie électronique, comme [Thunderbird](https://www.thunderbird.net/), ou dans un éditeur de texte.
## Nettoyer ePADD
Pour chaque module, ePADD enregistre son contenu dans un répertoire correspondant dans C:/Users/user. Tous les courriers électroniques de ces répertoires s'afficheront dans le module correspondant, quelle que soit leur provenance, ce qui signifie qu'ils doivent être supprimés entre les projets de traitement afin d'éviter tout mélange accidentel. Afin d'assainir ePADD :


1. Allez à C:/Users/user.
2. Il y aura un certain nombre de répertoires dont les titres commencent par "epadd-". Supprimez tous ces répertoires SAUF les "epadd-settings".
ePADD peut maintenant être utilisé pour traiter un nouveau groupe de courriels.
