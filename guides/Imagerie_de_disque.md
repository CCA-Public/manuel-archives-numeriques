# Création d'images disques à partir d'un support physique

* [Création d'une image disque avec Guymager (BitCurator)](#guymager)
* [Création d'une image disque avec FTK Imager](#ftk)
* [Création d'une image disque avec IsoBuster](#isobuster)
* [Création d'une image disque avec FC5025](#fc5025)
* [Création d'une image disque avec Kryoflux](#kryoflux)
* [Création d'une image disque avec le Nimbie et ImgBurn](#nimbie)
* [Extraction d'un CD audio avec cdparanoia](#cdparanoia)
* [Dépannage](#depannage)

Au CCA, nous saisissons le contenu des médias physiques originaux sous forme d'images disque brutes. Une image disque est un fichier informatique qui consiste en une réplique exacte du contenu d'un disque ou d'un autre support de stockage numérique. Comme les images disques peuvent être stockées de façon redondante, sauvegardées et contrôlées, contrairement aux supports physiques tels les DVD ou les disques durs externes, elles sont mieux adaptées à la préservation des informations numériques. Elles assurent également la conservation de toutes les caractéristiques du support physique d'origine.

Sauf lorsque les circonstances demandent des solutions différentes, le CCA préfère les formats d'image disque brute (par exemple "dd" ou "raw") ou les images ISO (pour les supports optiques).

**Note : Afin de garantir que le média source reste inchangé par le processus de capture et de transfert des données, les disques durs et les lecteurs de médias amovibles doivent toujours être connectés au poste de capture par l'intermédiaire d'un bloqueur d'écriture.**

Nous utilisons les outils suivants pour créer des images de disques : Kryoflux (par défaut), Guymager, FTK Imager, IsoBuster, ou FC5025. Quel que soit l'outil que vous utilisez, commencez toujours par effectuer l'étape suivante :

Attribuez à chaque support numérique un identifiant AS (ArchivesSpace) si ce n'est pas déjà fait. Cet identifiant doit être inscrit sur le support et sur son boîtier au feutre ou au crayon (très légèrement), ou collé sur le boîtier en utilisant une étiqueteuse si disponible. Pour plus d'informations sur la création d'un identifiant AS, veuillez consulter le document « New Numbering Scheme for ArchivesSpace item-level records » disponible sur le serveur.

<a name="guymager"></a>
### Création d'une image disque avec Guymager (BitCurator)
Guymager est un outil open source de création d'images disques au format brut (.dd) que l'on trouve dans l'environnement BitCurator et c'est l'un des outils privilégiés au CCA. 

Avant de commencer à créer des images disques à partir d'une acquisition, créez un dossier dans le répertoire `/mnt/1TB_RAID` dans lequel vous enregistrerez votre travail. Donnez à ce dossier un nom mémorable et significatif, tel qu'un numéro d'acquisition ou un autre identifiant.

### Étapes :

* Avant de créer une image disque, faites un scan antivirus du support à l'aide de ClamAV.
   * S'il n'y a pas de virus, passez à l'étape suivante.
   * Si ClamAV trouve des virus, arrêtez-vous, notez le(s) virus rencontré(s) dans votre fichier de travail, mettez le support de côté et consultez l'archiviste numérique.
* Ouvrez Guymager (à partir du dossier "Imaging Tools" sur le bureau de Bitcurator).

![Bitcurator1](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/guymager_open.png)
* Faites un clic droit avec la souris sur le lecteur que vous souhaitez copier et sélectionnez "Acquire image". Si le lecteur/appareil que vous souhaitez copier n'apparaît pas, actualisez la fenêtre en cliquant sur "Rescan" dans le coin supérieur gauche de l'interface graphique Guymager.

![Bitcurator2](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/guymager1_AcquireImage.png)
*(Ces images ont été prises sur le site suivant : <a href="https://bitcurator.github.io/documentation/All%20Step-by-Step%20Guides/Imaging%20and%20Recovery%20Guides/Imaging%20with%20Guymager/">BitCurator Docs</a>)*

* Choisissez le format de fichier "Linux dd raw image" (extension de fichier .dd ou .xxx).
* Assurez-vous que l’option “Split size” ne soit pas cochée.
* Entrez les métadonnées/réglages suivants :
   * **Répertoire d'images** : Sélectionnez le répertoire que vous avez créé dans /mnt/1TB_RAID.
   * **Nom du fichier image** : entrez l'identifiant du disque sans espaces. Remplacez les deux points (':') par des traits de soulignement ('_').
   * **Nom de fichier info** : il devrait être créé automatiquement en fonction de votre nom de fichier image. Ne modifiez pas ce champ.
   * **Calcul/vérification du hachage** :
      * Cochez "Calculer MD5", "Calculer SHA-1", et "Vérifier l'image après acquisition".
      * Ne pas cocher les autres options


![Bitcurator2](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/guymager_settings.png)


* Une fois les paramètres confirmés, appuyez sur "Start" pour lancer le processus d'imagerie du disque.
* Guymager suivra sa progression et vous donnera des indications par code couleur lorsque le processus est achevé avec succès ou échoue. En cas d'échec, notez ce fait dans le document Excel de stabilisation du versement et mettez le disque de côté pour que l'archiviste numérique puisse l'examiner.
* Si l'image est créé avec succès, allez dans votre dossier de projet sur le bureau et faites une vérification visuelle rapide pour vous assurer que tout est en ordre. Vous devriez voir deux fichiers : l'image disque elle-même et un fichier de métadonnées ".info".
* Si tout semble correct, répétez ce processus avec le disque suivant jusqu'à ce que tous les supports aient été imagés. Une fois que tous les supports ont été imagés, alertez l'archiviste numérique.

<a name="ftk"></a>
### Création d'une image disque avec FTK Imager
AccessData FTK Imager est un outil d'imagerie de disque gratuit mais propriétaire utilisé sur l'un de nos ordianteurs Windows et fait partie de la suite logicielle Forensics Toolkit. Au CCA, nous utilisons FTK Imager pour créer des images disques pour des supports ne pouvant être traitées par Guymager.

FTK Imager est installé sur le poste de travail (DSK-065-14) situé dans laboratoire numérique du CCA. Avant de commencer la création d'images disques créez d'abord un dossier dans lequel vous allez enregistrer votre travail et donnez lui un nom significatif, par exemple un numéro d'acquisition ou d'identification.

#### Étapes :

* Avant de créer une image disque, effectuez une analyse antivirus à l'aide du logiciel SentinelOne :
   * Faite un clic droit sur le fichier ou sur le dossier que vous souhaitez analyser et sélectionnez l'option "Scan for threats" dans le menu déroulant.
   * Si le logiciel ne trouve pas de virus informatique, procédez à l'étape suivante. Sinon, arrêtez-vous et assurez vous de notez le ou les virus trouvé(s) dans le fichier de travail "versement_stabilization", alertez ensuite l'Archiviste Numérique.
     
* Ouvrez le logiciel FTK Imager.
* Dans le menu Fichier, sélectionnez "Create a disk image".
![FTK1](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/ftk_capture1-2.PNG)  

* Sélectionnez la source appropriée : Pour les disques durs la source appropriée sera "Physical Drive". Pour la plupart des autres types de supports (y compris les CD, les DVD et les disquettes), la source sera "Logical Drive".

![FTK2](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/ftk_capture2-1.PNG).

* Sélectionnez le lecteur approprié dans le menu déroulant.

![FTK3](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/ftk_capture3.PNG) 

* Sélectionnez "Add" pour ajouter la destination de l'image. Cochez "Verify images after they are created", mais laissez "Create directory listings..." non coché.

![FTK4](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/ftk_capture4.PNG)

* Sélectionnez le type d'image "raw (dd)".
  
* FTK vous demandera d'ajouter des métadonnées pour votre image disque. Entrez les métadonnées suivantes :
   * **Case number** : Numéro ou identifiant du versement
   * **Evidence number** : Identifiant du support physique numérique que vous désirez copier
   * **Unique description** : Entrez une brève description du support et/ou ses annotations (par exemple, disquette 3,5" portant la mention "FOA Photos 2002")
   * **Examiner**: Votre nom
   * **Notes** : Laissez ce champ vide

* FTK Imager va maintenant vous demander des informations sur l'endroit où enregistrer l'image disque et les fichiers de métadonnées qui en résultent. Saisissez les informations suivantes, puis sélectionnez "Finish" :
   * **Image destination folder** : Saisissez l'emplacement réseau de votre dossier de travail actuel.
   * **Image filename** : entrez l'identifiant du disque sans espaces. Remplacez les deux points (':') par des traits de soulignement ('_').
 
![FTK5](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/ftk_capture5.PNG)

* Vérifiez que la destination et les paramètres apparaissent correctement, puis sélectionnez "Start" pour lancer le processus de création d'image disque.

![FTK6](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/ftk_capture6.PNG)

* Une fenêtre de progression n'apparaîtra pas pour vous tenir informé de la progression de l'imagerie du disque. Si l'imagerie disque échoue ou semble être bloquée sur un grand nombre de secteurs défectueux, notez le dans le fichier Excel de stabilisation du versement et mettez le disque de côté pour que l'archiviste numérique puisse l'examiner.
* Si l'image est créée avec succès, allez dans votre dossier de projet dans le dossier Dépôt numérique et faites une vérification visuelle rapide pour vous assurer que tout semble bon. Vous devriez voir au moins deux fichiers : la ou les images disque elles-mêmes (éventuellement divisées en plusieurs fichiers portant le même nom mais avec des extensions .001, .002, etc.), un fichier de métadonnées ".txt"., ainsi qu’un fichier de métadonnées ".txt". Si tout semble correct, répétez ce processus avec le disque suivant jusqu'à ce que tous les supports aient été imagés. Une fois tous les supports imagés, alertez l'archiviste numérique.
* Note: Le processus d'imagerie de disque de l'imageur FTK est très persistant. Si le disque que vous voulez imager prend beaucoup de temps à traiter, il n'est pas nécessairement défectueux. L'imageur continuera d'essayer d'imager les secteurs du disque jusqu'à ce que ce soit fait. Il est toujours possible d'extraire une image utilisable d'un disque après 30 heures ou plus de tentatives, alors gardez cela à l'esprit.

<a name="isobuster"></a>
### Création d'une image disque avec IsoBuster
[IsoBuster ](https://www.isobuster.com/help/) est un outil d'imagerie de disque basé sur Windows et produit par Smart Projects (géré par Peter Van Hove). Au CCA, nous utilisons IsoBuster pour créer des images disques pour des types particuliers de supports optiques - principalement des DVD, des CD audio et des supports optiques contenant plus de 1024 Mo de données - et comme outil pour documenter l'état actuel des supports endommagés.

Avant de passer au processus d'imagerie de disque, assurez-vous que vous utilisez la station de travail d'imagerie de disque (DSK-065-14) du laboratoire numérique du CCA. Créez un dossier de projet dans lequel vous enregistrez votre travail. Donnez à ce dossier un nom mémorable et significatif, par exemple un numéro d'acquisition ou d'identification.

#### Étapes : 

* Étape 1 : Avant de créer une image disque, effectuez une analyse antivirus à l'aide du logiciel SentinelOne :
   * Faite un clic droit sur le fichier ou sur le dossier que vous souhaitez analyser et sélectionnez l'option "Scan for threats" dans le menu déroulant.
   * Si le logiciel ne trouve pas de virus informatique, procédez à l'étape suivante. Sinon, arrêtez-vous et assurez vous de notez le ou les virus trouvé(s) dans le fichier de travail "versement_stabilization", alertez ensuite l'Archiviste Numérique.
* Étape 2 : Ouvrez le logiciel IsoBuster et allez directement dans le menu Start pour vérifier les paramêtres suivants. Il se peut que vous deviez modifier certains paramètres en fonction des besoins de votre projet de préservation numérique.
   * **Image file size** : Allez à Image Files dans le menu Options , allez à *Image File Creation* images et décochez l'option *Split large Image Files to specified size*.
   * **Cuesheet file** : Toujours sous Image Files, allez à *Select when a cuesheet file will be created*, sélectionnez **Always after a CD, DVD or BD image is created**.
   * **MD5 checksum file** : Toujours sous Image Files, allez à *Select when an MD5 checksum file will be created* et sélectionnez **Always after an image is created**.
  
* IsoBuster lit automatiquement le contenu entier du disque et affiche une vue arborescente des fichiers dans la colonne de gauche. Si ce n'est pas le cas, sélectionnez le bon lecteur d'option dans la boîte déroulante sous le menu. Le message "No media present" s'affiche si aucun disque n'est monté sur le lecteur.
![IsoBuster](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/isobuster_01.PNG?raw=true)

* Le support détecté (CD/DVD, disquette) apparaît en haut de l'arborescence. Cliquez sur la flèche à gauche de l'icône du système de fichiers (par exemple, l'icône verte UDF nommée "board2" dans l'image ci-dessous) afin d'afficher la structure interne des dépôts. Lorsque vous sélectionnez un dépôt, son contenu s'affiche dans le volet de droite.
![IsoBuster](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/isobuster_06.PNG?raw=true)

* Dans le volet de gauche, cliquez avec le bouton droit de la souris sur l'icône des médias. Sous l'option , sélectionnez "RAW (.bin, .iso)".
![IsoBuster](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/isobuster_02.png?raw=true)

* Une nouvelle fenêtre s'ouvre, vous demandant où vous souhaitez enregistrer votre fichier image. Sélectionnez le dossier de projet que vous avez créé précédemment. Donnez un titre à l'image disque en saisissant l'identifiant du disque sans espace et en remplaçant 
     les deux points par des traits de soulignement (par exemple : DR2008:0016:346 devient DR2008_0016_346).
* Dans le menu "Save as type", sélectionnez l'extension .iso.

![IsoBuster](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/isobuster_03.PNG?raw=true)

* Cliquez sur "Save". Une nouvelle fenêtre s'ouvre, montrant la progression de l'extraction de l'image disque.
* Une fois l'extraction terminée, IsoBuster créera un fichier checksum MD5.

Étape 3 : Vérifier le contenu de l'image disque
* Une fois que vous avez créé une image disque, ouvrez votre dossier de projet et assurez-vous que vous avez tous les bons composants. Vous devez avoir au moins trois fichiers : le fichier d'image disque (.iso), un fichier de cuesheet (.cue) et un fichier de checksum (.md5).
* Afin de vérifier l'intégrité du fichier image disque, retournez dans IsoBuster et sélectionnez Ouvrir un Fichier Image dans le menu de la barre d'outils "Fichier". Ensuite, double-cliquez sur le fichier cue (.cue) associé à votre fichier image (.iso).
* **REMARQUE** : Les fichiers cue-sheet (.cue) sont couramment utilisés et combinés avec les **fichiers d'image de disque optique** pour avoir une idée de la disposition des pistes des CD, DVD, BD. Les fichiers cue sont en fait des fichiers texte, pour lesquels les données réelles du CD sont toujours contenues dans un fichier différent (.bin, .iso,...) Donc si vous ouvrez un fichier .cue avec IsoBuster, il connaîtra la disposition des pistes de l'image mais obtiendra les données réelles d'un autre fichier. Le nom de ce fichier est également contenu dans le fichier .cue.
* Vérifiez que les dépôts et les fichiers sont tous là, pour garantir l'intégrité du fichier image. Si un X rouge apparaît à côté de certains fichiers, c'est que ces fichiers comportent des erreurs de lecture et qu'ils n'ont peut-être pas été imagés correctement.
* Faites un clic droit sur l'icône du support (CD), puis dans le menu déroulant, sélectionnez "Verify this image file with existing MD5 Checksum file". Le message "The checksum matches with the image file" confirme que l'image disque correspond aux données du support original.

#### Pour extraire les pistes d'un CD audio
Les CD audio ne contiennent aucune donnée et n'ont donc pas de système de fichiers. Il n'y a donc ni fichiers de données ni dossiers sur un CD audio, mais des pistes audio répertoriées dans une table des matières (TOC).
* Suivez les étapes 1 et 2
* Extrayez le contenu de chaque piste audio dans un fichier WAVE non compressé.
* Faites un clic droit sur l'icône du CD, puis sous « Extract CD <Content> », sélectionnez « Extract Audio to Wave File (\*.wav) ».
* Une fois l'extraction terminée, assurez-vous que les fichiers Wave se trouvent dans le dossier de travail actuel et renommez-le(s) en utilisant le numéro d'accès du média (par exemple, DR2008_0016_264.wav). Si vous avez plusieurs pistes, ajoutez le numéro de piste à la fin du titre (par exemple : DR2008_0016_264_01 ; DR2008_0016_264_02).
* Signalez tous les CD audio dans votre document de travail Excel.

#### Pour créer une image disque d'un DVD
1. Suivez les étapes 1 et 2.
2. Utiliser le paramètre d'ajustement de la taille de fichier IsoBuster évite de fractionner les gros fichiers images - comme le contenu d'un DVD - en plusieurs fichiers images plus petits. Si vous avez un DVD ou tout autre support contenant plus de 1024 Mo de données, vous pouvez utiliser IsoBuster au lieu de l'imageur FTK. Ce dernier fractionnera tout fichier image volumineux en fichiers image plus petits de 1024 Mo.
3. Dans le panneau de gauche, cliquez avec le bouton droit de la souris sur l'icône du média (DVD+R). Sous "Extract DVD+R", sélectionnez "User Data (.tao, .bin, .iso)". Les DVD n'ont qu'un seul type de blocs, qui ne contiennent que des données utilisateur (il n'existe pas de DVD RAW). Sous "Extract DVD+R", les options RAW et RAW2User ont été grisées. Sélectionnez "Données utilisateur (.tao, .bin, .iso)" pour lancer le processus d'imagerie du disque.
4. Entrez le chemin de votre dossier de projet actuel.
5. Utilisez l'identifiant du média comme nom de fichier de l'image, en remplaçant les deux points (" :") par des traits de soulignement ("_"). (par exemple : DR2008:0016:346 devient DR2008_0016_346)
6. Sélectionnez l'extension .iso dans le menu "Save as type".
7. Cliquez sur "Enregistrer". Une nouvelle fenêtre apparaîtra, indiquant l'état d'avancement de l'extraction de l'image disque.
8. Une fois l'extraction terminée avec succès, créera un fichier MD5 Checksum
9. Suivez l'étape 3 pour vérifier l'intégrité du fichier d'image disque.
10. Signalez tous les DVD dans votre document de travail Excel.

#### Supports endommagés par la création d'image disque
Les lignes directrices suivantes peuvent être utiles si vous rencontrez des difficultés de lecture et/ou de support d'imagerie de disque. Elles ne vous permettront pas nécessairement de régler le problème, mais elles peuvent certainement vous aider à documenter l'état actuel du matériel numérique que vous conservez. Veuillez consulter l'archiviste numérique avant d'acquérir des supports numériques endommagés.
1. Suivez les étapes 1 et 2. Si le disque sur lequel vous travaillez comporte de nombreux secteurs défectueux, il se peut que vous ne puissiez pas effectuer une analyse antivirus.
2. Dans le panneau de gauche, cliquez avec le bouton droit de la souris sur l'icône du média (CD/DVD+R) et sélectionnez "Effectuer un balayage de surface".
3. Une fois l'examen terminé, IsoBuster vous donne plus d'informations sur l'état de votre disque. Si tout est bon, le message "Aucune erreur physique rencontrée. Votre disque est toujours en bon état" apparaîtra. Sinon, IsoBuster génère un rapport vous indiquant la lisibilité du disque (en pourcentage).

![IsoBuster](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/isobuster_07.PNG?raw=true)

4. Vous pouvez lancer un rapport plus détaillé en cliquant avec le bouton droit de la souris sur l'icône du système de fichiers > Arbre des dossiers et informations sur les fichiers > Liste des fichiers présentant des erreurs de lecture (dans la fenêtre d'édition). Les fichiers comportant des erreurs de lecture sont identifiés par un X rouge dans le panneau de droite. Dans le rapport, notez "Fichiers avec erreurs de lecture dans [Numéro d'identification] :" et enregistrez la liste dans votre dossier de travail, en utilisant son numéro d'identification comme nom de fichier (par exemple : DR2008_0016_118_ErrorFileList).


![IsoBuster](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/isobuster_10.PNG?raw=true)


5. En fonction des résultats des deux analyses précédentes, vous pouvez soit procéder à l'extraction de l'image du disque, soit identifier que le disque ne peut pas être imagé dans le tableur de stabilisation du versement. Suivez les étapes 3 et 4 pour extraire l'image disque.
6. Identifiez les supports endommagés dans la feuille de calcul de stabilisation du versement, en incluant autant de détails que possible sur l'état réel des supports. Inscrivez les noms de fichiers des journaux d'erreurs dans la colonne "Note" de le document Excel de stabilisation des versements pour référence ultérieure.

<a name="fc5025"></a>
### Création d'une image disque avec FC5025
Le FC5025 est un contrôleur de disquettes 5,25" qui se branche sur le port USB de n'importe quel ordinateur et permet de lire des disquettes 5,25". Il est accompagné d’un programme d'image disque et d'outils de navigation permettant de créer et d'accéder à des copies de matériel numérique. Il y a deux façons d'utiliser le logiciel FC5025 pour l'imagerie disque : à partir de l'interface graphique ou de la ligne de commande. Chacune de ces options possèdent ses avantages et ses inconvénients : l'interface graphique offre une interface instinctive et facile à utiliser, tandis que la ligne de commande vous permettra de capturer le processus d'imagerie du disque en envoyant la sortie standard et les erreurs standards dans un fichier.

Avant de commencer le traitement, vous devez d'abord insérer la disquette dans le lecteur FC5025, situé dans la station de travail d'imagerie de disque (DSK-065-14), avec la face avant vers le haut - généralement celle sur laquelle se trouvent les étiquettes - dirigée vers vous. L'encoche de protection en écriture devrait se trouver sur la gauche de la disquette lorsque vous la placez avec l'étiquette plus proche de vous. Une autre façon de s'assurer que la disquette est correctement insérée, consiste à examiner les faces de la disquette et à identifier le verso : vous devriez pouvoir discerner les parties pliées au verso de la pochette en plastique. Une fois la disquette insérée, tournez le bouton dans le sens des aiguilles d'une montre pour verrouiller la disquette dans le lecteur. Le témoin lumineux devrait alors s'allumer en vert lorsque la disquette est lue dans le lecteur. Lorsque le voyant s'éteint, vous pouvez retirer la disquette du lecteur en toute sécurité en la déverrouillant d'abord.

#### Images du disque avec l’interface graphique
1. Une fois le disque correctement inséré, démarrez le logiciel FC5025. Une fenêtre s'affiche avec quatre paramètres à configurer : Lecteur source, Type de disque, Répertoire de l'image de sortie et Nom du fichier de l'image de sortie.
2. **Lecteur source**: Doit toujours indiquer le dispositif FC5025. Aucune autre option ne devrait être disponible à cette étape.
3. **Type de disque** : Sélectionnez le format du disque que vous êtes en train de lire sur l'appareil. Si le type de disque n'est pas précis, le disque ne sera tout simplement pas lu correctement ou ne sera pas lu du tout. Pour définir le type de disque, vous pouvez sélectionner une option dans le menu déroulant et la tester en premier lieu. Examinez d'abord l'étiquette afin de trouver toute information indiquant le type de disque. Par exemple, si vous avez une disquette de 360KB 5,25" créée dans un environnement DOS, sélectionnez "MS-DOS 360k".
4. Après avoir sélectionné le type de disquette, cliquez sur "Parcourir le contenu de la disquette". Une nouvelle fenêtre s'affiche. Si le type de disque correspond, le disque est lu correctement et la liste des fichiers apparaît dans la fenêtre de dialogue.

![FC5025](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/fc5025_03.JPG?raw=true)

5. Si le type de disque ne correspond pas, un message l'indique : "Unable to get file listing!". Notez que cette fonction n'est pas disponible pour tous les types de disques. 

![FC5025](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/fc5025_02.JPG?raw=true)

6. **Répertoire des images de sortie** : Copiez le lien d'accès au répertoire qui contiendra le fichier image du disque.
7. **Nom de fichier de l'image de sortie** : sélectionnez un emplacement et un nom qui décrivent le mieux le contenu que vous visualisez sur le disque, comme l'identifiant du média.

![FC5025](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/fc5025_01.JPG?raw=true)

8. **Capture de disque** : Cliquez sur le bouton "Capturer le fichier image du disque" pour commencer à utiliser le lecteur. Chaque erreur de lecture est indiquée dans la fenêtre d'affichage de la progression. S'il y a plusieurs erreurs, elles sont généralement affichées rapidement l'une après l'autre, chaque erreur successive effaçant celle qui la précède. Il s’agit de l'un des principaux inconvénients de l'utilisation de l'interface graphique pour l'imagerie de disque. Nous pouvons garder une trace des multiples erreurs de lecture et garder une trace du processus d'imagerie du disque en utilisant la ligne de commande. Les directives suivantes nous montreront comment faire.

![FC5025](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/fc5025_04.JPG?raw=true)

#### Création d'une image disque avec la ligne de commande
1. Sur le poste de travail d'imagerie de disque (DSK-065-14), ouvrez l'invite de commande à partir du menu Démarrer.
2. **Erreurs d'enregistrement** : Si vous devez enregistrer la sortie standard et les erreurs standard de votre traitement, vous pouvez utiliser la commande fcimage pour les diriger toutes les deux vers un rapport d’erreurs. Commencez par placer l'invite de commande sur le chemin d'accès de votre dossier de projet. Assurez-vous que vous êtes sur le bon serveur :
```cd Users\username\Desktop\ARCH222229```
3. Si les outils logiciels ont été correctement installés, vous pouvez appeler la commande directement depuis la ligne de commande. La syntaxe complète pour fcimage to disk image the media while exporting the log in a text file est la suivante :
4. ```fcimage -f format outputfile 1> logfile 2>&1```
5. À la suite de notre exemple, le commandement est :
6. ```fcimage -f msdos360 ARCH222229.img 1> ARCH222229.log 2>&1```


7. Une fois la commande terminée, ouvrez votre dossier de projet et assurez-vous que tout y est. Vous devez disposer d'un fichier .img (votre fichier image disque) et d'un fichier .log (les erreurs enregistrées).

<a name ="kryoflux"></a>
### Création d'une image disque avec Kryoflux
Note : Les éléments des lignes directrices ci-dessous ont été recueillis dans le [Guide de l'archiviste pour KryoFlux](https://docs.google.com/document/d/1LViSnYpvr2jf1TrCh6ELuL-FWo14ICw-WZeb8j5GGpU/edit#), une ressource complète pour les praticiens travaillant avec des documents nés numériques dans un contexte archivistique.
Le [Kryoflux](https://www.kryoflux.com/) est une carte contrôleur de disquettes développée par [Software Preservation Society](http://www.softpres.org/) pour l'imagerie d'une grande variété de disquettes anciennes. Sa particularité réside dans sa capacité à capturer des données de piste brutes en échantillonnant la fluctuation des cellules de bits sur le plateau, permettant la capture de tout type de disquette 5,25" ou 3,5", malgré son format.
#### Capture d'images de disque à l'aide de l'interface utilisateur graphique (GUI)
1. Au poste de travail BitCurator03, lancez l'interface graphique KryoFlux en double-cliquant sur le fichier appelé kryoflux-ui.jar situé sur le Bureau.
2. Au début de chaque session d'imagerie, calibrer le lecteur de disquettes en sélectionnant le bon lecteur dans le menu Lecteur puis en sélectionnant Calibrate dans le même menu. Le lecteur 5,25" correspond au lecteur 0 et le lecteur 3,5" au lecteur 1. Vous ne devriez avoir à calibrer le lecteur qu'une seule fois par session d'imagerie et chaque fois que vous passez d'un lecteur à l'autre.
![Kryoflux](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/kryoflux_step2_calibrate.png)
3. Configurez l'interface graphique de KryoFlux pour sélectionner le répertoire de sortie de vos images disques et fichiers journaux nouvellement créés. Pour ce faire, sélectionnez *File → Settings* et cliquez sur l'onglet *Output*. Naviguez jusqu'au chemin d'accès approprié au stockage. Assurez-vous que le bouton Logs est coché, puis cliquez sur *OK*.
4. Pour chaque disque, entrez un identifiant unique. Cliquez sur *Enter name…* et saisissez un identifiant unique associé au disque. Le texte saisi ici deviendra le nom de fichier pour toutes les images de disque et tous les fichiers journaux créés. Ne pas inclure l'extension du nom de fichier.
5. Sélectionnez le(s) format(s) d'image pour l'image disque en utilisant la liste déroulante sous le champ du nom de fichier.
![Kryoflux](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/kryoflux_step5_selectformat_02.png)
6. Utilisez les tableaux ci-dessous pour sélectionner le(s) bon(s) format(s) d'image. Afin de choisir plusieurs sorties, maintenez la touche Ctrl enfoncée tout en effectuant vos sélections. Dans la plupart des cas, la sélection d'un format d'image pour obtenir une image de secteur nécessite que vous connaissiez un peu le média en question (format physique, format système, densité, etc.)
**Types de médias et formats d'images courants**
|Format physique|        Format du système        | Encodage        | Capacité | Profil/Format de l'image |
| ------------- |:-------------:| -------- | -------- | -------------------- |
| 3.5” double densité |        Macintosh |        GCR        | 400 KB; 800 KB | Apple DOS 400K/800K sector image
| 3.5” double densité |        PC        | MFM        | 720 KB | MFM sector image |
| 3.5” haute densité |        Tout        | MFM        | 1440 KB | MFM sector image |
| 5.25” double densité        | PC        | MFM        | 320 KB; 360 KB | MFM sector image [40 tracks] |
| 5.25” haute densité        | PC        | MFM        | 1200 KB | MFM sector image [1.2MB] |


**Spécifications pour les profils d'images couramment utilisés**
| Nom du profil |        Piste de départ        | Piste finale        | Mode secondaire | Taille du secteur | Comptage des secteurs | Distance de la piste | Objectif RPM |
| ------------ | ----------- | --------- | --------- | ----------- | ------------ | -------------- | ---------- |
| MFM sector image [1.2MB] |        Au moins 0 |        Au maximum 83        | Les deux côtés  | 512 Bytes | Exactement 15 | 80 Pistes | 360 |
| MFM sector image |        Au moins 0 |        Au maximum 83        | Les deux côtés | 512 Bytes | tous | 80 Pistes | Par type d'image |
| MFM sector image [40 tracks] | Au moins 0 | Au maximum 83 | Les deux côtés | 512 Bytes | tous | 40 Pistes | Par type d'image |
| Apple DOS 400K/800K sector image | Au moins 0 | Au maximum 83 | Les deux côtés | 512 Bytes | tous | 80 Pistes | Par type d'image |






Une fois que vous avez tout configuré, insérez le disque dans le lecteur approprié et cliquez sur Démarrer. Dans la section Pistes de la fenêtre, vous devriez voir les cellules se remplir progressivement de différentes couleurs. Voici la signification de chaque couleur :


Couleur
	Signification
	Verte
	Bon : La piste a été imagée avec succès !
	Orange
	Bon + modifié : La piste a été imagée avec succès mais comporte un ou plusieurs secteurs qui ont été modifiés après formatage ou mastering.
	Rouge
	Mauvais : La piste n'a pas été imagée avec succès
	Gris
	Inconnu : le logiciel Kryoflux n'a pas pu déterminer le statut de cette piste. Cela peut signifier ou non qu'elle a été lue avec succès. Cela pourrait indiquer que cette piste n'était pas formatée ou que le mauvais format a été sélectionné avant la capture. Si vous ne créez que des fichiers de flux de préservation, tous les secteurs seront gris.
	

9. Lorsque vous entendez la tête de lecture revenir à son point de départ (0), le disque cesse de tourner et le voyant lumineux du lecteur s'éteint, ce qui signifie que la capture est terminée. Un fichier sera automatiquement généré dans le répertoire que vous avez sélectionné à l'étape 3.
10. Pour imager un autre disque, revenez à l'étape 4 et continuez à partir de là. Si vous changez de disque et que vous n'avez pas calibré l'autre disque, continuez à partir de l'étape 3.

![Kryoflux](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/kryoflux_step7_cells.png)

11. (Under image) *Les cellules colorées montrent que le profil d'image choisi n'était pas approprié pour le disque. Chaque fois que vous voyez un modèle de résultat alternant entre Inconnu et Bon (+ Modifié), vous avez probablement un disque de 40 pistes. Réessayez l'imagerie avec le profil de l'image du secteur MFM [40 pistes] et comparez les résultats.*
####Capture de disquettes présentant des dommages physiques ou des difficultés de lecture
REMARQUE IMPORTANTE : chaque fois que vous remarquez la présence de moisissures ou de champignons sur un support numérique, consultez la Conservation et l'Archiviste numérique avant de capturer l'image disque. La moisissure pourrait se répandre à l'intérieur du lecteur et sur la tête de lecture risquant de contaminer d'autres disques par la suite. Pour réduire le risque de contamination, vous pourriez utiliser un lecteur exclusivement dédié à l'imagerie de supports contaminés. Pour les disques tenaces, qui semblent avoir de multiples mauvais secteurs et des dommages physiques, voici la procédure
1. Dans la liste déroulante des formats de sortie, sélectionnez **le format que vous pensez être celui du disque et les fichiers de flux Kryoflux, formats de préservation**. Vous pourrez ainsi vérifier si le disque a été lu correctement, et effectuer des tentatives en cas d'erreurs. En outre, les fichiers de flux bruts serviront de fichiers de préservation si le format de codage sélectionné ne correspond pas au format du disque. Ils peuvent également être utilisés pour produire de nouveaux fichiers d'image disque en mode [sans périphérique](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/diskimaging.md#deviceless).
2. **AVERTISSEMENT : faire tourner la tête du lecteur plusieurs fois sur le même secteur d'un disque peut créer des dommages physiques permanents sur le support. N'utilisez cette option que si la préservation des données prévaut sur la préservation physique du support**. Vous pouvez régler le nombre de tentatives sur une valeur plus élevée si le disque est particulièrement difficile à lire. Chaque fois que la tête essaie de lire un secteur, elle le "polit" en coupant les substances intrusives, telles que la poussière, les champignons et les moisissures. Nous avons fixé le nombre de tentatives à 20 - ce qui est déjà plus important que le nombre par défaut de 5 tentatives - mais vous pourriez aller jusqu'à 100. Pour définir le nombre de tentatives, allez dans Fichier > Paramètres > Sortie et saisissez le nombre de tentatives que vous souhaitez exécuter dans le champ "Retries".
3. Suivez les étapes 6 à 8 de la section précédente.
4. Faites attention : Écoutez le son du disque dur et remarquez toute anomalie. Examinez l'état de l'interface graphique de Kryoflux et notez tout secteur défectueux ou format inconnu dans votre feuille de calcul de traitement.
*Les instructions de cette section ont été inspirées par l'article du Dr Gough dans la Tech Zone sur le [traitement des disques et des lecteurs difficiles](http://goughlui.com/2013/05/19/project-kryoflux-part-6-dealing-with-difficult-disks-and-drives/). Veuillez vous référer à l'article complet pour plus de détails sur l'entretien du matériel et la récupération des données à l'aide du Kryoflux.*
####Utilisation de l'interface graphique en mode sans dispositif**
Une fois capturés, les fichiers de flux Kryoflux peuvent être utilisés directement à partir de l'interface graphique pour produire des fichiers d'images encodés et pour éviter de faire fonctionner un quelconque matériel externe. Cette technique peut être utile pour traiter des disques fragiles qui ne doivent pas être lus plusieurs fois afin d'éviter des dommages physiques permanents. Elle peut également être utilisée pour traiter des fichiers de préservation à un moment ultérieur de votre workflow. D'un autre côté, les fichiers de flux Kryoflux sont propriétaires et sont beaucoup plus volumineux que les fichiers d'image disque : leur préservation à long terme n'est donc pas encouragée au CCA.


Voici les étapes à suivre pour produire de nouveaux fichiers d'images encodés à partir des fichiers de flux Kryoflux :
1. Allez sur le *Drive* et sélectionnez "Stream Files”
2. Sélectionnez la destination de sortie.
3. Pour chaque disque, entrez un identifiant unique. Cliquez sur Enter name... et saisissez un identifiant unique associé au disque. Le texte saisi ici deviendra le nom de fichier pour toutes les images de disque et les fichiers journaux créés. Ne pas inclure l'extension du nom de fichier.
4. Sélectionnez le(s) format(s) de l'image disque à l'aide de la liste déroulante située sous le champ du nom de fichier.
5. Cliquez sur Start et sélectionnez le dossier contenant les fichiers de flux que vous souhaitez traiter. Cliquez sur Ouvrir et la création du fichier d'image disque commencera immédiatement. Les résultats s'afficheront dans les cellules de l'interface graphique, comme d'habitude.

<a name="nimbie"></a>
### Création d'une image disque avec le Nimbie et ImgBurn
Le Nimbie est un dispositif d'autochargement utilisé pour lire, écrire et créer simultanément, des images disques pour de nombreux CD ou DVD, tout en requérant un minimum d'intervention de l'utilisateur. Veuillez lire le [manuel d'utilisation du Nimbie](http://www.acronova.com/file/2/download.html) pour savoir comment configurer l'unité Nimbie. Le logiciel qui peut être utilisé en conjonction avec le Nimbie est ImgBurn. Pour créer des images disque en utilisant le Nimbie et ImgBurn, vous aurez besoin de ce qui suit :
* Windows XP/Vista/ 7 ou Apple OS X 10.6 / 10.7 (pour QQGetTray uniquement)
* 1 Go de RAM ou plus
* Port USB 3.0 (rétrocompatible avec USB 2.0)
* ImgBurn version 2.5.8.0 (y compris le pack de [mise à jour BSRobots](http://www.acronova.com/files/BSRobots_2.2.0.333.zip)) ou ultérieure
* Unité Nimbie USB Plus avec les [pilotes appropriés installés](http://www.acronova.com/file/51/download.html)


**Comment mettre en place le Nimbie pour la création d'image disque**
1. Assurez-vous que l'appareil Nimbie est branché dans une prise murale et que le cordon USB est connecté à l'ordinateur.
2. Fixez le bac à disques traités devant l'unité. Lorsque le Nimbie a fini de traiter un disque, il l'éjecte par la fente avant, dans le bac à disques. Si le Nimbie ne peut pas traiter un disque (à cause de la saleté ou d'un disque rayé, entre autres possibilités), le disque sera éjecté par le bas de l'appareil. Assurez-vous qu'il n'y a rien sous l'appareil pour laisser suffisamment de place aux disques rejetés.
3. Ouvrez le couvercle de l'appareil. Il y a 4 lumières LED à l'avant de l'appareil qui vous indiquent son état. Un guide pictural à l'intérieur du couvercle vous indique la signification des configurations lumineuses.
4. Insérez les disques dans la machine, la face de l'étiquette tournée vers le haut. Le Nimbie peut traiter 20 disques à la fois, à moins que vous n'attachiez les 3 tiges d'extension fournies, auquel cas le Nimbie peut traiter jusqu'à 100 disques. Les tiges se vissent à trois endroits dans la lèvre sous le couvercle, et sont destinées à maintenir le couvercle ouvert et à empêcher la pile de disques de s'effondrer. Si vous souhaitez traiter plusieurs disques à la fois, il est nécessaire de soutenir le Nimbie sur une hauteur d'au moins 96 mm pour tenir compte des disques une fois que le Nimbie a fini de les traiter. Une fois que les disques sont dans le Nimbie, l'unité est alors configurée pour l'imagerie des disques.
Attention : Bien que le manuel mentionne que le Nimbie peut traiter jusqu'à 100 disques par lot, il ne mentionne pas que l'utilisateur doit également s'assurer que son installation puisse traiter en toute sécurité le volume élevé de disques éjectés de l'unité Nimbie au cours du processus. Si ce n'est pas le cas, les disques éjectés et traités peuvent s'empiler et tomber, ce qui risque de les endommager.
**Comment configurer ImgBurn pour qu'il fonctionne avec Nimbie USB Plus**
1. Connectez le Nimbie USB au PC et allumez-le.
2. Assurez-vous que les pilotes de l'autochargeur sont correctement installés.
3. Téléchargez et installez [ImgBurn](http://www.imgburn.com/index.php?act=download).
4. Téléchargez le BSRobots Upgrade Pack et extrayez les fichiers à l'endroit où vous avez installé ImgBurn (c'est-à-dire C:\Program Files\ImgBurn).
5. Lancez ImgBurn, allez dans Outils > Paramètres
![nimbie](http://www.acronova.com/images/howto/howto_imgburn_setup_screenshot1.png)
6.  Allez à I/O. Sous "Enumerate Devices", vérifiez "Auto Loaders" et "Acronova - BSRobots20.dll".
![nimbie](http://www.acronova.com/images/howto/howto_imgburn_setup_screenshot2.png)
7. Cliquez sur OK pour fermer la fenêtre des paramètres, et fermez ImgBurn pour terminer l'installation.
(Ces instructions ont été prises [ici](http://www.acronova.com/howto/article/23/review.html#ancher-imgburn))
**Pour créer des images de disque à partir de CD et de DVD**
1. Assurez-vous que le Nimbie est connecté et allumé
2. Démarrez ImgBurn et attendez que l'autochargeur ait terminé son initiation robotique.
3. Sélectionnez la fonction Créer un fichier image à partir du disque
![nimbie](http://www.acronova.com/images/howto/imgburn-create-image-1.jpg)
4. Cochez **Batch mode**
![nimbie](http://www.acronova.com/images/howto/imgburn-create-image-2.jpg)
5. Cliquez sur l'icône pour commencer le chargement du disque
![nimbie](http://www.acronova.com/images/howto/imgburn-create-image-3.jpg)
6. Une fois le premier disque chargé, ImgBurn demande à l'utilisateur de définir le dossier de destination pour le stockage des ISO. (L'invite n'apparaîtra que pour le premier disque).
7. Tous les disques seront traités un par un jusqu'à ce que le chargeur soit vide.


Vous trouverez un récapitulatif complet des paramètres d'ImgBurn [ici](https://forum.imgburn.com/index.php?/topic/6232-the-imgburn-settings/)


(Ces instructions ont été prises [ici](http://www.acronova.com/howto/article/23/review.html#ancher-imgburn))
**Si vous souhaitez que ImgBurn crée des fichiers de somme de contrôle pour chaque image disque réalisée**

1.	Aller à Tools>settings 
2.	Dans les outils, allez à l'onglet "Read".
3.	Sélectionnez "Create MD5 File".

**Si vous voulez voir le rapport de ce que vous avez fait**
ImgBurn génère automatiquement un rapport qui répertorie toutes les actions récemment effectuées. Pour consulter ce fichier, vous pouvez aller à Affichage et cliquer sur Journal . Le rapport apparaîtra alors dans une fenêtre séparée. Pour enregistrer ce fichier, allez à Fichier et cliquez sur Enregistrer sous.

<a name="cdparanoia"></a>
### Extraction d’un CD audio avec cdparanoia (Bitcurator)  
cdparanoia est un utilitaire de lecture de CD audio en ligne de commande qui récupère les pistes audio d'un disque compact audio numérique (CD-DA). Au CCA, nous utilisons le logiciel cdparanoia lorsqu’on ne peut pas utiliser IsoBuster pour l'extraction des pistes audios. Cliquez [ici](#pour-extraire-les-pistes-dun-cd-audio) pour découvrir comment extraire un CD audio avec IsoBuster et cliquez [ici](#depannage) pour plus d'informations sur le problème rencontré qui est à l'origine de ce nouveau flux de travail.

Avant de commencer l'extraction, créez un dossier dans le répertoire `/mnt/1TB_RAID` pour y enregistrer votre travail. Nommez ce dossier avec un nom facile à retenir et significatif, comme un numéro d'acquisition ou un autre identifiant unique.

Pour extraire un CD audio avec cdparanoia, suivez les étapes ci-dessous.

1. Insérez le CD dans son lecteur sur l’un des BitCurators.
2. Analysez le CD à l'aide d’un logiciel antivirus comme ClamAV. S'il n'y a pas de virus, passez à l'étape suivante. 
3. Effectuez une analyse du disque optique :
	* Ouvrez le terminal, saisissez la commande « lsblk » et appuyez sur Entrée. La commande lsblk (list block devices) affichera tous les périphériques de bloc disponibles. Vous y trouverez le nom attribué par Linux à votre lecteur optique. Ce nom doit ressembler à « sr# », par exemple sr0 ou sr1. Si le nom de votre montage est sr0, le chemin d'accès à votre lecteur sera « /dev/sr0 ».
	* Saisissez « sudo disktype » + (chemin d’accès de votre lecteur) + « > filename-disktype.txt » comme ceci : 
« sudo disktype /dev/sr# > filename-disktype.txt » et appuyez sur Entrée.
	* Saisissez « sudo cd-info » + (chemin d’accès de votre lecteur) + « > filename-cdinfo.txt » comme ceci :
« sudo cd-info /dev/sr# > filename-cdinfo.txt » et appuyez sur Entrée.
Ces deux commandes créeront deux documents texte dans votre dossier Home que vous pouvez utiliser pour analyser votre CD.
	* S’il est inscrit que le mode de votre disque est **« CD-DA »**, suivez les directives ci-dessous.
4. Extrayez les pistes audio :
	* Ouvrez le terminal si ce n’est pas déjà fait.
	* Saisissez « cdparanoia -B -L » et appuyez sur Entrée. Chaque piste du CD sera extraite et sauvegardée dans un fichier WAVE distinct. L’option -B (par lots) divisera la sortie en plusieurs fichiers au niveau des pistes, et l’option -L (Log-debug) générera un fichier journal détaillé.
	* Une fois terminé, éjectez le CD. Vous trouverez le(s) fichier(s) WAVE dans le dossier Home, avec son fichier journal correspondant.
	* Vérifiez la qualité des pistes audio pour vous assurer que tout fonctionne correctement. Vous pouvez transférer temporairement les fichiers du BitCurator vers un ordinateur Windows si vous rencontrez des difficultés pour écouter l’enregistrement audio.
5. Finalisation :
	* Déplacez tous les fichiers associés du dossier Home vers votre dossier de travail situé sur le RAID.
	* Renommez les pistes avec leur identifiant unique, comme expliqué [ici](#pour-extraire-les-pistes-dun-cd-audio)

*(_Ces instructions ont été tirées du Disk Imaging Guide du musée Tate disponible_ <a href="https://www.tate.org.uk/documents/3/sbapp_disk_imaging_guide_01_00.pdf" target="blank">ici</a> et du blog BitsGalore disponible <a href="https://bitsgalore.org/2015/11/13/preserving-optical-media-from-the-command-line.html" target="blank">ici</a>)*

<a name="depannage"></a>
### Dépannage
* **Problème** : Un problème rencontré en utilisant le Nimbie pour la création d'images diques est que certaines copies provenant de CD ne générait pas les fichiers .iso, mais créait des fichier .bin. Apparemment, cela est dû au type de mode de secteur que le CD utilise pour stocker les données. Les CD utilisant le mode 1 donnent des fichiers d'image .iso, tandis que les CD utilisant le mode 2/type 1 donnent des fichiers .bin. Plus d'informations peuvent être trouvées [ici](http://www.multimediadirector.com/help/technology/cd-rom/cdrom_spec.htm).
   * **Solution** : La meilleure solution qu'on a pu trouver a été de changer simplement l'extension de fichier de "nomdefichier.bin" à "nomdefichier.iso". Cela ne semble pas avoir d'effet sur le fichier image, car nous avons toujours été capable d'extraire des fichiers du fichier image sans problème. Cette solution a été trouvée [ici](http://forum.imgburn.com/index.php?/topic/19845-image-from-disk-results-in-bin-file-instead-of-iso-file/).

* **Problème** :  L'autochargeur Nimbie n'apparaît pas comme un lecteur utilisable dans ImgBurn
   * **Solution** : Il y a quelques causes possibles à cela, car cela s'est produit plusieurs fois en laboratoire. Voici les solutions que nous avons utilisées :
      * Changer le câble qui relie le Nimbie à l'ordinateur. Le câble nécessaire est de type B en USB 2.0 ou A en USB 2.0 ou 3.0
      * Réinstaller les pilotes de périphériques (nécessite des privilèges d'administrateur)
      * Vérifiez que le pilote est installé au bon endroit, c'est-à-dire à l'endroit où ImgBurn est installé (c'est-à-dire C:\Program Files\ImgBurn)
    
* **Problème :**
l'icone du CD n'apparait pas sur le BitCurator.
	* **Solution :** Essayez d'éjecter le disque et le réinsérer. Parfois il peut y avoir un bug lorsque le logiciel antivirus ClamTK est ouvert et qu'un CD a été inséré.

* **Problème :**
Après l'utilisation de Disk Image Processor ou Folder Processor (Outils développés par le CCA), le nom du fichier logigique est modifié (caractères ou syntaxe différents de ceux des autres documents, abréviations, etc.)
	* **Solution :** Essayez de monter l'image disque et comparez les noms des dossiers. S'il y a une différence, copiez le nom du dossier de l'image disque montée dans votre SIP.

* **Problème :**
L'ordinateur Windows éjecte automatiquement le CD audio. Cependant, lorsqu’on l’insert dans un ordinateur BitCurator, l’îcone du CD apparait et on y retrouve des fichiers audio verrouillés.
	* **Solution :**
Dans ce cas, vous pouvez utiliser [cdparanoia](https://xiph.org/paranoia/index.html) pour extraire les pistes audio verrouillées sur l'un des postes de travail BitCurator. Pour plus d’information sur notre flux de travail, veuillez-vous référer à [cette section](#extraction-dun-cd-audio-avec-cdparanoia-bitcurator). 

