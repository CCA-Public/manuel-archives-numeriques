# L'administration d'Archivematica

* [Connexion](#connexion)
* [Commencer une ingestion](#ingestion)
* [Surveillance des serveurs d'Archivematica](#surveillance)
* [Vérification et réparation des réparations](#verification)
* [L'abandon des données MySQL et ES dans les pipelines](#abandon)
* [Suppression des AIP](#suppression)
* [Nettoyage après l'ingestion réussie d'outils d'automatisation](#nettoyage)
* [Réagir aux échecs des outils d'automatisation](#reagir)
* [Ajout et changement d'emplacement des AIP Store](#aip_store)
* [Mise à jour de la configuration de traitement des outils d'automatisation](#miseajour)
* [Libérer de l'espace lorsque le disque local est presque plein](#liberer)
* [Redémarrage des services](#redemarrage)
* [Rapport des modifications apportées au FPR par défaut d'Archivematica](#modifications)
* [Paramètres personnalisés d'Archivematica](#parametres)
* [Mises à jour d'Archivematica et dépendances](#dependances)

<a name="connexion"></a>
## Connexion
Pour se connecter aux serveurs d'Archivematica,  les administrateurs doivent demander aux services informatique du CCA de leur ouvrir un compte. La commande pour accéder au serveur est ssh `user@172.17.50.71` où `utilisateur` est votre nom d'utilisateur et la suite de chiffres correspond à l'URL du pipeline ou du service de stockage. Entrez ensuite votre mot de passe lorsque vous y êtes invité.


Pour vous déconnecter, utilisez `Ctrl+D`.

<a name="ingestion"></a>
## Commencer une ingestion
Confirmer avez les archivistes du traitement numérique pour vous assurer qu’ils ont bien téléchargé leurs SIP dans la filière appropriée. Une fois connecté au serveur pour ce pipeline, faites-le :


```
cd /mnt/incoming/transfers/UPLOADED_SIP_FOLDER
sudo mv * /mnt/incoming/auto-transfers/
```


Les SIP sont ainsi déplacés dans un dossier surveillé. Archivematica commencera à ingérer ces SIP à la prochaine intervalle de cinq minutes. Confirmez ensuite que le dossier est vide en utilisant la commande `ls`. Ensuite, supprimez le dossier vide :


```
cd ..
rm -rf /UPLOADED_SIP_FOLDER/
```

<a name="surveillance"></a>
## Surveillance des serveurs d'Archivematica
[Surveillance des serveurs](https://vsp-prtg-01.int.cca/public/mapshow.htm?id=2636&mapid=archivematica)

<a name="verification"></a>
## Vérification et réparation des réparations
Les vérifications de la stabilité de tous les PIA sont effectuées sur une base trimestrielle à l'aide de l'application [Fixity](https://github.com/artefactual/fixity). La fonction `scanall` de Fixity est exécutée via les scripts cca-fixity installés dans `/var/archivematica/cca-fixity` sur la Machine Virtuelle (VM) du service de stockage. Elle est appelée automatiquement le deuxième vendredi des mois de janvier, avril, juillet et octobre, via la crontab. Les rapports sont enregistrés sur le serveur du service de stockage d'Archivematica à l'adresse `/var/log/cca-fixity` et les résultats sont envoyés par courriel aux administrateurs concernés.


Pour effectuer manuellement un contrôle de stabilité d'une seule AIP :


1. Connectez-vous à VSP-AMSS-01
2. Charger les variables environnementales : `source /etc/profile.d/fixity.sh`
3. Exécution de la fonction fixity scan : `fixity scan <AIP UUID>`


Si vous devez effectuer un contrôle de stabilité scanall manuellement, utilisez [nohup](https://en.wikipedia.org/wiki/Nohup) pour vous assurer que le processus se déroule complètement en arrière-plan, même si votre session de terminal se termine


1. Se connecter à VSP-AMSS-01
2. Charger les variables environnementales : `source /etc/profile.d/fixity.sh`
3. Exécution de la fonction fixity scanall : `nohup fixity scanall &`


Lorsque la corruption d’un AIP est détectée, il faut en informer le service informatique et restaurer l'AIP à partir des sauvegardes, conformément aux procédures de [récupération](https://www.archivematica.org/en/docs/storage-service-0.10/recovery/#recovery) du service de stockage.

<a name="abondon"></a>
## L'abandon des données MySQL et ES dans les pipelines
Nous supprimerons périodiquement les index et les lignes Elasticsearch des bases de données MySQL sur chacun des pipelines de traitement afin de minimiser l'épuisement des ressources et de maintenir l’efficacité de ces derniers. Cette opération devrait être fait tous les quelques mois et seulement une fois toutes les ingestions soumises avec succès à un contrôle de qualité.


Il a été demandé à Artefactual Support de créer un devis pour un script permettant de faire ce nettoyage pour les bases de données MySQL en pipeline.


Pour déposer l'index ES sur un pipeline :


`curl -XDELETE http://<pipeline.ip.address>:9200/aips`


Lorsque l'index ES est supprimé, les sauvegardes et les journaux de `/srv/am-est-backups` et de`/var/log/elasticsearch` peuvent également être supprimés. Cela permettra d'économiser de l'espace sur le disque local.
## Réindexation des index de stockage des archives AIP
Pour ré-indexer un AIP dans un index de stockage sur un pipeline donné, vous pouvez utiliser les scripts `rebuild-aip-index.py` et `reindex-aip.sh` du dossier Archivematica des [scripts CCA repo](https://github.com/CCA-Public/cca-scripts/tree/master/archivematica) sur le pipeline où vous souhaitez que les AIP soient ré-indexés.


Le script bash `reindex-aip.sh` réindexe un AIP à l'aide des [outils de développement d'Archivematica](https://github.com/artefactual/archivematica-devtools).


Le script Python `rebuild-aip-index.py` vous permet de spécifier les UUIDs des AIP que vous souhaitez indexer en les ajoutant sous forme de suite de caractères à la liste "aip_list", puis appelle `reindex-aip.sh` pour chacun des AIP.


Avant d'utiliser les scripts :


* Clonez le repo `archivematica-devtools` dans votre dossier personnel sur le serveur pipeline
* Modifier les chemins d'accès dans les scripts pour pointer vers les bons emplacements 

<a name="suppression"></a>
## Suppression des AIP
Pour envoyer une demande de suppression pour un AIP indexé sur un pipeline d'Archivematica, [suivez ces instructions](https://www.archivematica.org/en/docs/archivematica-1.7/user-manual/archival-storage/archival-storage/#delete-aip).


Pour envoyer une demande de suppression pour un AIP qui n'est pas actuellement indexé sur un pipeline Archivematica, ssh dans la VM Storage Service, exécutez la commande curl suivante, en remplaçant toutes les valeurs dans < > par les informations appropriées :


```
curl -X POST -H "Content-Type: application/json" -H "Authorization: ApiKey <SS user>:<SS user API key>" -d '{"event_reason":"<reason for deletion>","pipeline":"<UUID to pipeline to send deletion from>","user_id":<integer pipeline user primary key>,"user_email":"<email to send deletion notice to>"}' <SS URL>/api/v2/file/<AIP UUID>/delete_aip/
```
<a name="nettoyage"></a>
## Nettoyage après l'ingestion réussie d'outils d'automatisation
Lorsque les ingestions, entamées via les outils d'automatisation, se terminent avec succès, elles doivent ensuite être supprimées manuellement de la source de transfert (dans ce cas, `/mnt/incoming/auto-transfers/`). Ceci doit être fait par un utilisateur qui possède les permissions `sudo`, par exemple `sudo rm -rf /path/to/transfer/`. **Faites attention lorsque vous supprimez des fichiers à l’aide de la commande sudo, car il est très facile de supprimer accidentellement des fichiers que vous n'aviez pas l'intention de supprimer**.


Tim a écrit un script pour le dépôt Automation Tools qui supprime automatiquement les fichiers sources de transfert après une ingestion réussie si le script `transfer-script.sh` est exécuté avec un drapeau `--delete`. Ce script est actuellement [en cours de révision](https://github.com/artefactual/automation-tools/pull/44) - si la demande d'extraction est acceptée et fusionnée, il ne sera plus nécessaire de procéder à un nettoyage manuel après une ingestion réussie des Automation Tools.

<a name="reagir"></a>
## Réagir aux échecs des outils d'automatisation
Lorsqu'une ingestion, lancée via les outils d'automatisation échoue, la première chose à faire est de déterminer pourquoi l'ingestion a échoué. Il faut ensuite soit corriger le transfert ou soumettre un ticket de support avec Artefactual.


Lorsque vous êtes prêt à relancer le transfert/ingestion, après avoir corrigé le problème, vous remarquerez que le simple fait de mettre le transfert dans le dossier surveillé ne fonctionnera pas. Cela est dû au fait que la base de données SQLite `transfers.db`, utilisée par les outils d'automatisation pour garder une trace des transferts déjà été lancés, inclura le transfert (reconnu en fonction du nom du dossier), l'empêchant ainsi d'être lancé.


La solution consiste donc à supprimer la base de données `transfers.db` et à relancer manuellement le `transfer-script.sh` avec les autorisations sudo :


* `sudo rm -f /var/archivematica/automation-tools/transfers.db`
* `sudo -u archivematica /etc/archivematica/automation-tools/transfer-script.sh`


Vous ne devez appeler manuellement `transfer-script.sh` qu'une seule fois - après cela, la crontab appellera le script toutes les 5 minutes, selon les instructions d'installation recommandées.


**Notez que la suppression de `transfers.db` signifie que les outils d'automatisation n'auront plus d'enregistrement des transferts déjà lancés dans le répertoire `/mnt/incoming/auto-transfers`, vous devrez donc vous assurer que seuls les transferts que vous avez l'intention de lancer sont présents dans ce répertoire avant de supprimer la base de données.**
## Vérification des rapports provenant des outils d'automatisation
Si vous rencontrez un comportement inattendu de la part des outils d'automatisation (par exemple, si des transferts ne démarrent pas ou ne sont pas approuvés, si des DIP ne sont pas créés pour de nouveaux AIP), il faut d’abord les rapports provenant de ces outils.


Rapports pertinents :


* Transferts des outils d'automatisation : `/var/log/archivematica/automation-tools/transfers.log`
* Créer un emploi DIP : `/var/log/archivematica/automation-tools/create-dip-jobs.log`

[name="aip_store"></a> 
## Ajout et changement d'emplacement des AIP Store
Chaque emplacement de stockage configuré dans le service de stockage d’Archivematica, possède une taille de 5 To (ceci a été mis en place afin de faciliter les sauvegardes pour l'informatique). Au fur et à mesure du remplissage de ces espaces de stockage, de nouveaux emplacements devront être ajoutés et remplacés comme valeurs par défaut pour les pipelines. **Les emplacements ne devraient contenir que des AIP pour lesquels il existe des DIP (par exemple, des archives numériques traitées) ou des AIP pour lesquels il n’existe pas de DIP (par exemple, des masters de numérisation). Ces deux types de AIP ne peuvent être combinés.**


Étapes pour commencer à utiliser un nouvel emplacement du AIP Store :

1. S'assurer que le répertoire à ajouter est monté sur la Machine Virtuelle (VM) du service de stockage (lecture/écriture) et les VM en pipeline (lecture seule). Demandez à l'administrateur système du CCA de configurer le tout si ce n'est pas le cas.
2. Configurez un espace et un emplacement de stockage AIP dans l'interface graphique du service de stockage (ou demandez au support Artefactual de le faire pour vous).
3. Définissez un nouvel emplacement de stockage AIP comme valeur par défaut dans les pipelines appropriés.
4. Remplacez le fichier defaultProcessingMCP.xml, utilisé avec les outils d'automatisation des transferts dans `/opt/archivematica/automation-tools/transfers/pre-transfer/defaultProcessingMCP.xml` par une configuration mise à jour.
5. (Si le nouvel emplacement de stockage contiendra des AIP pour lesquels nous voulons générer des DIP) Modifier la valeur de `--location-uuid` dans `/etc/archivematica/automation-tools/create_dips_job_script.sh` à la valeur du nouvel emplacement de stockage des AIP. S'il est nécessaire de surveiller et de créer des DIP pour plus d'un emplacement de l'AIP Store, créez un deuxième script (par exemple, `create_dips_job_script_1.sh`) et ajoutez ce script supplémentaire à la crontab sous user `archivematica` (pour modifier la crontab, utilisez `sudo crontab -u archivematica -e`).

Ces emplacements AIP Store sont déjà configurés dans le service de stockage d'Archivematica :

| AIP Store | Actuellement en service ? | Configuré avec le script de création DIP d'Automation Tools ? | Notes |
| ----------| :---------------------:   |	:------------------------------------------------------------:| :------:|
| DARK_ARCHIVE_001 | Oui | Oui | Emplacement actuel par défaut de l'AIP Store pour le pipeline 2 (archives numériques traitées) |
| DARK_ARCHIVE_002 | Oui | Non | Emplacement actuel par défaut de l'AIP Store pour le pipeline 1 (accessions et A/V) |
| DARK_ARCHIVE_003 | Non | N/a | N/a |
| DARK_ARCHIVE_004 | Non | N/a | N/a |
| DARK_ARCHIVE_005 | Non | N/a | N/a |

<a name="miseajour"></a>
## Mise à jour de la configuration de traitement des outils d'automatisation
Lors de la mise à jour de la configuration de traitement, allez dans l'onglet "Administration" du tableau de bord du pipeline approprié, sélectionnez la configuration "Par défaut" et ajustez les paramètres si nécessaire. Cliquez ensuite sur "Enregistrer" et téléchargez le fichier de configuration mis à jour à partir de la page suivante.


Celui-ci doit ensuite être placé dans Automation Tools in Archivematica. Envoyez le fichier de configuration vers le pipeline approprié en utilisant le script "send_to_archivematica.py" sur les machines BitCurator. Ensuite, déplacez le fichier de `/mnt/incoming/transfer` vers Automation Tools.

<a name="liberer"></a>
## Libérer de l'espace lorsque le disque local est presque plein
Lorsque l'espace disque local de l'un des pipelines d'Archivematica est presque plein, le service informatique envoie une alerte. Pour libérer de l'espace, vous pouvez supprimer certains rapports ainsi que les anciennes sauvegardes MySQL et Elasticsearch, à savoir


* `/srv/am-db-backups` : Conservez la dernière sauvegarde ; toutes les autres peuvent être supprimées
* `/srv/am-es-backups` : Conservez la dernière sauvegarde (vérifiez la taille du fichier pour vous assurer qu'il s'agit d'une vraie sauvegarde) ; toutes les autres peuvent être supprimées
* `/var/log/elasticsearch` : Supprimer tout rapport datant de plus d'un mois

<a name="redemarrage"></a>
## Redémarrage des services

Pour arrêter les services :
```sudo stop archivematica-mcp-server
sudo stop archivematica-mcp-client
sudo stop archivematica-dashboard
sudo service nginx stop
sudo /etc/init.d/gearman-job-server stop
sudo service mysql stop
sudo /etc/init.d/elasticsearch stop
```
Pour démarrer les services :


```sudo /etc/init.d/elasticsearch start
sudo service mysql start
sudo /etc/init.d/gearman-job-server start
sudo start archivematica-dashboard
sudo service nginx start
sudo start archivematica-mcp-server
sudo start archivematica-mcp-client
```
Pour redémarrer uniquement le serveur/client/tableau de bord d'Archivematica :


`sudo bash -c 'for i in dashboard mcp-client mcp-server; do service archivematica-$i restart; done'`

<a name="modifications"></a>
## Rapport des modifications apportées au FPR par défaut d'Archivematica
* Remplacement de la commande FITS par un script bash pour éviter que les sorties non-XML ne provoquent des erreurs (corrigé dans AM 1.7)
* FITS est un outil de caractérisation pour tous les formats de fichiers -- à noter qu’il est crucial, car il indique une date de dernière modification, indexée pour tous les fichiers ingérés. Voir la [documentation METSFlask](https://github.com/timothyryanwalsh/metsflask#detailed-identification-and-dates) pour plus de détails sur la façon d'assurer la caractérisation FITS pour tous les fichiers dans l'AM 1.6
* Les règles d'extraction pour les images disques RAW, ISO, AFF et E01 sont désactivées afin que les images disques puissent être stockées avec les fichiers (l'extraction des images disques se fait dans BitCurator avant l'ingestion d'Archivematica dans nos flux de travail locaux)
* Remplacement de la commande Ghostscript PDF->PDF/A par un script bash qui empêche les erreurs lorsque les chemins d'accès aux fichiers de sortie ont plus de 255 caractères
* Les règles de normalisation pour Adobe Flash, Macromedia Flash et Generic SWF sont désactivées (par défaut, Archivematica tente de normaliser ces formats pour la vidéo ffv1/Matroska, ce qui échoue presque 100 % du temps)
* Ajout de Libreoffice et de commandes pour le transcodage en docx, odt, xlsx, ods et pptx



<a name="parametres"></a>
## Paramètres personnalisés d'Archivematica
* La valeur de l'option Elasticsearch request_timeout est passée de 10 à 60 secondes
* Le service de stockage sera configuré pour utiliser tous les noyaux disponibles pour la vérification de la stabilité de bagit-python (la valeur par défaut est 1 ; devrait être configurable par l'utilisateur dans SS/0.11)


Artefactual a également documenté des aspects plus atypiques de l'organisation Archivematica du CCA :


* Les outils d'automatisation sont installés dans /usr/lib/archivematica/automation-tools/
* Le script situé dans /etc/archivematica/automation-tools/transfer-script.sh s'exécute toutes les 5 minutes en tant qu'utilisateur système d'archivematica, et utilise l'autobot de l'utilisateur d'Archivematica.
* Le fichier de configuration se trouvant dans /etc/archivematica/automation-tools/transfers.conf définit le fichier rapport et la base de données dans `/var/log/archivematica/automation-tools/` , et le fichier de verrouillage dans `/var/archivematica/automation-tools/transfers-pid.lck`. Ce fichier devra peut-être être supprimé lorsque les outils d'automatisation cesseront de fonctionner.
* Les importations automatisées utilisent le dossier `/mnt/incoming/auto-transfers` comme source de transfert, et les AIP sont stockés dans DARK_ARCHIVE_002 aipstore pour VSP-AMPL1, et DARK_ARCHIVE_001 pour VSP-AMPL2

<a name="dependances"></a>
## Mises à jour d'Archivematica et dépendances
Les mises à jour des versions d'Archivematica doivent être effectuées par Artefactual, et sont incluses dans notre contrat de service avec eux. Cependant, comme Archivematica a un certain nombre de dépendances, l'archiviste numérique doit évaluer la capacité du support informatique local et d'Artefactual avant de procéder à la mise à jour.


Les dépendances qui peuvent affecter le succès des mises à niveau sont les suivantes


* **Les outils d'automatisation sur les machines BitCurator** : Tout changement qui entraîne une modification des clés de sécurité du serveur Archivematica Pipeline entraînera l'échec du script create_dip.sh. Le script doit être mis à jour pour refléter la nouvelle clé.
* **API TMS** : L'API TMS a été affectée par la mise à jour vers la version 2019 d'Archivematica. Plus de détails à venir.
* SCOPE
