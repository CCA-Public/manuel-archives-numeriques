# L'acquisition et la stabilisation des archives nées numériques

Ce guide décrit les normes du CCA pour l'acquisition et la stabilisation des documents d'archives nés numériques, quelle que soit la forme sous laquelle ils arrivent au CCA. Il comprend :

* [Aperçu général](#aperçu)
* [Stabilisation](#stabilisation)
  * [Transferts de fichiers en réseau](#transferts)
  * [Supports physiques temporaires](#supports_temps)
  * [Supports physiques originaux](#supports_originaux)
* [Ingestion des données brutes dans un dépôt numérique](#integrer)

<a name="aperçu"></a> 
## Aperçu général

En général, le contenu numérique arrive au CCA par l'une des trois façons suivantes : sous forme de transfert réseau (par exemple FTP, Dropbox, WeTransfer), sur des supports physiques temporaires (par exemple clé USB, disque dur externe) ou sur des supports physiques originaux (par exemple disquette, CD, DVD). Une seule acquisition (versement) peut contenir des fichiers numériques envoyés par l'une ou l'ensemble de ces trois méthodes.

Les directives suivantes décrivent comment le CCA procède pour acquérir et stabiliser le contenu numérique d'un versement et la manière dont le CCA ingère le contenu brut dans son système de préservation numérique, une fois toutes les étapes préparatoires complétées.

Il est à noter qu'avant la réception d'une acquisition d'archives nées numériques, le CCA envoie 2 documents au donateur ou à la donatrice afin d'avoir une meilleure compréhension du contexte de création et de l'usage des fichiers numériques : [Le guide des donateurs et donatrices](https://github.com/CCA-Public/digital-archives-manual/blob/master/forms/ccaDonorTransferGuide.pdf) et [La fiche d'information sur la soumission des fichiers numériques](https://github.com/CCA-Public/digital-archives-manual/blob/master/forms/Submission_of_Digital_Files_Questionnaire.pdf), disponibles en anglais seulement.

Le présent guide a été mis à jour en 2025 suite à l'implémentation d'ArchivesSpace dans notre flux de travail.

<a name="stabilisation"></a> 
## Stabilisation

<a name="transferts"></a>
### Transferts de fichiers en réseau
Étapes :
* **Membre du personnel qui reçoit le transfert (généralement l'Archiviste Numérique): Réception**
   * Création de l'acquisition dans ArchivesSpace.
   * S'assurer que les documents administratifs relatifs à l'acquisition (ex. acte de donation, pro forma, inventaires, correspondance, documents d'expédition, etc.) se trouvent dans le dossier approprié situé sur le serveur.
   * Envoyer le transfert au Technicien/ à la technicienne aux Archives Numériques.
* **Technicien/ne aux Archives Numériques: Stabilisation**
   * Télécharger et sauvegarder le fichier dans le dossier _AP/CD_ du répertoire _Shipping Space_ situé sur le serveur de fichiers.
   * Lancer une analyse antivirus sur l'entièreté de l'acquisition.
   * Vérifier les métadonnées, spécifiquement la date de la dernière modification sur chacun des fichiers afin de s'assurer que rien n'a été modifié durant le transfert.
   * Comparer l'inventaire du donateur/ de la donatrice avec les fichiers reçus, si disponible.
   * Empaqueter les fichiers reçus en tant que SIP Archivematica (paquet d'information à archiver) en compressant les fichiers dans un des divers formats d'archive (zip, tar, rar, etc.).
   * Renommer le SIP selon les [procédures pour l'ingestion des données brutes](#integrer).
   * Aviser l'Archiviste Numérique que le SIP est prêt à être ingéré dans Archivematica.
* **Archiviste Numérique : ingestion**
   * Ingérer le SIP dans Archivematica en suivant les [procédures pour l'ingestion des données brutes](#integrer).
   * Supprimer toutes copies inutiles de fichiers dans le dossier _Processing_, _Digital Shipping Space_ ou sur les postes de travail BitCurator.
   * Demander au Technicien/ à la Technicienne aux Archives Numériques de mettre à jour le conteneur de l'acquisition dans ArchivesSpace pour refléter le nouvel emplacement.
* **Technicien/ne aux Archives Numériques: Mise à jour de l'emplacement**
   * Ajouter "Dark Archive" comme conteneur dans le dossier d'acquisition sur ArchivesSpace.

<a name="supports_temps"></a>
### Supports physiques temporaires
Étapes : 
* **Membre du personnel qui reçoit le support physique temporaire (généralement l'Archiviste Numérique): Réception** 
  * Création de l'acquisition dans ArchivesSpace.
  * S'assurer que les documents administratifs relatifs à l'acquisition (ex. acte de donation, pro forma, inventaires, correspondance, documents d'expédition, etc.) se trouvent dans le dossier approprié situé sur le serveur.
  * Donner le support physique temporaire au Technicien/ à la technicienne aux Archives Numériques.
* **Technicien/ne aux Archives Numériques: Stabilisation**
  * Utiliser le bloqueur d'écriture et le logiciel Guymager pour créer une image disque du support physique temporaire sur un des BitCurator. 
  * Lancer une analyse antivirus sur l'entièreté de l'acquisition.
  * Vérifier les métadonnées, spécifiquement la date de la dernière modification sur chacun des fichiers afin de s'assurer que rien n'a été modifié durant le transfert.
  * Comparer l'inventaire du donateur/ de la donatrice avec les fichiers reçus, si disponible.
  * Empaqueter les fichiers en tant que SIP Archivematica (paquet d'information à archiver) en compressant les fichiers dans un des divers formats d'archive (zip, tar, rar, etc.).
  * Renommer le SIP selon les [procédures pour l'ingestion des données brutes](#integrer).
  * Transférer le SIP vers le dossier AP/CD dans le répertoire _Shipping Space_ situé sur le serveur.
  * Aviser l'Archiviste Numérique que le SIP est prêt à être ingéré dans Archivematica et redonner lui le support physique temporaire.
* **Archiviste Numérique : ingestion**
  * Ingérer le SIP dans Archivematica en suivant les [procédures pour l'ingestion des données brutes](#integrer).
  * Supprimer toutes copies inutiles de fichiers dans le dossier _Processing_, _Digital Shipping Space_ ou sur les postes de travail BitCurator.
  * Demander au Technicien/ à la Technicienne aux Archives Numériques de mettre à jour le conteneur de l'acquisition dans ArchivesSpace pour refléter le nouvel emplacement.
  * Reformater (effacer) le support et le retourner au donateur ou à la donatrice, le réutiliser ou le détruire selon le cas.
* **Technicien/ne aux Archives Numériques: Mise à jour de l'emplacement**
   * Ajouter "Dark Archive" comme conteneur dans le dossier d'acquisition sur ArchivesSpace.

<a name="supports_originaux"></a>
### Supports physiques originaux
Note : Il s'agit d'une vaste catégorie qui inclut les disquettes, les supports optiques (CD/DVD), les ordinateurs, les disques durs internes et les stockages à bandes magnétiques tels que les LTO par exemple. Pour vous aider à identifier correctement les types de supports, veuillez consulter le [guide d'identification des supports informatiques](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/mediaIDGuide.docx) ou la page ["Know Your Media"](http://lib.utsa.edu/knowyourmedia/) des bibliothèques de l'Université du Texas à San Antonio (UTSA).

Étapes :
* **GesCo**
   * Créer l'acquisition dans TMS comme décrit ci-dessus.
   * À l'arrivée des boîtes d'archives, déterminer s'il est possible de séparer les supports numériques.
   * SI OUI : GesCo sépare les supports numériques des documents papiers (entreposé sur les étagères de la chambre froide) et crée des versement-objets distincts par conteneur.
   * SI NON : GesCo doit indiquer dans TMS dans la section "Description du contenu" de la page du versement-objet que le versement contient des supports numériques. Le matériel numérique sera ensuite stabilisé par le technicien ou la technicienne des archives numériques ou le versement-objet sera ajouté dans le fichier du "Backlog Project". 
* **Archiviste numérique**
   * Note : Ces étapes peuvent ne pas être réalisées immédiatement.
   * Superviser le technicien ou la technicienne des archives numériques lors de la tâche de la création d'images disques.
   * Si le versement ne peut pas être traité immédiatement, regrouper toutes les images disques dans un seul SIP et ingérer le SIP dans Archivematica en suivant les [procédures d'insertion des données "brutes"](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/stabilization.md#rawingest).
   * Faire une demande de déplacement auprès de GesCo afin de changer l'emplacement du versement-objet dans TMS au "Dark Archive".
   * Supprimer les fichiers inutiles dans le répertoire Digital Shipping Space ou sur les postes de travail BitCurator.
* **GesCo**
   * Ajouter "Dark Archive" comme emplacement du versement dans TMS.
* **Archiviste Numérique**
   * Pendant ou après le traitement, l'Archiviste Numérique évalue la valeur artéfactuelle de chaque support physique original. Cette évaluation peut aboutir à trois résultats :
      * Les supports ont une valeur artéfactuelle et seront conservés en permanence au CCA dans leur intégralité.
      * Les supports ont une valeur artéfactuelle et un échantillon (un seul support) sera conservé en permanence au CCA.
      * Les supports n'ont pas de valeur artéfactuelle et seront détruits ou retournés au donateur ou à la donatrice.
   * Au CCA, tous les supports sont conservés uniquement pour leur valeur artéfactuelle et non comme supports de stockage ou de sauvegarde. L'Archiviste Numérique doit alors prendre la décision finale de ce qui doit être fait en terme de description et de classification pour ces supports. Lorsqu'on se débarrase d'un support physique original, l'archiviste chargé du traitement doit l'indiquer dans TMS dans la section "Évaluation-destruction" au niveau du fonds.

<a name="integrer"></a>
## Ingestion des données brutes dans un dépôt numérique
Une fois que l'archiviste au traitement ou que le technicien/ la technicienne ait téléchargé les fichiers et stabilisé tous les supports physiques ou temporaires, l'acquisition doit être ingérée dans le dépôt numérique du CCA, Archivematica. Le but de cette étape est de conserver et de stocker en toute sécurité une copie des données telles qu'elles sont arrivées au CCA. 

**Il est à noter que tous les fichiers provenant de transferts en réseau ou de supports temporaires doivent être exportés dans un format d'archive approprié (zip, tar, rar, etc.), faute de quoi Archivematica modifiera les noms des fichiers et les dates de créations des fichiers, allant à l'encontre de l'ingestion brute des données sans modification aucune. 
Au CCA, nous préférons créer nos SIP en utilisant le format tar. Il est alors suggéré de bien vérifier que les fichiers ont été compressés avec succès et qu'ils peuvent être rouverts, car les fichiers zip défectueux peuvent entraîner la perte de documents et donc, de matériel de collection. Notez également que cette étape peut être facultative si les images disques doivent être conservées.**

Ce SIP est composé de tous les fichiers, les paquets d'archives et les images disques en lien avec l'acquisition. Il est nommé selon la convention de nommage suivante `<numéro d'acquisition>_raw`, toute la ponctuation est remplacée par des traits de soulignement (par exemple, `AR2018_0001_raw`).


Pour l'ingestion de données brutes non traitées, nous utilisons le pipeline de traitement VSP-AMPL-01. Dans ce pipeline, Archivematica est configuré par défaut pour ne pas extraire de paquets, examiner le contenu ou normaliser les fichiers.

**Procédure**:


1. Créez un SIP nommé `<numéro d'acquisition>_raw`, contenant les fichiers tels qu'envoyés par le donateur et/ou les images disque. Si une acquisition n'a pas encore été créée dans TMS, stockez temporairement le SIP dans l'espace d'expédition numérique jusqu'à ce que le numéro d'acquisition ait été attribué et qu'un enregistrement ait été créé dans TMS.
2. Copiez le SIP dans le pipeline VSP-AMPL-01 à l'aide du script `send_to_archivematica.py.`
3. (Administrateur Digital Archivist/Archivematica) Déplacez le SIP dans le dossier surveillé Automation Tools pour l'ingérer. Suivez les procédures d'ingestion et d'assurance qualité habituelles.
Une fois l'acquisition ingérée dans Archivematica, supprimez toute copie supplémentaire des machines BitCurator, Digital Shipping Space, etc. et demandez à Déplacement de mettre à jour l'emplacement des enregistrements d'acquisition appropriés à "Dark Archive".
