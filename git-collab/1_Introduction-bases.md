# DQPRM 2026-208

## A la (re)découverte de Python

#### Albertine Dubois - albertine.dubois@cea.fr, Ludovic Ferrer - Ludovic.Ferrer@ico.unicancer.fr & Marion Savanier - marion.savanier@cea.fr

Version 2026

---

* Travail en groupe 

## Présentation et objectifs

* Python est un langage de programmation **open source** et **gratuit**, très largement utilisé dans le monde de la recherche pour le traitement de données scientifiques, le développement d'applis web, l'administration système, le prototypage, ...

* Il permet de tester très rapidement des traitements informatiques et d'analyser rapidement et de manière reproductible ses données (ses images notamment).

* Enseigné partout, il est idéal pour des débutants comme pour des developpeurs confirmés.

* Son inventeur est Guido van Rossum, informaticien hollandais. Projet personnel débuté en 1989 avec pour objectif de créer un langage de programmation **facile à apprendre**, doté d'une **syntaxe intuitive** et **puissant**.

L'objectif de ce cours est de (re)découvrir les grands concepts de la programmation en Python en observant le résultat de diverses fonctions. Nous avons essayé de ne présenter que le strict nécessaire pour bien débuter avec Python. N'hésitez pas à tester autre chose !

Si vous souhaitez un descriptif plus spécifique d'une fonction, tapez : `help nom_de_la_fonction`

L’aide est généralement très bien faite lorsqu’on connaît la fonction à utiliser ; c’est plus difficile si on ne connaît pas le nom de la fonction de trouver comment faire. Prenez le réflexe de poser votre question à Google. Il est fort probable que quelqu'un ait posté la réponse.

