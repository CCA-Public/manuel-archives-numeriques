# L'acquisition et la stabilisation des archives nées numériques

Ce guide décrit les normes du CCA pour l'acquisition et la stabilisation des documents d'archives nés numériques, quelle que soit la forme sous laquelle ils arrivent au CCA. Il comprend :

* [Aperçu général](#aperçu)
* [Transferts de fichiers en réseau](#transferts)
* [Supports physiques temporaires](#supports_temps)
* [Supports physiques originaux](#supports_originaux)
* [Ingestion des données brutes dans un dépôt numérique](#integrer)

<a name="aperçu"></a> 
## Aperçu général

En général, le contenu numérique arrive au CCA par l'une des trois façons suivantes : sous forme de transfert réseau (par exemple FTP, Dropbox, WeTransfer), sur des supports physiques temporaires (par exemple clé USB, disque dur externe) ou sur des supports physiques originaux (par exemple disquette, CD, DVD). Une seule acquisition (versement) peut contenir des fichiers numériques envoyés par l'une ou l'ensemble de ces trois méthodes.

Les directives suivantes décrivent comment le CCA procède pour acquérir et stabiliser le contenu numérique d'un versement et la manière dont le CCA ingère le contenu brut dans son système de préservation numérique, une fois toutes les étapes préparatoires complétées.

<a name="transferts"></a>
## Transferts de fichiers en réseau
Étapes :
* **Le membre du personnel qui reçoit le transfert (généralement l'Archiviste Numérique ou un membre de l'équipe de gestion de collection, GesCo)**
   * Aviser l'équipe GesCo ou l'archiviste numérique dès la réception du transfert.
   * Compresser les fichiers et déplacer le fichier nouvellement compressé dans le répertoire Processing du serveur de fichiers.
* **GesCo : Création de l'acquisition dans TMS**
   * Pour les acquisitions comprenant exclusivement des archives nées numériques, ne créer qu'un numéro de versement dans TMS (pas de versement-objet ni de numéro ARCH). Inclure une brève note permettant d'identifier l'acquisition dans la section "Description du contenu". Par exemple, vous pouvez utiliser le nom du dossier Dropbox de l'acquisition.
   * Pour les acquisitions de photos ou de P&D, créer des enregistrements de groupe ou de pièce comme d'habitude.
* **Archiviste numérique : ingestion**
   * Ajouter de l'information concernant le contenu des fichiers nouvellement acquis dans la section "Description du contenu" dans TMS.
   * Emballer le fichier compressé sous forme de SIP (paquet d'information à archiver) et ingérez-le dans Archivematica en suivant les [procédures d'ingestion des données brutes](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/stabilization.md#rawingest).
   * Faire une demande de déplacement auprès de GesCo afin de déplacer les fichiers vers l'emplacement "Dark Archive" dans TMS.
   * Supprimer les fichiers inutiles dans le répertoire Processing, Digital Shipping Space ou sur les postes de travail BitCurator.
* **GesCo**
   * Ajouter "Dark Archive" comme emplacement du versement dans TMS.

<a name="supports_temps"></a>
## Supports physiques temporaires
Étapes : 
* **GesCo : Créer des dossiers d'acquisition**
   * Pour les archives, créez uniquement un enregistrement de versement (pas d'objet de versement ou d'enregistrement ARCH). Inclure une brève note dans la "Description du contenu" indiquant comment les fichiers sont arrivés (par exemple "Fichiers arrivés au CCA sur une clé USB de 64 Go")
   * Pour Photo/P&D, créez des enregistrements de groupe ou de pièce comme d'habitude
* **Archiviste numérique : ingérer**
   * Ajouter une brève note descriptive sur le contenu au versement "Description du contenu".
   * Emballer le contenu sous forme de SIP Archivematica et l'ingérer dans Archivematica, en suivant les [procédures d'ingestion des données "brutes"](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/stabilization.md#rawingest).
   * Faire une demande de déplacement des fichiers à localiser vers Dark Archive.
   * Supprimer les copies de fichiers inutiles de Digital Shipping Space, des postes de travail BitCurator, etc.
   * Reformater (effacer) le support et le retourner au donneur ou à la donatrice, le réutiliser ou le jeter.
* **GesCo**
   * Ajouter "Dark Archive" comme emplacement du versement dans TMS.

<a name="supports_originaux"></a>
## Supports physiques originaux
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
* **Archiviste numérique en chef**
   * Pendant ou après le traitement, l'Archiviste numérique en chef évalue la valeur artéfactuelle de chaque support physique original. Cette évaluation peut aboutir à trois résultats :
      * Les supports ont une valeur artéfactuelle et seront conservés en permanence au CCA dans leur intégralité.
      * Les supports ont une valeur artéfactuelle et un échantillon (un seul support) sera conservé en permanence au CCA.
      * Les supports n'ont pas de valeur artéfactuelle et seront détruits ou retournés au donateur ou à la donatrice.
   * Au CCA, tous les supports sont conservés uniquement pour leur valeur artéfactuelle et non comme supports de stockage ou de sauvegarde. L'Archiviste en chef doit alors prendre la décision finale de ce qui doit être fait en terme de description et de classification pour ces supports. Lorsqu'on se débarrase d'un support physique original, l'archiviste chargé du traitement doit l'indiquer dans TMS dans la section "Évaluation-destruction" au niveau du fonds.

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
