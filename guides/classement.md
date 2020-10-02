# Classement des archives de personnes nées-numériques
La première étape du traitement des archives (qu'elles soient en format numérique ou analogique) est la classification. Ce guide décrit l'approche du CCA en matière de classement des archives nées numériques et comprend :


* [Le principe de l'organisation des archives de personnes nées numériques](#principe)
* [Facteurs affectant l'organisation des archives nées numériques](#facteurs)
  * [L’arrivée des archives au CCA](#arriver)
    * [Les gros transferts](#gros_transferts)
    * [Répartition des archives sur des supports de stockage plus petits](#repartition)
  * [Organisation existante](#existante)
  * [Contexte de création et d'utilisation](#contexte)
  * [Nature de la collection d'archives](#nature)
  * [Priorités institutionnelles](#priorities)
  * [Élaboration d'un plan de traitement](#elaboration)
  * [SIP non emballé (de préférence)](#non_emballe)
  * [SIP emballé (juste au cas où - il n'y a normalement aucune raison de créer un SIP sous cette forme)](#emballe)
* [Traitement des images disque avec Disk Image Processor](#disk_image_processor)
* [Traitement des répertoires de fichiers avec Folder Processor](#folder_processor)
* [Normalisation manuelle pour Archivematica](#normalisation)
* [Traitement des dossiers en cours de migration](#migration)
    

<a name="principe"></a>
## Le principe de l'organisation des archives de personnes nées numériques


Il existe un certain nombre d'approches pour organiser les documents nés numériques, en particulier lorsque ces documents ne constituent qu'une partie d'une archive hybride. Il est possible d'organiser les enregistrements numériques :


* Dans une série séparée "born-digital" (par exemple Fonds -> Série : Fichiers numériques)
* Dans des sous-séries distinctes "nées-numériques" au sein de séries existantes (par exemple Fonds -> Série : Projets -> Sous-série : Fichiers numériques)
* Co-arrangé avec d'autres formats (par exemple Fonds -> Série : Projets -> Fichier de projet : Exemple de projet -> Groupe de modèles numériques 3D au niveau du fichier)


Au CCA, nous pouvons adopter l'une ou l'autre de ces approches pour un projet de traitement numérique. L'approche adoptée dépend d'un certain nombre de [facteurs](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/arrangement.md#arrfactors), dont des priorités institutionnelles, la classification établie lors de l’arrivée des documents au CCA, de l'état d'organisation des documents, du contexte de création et d'utilisation active des documents, de l'utilisation anticipée pour les chercheurs et des exigences de notre interface d'accès aux archives nées numériques. Le plus souvent, nous chercherons à regrouper les documents nés numériques avec des documents similaires dans d'autres formats lorsque cela est possible.


Comme pour les documents physiques, le niveau de travail impliqué dans l'arrangement variera selon les fonds et les projets de traitement. Dans certains cas, il est nécessaire de conserver et de décrire tous les fichiers d'un même support en tant que groupe au niveau du fichier. Dans d'autres cas, il peut s'agir d'identifier différents répertoires stockés sur le même support physique en tant que groupes distincts et de les organiser en différents fichiers ou séries de projets. Il peut également être logique de regrouper des fichiers qui avaient été enregistrés sur des supports de stockage distincts.


Il est toujours préférable, à moins de circonstances extraordinaires (qui doivent être discutées avec l'archiviste numérique lors des réunions de prétraitement et/ou des vérifications en cours de traitement), d’organiser des répertoires et non des fichiers individuels.

<a name="facteurs"></a>
## Facteurs affectant l'organisation des archives nées numériques
Comme indiqué ci-dessus, les pratiques en matière d’organisation varient en fonction d'un certain nombre de facteurs. Notamment les suivants:

<a name="arriver"></a>
### L’arrivée des archives au CCA
Les archives peuvent être transférées vers le CCA de deux façons : soit sous la forme d'un ou de plusieurs gros transferts (comme un disque dur ou un transfert réseau) ou réparti sur de nombreux petits supports de stockage (comme des disquettes ou des CD). La forme sous laquelle les archives numériques ont été stockés et sont parvenues au CCA définit les paramètres de l’organisation et de la classification des archives pendant le traitement.

<a name="gros_transferts"></a>
#### Les gros transferts
* (Par exemple, le contenu entier d'un disque dur ou un transfert de réseau important)
* Plus susceptibles de conserver leur structure organisationnelle d'origine
* Plus susceptibles de contenir des liens inconnus entre les dossiers qui pourraient se briser avec le réarrangement
* Une description de plus haut niveau et un traitement moins manuel pourraient être préférables

<a name="repartition"></a>
#### Répartition des archives sur des supports de stockage plus petits
* Le matériel a-t-il été compartimenté sur différents supports par nécessité ou cela reflète-t-il un choix organisationnel ?
* Il est plus probable qu'il y ait un rapport détaillé en lien avec du matériel physique spécifique (par exemple, une disquette dans un dossier contenant de la correspondance ou des dossiers de projet)
* Les documents situés au même endroit nécessitent un classement plus actif et/ou une description plus précise

<a name="existante"></a>
### Organisation existante
Un autre facteur à prendre en compte est l'organisation existante du matériel. L'ordre existant semble-t-il avoir un sens ? Existe-t-il des preuves selon lesquelles cette organisation constitue un ordre original, tel qu'utilisé par le créateur des archives? L'ordre existant reflète-t-il une approche de gestion volontaire ou résulte-t-il simplement des contraintes matérielles des supports de stockage (par exemple, une sauvegarde répartie entre plusieurs disquettes ou CD en raison de l'espace de stockage limité sur chaque disque) ? La documentation produites par les créateurs de disques et/ou les sources de dons peut grandement aider à tirer ces conclusions.


L’organisation initiale du matériel doit être considérée en fonction des besoins des utilisateurs. L'ordre existant est-il évident ou accessible aux chercheurs ? Peut-il être plus être plus accessible par le biais de fonds, séries et descriptions au niveau des dossiers ? Si la réponse à ces deux questions est négative, la situation peut nécessiter une réorganisation ou une autre méthode de traitement.


En cas de réorganisation, nous mettrons à la disposition des chercheurs des informations sur l'organisation antérieure des dossiers au moment du transfert, tels que des documents Excel joints à la description du fonds.

<a name="contexte"></a>
### Contexte de création et d'utilisation 
Le contexte de création et d'utilisation des dossiers est un autre facteur à prendre en compte. Quelles relations, le cas échéant, les documents numériques ont-ils avec les documents analogiques et physiques du fonds ? Des documents de différents formats ont-ils été conservés ensemble lorsque les documents étaient en cours d'utilisation ?


Quelles sont les relations entre les dossiers du fonds ? Les fichiers sont-ils liés à des références externes (par exemple, un bloc titre utilisé dans un certain nombre de fichiers AutoCAD) ? Si oui, quel travail doit être effectué pour s'assurer que nous ne brisons pas les liens vers de telles ressources externes ?

<a name="nature"></a>
### Nature de la collection d'archives
Un autre facteur à prendre en compte lors de la réflexion sur l'organisation est la nature des archives auxquelles les documents appartiennent. Le CCA a-t-il acquis l'intégralité du fonds de ce créateur ou les documents appartiennent-ils à un projet d'archives ou à un ensemble d'archives ? Le CCA s'attend-il à recevoir d'autres acquisitions qui devront être intégrées dans les archives à une date ultérieure ?

<a name="priorities"></a>
### Priorités institutionnelles
* Lien avec d'autres projets CCA
* Utilisation anticipée par les chercheurs

<a name="elaboration"></a>
## Élaboration d'un plan de traitement
Une fois les copies de consultation des dossiers, rapports et autres documents placées dans le réseau des catalogueurs, l'archiviste chargé du traitement doit se familiariser avec le matériel pendant une à deux semaines. Cela a lieu pendant ou juste après la phase d'enquête et implique l'analyse de la structure organisationnelle des documents, la lecture de la documentation et la consultation des fichiers sur les ordinateurs et/ou sur l'un des postes de travail CAO.


Après cette période, l'archiviste chargé du traitement, l'archiviste numérique, le conservateur, l'archiviste/directeur associé et les parties prenantes des autres divisions du CCA tiendront une réunion de prétraitement. Dans le cadre de cette réunion, les participants analysent collectivement les rapports, rédigent un plan de classification, fixent des normes descriptives pour le projet (si elles doivent différer de la pratique habituelle), identifient les problèmes de préservation, dont la normalisation du format de fichier (si nécessaire), discutent de la manière dont les supports de stockage physique originaux seront traités et fixent les dates pour les étapes subséquentes du projet. Au cours de la réunion, les décisions sont officialisées par la création d'un document de plan de traitement qui est conservé dans le dossier "Acquisition et traitement" du projet.
## Emballage des SIP pour Archivematica
Une fois le contenu de votre SIP déterminé, les outils de workflow du CCA tels que le  [Folder Processor et le Disk Image Processor](https://github.com/CCA-Public/cca-tools) aident à standardiser chaque SIP afin qu'il réponde aux exigences du CCA en matière d'intégration dans Archivematica. Tous les SIP doivent avoir l'une des deux structures suivantes :

<a name="non_emballe"></a>
### SIP non emballé (de préférence)
* Dossier d'information sur la soumission (SIP) : Nommé d'après l'identifiant (généralement, un numéro AP ou ARCH)
   * `objects/`: dossier pour les objets numériques à ingérer
      * `diskimage/` : (dossier optionnel, à utiliser uniquement lorsque l'image disque et les fichiers sont ingérés ensemble)
      * `files/` : (dossier optionnel, à utiliser uniquement lorsque l'image disque et les fichiers sont ingérés ensemble)
   * `metadata/` : dossier pour les métadonnées associées aux objets numériques
      * `checksum.md5` : manifeste contenant les sommes de contrôle pour chaque fichier dans les objets
      * `submissionDocumentation/` : dossier contenant toute documentation supplémentaire relative aux objets numériques

<a name="emballe"></a>
### SIP emballé (juste au cas où - il n'y a normalement aucune raison de créer un SIP sous cette forme)
* Dossier d'information sur la soumission (SIP) : Nommé d'après l'identifiant (généralement, un numéro AP ou ARCH)
   * `bag-info.txt` : fichier bagit
   * `bagit.txt` : fichier bagit
   * `manifest-md5.txt` : fichier bagit
   * `tagmanifest-md5.txt` : fichier bagit
   * `data` : dossier bagit contenant le contenu du transfert
      * `objects/` : dossier pour les objets numériques à ingérer
         * `diskimage/` : (dossier optionnel, à utiliser uniquement lorsque l'image disque et les fichiers sont ingérés ensemble)
         * `files/` : (dossier optionnel, à utiliser uniquement lorsque l'image disque et les fichiers sont ingérés ensemble)
      * `metadata/` : dossier pour les métadonnées associées aux objets numériques
         * `submissionDocumentation/` : dossier contenant toute documentation supplémentaire relative aux objets numériques

<a name="disk_image_processor"></a>
## Traitement des images disque avec Disk Image Processor
*Instructions valables pour Disk Image Processor v1.0.0*


[Disk Image Processor](https://github.com/CCA-Public/diskimageprocessor) prend un dossier d'images disque et transforme son contenu en un SIP prêt à l'emploi, standardisé pour Archivematica. L'outil produit également un document Excel de description préremplie comprenant des informations pour chacun des SIP. Les SIP comprennent par défaut un fichier checksum.md5deepgenerated dans le répertoire "metadata", mais peuvent éventuellement être emballés à la place. L'outil remplit chaque répertoire "objects" par défaut avec des fichiers découpés de l'image disque par tsk_recover, HFSExplorer, ou une routine de montage et de copie, selon le système de fichiers détecté.


En option, il est possible de créer des SIP qui contiennent également une image disque brute (même si l'image disque source est EWF/E01) et les fichiers exportés. Les fichiers du répertoire source qui ne sont pas des images disque sont ignorés (à l'exception des fichiers qui partagent le même nom de base, tels que les fichiers de métadonnées .info sidecar pour les images disque, qui seront copiés dans le fichier "objects/diskimage" à la fin du traitement si l'utilisateur a choisi l'option de conserver les images disque dans le SIP).


Ce workflow suppose qu'une description au niveau du fichier sera attribuée à chaque élément du support de stockage dans une acquisition. Si le contenu des supports doit être divisé en plusieurs fichiers, une approche différente est nécessaire.


Pour ce parcours, nous commencerons par un exemple de répertoire contenant 4 images de disque :


![diskimage1](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/diskimage1.png)  


Étapes :


* Double-cliquez sur l'icône "Disk Image Processor" dans le dossier "CCA Tools" sur le bureau de Bitcurator.
![diskimage2](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/diskimage2.png)  


* Entrez le chemin du dossier source contenant les images disques dans "Source" (ou sélectionnez en utilisant le bouton "Parcourir") et le chemin d'un nouveau dossier pour les sorties dans "Destination". Choisissez parmi les options souhaitées. Appuyez sur le bouton "Start" pour commencer le traitement.


![diskimage3](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/diskimage3.png) 


* Lorsque l'outil a terminé le traitement, dans le dossier Destination, vous verrez maintenant ce qui suit : un fichier CSV contenant une description archivistique pré-remplie pour chaque image disque, un fichier journal pour l'outil Disk Image Processor, et un dossier contenant chaque SIP traité.


![diskimage6](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/diskimage6.png)  


![diskimage7](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/diskimage7.png) 


* Chaque SIP individuel contient une structure standard, comme le montre l'image ci-dessous. Au niveau le plus élevé, le SIP contient des dossiers "objet" et "métadonnées". Le dossier "objet" est subdivisé pour contenir une copie d'image disque brute et une copie de tous les fichiers découpés à partir de l'image disque. Le dossier "metadata" contient un fichier checksum.md5 qui peut être utilisé ultérieurement par Archivematica pour assurer la fixité du fichier et un dossier "submissionDocumentation", qui contient un rapport Brunnhilde pour le SIP, un fichier DFXML pour l'image disque et un fichier texte contenant la sortie du type de disque pour l'image disque brute.

![diskimage8](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/diskimage8.png)  

* À partir de là, il suffit de continuer à décrire les SIP dans le tableur et de renommer les répertoires SIP selon le schéma suivant : [identifiant]---[numéro d'accès].

<a name="folder_processor"></a>
## Traitement des répertoires de fichiers avec Folder Processor
* [Folder Processor](https://github.com/CCA-Public/folderprocessor) permet aux utilisateurs de créer des SIP de manière cohérente à partir de n'importe quel nombre de répertoires d'entrée sélectionnés. Chaque SIP est conditionné pour Archivematica et contient une copie des fichiers, un manifeste md5, un fichier DFXML et des rapports Brunnhilde.

![folderprocessor](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/folderprocessor.png)


Pour créer des SIP avec Folder Processor :
* Appuyez sur le bouton "Select source" en haut de l'interface graphique et choisissez le répertoire dans lequel vous voulez pouvoir sélectionner les répertoires d'entrée. La fenêtre "Directory Selector" se remplira alors d'une interface à cases à cocher.
* Sélectionnez tous les répertoires à partir desquels vous souhaitez créer des SIP en cochant la case située à gauche du nom du répertoire. Tous les fichiers sélectionnés seront ignorés.
* Saisissez la destination de vos SIP dans "Destination", soit en entrant le chemin d'accès au répertoire dans la case, soit en sélectionnant un dossier à l'aide du bouton "Parcourir". Dans ce dernier cas, vérifiez que le chemin d'accès est correct avant de continuer (il est facile de sélectionner accidentellement un répertoire supérieur à celui que vous souhaitez lorsque vous créez de nouveaux répertoires de sortie via l'interface graphique).
* Si vous le souhaitez, sélectionnez les options "Bag SIPs" ou "Run bulk_extractor". Dans la plupart des cas, ne cochez pas ces options.
* Lorsque vous êtes prêt à commencer, appuyez sur le bouton "Créer SIPs". Le processus commencera à fonctionner, et la barre d'état devrait s'incrémenter pour chaque répertoire qui est transformé avec succès en SIP. Soyez patient - pour les grands répertoires de saisie, cela peut prendre un certain temps. Si vous devez annuler le processus à tout moment, vous pouvez utiliser le bouton "Annuler" dans le coin inférieur droit de l'interface graphique.
* Lorsque le processus est terminé, le répertoire de destination contiendra une description CSV (contenant une description archivistique pré-remplie pour les SIP) et un répertoire contenant chacun des SIP. À partir de là, il suffit de continuer à décrire les SIP dans le tableur et de renommer les répertoires SIP selon le schéma suivant : [identifiant]---[numéro d'accès]. Les noms originaux des répertoires sont conservés dans le SIP au sein du répertoire "objets".
## Créer des SIP uniques à partir de répertoires et de fichiers avec SIP Creator
[SIP Creator](https://github.com/CCA-Public/sipcreator) permet aux utilisateurs de créer un SIP unique à partir d'un nombre quelconque de répertoires et de fichiers d'entrée. Le SIP qui en résulte est standardisé pour Archivematica et contient une copie des fichiers, un manifeste md5, un fichier DFXML et des rapports Brunnhilde.


![sipcreator](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/sipcreator.png)


Pour créer des SIP avec SIP Creator :


* Appuyez sur le bouton "Select source" en haut de l'interface graphique et choisissez le répertoire dans lequel vous voulez pouvoir sélectionner les fichiers. La fenêtre "Directory Selector" se remplira alors d'une interface à cases à cocher.
* Sélectionnez tous les fichiers et répertoires que vous souhaitez ajouter au SIP en cochant la case située à gauche du nom du fichier.
* Saisissez la destination de vos SIP dans "Destination", soit en entrant le chemin d'accès au répertoire dans la case, soit en sélectionnant un dossier à l'aide du bouton "Parcourir". Dans ce dernier cas, vérifiez que le chemin d'accès est correct avant de continuer (il est facile de sélectionner accidentellement un répertoire supérieur à celui que vous souhaitez lorsque vous créez de nouveaux répertoires de sortie via l'interface graphique).
* Si vous le souhaitez, sélectionnez les options "Bag SIP" ou "Run bulk_extractor". Dans la plupart des cas, ne cochez pas ces options.
* Lorsque vous êtes prêt à démarrer, appuyez sur le bouton "Créer SIP". Le processus commencera à fonctionner, et la barre d'état devrait s'incrémenter une fois que le SIP est créé, et de nouveau lorsque la description CSV a été générée. Soyez patient - pour les grands SIP, cela peut prendre un certain temps. Si vous devez annuler le processus à tout moment, vous pouvez utiliser le bouton "Annuler" dans le coin inférieur droit de l'interface graphique.
* Lorsque le processus est terminé, le répertoire de destination contiendra une description CSV (contenant la description archivistique pré-remplie pour les SIP) et un répertoire contenant le SIP nouvellement généré. À partir de là, il suffit de continuer à décrire le SIP dans le tableur (vous pouvez copier et coller cette ligne dans un tableur existant de manière à ce qu'il n'y ait pas de tableur pour chaque fichier) et de renommer le répertoire SIP selon le schéma suivant : [identifiant]---[numéro d'accès].


<a name="normalisation"></a>
## Normalisation manuelle pour Archivematica
Dans certains cas, Archivematica ne normalisera pas automatiquement les fichiers dans leur format de conservation. Cela se produit principalement dans les cas où un type de fichier n'est pas conforme aux spécifications et n'est pas reconnu par Siegfried, mais est tout de même lisible. (Voir les MP3 manipulés par le logiciel Virtools dans AP167 : ONL NSA Muscle project records pour un exemple). Lorsque cela se produit, ces types de fichiers peuvent nécessiter une normalisation manuelle pour être préservés. Cela ne devrait s’effectuer qu’uniquement dans les cas où les fichiers peuvent être facilement normalisés en lot, par un logiciel ou script OU lorsque certains fichiers de grande valeur sont identifiés.


* Créez le SIP comme d'habitude.
* Dans le dossier objects, créez un dossier intitulé manualNormalization.
* Dans le dossier manualNormalization, créez un dossier intitulé preservation.
* Dans le dossier preservation, recréez manuellement la structure du répertoire en commençant par le répertoire supérieur.
* Normalisez le(s) type(s) de fichier en utilisant la ligne de commande si possible. Enregistrez-les dans le répertoire en préservation qui correspond à leur répertoire d'origine.
La structure finale des répertoires du SIP doit ressembler à ce qui suit :
* répertoire principal
   * Metadata
   * Objects
      * nom du répertoire top (avec objets)
      * manuelNormalisation
         * Préservation
            * nom du répertoire principal
               * recréation de la structure des répertoires
                  * copies de conservation
* Mettez à jour le fichier checksum.md5 en conséquence. Pour ce faire, supprimez le fichier checksum.md5 original dans Top Directory/metadata. Ouvrez Terminal, et cd dans ce dossier. Exécutez ensuite le script suivant pour créer un nouveau manifeste 
```md5deep -rl ../objects > checksum.md5```
Dans certains cas, après l'ingestion, le rapport Archivematica pour le SIP normalisé manuellement aura un statut "échec" pour "Relier les fichiers de préservation normalisés manuellement aux fichiers originaux". Selon Archivematica, cela se produit lorsque deux ou plusieurs fichiers portent le même nom. En pratique, cela se produit aussi souvent lorsqu'il y a un grand nombre de fichiers dans un SIP ou si le SIP possède une hiérarchie de répertoires complexe.


Pour résoudre l'erreur, créez une feuille de calcul normalization.csv en suivant les instructions données [ici](https://www.archivematica.org/en/docs/archivematica-1.6/user-manual/ingest/manual-normalization/#normalizing-files-with-the-same-name), mettez à jour la somme de contrôle et réanalysez le SIP.


<a name="migration"></a>
## Traitement des dossiers en cours de migration
À des fins d'exposition, de recherche et d'accès, certains documents, faisant partie de l'ensemble numérique d’origine, ont été transférés dans une version plus récente de leur format original. Ces nouvelles versions des documents pourraient être utilisées comme copies d'accès, car elles sont plus faciles à consulter à travers les outils du CCA. Vous trouverez ci-dessous les lignes directrices permettant de conserver ces documents et d'y donner accès, tout en conservant le lien avec leurs versions originales.


Rassemblez les fichiers migrés vers le format plus récent dans des dossiers de premier niveau, correspondant à une description existante au niveau du dossier. Il n'est pas nécessaire de recréer les répertoires car la structure originale sera fournie à travers les chemins d'accès aux fichiers dans la description archivistique.


Nommez le nouveau dossier de fichiers en utilisant le numéro de référence de sa source et ajoutez FM (forward-migrated) à la fin. Par exemple, si le dossier d'origine porte le numéro AP222.S2.002, le dossier contenant ses fichiers migrés vers le nouveau format sera identifié comme AP222.S2.002.FM. Les SIP peuvent maintenant être créés avec SIP Creator. Complétez le numéro d'identification du SIP avec son numéro d'accès correspondant : par exemple AP222.S2.002.FM---AR2020.0056


Il se peut qu'à l'avenir, un autre événement migratoire se produise. Par exemple, une nouvelle version du logiciel peut être publiée ou le CCA peut obtenir un nouveau logiciel pour des fichiers auparavant inaccessibles. Dans ce cas, créez un nouveau SIP avec les nouveaux fichiers migrés vers le nouveau format et conservez l'ancien. Le schéma de numérotation est le suivant : AP222.S2.002.FM1, AP222.S2.002.FM2, etc.


Une fiche descriptive correspondante doit être ajoutée dans TMS. Elle doit être disposée à côté de sa description d'origine au niveau du fichier ("est inclus dans" la même série ou le même projet). Elle doit également être liée à l'adhésion par "provient de". Veuillez vous référer à la norme descriptive FILE pour des orientations générales et à ce qui suit pour des considérations plus spécifiques :


* Code de référence (ISAD(G) 3.1.1)/Numéro d'objet :
   * Dupliquer le numéro de référence du dossier original et ajouter "FM" : par exemple :  AP222.S2.002.FM
* Titre (ISAD(G) 3.1.2)/Titre :
   * Suivez les directives de titrage pour la description au niveau du fichier. Le titre doit indiquer la nature des fichiers (c'est-à-dire qu'il s'agit de versions migrées vers l'avant). Le titre doit inclure un certain niveau de détail sur les formats, dans la mesure du possible, afin d'améliorer l'accès aux documents. Par exemple : "Fichiers à migration anticipée*Z 6 et 7 pour 3 des fichiers de travail numériques RUR".
* Scope and content note (ISAD(G) 3.3.1)/Description du contenu :
   * Détailler et contextualiser les fichiers qui ont été migrés : énumérer les chemins d'accès au fichier original et indiquer toute spécificité des nouvelles versions de fichiers si elles n'apparaissent pas dans la feuille de calcul de traitement. Se référer au numéro d'identification de la description de fichier de l'original. Ajouter des informations sur le processus de migration, si elles sont connues : qui, comment, quand et pourquoi. Par exemple : "Les fichiers ont été migrés par un collaborateur du CCA en 2014 dans le cadre de la préparation de l'exposition Archeology of the Digital Complexity and Convention".
* Caractéristiques physiques et exigences techniques (ISAD(G) 3.4.4)/Champ de description physique :
   * Indiquez le logiciel désigné pour l'accès aux fichiers. Par exemple : "Les fichiers peuvent être consultés en utilisant le formulaire*Z version 6 à 8".


Enfin, dans la note relative à la portée et au contenu du dossier, contenant les fichiers originaux (par exemple AP222.S2.002), indiquez que les fichiers ont été migrés vers une version plus récente du logiciel et donnez les titres des dossiers contenant les fichiers migrés (par exemple AP222.S2.002.FM). Énumérez les fichiers migrés et leurs chemins d'accès, et indiquez leur version de logiciel.


Si le nombre de fichiers rend ce type de liste difficile à inclure dans TMS, les archivistes doivent déplacer la liste vers un rapport ou un fichier readme dans le SIP migré vers l'avant.
