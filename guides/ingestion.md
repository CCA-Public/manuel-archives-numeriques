# Ingestion dans Archivematica
*Version actuelle d'Archivematica : 1.9.2 à partir de mai 2019*


Cette page décrit les configurations et les politiques utilisées par Archivematica pendant l'ingestion. Elle comprend :
**LINKS**


## Configuration d'Archivematica au CCA

En plus de prendre en charge les serveurs de fichiers, l'infrastructure Archivematica du CCA fonctionne sur quatre machines virtuelles (VM) :

| VM | Nom | caractéristiques | Matières à ingérer |
| -- | -- | ------------- | ------------------|
| VSP-AMPL-01 | Pipeline 1 | Le pipeline 1 est utilisé pour les archives décrites dans TMS et pour lesquels aucune extraction ou normalisation de format n'est souhaitée. Ce pipeline ne crée pas de copies d'accès dans SCOPE. | Archives non traitées, matériel restreint, matériel qui n'est pas autrement destiné au public | 
| VSP-AMPL-02 | Pipeline 2 | Le pipeline 2 est utilisé pour les archives décrites dans TMS qui feront l’objet d’un traitement par Archivematica. Il devrait être utilisé pour les archives numériques traitées. Un DIP est créé et envoyé à SCOPE. | Archives numériques traitées |
| VSP-AMPL-03 | Pipeline 3 | Le pipeline 3 est utilisé pour les actifs décrits dans Horizon. Il n'existe pas encore de protocole pour l'ingestion de documents provenant de la bibliothèque. L'accès est présumé se faire par la bibliothèque, et aucune copie d'accès n'est envoyée à SCOPE. Les copies d'accès sont temporairement stockées à \SVRDATA\ResearchMaterial$\01 - Library Access Copies. | Matériel de bibliothèque (à déterminer) |
| VSP-AMSS-01 | Storage Service | Le service de stockage gère le stockage, l'indexation et la récupération des Archival Information Packages (AIP) et effectue des contrôles de stabilité de la bibliothèque de AIP. | (pas de pipeline, pas d'ingestion) |


## Les workflows d’ingestion Archivematica
Au CCA, il existe deux méthodes principales pour ingérer des données dans Archivematica : à l'aide [d'outils d'automatisation](https://github.com/artefactual/automation-tools) ou manuellement, par le biais du tableau de bord Web d'Archivematica.


Lorsque cela sera possible, nous favorisons l’utilisation des outils d'automatisation, car ils permettent une récupération automatisée et efficace des métadonnées de TMS (et peut-être, éventuellement, d'Horizon).


**REMARQUE : Comme nous voulons que nos AIP soient complets et autodescriptifs, la description archivistique doit être complète et saisie dans TMS pour tous les fichiers/SIP avant d'être ingérée dans Archivematica.**




### Outils d'automatisation
Des outils d'automatisation sont actuellement mis en place sur les pipelines 1 et 2. Sur ces derniers, Automation Tools vérifie le répertoire /mnt/incoming/auto-transfers toutes les 5 minutes. Il s’assure d’abord que rien n'est en cours de transfert ou ingéré et exécute ensuite des scripts de pré-transfert (qui vérifient que le transfert soit du bon type, transmettent le numéro d'accès du transfert à Archivematica et ajoutent des métadonnées au transfert en utilisant l'API TMS). Finalement, Automation Tools lance le transfert suivant. Le reste du processus de transfert et d'ingestion est automatisé.


Il revient à l'archiviste qui traite les documents numériques de s’assurer de la qualité des résultats de ce processus et de veiller à ce que tous les processus soient menés à terme, tout en respectant le cadre des paramètres acceptables pour la réussite.


#### Procédure d'ingestion des outils d'automatisation : archives numériques
Voici la procédure à suivre pour effectuer l'ingestion des SIP traités avec les outils d'automatisation :


