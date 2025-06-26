# Capturer les archives du Web à l'aide d'Archive-It
L'archivage web est la pratique qui consiste à utiliser des outils de capture pour explorer des sites web et sauvegarder leur contenu. Il en résulte des fichiers d'archivage web (WARC), un fichier conteneur qui contient le script, les médias et les autres éléments d'un site web. Les fichiers WARC sont le format de préservation des sites web et peuvent être lus pour afficher le site web tel qu'il apparaissait sur le web en direct, au moment de la capture.


Le CCA utilise l'application web [Archive-It](https://archive-it.org/) pour capturer certains types de contenu web liés à nos intérêts de collecte. Les collections web sont accessibles via le [microsite du CCA](https://archive-it.org/home/Canadian-Centre-for-Architecture). Les métadonnées sont contrôlées localement, et la lecture se fait par l'intermédiaire de la [Wayback Machine](https://archive.org/web/).


Archive-It dispose d'un [centre d'aide](https://support.archive-it.org/hc/en-us), [d'un guide de l'utilisateur](https://support.archive-it.org/hc/en-us/articles/360041250172-Guide-for-new-Archive-It-users) et d'un [forum](https://support.archive-it.org/hc/en-us/community/topics), qui devraient servir de documentation principale et de ressource pour le dépannage.
## Workflow
1. Consultez la liste des seeds de l'archivage web pour voir quelles seeds doivent être capturés. Il vit ici : H:\Archives\Archives numériques\Systems Development\Web Archiving.
2. [Définissez des règles de cadrage et effectuez des tests et des captures de production.](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/web.md#scoping)
   1. [Utiliser WebRecorder pour capturer du contenu dynamique](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/web.md#webrecorder).
3. [Réaliser l'AQ](https://support.archive-it.org/hc/en-us/sections/115000624306-Quality-Assurance-QA-)
4. [Ajoutez des métadonnées à chaque seed](https://github.com/CCA-Public/digital-archives-manual/blob/master/guides/web.md#metadata).
5. Mettre à jour le journal de captures pour refléter chaque capture SAUVÉ. Il se trouve dans le même dossier que l'étape 1.
## La recherche et la réalisation de captures
Ajoutez un seed à une collection et définissez sa portée en utilisant les [directives d'Archive-It](https://support.archive-it.org/hc/en-us/sections/201864583-Scoping). Notez que les sites de médias sociaux, tels que Facebook, Instagram et Youtube, nécessitent des [règles spécifiques de cadrage](https://support.archive-it.org/hc/en-us/articles/208001336-Scoping-guidance-for-specific-types-of-sites).


Notez que chaque fois que vous ajoutez un nouveau seed, vous DEVEZ effectuer un [test de capture](https://support.archive-it.org/hc/en-us/articles/208001226-Run-monitor-and-save-a-test-crawl). Cela garantit que la capture finale, enregistrée dans l'archive, est correctement dimensionné. Les captures de production ne peuvent pas être supprimés, ce qui signifie qu'une capture mal dimensionné peut absorber une grande partie du budget de données. Il est toutefois possible de sauvegarder les essais, ce qui constitue le point de départ idéal, en particulier pour les seeds qui sont testées pour la première fois.


Une capture peu profonde est programmée pour les sites web du CCA (français/anglais) chaque semaine. Il est également recommandé d'effectuer un test complet tous les trimestres, mais il doit être lancé manuellement. Au moment de la rédaction du présent document, tous les autres seeds sont programmées pour une capture unique.


### Utiliser le WebRecorder pour capturer du contenu dynamique
Un [problème connu](https://support.archive-it.org/hc/en-us/articles/209637043-Known-Web-Archiving-Challenges#dynamic) avec Archive-It est la capture de contenu dynamique, c'est-à-dire de contenu qui nécessite une interaction humaine pour être rendu correctement. Cela inclut Flash, utilisé par plusieurs sites d'expositions antérieures du CCA. Dans les cas où le contenu ne peut pas être capturé par Archive-It, on utilisera [WebRecorder](https://webrecorder.io/).


Suivez les instructions du [guide d'utilisation](https://guide.webrecorder.io/) de WebRecorder pour créer et télécharger un fichier WARC du site web souhaité. Téléchargez-le dans Archive-It en suivant les instructions [ici](https://support.archive-it.org/hc/en-us/articles/360000651246-Integrate-external-W-ARC-files-into-Archive-It-collections).
## Métadonnées
La description devrait se trouver à trois endroits : les métadonnées de niveau seed devraient se trouver dans Archive-It et dans le catalogue de la bibliothèque du CCA, et les métadonnées de niveau "fonds" devraient se trouver dans TMS.


Description d'Archive-It
Les métadonnées peuvent être ajoutées à des seeds individuelles en cliquant sur l'URL d'une seed et en naviguant vers l'onglet "Métadonnées". Cliquez sur "Modifier" pour commencer à saisir les métadonnées dans les champs ; vous devez cliquer sur "Ajouter" pour enregistrer les modifications. Les champs suivants sont obligatoires pour tous les seeds :


* **Titre** : Utilisez la fonction "Saisir le titre" lorsque c'est possible. N'hésitez pas à modifier les résultats de la fonction "Grab title" s'ils sont particulièrement longs ou ne représentent pas un titre approprié. Si la fonction "Attraper le titre" ne fonctionne pas pour un seed particulier, générez le titre du site web en utilisant votre meilleur jugement.
* **Créateur** : L'organisation ou la personne responsable de la création du contenu d'un site web.
* **Contributeur** : Comprend tout contributeur "significatif mais secondaire" à une ressource non couverte par d'autres domaines.
* **Date** : Valeurs de l'année liées au site web. Il s'agit au minimum de l'année de la capture, et peut également inclure les dates d'exposition. Chaque année doit être saisie séparément et mise en contexte. Exemples : -2012-2016 (publié) 2013-2014 (dates d'exposition) 2018 (capturé) - capturé 2018
* **Tapez** : Il s'agira toujours d'"archives web" pour les contenus archivés (c'est-à-dire les captures ponctuelles) et de "sites web" pour les sites vivants (c'est-à-dire les captures continues et programmées).
* **Format** : Saisie dans le champ "Format". Il s'agira toujours de "1 site web archivé".
* **Relation (obligatoire le cas échéant)** : Si le site web se rapporte à un autre fonds d'archives du CCA, indiquez le titre du fonds avec un lien vers l'instrument de recherche.
* **Source** : Il s'agira toujours de "Description basée sur la page web archivée saisie (date de saisie)". Dernière mise à jour (date)".
* **Collectionneur** : Il s'agira toujours de "Centre canadien d'architecture".
* **Langue** : Langue(s) principale(s) représentée(s) sur un site web. Chaque langue doit être saisie séparément (par exemple, "anglais", "français", et non "anglais et français").


Les champs suivants sont facultatifs :


* **Sujets (recommandé)** : 1-3 sujets liés au site web disponibles dans [searchFAST](http://fast.oclc.org/searchfast/), y compris le créateur. Bien que l'analyse des sujets soit généralement en dehors de la description archivistique typique du CCA, elle rendra nos seeds plus facilement accessibles dans les environnements Archive-It et Wayback.
* **Description (recommandée)** : Un résumé de 3 à 5 phrases du contenu du site web. Ce résumé peut être copié et collé directement à partir de la page "À propos" du site (ou similaire). Il est également recommandé d'inclure des informations sur la provenance (c'est-à-dire la raison pour laquelle un site particulier a été choisi pour la capture) le cas échéant.
* **L'éditeur (si nécessaire)** : À n'utiliser que si l'éditeur diffère du créateur.
* **Couverture (recommandée)** : Un nom de lieu disponible dans searchFAST.


Tous les autres champs ne sont pas utilisés.
### Description du catalogue
Il doit y avoir un enregistrement dans le catalogue de la bibliothèque pour chaque seed. Ceux-ci correspondront exactement aux descriptions dans Archive-It ; [voir les métadonnées descriptives d'OCLC pour l'archivage Web](https://www.oclc.org/content/dam/research/publications/2018/oclcresearch-wam-recommendations.pdf) pour un tableau de concordance MARC-Archive-It. L'accès sera possible grâce à l'URL de la page d'accueil de chaque seed ([par exemple](https://wayback.archive-it.org/10908/*/http://we-aggregate.org/)).


Une fois par mois, envoyez au catalogueur (Mary) un document Excel contenant les nouveaux seeds à cataloguer. Les seeds dont les captures sont récurrentes et programmées ne doivent être mises à jour qu'après la première capture d'une nouvelle année pour refléter la nouvelle date.
### Description de TMS et son ingestion dans Archivematica
A la fin de chaque période d'abonnement à Archive-It, le CCA accédera à un disque dur de toutes les ARM capturées au cours de cette année. Il faudra créer un dossier au niveau du fonds et les acquisitions devront y être intégrées. Les normes de métadonnées appropriées doivent suivre les [OCLC Descriptive Metadata for Web Archiving](https://www.oclc.org/content/dam/research/publications/2018/oclcresearch-wam-recommendations.pdf) et seront développées au moment de la première acquisition. Une fois les métadonnées TMS terminées, les CAMR doivent être ingérées dans Archivematica.