Et pour ceux qui voudraient aller plus loin avec Python, nous vous recommandons de suivre ce [MOOC](https://www.fun-mooc.fr/courses/course-v1:UCA+107001+session02/about).

<center>
<img witdh=500 src='./data/python.jpeg'>
</center>

Ce notebook d'introduction à la programmation en Python est découpé en 6 parties :

*   <a href="#part1">1. Quelques bases indispensables pour bien démarrer avec Python</a>
*   <a href="#part2">2. Faire du calcul scientifique avec Python</a>
*   <a href="#part3">3. Tracer des courbes en 2D, des histogrammes, des surfaces et afficher des images</a>
*   <a href="#part4">4. Lire et manipuler des fichiers Excel ou csv</a>
*   <a href="#part5">5. Exporter ses données sous forme de graphique</a>
*   <a href="#part6">6. Faire des statistiques avec Python</a>

## Préambule

*   Python est un langage interprété, pas besoin de phase de compilation comme en C ou java ; `python3` est l'interpréteur.

*   On peut utiliser ce langage selon 2 modes : **interactif** (calculette) et **script** (programme).

Pendant toute la durée de cet optionnel, nous allons travailler avec des *Jupyter Notebook* comme celui-ci, qui fonctionnent en mode interactif. Vérifiez en haut à droite que vous êtes bien en Python 3. Si ce n'est pas le cas, allez dans la barre de menu, sélectionnez "Kernel", puis "Change Kernel" et choisissez "Python 3".

La cellule est l'élement avec lequel vous intéragissez au sein de votre notebook. Elle permet aussi bien de rentrer du code dans un langage informatique comme `python` ou bien du texte que l'on peut formater selon un langage à balises simples nommé [*Markdown*](http://fr.wikipedia.org/wiki/Markdown). Cela permet de simplifier l'écriture de texte pour les pages de texte affichées dans un navigateur internet.

La bascule d'un mode à l'autre se fait par l'intermédiaire du bouton à menu déroulant `Code`. Il suffit de sélectionner la ligne *Markdown* pour pouvoir éditer du texte ou bien *Code* pour entrer du code.

Pour executer le contenu d'une cellule, il faut cliquer sur le bouton <button class='btn btn-default btn-xs'><i class="fa fa-play icon-play"></i></button> de la barre d'outil ou bien taper la combinaison de touches `Shift+Enter`

**Top, non ? On essaie ?**

Exécutez cette cellule pour lui redonner son apparence initiale si vous avez double-clické dessus, puis exécutez la cellule suivante.

Dans cette cellule, je mets du texte qui va s'afficher comme du texte.

Dans la cellule suivante, j'affiche du texte avec Python à l'aide de la fonction `print`


```python
print("Coucou les futurs physiciens médicaux")
```


```python
from platform import python_version
print("Version de Python utilisée durant cet optionnel :",python_version())
```


```python
# Ceci est un commentaire
a = input("Nombre d'étudiants inscrits à l'INSTN : ")
b = input("Nombre d'étudiants inscrits au DQPRM : ")
n = 100*(b/4)
print("Les étudiants inscrits au DQPRM représentent", n, "% de la totalité des étudiants inscrits à l'INSTN")
```

Oups ! `a` et `b` sont des chaines de caractères (`str`), donc l'opération `a+b` concatène ces chaînes

Solution:  `a = int(input(...))` et idem pour `b`


```python
a = int(input("Nombre d'étudiants inscrits à l'INSTN : "))
b = int(input("Nombre d'étudiants inscrits au DQPRM : "))
n = 100*(b/a)
print("Les étudiants inscrits au DQPRM représentent", n, "% de la totalité des étudiants inscrits à l'INSTN")
```

## <a name="part1"></a> 1. Quelques bases indispensables pour bien démarrer avec Python

### 1.1 Variables

Pas de déclaration, créée par simple **affectation**.


```python
a = 5
print("la valeur de a est :",a)
print(a+3)
a = a*2
print(a)
#a++ # Syntax error
a += 1
print(a)
```

*  Nom de variable : 1 lettre + 0 ou plusieurs {lettre,chiffre}
* Exemple : a, x1, couleur, nb_formes
*  Sensible à la casse, lettres accentuées possibles


```python
cafe = "froid"
Cafe = "chaud"
café = "moulu"
print(cafe, Cafe, café)
```

/!\ Bon usage : éviter de commencer un nom de variable avec une majuscule ou _

*   **Type selon contenu :** concept de "typage dynamique"


```python
a = 5
print(type(a))

a = 2.5
print(type(a))

a = False
print(type(a))

a = "toto"
print(type(a))

# Vérification
print(type(a) == str) # Ici, le signe double égal == correspond à un test. C’est différent d’une affectation
```

*   **Transformations de types :**


```python
str(5)
```


```python
int(2.5)
```


```python
float("3.14")
```


```python
int(True)
```


```python
int("toto")
```

*   **Mélanges de types :**


```python
type(2+3.14)    # <class 'float'> : type plus général
```


```python
type(2+True)    # <class 'int'>
```


```python
type(2+"toto")  # TypeError: unsupported operand type(s) for +: 'int' and 'str'
```


```python
type(2*"hop")   # <class 'str'>
print(2*'hop')
```

----
**Conclusion :**

  *  On ne déclare pas les variables
  *  Le type de la variable est le type de sa valeur courante
  *  On a vu les types : `int`, `float`, `bool`, `str`
  *  Il y a beaucoup d'autres types en Python qu'on appelle des structures de données (certains seront vus plus tard) : tuples, listes, ensembles, dictionnaires, tableaux, classes...
----

### 1.2 Opérations de comparaison



```python
# Variable x dont la valeur est 10 et variable y dont la valeur est 3
x = 10
y = 3
print("x =",x, "y =",y)

# Egal
print ("Egal, x == y ", x == y)

# Différent
print ("Différent, x != y ", x != y)

# Inférieur
print ("Inférieur, x < y ", x<y)

# Supérieur
print ("Supérieur, x > y ", x>y)

# Inférieur ou égale
print ("Inférieur ou égale, x <= y ", x<= y)
```


```python
A = 2.1
B = 5
C = 2.1

E = str('5')
F = str('5')
print(type(E))

print(A == B)
print(A == C)
print(A is C)
print(E is F)
```

### 1.3 Opérations d'affectation

* `z = x + y` met la valeur de `x + y` dans `z`

* x += y est équivalent à x = x + y

* x *= y est équivalent x = x * y



```python
# Variable x a la valeur 10 and la variable y a la valeur 3
x = 10
y = 3
print("x =",x, "y =",y)

print("Valeur après x+y : ", x+y)

print("Valeur après x*y : ", x*y)

print("Valeur après 2*x*y : ", 2*x*y)

x += y
print("Valeur après x+=y : ", x)

x *= y
print("Valeur après x*=y : ", x) # multiplication

x /= y
print("Valeur après x/=y : ", x) # division

x %= y
print("Valeur après x%=y : ", x) #reste de division entière

x **= y
print("Valeur après x**=y : ", x) #puissance

x //= y
print("Valeur après x//=y : ", x) #quotient de division entière
```

### 1.4 Opérations logiques


```python
var1 = True
var2 = False
print('var1 ET var2 :',var1 and var2)
print('var1 OU var2 :',var1 or var2)
print('NON var1 :',not var1)
```

### 1.5 Entrées Sorties



```python
print("bonjour")
a = 2 ; b = 3
print("mangez", a, "pommes et", b, "poires")
print("mangez", a, "pommes et", b, "poires", sep="--")
print("mangez", a, "pommes et", b, "poires", end="--")  # par défaut \n
help(print)

a = input()
b = input("poires : ")
print(type(b))                         # str : input() renvoie toujours un str
b = int(input("poires : "))
print(type(b))
```

### 1.6 Blocs d'instructions

*  Blocs d'instructions non délimités par { } ou begin end comme en C, java, Pascal

*  Blocs définis par l'indentation :
    *  des lignes qui se suivent avec même indentation forment un bloc
    *  une instruction nécessitant un sous-bloc est terminé par ":"
        *  un sous-bloc a une indentation plus grande
        *  en général on indente de 4 espaces
* Le premier bloc a une indentation de 0


```
instruction1
instruction2
instruction3 nécessitant un sous-bloc :
    instruction4
    instruction5 nécessitant un sous-bloc :
        instruction6
        instruction7
    instruction8
instruction9
```

*  Structures de contrôle nécessitant un sous-bloc : conditionnelle, boucle, fonction

* Possibilités de mettre une instruction sur plusieurs lignes, vues plus tard


**Exemple :** Ecrire un programme qui génère aléatoirement un entier et qui affiche s'il est postif ou négatif.

*  Indentation incorrecte :


```python
import random # Module permettant de tirer des nombres aléatoires
x = random.randint(-100,100) # Fonction du module random renvoyant un nombre entier tiré aléatoirement entre -100 inclus et 100 inclus
print("x =",x)
if x >=0:
    print('x is postive')
else:
    print('x is negative')
```

*  Indentation correcte :


```python
import random
x = random.randint(-100,100)
print("x =",x)
if x >=0:
    print('x is postive')
else:
    print('x is negative')
```

### 1.7 Structure Conditionnelle `if`

```
if condition1 :
        bloc1
```

ou
```
if condition1 :
        bloc1
else :
        bloc2
```




```python
nb_pommes = 5
fruit = input("Entrez un fruit : ")
if fruit == "pomme" :
    nb_pommes += 1
    print("Il y a", nb_pommes, "pommes.")
else :
    print("Je ne connais pas ce fruit.")
```


```python
chaine1 = "PoMmE"
chaine2 = "AZpoMMes"
chaine3 = "pome"
```


```python
chaine1_upper = chaine1.upper()
chaine2_upper = chaine2.upper()
chaine3_upper = chaine3.upper()

print(chaine1_upper, "POMME" in chaine1_upper)
print(chaine2_upper, "POMME" in chaine2_upper)
print(chaine3_upper, "POMME" in chaine3_upper)
```


```python
print(chaine1_upper in "POMME")
```

On peut imbriquer les structures conditionnelles :


```python
nb_pommes = 5 ; nb_poires = 8 ; nb_bananes = 2
fruit = input("Entrez un fruit : ")
if fruit == "pomme" :
    nb_pommes += 1
    print("Il y a", nb_pommes, "pommes.")
else :
    if fruit == "poire" :
        nb_poires += 1
        print("Il y a", nb_poires, "poires.")
    else :
        if fruit == "banane" :
            nb_bananes += 1
            print("Il y a", nb_bananes, "bananes.")
        else :
            print("Je ne connais pas ce fruit.")
```

Syntaxe pour désimbriquer :



```
if condition1 :
        bloc1
elif condition2 :
        bloc2
elif condition3 :
        bloc3
...
else :
        blocn

```




```python
nb_pommes = 5 ; nb_poires = 8 ; nb_bananes = 2
fruit = input("Entrez un fruit : ")
if fruit == "pomme" :
    nb_pommes += 1
    print("Il y a", nb_pommes, "pommes.")
elif fruit == "poire" :
    nb_poires += 1
    print("Il y a", nb_poires, "poires.")
elif fruit == "banane" :
    nb_bananes += 1
    print("Il y a", nb_bananes, "bananes.")
else :
    print("Je ne connais pas ce fruit.")
```

**Remarque :**
*  Un sous-bloc doit comporter au moins une instruction, sinon `pass`


```python
x = int(input("Donnez un nombre entier : "))
if x % 2 == 0 :
    pass
else :
    print("x est impair")
```

On aurait pu écrire plus simplement :


```python
if not (x % 2 == 0) :
    print("x est impair")
```

### 1.8 Boucle while

```
while condition1 :
        bloc1
```

**Exemple :** calculer la somme des entiers de 1 à n


```python
i = 1 ; n = 10 ; somme = 0
while i <= n :
    somme += i
    print("somme =",somme)
    i += 1    # en mode interactif sauter 1 ligne pour sortir du bloc
    print("i =",i)
print ("Le résultat est", somme)
```

**Exemple :** calculer les 10 premières puissances de 2


```python
i=1
while i < 1000:
    i = i*2
    print(i)
```

### 1.9 Boucle `for`
Boucle `for` très différente du C :

    for variable1 in expression1 :
        bloc1

`expression1` est de n'importe quel type "itérable" ;
`variable1` prend successivement les valeurs de chaque élément de `expression1`.


```python
for i in (7, 4, "oui") :
        print(i)
```


```python
for c in "plop" :
        print(c)
```

Comment faire une boucle sur un intervalle, comme en C ? Avec la classe **range**


```python
for i in range(1,10) : # i varie de 1 à 10-1=9
    y = i**2
    print(i, y)
```

On peut changer l'incrément :


```python
for i in range(1,10,3) :
    print(i)              # 1 4 7 : i avance de 3 en 3
```

**Exemple :**


```python
for i in range(10): # i varie de 0 à 10-1=9
    if i < 5:
        y=i**2
        print(y)
```

* Usage :
    * Boucler de `a` à `b` inclus dans le sens croissant : `range(a, b+1)`
    * Boucler de `b` à `a` inclus dans le sens décroissant : `range(b, a-1, -1)`

### 1.10 Fonctions


Déclarer une fonction :

    def nom_fonction (paramètre1, paramètre2, ...) :
        bloc1

Appeler la fonction :

    nom_fonction (valeur1, valeur2,...)
ou  

    résultat = nom_fonction (valeur1, valeur2,...)

Dans le bloc principal de la fonction :
    `return` ou `return valeur`
sort immédiatement


**Exemple :** écrire une fonction qui calcule, pour un paramètre `n` donné, la somme des `n`  entiers de `1` à `n`.


```python
# Déclaration de la fonction
def calculer_somme (n) :
    """
    calculer la somme
    args:
        n: int
    """
    i = 0
    somme = 0
    while i <= n :
        somme += i
        i += 1
    return somme

# Appel de la fonction
s = calculer_somme (100)
print ("Le résultat est", s)
```


```python
calculer_somme?
```

Portée des variables :
   *  Les paramètres et variables internes à la fonction sont locaux
   *  Lors de la fonction pas d'accès aux variables `n`, `i`, `somme`

Une fonction peut renvoyer plusieurs valeurs :


```python
def saisir_nom_prenom_age () :
    nom = input("Nom = ")
    prenom = input("Prénom = ")
    age = int(input("Age = "))
    return (nom, prenom, age)

n, p, a = saisir_nom_prenom_age()

print(a)
print(p)
print(n)
```

### 1.11 Listes et dictionnaires

* Une liste est une structure de données qui contient une série de valeurs.

* Python autorise la construction de liste contenant des valeurs de types différents (par exemple entier et chaine de caractères), ce qui leur confère une grande flexibilité.

* Une liste est déclarée par une série de valeurs, séparées par des virgules et le tout encadré par des crochets.


```python
stages = ['radiologie', 'médecine nucléaire', 'radiothérapie']
durée = [3, 3, 12]
```

Un des gros avantages d'une liste est que vous pouvez appeler ses éléments par leur position. Ce numéro est appelé **indice** (ou *index*) de la liste.

Soyez très attentifs au fait que les indices d'une liste de $n$ éléments commencent à $0$ et se termine à $n-1$. On dit aussi qu'en Python, les éléments d'une liste sont indexés à partir de $0$.


```python
stages[0]
```


```python
stages[3] #3 élements seulement dans cette liste, il n'y a donc pas d'élément d'indice 3
```

Une liste peut être indexée avec des nombres négatifs. C'est parfois pratique pour identifier la valeur du **dernier élément** d'une liste.


```python
print(stages[-1], stages[-2])
```

Les dictionnaires sont des collections non ordonnées d'objets (i.e pas d'indice). On accède aux **valeurs** d'un dictionnnaire par des **clés**.


```python
stages = {} # dictionnaire vide
stages["radiologie"] = 3
stages["médecine nucléaire"] = 3
stages["radiothérapie"] = 6
stages
```

Ici, on a rempli le dictionnaire avec différentes clés ("physique nucléaire", "dosimétrie", "radiobiologie") auxquelles on a affecté des valeurs (9, 3, 6).

Il est possible d'obtenir toutes les valeurs d'un dictionnaire à partie de ses clés.


```python
for key in stages:
    print(key, stages[key])
```

----
**<span style='color:red'>Rendez-vous à l'exercice 1 du notebook `Exercices.ipynb` pour une mise en pratique**</span>

----

## <a name="part2"></a> 2. Faire du calcul scientifique avec Python

### 2.1 Manipulation de vecteurs et de matrices avec NumPy

* [NumPy](https://numpy.org/) est une bibliothèque sous Python destinée à manipuler des **vecteurs**, des **matrices** ou plus généralement des **tableaux multidimensionnels**.
* Elle permet d'effectuer des calculs sur ces tableaux, **élément par élément**, via un nouveau type d'objet appelé `array`.
* Elle intègre également un grand nombre de fonctionnalités mathématiques.

<center>
<img src="./data/numpy_array_t.png" width="600pxl">
</center>

Voici quelques attributs intéressants pour décrire un objet de type `array` :

* `.ndim` renvoie le **nombre de dimensions** (par exemple, 1 pour un vecteur et 2 pour une matrice)
* `.shape` renvoie les **dimensions** sous forme d'un tuple. Dans le cas d'une matrice (array à deux dimensions), la première valeur du tuple correspond au nombre de lignes et la seconde au nombre de colonnes
* `.size` renvoie le **nombre total d'éléments** contenus dans l'array

Importez le module `numpy` pour pouvoir l'utiliser dans la suite du notebook.


```python
import numpy as np # On définit ici un nom raccourci (ou alias) pour numpy
print("Version de NumPy utilisée durant cet optionnel :",np.__version__)
```

### 2.2 Vecteurs

* Définir un vecteur



```python
# définir un vecteur
v = np.array([1, 2, 3])
print(v)
print(type(v))
```

* Addition


```python
# définir un premier vecteur
a = np.array([1, 2, 3])
print(a)
# définir un second vecteur
b = np.array([1, 2, 3])
print(b)
# addition
c = a + b
print(c)
```

* Soustraction


```python
# définir un premier vecteur
a = np.array([1, 2, 3])
print(a)
# définir un second vecteur
b = np.array([2.5, 2.5, 2.5])
print(b)
# soustraction
c = a - b
print(c)
```

* Multiplication (élément par élément)


```python
# définir un premier vecteur
a = np.array([1, 2, 3])
print(a)
# définir un second vecteur
b = np.array([1, 2, 3])
print(b)
# multiplication
c = a * b
print(c)
```

* Division


```python
# définir un premier vecteur
a = np.array([1, 2, 3])
print(a)
# définir un second vecteur
b = np.array([1, 2, 3])
print(b)
# division
c = a / b
print(c)
```

* Multiplication vecteur-scalaire


```python
# définir un vecteur
a = np.array([1, 2, 3])
print(a)
# définir un scalaire
s = 0.5
print(s)
# multiplication vecteur-scalaire
c = s * a
print(c)
```

* Accéder aux différents éléments d'un vecteur à l'aide de ses indices (positifs ou négatifs)

<center>
<img src="./data/array1.png" width="400pxl">
<img src="./data/array1bis.png" width="400pxl">
</center>

* Ne sélectionner qu'une partie d'un vecteur (concept de tranche ou *slicing*)

<center>
<img src="./data/array3.png" width="400pxl">    
<img src="./data/array4.png" width="400pxl">        
<img src="./data/array5.png" width="400pxl">      




```python
t = np.arange(-5,5) # Fonction définissant un vecteur d'entiers de -5 à 5
print('Valeurs de t =',t)
print('Deuxième élément :',t[1])
print('Dernier élément :',t[-1])
print('Cinq premiers éléments :',t[:5])
```


```python
f = np.linspace(3,2,23) # Fonction renvoyant 23 éléments régulièrement espacés entre 3 et 2, 3 et 2 inclus
print('Valeurs de f =',f)
print('Neuvième élément :',f[10])
```


```python
# Renvoie des éléments d'un array satisfaisant une condition
print(t)
print([t==0])
print(t[t==0])
print(t[t<3])

print()

# Ci-dessous la condition sur t définit certains indices de f
print(f[t[t==0]]) # Equivaut à f[0]
print(f[t[t<3]])  # Equivaut à np.array([f[-5],f[-4],f[-3],f[-2],f[-1],f[0],f[1],f[2]])
```

### 2.2 Matrices

Avant de continuer, il est important de bien comprendre comment sont organisés les arrays 2D qui représentent des matrices.

Il s'agit de tableaux de nombres qui sont organisés en lignes et en colonnes comme le montre la figure ci-dessous.

<center>
<img src="./data/matrice.png" width="400">
</center>

* Définir une matrice


```python
# création d'une matrice
A = np.array([[1, 2],[3,4], [5, 6]])
print(A)
print(type(A))
```


```python
print(A.ndim) # Dimension
print(A.size) # Nombre total d'éléments
print(A.shape) # Nombre de lignes et de colonnes (dans cet ordre)
```

* Addition


```python
# définir une première matrice
A = np.array([
[1, 2, 3],
[4, 5, 6]])
print(A)
# définir une seconde matrice
B = np.array([
[1, 2, 3],
[4, 5, 6]])
print(B)
# addition
C = A + B
print(C)
```

* Soustraction


```python
# définir une première matrice
A = np.array([
[1, 2, 3],
[4, 5, 6]])
print(A)
# définir une seconde matrice
B = np.array([
[0.5, 0.5, 0.5],
[0.5, 0.5, 0.5]])
print(B)
# soustraction
C = A - B
print(C)
```

* Multiplication (produit de Hadamard)


```python
# définir une première matrice
A = np.array([
[1, 2, 3],
[4, 5, 6]])
print(A)
# définir une seconde matrice
B = np.array([
[1, 2, 3],
[4, 5, 6]])
print(B)
# multiplication
C = A * B
print(C)
```

* Division


```python
# définir une première matrice
A = np.array([
[1, 2, 3],
[4, 5, 6]])
print(A)
# définir une seconde matrice
B = np.array([
[1, 2, 3],
[4, 5, 6]])
print(B)
# division
C = A / B
print(C)
```

* Multiplication (produit matriciel)


```python
# définir une première matrice
A = np.array([
[1, 2],
[3, 4],
[5, 6]])
print(A)
# définir une seconde matrice
B = np.array([
[1, 2],
[3, 4]])
print(B)
# multiplication matricielle
C = A.dot(B)
print(C)
# multiplication matricielle avec @
D = A @ B
print(D)
```

* Multiplication matrice-vecteur


```python
# définir une matrice
A = np.array([
[1, 2],
[3, 4],
[5, 6]])
print(A)
# définir un vecteur
B = np.array([0.5, 0.5])
print(B)
# multiplication vecteur-matrice
C = A.dot(B)
print(C)
```

* Multilication matrice-scalaire


```python
# définir une matrice
A = np.array([[1, 2], [3, 4], [5, 6]])
print(A)
# définir un scalaire
b = 0.5
print(b)
# multiplication matrice-scalaire
C = A * b
print(C)
```

* Matrices utiles


```python
Z = np.zeros((2,4))
print(Z,'\n')
U = np.ones((5,3))
print(U,'\n')
# matrice identité
I = np.identity(3)
print(I,'\n')
# un equivalent
J = np.eye(5)
print(J)
```

* Accéder aux différents éléments d'une matrice à l'aide de ses indices (positifs ou négatifs)

<center>
<img src="./data/array2.png" width="400"> <img src="./data/array2bis.png" width="400">
</center>

* Ne sélectionner qu'une partie d'une matrice (concept de tranche ou *slicing*)

<center>
<img src='./data/array7.png' width="400">  <img src='./data/array6.png' width="400">    
</center>


```python
M = np.array([[1,2,3,4,5,6],[10,20,30,40,50,60],[11,22,33,44,55,66]])
print(M,'\n')
print(M.shape,'\n')

print(M[1,3],M[2,1],'\n') # donne les éléments sur la ligne 1/2 et la colonne 3/1 donc ici 40 et 22

print(M[1,:],'\n') # deuxième ligne, donc ici array([10, 20, 30, 40, 50, 60])

print(M[:,3],'\n') # quatrième colonne, donc ici array([4, 40, 44])

print(M.max(),'\n') # élément de valeur maximale

N = M[0:2,2:] # deux premières lignes et quatre dernières colonnes
print(N)
```


```python
print(M,'\n')

M[M<4] = M[M<4]+10 # Remplace tous les éléments de la matrice satisfaisant cette condition par leur valeur + 10

print(M,'\n')
print(M>23,'\n') # Retourne True si la condition est satisfaite, False sinon

print(M[M>23],'\n') # Renvoie dans un array les éléments de la matrice satisfaisant la condition
```


```python
M[M>50] = 100 # Affecte la valeur 100 aux éléments de la matrice qui satisfont la condition
print(M)
```


```python
M[M == 22] = 99 # Affecte la valeur 99 aux éléments de la matrice qui satisfont la condition
print(M)
```

## <a name="part3"></a> 3. Tracer des courbes en 2D, des histogrammes, des surfaces et afficher des images

### 3.1 Matplotlib : librairie permettant de tracer des graphes (dans le sens graphiques)

[Matplotlib](https://matplotlib.org/) est une excellente librairie graphique (inspirée de Matlab au départ) pour générer des figures scientifiques en 2D et 3D. Parmi les avantages de cette librairie, on peut citer :

* Une prise en main facile
* Des figures de haute qualité et plusieurs formats PNG, PDF, SVG, EPS etc.
* Le texte qui peut être formatté en Latex

Matplotlib rend ainsi possible la création de graphes à l'intérieur d'applications complexes autorisées par le langage Python, et ceci sans quitter le langage Python.



Importez le module `matplotlib` pour pouvoir l'utiliser dans la suite du notebook.


```python
import matplotlib
print("Version de Matplotlib utilisée durant cet optionnel :",matplotlib.__version__)
import matplotlib.pyplot as plt
# affichage des graphiques sur Jupyter notebook
%matplotlib inline
```

### 3.2 "Scatter plot" (nuage de points)

Commençons par créer des points à afficher.

Pour dessiner un "scatter plot" (nuage de points), on utilise la méthode `scatter`.



```python
import numpy as np
X = np.array([0,1,2,3,4,6,8,10]) # les abscisses
Y = np.array([5,8,12,9,7,4,-1,2]) # les ordonnées
plt.scatter(X,Y)
```


```python
xs = np.arange(1,25) # Fonction définissant 24 entiers de 1 à 25 exclu par pas de 1 (valeur par défaut)
print(xs)
ys = 1/xs
# Autrement, en passant par des listes
#xs = range(1,25)
#ys = [1 / x for x in xs]
plt.scatter(xs, ys, marker='X', color='red')
```

On peut combiner ce graphique avec un autre ensemble de points. Créons d'autres points.


```python
zs = 1 / (25 - xs)
```

Affichez les deux ensembles de points dans un même graphique.


```python
plt.scatter(xs, ys, facecolor = 'purple', edgecolor = 'k')
plt.scatter(xs, zs, facecolor = 'silver', edgecolor = 'k')
```

Pour ajouter une légende, des axes et un titre à notre graphique (qui peut inclure du code Latex) :



```python
plt.scatter(xs, ys, label="$y=\\frac{1}{x}$")
plt.scatter(xs, zs, label="$y=\\frac{1}{25 - x}$")

plt.xlabel("$x$")
plt.ylabel("Valeur")
plt.title("Mon premier \"scatter plot\" ")

plt.legend()
```

### 3.3 Courbes en 2D


```python
X = np.array([0,1,2,3,4,6,8,10]) # les abscisses
Y = np.array([5,8,12,9,7,4,-1,2]) # les ordonnées
print("Valeurs de X : {} et de Y : {}".format(X,Y))
plt.plot(X,Y)
```


```python
X = np.linspace(0,70,8) # Fonction définissant 8 entiers d'intervalles réguliers entre 0 et 70
print("Valeurs de X :", X)
plt.plot(X,Y+2)
plt.plot(X,Y,'--',color='green',lw=4)
```


```python
t = np.linspace(-4*np.pi,4*np.pi) # Si on ne précise pas le nombre d'élements souhaités, il est de 50 par défaut
f = np.sin(t)
plt.plot(t,f,'o-')
t = np.arange(-4*np.pi,4*np.pi,0.01)
f = np.sin(t)
plt.plot(t,f,'-')
g = np.cos(t)
plt.plot(t,g,'r')
```


```python
t = np.arange(-5,5,0.1)
f = t
plt.plot(t,f,'o')
f = t**2
plt.plot(t,f,'o',markerfacecolor='silver',markeredgecolor='orange')
f = t**3
plt.plot(t,f,'o',markerfacecolor='silver',markeredgecolor='purple')
plt.xlim(-8,8)
```


```python
t = np.arange(0,5,0.01)
f = np.sqrt(t)
plt.plot(t,f,color='purple')
plt.xlim(left=0,right=5)
plt.ylim(bottom=0,top=2.5)
plt.xlabel('abscisse')
plt.ylabel('ordonnée = racine carrée')
plt.title('Courbe de la racine carrée')

```

### 3.4 Histogramme

Commençons par générer des points de manière aléatoire à partir d'une loi de distribution.

* Loi exponentielle


```python
import random  # Module permettant de générer des nombres aléatoirement

nombre_de_points = 50000 # on définit un nombre de points

d = np.zeros(nombre_de_points) # on initialise avec des zéros un vecteur d de la taille du nombre de points

# La boucle suivante permet d'affecter à chaque élément du vecteur d
# une valeur au hasard issue d'une loi de distribution exponentielle de paramètre lambda = 0.5
for i in range(nombre_de_points):
    d[i] = random.expovariate(lambd=.5)
```

Dessinons maintenant l'histogramme correspondant.


```python
h = plt.hist(d, edgecolor='black', color='blue',align='left')
```

Nous pouvons changer le nombre de rectangles (*bins* en anglais) et les normaliser (afficher des probabilités entre 0 et 1 au lieu de fréquences)


```python
plt.hist(d, bins=35, density=True, edgecolor='black', color='blue',align='left') ;
```

Il est connu qu'une loi exponentielle  de paramètre $\lambda$ a une fonction de densité de probabilité qui s'écrit $f(x) = \lambda e^{-\lambda x}$.

On peut superposer la courbe de la densité de probabilité correspondante sur le graphique.


```python
import math # Module donnant accès à la plupart des fonctions mathématiques de base

lambd = 0.5

x = np.arange(15) # on définit un vecteur de 15 valeurs d'entiers entre 0 et 14 pour les abscisses
y = lambd * np.exp(- lambd * x)

plt.hist(d, bins=35, density=True, edgecolor='black', color='blue', align='left')
plt.plot(x, y, color='red');
```

* Loi normale


```python
n = np.random.randn(100000) # Ici, on génère 100000 échantillons issus de la distribution normale. Par défaut, si on ne précise rien, mu=0 et variance=1

def DensiteNormale(x,mu,sigma):
    return 1/(sigma * np.sqrt(2*np.pi))*np.exp(-0.5*((x-mu)/sigma)**2)

lx = np.linspace(-5,5,200)
ly = DensiteNormale(lx,0,1)

plt.subplots(1, 3, figsize=(14,4))
plt.subplot(131)
plt.hist(n, color='blue', edgecolor='black') # nombre de bins par défaut
plt.xlim(min(n),max(n))
plt.title("Histogramme par défaut")
plt.subplot(132)
plt.hist(n, cumulative=True, color='blue', edgecolor='black')
plt.xlim(min(n),max(n))
plt.title("Histogramme cumulé")
plt.subplot(133)
plt.hist(n, bins=30, density=True, color='blue', edgecolor='black', label ='loi normale') # on fixe le nombre de bins à 30 et on normalise l'histogramme
plt.plot(lx, ly,'r', label = ' fonction de densité de la loi normale')
plt.legend(loc='upper right')
plt.xlim(min(n),max(n))
plt.title("Histogramme normalisé (#bins = 30)");
```

### 3.5 Surfaces et images

Pour créer des courbes, on se servait d’une variable par exemple `t` :
`t = np.arange(0,100)`

Cette variable nous indique la valeur de `t` en chaque point.

Pour créer des surfaces, on aura besoin de deux variables (par exemple `x` et `y`) et on aura besoin de connaître les valeurs de ces variables sur tous les points de la surface (donc la valeur de `x` pour chaque point quand on fait varier `x` et `y` ainsi que la valeur de `y` pour chaque point quand on fait varier `x` et `y`).

La visualisation d'une fonction de deux variables `f(x,y)` est peu plus compliquée à gérer...

Pour visualiser une fonction $z = f(x, y)$ :

* Il faut d’abord générer des tableaux X et Y (noms arbitraires) qui contiennent les valeurs des abscisses et ordonnées pour chacun des points grâce à la fonction `meshgrid()`.

* Ensuite calculer la valeur de z pour chacun de ces points.

`meshgrid()` permet de générer un maillage.

* **Exemple :** fonction gaussienne 2D


```python
from mpl_toolkits.mplot3d import axes3d, Axes3D
x = np.arange(-15, 15, 0.1)
y = np.arange(-15, 15, 0.1)

X, Y = np.meshgrid(x, y) # permet de générer 2 matrices, l'une avec les abscisses, l'autre avec les ordonnées

# Ainsi, on peut évaluer une fonction sur une matrice de valeurs. Ici, une fonction de 2 variables
z = np.exp(-X*X/50 - Y*Y/50)
print(z.ndim, z.shape)

plt.imshow(z)

fig = plt.figure(figsize=(8,6))
# ax = fig.gca(projection='3d')
ax = Axes3D(fig)
surf = ax.plot_surface(X, Y, z, cmap='viridis', linewidth=0.1, edgecolor='gray', antialiased=True)
```

La fonction`imread` de Matplotlib renvoie un array numpy dont les dimensions dépendent du type d'image (N&B, RGB ou RGBA).

* **Exemple :** image 2D N&B


```python
img1 = plt.imread('./data/main-radio.jpg')
print("Dimensions de l'image :", img1.ndim)
print("Largeur de l'image (i.e. nombre de colonnes) :", img1.shape[1])
print("Hauteur de l'image (i.e. nombre de lignes) :", img1.shape[0])
plt.imshow(img1, cmap='gray');
```

* **Exemple :** image 2D RGB


```python
img2 = plt.imread('./data/marguerite.jpg')
print("Dimensions de l'image :", img2.ndim)
print("Largeur de l'image (i.e. nombre de colonnes) :", img2.shape[1])
print("Hauteur de l'image (i.e. nombre de lignes) :", img2.shape[0])
print("Profondeur de l'image :", img2.shape[2])
plt.imshow(img2);
```

*NB. La fonction `subplot()` permet d’organiser différents tracés à l’intérieur d’une grille d’affichage. Il faut spécifier le nombre de lignes, le nombre de colonnes ainsi que le numéro du tracé.*

* Exemple de disposition en colonne<br>
<img width=300 src='./data/test_subplot_colonne.png'>
* Exemple de disposition en ligne<br>
<img width=300 src='./data/test_subplot_ligne.png'>
* Exemple de disposition en grille<br>
<img width=300 src='./data/test_subplot_grille.png'>


```python
plt.subplots(1,2,figsize=(10,10)) #figsize spécifie la largeur et la hauteur de la figure en pouces
plt.subplot(121)
plt.imshow(img1,cmap='gray')
plt.subplot(122)
plt.imshow(img2,cmap='gray')
```

## <a name="part4"></a> 4. Lire et manipuler des fichiers Excel ou csv


```python
import pandas as pd

df=pd.read_csv('./data/resultats.csv') # lecture d'une table sans header
df
# df est un dataframe = tableau à deux dimensions (ici, 5 lignes et 5 colonnes)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>13024</th>
      <th>1124660</th>
      <th>1</th>
      <th>8735</th>
      <th>1153.24</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>125</td>
      <td>10794.20</td>
      <td>1651</td>
      <td>8735</td>
      <td>3923.50</td>
    </tr>
    <tr>
      <th>1</th>
      <td>9375</td>
      <td>809562.00</td>
      <td>31</td>
      <td>8735</td>
      <td>1526.33</td>
    </tr>
    <tr>
      <th>2</th>
      <td>114</td>
      <td>9844.27</td>
      <td>4163</td>
      <td>8735</td>
      <td>5341.22</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3653</td>
      <td>315448.00</td>
      <td>1</td>
      <td>1955</td>
      <td>195493.00</td>
    </tr>
  </tbody>
</table>
</div>



* Par défaut, suppose qu'il y a un header (`header = 0` --> la ligne d'indice 0 =  noms des champs) et qu'il n'y a pas de noms de colonne (`index_col = None`).
* `index_col` à renseigner si on veut définir l'index à partie d'une colone spécifique (celle d'indice 0 le plus souvent).
* `decimal` permet d'indiquer le format du point décimal (point ou virgule)
* `sep = '\t'` ou `delimiter = '\t'` indique si le séparateur est une tabulation plutôt qu'une virgule.



```python
df=pd.read_csv('./data/resultats.csv', decimal='.', header=None)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13024</td>
      <td>1124660.00</td>
      <td>1</td>
      <td>8735</td>
      <td>1153.24</td>
    </tr>
    <tr>
      <th>1</th>
      <td>125</td>
      <td>10794.20</td>
      <td>1651</td>
      <td>8735</td>
      <td>3923.50</td>
    </tr>
    <tr>
      <th>2</th>
      <td>9375</td>
      <td>809562.00</td>
      <td>31</td>
      <td>8735</td>
      <td>1526.33</td>
    </tr>
    <tr>
      <th>3</th>
      <td>114</td>
      <td>9844.27</td>
      <td>4163</td>
      <td>8735</td>
      <td>5341.22</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3653</td>
      <td>315448.00</td>
      <td>1</td>
      <td>1955</td>
      <td>195493.00</td>
    </tr>
  </tbody>
</table>
</div>




```python
print("Ce dataframe comprend {0} lignes et {1} colonnes ".format(df.shape[0],df.shape[1]) )
```

    Ce dataframe comprend 5 lignes et 5 colonnes 



```python
print(df.loc[1],'\n')
```

    0      125.0
    1    10794.2
    2     1651.0
    3     8735.0
    4     3923.5
    Name: 1, dtype: float64 
    



```python
print(df[0],'\n') # 1ere colonne
print(df[0][0],'\n') # 1er élément de la 1ere colonne
print(df.iloc[1],'\n') # 2eme ligne
print(df.iloc[1][0],'\n') # 1er élément de la 2eme ligne
```

    0    13024
    1      125
    2     9375
    3      114
    4     3653
    Name: 0, dtype: int64 
    
    13024 
    
    0      125.0
    1    10794.2
    2     1651.0
    3     8735.0
    4     3923.5
    Name: 1, dtype: float64 
    
    125.0 
    


Il est possible d'indexer (voire de renommer) les lignes et/ou les colonnes avec des étiquettes spécifiques


```python
df.index = ["foie_total","tum_dome_CT","lobe_droit","tum_dome_SPECT","lobe_gauche"] # Pour indexer les lignes avec des étiquettes spécifiques
df.columns = ["Nombre de voxels [voxels]","Volume [mm3]","Minimum","Maximum","Moyenne"] # Pour indexer les colonnes avec des étiquettes spécifiques
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre de voxels [voxels]</th>
      <th>Volume [mm3]</th>
      <th>Minimum</th>
      <th>Maximum</th>
      <th>Moyenne</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>foie_total</th>
      <td>13024</td>
      <td>1124660.00</td>
      <td>1</td>
      <td>8735</td>
      <td>1153.24</td>
    </tr>
    <tr>
      <th>tum_dome_CT</th>
      <td>125</td>
      <td>10794.20</td>
      <td>1651</td>
      <td>8735</td>
      <td>3923.50</td>
    </tr>
    <tr>
      <th>lobe_droit</th>
      <td>9375</td>
      <td>809562.00</td>
      <td>31</td>
      <td>8735</td>
      <td>1526.33</td>
    </tr>
    <tr>
      <th>tum_dome_SPECT</th>
      <td>114</td>
      <td>9844.27</td>
      <td>4163</td>
      <td>8735</td>
      <td>5341.22</td>
    </tr>
    <tr>
      <th>lobe_gauche</th>
      <td>3653</td>
      <td>315448.00</td>
      <td>1</td>
      <td>1955</td>
      <td>195493.00</td>
    </tr>
  </tbody>
</table>
</div>




```python
df["Moyenne"]
```




    foie_total          1153.24
    tum_dome_CT         3923.50
    lobe_droit          1526.33
    tum_dome_SPECT      5341.22
    lobe_gauche       195493.00
    Name: Moyenne, dtype: float64



Il est possible d'ajouter une colonne, ici la valeur des masses en multipliant les volumes par la masse volumique


```python
df.iloc[0]
```




    Nombre de voxels [voxels]      13024.00
    Volume [mm3]                 1124660.00
    Minimum                            1.00
    Maximum                         8735.00
    Moyenne                         1153.24
    Name: foie_total, dtype: float64




```python
df.loc['foie_total']
```


```python
masses = df["Volume [mm3]"] * 1.03e-3
df["Masse [g]"] = masses
df
```


```python
df.values # Renvoie un array numpy
```


```python
a = df.Moyenne.values # Renvoie un array NumPy
print(a)
print(type(a))
```


```python
df.Moyenne.describe() # Affiche les statistiques relatives à la colonne Mean
```

----
**<span style='color:red'>Rendez-vous aux exercices 2, 3 et 4 du notebook `Exercices.ipynb` pour une mise en pratique**</span>

----

## <a name="part5"></a> 5. Exporter ses données sous forme de graphique


```python
import matplotlib.pyplot as plt
x = np.arange(-100, 100, 0.1)

h = plt.plot(x,np.sin(x/5),label='fonction sinusoïdale',color='purple')
plt.xlabel('x',size=13)
plt.ylabel(r'$sin(\frac{x}{5})$',size=13)
plt.ylim(-1.5,1.5)
plt.text(-80,1.2, "Tracé de la fonction " + r'$sin(\frac{x}{5})$', horizontalalignment='left',family="sans-serif", color='red', size=13)
plt.legend(loc="lower right", ncol=1, shadow=True, fancybox=True, framealpha=0)

# Sauvegarde dans un format vectoriel (pdf ou svg)
plt.savefig('./output/test.pdf') # .svg

# Sauvegarde dans un format image avec choix de la résolution, de la transparence etc.
plt.savefig('./output/test.png', dpi=150, transparent=True, bbox_inches="tight") # bbox_inches TRES important retire le blanc autour formats : .tif, .jpg etc.
```

## <a name="part6"></a> 6. Faire des statistiques avec Python

Avec NumPy, on a déjà vu qu’il existait beaucoup d’opérations permettant par exemple de :

* Générer des tableaux particuliers : `np.arange`, `np.ones`, `np.linspace`, ...
* Faire des opérations à partir des valeurs du tableau : `np.sum`, `np.sin`, `np.histogram`, etc.

Le module [SciPy](http://docs.scipy.org/doc/scipy/reference/) est la boîte à outils numérique pour les tableaux NumPy. On trouve dans SciPy les opérations de manipulation / traitement de données numériques classiques, mais spécifiques à un type d’application (algébre linéaire, statistiques, etc.). Ce sont donc des fonctions plus "haut niveau" que celles de NumPy.

Dans les cellules sui suivent, nous nous intéresserons en particulier aux sous-modules de calcul statistique et de régression linéaire.

### 6.1 Calcul statistique avec `scipy.stats`

#### Statistiques descriptives


```python
import numpy as np
import matplotlib.pyplot as plt
import scipy.stats

d = np.array([0.553,0.57,0.576,0.601,0.606,0.606,0.609,0.611,0.615,0.628,0.572,0.608,0.631,0.654,0.662,0.668,0.67,0.672,0.69,0.693,0.749])
#objet statistiques descriptives
stat_d = scipy.stats.describe(d)
print(stat_d)

#par indice
print(stat_d[0])
#par nom possible aussi
print(stat_d.nobs)
#possiblité d'éclater les résultats avec une affectation multiple
n,mm,m,v,sk,kt = scipy.stats.describe(d)
print(n,m) # 18   0.635166, accéder au nombre d’obs. et à la moyenne
#médiane de NumPy
print(np.median(d)) # 0.6215
#fonction de répartition empirique
print(scipy.stats.percentileofscore(d,0.6215))
```

#### Test d'adéquation à la loi normale


```python
# Vérifier que la distribution est compatible avec la loi Normale (Gauss)
#test de normalité d'Agostino
ag = scipy.stats.normaltest(d)
print(ag) # (0.714, 0.699), statistique de test et p-value (si p-value < α, rejet de l’hyp. de normalité)
#test de Normalité Shapiro-Wilks
sp = scipy.stats.shapiro(d)
print(sp) # (0.961, 0.628), statistique et p-value
#test d'adéquation d'Anderson-Darling
ad = scipy.stats.anderson(d,dist="norm") # test possible pour autre loi que « norm »
print(ad) # (0.3403, array([ 0.503,  0.573,  0.687,  0.802,  0.954]), array([ 15. ,  10. ,   5. ,   2.5,   1. ]))
#stat de test, seuils critiques pour chaque niveau de risque, on constate ici que la p-value est sup. à 15%
```

#### Test de conformité à un standard


```python
import math

# Test de conformité à un standard – Test de Student
# Objectif : H0 : μ = 0.618  -  H1 : μ ≠ 0.618
#test de conformité de la moyenne
print(scipy.stats.ttest_1samp(d,popmean=0.618)) # (1.446, 0.166), stat. de test et p-value, p-value < α, rejet de H0
#*** si l'on s’amuse à détailler les calculs *** #moyenne m = np.mean(d) # 0.6352
#écart-type – ddof = 1 pour effectuer le calcul : 1/(n-1)
sigma = np.std(d,ddof=1) # 0.0504 #stat. de test t import math
t = (m - 0.618)/(sigma/math.sqrt(d.size))
print(t) # 1.446, on retrouve bien la bonne valeur de la stat de test #p-value – c’est un test bilatéral #t distribution de Student, cdf() : cumulative distribution function
p = 2.0 * (1.0 - scipy.stats.t.cdf(math.fabs(t),d.size-1))
print(p) # 0.166, et la bonne p-value
```

----
**<span style='color:red'>Rendez-vous à l'exercice 5 du notebook `Exercices.ipynb` pour une mise en pratique**</span>

----

#### Comparaison de populations - échantillons indépendants


```python
#treated – valeurs pour échantillon des individus ayant suivi le traitement
dt = np.array([24,43,58,71,43,49,61,44,67,49,53,56,59,52,62,54,57,33,46,43,57])
#control – échantillon de contrôle
dc = np.array([42,43,55,26,62,37,33,41,19,54,20,85,46,10,17,60,53,42,37,42,55,28,48])

plt.boxplot([dc,dt],labels=['Control','Treated'],patch_artist=True)
plt.grid()
plt.show()
```


```python
#t-test – comparaison de param. de localisation – hyp. de variances égales
print(scipy.stats.ttest_ind(dt,dc)) # (t = 2.2665, p-value = 0.0286)
#t-test de Welch – comparaison de moyennes – hyp. de variances inégales
print(scipy.stats.ttest_ind(dt,dc,equal_var=False)) # (2.3109, 0.0264)
```

Ici, il s'agit d'un test t de Student standard pour comparer les valeurs de 2 échantillons.

Il renvoie une paire de 2 valeurs : (statistique t, p-value), ici (2.266551599585943, 0.028629482832245753) - en fait, objet de la classe scipy.stats.stats.Ttest_indResult. Le test fait l'hypothèse d'une variance égale, sinon, rajouter `equal_var = False`.


```python
#test de Mann-Whitney - non paramétrique - avec correction de continuité
print(scipy.stats.mannwhitneyu(dt,dc)) # (stat. U = 135, p-value unilatérale = 0.00634)
```

Test de Wilcoxon Mann-whitney non apparié (non paramétrique) qui teste pour les rangs :
* il prend en compte les valeurs égales et a une correction de continuité.
* `res = scipy.stats.mannwhitneyu(range(1, 20), range(21, 40), alternative = 'two-sided')` renvoie un tuple nommé de 2 valeurs : statistic et p-value.
* on peut utiliser aussi `alternative = 'less'` ou `alternative = 'greater'`

----
**<span style='color:red'>Rendez-vous à l'exercice 6 du notebook `Exercices.ipynb` pour une mise en pratique**</span>

----

#### Comparaison de populations - echantillons appariés


```python
#paired samples test
d1968 = np.array([0.42,0.5,0.52,0.45,0.43,0.55,0.45,0.34,0.45,0.54,0.42,0.51,0.49,0.54,0.5,0.58,0.49,0.56,0.63])
d1972 = np.array([0.45,0.5,0.52,0.45,0.46,0.55,0.60,0.49,0.35,0.55,0.52,0.53,0.57,0.53,0.59,0.64,0.5,0.57,0.64])

plt.boxplot([d1968,d1972],labels=['1968','1972'],patch_artist=True)
plt.grid()
plt.show()
```


```python
#t-test related samples - paramétrique
print(scipy.stats.ttest_rel(d1968,d1972))# (stat.test = -2.45, p-value = 0.024)
#test des rangs signés – non paramétrique
print(scipy.stats.wilcoxon(d1968,d1972, mode='approx')) #  (stat = 16, p-value = 0.0122)
```

Test t apparié (il doit y avoir autant de valeurs dans les 2 vecteurs). Renvoie une paire (statistique t, p-value), ici (-2.457703815601802, 0.024352597586836344).

Test de Wilcoxon apparié (non paramétrique) : c'est une version non paramétrique du paired t-test. `res = scipy.stats.wilcoxon(range(1, 20), range(21, 40))` renvoie un tuple nommé de 2 valeurs : statistic et pvalue.

----
**<span style='color:red'>Rendez-vous à l'exercice 7 du notebook `Exercices.ipynb` pour une mise en pratique**</span>

----

### 6.2 Fitting / régression linéaire

#### Régression polynomiale (et donc aussi régression linéaire) :


```python
fit = np.polyfit([3, 4, 6, 8], [6.5, 4.2, 11.8, 15.7], 1)
print(fit)
# Fait une régression polynomiale de degré 1 et renvoie les coefficients, d'abord celui de poids le plus élevé.
# Donc ici [a, b] si y = ax + b. Renvoie ici array([2.17966102, -1.89322034]).
```


```python
# On peut alors après construire la fonction polynôme correspondante :
poly = np.poly1d(fit) # (renvoie une fonction)
# Et évaluer cette fonction sur une valeur de x :
print(poly(7.0)) # donne 13.364406779661023.
# Cette fonction peut être évaluée directement sur une liste :
print(poly([2, 3, 4, 5])) # donne array([2.46610169, 4.64576271, 6.82542373, 9.00508475]).
```

#### Regression linéaire    


```python
# On peut aussi faire
lr = scipy.stats.linregress([3, 4, 6, 8], [6.5, 4.2, 11.8, 15.7])
print(lr)
```

Renvoie un tuple avec 5 valeurs (ici, (2.1796610169491526, -1.8932203389830509,0.93122025491258043, 0.068779745087419575, 0.60320888545710094)) :
* la pente (*slope*).
* l'ordonnée à l'origine (*intercept*).
* le coefficient de corrélation, positif ou négatif (pour avoir le coefficient de détermination $R^2$, prendre le carré de cette valeur).
* la p-value.
* l'erreur standard de l'estimation du gradient.


```python
a = [3, 4, 6, 8]
b = [6.5, 4.2, 11.8, 15.7]
x = np.linspace(0,10,10)
slope = lr[0]
intercept = lr[1]
plt.plot(slope*x+intercept,'r',label='régression linéaire')
plt.plot(a,b,'ob',label='données')
plt.grid()
plt.legend()
plt.show()
```

**`numpy.linalg.lstsq`** : permet de résoudre l'équation $ax = b$ avec $a$ et $b$ des matrices $m \times n$ et $m \times 1$ respectivement par la méthode des moindres carrés où le système d'équation peut être sur-déterminé, sous-déterminé ou exactement déterminé :



```python
# Exemple :

x = np.arange(0,9)
A = np.array([x, np.ones(9)])

y = np.array([19,20,20.5,21.5,22,23,23,25.5,24])

w, residues, rank, s = np.linalg.lstsq(A.T, y, rcond=None)
print(w, residues, rank, s)
```

Le tuple renvoyé consiste en :
* $w$ : la solution, de dimension $n \times 1$
* $residues$ : la somme des carrés des résidus.
* $rank$ : le rang de la matrice.
* $s$ : les valeurs singulières de la matrice.


```python
slope = w[0]
intercept = w[1]

plt.plot(x,slope*x + intercept,'r-',label='régression linéaire')
plt.plot(x,y,'ob',label='données')
plt.grid()
plt.legend()
plt.show()
```

----
**<span style='color:red'>Rendez-vous à l'exercice 8 du notebook `Exercices.ipynb` pour une mise en pratique**</span>

----


```python

```


```python

```