1. Vérifiez que tous les éléments suivants soient vrais :
   1. Vos SIPs traités sont prêts dans /mnt/1TB_RAID sur une des machines BitCurator
   2. Tous les SIP sont nommés avec le schéma [identifiant]---[numéro d'adhésion]. Si les SIP sont constitués de matériel non traité, une image disque par exemple, n'utilisez que son identifiant pour le nommer. L’accès à l'API TMS ne fonctionnera pas s'il n'y a pas exactement trois tirets entre l'identifiant et le numéro d'accès.
   3. La saisie des données pour tous les SIP a été effectuée dans TMS
   4. La description au niveau de la collection est inscrite dans le champ d'application (si elle n'existe pas déjà).
2. Copiez les SIP dans la source de transfert de la pipeline 2 en utilisant le script `"send_to_archivematica.py" avec l'option "--pipeline 2" : python3 /path/to/send_to_archivematica.py --pipeline 2 '/path/to/transfer'`
3. Prévenez l'archiviste numérique que vos SIPs sont prêts à être ingérés.
4. Lorsque le pipeline est libre, l'archiviste numérique déplacera les SIP dans le dossier surveillé Automation Tools pour les ingérer par lots de <50 SIP à la fois. Archivematica ingérera ensuite chacun des SIP, un à la fois.
5. Faire le contrôle de la qualité des données ingérées, en marquant toutes les informations dans une [feuille de calcul Excel dédiée à Archivematica](https://github.com/CCA-Public/digital-archives-manual/blob/master/forms/amatica_ingest_spreadsheet.xlsx) :
   1. Pour chaque SIP, il est nécessaire de s'assurer que le transfert et l'ingestion aient été effectués avec succès et que l'AIP soit stocké. Pour ce faire, cliquez sur "Archival storage" en haut de la page d'Archivematica, et assurez-vous que tous vos SIP y soient. S'ils sont répertoriés, c'est qu'ils ont été achevés avec succès.
   2. Pour chaque SIP, ajoutez les informations suivantes à votre feuille de calcul Excel Ingest :
      1. Identifiant
      2. Adhésion
      3. Numéro du fonds
      4. Pipeline (VSP-AMPL-01 ou VSP-AMPL-02 ou VSP-AMPL-03)
      5. Ingestion réussie ? (Vrai/Faux)
      6. Notes
      7. AIP UUID
      8. AQ standard (Vrai/Faux)
   3. Connectez-vous ensuite à SCOPE et assurez-vous que le nombre prévu de SIP est présent. Cochez "Orphan Folders" si des SIP manquent dans la collection. Si certains SIP ne sont pas présents du tout, informez l'archiviste numérique de ce qui manque, et il les mettra en file d'attente pour les ré-ingérer.
   4. Pour chaque cinquième SIP, effectuez un contrôle de la qualité plus complet. Vérifiez les critères suivants et si ils sont remplis, inscrivez "True" dans la colonne "Full QA" du tableau "Ingest" :
      1. Examinez le rapport de normalisation et assurez-vous qu'aucune normalisation de fichier pour la préservation n'ait échoué.
      2. Connectez-vous à SCOPE et assurez-vous que les métadonnées du Dublin Core, au niveau du dossier, ainsi que les métadonnées supplémentaires au niveau du fichier soient présentes.
   5. Vous avez peut-être aussi reçu, par courriel, un certain nombre de rapports d'échec de normalisation d'Archivematica pendant l'ingestion. Dans les cas où les fichiers défaillants ont des codes de sortie 0 ou 2, ceux-ci peuvent être ignorés. Dans les cas où les fichiers en échec ont le code de sortie 1, il est utile de confirmer que le type de fichier est effectivement normalisé au niveau du CCA ; si c'est le cas, il peut être utile d'approfondir la question, car ces fichiers peuvent avoir besoin d'être [normalisés manuellement](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/arrangement.md#mannorm) pour être ensuite ré-ingérés.
6. Lorsque l'ingestion et le contrôle qualité sont terminées : * Informez et envoyez une copie de votre feuille de calcul Excel d'ingestion à l'archiviste numérique
   1. Sauvegardez votre feuille de calcul Excel d'ingestion dans le dossier "Acquisition et traitement"
   2. Supprimez la copie locale des SIP de la machine BitCurator et de tout autre endroit où vous pourriez avoir des copies du matériel
7. Créez un paquet d'objets pour les fichiers dans TMS correspondant aux SIP. Envoyez ensuite un courriel à Déplacement pour demander que chacun des fichiers du paquet d'objets soit localisé avec l'emplacement "Dark archive", CCing the Digital Archivist.
8. L'archiviste numérique supprimera les SIP ingérés avec succès dans `/mnt/incoming/auto-transfers` (dans le pipeline 1, le script transfer.py a été modifié pour supprimer automatiquement la source de transfert après une ingestion réussie, mais il est toujours nécessaire de supprimer manuellement les sources de transfert des pipelines 2 et 3).


#### Procédure d'ingestion des outils d'automatisation : A/V numérisé
Procédures à venir.


### Utilisation de l'interface utilisateur d'Archivematica Web
Les transferts de collections d’archives vers Archivematica peuvent également être lancés et contrôlés à partir du tableau de bord Web. Avant de commencer, vérifiez que le type de transfert sélectionné s’applique correctement au matériel que vous souhaitez ingérez. Modifiez ensuite la configuration de traitement de manière à ce qu'elle mette le processus en pause lorsque des métadonnées doivent être saisies. Vous devrez saisir manuellement les métadonnées selon le schéma décrit dans la section [Ajout de métadonnées descriptives à l'AIP](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/ingest.md#dcmetadata).


*Ne le faites pas sans consulter au préalable l'archiviste numérique, car cette méthode peut entraîner la perte des métadonnées nécessaires.*


Lorsque vos SIP traités sont prêts dans `/mnt/1TB_RAID` sur l'une des machines BitCurator, que tous les SIP sont nommés avec le schéma [identifiant]---[numéro d'accès], et la saisie des données pour tous les SIP a été effectuée dans TMS, informez l'archiviste numérique du fait que vous êtes prêt à passer à la phase d'Ingestion du projet. Copiez ensuite les SIP dans /mnt/incoming/transfers sur le pipeline approprié en utilisant le script `send_to_archivematica.py`. Si les SIP sont constitués de matériel non traité, une image disque par exemple, n'utilisez que son identifiant pour le nommer.


## Configurations de traitement d'Archivematica
### Configuration pour l'ingestion de données "brutes" (Pipeline 1 par défaut)
| VM | Nom | Caractéristiques | Matières à ingérer |
| -------- | -------- | -------- | -------- |
| VSP-AMPL-01 | Pipeline 1 | Le pipeline 1 est utilisé pour les biens qui sont décrits dans le TMS et pour lesquels aucune extraction ou normalisation de format n'est souhaitée. Ce pipeline ne crée pas de copies d'accès dans SCOPE. | Archives non traitées, matériel restreint, matériel qui n'est pas autrement destiné au public  |
| VSP-AMPL-02 | Pipeline 2 | Le pipeline 2 est utilisé pour les biens qui sont décrits dans le TMS et qui seront entièrement traités par Archivematica. C'est ce pipeline qui devrait être utilisé pour les archives numériques traitées. Un DIP est créé et envoyé à SCOPE. | Archives numériques traitées |
| VSP-AMPL-03 | Pipeline 3 | Le pipeline 3 est utilisé pour les actifs qui sont décrits dans Horizon. Il n'existe pas encore de protocole pour l'ingestion de documents de bibliothèque. L'accès est présumé se faire par la bibliothèque, et aucune copie d'accès n'est envoyée à SCOPE. Les copies d'accès sont temporairement stockées à \\SVRDATA\ResearchMaterial$\01 - Library Access Copies. | Matériel de bibliothèque (à déterminer) |
| VSP-AMSS-01 | Service de stockage | Le service de stockage gère le stockage, l'indexation et la récupération des Archival Information Packages (AIP) et effectue des contrôles de fixité du magasin AIP. | (pas un pipeline, pas d'ingestion) |


