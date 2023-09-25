# L'acquisition et la stabilisation des archives nées numériques

Ce guide décrit les normes du CCA pour l'acquisition et la stabilisation des documents d'archives nés numériques, quelle que soit la forme sous laquelle ils arrivent au CCA. Il comprend :

* [Aperçu général](#aperçu)
* [Transferts de fichiers en réseau](#transferts)
* [Supports physiques temporaires](#supports_temps)
* [Supports physiques originaux](#supports_originaux)
* [Ingestion des données brutes dans un dépôt numérique](#integrer)

<a name="aperçu"></a> 
## Aperçu général

En général, le contenu numérique arrive au CCA de l'une des trois façons suivantes : sous forme de transfert réseau (par exemple FTP, Dropbox, WeTransfer), sur des supports de transfert physique temporaires (par exemple clé USB, disque dur externe) ou sur des supports de stockage physique originaux. Un seul dépôt (versement) peut contenir des fichiers numériques arrivés au CCA par l'une ou l'autre de ces méthodes.

Les procédures suivantes décrivent comment le CCA procède aux versements et stabilise le contenu de chacune de ces méthodes de versement, ainsi que la manière dont le CCA ingère le contenu brut d'un versement dans son dépôt numérique, une fois toutes les étapes préparatoires complétées.

<a name="transferts"></a>
## Transferts de fichiers en réseau
Étapes :
* **Le membre du personnel qui reçoit le transfert (généralement l'Archiviste Numérique ou un membre de l'équipe de gestion de collection, GesCo)**
   * Aviser l'équipe GesCo et l'archiviste numérique, le cas échéant.
   * Compresser les fichiers et déplacez le fichier compressé dans le dossier d'acquisition Processing.
* **GesCo : Créer des dossiers d'acquisition**
   * Pour les entrées exclusivement numériques dans les archives, ne créer qu'une fiche de versement (pas d'objet de versement ou de fiche ARCH). Inclure une brève note d'identification de l'acquisition dans la "Description du contenu" (par exemple, le nom du dossier Dropbox)
   * Pour Photo/P&D, créez des enregistrements de groupe ou de pièce comme d'habitude
* **Archiviste numérique : ingérer**
   * Ajouter une brève note descriptive sur le contenu au versement "Description du contenu".
   * Emballer le contenu sous forme de SIP et l'ingérer dans Archivematica, en suivant les [procédures d'ingestion des données brutes](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/stabilization.md#rawingest).
   * Faites une demande de déplacement des fichiers vers l'emplacement "Dark Archive".
   * Supprimer les copies des fichiers non nécessaires de Digital Shipping Space, des postes de travail BitCurator, etc.
* **GesCo**
   * Ajouter "Dark Archive" comme lieu de l'enregistrement d'acquisition (par exemple, versement)

<a name="supports_temps"></a>
## Supports physiques temporaires
Étapes : 
* **GesCo : Créer des dossiers d'acquisition**
   * Pour les archives, créez uniquement un enregistrement de versement (pas d'objet de versement ou d'enregistrement ARCH). Inclure une brève note dans la "Description du contenu" indiquant comment les fichiers sont arrivés (par exemple "Fichiers arrivés au CCA sur une clé USB de 64 Go")
   * Pour Photo/P&D, créez des enregistrements de groupe ou de pièce comme d'habitude
* **Archiviste numérique : ingérer**
   * Ajouter une brève note descriptive sur le contenu au versement "Description du contenu".
   * Emballer le contenu sous forme de SIP Archivematica et l'ingérer dans Archivematica, en suivant les [procédures d'ingestion des données "brutes"](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/stabilization.md#rawingest).
   * Faites une demande de déplacement des fichiers à localiser vers Dark Archive.
   * Supprimer les copies de fichiers inutiles de Digital Shipping Space, des postes de travail BitCurator, etc.
   * Reformater (effacer) le support et le retourner au donneur, le réorienter ou le élagage selon le cas
* **GesCo**
   * Ajouter "Dark archive" comme lieu de l'enregistrement d'acquisition (par exemple, versement)

<a name="supports_originaux"></a>
## Supports physiques originaux
Note : Il s'agit d'une vaste catégorie qui peut inclure, par exemple, les disquettes, les supports optiques (CD/DVD), les ordinateurs, les disques durs internes, les formats de bandes de sauvegarde tels que les LTO, etc. Pour vous aider à identifier correctement les types de supports, veuillez consulter le [guide d'identification des supports informatiques](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/mediaIDGuide.docx) ou la page ["Know Your Media"](http://lib.utsa.edu/knowyourmedia/) des bibliothèques de l'UTSA.
Étapes :

* **GesCo**
   * Créer des dossiers d'acquisition comme décrit ci-dessus
   * Déterminer s'il est possible de séparer les médias numériques à l'arrivée
   * SI OUI : Le bureau d'enregistrement sépare les supports numériques des matériaux physiques à leur arrivée (stockés dans des rayonnages froids de la chambre forte) et crée des versement-objets distincts pour le(s) conteneur(s) des supports numériques.
   * SI NON : le bureau d'enregistrement note dans le champ "Description du contenu" des enregistrements d'objets de versement qu'ils contiennent des supports numériques. Ce matériel sera ensuite stabilisé selon les workflow de l'arriéré des médias par le technicien des archives numériques dans le cadre de son travail habituel ou au moment du traitement.
* **Archiviste numérique**
   * Note : Ces étapes peuvent être réalisées avec un certain retard
   * Superviser l'imagerie disque des médias
   * Si les archives ne doivent pas être traitées immédiatement, regroupez toutes les images disque dans un seul SIP Archivematica et insérez-le dans Archivematica, en suivant les [procédures d'insertion des données "brutes"](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/stabilization.md#rawingest).
   * Faites une demande de déplacement des fichiers à localiser vers Dark Archive.
   * Supprimer les copies de fichiers non nécessaires de Digital Shipping Space, des postes de travail BitCurator, etc.
* **GesCo**
   * Ajouter "Dark Archive" comme lieu de l'enregistrement d'adhésion (par exemple, versement)
* **Archiviste numérique, Archiviste/Chef/Curateur, Directeur associé**
   * **Note : Les politiques relatives à cette étape sont en cours de révision par Adria Seccareccia, Archiviste, en relation avec les politiques générales d’élagage du CCA**
   * Pendant ou après le traitement, l'Archiviste Numérique et soit l'Archiviste, soit le conservateur/chef approprié évaluent les supports pour leur valeur artéfactuelle et confirment avec le Directeur Associé de la Collection. Cette évaluation peut aboutir à trois résultats :
      * Les supports ont une valeur artéfactuelle et seront conservés en permanence au CCA dans leur intégralité
      * Les supports ont une valeur artéfactuelle et un échantillon sera conservé en permanence au CCA
      * Les médias n'ont pas de valeur artéfactuelle et seront détruits ou retournés au donateur
   * Tous les supports conservés au CCA sont conservés uniquement pour leur valeur artéfactuelle, et non comme supports de stockage ou "sauvegardes" de fichiers numériques dans la collection du CCA. La description et la disposition de ces objets doivent être discutées avec l'archiviste numérique et l'archiviste/chef/catalogueur approprié. Chaque fois que des supports sont retournés ou détruits, l'archiviste chargé du traitement en prend note dans le champ de saisie "Évaluation-destruction" du TMS au niveau du fonds.

<a name="integrer"></a>
## Ingestion des données "brutes" dans un dépôt numérique
Une fois les données de l'ensemble du transfert réseau, des supports temporaires et des supports originaux d'une acquisition stabilisées, la composante numérique de l'acquisition est ingérée dans le dépôt numérique du CCA basé sur Archivematica. Le but de cette étape est de conserver et de stocker en toute sécurité une copie des données exactement comme elles sont arrivées au CCA jusqu'à ce qu'un archiviste traite l'acquisition. **Il est à noter que tous les fichiers provenant de transferts en réseau ou de supports temporaires doivent être exportés dans un format d'archive approprié (zip, tar, rar, etc.), faute de quoi Archivematica modifiera les noms de fichiers et les horodatages originaux, allant à l'encontre d'une partie de l'objectif de l'ingestion "brute". Au CCA, nous préférons généralement conserver les fichiers tar. Vérifiez que les fichiers ont été compressés avec succès et qu'ils peuvent être rouverts, car les fichiers zip défectueux peuvent entraîner la perte du matériel de collection. Notez également que cette étape peut ne pas être nécessaire si les images disque doivent être conservées comme partie du matériel traité.**
Ce SIP est composé de tous les fichiers, paquets d'archives et images disques qui correspondent à une acquisition. Il est nommé selon la convention `<numéro d'acquisition>_raw`, toute la ponctuation est remplacée par des traits de soulignement (par exemple, `AR2018_0001_raw`).


Pour l'ingestion de données brutes non traitées, nous utilisons le pipeline de traitement VSP-AMPL-01. Dans ce pipeline, Archivematica est configuré par défaut pour ne pas extraire de paquets, examiner le contenu ou normaliser les fichiers.

**Procédure**:


1. Créez un SIP nommé `<numéro d'acquisition>_raw`, contenant les fichiers tels qu'envoyés par le donateur et/ou les images disque. Si une acquisition n'a pas encore été créée dans TMS, stockez temporairement le SIP dans l'espace d'expédition numérique jusqu'à ce que le numéro d'acquisition ait été attribué et qu'un enregistrement ait été créé dans TMS.
2. Copiez le SIP dans le pipeline VSP-AMPL-01 à l'aide du script `send_to_archivematica.py.`
3. (Administrateur Digital Archivist/Archivematica) Déplacez le SIP dans le dossier surveillé Automation Tools pour l'ingérer. Suivez les procédures d'ingestion et d'assurance qualité habituelles.
Une fois l'acquisition ingérée dans Archivematica, supprimez toute copie supplémentaire des machines BitCurator, Digital Shipping Space, etc. et demandez à Déplacement de mettre à jour l'emplacement des enregistrements d'acquisition appropriés à "Dark Archive".
