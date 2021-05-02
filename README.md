# Kaggle_Competition_Reddit
Predicted the popularity of a Reddit comment using text analysis (NLP) and network mining

## Project description

1. Architecture
Cette archive est constitué :
	- d'un dossier Notebooks contenant nos différents codes avec :
		-handling_body implémentant des features textes (sur la variable body)
		-handling_links implémentant des features réseaux en fonction des variables name, link_id et parent_id
		-handling_merged implémentant les features textes et réseaux utilisées précédemment
		-handling_authors implémentant des features réseaux en fonction de la variable author
	

2. Exécution
	Exécuter handling_body et handling_links avant les deux autres

3. Features
Voici la liste des différentes features implémentées et l'intuition transmise

features textes :
	-Analyse de sentiments : un texte contient un sentiment en fonction de deux critères, la subjectivité (intensité de l'opinion de l'auteur) et la polorité (le niveau de l'émotion transmise)
				Donc plus un message est subjectif et dégage un sentiment positif, plus il est susceptible d'avoir un bon score
	-Recherche de topics : un commentaire peut appartenir à plusieurs topics, donc plus il est étendu, plus il a un bon score

features réseaux :

Construction du graphe: On a considéré un graphe dirigé où les noeuds sont représentés par la variable name et la variable link_id, et les arcs sont représentés par la variables parent_id. 
			Nous considérons qu'un noeud pointe vers un autre noeud si celui-ci est égal à son parent_id. 
	
	- Successeurs : Il calcule le degré sortant de chaque noeud. Du fait qu'un commentaire ne peut pas repondre à plus d'un commentaire alors cette variable vaut 0 ou 1. 
	-Calcul de centralité :
		- degré : Même idée que les successeurs.
		- Proximité : évalue comment accéder à un nombre de commentaire à partir d'un commentaire donné. On part de l'intuition que plus un noeud (commentaire) est proches à un grand nombre 
		 	      de commentaires plus son score est élevé. 
		- Vecteur propre : On part de l'intuition que plus est noeud est connecté à un grand nombre de noeuds qui ont un bon score plus son score sera élevé. 
	-Cacul de prestige : On utilise la notion de prestige au sein de l'algorithme du PageRank, plus un noeud est prestigieux, plus le score est élevé.
				Un noeud est prestigieux s'il pointe vers beaucoup de noeuds et si les noeuds qui pointent vers lui sont eux-mêmes prestigieux.
	