*Remarque : chaque bibliothèque AIP Store possède une capacité de 5 To. Ces emplacements sont remplis de manière séquentielle. Pour faciliter l'intégration avec les outils d'automatisation, chaque bibliothèque AIP ne doit être utilisé que pour un seul d'entre eux : les AIP pour lesquels des DIP sont générés, ou les AIP sans DIP correspondant.*


### Configuration pour l'ingestion de données "traitées" (par défaut Pipeline 2)
| Type | Valeur |
| -------- | -------- |
| Attribuer des UUID aux annuaires | "None" |
| Envoyer le transfert en quarantaine | "No" |
| Sortir de la quarantaine après | n/a (toute réponse peut être apportée ici) |
| Générer un rapport sur la structure des transferts | "Yes" |
| Effectuer l'identification du format de fichier (transfert) | "None" |
| Paquets d'extraits | "No" |
| Supprimer les paquets après extraction |  n/a (toute réponse peut être apportée ici) |
| Effectuer des contrôles politiques sur les originaux | "None" |
| Examiner le contenu | "Skip examine contents" |
| Créer SIP(s) | "Create single SIP and continue processing" |
| Effectuer l'identification du format de fichier (Ingest) | "No, use existing data" |
| Normaliser | "Do not normalize" |
| Approuver la normalisation | "Yes" |
| Générer des vignettes | "None" |
| Effectuer des contrôles de politique sur les dérivés de conservation | "None" |
| Effectuer des contrôles de politique sur les produits dérivés d'accès | "None" |
| Lier PIDs | "None" |
| Documenter les annuaires vides | "None" |
| Rappel : ajoutez des métadonnées si vous le souhaitez | "Continue" |
| Transcrire les fichiers (OCR) | "No" |
| Effectuer l'identification du format de fichier (documentation de la soumission et métadonnées) | "None" |
| Sélectionner l'algorithme de compression | "Uncompressed" |
| Sélectionner le niveau de compression | n/a (any answer can be put here) |
| Garder AIP | "Yes" |
| Garder location d'AIP | *appropriate AIP store* |
| Télécharger DIP | "Do not upload DIP" |
| Garder DIP | "Do not store" |
| Garder location du DIP | "None" | 




