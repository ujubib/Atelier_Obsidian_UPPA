---
title: "Rédaction&nbsp;: gérer les différences de versions avec Git"
subtitle: Carnet Hypothèses Engagées^[https://engagees.hypotheses.org/3959]
author: Aurore Turbiau
date: 2023-01-28
url: https://engagees.hypotheses.org/3959
lang: fr
publication: oui
---

Dernières lignes droites de la thèse. Je suis en train de boucler les chapitres, de les recomposer, de couper dans le lard (enfin, d’essayer), et de faire un certain nombre d’échanges de relectures / réécritures : c’est à la fois le moment où j’ai peur de m’emmêler les pinceaux et de perdre des bouts de texte, et celui de la multiplication des versions. Comme j’ai créé un compte GitLab [en prévision du dépôt de mon code de base de données cet été](https://engagees.hypotheses.org/97), je me suis dit que j’allais tester Git pour la rédaction elle-même. Spoiler : billet méga geek.

En principe, **Git est un outil destiné aux programmeuses et programmeurs** : il permet de modifier un code progressivement sans risquer de faire de bêtises ou de perdre des morceaux, comme de collaborer à plusieurs en même temps sur un même code sans que le chevauchement des réécritures pose problème. Pas vraiment littéraires-friendly au départ, quoi : mais en même temps pourquoi pas essayer. Comme les programmes des informaticien·nes, mes fichiers de thèse ne sont en fin de compte que des fichiers de texte pur (par opposition à un fichier word ou libre office), et comme les programmeurs/programmeuses, j’ai besoin de comparer des versions, de me garantir à moi-même que je ne perdrai jamais rien même si un jour j’ai la fâcheuse idée de couper un bout de texte dont j’aurai finalement besoin plus tard, besoin aussi de manipuler différents états de fichiers sans me perdre dans des copies infinies, en travaillant en fait, idéalement, avec *une seule* version du fichier (mais de sorte que le logiciel se souvienne de toutes les autres). Alors pourquoi pas, hein.

Manifestement d’autres personnes ont la même idée légèrement hétérodoxe : grâce à \@UjuBib sur Twitter j’ai par exemple pu parcourir cet article :

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Git for Writers | How to Organize Projects with Git and GitKraken <a href="https://t.co/XkD3jHgS4x">https://t.co/XkD3jHgS4x</a></p>&mdash; J.R. (\@UjuBib) <a href="https://twitter.com/UjuBib/status/1617463150089236480?ref_src=twsrc%5Etfw">January 23, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Au moment où j’écris, cela fait un mois que j’utilise Git. J’ai pu l’utiliser pour différentes choses :

* **De la refonte intense de chapitres** : pour ceux que je n’avais encore que [sous forme de brouillons](https://engagees.hypotheses.org/3825), analyses de textes entièrement rédigées mais structure globale en bazar, il a fallu que je copie-colle un max, restructure, déplace, supprime, etc. Enjeu de la conservation/comparaison des versions : ne rien risquer de perdre au milieu de ces grands déménagements.
* **De la relecture réécriture perso**. Enjeu de la conservation/comparaison des versions, à part, toujours, ne rien risquer de perdre : ne pas multiplier les fichiers, un seul par chapitre et basta.
* **De la réécriture post-commentaires de ma directrice de thèse**. Enjeu spécifique : pouvoir comparer spécifiquement les versions que je lui envoie à elle (pour moi, entre temps, il y en a une multiplicité), afin de pouvoir, à elle, lui épargner de relire des choses déjà parcourues, à moi, à la fois m’éviter de me perdre dans mes fichiers, et ne pas m’embêter à devoir retrouver, ligne à ligne et à la main, ce qui change entre un vieux fichier et un autre (le logiciel le fait pour moi, quoi, moi je m’occupe juste d’avancer).

Sur ce dernier point, j’imagine que ça peut paraître obscur et bizarre aux personnes qui bossent sur Word ou Libre Office : si tu bosses directement sur ton fichier doc ou odt, facile de garder trace des commentaires de la DT, et d’y répondre, et de mettre en surlignage les modifications et hop le tour est réglé. En vrai, oui, absolument. Seulement moi je travaille sur Zettlr en markdown, que je préfère pour tout un tas de raisons, la principale étant la gestion de la mise en forme finale des chapitres puisque Word et Libre Office ont une fâcheuse tendance à faire n’importe quoi avec les styles et balisages texte, l’autre principale étant la gestion de la bibliographie, que je trouve hyper économique et claire dans Zettlr (j’avais parlé de mon choix de Zettlr pour la rédaction de la thèse [par ici](https://engagees.hypotheses.org/2948)). Or ce ne sont pas mes fichiers .md que j’envoie à ma directrice de thèse (mais des exports doc ou odt) ; et en outre, Zettlr ne permet pas les surlignages ou les commentaires (enfin, pas vraiment, pas aussi ergonomiquement, pour le coup, qu’un traitement de texte standard). Bref, l’inconvénient de Zettlr, c’est que je ne peux pas directement travailler sur les retours de ma directrice, je dois les y transposer et me débrouiller comme ça.

C’est le point de départ spécifique de mon utilisation de Git, donc : le fait de travailler sur Zettlr, donc d’écrire ma **thèse en markdown** (= fichiers de texte pur, adaptés pour l’usage de Git), et d’avoir une problématique originale de **gestion des réécritures**. Si vous n’êtes pas dans ce cas, j’imagine que le bail vous intéressera moyen. Maintenant allons-y.


Contextes et cas d’utilisation : comment ça marche
----------

![Mon compte GitLab : on voit un projet public (pour l’instant vide), celui de la banque de citations, et deux projets privés auxquels je suis seule à avoir accès, dont la thèse.
](https://engagees.hypotheses.org/files/2023/01/Billet-Git-Le-compte-sur-GitLab.png)

L’usage de Git implique de pouvoir synchroniser ses fichiers à deux endroits différents : d’une part, sur votre ordinateur comme d’habitude, d’autre part, sur un dépôt distant, privé mais en ligne. Pour cela, il faut se créer un compte (sur GitLab, ou GitHub…) : dans la capture ci-contre, vous pouvez voir l’aperçu du mien, qui comporte trois projets, celui de la thèse (privé), celui du code de la banque de citations que je prévois de mettre en ligne cet été (public, vide pour l’instant), celui du code actuel de la banque de citations (privé).

En ligne sur votre dépôt, comme dans l’explorateur de votre ordinateur, se trouvent les fichiers du projet (de la thèse) :

<table>
<tr>
<td>

![À gauche : sur mon ordinateur, dossier où sont contenus les fichiers de thèse (ici deux fichiers par chapitre : un dossier avec le texte, un dossier avec les notes).](https://engagees.hypotheses.org/files/2023/01/Billet-Git-arborescence-fichiers-projet-Git.png)

</td>
<td>

![À droite : sur le dépôt GitLab en ligne, projet où sont contenus exactement les mêmes fichiers. “Début retravail partie 2” est le commentaire que j’ai associé à ma dernière mise à jour des fichiers.
](https://engagees.hypotheses.org/files/2023/01/Billet-Git-Laffichage-des-fichiers-sur-GitLab.png)

</td>
</tr>
</table>

Concrètement, on n’est pas obligé·es d’aller voir en ligne ce qui s’y passe, tout peut se passer sur l’ordinateur en local, mais c’est en ligne que se trouve la vraie sauvegarde de l’évolution de la thèse.

L’intérêt majeur de ce dispositif : certes, comme on voit, les fichiers sont assez nombreux (18 fichiers de chapitres pour moi, plus les fichiers secondaires comme annexes, remerciements, introductions de parties, etc.), mais ils sont *uniques.* **Git permet de se dispenser des multiples V1, V2, V3, V45, version-finale, version-finale-finale, etc.** Un seul fichier pour chaque section : Git garde l’historique et permet de revenir en arrière ou de revoir ce qui se trouvait auparavant dans le fichier. Git = astuce propreté dans les fichiers, hygiène organisationnelle.

Plusieurs outils permettent de visualiser facilement l’évolution des dépôts, la construction progressive de la thèse. Gitg principalement :

![Capture d'écran gitg](https://engagees.hypotheses.org/files/2023/01/Billet-Git-Affichage-gitg.png)

Elle présente l’affichage graphique de l’état du projet Git. Dans la colonne de gauche, les différents lieux de dépôt, distant (“origin/main”) et local (“main”), ainsi que le récap des tags utilisés (ici “V1-Tomiche”). La fenêtre principale, à droite en haut, indique l’arborescence du projet : dans mon cas c’est simple, il n’y a aucun embranchement puisque je travaille solo sur un seul ordinateur, donc les versions se succèdent, du bas vers le haut, de l'”initial commit” jusqu’à l’état actuel qui marque la réécriture du chapitre 4 ; on voit que l’avant-avant-dernier dépôt marque une étape plus importante que les autres, c’est l’état des fichiers au moment de leur envoi pour relecture à ma directrice de thèse. Enfin, la fenêtre en bas indique sommairement les changements opérés entre les deux derniers dépôts : dans le fichier “2. 4. Actio, atteindre les lecteurices”, j’ai, apparemment, par exemple, changé un “oeuvre” en “œuvre”, et placé un italique autour du titre de l’œuvre *Antre.*

D’autres outils, à un niveau plus fin, permettent de comparer les versions. Un exemple en vidéo :


<video class="wp-video-shortcode" id="video-3959-1" preload="metadata" controls="controls"><source type="video/mp4" src="https://engagees.hypotheses.org/files/2023/01/Billet-Git-Usage-Meld-pour-comparer-des-changements-structurels.mp4?_=1" /><a href="https://engagees.hypotheses.org/files/2023/01/Billet-Git-Usage-Meld-pour-comparer-des-changements-structurels.mp4">https://engagees.hypotheses.org/files/2023/01/Billet-Git-Usage-Meld-pour-comparer-des-changements-structurels.mp4</a></video>

Dans cette capture vidéo de mon écran, vous pouvez voir à gauche l’ancienne version du fichier que j’ai demandé à examiner, à droite, la nouvelle. Au défilement, le logiciel tâche de faire coïncider les paragraphes qui sont identiques et souligne les différences d’une version à l’autre : il indique là où des paragraphes ont été ajoutés ou supprimés (le système dynamique des accolades permet de les visualiser, à partir de là il est facile de récupérer les éventuels textes perdus, ou bien de réévaluer la pertinence des changements apportés), et le logiciel permet aussi de voir dans le détail du texte ce qui y a été modifié (ici, en surligné clair ce qui se trouve “en plus” dans une version par rapport à l’autre).

Comme je l’évoquais plus haut, j’utilise notamment cet outil pour repérer facilement les différences entre une version du texte en travail et une version du texte envoyé à ma directrice de thèse : cela me permet de savoir ce dont je dois parler avec elle, ce que je dois souligner dans mon prochain envoi comme modification importante de mon texte.

![À gauche, la version relue par ma directrice de thèse, ses remarques apparaissant en code markdown sous la forme de commentaires, à droite, ma version (en partie) corrigée à partir de ces remarques. Les variations d’un document à l’autre apparaissent en surligné : phrases, mots, ponctuation… -- Capture d'écran de Meld](https://engagees.hypotheses.org/files/2023/01/Billet-Git-Comparaison-de-versions-pour-les-corrections.png)

J’utilise Meld pour logiciel de comparaison des versions, je trouverai peut-être mieux par la suite ; dans la capture d’écran postée ci-dessus, j’ai accentué les contrastes, qui sont moins évidents dans la véritable coloration du logiciel.

Voilà pour le fonctionnement général ! Maintenant, si c’est quelque chose qui vous paraît intéressant pour votre travail, quelques indications techniques sur le mode d’emploi.

Tuto pas à pas
----------

Pour les personnes qui souhaitent tenter l’utilisation de Git, tuto pas à pas. J’ai appris en le faisant de mon côté, je connaissais Git de nom auparavant mais sans savoir comment ça marchait exactement : ça fait un peu peur au début (surtout quand on n’a pas trop l’habitude de travailler en lignes de commande), mais en fait c’est toujours des mêmes commandes basiques qu’on a besoin, si bien qu’à l’usage c’est plutôt très simple à gérer. Pas de panique donc ! Je ne dirais vraiment pas que quelqu’un·e d’allergique à l’informatique peut s’y frotter, mais pour une utilisation basique il suffit d’avoir un peu envie d’expérimenter.

Attention quand même : *faites des sauvegardes* ; on peut faire des erreurs au démarrage, ce serait bête d’écraser des fichiers par erreur. J’ai une sauvegarde automatiquement sauvegardée sur Dropbox de mon côté.

**Attention** : *Hypothèses* transforme tous mes doubles tirets en tirets moyens, mais les commandes indiquées ci-dessous doivent bien, souvent, noter un double tiret.

### Initialisations

**Installations générales (à ne faire qu’une seule fois et pour toujours) :**

* **Git en ligne : le dépôt distant**. Il faut d’abord se créer un compte sur un serveur Git (GitLab ou GitHub…) : il existe différentes plateformes, aux politiques différentes selon les cas ; les personnes qui programment dans mon entourage ne jurent cependant que par [GitLab](https://gitlab.com/), j’ai donc choisi GitLab. C’est gratuit pour l’usage dont je parle ici, pas besoin du premium. Dans les préférences de votre compte, il faudra installer une clé SSH pour la ligne de commande (cela permet la mise en place du lien entre le dépôt en ligne et votre dossier local sur ordinateur) : les indications sont [ici](https://docs.gitlab.com/ee/user/ssh.html) ; il faudra lui trouver un nom, par exemple “Clé [Nom de l’ordinateur sur lequel vous travaillez]” (mon ordi à moi s’appelle Chronos 🤷). C’est la seule étape vraiment un peu compliquée si vous n’êtes pas expert·es en ligne de commande : faites comme moi, trouvez quelqu’un·e pour le faire à votre place.
* **Git chez vous : le dépôt local**. Vous devez installer le logiciel Git, qui fonctionne sur votre ordinateur (tous systèmes d’exploitation ok) en ligne de commande. Sur Ubuntu, installez gitg, qui permet de voir l’historique des fichiers (`sudo apt install gitg`). Sur Windows, à voir (une piste : gitkraken ?).
* **Votre identité**. Il va falloir donner votre identité à Git. La raison : Git étant un logiciel prévu au départ pour que des personnes puissent collaborer ensemble sur des mêmes fichiers, il exige de pouvoir identifier facilement qui a déposé quoi ; dans votre cas si l’usage est perso, vous pouvez mettre ce que vous voulez, peu importe. Pour ça, les commandes : `git config –global user.name “Prénom Nom”`, puis `git config –global user.email “prenom.nom@mail.com”`.
* **Logiciel d’édition** : par défaut, Git utilise Vim pour l’édition des textes, il est important de lui faire changer pour le bloc-notes, geany, gedit, ce que vous voulez[^1]. La ligne de commande est par exemple, dans mon cas, `git config –global core.editor “gedit -s”`
* **Logiciel de visualisation des différences** : beaucoup plus crucial dans le cas d’une utilisation pour la thèse, il faut changer le logiciel de visualisation des changements prévu par défaut, qui est plutôt adapté pour la visualisation de micro-changements entre deux fichiers que pour la gestion de texte long. Meld fonctionne relativement bien ; installez-le sur votre ordinateur ([ici la page du logiciel](https://meldmerge.org/)), puis paramétrez Git dans la console : `git config –global diff.tool meld`

Là, vous avez installé la base : vous pourrez utiliser Git pour tout ce que vous voudrez, la thèse, du code, un autre projet, etc. Ensuite, il faut paramétrer ces projets spécifiquement :

**Installation initiale du projet (à ne faire qu’une fois par projet, une fois pour toutes pour la thèse par exemple, donc) :**

* **Git en ligne : le dépôt distant**. Dans votre compte en ligne, créer le projet “Thèse” (ou tout autre titre plus fun si vous voulez), le paramétrer en privé évidemment (il me semble que c’est de toute façon le réglage par défaut). Quand il est créé, cliquer sur “Clone” et copier l’identifiant SSH.
* **Git chez vous : le dépôt local**. Ouvrir, à partir de la console, le dossier dans lequel vous voudrez que soit créé le dossier projet, celui qui sera synchronisé entre votre ordi et le dépôt en ligne. Par exemple, un dossier “Git” dans “Mes documents”. Ou, logiquement, le dossier dans lequel vous placez habituellement vos fichiers de rédaction. Puis, toujours dans la console, lancer `git clone [coller l’identifiant SSH]`

Là, le lien est fait entre vos dossier de thèse local et votre dépôt en ligne ; ce ne sera pas à refaire, c’est juste l’initialisation.

### Modifier et charger des versions de projet

![Capture d'écran de la console](https://engagees.hypotheses.org/files/2023/01/Billet-Git-Ouvrir-la-console-dans-le-dossier-du-projet-Git.png)

Ouverture de la console à partir du dossier où se trouve le projet Git dans mon navigateur de fichiers.

Git fonctionne intégralement en ligne de commande. Vous pouvez faire ce que vous voulez dans votre dossier, modifier les fichiers, en copier-coller, en supprimer, etc., tant que ça n’aura pas été formellement indiqué à Git, il ne l’aura pas enregistré et vous ne trouverez pas vos opérations sur le dépôt en ligne. Donc, après modifications, toujours penser à ouvrir Git : sur l’ordi, aller dans le répertoire du projet et l’ouvrir dans la console, tout se gère à partir de là.

**Mises à jour des versions**

* **Pour comprendre**. Git fonctionne avec certaines commandes de base :
  * Notamment “add” (`git add fichier.md`), qui sert à signaler à Git que les fichiers nommés devront être enregistrés lors de la prochaine sauvegarde dans l’historique des versions.
  * Et aussi “commit” qui lance une sauvegarde d’historique et, lorsqu’il est utilisé seul, ouvre un fichier avec le logiciel d’édition associé à Git, afin que l’utilisateurice y inscrive des informations sur les modifications apportées dans la sauvegarde en cours. Par exemple, Git enregistre “modifications sur chap1, ajout de la bibliographie”.
    * Fonctionnement standard, `git commit` : vous indiquez les infos dans le fichier qui s’ouvre (par exemple “ajout de la bibliographie”), enregistrez le fichier, et fermez[^2]. C’est tout bon pour Git.
    * Fonctionnement alternatif, `git commit -m “ajout de la bibliographie”` : il se passe exactement la même chose que dans le cas précédent pour Git, sauf que vous vous êtes épargné le passage par le logiciel d’édition.

* **Plus rapide et efficace, faire les deux d’un coup** : `git commit -am “Commentaire”` Dans ce cas, Git fait à la fois add et commit et inscrit le commentaire, c’est le plus simple. Attention cependant s’il y a dans votre dossier des fichiers qui sont nouveaux pour Git, faites d’abord l’étape “add”.

Quand vous avez “add” et “commit” les fichiers, Git a compris que vous aviez fait des modifications, que vous les avez validées et que vous êtes prêt·e à les synchroniser sur le dépôt en ligne. Il faut donc à partir de là **envoyer ces modifications sur le dépôt à distance** :

* Charger l’historique : `git push`
* Si jamais besoin de récupérer l’historique à partir du dépôt distant (dans l’hypothèse où vous changez d’ordinateur par exemple), faire venir les dernières versions, à partir du dépôt en ligne, sur votre ordi : `git pull`

La plupart du temps, un commentaire expliquant à quoi tient la modification des fichiers ou, dans le cas d’une thèse par exemple, à quelle étape vous avez fait la dernière validation d’historique (par ex. “V2 chap 2”, “écriture conclusion”), suffit en commit. Mais il peut être utile d’accentuer certains enregistrements particulièrement importants pour pouvoir y revenir facilement : vous avez la possibilité de **nommer certaines versions du projet, grâce à des tags**.

Typiquement, pour ce qui me concerne, je distingue les enregistrements standards (par exemple quand j’ai fini un chapitre, je mets à jour l’ensemble de mon projet en commentant “chap x achevé”, sans tag parce que ça reste le flux normal de la rédaction) des dépôts qui correspondent à un envoi de mes fichiers à ma directrice de thèse : eux, je les taggue (“envoi-partie-1-DT” par exemple), pour pouvoir facilement revenir à cette version-là pour comparer mes fichiers retravaillés avec ceux que je lui ai envoyés — c’est ce qui me permet de repérer très vite ce que je dois lui montrer comme évolution de mes chapitres.

Il faut donc éviter d’utiliser les tags trop souvent, mais ils sont utiles. Les tags, comme les fichiers, doivent être validés et chargés explicitement sur Git : `git tag envoi-partie-1-DT` par exemple, qui identifie la version du projet sur laquelle on est en train de travailler, puis `git push –tags` (bien le préciser, sinon, par défaut, les tags ne sont pas envoyés).

Autre cas de figure potentiellement utile, pour le cas où vous voulez **renommer des fichiers** : il est impératif de dire à Git que tel fichier x se nomme désormais y, sans quoi vous ferez vos modifs et réécritures sans qu’il les prenne jamais en compte. Il ne faut pas changer les noms de fichier dans le navigateur, mais utiliser `git mv “Ancien nom du fichier.md” “Nouveau nom du fichier.md”` Ces changements, comme toutes les modifications de fichier, doivent ensuite être “commited” et “pushed” sur le dépôt en ligne.

Là, c’est bon, vos dépôts et fichiers locaux sont synchros.

**Comparer les versions, vérifier où on en est**

![Exemple de commande `git status` : on voit ici que certains de mes fichiers présents dans le dossier local n’ont pas été “added” sur le dépôt en ligne. Je peux modifier ces fichiers tant que je veux en local, tant que je ne les aurai pas officiellement ajoutés à Git, ils ne seront pas suivis. -- Capture d'écran de la console](https://engagees.hypotheses.org/files/2023/01/Billet-Git-Git-status.png)

On en arrive au cœur de l’intérêt de Git, la comparaison des versions. D’abord, quelques commandes potentiellement utiles :

* `git status` : permet de voir si vous avez dans votre dossier local des fichiers modifiés qui n’ont pas encore été validés dans l’historique de Git (dans ce cas, passer par add, commit, push…).
* `gitg` : permet de visualiser facilement l’état de l’arborescence des versions (cf. exemple plus haut).

Pour pouvoir comparer des versions, il faut pouvoir **les identifier**. Chaque version du projet donne lieu à une chaîne de caractères automatique qui l’identifie, vous pouvez la retrouver grâce à la commande `git log` ou dans gitg : il vous faut la copier pour pouvoir ensuite indiquer à Git que vous souhaitez comparer votre version courante et cette version-là. Si vous avez utilisé des tags, le tag peut remplacer l’identifiant : d’où leur intérêt, ils simplifient la vie.

![Ici, par exemple, le git log du moment où j’écris : mon dernier enregistrement de version, que j’avais commenté “Début retravail partie 2” est identifié par le numéro 168dad6a679d9f6ed0846ea19f5ff276765ad8e5 (peu sexy). Le précédent, qui lui aussi a un identifiant très indigeste, avait été taggué par mes soins, “V1-Tomiche”, c’est indiqué sur la ligne d’identification du commit. Encore auparavant, j’avais déposé une V2 de mon chapitre 2, non taggée. -- Capture d'écran de la console](https://engagees.hypotheses.org/files/2023/01/Billet-Git-Exemple-git-log.png)

![Vous pouvez aussi trouver l’identifiant d’un commit sur la page GitLab du dépôt : cliquez sur le fichier qui vous intéresse, consultez son historique, l’identifiant est affiché à droite.](https://engagees.hypotheses.org/files/2023/01/Billet-Git-Recuperer-identifiant-dun-commit-sur-GitLab-e1674913909802.png)

Ensuite, vous pouvez utiliser gitg pour comparer les versions, ou le logiciel dédié à cet usage et adapté aux textes longs que vous avez paramétré sur votre ordinateur à l’étape “Initialisation” (moi c’est Meld) :

* Si vous n’avez pas de tag : `git difftool [premiers éléments du numéro du commit] “fichier.md”`
* Si vous comparez votre version courante à un enregistrement taggé : `git difftool nom-du-tag “fichier.md”`

Pour reprendre l’exemple de la capture d’écran : si je souhaite comparer ma version de travail actuelle et mon précédent dépôt, je pourrai utiliser les premiers numéros du dernier commit (“168dad6a679d9”, Git trouvera), ou bien si je veux comparer plutôt à ce que j’avais envoyé à ma directrice, je peux utiliser “V1-Tomiche”.

Si jamais, suite à une comparaison de fichiers, vous avez besoin de revenir à une ancienne version, vous pouvez utilise`r git checkout [premiers éléments du numéro du commit, par exemple 15ff7e10a48a]` ; cela échange les fichiers du projet avec une ancienne version, évitez de modifier les fichiers dans cet état-là, sinon les modifications risquent de disparaître. À éviter globalement, mais au pire Git envoie des avertissements si vous êtes sur le point de faire une bêtise (ouf). Vous pouvez revenir à votre version principale en utilisant `git checkout main`

***

Je pense que pour un usage tel que celui que je propose, pour une thèse, on n’a pas franchement besoin des commandes qui permettent aux programmeurs et programmeuses de gérer des arborescences de fichiers hyper complexes et de travailler en collaboration (enfin sauf si vous avez un·e DT hyper geek qui se met aussi à Git à la rigueur, mais bon…). Le système des embranchements (créer des branches puis les réunir pour travailler séparément sur deux aspects différents d’une réécriture) pourrait éventuellement être utile, ça ne paraît pas évident non plus, je n’ai pas encore creusé ! Le lien que je proposais en début d’article offre quelques pistes à ce sujet.

Attention aussi, je n’ai pas pris en compte ici le cas où vous travaillez sur différents ordinateurs, qui peut être plus compliqué à gérer : chaque machine correspondra à sa propre branche sur l’historique général, et il faudra pouvoir gérer la fusion des versions et leurs éventuels conflits (avec git pull, voir doc [par ici par exemple](https://git-scm.com/book/fr/v2/Les-branches-avec-Git-Branches-et-fusions%C2%A0%3A-les-bases)).

Du coup, **au quotidien, c’est vraiment assez basique** : j’écris, je change mes trucs, quand j’arrive à la fin d’une étape je “commit -am”, “push”, éventuellement je mets un tag, et puis quand j’ai des coups de stress et besoin de vérifier l’ancien état d’un chapitre je compare mes versions, ça reste relativement rare, c’est tranquille.

::: {.fin}
Citer cet article : Aurore Turbiau, "Rédaction : gérer les différences de versions avec Git", dans *Littératures engagées*, publié le 28/01/2023, [https://engagees.hypotheses.org/3959](https://engagees.hypotheses.org/3959), consulté le 21/09/2023.
:::

[^1]: Le risque si vous tombez sur Vim sans connaître, c’est de ne jamais pouvoir en sortir !! 

[^2]: Le fichier est temporaire, c’est juste un mode de fonctionnement de Git : vous ne le trouverez nulle part par la suite.
