# Manuel de Traitement des Archives Numériques du CCA
Il s'agit du manuel de traitement du CCA pour les archives nées numériques. Il consiste en un document vivant, édité en permanence, fonctionnant en tant que composante du manuel de traitement du CCA. Le manuel de traitement des archives numériques couvre chaque étape du processus de traitement des archives nées numériques, incluant la saisie de données, la classification, la description, ainsi que l'accès et l'ingestion dans notre dépôt numérique, Archivematica. Il comprend également des politiques et procédures générales, ainsi que des informations spécifiques sur les outils utilisés dans ce processus.

## Table des matières

* **[Guides détaillés](#details)**
* **[Introduction au traitement des archives nées-numériques](#introduction)**
* **[Le workflow des archives numériques en bref](#workflow)**
* **[Aperçu général sur la préservation numérique au CCA](#aperçu)**

<a name="details"></a>
### Guides détaillés
* **[L'acquisition et la stabilisation des archives nées numériques](guides/stabilisation.md)**
   * [Transferts de réseau](guides/stabilisation.md#transferts)
   * [Supports physiques temporaires](guides/stabilisation.md#supports-physiques-temporaires)
   * [Supports physiques originaux](guides/stabilisation.md#supports-physiques-originaux)
   * [Ingestion des données "brutes" dans un dépôt numérique](guides/stabilisation.md#integrer)

* **[Imagerie de disque support physique original](guides/Imagerie_de_disque.md)**
   * [Imagerie de disque avec Guymager (Bitcurator)](guides/Imagerie_de_disque.md#guymager)
   * [L'imagerie des supports physiques avec le FTK Imager](guides/Imagerie_de_disque.md#ftk)
   * [Imagerie de disque avec IsoBuster](guides/Imagerie_de_disque.md#isobuster)
   * [Imagerie de disques disquettes 5,25" avec FC5025](guides/Imagerie_de_disque.md#fc5025)
   * [L'imagerie sur disque avec le Kryoflux](guides/Imagerie_de_disque.md#kryoflux)
   * [L'imagerie sur disque avec le Nimbie et l'ImgBurn](guides/Imagerie_de_disque.md#nimbie)
   * [Dépannage](guides/Imagerie_de_disque.md#depannage)
   
* **[Prétraitement : Triage et évaluation des archives nées numériques](guides/Pretraitement.md)**
   * [Analyse des images de disque avec le Disk Image Processor](guides/Pretraitement.md#analyse)
   * [Extraction de fichiers à partir de paquets et d'images disque](guides/Pretraitement.md#paquets)
      - [Extraction de fichiers à partir d'images de disque avec Bitcurator](guides/Pretraitement.md#extraction_bitcurator)
         + [Outil de reporting BitCurator - Accès aux fichiers](guides/Pretraitement.md#reporting)
         + [Script de montage de l'image disque](guides/Pretraitement.md#script)
      - [Extraction de fichiers à partir d'images de disque avec FTK Imager](guides/Pretraitement.md#ftk)
      - [Extraction de fichiers à partir d'images de disques HFS (Hierarchical File System)](guides/Pretraitement.md#hfs)
   * [Extraction des archives et rapport sur les fichiers logiques](guides/Pretraitement.md#fichiers_logiques)
   * [Déplacement des dossiers vers le lieu de traitement](guides/Pretraitement.md#deplacement)
   * [Soumission des fichiers à PRONOM](guides/Pretraitement.md#pronom)

* **[Archives courriel et ePADD](guides/courriele.md)**

* **[Capturer les archives du Web à l'aide d'Archive-It](guides/archive-it.md)**

* **[Classement des archives de personnes nées-numériques](guides/classement.md)**
    * [Le principe de l'organisation des archives de personnes nées numériques](guides/classement.md#principe)
    * [Facteurs affectant l'organisation des archives nées numériques](guides/classement.md#facteurs)
      * [L’arrivée des archives au CCA](guides/classement.md#arriver)
      * [Organisation existante](guides/classement.md#existante)
      * [Contexte de création et d'utilisation](guides/classement.md#contexte)
      * [Nature de la collection d'archives](guides/classement.md#nature)
      * [Priorités institutionnelles](guides/classement.md#priorities)
      * [Élaboration d'un plan de traitement](guides/classement.md#elaboration)
      * [SIP non emballé (de préférence)](guides/classement.md#non_emballe)
      * [SIP emballé](guides/classement.md#emballe)
    * [Traitement des images disque avec Disk Image Processor](guides/classement.md#disk_image_processor)
    * [Traitement des répertoires de fichiers avec Folder Processor](guides/classement.md#folder_processor)
    * [Normalisation manuelle pour Archivematica](guides/classement.md#normalisation)
    * [Traitement des dossiers en cours de migration](guides/classement.md#migration)
    
 * **[Description des archives nées-numériques](guides/description.md)**
    * [Principes et lignes directrices pour la description des archives nées-numériques](guides/description.md#principes)
    * [Description des fonds, des séries et des projets](guides/description.md#description_des_fonds)
    * [Description du niveau du fichier ("groupe")](guides/description.md#description_groupe)
      * [Saisie de la description au niveau du fichier dans les documents Excel](guides/description.md#fichier_excel)
      * [Saisie de la description au niveau du fichier dans le TMS](guides/description.md#fichier_tms)
        * [Informations sur la gestion interne](guides/description.md#gestion_interne)
        * [Éléments de description des archives](guides/description.md#elements_description)
    * [Description de la pièce ("item")](guides/classement.md#description_piece)
    
 * **[Ingestion dans Archivematica](guides/ingestion.md)**
    * [Les workflows d’ingestion Archivematica](guides/ingestion.md#workflows)
    * [Configurations de traitement d'Archivematica](guides/ingestion.md#config_traitement)
    * [Ajout de métadonnées descriptives à l'AIP](guides/ingestion.md#ajout_aip)
    * [Politiques relatives au format de fichier CCA](guides/ingestion.md#politiques)

* **[Accès](guides/acces.md)**
	* [Définition des DIP de type CCA](guides/acces.md#definition)
	* [Créer des DIP de type CCA](guides/acces.md#creer)
	* [Workflow d’Accès](guides/acces.md#workflow)
 
 * **[L'administration d'Archivematica](guides/administration.md)**
 	* [Connexion](guides/administration.md#connexion)
	* [Commencer une ingestion](guides/administration.md#ingestion)
	* [Surveillance des serveurs d'Archivematica](guides/administration.md#surveillance)
	* [Vérification et réparation des réparations](guides/administration.md#verification)
	* [L'abandon des données MySQL et ES dans les pipelines](guides/administration.md#abandon)
	* [Suppression des AIP](guides/administration.md#suppression)
	* [Nettoyage après l'ingestion réussie d'outils d'automatisation](guides/administration.md#nettoyage)
	* [Réagir aux échecs des outils d'automatisation](guides/administration.md#reagir)
	* [Ajout et changement d'emplacement des AIP Store](guides/administration.md#aip_store)
	* [Mise à jour de la configuration de traitement des outils d'automatisation](guides/administration.md#miseajour)
	* [Libérer de l'espace lorsque le disque local est presque plein](guides/administration.md#liberer)
	* [Redémarrage des services](guides/administration.md#redemarrage)
	* [Rapport des modifications apportées au FPR par défaut d'Archivematica](guides/administration.md#modifications)
	* [Paramètres personnalisés d'Archivematica](guides/administration.md#parametres)
	* [Mises à jour d'Archivematica et dépendances](guides/administration.md#dependances)

* **[Logiciels et formats de fichiers CAO, BIM et modélisation 3D](guides/formats.md)**

* **[Ressources supplémentaires](guides/ressources.md)**
	* [Matériel de lecture](guides/ressources.md#lecture)
	* [Identification et information des supports de stockage numérique](guides/ressources.md#stockage)
	* [Identification et informations sur le format de fichier](guides/ressources.md#format_de_fichier)
	* [Outils de préservation numérique](guides/ressources.md#preservation)
	* [Ressources en matière de script](guides/ressources.md#res_script)
	* [Scripts utiles en ligne de commande](guides/ressources.md#scripts)
	* [Préservation de la conception assistée par ordinateur](guides/ressources.md#conception)
	* [Ressources générales](#generales)

<a name="introduction"></a>
## Introduction au traitement des archives nées-numériques
Pour les chercheurs, le processus d'accès aux archives numériques consiste en plusieurs étapes distinctes. Il est préférable de considérer ces étapes comme le résultat de projets distincts. En tant qu'archiviste ou technicien.ne aux archives numériques, vous serez impliqué dans les étapes de stabilisation, de prétraitement (triage), de traitement (classification et description) et d'ingestion. Chaque étape doit généralement commencer seulement lorsque l'étape précédente a été entièrement achevée (certains projets peuvent nécessiter une approche différente). Au sein d'une même archive ou même d'une même acquisition, ces étapes peuvent être réalisées par différentes personnes.

Les guides détaillés du présent manuel donnent des instructions plus précises sur la manière de mener à bien chacune des étapes du processus. Bien que ces instructions s'appliquent de manière générale, il est important de noter qu'en raison de la nature des premiers documents numériques acquis par le CCA, et de l’intérêt de ce dernier pour des documents supportés par des logiciels ou autres médias particulièrement complexes (de conception assistée par ordinateur par exemple) certains cas peuvent nécessiter une approche différente qui sera identifiée lors du prétraitement.

Quelques principes généraux sont à garder en tête lors du traitement des matériaux nés numériques :
- Les principes généraux de la théorie de la gestion des archives (ordre original, respect du fonds, description globale) s'appliquent aux documents nés numériques, au même titre qu'aux documents analogiques.
Peu de fonds sont uniquement constitués de matériel né numérique. Lorsque des documents numériques coexistent avec des documents d'autres formats, assurez-vous que vos décisions et actions de traitement de ces derniers tiennent compte et respectent le fonds dans son ensemble.
- Comme pour les matériaux analogiques, l'objectif fondamental du travail de traitement est de rendre les matériaux disponibles aux chercheurs dans des délais raisonnables et de fournir à nos utilisateurs les outils appropriés pour rechercher, identifier, sélectionner et obtenir les matériaux qui répondent à leurs besoins de recherche.
- Comme pour les matériaux analogiques, nous devons faire preuve de souplesse dans nos pratiques de classement afin de respecter au mieux la commande initiale et répondre aux besoins de nos utilisateurs. Ceci implique souvent de regrouper des documents aux formats différents dans une même série et dans des fichiers de projet. Toutefois, les réalités d'un ensemble particulier de fichiers nés numériques et d'autres facteurs peuvent nécessiter d'autres approches de classement au cas par cas.
- Les matériaux numériques contiennent déjà une grande partie de leur propre description et peuvent être traités de manière algorithmique, ce qui n'est pas le cas des matériaux analogiques. Laissez les machines accomplir les tâches pour lesquelles elles ont été conçues et concentrez vos efforts sur les tâches auxquelles les humains excellent (à savoir l'analyse du contenu et du contexte).
- Le travail de classement et de description doit généralement se concentrer sur les dossiers de niveau supérieur, dans une structure de répertoire, ou sur un support particulier considéré individuellement. Le classement et la description manuelle de fichiers individuels sont l'exception et ne doivent être entrepris que dans des cas exceptionnels et convenus lors de la planification du prétraitement.
- Les mesures adoptées, à chaque étape du workflow des archives numériques, sont documentées. Cette documentation est cruciale pour démontrer l'authenticité des fichiers numériques et permettre les efforts de préservation futurs.

<a name="workflow"></a>
## Le workflow des archives numériques en bref
1. Le matériel d'archives (né-numérique ou hybride) est archivé et stabilisé :
   1. Les fichiers envoyés via des transferts réseau ou des supports temporaires (par exemple, clés USB, disques durs externes) sont emballés sous forme de fichiers tar et stockés dans les archives non-traitées ou Dark Archive sous forme de copie "brute" avec leurs données d'acquisition.
   2. Des images disque sont créées à partir des supports physiques originaux, elles sont ensuite stockées dans les archives non-traitées ou Dark Archive en tant que copie "brute" avec leurs données d'accès.
2. Pré-traitement, triage et évaluation :
   1. Archiviste Numérique ou Archiviste de Traitement télécharge les AIP contenant les données brutes de tous les accès à traiter.
   2. Archiviste Numérique ou Archiviste de Traitement extrait les fichiers des paquets d'archives si nécessaire.
   3. Archiviste Numérique ou Archiviste de Traitement trie et évalue le contenu à l'aide d'outils comme [Brunnhilde](https://github.com/timothyryanwalsh/brunnhilde) et [Disk Image Processor](https://github.com/CCA-Public/diskimageprocessor).4. Une copie "de référence" des fichiers peut être déplacée sur des lecteurs réseau, où les fichiers peuvent être consultés à partir de postes de travail CAO pendant le traitement.
   5. L'archiviste chargé du traitement élabore un plan de traitement pour l'(les) acquisition(s).
   6. L'archiviste numérique, l'archiviste de traitement et éventuellement d'autres personnes (archiviste, conservation, etc.) se réunissent pour discuter du plan de traitement.
3. Arrangement et description :
   1. L'Archiviste de Traitement procède à l’élagage, la classification et à des actions de préservations tout en explorant le contenu des fichiers dans les postes de travail Bitcurator et CAO selon les besoins.
   2. L'Archiviste de Traitement utilise des outils tels que [Folder Processor, SIP Creator, et/ou Disk Image Processor](https://github.com/CCA-Public/cca-tools) pour créer des SIPs traités à partir des données d'acquisition brutes et commence la description au niveau du fichier dans le fichier Excel de traitement standard, généré par le processeur de dossiers ou le processeur d'images disque.
   3. L'Archiviste de Traitement complète et termine la description au niveau du fichier dans le fichier Excel de traitement standard, générée par le processeur de dossiers ou le processeur d'images de disque.
   4. L'archiviste de Traitement rédige les descriptions des fonds, des séries et des projets dans des fichiers de texte simple.
   5. Les descriptions sont examinées avec l'archiviste numérique et approuvées pour leur entrée dans TMS.
   6. L'archiviste chargé du traitement copie et colle les descriptions des fichiers texte et de la feuille de calcul de traitement dans TMS et crée des ensembles d'objets de documents nouvellement traités.
   7. L'archiviste chargé du traitement crée un enregistrement au niveau de la collection (s'il n'existe pas déjà) dans SCOPE.
4. Les SIP traités sont ingérés dans Archivematica
   1. Les SIP traités définitivement sont copiés dans un dossier surveillé sur le serveur principal du pipeline de traitement d'Archivematica.
   2. Les QA des archivistes de traitement ingèrent (extraction automatisée des métadonnées descriptives du TMS, normalisation, etc.) et stockent les DIP
   3. L'archiviste numérique effectue un contrôle final de qualité lorsque toutes les données d'une acquisition sont ingérées
   4. La copie "brute" des données d'accès est supprimée des archives non-traitées ou Dark Archive, sauf s'il existe une raison suffisante pour la conserver
5. Activités en cours :
   1. Surveillance de la santé des PIA dans Archivematica
   2. Restauration à partir de sauvegardes si nécessaire
   3. Accès et soutien à l'utilisation de SCOPE par les chercheurs
   
<a name="aperçu"></a>   
## Aperçu général sur la préservation numérique au CCA
Le CCA prend un certain nombre de mesures face à tous les fichiers numériques de sa collection, celles-ci contribuent à garantir leur accessibilité permanente pour une utilisation pérenne. Tous les fichiers des archives numériques du CCA sont :


* Scannés pour détecter les virus ;
* Précisément identifiés grâce à une comparaison automatisée avec les bases de données internationales de formats de fichiers telles que les Archives nationales britanniques PRONOM ;
* Dupliqués, lorsque cela est nécessaire et possible, dans des formats de fichiers neutres et faciles à conserver, qui ont plus de chances de demeurer accessibles à mesure que les logiciels et le matériel actuels devient obsolètes ;
* "Fingerprinted" (empreintes digitales) par l'utilisation de hachages cryptographiques (également appelés "checksums") et régulièrement vérifiés pour garantir leur authenticité permanente; et
* Stocké et sauvegardé dans un système redondant et géographiquement distribué selon les meilleures pratiques de l'industrie.


Toutes les actions qui ont lieu sur les fichiers une fois qu'ils sont ingérés dans le dépôt numérique du CCA sont documentées par une mise en œuvre de la norme de métadonnées PREMIS (PREservation Metadata : Implementation Strategies).

   
