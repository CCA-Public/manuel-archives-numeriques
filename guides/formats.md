# Logiciels et formats de fichiers CAO, BIM et modélisation 3D
Formats spécifiques aux fournisseurs et aux logiciels :

* [AutoCAD (.dwg, .dxf, .dwf)](#autocad)
* [Revit (.rvt)](#revit)
* [3DS Max (.3ds, .max)](#3ds)  
* [Rhinoceros (.3dm)](#rhino)  
* [Microstation (.dgn)](#microstation)  
* [Maya (.ma, .mb)](#maya)  
* [Alias (.wire)](#alias)
* [form·Z (.fmz)](#formz)  
* [CATIA (.CATPart, .CATProduct, autres)](#catia)  
* [Digital Project (.CATPart, .CATProduct)](#digitalproject)  
* [SOLIDWORKS (.SLDPRT)](#solidworks)  
* [SketchUp (.skp)](#sketchup)  

Formats neutres vis-à-vis des fournisseurs :

* [STL (.stl)](#stl)  
* [IGES (.iges, .igs)](#iges)  
* [STEP (.step)](#step)  
* [COLLADA (.dae)](#dae)  
* [IFC (.ifc)](#ifc)  

NOTE GÉNÉRALE : CONSULTEZ ÉGALEMENT [NAVISWORKS](https://knowledge.autodesk.com/support/navisworks-products/troubleshooting/caas/sfdcarticles/sfdcarticles/Supported-file-formats-and-applications-for-Autodesk-Navisworks-2009-to-2012.html) EN TANT QUE VISIONNEUSE MULTI-CADRES.



<a name = "autocad"></a>
## AutoCad
**Extensions de fichiers associées** : .dwg, .dxf, .dwf
**Vendeur** : Autodesk


**Résumé**
Lancé en 1982, AutoCAD est l'outil de conception et de dessin assisté par ordinateur en 2D et 3D le plus utilisé au monde (et, depuis 2010, dans le nuage).


**Formats de fichiers associés**
**DWG** : format de fichier binaire natif propriétaire d'AutoCAD. Bien que le DWG soit un format propriétaire, il a fait l'objet d'une ingénierie inverse et est maintenant compatible (à des degrés divers) avec de nombreuses plateformes logicielles autres qu'AutoDesk.


**DXF (Drawing Interchange Format, ou format d'échange de dessins)** : Un format ouvert de transfert de données développé par Autodesk, dont les [spécifications](http://images.autodesk.com/adsk/files/autocad_2012_pdf_dxf-reference_enu.pdf) sont disponibles en ligne. Le DXF existe à la fois sous forme ASCII et binaire. Les fichiers DXF ASCII sont des fichiers texte qui peuvent être lus et modifiés avec n'importe quel éditeur de texte.


**DWF (Design Web Format)** : Un format ouvert de visualisation de données 2D et 3D développé par Autodesk. Les fichiers DWF sont hautement compressés et ne sont pas destinés à remplacer les fichiers de conception originaux.


**Comment visualiser les fichiers sur les postes de travail CAO CCA**
Ces trois types de fichiers peuvent être ouverts avec AutoCAD 2014 (lecture/écriture), DWG TrueView (lecture seule) et Bentley View (lecture seule).


En raison de la popularité de DWG, il peut également être visualisé (moins efficacement) avec un logiciel de format d'image général tel que QuickView Plus.


En général, DWG TrueView est l'outil le plus complet et le plus simple pour visualiser les formats de fichiers AutoCAD standard. Si vous avez besoin d'examiner un fichier via le terminal de commande, utilisez plutôt AutoCAD.


**Sauvegarde (BAK) et enregistrement automatique des fichiers**
"Les fichiers de sauvegarde des dessins sont généralement créés chaque fois que vous enregistrez manuellement un fichier .dwg. Par défaut, le fichier sera enregistré au même endroit que le fichier .dwg et portera le même nom que le dessin, mais avec une extension .bak, par exemple, site_topo.bak. Un fichier de sauvegarde est une copie exacte du fichier du dessin avant la dernière sauvegarde. Les fichiers de sauvegarde sont donc toujours une version plus ancienne que le dessin actuellement sauvegardé. Un seul fichier de sauvegarde est conservé à la fois, de sorte que les sauvegardes nouvellement créées remplaceront toujours les anciennes sauvegardes du même nom.


Note : Les fichiers de sauvegarde ne sont créés que si la variable système ISAVEBACK est définie à 1.


Les fichiers de sauvegarde sont essentiellement des fichiers .dwg renommés. Vous pouvez récupérer des données enregistrées dans des fichiers .bak en renommant l'extension .bak en dwg et en ouvrant ensuite ce fichier dans AutoCAD".


Source : ["Understanding AutoCAD backup and autosave files", Autodesk, 30 janvier 2015](https://knowledge.autodesk.com/support/autocad/troubleshooting/caas/sfdcarticles/sfdcarticles/Understanding-AutoCAD-backup-and-autosave-files.html)


**Caractéristiques à noter**
AutoCAD 2014 est capable de lire toutes les versions des formats de fichiers DWG et d'écrire certains formats DWG plus anciens (R14 et plus récents).


AutoCAD n'a pas été produit pour Mac entre 1994 et 2010.


**Peut importer**
.3ds, .dgn, .dwg, .dws, .dwt, .dxf, .fbx, .sat, .wmf


**Peut exporter**
.3ds, .bmp, .dgb, .dwf, .dwg, .dxf, .fbx, .pdf


**Navigation et utilisation**
Dans AutoCAD, il est possible d'interagir avec le terminal de commande ou l'interface graphique. Les fonctions de navigation de base (telles que le panoramique, le zoom et l'orbite) sont principalement prises en charge par la barre de navigation.

<a name="revit"></a>
## Revit
**Extensions de fichiers associées** : .rvt
**Vendeur** : Autodesk


**Résumé**
Lancé en 2000, Revit est un logiciel de modélisation des informations du bâtiment (BIM) destiné aux architectes, ingénieurs, concepteurs et entrepreneurs. Le logiciel BIM permet d'utiliser le même fichier pour la conception 3D, le dessin 2D, l'annotation et l'intégration d'informations sur le bâtiment, provenant entre autre d’un catalogue de pièces standards. Il comprend des outils spécifiques à chaque étape du cycle de vie d'un bâtiment, y compris la conception, la construction, l'entretien et la démolition.


**Comment visualiser les fichiers sur les postes de travail CAO CCA**
La plupart des dossiers Revit devraient être ouverts avec la version 2014. Si vous avez des difficultés à ouvrir un dossier, essayez de l'ouvrir avec le bouton "Audit" coché dans Revit.


**Caractéristiques à noter**
Les projets Revit peuvent être exportés sous forme de fichiers IFC. Certaines informations spécifiques à Revit peuvent être perdues au cours du processus, mais l'IFC est ce qui se rapproche le plus d'un format standard complet et neutre pour le BIM.


**Peut importer**
.dgn, .dwg, .dxf, .jpg, .png, .sat, .skp, .tif


**Peut exporter**
.avi, .dgn, .dwf, .dwg, .dxf, .fbx, .ifc, .jpg, .pdf, .png, .sat, .tif


**Navigation et utilisation**
lorem ipsum

<a name="3ds"></a>
## 3ds Max
**Extensions de fichiers associées** : .3ds, .max
**Vendeur** : Autodesk




**Résumé**
3ds Max est sorti pour la première fois sous le nom de 3D Studio en 1990. Au fil des ans, le nom est passé de 3D Studio à 3D Studio Max (1996) puis à 3ds Max (2006). 3ds Max est une application de bureau pour la modélisation, le rendu et l'animation 3D utilisée par les industries de l'architecture, des jeux, du cinéma et de l'animation. Elle peut entre autres être utilisée pour créer des rendus haute définition de projets conçus dans Revit.


**Types de fichiers**
3DS : 3DS est un format de fichier binaire natif pour 3ds Max. Contrairement à MAX, 3DS est interopérable avec d'autres logiciels de modélisation 3D.
MAX : MAX est le format de fichier interne natif de 3ds Max.


**Comment visualiser les fichiers sur les stations de travail CAO CCA**
Les fichiers 3DS et MAX peuvent être ouverts avec 3ds Max 2015.


**Peut importer**
Studio 3D (.3DS)
Adobe Illustrator (.AI)
Exportation de scènes ASCII (.ASE)
Lightscape - Matériel (.ATR), Blocs (.BLK), Paramètre (.DF), Couches (.LAY), Préparation (.LP), Vue (.VW)
Autodesk DWF (.DWF)
Autocad DWG (.DWG)
Autocad DXF (.DXF)
Autodesk FBX (.FBX, .DAE)
Fichier HTR d'analyse de mouvement (.HTR)
IGES (.IGS)
JSR-184 (.M3G)
Objet et matériel de front d'onde (.OBJ) et matériel (.MTL)
StereoLitho (.STL)
Shockwave 3D (.W3D)
VRML97 (.WRL)


**Peut exporter**
Studio 3D (.3DS, .PRJ)
Adobe Illustrator (.AI)
LandXML / DEM / DDF (.XML, .DEM, .DDF) Dessin sur Autocad (.DWG, .DXF)
Legacy Autocad (.DWG)
Autodesk FBX (.FBX, .DAE)
Fichier HTR d'analyse de mouvement (.HTR)
IGES (.IGE, .IGS, .IGES)
Inventeur Autodesk (.IPT, .IAM)
Lightscape (.LS, .LP, .VW)
Objet de front d'onde (.OBJ) et matériau (.MTL) Forme de studio 3D (.SHP)
StereoLitho (.STL)
Analyse du mouvement Fichier TRC (.TRC) VRML (.WRL, WRZ)
VIZ Matériel XML (.XML)


**Navigation et utilisation**
Il existe de nombreuses façons de visualiser et de naviguer dans l'espace 3D dans 3ds Max. Pour une bonne introduction, voir [ce guide](https://knowledge.autodesk.com/support/3ds-max/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/3DSMax/files/GUID-CDA67D65-73D5-4F91-9378-D00B85ED6898-htm.html).


La façon la plus simple de naviguer dans un fichier 3D dans 3ds Max est probablement par le [ViewCube](https://knowledge.autodesk.com/support/3ds-max/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/3DSMax/files/GUID-F8D9EF38-A2BB-4502-95A7-4897A7F30F21-htm.html).

<a name="rhinoceros"></a>
## Rhinoceros
**Extensions de fichiers associées** : .3dm
**Vendeur** : Robert McNeel & Associés


**Résumé**
Rhinoceros (plus communément appelé Rhino) est un outil de conception en 3D basé sur NURBS pour Windows et Mac OS X, lancé en 1998 et couramment utilisé pour la conception assistée par ordinateur, la fabrication, l'impression 3D et le travail multimédia. L'attrait de Rhino peut être attribué en partie à sa vaste bibliothèque de plug-ins, tels que Grasshopper (script visuel) et V-Ray (rendu), qui étendent les fonctionnalités natives de Rhino.


**Comment visualiser les fichiers sur les stations de travail CAO CCA**
Vous pouvez ouvrir des fichiers .3dm (et beaucoup d'autres) avec Rhinocéros 5.


**Caractéristiques à noter**
Le format de fichier 3DM de Rhino a été ouvertement documenté dans le cadre de l'initiative openNURBS de Robert McNeel & Associates, et peut être lu et écrit par la boîte à outils openNURBS.


Lorsque vous ouvrez des formats de fichiers CAO qui ne sont pas dans le format natif de Rhino, le programme crée toujours un nouveau dessin appelé "Sans titre" et convertit le fichier, ce qui signifie que pour que le fichier reste dans son ancien format de fichier, il doit être reconverti dans son format d'origine.


Bien que Rhino puisse importer des fichiers DWG, il ne peut pas toujours lire les versions les plus récentes de ce format. Ce retard peut être attribué au temps qu'il faut pour inverser les nouvelles versions du format DWG après leur sortie par Autodesk. Rhino 5 peut importer et exporter des formats de fichiers DWG/DXF jusqu'à la version 2014.


En l'absence de Microstation, Rhino est le meilleur outil disponible pour importer des DGN pour l'exportation dans d'autres formats pour une utilisation entre autres dans les publications électroniques.


**Peut importer/exporter**
DWG/DXF (jusqu'à la version 2014), IGES, STEP, SLDPRT, SAT, DGN, FBX, 3DS, LWO, STL, SLC, OBJ, AI, RIB, POV, UDO, VRML, CSV, BMP, TGA, TIFF, VDA, GHS, GTS, KML, PLY, SketchUp


D'autres formats peuvent être pris en charge par des plugins tiers.


**Navigation et utilisation**
Commencez à vous familiariser avec les fonctions de navigation de Rhino 5 en regardant cette [courte vidéo](https://vimeo.com/58212839).


En perspective :


Rotation : Bouton droit de la souris + glisser
Pan : Shift + bouton droit de la souris + glisser
Zoom : Ctrl + bouton droit de la souris + glisser OU molette de défilement


En vue ortho (en haut, devant, à droite) :


Pan : Bouton droit de la souris + glisser
Zoom : Ctrl + bouton droit de la souris + glisser OU molette de défilement


Sachez que des éléments d'un modèle 3D peuvent exister dans des couches qui ne sont pas activées au moment de l'ouverture du fichier. Pour gérer les couches, allez dans l'onglet "Couches" sur la droite de l'écran. Cliquez sur l'icône de l'ampoule pour allumer et éteindre les calques.

<a name="microstation"></a>
## Microstation
**Extensions de fichiers associées** : .dgn
**Vendeur** : Bentley Systems


**Résumé**
Microstation est un logiciel de CAO 2D et 3D développé et vendu par Bentley Systems, dont la première version est sortie en 1985. Microstation est couramment utilisé pour les projets d'infrastructure. Sa plus grande base d'utilisateurs se trouve au Royaume-Uni. La version actuelle de Microstation, en avril 2016, est Microstation V8i.


**Comment visualiser les fichiers sur les stations de travail CAO CCA**
Bien que le CCA ne dispose pas d'une version avec license complète de Microstation, les fichiers DGN peuvent être consultés en lecture seule dans le logiciel gratuit Bentley View, installé sur nos postes de travail de CAO. Les fichiers DGN peuvent également être importés (et ensuite réexportés dans d'autres formats) dans Rhino 5.


**Caractéristiques à noter**
Bien qu'historiquement Microstation ait proposé des versions Mac et UNIX de ses logiciels, Microstation est maintenant un produit exclusivement Windows.

<a name="maya"></a>
## Maya
**Extensions de fichiers associées** : .ma, .mb
**Vendeur** : Autodesk (à l'origine Alias)


**Résumé**
Maya est une application utilisée pour générer des animations 3D destinées à être utilisées dans le cinéma, la télévision, le développement de jeux et l'architecture. Le logiciel a d'abord été développé par Alias Systems (plus tard Alias|Wavefront, qui appartenait à Silicon Graphics Inc.) et a été mis sur le marché pour le système d'exploitation IRIX en février 1998. Cependant, ce support a été interrompu en août 2006 après la sortie de la version 6.5. Maya était disponible en édition "complète" et "illimitée" jusqu'en août 2008, date à laquelle il a été transformé en une seule suite.


Les utilisateurs définissent un espace de travail virtuel (scène) pour mettre en œuvre et éditer les médias d'un projet particulier. Les scènes peuvent être enregistrées dans différents formats, le format par défaut étant .mb (Maya Binary). Maya expose une architecture de graphe de nœuds. Les éléments de la scène sont basés sur les nœuds, chaque nœud ayant ses propres attributs et sa propre personnalisation. Par conséquent, la représentation visuelle d'une scène est entièrement basée sur un réseau de nœuds interconnectés, en fonction des informations de chacun. Pour faciliter la visualisation de ces réseaux, il existe une dépendance et un graphique acyclique dirigé.


Maya continue d'être utilisé sous Windows et Mac OS X pour de nombreux grands projets cinématographiques, de jeux et d'architecture.


**Types de fichiers**
MA : Maya ASCII (format texte)
MB : Maya Binary (comprimé, format binaire)


**Comment visualiser les fichiers sur les postes de travail CAO CCA**
Vous pouvez ouvrir des fichiers .ma et .mb avec Autodesk Maya 2014.


**Caractéristiques à noter**
Le format de fichier ASCII de Maya a changé à partir de Maya 2013. Cela rompt la rétrocompatibilité, en particulier lorsque le fichier .ma contient des maillages.


**Navigation et utilisation**
En Maya 2014 :


Pan : Alt + bouton du milieu de la souris
Rotation : Alt + bouton gauche de la souris
Zoom : Alt + bouton droit de la souris


Pour plus d'informations, voir [ce tutoriel sur la navigation dans Viewport dans Maya](http://www.worldofleveldesign.com/categories/3d_modeling/maya-tutorial-for-beginners-04-viewport-navigation.php).

<a name="alias"></a>
## Alias
**Extensions de fichiers associées** : .wire
**Vendeur** : Autodesk (à l'origine Alias)


**Résumé**
Peut se référer à l'un ou l'autre des Alias Studio, etc. (ensemble d'outils de conception industrielle) ou PowerAnimator (suite de modélisation 3D, d'animation et d'effets visuels qui a été le précurseur de Maya).


**Comment visualiser les fichiers sur les stations de travail CAO CCA**
Les stations de travail CAO du CCA sont équipées de trois versions d'Alias faisant partie de la suite Autodesk 2014. Ils devraient pouvoir ouvrir n'importe quel fichier .wire Alias.

<a name="formz"></a>
## form·Z
**Extensions de fichiers associées** : .fmz
**Vendeur** : AutoDesSys


**Résumé**
Form-Z est un outil de conception assistée par ordinateur (CAO) développé par AutoDesSys pour tous les domaines de conception qui traitent de l'articulation des espaces et des formes 3D et qui est utilisé pour la modélisation, le dessin, l'animation et le rendu 3D.


En général, Form-Z permet de concevoir en 3D ou en 2D, en utilisant des entrées numériques ou graphiques interactives par le biais de dessins linéaires ou de dessins à ombres lisses (OpenGL) parmi les plateformes de dessin, de modélisation, de rendu et d'animation.


**Comment visualiser les fichiers sur les stations de travail CAO CCA**
Le CCA a installé deux versions de form-Z sur ses postes de travail de CAO : form-Z 8 Pro et form-Z 6.73. form-Z 8 Pro ne peut ouvrir que les fichiers form-Z relativement récents ou les fichiers qui ont été migrés vers la dernière version du format .fmz. form-Z 6.73 peut lire certains (mais pas tous) fichiers .fmz plus anciens, en faisant la version privilégiée pour tenter d'ouvrir des fichiers .fmz issus des archives.


Il se peut qu'aucune des versions de form-Z, installées sur les postes de travail de CAO, ne soit capable d'ouvrir des fichiers dans une archive. Si tel est le cas, veuillez en informer l'archiviste numérique, afin que nous puissions étudier les possibilités d'accès aux fichiers en question.


**Caractéristiques à noter**
Il est important de savoir que le formulaire Z n'est pas rétrocompatible. Les versions plus récentes du logiciel ne peuvent donc pas ouvrir les fichiers créés dans l'ancienne version du formulaire Z.


**Navigation et utilisation**
Voir les ressources suivantes :


* [Voir la navigation et le contrôle](http://www.formz.com/manuals/formz7/!SSL!/WebHelp/01020_View_navigation_and_control.html)
* [vidéo form-Z : Navigation](https://www.youtube.com/watch?v=x0ipLHhbZjY)

<a name="catia"></a>
## CATIA
**Extensions de fichiers associées**: .CATPart, .CATProduct, others
**Vendeur**: Dassault Systèmes
**Résumé**
lorem ipsum
**Comment visualiser les fichiers sur les stations de travail CAO CCA**
lorem ipsum
**Caractéristiques à noter**
lorem ipsum
**Navigation et utilisation**
lorem ipsum
## Digital Works
**Extensions de fichiers associées**: .CATPart, .CATProduct
**Vendeur**: Gehry Technologies
**Résumé**
lorem ipsum
**Comment visualiser les fichiers sur les stations de travail CAO CCA**
lorem ipsum
**Caractéristiques à noter**
lorem ipsum
**Navigation et utilisation**
lorem ipsum



<a name="solidworks"></a>
## SolidWorks
**Extensions de fichiers associées**: .SLDPRT
**Vendeur**: Dassault Systèmes
**Résumé**
lorem ipsum
**Comment visualiser les fichiers sur les stations de travail CAO CCA**
lorem ipsum
**Caractéristiques à noter**
lorem ipsum
**Navigation et utilisation**
lorem ipsum

<a name="sketchup"></a>
## Sketchup
**Extensions de fichiers associées** .skp
**Vendeur**: Trimble Navigation (originally Google)
*Résumé**
lorem ipsum
**Comment visualiser les fichiers sur les stations de travail CAO CCA**
lorem ipsum
**Caractéristiques à noter**
lorem ipsum
**Navigation et utilisation**
lorem ipsum



<a name="stl"></a>
## STL
**Extensions de fichiers associées** : .stl
**Vendeur** : Non spécifique au vendeur


**Résumé**
STL est un format de fichier indépendant du fournisseur, utilisé le plus souvent pour l'impression 3D et la fabrication assistée par ordinateur (FAO). Il existe des variantes ASCII et binaires du format STL.


**Comment visualiser les fichiers sur les postes de travail CAO CCA**
Les fichiers STL sont plus faciles à consulter dans Rhino.


**Caractéristiques à noter**
Les fichiers STL ne contiennent que des informations sur la géométrie des surfaces. Voir la page [wikipédia STL](https://en.wikipedia.org/wiki/STL_(file_format)) pour des informations plus détaillées.

<a name="iges"></a>
## IGES
**Extensions de fichiers associées** : .iges, .igs
**Vendeur** : Non spécifique au vendeur


**Résumé**
IGES, ou Initial Graphics Exchange Specification, est un format CAO léger et neutre pour l'échange de données géométriques. Il s'agit d'un format ASCII, c'est-à-dire codé en ASCII et basé sur du texte. Concrètement, cela signifie que vous pouvez ouvrir les fichiers IGES dans un éditeur de texte pour explorer leur contenu et même apporter des modifications aux modèles.


IGES a été publié en 1980 et est pris en charge comme format d'importation/exportation dans la plupart des produits de CAO. Bien qu’il soit répandu à l’époque, son principal inconvénient est que les fichiers IGES ne peuvent contenir rien de plus que des informations géométriques de base. C'est pour cette raison que la dernière version publiée du format IGES date de 1996, à peu près au même moment où le logiciel STEP gagnait en popularité.


**Comment visualiser les fichiers sur les stations de travail CAO CCA**
Les fichiers IGES peuvent être consultés à partir de la plupart des programmes de CAO. Comme tous les logiciels ne sont pas précisément conformes à la norme IGES, il est conseillé d'ouvrir les fichiers dans un logiciel qui s’apparente autant que possible au logiciel sur lequel le fichier a été créé, s'il est connu.

<a name="step"></a>
## STEP
**Extensions de fichiers associées** : .step, .stp, .p21
**Vendeur** : Non spécifique au vendeur


**Résumé**
STEP, ou Standard for the Exchange of Product Model Data, est un format ISO lancé en 1984 pour remplacer les normes existantes telles que l'IGES, en les complétant et en les définissant rigoureusement. Le développement s'est poursuivi depuis, des éléments de la norme ayant été publiés tout au long des années 1990 et 2000.


Un certain nombre de formats de fichiers autorisés ont été inclus dans le cadre de la norme STEP. Ceux-ci ont été regroupés et désignés comme fichiers STEP. Les formats les plus courantes de STEP sont AP203 ; AP214, qui s'étend sur AP203 avec un support pour les informations telles que les couches ; et AP242, un format plus lourd destiné à être utilisé dans les industries manufacturières et aérospatiales.


Bien que la conversion de la plupart des modèles de CAO propriétaires en STEP implique un certain degré de perte de données (comme les données paramétriques), STEP est ce qui se rapproche le plus d'un format d'échange de fichiers de CAO complet et indépendant du fournisseur, et a souvent été présenté comme un format de préservation potentiel. De nombreux produits de CAO soutiennent désormais les importateurs et les exportateurs STEP, en partie grâce aux efforts de groupes tels que le CAx Implementors Forum, qui ont contribué à la mise au point de ces outils.


**Comment visualiser les fichiers sur les stations de travail CAO CCA**
Les fichiers STEP peuvent être ouverts dans un certain nombre de programmes de CAO. En raison de la possibilité que le logiciel d'origine ne soit pas précisément conforme à la norme STEP, il est conseillé d'ouvrir les fichiers dans un logiciel qui s’apparente autant que possible du logiciel sur lequel le fichier a été créé, s'il est connu.

<a name="dae"></a>
## COLLADA
**Extensions de fichiers associées** : .dae
**Vendeur**: Non-vendor specific
*Résumé**
lorem ipsum
**Comment visualiser les fichiers sur les stations de travail CAO CCA**
lorem ipsum
**Caractéristiques à noter**
lorem ipsum
**Navigation et utilisation**
lorem ipsum

<a name="ifc"></a>
## IFC
**Extensions de fichiers associées**: .ifc
**Vendeur**: Non-vendor specific
*Résumé**
lorem ipsum
**Comment visualiser les fichiers sur les stations de travail CAO CCA**
lorem ipsum
**Caractéristiques à noter**
lorem ipsum
**Navigation et utilisation**
lorem ipsum
