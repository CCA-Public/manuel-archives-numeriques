# Ressources supplémentaires

Des ressources utiles, notamment :

* [Matériel de lecture](#lecture)
* [Identification et information des supports de stockage numérique](#stockage)
* [Identification et informations sur le format de fichier](#format_de_fichier)
* [Outils de préservation numérique](#preservation)
* [Ressources en matière de commandes](#res_script)
* [Commandes utiles](#scripts)
* [Préservation de la conception assistée par ordinateur](#conception)
* [Ressources générales](#generales)


<a name="lecture"></a>
## Matériel de lecture
### Préservation numérique 101
* Lavoie, Brian. "[The Open Archival Information System (OAIS) Reference Model: Introductory Guide (2nd Edition),](http://www.dpconline.org/component/docman/doc_download/1359-dpctw14-02)" DPC Technology Watch Report, 2014.
* Trace, Ciaran. "[Beyond the Magic to the Mechanism: Computers, Materiality, and What it Means for Records to Be 'Born Digital,](https://www.ischool.utexas.edu/~cbtrace/pubs/CBT_Archivaria_2011.pdf)" Archivaria 72, 2011.
* Caplan, Priscilla. "[Understanding PREMIS](http://www.loc.gov/standards/premis/understanding-premis-rev2017.pdf)," Library of Congress Network Development and MARC Standards Office, revised 2017.
### Sur la description archivistique
* Callahan, Maureen. "[The Value of Archival Description Considered](https://icantiemyownshoes.wordpress.com/2014/04/04/the-value-of-archival-description-considered/)", Chaos->Order, 2014 : Pas strictement une lecture de préservation numérique, mais de l’information utile qui devrait être lue et revisiter pour quiconque arrange et décrit des archives.

### Sur le code/logiciel
* Ford, Paul. "[What is code](http://www.bloomberg.com/graphics/2015-paul-ford-what-is-code/) ?", Bloomberg Businessweek, 11 juin 2015 : Probablement le meilleur article jamais écrit (et le plus divertissant) sur la nature des codes/logiciels.

<a name="stockage"></a>
## Identification et information des supports de stockage numérique
* [Connaître vos médias](http://lib.utsa.edu/knowyourmedia/)

<a name="format_de_fichier"></a>
## Identification et informations sur le format de fichier
* [Siegfried](http://www.itforarchivists.com/siegfried) : Vous avez un dossier avec une extension de dossier manquant ou suspect ? Faites glisser le fichier sur le marteau de Siegfried et ce site fera de son mieux pour reconnaître le fichier pour vous.
* [Toutes les extensions connues](http://www.digipres.org/formats/extensions/) : Vous ne savez rien d'un fichier à part son extension ? C'est un bon point de départ.
* [PRONOM](http://www.nationalarchives.gov.uk/PRONOM/Default.aspx) : Le registre de formats de fichiers le plus complet et le plus détaillé. Développé et maintenu par les Archives nationales du Royaume-Uni.
* [Planification de la viabilité des formats numériques pour les collections de la Library of Congress](http://www.digitalpreservation.gov/formats/index.shtml)

<a name="preservation"></a>
## Outils de préservation numérique
* [COPTR](http://coptr.digipres.org/Main_Page) : le registre des outils de préservation numérique appartenant à la communauté. Comprend la grille d'outils utiles et classe les outils de préservation numérique par fonction.
* [Spécification BagIt 0.97](http://www.digitalpreservation.gov/documents/bagitspec.pdf) : Les spécifications du schéma de conditionnement et de validation largement utilisé, développé par la Library of Congress.
* [Bitcurator wiki](http://wiki.bitcurator.net/index.php?title=Main_Page)
* [Archivematica documentation](https://www.archivematica.org/en/docs/archivematica-1.4/)
* [Preserving optical media from the command line](http://blog.kbresearch.nl/2015/11/13/preserving-optical-media-from-the-command-line/)

<a name="res_script"></a>
## Ressources en matière de commandes
* [Script Ahoy](http://dd388.github.io/crals/) : "Notre ressource communautaire est destinée à fournir des liens utiles et des codes de script spécifiquement tirés d'exemples réels dans les archives et les bibliothèques".
* [Cours accéléré sur la ligne de commande](https://learnpythonthehardway.org/book/appendixa.html) : Learn Python the Hard Way

<a name="scripts"></a>
## Commandes utiles

* **Conversion par lots de fichiers dans un répertoire et des sous-répertoires en utilisant LibreOffice.**

      cd topDirectory
      for f in $(find . -type f -name "*EXT"); do libreoffice --convert-to doc $f --outdir $(dirname $f); done

   Remplacez "EXT" par l'extension de fichier des fichiers originaux ; notez que cette opération est sensible aux espacements dans le nommage des fichiers Remplacez "doc" par l'extension de fichier vers laquelle les fichiers doivent être convertis.
   Voir "[Formats de fichiers supportés](https://en.wikipedia.org/wiki/LibreOffice)" pour plus d'informations.


* **Décompressez de façon récursive les fichiers dans un nouveau dossier avec le titre du fichier zip à leur place actuelle dans le répertoire, puis supprimez le fichier zip original lorsque cela est fait** :

      cd topDirectory
      for F in $(find . -type f -name *.zip); do unzip "$F" -d "${F%.*}/" && rm "$F"; done
  
   [(Source)](https://stackoverflow.com/a/30339287/9459120)

   Pour le même résultat avec les fichiers .rar, utilisez :

      cd topDirectory
      for F in $(find . -name "*.rar"); do unrar x "$F" "${F%.*}/" && rm "$F"; done

   Notez que la commande find est sensible aux espacements dans le nommage des fichiers. Elle devra donc être modifiée en fonction des noms attribués aux fichiers zip ou rar. Les deux formats ne doivent pas comporter d'espaces dans leur nom de fichier, sinon la 
   commande échouera. Si nécessaire, utilisez la commande Detox avant d'extraire les fichiers.


* **Identifiez les répertoires en double dans une collection :**

   Essayez d'utiliser [Direct-Dedupe](https://github.com/stefanabreitwieser/direct-dedupe) et suivez ensuite les instructions ci-dessous. Il a été construit à partir des commandes suivantes :

   Exécutez les scripts suivants dans la ligne de commande individuellement. (Remplacez topDirectory par le chemin d'accès au fichier pour le répertoire de plus haut niveau).

      cd topDirectory/
      find . -type d >> /home/bcadmin/Desktop/directories.csv
      for D in $(find . -type d); do du -sh $D >> /home/bcadmin/Desktop/filesize.csv; done
      for D in $(find . -type d); do find $D -type f -exec md5sum {} + | awk '{print $1}' | sort | md5sum >> /home/bcadmin/Desktop/checksums.csv; done
			
   Cette commande finale peut prendre un certain temps en fonction de la taille de la collection. Ensemble, ces commandes permettent de créer trois feuilles de calcul CSV Excel sur le bureau Bitcurator, contenant respectivement la liste des répertoires, leur taille 
   lisible par l'utilisateur et leurs sommes de contrôle. Déplacez les colonnes dans une seule feuille de calcul Excel, en gardant à l'esprit que les colonnes nécessitent un léger nettoyage des données afin de les aligner. Il peut être plus facile de faire du 
   TOPDIRECTORY un sous-répertoire et de combiner toutes les feuilles de calcul Excel à la fin si vous avez plus que quelques milliers de répertoires au total.

   Une fois que vous vous êtes assuré qu'ils correspondent, créez des en-têtes pour chacune des colonnes et insérez des filtres (Data/Filters ou Donnees/Filtrer). Mettez en évidence la colonne de la somme de contrôle et faites Accueil/Mise en forme 
   conditionnelle/Règles de mise en surbrillance des cellules/Valeurs en double. Cela modifiera la couleur de tous les doublons de sommes de contrôle, vous permettant ainsi d'identifier et de supprimer les répertoires en double.


* **Identifiez tous les fichiers avec des horodatages problématiques dans un répertoire et modifiez les horodatages :**

      cd topDirectory
      find . -type f -newermt "YYYY-MM-DD" ! -newermt "YYYY-MM-DD" -exec touch -t "YYYYMMDDHHMM" {} +

   ([Source 1](https://askubuntu.com/questions/191044/how-to-find-files-between-two-dates-using-find) et [Source 2](https://stackoverflow.com/questions/3718645/unix-shell-script-update-timestamp-on-all-sub-directories-and-sub-files-includ))

   Dans ce cas, le script recherchera des fichiers (-type f) dans une certaine plage de dates (-newermt "YYYY-MM-DD" ! -newermt "YYYY-MM-DD"), puis il modifiera ces dates pour les remplacer par celles spécifiées par "YYYYMMDDHHMM".

   Avant décembre 2018, il a été déterminé que si la modification était requise, suite à un problème d'interprétation de l'horodatage par le système de temps UNIX, la nouvelle date devrait être "197001010000", ce qui correspond au temps 0 dans le système de temps UNIX. 
   Cette stratégie a été réévaluée et la nouvelle date devrait être dérivée du contenu de l'archive en cours de traitement. Confirmer la date de remplacement avec Digital Archivist.


* **L'utilitaire Detox nettoie les noms de fichiers et les répertoires en supprimant les espaces et en nettoyant les caractères Latin-1 (ISO 8859-1) encodés en ASCII 8 bits, les caractères Unicode encodés en UTF-8 et les caractères d'échappement CGI.**

   Pour faire un test (c'est-à-dire voir les changements de noms de fichiers proposés sans effectuer les changements) :

      detox -rn topDirectory

   Pour effectuer les changements :

      detox -r topDirectory

* **Lister et supprimer les fichiers et répertoires vides.**
    Pour lister tous les fichiers et répertoires vides :

      cd [topDirectory]
      find . -empty

    Pour supprimer les fichiers vides :
      find . -type f -empty -delete

    Pour supprimer les répertoires vides :
      find . -type d -empty -delete

* **Pour trouver et supprimer les fichiers cachés**

      cd filepath/to/directory find -type f -name '.*' (#pour trouver tous les fichiers qui commence par un .)
      cd filepath/to/directory find -type f -name '.*' -delete (#pour supprimer tous les fichier qui commence par un .)

      find -type f -name "*.db" -delete

      find -type f -name "~*" -delete

      find -type f -name "*.DS_Store" -delete


* **Imprimer les discordances de checksum entre le fichier checksum.md5 et le répertoire d'objets du terminal**

      cd /path/to/metadata/directory 
      md5deep -rlX checksum.md5 ../objects

    (le drapeau -X affiche le hachage et le nom de fichier pour chaque fichier du répertoire des objets qui ne correspond pas à la liste des hachages connus dans le fichier checksum.md5)
  

* **Supprimer en lot les virgules des noms de fichiers et les remplacer par des traits de soulignement**

      cd /path/to/directory
      for f in $(find . -name "*,*"); do rename -v 's/,/_/' $f; done

    Notez que cela ne changera que la première virgule de chaque nom de fichier. Par exemple, si un nom de fichier contient cinq virgules, vous devrez exécuter la commande cinq fois pour remplacer chaque virgule.


* **Synchroniser les dossiers**
Ce script copie ou synchronise un dossier source avec un dossier de destination. Il est particulièrement utile si vous avez une copie de vos fichiers sur un RAID et sur Processing, et souhaitez en mettre une à jour pour refléter le traitement sans avoir à faire un copier-coller de l'ensemble. Pour les archives de grande amplitude, ce processus accélère le traitement  car il permet de conserver tous les fichiers qui restent tel quel.
Le script crée une copie du dossier source, nommé de la même façon, dans le répertoire de destination. Si le titre de ce dossier existe déjà, il synchronisera les fichiers. `-qam` est destiné à la copie silencieuse (c'est-à-dire aux messages d'erreur 	uniquement), à la copie d'archives et au découpage des répertoires vides. `--delete` supprime tous les fichiers à la destination qui n'existent pas à la source.

    Notez que ce script **écrase, supprime et utilise sudo**, ce qui signifie qu'il est très puissant. Il n'est pas recommandé de l'utiliser sans avoir une certaine expérience de rsync.

      sudo rsync -qam --delete "/PATH/TO/SIPs/" "/PATH/TO/PARENT_OF_SIPs/"
  

* **Déverrouiller des dossiers**

   Cette commande déverrouille le dossier en utilisant "sudo". 
   Souvent, lors de la création d'une image disque sur le Bitcurator, un fichier vérouillé peut être créé. Si vous avez besoin de déverrouiller un dossier, remplacez le * par le chemin du dossier.

      sudo chmod 777 *

    ou utilisez-la de manière récursive pour déverrouiller tous les sous-dossiers.

      sudo chmod -R 777 *
  
* **Analyse antivirus**

    Cette commande utilise le logiciel clamAV pour lancer l'analyse antivirus sur un dossier ou sur des fichiers.

      clamscan -r /path/to/staging --max-filesize=Xm --max-scansize=Ym > collection.log

    X correspond à la plus grande taille de fichier (en mégaoctets) que vous souhaitez scanner, et Y correspond au plus grand nombre de mégaoctets que vous souhaitez extraire d'un seul fichier compressé.

* **Pour ajouter un préfixe et un suffixe aux fichiers (répertoires)**

      ls | xargs -I {} mv {} PRE_{}
      ls | xargs -I {} mv {} {}_SUF

<a name="conception"></a>
## Préservation de la conception assistée par ordinateur
* Ball, Alex. "[Preserving Computer-Aided Design (CAD)](http://dx.doi.org/10.7207/twr13-02)," DPC Technology Watch Report 13-02, April 2013.
* Barrett, Anne. "[Born-digital Architectural Records: Defining the Archivable Record](https://cdr.lib.unc.edu/indexablecontent/uuid:4b813f81-387f-4fb7-9f5e-daa7f7b764f1)," UNC Master's Thesis, 2012.
* Smith, MacKenzie. "[Curating Architectural 3D CAD Models](https://ijdc.net/index.php/ijdc/article/view/81)," The International Journal of Digital Curation 1, vol. 4, 2008.

<a name="generales"></a>
## Ressources générales
* [Digital Curation Google group](https://groups.google.com/forum/?fromgroups#!forum/digital-curation) : Un groupe Google sur la curation numérique.
* [BitCurator Users Google group](https://groups.google.com/g/bitcurator-users) : Le groupe Google des utilisateurs de BitCurator.
* [Manuel de préservation numérique du Digital Preservation Coalition](https://www.dpconline.org/handbook) : une version française est disponible ! 
* [The Signal](http://blogs.loc.gov/digitalpreservation/) : Un blog de la Library of Congress sur la préservation numérique.
* [DSHR's blog](http://blog.dshr.org/) : Le blog de David S. Rosenthal, vétéran de la préservation numérique et développeur de LOCKSS.
* [Bentley Historical Library ArchivesSpace-Archivematica-DSpace Integration project blog](http://archival-integration.blogspot.ca/) : Bien qu'il s'agisse d'un blog qui parle d'un projet spécifique de préservation numérique, il contient de nombreux articles pertinents sur les problèmes auxquels sont confrontés les archivistes et les institutions qui traitent des archives numériques.