*Remarque : le CCA crée des DIP à partir de nos AIP par le biais du script [create_dip.py](https://github.com/artefactual/automation-tools/blob/master/aips/create_dip.py) plutôt que par l'option standard "Normalisation pour l'accès" d'Archivematica.*


### Configuration pour la ré-ingestion
*Remarque : Sauvegardé en tant que configuration de traitement "reingest" sur les pipelines.Ceux-ci n'ont pas été revus depuis la mise à jour de la version d'Archivematica de mai 2019.*


| Type | Valeur |
| -------- | -------- |
| Envoyer le transfert en quarantaine | "Non" |
| Approuver la normalisation | "Oui" |
| Garder AIP | "Oui" |
| Transcrire les fichiers (OCR) | "No" |
| Générer un rapport sur la structure des transferts | "Oui" |
| Sortir de la quarantaine après | n/a |
| Créer SIP(s) | "Create single SIP and continue processing" |
| Paquets d'extraits | "Oui" |
| Normaliser | "Normalize for preservation" |
| Rappel : ajoutez des métadonnées si vous le souhaitez | "Continue" |
| Examiner les contenus | "Skip examine contents" |
| Commande d'identification du format de fichier (Transfert) | "Siegfried" |
| Commande d'identification du format de fichier(Ingestion) | "Siegfried" |
| Commande d'identification du format de fichier(Documents de soumission et métadonnées) | "Siegfried" |
| Supprimer les paquets après extraction | "Oui" |
| Sélectionner l'algorithme de compression | "Uncompressed" |
| Sélectionner le niveau de compression | "5 - normal compression mode" |
| Garder AIP | "Oui" |
| Garder emplacement d'AIP | *emplacement AIP approprié* |
| Garder l'emplacement du DIP | "None" |  


### Configuration pour la ré-installation des métadonnées uniquement
* Remarque : Sauvegardé en tant que configuration de traitement "update_metadata" sur les pipelines. Ceux-ci n'ont pas été revus depuis la mise à jour de la version d'Archivematica de mai 2019.*
| Type | Valeur |
| -------- | -------- |
| Envoyer le transfert en quarantaine | "Non" |
| Approuver la normalisation | "Oui" |
| Garder AIP | "Oui" |
| Transcrire les fichiers (OCR) | "No" |
| Générer un rapport sur la structure des transferts | "Oui" |
| Sortir de la quarantaine après | n/a |
| Créer SIP(s) | "Create single SIP and continue processing" |
| Paquets d'extraits | "Oui" |
| Normaliser | "Normalize for preservation" |
| Rappel : ajoutez des métadonnées si vous le souhaitez | "None" |
| Examiner les contenus | "Skip examine contents" |
| Commande d'identification du format de fichier (Transfert) | "Siegfried" |
| Commande d'identification du format de fichier(Ingestion) | "Siegfried" |
| Commande d'identification du format de fichier(Documents de soumission et métadonnées) | "Siegfried" |
| Supprimer les paquets après extraction | "Oui" |
| Sélectionner l'algorithme de compression | "Uncompressed" |
| Sélectionner le niveau de compression | "5 - normal compression mode" |
| Garder AIP | "Oui" |
| Garder emplacement d'AIP | *emplacement AIP approprié* |
| Garder l'emplacement du DIP | "None" |  




## Ajout de métadonnées descriptives à l'AIP
Le CCA ajoute des métadonnées descriptives pour chaque AIP afin de faciliter la découverte et la réutilisation des données. Dans la plupart des cas, les métadonnées seront saisies automatiquement au cours du processus d'ingestion à l'aide des [outils d'automatisation](https://github.com/artefactual/automation-tools) et de [add-tms-metadata.py](https://github.com/CCA-Public/cca-scripts/blob/master/archivematica/add_tms_metadata.py). Le script add-tms-metadata.py récupère les métadonnées à l'aide d'une API TMS minimale GET uniquement. Cette fonction a été mise en œuvre par un ancien programmeur du CCA sur la base de travaux similaires réalisés en open source par le MoMA. Pour récupérer certaines métadonnées de base (avec des champs limités) pour un enregistrement dans TMS, faites un appel à l'API GET à http://api.tms.cca.qc.ca/API/Object/<enter ObjectNumber ici>. Par exemple, les informations relatives à l'enregistrement au niveau du fonds pour les enregistrements du projet Testa & Weiser (AP174) peuvent être consultées à l'adresse [http://api.tms.cca.qc.ca/API/Object/AP174](http://api.tms.cca.qc.ca/API/Object/AP174).


Les normes locales du CCA pour la saisie des métadonnées sont les suivantes :
| Champ | Valeur |  
| ----- | ----- |  
| Titre | Titre |  
| Partie de l'AIC | Identifiant de l'AIC (le cas échéant) |  
| Creator | Créateur de l'archive (doit être le même que celui qui constitue TMS) |  
| Sujet | n/a |  
| Description | Note sur le champ d'application et le contenu (optionnel) |  
| Éditeur | Centre Canadien d'Architecture |  
| Contributeur | n/a |  
| Date | Suivez les normes ISO8601. Valeurs autorisées : AAAA, AAAA-MM, AAAA-MM-JJ, AAAA/AAAA, AAAA-MM/AAAA-MM, AAAA-MM-JJ/AAAA-MM-JJ |  
| Format | Déclaration sur l'étendue et le support - e.g. "10 digital files (25 MB)" |  
| Identifiant | Identifiant du matériel ingéré |  
| Source | Numéro d'adhésion (par exemple, versement) -- pour les ingestions "brutes", laissez ce champ vide |  
| Relation | Numéro du fonds (AP###) -- pour les ingestions "brutes", laissez ce champ vide |  
| Langue | n/a |  
| Couverture | n/a |  
| Droits | n/a |  




## Politiques relatives au format de fichier CCA
Version actuelle : [Format Policy Registry, version 2](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/CCA%20Format%20Policy%20Registry%20v2%20201804.pdf)
