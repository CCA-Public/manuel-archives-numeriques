# Accès

* [Définition des DIP de type CCA](#definition)
* [Créer des DIP de type CCA](#creer)
* [Workflow d’Accès](#workflow)

<a name="definition"></a>
## Définition des DIP de type CCA
Les DIP de type CCA prennent la forme suivante :


`[transfer name]_[AIP UUID]_DIP` (top directory)
`----METS.[AIP UUID].xml` (Fichier METS décrivant le contenu du DIP)
`----objects` directory
`--------[transfer name].zip` (Contenu du DIP zippé en un seul fichier)


Le fichier zip, dans le répertoire `objects`, contient une copie de tous les fichiers originaux, inclus dans le transfert - avec les noms de fichiers et les dates des dernières modifications restaurées à leurs valeurs d'origine -, ainsi qu'une copie du répertoire `submissionDocumentation` de l'AIP et du fichier METS de l'AIP.

<a name="creer"></a>
## Créer des DIP de type CCA
Les DIP de type CCA peuvent être créés à partir des AIP enregistrés dans le service de stockage en utilisant le script [create_dip.py](https://github.com/artefactual/automation-tools/blob/master/aips/create_dip.py) inclus dans les outils d'automatisation d'Artefactual. La meilleure pratique (sans utiliser SCOPE) pour générer un DIP, à la demande, à partir d'un AIP enregistré, consiste à appeler le script Python, avec tous les paramètres nécessaires à l'aide du script shell [create_dip_script.sh](https://github.com/artefactual/automation-tools/blob/master/etc/create_dip_script.sh). Pour plus de détails, voir le site [Automation Tools repo](https://github.com/artefactual/automation-tools#dip-creation).


Sur le pipeline Archivematica VSP-AMPL-02, le script [create_dips_job.py](https://github.com/artefactual/automation-tools/blob/master/aips/create_dips_job.py) est configuré dans Automation Tools pour générer automatiquement un DIP pour chaque AIP stocké dans les bibliothèques AIP appropriés (à l'exception de ceux utilisés pour stocker des AIP "bruts" non traités).


Une version locale d'Automation Tools a également été installée et configurée sur chacun des postes de travail BitCurator pour permettre la création locale de DIP dans BitCurator selon les besoins - par exemple, pour aider à remplir une demande de référence. Pour créer un DIP sur l'une des stations BitCurator :


* Cherchez et copiez l'UUID de l'AIP concerné dans le service de stockage
* Exécutez le script `create_dip_script.sh`, en passant l'UUID AIP en premier argument :
* `/mnt/1TB_RAID/dips/automation-tools/create_dip_script.sh <UUID>`


Le DIP sera créé dans `/mnt/1TB_RAID/dips/dips`.

<a name="workflow"></a>
## Workflow d’Accès
[SCOPE](https://github.com/CCA-Public/dip-access-interface) est une interface d'accès aux archives numériques, développée par le CCA et Artefactual Systems. Lorsqu'un nouveau matériel est ingéré par le pipeline 2 d'Archivematica, un DIP est automatiquement créé et introduit dans SCOPE. Lorsqu'un chercheur demande l'accès à du matériel né numérique traité, Reference lui crée un login SCOPE afin que le chercheur puisse accéder au matériel de façon autonome.


SCOPE est uniquement accessible au chercheur à partir du poste de travail CAO, situé dans la salle d'étude du CCA, ainsi qu’à partir du poste de travail de virtualisation. Le poste de travail CAO et le poste de travail de virtualisation de la salle d'étude n'ont pas d'accès Internet et les ports USB y sont bloqués. Les chercheurs peuvent effectuer des captures d'écran du matériel selon leurs besoins. L’équipe de la référence les regroupe ensuite dans un fichier PDF à faible résolution pour les envoyer au chercheur par courriel.


Le personnel des archives du CCA (pas les chercheurs internes) peuvent accéder à SCOPE via les machines BitCurator et le bureau de référence. L'accès à la recherche est limité à la salle de lecture uniquement, y compris pour tous les autres membres du personnel du CCA.


Les documents de la collection numérique non traités peuvent être mis à disposition, au cas par cas. Le personnel de référence doit informer l'archiviste numérique de la demande. Ce dernier, en se basant sur le workflow, crée un DIP [ci-dessus](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/access.md#dipcreation) et déplace les fichiers dans le dossier "Research Materials" destiné au chercheur. Le chercheur peut alors accéder aux fichiers via les postes de travail de la salle d'étude.
