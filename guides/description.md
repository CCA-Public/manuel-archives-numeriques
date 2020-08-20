  # Description des archives nées-numériques
Une fois le plan de traitement établi et l’organisation global de la ou des acquisition(s) finalisée, il est temps de réfléchir plus en détail à la seconde moitié du traitement : la description. Ce guide décrit les normes du CCA pour la description des documents nés numériques dans les fichiers Excel appropriés et au sein du système de musée (TMS), il comprend:

* [Principes et lignes directrices pour la description des archives nées-numériques](#principes)
* [Description des fonds, des séries et des projets](#description_des_fonds)
* [Description du niveau du fichier ("groupe")](#description_groupe)
  * [Saisie de la description au niveau du fichier dans les documents Excel](#fichier_excel)
  * [Saisie de la description au niveau du fichier dans le TMS](#fichier_tms)
    * [Informations sur la gestion interne](#gestion_interne)
    * [Éléments de description des archives](#elements_description)
* [Description de la pièce ("item")](#description_piece)
  


<a name="principes"></a>
## Principes et lignes directrices pour la description des archives nées-numériques
* "Choisissez de guider, pas de cartographier" : Laissez le chercheur faire ses propres recherches, mais donnez-lui une idée suffisamment précise du contenu et du contexte des documents pour qu'il sache où concentrer ses énergies. Considérez le passage suivant de l'ouvrage de Maureen Callahan "[The Value of Archival Description, Considered](https://icantiemyownshoes.wordpress.com/2014/04/04/the-value-of-archival-description-considered/)" :


Lorsque j'enseigne la description, j'incite les travailleurs à évaluer les documents plutôt qu'à les représenter. Par exemple, une série de correspondance comprend-elle des lettres longues, consistantes et manuscrites dans lesquelles l'auteur verse son cœur ? Ou s'agit-il de copies carbones dictées à partir de formulaires ? Le titre "Lettre de John Doe à Jane Smith" ne nous le dit pas, mais la portée et le contenu d'une note d'archiviste le peuvent. Il faut beaucoup de temps pour taper "Correspondance" et la date un million de fois. Les chercheurs ne préféreraient-ils pas une description globale et une fourchette de dates avec une jolie note complète sur le type de correspondance et le type d'informations qu'elle contient ? Il s'agit d'un choix de guide plutôt que de carte.


* "Laissez l’information numérique se décrire elle-même" : Les informations exploitables par la machine, telles que l'étendue, les formats de fichiers et les métadonnées du système de fichiers, doivent être saisies automatiquement, jamais calculées à la main et rarement transcrites.
* Les archives né numériques peuvent ne pas refléter la terminologie/pratique des étapes d’un projet architectural traditionnel - ne forcez pas la terminologie là où elle ne convient pas.
* La description sera saisie et mise à jour dans des documents Excel de traitement. La saisie de ces données dans TMS nécessitera la saisie manuelle de certains champs, mais vous pouvez faire un copier-coller à partir de votre document Excel de traitement lorsque cela est possible. Assurez-vous que toutes les révisions de votre description sont effectuées avant de saisir les données dans TMS.
* Ne passez pas trop de temps au niveau du fichier. Les descriptions au niveau du fichier sont en grande partie automatisées par le processeur d'images disque et le processeur de dossiers du CCA. Dans de nombreux cas, il suffit d'examiner rapidement les fichiers inclus et d'ajouter un titre. Résistez à la tentation d'ouvrir et d'examiner chaque fichier numérique dans un répertoire/une image disque donné(e).

<a name="description_des_fonds"></a>
## Description des fonds, des séries et des projets
Vos descriptions de niveau supérieur (fonds, séries et projets) doivent suivre les directives établies pour ces niveaux de description dans le manuel général de traitement des archives du CCA.


Les documents relatifs aux fonds, séries et projets doivent être saisis directement dans TMS, mais doivent d'abord être rédigés et examinés dans un document en texte clair (Word ou Excel).


L’information concernant les documents numériques dans les relevés de collationnement des documents au niveau du fonds, de la série et du dossier doivent prendre la forme suivante : "x fichiers numériques (y KB/MB/GB)", par exemple "760 fichiers numériques (18 GB)".

<a name="description_groupe"></a>
## Description du niveau du fichier ("groupe")
La description au niveau du dossier ("groupe") est le niveau de description le plus bas effectué au cours de projets typiques de traitement et doit suivre les directives énoncées dans le manuel général de traitement des archives du CCA. La description se fera d'abord dans des documents Excel. Ne saisissez aucune information au niveau du dossier dans TMS avant que ce document Excel n’ait reçu l'approbation de l'archiviste numérique.


Notez que tous les répertoires de contenu numérique doivent être décrits comme des fichiers ("groupes"), même s'ils ne contiennent qu'un seul fichier numérique.

<a name="fichier_excel"></a>
### Saisie de la description au niveau du fichier dans les documents Excel
La description au niveau du fichier doit être saisie et examinée dans des documents Excel (une feuille de calcul par série ou par projet, en fonction du volume).


| Colonne | ISAD élément | Obligatoire? | Valeur|
| :----: | :------------: | :---------: | :---- |
| Parent | n/a | Oui| Identifiant du parent immédiat (par exemple, série ou projet) |
| Identifiant | 3.1.1 | Oui | Identificateur du fichier (groupe). Il doit s'agir d'un numéro d'archive composé des numéros de fonds, de séries, de sous-séries, de dossiers et de groupes, selon le cas (e.g. "AP500.S1.1996.PR1.001" ou "AP174.S2.001") |
| Titre | 3.1.2 | Oui | Titre fourni ou original, selon les procédures de titrage standard. N'utilisez pas de nom de fichier ou de répertoire comme titre, sauf si vous ne pouvez pas fournir un titre plus succinct. |
| Créateur d'archives | 3.2.1 | Non | Indiquez la forme standard du nom du créateur du fonds |
| Expression de la date | 3.1.3 | Oui | Des années seulement. Ces informations seront pré-remplies dans des feuilles de calcul de description. Ne les révisez que si nécessaire (par exemple, si la valeur dans le système de fichiers est clairement fausse). |
| Date de début, Date de fin | 3.1.3 | Oui | Ces informations seront pré-remplies dans des feuilles de calcul de description. Ne les révisez que si cela s'avère nécessaire (par exemple, si la valeur dans le système de fichiers est clairement fausse). Toutes les dates doivent être au format ISO8601. Formats de date acceptables : AAAA-MM-JJ, AAAA-MM, AAAA. Si le fichier ne comporte qu'une seule date (par exemple 1990 ou 1990-01-20), celle-ci doit être saisie à la fois dans Début de la date et Fin de la date. |
| Niveau de description | 3.1.4 | Oui | "File" |
| Étendue et moyen | 3.1.5 | Oui | Ces informations seront pré-remplies dans des feuilles de calcul de description, sous la forme de "x fichiers numériques (y octets/KB/MB/GB/TB)". Sauf si la valeur est "VIDE", ne pas modifier sauf en cas de discussion avec l'archiviste numérique. |
| Portée et contenu | 3.3.1 | Oui | Ajoutez une note sur le champ d'application et le contenu si les informations sur le titre doivent être complétées (par exemple, avec des informations sur le support de stockage d'où proviennent les fichiers), si le contenu n'entre pas dans le champ d'application de votre description de niveau supérieur ou pour attirer l'attention sur des documents importants. Comme les groupes de documents numériques sont souvent volumineux et complexes, des notes détaillées sur la portée et le contenu seront plus courantes pour ce matériel que pour d'autres formats. Pour les fichiers provenant de supports numériques tels que les disquettes ou les CD, commencez la note par "Contenu complet de ..." ou "Contenu partiel de ..." et l'identificateur/le type de support, ainsi que toute annotation sur le support. Pour les groupes d'enregistrements nés sous forme numérique, le champ de note sur la portée et le contenu de votre feuille de calcul de traitement sera prérempli avec des informations générées par script sur l'historique du traitement et les formats de fichiers courants. Ces informations doivent être conservées à la fin de la note. *Exemple de note sur la portée et le contenu du SIP généré par le processeur de dossiers* : "Contient des fichiers de conception assistée par ordinateur en 3D, essentiels au processus de développement de Carbon Tower. La plupart des fichiers de conception sont dans Rhinocéros et sont classés dans des dossiers par année. Comprend également quelques rendus Maya ainsi que des fichiers de conception et d'images résultant des premières tentatives de modélisation de la Carbon Tower dans CATIA. Nom du répertoire d'origine : "3D CATIA MAYA RHINO". Formats de fichiers les plus courants : 3DM, fichier de texte brut, spécification initiale d'échange de graphiques (IGES), format de fichier binaire Maya, fichier DS_store (MAC)". |
| Arrangement | 3.3.4 | Non | Pas nécessaire au niveau du dossier mais peut être utilisé pour indiquer un réarrangement manuel lorsqu'il a été fait pour certains dossiers mais pas pour d'autres dans la même série. |
| Numéro d'adhésion | n/a | Oui | Numéro du Versement |
| Conditions d'accès | 3.4.1 | Non | N'entrez au niveau du dossier que lorsque les conditions d'accès diffèrent des conditions générales fixées à un niveau supérieur. |
| Conditions de reproduction | 3.4.2 | Non | Only enter at file-level when conditions governing reproduction differ from general conditions set at higher level. |
| Langue | 3.4.3 | Non | N'entrez pas au niveau du dossier, sauf dans de rares circonstances et après discussion avec un archiviste. |
| Aides à la recherche | 3.4.5 | Non | N'entrez pas au niveau du dossier, sauf dans de rares circonstances et après discussion avec un archiviste. |
| Unités de description connexes | 3.5.3 | No | N'entrez pas au niveau du dossier, sauf dans de rares circonstances et après discussion avec un archiviste. |
| Note | 3.6.1 | Non | N'entrez pas au niveau du dossier, sauf dans de rares circonstances et après discussion avec un archiviste. |
| Numéro de dossier | n/a | Non | n/a |
| Numéro de boîte | n/a | Non | n/a |
| Points d'accès aux sujets | n/a | Oui | "born-digital" (et, éventuellement, un autre type d'objet de la liste des normes de description des fichiers - par exemple, pour un répertoire de vidéos, vous pouvez saisir à la fois "born-digital" et "moving images". Lorsque vous saisissez plusieurs valeurs, assurez-vous qu'elles sont séparées par un tube) |
| Nom des points d'accès | n/a | Non | Facultativement, entrez le nom des points d'accès (et les rôles) des personnes physiques ou morales associées ou responsables de la création du fichier. N'entrez pas au niveau du dossier, sauf dans de rares circonstances et après discussion avec un archiviste. |  
| Description du statut | n/a | No | Laisser vide |
| Niveau de détail | n/a | No | Laisser vide |

<a name="fichier_tms"></a>
### Saisie de la description au niveau du fichier dans le TMS

Une fois votre document Excel de traitement examinée et approuvée par l'archiviste numérique, suivez les instructions suivantes pour saisir les informations dans TMS, en faisant des copier-coller à partir des feuilles de calcul lorsque cela est possible. Le meilleur moyen d'y parvenir est d'utiliser des modèles. Il existe déjà des modèles pour la description au niveau du fichier de divers types de documents ; pour un travail plus efficace, créez une version personnalisée du modèle "Archives - Fichiers - Born Digital" pour votre archive, contenant les informations suivantes:


* Créateur de l'archive
* Numéro du fonds
* Ligne de crédit


En particulier pour les collections de grand volume, l'utilisation d'un modèle de saisie des données, spécifique à l'archive et au type de document, accélérera considérablement le processus. Tous les enregistrements au niveau du dossier doivent être créés et associés à leur série et à leur aquisition en lot.


Les seuls types d'informations que vous devez saisir dans TMS et qui ne se trouveront pas dans votre feuille de calcul de traitement sont les associations et les éléments des [informations de gestion interne] ci-dessous (notez que nombre d'entre eux sont déjà saisis dans les modèles de saisie de données existants).

<a name="gestion_interne"></a>
#### Informations sur la gestion interne
| Champ de TMS | Valeur |
| :-----: | :-----: |
| Département | "Archives" |
| Objet virtuel | Non (non coché) |  
| Indicateurs du status de l'objet | "traitement en cours" (à classer en "inventaire" lors de la publication de l'aide de recherche) |
| Ligne de credit | Entrez comme d'habitude |  
| Numéro alternatif | Entrez le numéro de fonds (AP###) comme numéro alternatif pour tous les documents d'une archive, en utilisant la description "fonds number". | 
| Nombre de l'objet | "1" |  
| Nom de l'objet | "File" |  
| "Object type" attribut | "born-digital"/"né numérique" (et, optionnellement, un autre type d'objet) |



<a name="elements_description"></a>
#### Éléments de description des archives
| Colonne dans le tableur | Champ de TMS | Instructions |
| :-----: | :-----: | :------ |
| Parent | Elements reliés | Lier l'objet au versement via le type d'association "Est inclus dans |
| Identifiant | Numéro de l'objet | Copier et coller à partir du tableur |
| Titre | Titre | Copier et coller à partir du tableur |
| Créateurs | Personne(s) et institution(s) | Entrer le créateur en tant que constituant avec le rôle de "archive creator" |
| Dates | Dates | Saisissez les valeurs de date dans "Désignation date" |
| Niveau de description | Classification | "groupe" |
| Étendue et moyen | "Collation" saisie de texte | Copier et coller à partir du tableur |
| Portée et contenu | Description du contenu | Copier et coller à partir du tableur |
| Arrangement | "1.8B13-classement" saisie de texte | Copier et coller à partir du tableur |
| Numéro d'adhésion | Elements reliés | Lier l'objet au versement via le type d'association "Provient de" |
| Conditions governing access | "1.8B16a-restrictions à la consultation" text entry | Copier et coller à partir du tableur |
| Conditions de reproduction | "1.8B16c-restric. à l'utilis. et repro." text entry | Copier et coller à partir du tableur |
| Langue | "1.8B14-langue" text entry | Copier et coller à partir du tableur |
| Aides de recherche| "1.8B17-instruments de recherche" saisie de texte | Copier et coller à partir du tableur |
| Unités de description liées | "1.8B20a-docs reliés meme fonds" saisie de texte  | Copier et coller à partir du tableur |
| Note | "1.8B21-générale" saisie de texte  | Copier et coller à partir du tableur |  
| Nommez les points d'accès | Personne(s) et institution(s) | Inscrire en tant qu'électeurs avec des rôles appropriés (le cas échéant) |  



<a name="description_piece"></a>
## Description de la pièce ("item")
Au CCA, nous ne traitons généralement pas les fichiers numériques au niveau des items. Les métadonnées au niveau de l'élément sont au contraire générées automatiquement par Archivematica et enregistrées dans un `amdSec` dans le fichier METS de l'AIP pour chaque fichier numérique dans un SIP. Ces informations sont accessibles aux chercheurs via SCOPE.


L'équipe de numérisation a antérieurement décrit des fichiers numériques individuels dans le cadre du projet Find and Tell, et maintient ses propres normes descriptives au niveau du fichier, parfois appliquées aux documents d'archives nés numériques. Ce travail descriptif se trouve hors de la portée des tâches attribuées à l'équipe des Archives.
