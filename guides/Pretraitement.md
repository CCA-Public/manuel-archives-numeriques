## Prétraitement : Triage et évaluation des archives nées numériques

Lorsqu'une acquisition doit être traitée, l'archiviste numérique télécharge les AIP "bruts" contenant toutes les données numériques et commence le processus de triage et d’inventaire. Le résultat de ce processus sera des fichiers de travail que le responsable du traitement pourra classer et décrire, ainsi que des rapports détaillés pour aider à la prise de décision concernant le classement, la description et la préservation des archives. Ce guide décrit les étapes de cette étape de prétraitement et comprend:

* [Analyse des images de disque avec le Disk Image Processor](#analyse)
* [Extraction de fichiers à partir de paquets et d'images disque](#paquets)
  - [Extraction de fichiers à partir d'images de disque avec Bitcurator](#extraction_bitcurator)
    + [Outil de reporting BitCurator - Accès aux fichiers](#reporting)
    + [Script de montage de l'image disque](#script)
  - [Extraction de fichiers à partir d'images de disque avec FTK Imager](#ftk)
  - [Extraction de fichiers à partir d'images de disques HFS (Hierarchical File System)](#hfs)
* [Extraction des archives et rapport sur les fichiers logiques](#fichiers_logiques)
* [Déplacement des dossiers vers le lieu de traitement](#deplacement)
* [Soumission des fichiers à PRONOM](#pronom)


<a name="analyse"></a>
### Analyse des images de disque avec le Disk Image Processor
*Note : Cette section est exacte à partir de Disk Image Processor v1.0.0.*


[Disk Image Processor](https://github.com/CCA-Public/diskimageprocessor) est un outil graphique développé pour BitCurator qui se trouve au-dessus de deux scripts Python 3 : diskimageanalyzer.py et diskimageprocessor.py.


Chacun des deux scripts/modes prend un répertoire d'images disque et de fichiers connexes en entrée et crée des sorties standardisées cohérentes ainsi qu'une description CSV.


En mode analyse, l'outil peut être utilisé pour obtenir une compréhension à haut niveau du contenu d'une collection d'images disque. L'outil fait une boucle sur tous les fichiers d'un répertoire, détermine lesquels sont des images de disque, puis pour ceux-ci :
________________
* Convertit l'image en image brute, si elle est présentée comme une image disque (E01)
* Créer un répertoire "reports" pour les images disques de la collection :
   * Un fichier DFXML
   * Sortie de texte de l'utilitaire disktype
   * Rapports Brunnhilde (y compris les journaux et les rapports de clamAV et bulk_extractor)
* En option, crée un répertoire "files" contenant les copies de référence des fichiers exportés de l'image disque.
L'outil crée en outre un fichier "analyse.csv" qui contient les informations suivantes pour chaque disque qu'il a pu lire :
* Nom de l'image du disque
* Système de fichiers
* Type de date
* Date du rapport
* Date la plus proche
* Date limite
* Étendue
* Virus trouvé (Vrai/Faux)
* Liste triée des formats de fichiers

![diskimageprocessoranalysis](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/dip-analysis.png)


L'utilisation du mode Analyse peut vous aider à comprendre des aspects cruciaux d'une collection d'images disques, et à commencer à formuler une stratégie pour leur classement, leur description, et tout travail de normalisation de format ou autre travail de préservation qui pourrait être nécessaire.

<a name="paquets"></a>"
### Extraction de fichiers à partir de paquets et d'images disque
Une autre possibilité consiste à utiliser l'un des nombreux outils permettant soit de découper des fichiers à partir d'images disque, soit de monter l'image disque et de copier les fichiers à partir du disque monté. Dans les deux cas, cela vous permettra de copier les fichiers sur le lecteur du catalogueur et de les visualiser ensuite à partir de n'importe quel ordinateur connecté au réseau du CCA.

Pour l'extraction de fichiers à partir d'images disques en dehors du processus de rapport, nous utilisons généralement l'un des deux outils d'extraction de fichiers à partir d'images de disques : [Bitcurator](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/triage.md#bitcuratorfiles)ou [FTK Imager](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/triage.md#ftkimagerfiles).

<a name="extraction_bitcurator"></a>
### Extraction de fichiers à partir d'images de disque avec Bitcurator
Bitcurator dispose de deux outils natifs pour extraire des fichiers d'images disque : [l'interface d'accès aux images disque Bitcurator](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/triage.md#bcaccess) et le script de [montage d'images disque](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/triage.md#mountscript).

<a name="reporting"></a>
#### Outil de reporting BitCurator - Accès aux fichiers
Voir les instructions pour [l'exportation de fichiers à partir d'images disque](https://wiki.bitcurator.net/index.php?title=File_Access) sur le wiki BitCurator
Notez que cette méthode peut ne pas conserver les horodatages originaux des dossiers. Si les dates originales du système de fichiers doivent être conservées, vous pouvez tenter d'extraire les fichiers de l'image disque par la méthode suivante : [Script de montage de l'image disque](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/triage.md#mountscript) de Bitcurator.

<a name="script"></a>
#### Script de montage de l'image disque
En plus de l'onglet Accès aux fichiers de l'outil de reporting BitCurator, BitCurator offre une autre option : le montage d'images de disque en tant que lecteurs via un script de système de fichiers Mount Disk Image inclus et la copie manuelle sur les fichiers.


Étapes :


* Cliquez avec le bouton droit de la souris sur l'image disque. Dans le menu Scripts, choisissez "Monter l'image disque".


![mountscript1](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/mountscript1.png)  


* Si le script a réussi à monter l'image disque, vous verrez un nouveau lecteur disponible sur le bureau et dans le dock sur le côté gauche de l'écran.

![mountscript2](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/mountscript2.png)  

* Cliquez sur l'icône du lecteur sur le dock (ou sur le bureau). Cela vous permettra d'accéder aux fichiers sur le disque par l'intermédiaire de l'interface graphique. De là, copiez et collez le répertoire racine ou tout fichier dans un nouveau dossier de votre dossier de projet sur le bureau (nommé d'après l'identifiant du disque).

![mountscript3](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/mountscript3.png)

* Note : Comme vous pouvez le voir dans la fenêtre du terminal, sur la capture d'écran ci-dessous, le script de montage de l'image disque fonctionne en montant le disque dans le répertoire /media. L'image restera montée comme un lecteur dans ce répertoire jusqu'à ce que vous démontiez l'image disque. Veillez à démonter l'image disque après avoir terminé la copie de tous les fichiers. Pour démonter l'image disque, cliquez avec le bouton droit de la souris sur le fichier d'image disque. Dans le menu Scripts, choisissez "Démonter l'image disque". Si vous n'êtes pas sûr que l'image ait été démontée, vous pouvez ouvrir un terminal et entrer la commande suivante : ```ls /media```

* Si vous voyez l'identifiant du disque dans les résultats, c'est que l'image du disque n'a pas encore été démontée.

![mountscript4](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/mountscript4.png)  

<a name="ftk"></a>
### Extraction de fichiers à partir d'images de disque avec FTK Imager

* Dans le menu Fichier, sélectionnez "Add Evidence...".

![ftkextract1](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/ftkextract1.jpg)  

* Dans le menu "Select Source", sélectionnez "Image File" et appuyez sur "Next".

![ftkextract2](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/ftkextract2.jpg)  

* Dans le menu de sélection des sources, cliquez sur "Browse", trouvez le fichier image disque dont vous souhaitez extraire des fichiers, puis appuyez sur "Open" et "Finish".

![ftkextract3](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/ftkextract3.jpg)

* Vous devriez maintenant voir les médias énumérés dans la fenêtre de l'arborescence. Dans cette arborescence (et non dans la liste des fichiers, comme illustré ci-dessous), cliquez avec le bouton droit de la souris sur le dossier racine que vous souhaitez extraire et choisissez "Export Files...".

![ftkextract4](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/ftkextract4.jpg)  

* Sélectionnez une destination pour les fichiers que vous extrayez.

![ftkextract5](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/ftkextract5.jpg)  

* Si le processus est réussi, vous devriez voir apparaître une fenêtre "Résultats de l'exportation" avec des détails sur le nombre de dossiers, de fichiers et d'octets copiés. Si le processus a réussi, appuyez sur "OK" et vérifiez visuellement dans l'explorateur de fichiers que les fichiers ont été enregistrés à l'endroit prévu. Si tout semble correct, notez que les fichiers ont été extraits dans le tableur de stabilisation du versement, et passez à l'image disque suivante. S'il y a eu des erreurs, notez-les dans le tableur de stabilisation du versement et consultez l'archiviste numérique.

![ftkextract6](https://github.com/CCA-Public/digital-archives-manual/blob/master/media/photos/ftkextract6.jpg)  

<a name="hfs"></a)
### Extraction de fichiers à partir d'images de disques HFS (Hierarchical File System)
Dans certains cas, vous constaterez que ni Bitcurator ni FTK Imager ne sont capables d'extraire des fichiers d'une image disque. En général, cela est dû au fait que le support est formaté à l'aide d'un système de fichiers que les systèmes d'exploitation modernes ne peuvent pas lire.


Neuf fois sur dix, lorsqu'une image disque ne peut être lue ou montée sur une machine moderne, c'est parce que le disque utilise le système de fichiers HFS. HFS (Hierarchical File System) est un système de fichiers Apple associé aux versions "classiques" du système d'exploitation Mac (c'est-à-dire celles antérieures à OS X). Bien que les machines modernes ne puissent pas lire HFS en natif, nous pouvons utiliser un outil open source appelé HFSExplorer (inclus dans Bitcurator) pour exporter des fichiers utilisables à partir de tels disques. C'est le même outil utilisé par Brunnhilde pour caractériser et extraire des fichiers de disques au format HFS.


HFSExplorer ne peut lire que des images disque brutes. Si vous commencez avec une image disque EWF/E01, vous devez d'abord convertir votre image disque E01 en un format brut que HFSExplorer peut lire. Pour ce faire, utilisez un utilitaire en ligne de commande appelé ewfexport. Dans Bitcurator, ouvrez un terminal de ligne de commande, naviguez jusqu'au répertoire contenant l'image disque E01 cible et entrez la commande

```ewfexport [FILENAME.E01]```

Si l'image de la disquette Encase a été divisée en plusieurs parties (E01, E02, etc.), il suffit de faire pointer ewfexport sur le fichier E01.
À ce stade, ewfexport vous demandera de fournir des informations supplémentaires. Saisissez les données suivantes :
* **Exportation au format** : brut (ce devrait être le format par défaut ; si c'est le cas, il suffit d'appuyer sur entrée)
* **Chemin cible et nom de fichier sans extension**... : ./FILENAME
* Taille du fichier du segment de preuve en octets : 0 (ce devrait être la valeur par défaut ; si c'est le cas, il suffit d'appuyer sur la touche Entrée)
* **Démarrer l'exportation à la valeur de décalage** : 0 (ce devrait être la valeur par défaut ; si c'est le cas, il suffit d'appuyer sur la touche Entrée)
* **Nombre d'octets à exporter** : valeur maximale dans la plage (ce devrait être la valeur par défaut ; si c'est le cas, il suffit d'appuyer sur la touche Entrée)
À ce stade, ewfexport vous indiquera que le processus peut prendre quelques minutes et que vous pouvez commencer. Lorsque le processus est terminé, il devrait y avoir un fichier *.raw dans votre destination cible pour correspondre au fichier E01 que vous avez sélectionné comme entrée.
Une fois l'image disque brute obtenue, ouvrez HFSExplorer (situé dans le dossier "Additional Tools" sur le bureau).

![hfsexplorer1](http://wiki.bitcurator.net/images/c/c2/HFS1.png)


Dans le menu "Fichier", sélectionnez "Charger le système de fichiers à partir du fichier", puis sélectionnez le fichier image disque brut.


![hfsexplorer2](http://wiki.bitcurator.net/images/3/30/HFS2.png)  


Si le chargement de l'image brute entraîne une erreur, le support n'a probablement pas été formaté comme un disque HFS. À ce stade, prenez note dans votre tableur de stabilisation du versement et consultez l'archiviste numérique.


Si HFSExplorer peut lire le disque, il vous donnera une option sur la partition à lire. En général, vous voudrez choisir HFS (si ce n'est pas une option ou si vous n'êtes pas sûr ici, consultez l'archiviste numérique). Vous devriez maintenant voir une liste de fichiers.


La dernière étape consiste à exporter ces fichiers de HFSExplorer vers un emplacement de bureau ou de réseau. Pour exporter des fichiers :


* Sélectionnez tous les fichiers à exporter (à ce stade, il devrait s'agir de tout, y compris les fichiers système) et appuyez sur le bouton "Extraire".

![hfsexplorer3](http://wiki.bitcurator.net/images/8/88/HFSextract1.png)  

* Choisissez votre lieu de destination et sélectionnez "Extraire ici".

![hfsexplorer4](http://wiki.bitcurator.net/images/6/61/HFSextract2.png)  

* Une fenêtre pop-up apparaîtra pour vous demander si vous souhaitez suivre des liens symboliques pendant l'extraction. Sélectionnez "Yes".

![hfsexplorer5](http://wiki.bitcurator.net/images/0/0a/HFSextract3.png)  

* Si tout se passe bien, vous recevrez un message disant "Extraction terminée". REMARQUE : il est fréquent que HFSExplorer rencontre un problème de caractères non valides dans les noms de fichiers pendant le processus d'exportation, en raison des différences entre les caractères de noms de fichiers autorisés par HFS et les systèmes de fichiers modernes. Lorsque HFSExplorer rencontre des fichiers contenant de tels caractères, une fenêtre contextuelle apparaît et vous demande de renommer automatiquement ou manuellement les fichiers. Vous pouvez sélectionner le renommage automatique, qui remplacera les caractères "illégaux" tels que les barres obliques ("/") et les points (".") par des traits de soulignement ("_").

<a name="fichiers_logiques"></a>
## Extraction des archives et rapport sur les fichiers logiques
Les fichiers peuvent être extraits des paquets d'archives via l'utilisation de logiciels libres et open source tels que 7zip (Windows/Linux) ou The Unarchiver (Mac). L'extraction de fichiers peut ne pas être nécessaire à des fins de rapport, car des outils comme Brunnhilde sont capables d'analyser le contenu de paquets d'archives communs.


L'outil de rapport standard pour les images non disque au CCA est [Brunnhilde](https://github.com/timothyryanwalsh/brunnhilde). Voir le site de Brunnhilde Github pour des informations détaillées sur l'utilisation de cet outil. Une interface graphique pour le programme est également disponible.


Brunnhilde recueillera des informations telles que :
* Types et versions de formats de fichiers
* Structure organisationnelle existante
* Étendue et types de fichiers courants dans les différents répertoires
* Duplication du contenu
* Problèmes potentiels de préservation
* Problèmes potentiels liés aux informations personnelles et à la confidentialité
Si bulk_extractor est exécuté avec Brunnhilde, les rapports résultants peuvent être analysés dans BitCurator à l'aide de BEViewer.

<a name="deplacement"></a>
## Déplacement des dossiers vers le lieu de traitement
Une fois les fichiers prêts à être classés et décrits et les rapports préliminaires établis, les copies de travail des fichiers sont déplacées vers un dossier dans le réseau partagé des catalogueurs. Il s'agit de copies temporaires destinées uniquement à être consultées sur les postes de travail CAO et autres ordinateurs en réseau au CCA. Les copies "master" des SIP doivent être conservées dans BitCurator dans un répertoire siuté dans /mnt/1TB_RAID/ jusqu'à ce que le traitement soit terminé.

<a name="pronom"></a>
## Soumission des fichiers à PRONOM

Si Brunnhilde renvoie des types de fichiers non identifiés, il peut être utile de les soumettre à [PRONOM](http://www.nationalarchives.gov.uk/PRONOM/Format/proFormatSearch.aspx?status=new), le registre des formats de fichiers qui supporte Siegfried. Pour ce faire :
1. Remplissez une nouvelle ligne sur le document de suivi interne pour les soumissions de CCA à PRONOM. Tous les champs sont facultatifs, car la quantité d'informations dont vous disposez sur chaque type de format variera. Le document Excel se trouve ici : \int.cca\Divisions\Collection\06_Archives\Archives numériques\Systems Development\PRONOM\PRONOM_FileFormatsSubmissions.xlsx
2. Utilisez les informations du tableur pour remplir le [formulaire de soumission PRONOM](https://www.nationalarchives.gov.uk/contact-us/submit-information-for-pronom/pronom-request-form/). Cochez la case indiquant si vous disposez d'échantillons de fichiers, et veillez à inclure la signature hexagonale du nouveau type de fichier si vous avez pu en identifier un.
3. Ensuite, compressez vos échantillons de fichiers (2-3 maximum si possible) et soumettez-les à PRONOM. Cela peut se faire de deux façons :
   1. Si les fichiers sont suffisamment petits pour tenir dans un e-mail, ils peuvent être envoyés directement à l'employé de la TNA qui vous contactera.
   2. Si les fichiers zippés sont trop volumineux, vous pouvez partager le dossier via le Cloud en faisant une demande auprès du service informatique. Remplissez le "Formulaire de partage externe" disponible sur l'Intranet du CCA et envoyez-le à soutien.informatique@cca.qc.ca. Le formulaire de demande est disponible sur l'Intranet (Formulaires, Technologies. Une fois rempli, il peut être envoyé au soutien informatique (soutiens@cca.qc.ca).
Une fois la demande traitée, le format de fichier sera pris en considération pour être inclus dans une prochaine version de PRONOM.
