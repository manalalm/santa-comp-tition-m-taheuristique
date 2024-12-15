# santa-comp-tition-m-taheuristique:
## Objectif :
L'objectif de cette compétition est de réorganiser des mots mélangés dans des passages d'histoires de Noël classiques afin de minimiser la perplexité du texte. La perplexité est une mesure qui indique à quel point un modèle trouve difficilement à prédire le texte suivant dans une séquence de mots. Moins la perplexité est élevée, plus le texte est fluide et compréhensible.
## Type de problème :
Ce problème peut être classé comme un problème d'optimisation combinatoire, plus précisément un problème de permutation avec une fonction objectif basée sur la perplexité.
(Problèmes combinatoires : Impliquent des variables discrètes ou entières, où les solutions possibles sont un ensemble fini ou dénombrable.)
## Fonction objectif (perplexité) :
•	L'objectif est de minimiser la perplexité, qui mesure la « confusion » du modèle quant à la séquence de mots générée. Une faible perplexité indique que la séquence est plus cohérente avec la langue naturelle, tandis qu'une grande perplexité suggère que la séquence est difficile à comprendre pour le modèle.
•	La perplexité est calculée par rapport au modèle de langage Gemma 2 9B, et l'objectif est de trouver la permutation des mots qui minimise cette valeur.
## Les contraintes :
•	La contrainte principale est que la séquence soumise doit être une permutation valide des mots de la séquence de base, c'est-à-dire que les mêmes mots doivent être présents, mais dans un ordre différent.
•	Unicité des mots : Aucun mot ne peut être répété ou omis dans la solution ; ont doit simplement réarranger les mots existants.
## La séquence :
La séquence fait référence à un ensemble ordonné de mots dans un passage d'un texte. Chaque passage (ou texte) donné est constitué d'une série de mots qui ont été mélangés, et votre tâche consiste à réorganiser ces mots dans un ordre logique et cohérent pour que le texte retrouve son sens initial.
## La solution :
La solution à ce problème est donc une permutation des mots de la séquence, qui représente l'ordre des mots qui donne la perplexité la plus faible. Cela signifie qu'il faut explorer différentes permutations et choisir celle qui maximise la fluidité du texte.
## Espace de solutions :
L'espace de solutions est l'ensemble de toutes les permutations possibles des mots dans la séquence donnée. Si la séquence contient N mots, l'espace de solutions contient N! (factorielle de N) permutations possibles.
## Complexité : O(N !)
## Comment changer les solutions (se déplacer)
Pour explorer l'espace de solutions, vous pouvez modifier la solution actuelle en effectuant des mouvements. Ces mouvements sont les suivantes :
•	Swap (échange de deux mots) : Vous pouvez échanger deux mots dans la séquence. Cela modifie l'ordre sans violer la contrainte de permutation.
•	Insertion : Vous pouvez déplacer un mot d'une position à une autre dans la séquence.

#  Métahuristique à appliquer
## Algorithmes génétiques (Genetic Algorithms) :
Les algorithmes génétiques sont adaptés aux problèmes de permutation. Ils utilisent des opérateurs comme la mutation (échanger des mots), le croisement (combiner des permutations) et la sélection (choisir les meilleures permutations) pour explorer l'espace des solutions de manière efficace.
• Exploration : L'exploration est gérée par des opérateurs de croisement (crossover) et de mutation qui créent de nouvelles solutions en combinant des parents de manière aléatoire.
• Exploitation : L'exploitation est effectuée via la sélection où les meilleures solutions (les plus proches du minimum de perplexité) sont plus susceptibles d'être sélectionnées pour la reproduction, et donc pour générer des solutions futures. Par ailleurs, la mutation dans les GAs introduit de la diversité, ce qui permet également un certain niveau d'exploration même à des stades avancés.
## Exploration et Exploitation dans les Algorithmes Génétiques (GA)
Exploration : Chercher de nouvelles solutions
•	Exploration dans le contexte des algorithmes génétiques fait référence à la capacité de l'algorithme à explorer un espace de solutions large et diversifié, en générant de nouvelles solutions, souvent loin des solutions précédentes. Cela permet à l'algorithme d'éviter de se retrouver piégé dans des minima locaux (c'est-à-dire des solutions qui sont bonnes mais qui ne sont pas optimales globalement).
o	Mutation : C’est un opérateur utilisé pour introduire de la diversité dans la population d'individus (solutions). La mutation modifie aléatoirement un individu de la population. Par exemple, dans le cadre du réarrangement de mots dans une séquence, cela pourrait consister à échanger aléatoirement deux mots de la séquence. Cela permet à l'algorithme d'explorer de nouvelles régions de l'espace des solutions. Même si l'algorithme a trouvé de bonnes solutions, la mutation permet de tester des solutions radicalement différentes.
o	Croisement (Crossover) : Le croisement consiste à combiner deux solutions (individus) pour créer de nouvelles solutions. Par exemple, dans le cas de la permutation de mots, le croisement pourrait impliquer de mélanger deux séquences de mots pour créer une nouvelle séquence. Cette méthode permet également d'explorer de nouvelles combinaisons de solutions en combinant les caractéristiques de deux parents.
Exploitation : Affiner les bonnes solutions
•	Exploitation fait référence à la capacité de l'algorithme à concentrer ses efforts sur les solutions prometteuses. Cela implique d’améliorer et d'affiner les solutions qui semblent proches de l'optimum global.
o	Sélection : Dans un algorithme génétique, les solutions sont sélectionnées en fonction de leur qualité (par exemple, la perplexité dans ce cas). Les solutions les plus proches de l'optimum (les meilleures) ont plus de chances d'être choisies pour générer les prochaines solutions. Cela permet d'exploiter les meilleures solutions trouvées jusqu'à présent pour en générer de nouvelles versions potentiellement améliorées.
o	Exploitation et croisement : Lors du croisement, on favorise souvent des solutions qui sont déjà proches de l'optimum. Par exemple, on peut mélanger deux solutions qui ont des qualités similaires, dans l'espoir de combiner leurs forces et d'améliorer encore la solution. Cela est une forme d'exploitation, car l'algorithme se concentre sur les solutions qui sont déjà bonnes.

## Comment cela fonctionne dans un Algorithme Génétique :
1.	Initialisation : Au début de l'algorithme, une population aléatoire de solutions est générée.
o	Ces solutions sont diverses, ce qui favorise l'exploration (c'est-à-dire qu'on n'a pas encore d'idées précises sur ce qui fonctionne bien).
2.	Sélection : À chaque itération, on sélectionne les meilleures solutions de la population actuelle, celles qui sont les plus proches de l'optimum.
o	Ces solutions sont exploitées (on se concentre sur les meilleures solutions existantes).
3.	Croisement et Mutation :
o	Croisement (Exploration) : On prend deux de ces bonnes solutions et on les combine pour produire de nouvelles solutions (crossover). Cela permet d'explorer de nouvelles solutions.
o	Mutation (Exploration) : Après le croisement, on peut appliquer une mutation à une solution pour encore introduire de la diversité et explorer des solutions radicalement différentes.
4.	Nouveaux individus : Les nouvelles solutions obtenues par croisement et mutation sont ajoutées à la population. L'algorithme va à nouveau sélectionner les meilleures solutions (exploitation), mais cette fois-ci parmi une population mise à jour qui a plus de diversité grâce à l'exploration.
Les paramétres a optimiser :
