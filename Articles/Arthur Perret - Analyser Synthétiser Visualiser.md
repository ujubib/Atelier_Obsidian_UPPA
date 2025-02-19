---
url: https://www.arthurperret.fr/blog/2022-02-17-analyser-synthetiser-visualiser.html
title: "Analyser, synthétiser, visualiser&nbsp;: le triptyque fiche, lien, graphe"
author: Arthur Perret
date: 2022-02-17
lang: fr
publication: oui
---

Ce billet prolonge le précédent, [« À quoi sert une vue graphe ? »](https://www.arthurperret.fr/blog/2022-02-13-a-quoi-sert-une-vue-graphe.html), dans lequel j’évoque l’utilité de la représentation visuelle pour la prise de notes interreliées. J’avançais principalement les idées suivantes :

> Les nouveaux outils de prise de notes émergent dans un contexte où l’effet de nouveauté prime sur les fonctionnalités documentaires, et répondent avant tout à un besoin façonné par plusieurs années de domination du smartphone et du moteur de recherche. […]
>
> Le graphe donne à voir l’hypertexte, conceptuellement et concrètement, ce qui influence la manière d’écrire et de penser l’interrelation ; et plus on fait en sorte qu’il donne également à voir le travail documentaire méthodique appliqué aux fiches, plus son utilité augmente.
>
> En admettant que l’essor des nouveaux outils de prise de notes a finalement peu de choses à voir avec l’hypertexte et la documentation, je pense qu’on comprend mieux pourquoi tant de gens se demandent à quoi peut bien servir une vue graphe.

Hendrik Erz, développeur de Zettlr, s’est emparé du sujet et m’a répondu dans un billet intitulé [« Quo vadis, PKM? »](https://www.hendrik-erz.de/post/quo-vadis-pkm), dont je vous recommande la lecture. Il contient deux éléments importants. D’abord, une critique des graphes :

> *“As humans we are used to detecting patterns, so whenever we look at a network, we immediately attempt to make sense of it. And that can lead to critical errors in judgment.”*« Nous, êtres humains, sommes faits pour détecter des motifs. Alors dès que nous observons un réseau, nous tentons immédiatement de lui attribuer du sens. Or cela peut conduire à d’énormes erreurs d’interprétation ».

Et ensuite, une proposition alternative (ou complémentaire) :

> *“We can have our computer search for connections between notes by looking at the words we use. This way, our computer can learn to identify synonyms on its own. By displaying this information in the appropriate places, our note taking tools can show us the network of our knowledge without either of us having to make any grave mistakes.”*« Nous pouvons demander aux ordinateurs de chercher des liens entre les notes par le biais des mots que nous utilisons. Un ordinateur peut apprendre à identifier des synonymes par lui-même. En affichant ces informations au bon endroit, nos outils de prise de notes peuvent nous suggérer l’interrelation de nos connaissances avec un risque d’erreur bien moindre ».

Sur cette proposition, je me garderai de tout commentaire technique, car je ne connais rien au traitement automatique des langues ni à l’apprentissage machine. Par contre, je suis curieux de voir cette fonctionnalité en action. L’idée de baser l’interrelation sur les mots-clés me paraît tout à fait pertinente. C’était la manière de procéder de [Paul Otlet](https://fr.wikipedia.org/wiki/Paul_Otlet), qui proposait d’indexer les documents via la [Classification décimale universelle](https://fr.wikipedia.org/wiki/Classification_décimale_universelle), et d’utiliser ensuite les tables d’indexation pour suggérer des relations entre les documents.

Sur le premier point en revanche, il faut absolument que je réponde car il y a un risque de malentendu.

Je suis entièrement d’accord avec Hendrik : interpréter la signification d‘un graphe est très risqué. Sauf que je ne crois pas du tout à cet usage dans le contexte de la prise de notes. J’ai écrit que le graphe nous incite à rechercher des motifs mais je ne pensais pas à un acte interprétatif : ces motifs servent la réflexivité du processus d’écriture, pas la réflexion sur le contenu des notes. Je redonne mes deux exemples : le graphe permet de repérer rapidement des notes isolées qu’on va vouloir relier à d’autres notes ; il permet aussi de constater l’existence d’un aggrégat de notes qui s’est densifié au fur et à mesure qu’on les interreliait une à une, et cela incite à regarder de plus près (pour se remémorer les liens, en ajouter, en enlever). Notez que je ne parle pas de découvrir un sens caché, ou une signification sur la relation entre deux idées, mais d’une visualisation comme aide à la décision dans le processus d’écriture.

En fait, je pense que le problème vient de l’expression « prise de notes », qui est trompeuse. Elle suggère que l’on capte des choses, que l’on extrait de l’information, et donc qu’on va pouvoir ensuite organiser cela pour en tirer du sens. Or ma perspective est complètement différente. Je ne suis pas dans une logique extractive, qu’elle soit purement manuelle ou en partie automatisée, et qui mènerait logiquement à vouloir faire de l’analyse de contenu, à interpréter. Je suis dans une logique créative, ce qui veut dire deux choses.

Premièrement, tout ce qui est contenu dans mes notes a été créé par moi. Certes, il y a beaucoup d’information issue de sources extérieures : mes fiches de lecture contiennent des extraits que j’ai recopiés ; mes fiches « concept » contiennent des définitions issues de dictionnaires et d’encyclopédies ; mes fiches « personne » représentent de vrais individus, pas des entités fictives. Mais je n’ai pas moissonné automatiquement ces choses-là à partir de pages web, d’entrepôts de données ou de fichiers d’autorités : je les ai copiées ou recopiées manuellement.

Et surtout, c’est la même chose pour les liens. Aucune relation n’est créée automatiquement. Si deux concepts sont reliés de manière hiérarchique dans mes fiches et dans mon graphe – par exemple, « Graphe » d’une part, et « Graphe de documents » d’autre part –, c’est moi qui l’ai inscrit ainsi, en qualifiant les liens façon thésaurus (concept générique/spécifique). Je rappelle au passage que c’est une fonctionnalité de [Cosma](https://cosma.graphlab.fr) que très peu d’outils proposent et qui se met en place de manière très simple au niveau de l’écriture, en mimant la logique sujet-prédicat-objet du Web sémantique :

```
Cet auteur a écrit sur [[identifiant]] un concept.

Mais cet autre [[préfixe:identifiant]] concept a une relation qualifiée de manière précise.

Le graphe de documents est un cas particulier de [[générique:identifiant]] graphe.
```

Je sais donc déjà tout ce qu’il y a dans mes fiches : je n’ai pas besoin de le découvrir, seulement de le re-découvrir. Je n’ai pas besoin de débroussailler une extraction de Wikidata ou du VIAF : j’ai juste besoin de me souvenir des choses que j’ai écrites, pour en écrire de nouvelles. Le sujet n’est donc pas l’interprétation mais bien la capacité à se remémorer, augmentée par l’outillage. En matière de références, on est ici à la fois dans l’augmentation de **Douglas Engelbart** [@engelbartAugmentingHumanIntellect1962], les *tools for thought* (outils pour penser) de Howard Rheingold [@rheingoldToolsThoughtHistory2000] [*Tools for thought*, 2000 [1985]](https://www.arthurperret.fr/blog/2022-02-17-analyser-synthetiser-visualiser.html#ref-rheingold2000).  
 et l’écriture comme technologie intellectuelle chez Jack Goody [*La Raison graphique*, 1979](https://www.arthurperret.fr/blog/2022-02-17-analyser-synthetiser-visualiser.html#ref-goody1979).  
.

Deuxièmement, le but de ma pratique est de produire des choses nouvelles. C’est là qu’on sort de la « prise de notes » entendue comme captation d’information extérieure, et qu’on rentre dans la « prise de notes » comme élaboration de sa propre pensée par le biais de l’écriture. Cela commence par une démarche analytique, au sens premier du mot « analyse » : « décomposition d’une chose en ses éléments, d’un tout en ses partiesSource : [*Trésor de la langue française*](https://cnrtl.fr/definition/analyse). ». C’est le passage de la problématique générale à des concepts ; de la littérature scientifique à des publications, et de ces publications aux idées qu’elles contiennent. Une fois tout cela mis en fiches, commence la synthèse : « par opposition à analyse, opération, méthode par laquelle on procède du simple au complexe, des éléments au tout, de la cause aux effetsSource : [*TLF*](https://cnrtl.fr/definition/synthèse).  
 ». Et la synthèse se fait par les liens.

Pour illustrer le rôle des liens, et puisqu’on m’a reproché de ne pas donner beaucoup d’exemples concrets dans mon précédent billet, voici un exemple.

Je travaille sur l’organisation des connaissances ; j’en ai donc fait une fiche concept. Je travaille en particulier sur l’organisation réticulaire, c’est-à-dire en forme de réseau, avec des cas particuliers de réseaux organisés de manière hiérarchique, les arbres ou arborescences ; réseau, arbre, deux fiches concept de plus.

Lorsque j’ai lu le premier tome de la *Théorie générale de la schématisation* de Robert Estivals, j’ai relevé cette idée essentielle : la cognition humaine reposerait sur un double mouvement de réduction arborescente et d’organisation réticulaire [Estivals, *Théorie générale de la schématisation 1*, 2002, p. 35](https://www.arthurperret.fr/blog/2022-02-17-analyser-synthetiser-visualiser.html#ref-estivals2002).  
. Je l’ai noté dans une fiche de lecture, j’ai créé une fiche « Schématisation » au passage, et j’ai ajouté pas mal de liens dans les deux.

Plus tard, en lisant la thèse de mon collègue Clément Borel, je suis tombé sur cette énumération des métaphores utilisées en organisation des connaissances : arbres, forêts et labyrinthes, rivières, océans et îles, territoires inexplorés, toiles [Borel, *Outils sémantiques au service du livre numérique*, 2014, p. 74‑81](https://www.arthurperret.fr/blog/2022-02-17-analyser-synthetiser-visualiser.html#ref-borel2014).  
. Une fiche de lecture de plus, reliée notamment à « Organisation des connaissances » et « Arbre ».

Arrive le moment de la synthèse. Un jour, en discutant avec des collègues, nous nous sommes fait la réflexion que les arbres et les réseaux sont les métaphores les plus populaires en organisation des connaissances, mais sans parvenir à un consensus sur les raisons de cette popularité. En revenant chez moi, et alors que la question me travaillait, j’ai décidé de mettre à profit mes fiches. En naviguant dans les connexions, j’ai fini par avoir une idée. J’ai alors créé une fiche de type « note » (définie par le fait que j’y mets mes réflexions propres, par opposition aux lectures, concepts et autres informations issues de sources extérieures), contenant grosso modo l’idée suivante : les métaphores en organisation des connaissances reflètent la cognition humaine, qui se trouve être arborescence et rhizomatique. Ci-dessous, je reproduis le contenu du fichier, en remplaçant simplement les `[[identifiants]]` par le symbole `⟡` pour plus de lisibilité. Le rendu dans [Cosma](https://cosma.graphlab.fr) est présenté dans la capture ci-contre. [![](https://www.arthurperret.fr/img/2022-02-17-cosma-fiche.png)](https://www.arthurperret.fr/img/2022-02-17-cosma-fiche.png)

```
Il existe de nombreuses métaphores pour décrire l’⟡ organisation des connaissances : arbres, forêts et labyrinthes, rivières, océans et îles, territoires inexplorés, toiles et bien d’autres choses encore [@borel2014, 74-81]. Les ⟡ arbres et les ⟡ réseaux peuvent être considérés comme les plus populaires, ce qui n’est pas un hasard : dans sa théorie de la ⟡ schématisation, Estivals a montré que la cognition humaine repose sur un double mouvement de réduction arborescente et d’organisation réticulaire [@estivals2002, 35].
```

J’en profite pour répondre à un point soulevé par Hendrik dans les dernières lignes de son billet :

>
>
> *“New insights do not necessarily come about by interconnecting already existing thoughts. New insights come around because we do other things when we don’t write.”*« Les intuitions ne viennent pas forcément de l’interconnexion d’idées déjà inscrites quelque part. Elles apparaissent aussi parce que nous faisons d’autres choses qu’écrire ».
>
>

Comme je l’ai décrit dans l’exemple ci-dessus, il m’arrive fréquemment d’avoir des idées alors que je ne suis pas en train d’écrire. Mais si je veux leur donner corps et les approfondir, je passe à l’écriture. Tiens, au passage, la raison pour laquelle j’ai des notes sur des personnes c’est que cela me permet d’écrire des choses comme celles-ci :

```
Mon ⟡ collègue m'a dit que ⟡ le concept A est essentiel pour comprendre ⟡ le sujet B.
```

Ici, j’utilise encore une fois l’écriture réticulaire pour multiplier les chemins vers l’information. J’ai tendance à me souvenir des échanges parfois mieux que des lectures. Je me dis « Ah mais quelqu’un m’a parlé de ça… », je vais alors vérifier la fiche que j’ai sur la personne en question, je regarde les rétroliens et là je retombe sur l’information. Je suis d’accord avec Hendrik sur le fait qu’on ne passe pas chaque minute de sa vie à écrire mais c’est précisément la raison pour laquelle il faut intégrer cela dans le travail d’écriture. Il est extrêmement utile de documenter l’interrelation des idées avec les personnes, les lieux, les organisations, et pas seulement entre idées : cela permet de façonner son système en fonction d’un milieu de savoir, pas juste d’un répertoire de fiches.

J’espère que cet exemple permet aux lecteurs restés perplexes face au billet précédent de mieux comprendre ma perspective. Ma pratique de la fiche est scientifique ; elle prend appui sur elle-même mais aussi sur le milieu dans lequel elle existe. Elle repose entièrement sur la fiche comme outil analytique (décomposer les choses) et sur le lien comme outil synthétique (composer de nouvelles idées). Enfin, je n’utilise pas le graphe comme un outil d’analyse ni de synthèse mais comme un outil de visualisation, pour augmenter ma capacité de mémorisation et de réflexivité sur le processus d’écriture.

Préciser la position à partir de laquelle j’écris me paraît essentiel, car je ne pense pas représenter la majorité des utilisateurs d’outils de prise de notes interreliées. Il n’y a pas que « prise de notes » qui soit trompeur : je pense que « gestion des connaissances personnelles » (*personal knowledge management*, PKM) l’est autant, voire plus.

Les méthodes et les outils de PKM sont en effet beaucoup utilisés non pas pour gérer de la connaissance mais des tâches. Si on prend une méthodologie de PKM populaire comme celle de Tiago Forte, par exemple, elle n’a pas grand chose à voir avec les techniques d’interrelation documentaire que je décrivais chez Otlet, Luhmann et Matuschak. Le [système PARA](https://fortelabs.co/blog/para/) de Forte (voir capture ci-contre) [![](https://www.arthurperret.fr/img/2022-02-17-para.webp)](https://www.arthurperret.fr/img/2022-02-17-para.webp) est une méthodologie de gestion de projet. On peut la traduire par une arborescence de dossiers dans un outil de prise de notes, mais aussi par les colonnes d’un tableau de type kanban. Bien sûr, elle peut accueillir une pratique telle que la mienne – analytique, synthétique et réticulaire, avec un objectif d’érudition. Mais elle va surtout appuyer des démarches relevant de la « productivité » (encore un terme ambigu…) comme le journal quotidien, la liste de tâches ou le suivi d’un *workflow* – ce qui ne nécessite pas forcément de faire des liens.

Par conséquent, un même outil de prise de notes peut être utilisé par des gens qui font systématiquement des liens et par d’autres qui n’en font pas du tout, ou très peu. On revient alors au sujet de mon précédent billet : à quoi sert la vue graphe, et à qui sert-elle ?

Le lien est le principe fondamental qui sous-tend ma pratique, et j’espère avoir clarifié cela avec mon exemple. Ma « productivité », c’est la production de nouvelles idées. Je les forme par synthèse – on pourrait dire par assemblage, par combinaisonGordon Brander dit : [*composition*](https://subconscious.substack.com/p/self-organizing-ideas).  
 – de différentes fiches, de différents fragments conceptuels. Or le mécanisme de la synthèse, ce qui la fonde, c’est le lien. Donc j’en mets partout.

Comme je le disais dans mon billet précédent, l’interface logicielle joue un rôle fondamental dans l’accompagnement de cette pratique. Mes fiches contiennent de plus en plus des « grappes » de liens, c’est-à-dire des phrases ou des paragraphes contenant plusieurs liens à la suite. Certaines de mes fiches de type « note » (mes idées propres), comme celle que j’ai montrée, se résument à une seule phrase ou un seul paragraphe de ce genre, à la manière des [notes d’Andy Matuschak](https://notes.andymatuschak.org). Si je procède ainsi, c’est parce que certaines applications montrent les liens (et rétroliens) de manière contextualisée, c’est-à-dire avec la phrase ou le paragraphe environnant. À force d’utiliser les rétroliens contextualisés comme moyen de me remémorer le sens d’une connexion, cela a fini par modifier la manière dont je rédige mes fiches.

Autre réflexion sur l’interface : utiliser abondamment les liens rend la vue graphe beaucoup plus utile. Pour moi, ça tombe sous le sens, mais là aussi je vais utiliser un exemple pour clarifier mon propos.

Depuis la publication du billet précédent, dans lequel je critiquais la propension des gens à publier des captures d’écran de leurs graphes, je suis retourné sur le Web examiner quelques exemples de ces captures. Alors que je m’étais focalisé jusqu’ici sur les gens qui s’émerveillent de leur graphe, je me suis intéressé cette fois-ci à ceux qui les critiquent, image à l’appui. Et en regardant les images en question, j’ai constaté qu’elles montraient souvent le même problème : soit l’absence totale d’interrelation entre les notes, soit un potentiel inachevé dans la fonctionnalité de visualisation.

Voici un aperçu de la nouvelle vue graphe de Zettlr, partagé par Hendrik Erz dans [le tweet qui a tout déclenché](https://twitter.com/zettlr/status/1492614979970863106) :

![Un aperçu de la vue graphe dans Zettlr, légendée ainsi par Hendrik Erz : « *Yes, my files are 99% unconnected, that’s not an error!* »](https://www.arthurperret.fr/img/2022-02-17-graph-zettlr.jpeg)

Évidemment qu’ici la vue graphe ne sert à rien : il n’y a quasiment pas de « graphe » au sens de structure, puisqu’il n’y a presque pas de liens entre les fiches. Le « graphe » au sens de visualisation ne permet ici aucune réflexivité sur l’écriture et il ne permet pas non plus de naviguer entre les fiches, son utilité est donc presque nulle.

Deuxième exemple, la vue graphe de Roam, avec cette capture illustrant le billet [« The Fall of Roam »](https://every.to/superorganizers/the-fall-of-roam) de Dan Shipper, dans lequel l’auteur critique vivement l’outil en question :

![La vue graphe de Roam, légendée ainsi par Dan Shipper : « *a very appealing looking garbage dump* ».](https://www.arthurperret.fr/img/2022-02-17-graph-roam.jpeg)

Ici le problème est double. D’abord, l’auteur utilise Roam comme un outil de « productivité » au sens de gestion des tâches, avec une concentration des liens sur une infime partie de ses notes. On se rend compte tout de suite que la vue graphe accompagne mal cette pratique, qui serait sans doute mieux servie par des techniques classiques d’arborescence et d’étiquetage (mots-clés).

Et ensuite, la fonctionnalité est très limitée. La disposition matricielle élimine toutes les régularités et irrégularités « naturelles » susceptibles d’alimenter la réflexivité du processus d’écriture. Et il n’y a pas de différenciation visuelle des catégorisations qui existent sûrement, que ce soit par la centralité de certaines notes ou par des ensembles exclusifs (type dossier) et inclusifs (type étiquettes). Dans ces conditions, est-ce qu’il faut s’étonner que l’auteur du billet qualifie la vue graphe d’« attrayant dépotoir » ?

Je voudrais offrir un contrepoint à tout cela en partageant deux captures d’écran de mes propres fiches, visualisées avec l’outil que mon équipe a conçu, [Cosma](https://cosma.graphlab.fr) :

![Mes fiches dans Cosma : à gauche, un menu permettant de modifier l’affichage du graphe ; à droite, une fiche ouverte.](https://www.arthurperret.fr/img/2022-02-17-graph-cosma.png)

![Une de mes fiches mise en focus dans Cosma : le travail documentaire sur les catégories et les mots-clés est mis à profit par les fonctionnalités du graphe (couleurs, tracés, filtrage).](https://www.arthurperret.fr/img/2022-02-17-graph-cosma-2.png)

En légende, je souligne deux aspects qui rendent la vue graphe dans Cosma plus utile que dans d’autres outils. Premièrement, le graphe est juxtaposé aux fiches. Je ne crois pas du tout à la supériorité du graphe seul, je pense qu’il est indispensable de le connecter étroitement au contenuOn peut reproduire cela dans Obsidian, qui a une interface modulaire extrêmement bien fichue.  
. Et deuxièmement, le graphe met à profit le travail documentaire – catégorisation des fiches et des liens, indexation par mots-clés – à travers la sémiologie graphique (couleur des nœuds, tracé des liens) et les interactions (filtrage, surbrillance, focus).

---

L’heure est venue de conclure. Dans ce billet, et dans le prolongement du précédent, je propose de considérer le triptyque fiche, lien, graphe en le superposant au triptyque analyser, synthétiser, visualiser – cette dernière opération n’étant pas productrice d’un sens autonome mais source de réflexivité dans le processus d’écriture. Dans cette perspective, la vue graphe a une utilité directement corrélée à la place des liens dans la technique de prise de notes, utilité qui décroît au fur et à mesure qu’on s’éloigne d’une écriture réticulaire pour se rapprocher de formes plus traditionnelles (liste, arborescence, étiquettes), généralement mises en œuvre dans le domaine des outils de « productivité ». À l’inverse, plus la vue graphe est proche de l’hypertexte dont elle donne à voir la structure, et plus elle tire parti d’un travail documentaire, même léger (catégorisation, indexation), plus son utilité augmente

Pour clore (temporairement) la réflexion, je voudrais profiter de l’opportunité qui m’est offerte par l’arrivée de nouveaux lecteurs pour attirer l’attention sur le rôle que joue la recherche scientifique dans ces questions.

Dans ma veille, je me suis fait l’écho de [la difficile progression des *tools for thought*](https://www.arthurperret.fr/blog/veille/2021-06-09-difficile-progression-tools-for-thought.html). Andy Matuschak l’a très bien résumé : si ce champ veut produire quelque chose de véritablement révolutionnaire, il faut pouvoir tirer des observations généralisables à partir de notre utilisation des différents outils, et en débattre. Actuellement, les conversations sont éparpillées et mentionnent rarement des travaux de recherche. Or ces travaux existent. C’est un peu le sens de mon intervention dans le débat ces jours-ci, et je pense que c’est aussi l’idée d’Hendrik avec son billet, dans lequel il rappelle son ancrage scientifique : valoriser la recherche sur les outils de prise de notes interreliées.

Mon travail s’inscrit dans les sciences de l’information et de la communication (SIC), cousines françaises de la *Library and information science* anglophone. Ce que j’écris aujourd’hui sur le triptyque fiche, lien, graphe est façonné par la connaissance de la littérature en documentologie et en organisation des connaissances. Cosma, ce n’est pas juste la réunion de l’hypertexte et de la visualisation de données : c’est aussi une filiation revendiquée avec la documentation de Paul Otlet[*Traité de documentation*, 2015 [1934]](https://www.arthurperret.fr/blog/2022-02-17-analyser-synthetiser-visualiser.html#ref-otlet1934).  
 et la tradition de la fiche érudite.

Ce travail a un débouché purement scientifique. Ainsi, dans ma thèse, j’écris que mes notes combinent les éléments d’un graphe de connaissances (modélisation des relations entre des entités, formalisées éventuellement via une ontologie) et d’un graphe documentaire (hypertexte formé par des documents ou des fragments de documents). Ce travail permet de faire progresser des hypothèses par rapport à une problématique.

Mais je pense qu’il est utile d’intervenir aussi hors du champ universitaire, grâce à un espace comme le carnet de recherche, susceptible d’être lu par d’autres publics. Et puisqu’on parle de lecture, et que ce billet touche à sa fin, il ne me reste plus qu’à vous remercier de m’avoir lu.

### Bibliographie

Borel, Clément. *Outils sémantiques au service du livre numérique. Modélisation et visualisation des liens transtextuels.* Thèse de doctorat. Université de Franche-Comté, 2014. [http://www.theses.fr/s22780](http://www.theses.fr/s22780).

Engelbart, Douglas C. *Augmenting Human Intellect: A Conceptual Framework*. SRI Summary Report n°AFOSR-3223. Stanford Research Institute, 1962. [https://www.dougengelbart.org/content/view/138/](https://www.dougengelbart.org/content/view/138/).

Estivals, Robert. *Théorie générale de la schématisation 1 : Épistémologie des sciences cognitives*. L’Harmattan, 2002. 978-2-7475-2641-0.

Goody, Jack. *La Raison graphique : la domestication de la pensée sauvage*. Les Editions de Minuit, 1979. 978-2-7073-0240-3.

Otlet, Paul. *Traité de documentation. Le livre sur le livre*. Les Impressions nouvelles, 2015 [1934]. 978-2-87449-299-0.

Rheingold, Howard. *Tools for thought: the history and future of mind-expanding technology*. MIT Press, 2000 [1985]. 978-0-262-68115-5.