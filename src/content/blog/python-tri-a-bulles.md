---
author: Mamoudou DIALLO
pubDatetime: 2023-08-30T00:00:00.000Z
title: Tri à bulles avec Python
postSlug: tri-a-bulles-python
featured: true
tags:
  - python
  - triabulles
  - tri
  - bubblesort
  - sort
description: Découvrez l'algorithme de tri à bulles avec Python
---

# Tri à bulles ou bubble sort

Le tri à bulles, également connu sous le nom de `"bubble sort"` en anglais, est l'un des algorithmes de tri les plus simples mais aussi les moins efficaces. Il appartient à la catégorie des algorithmes de tri comparatif, c'est-à-dire qu'il compare les éléments de la liste à trier pour les réorganiser dans l'ordre souhaité.

## Euuuh... 🤔 Mais déja c'est que c'est qu'un algorithme de tri ?

Un algorithme de tri est, en infomatique, une série d'instructions logiques et systématiques utilisées pour organiser un ensemble d'éléments dans un ordre spécifique. L'objectif principal d'un algorithme de tri est de reorganiser une liste d'éléments de manière à ce qu'ils suivent un certain ordre déterminé, tel que croissant ou décroissant.

Il existe de nombreux algorithmes de tri différents, chacun avec ses propres caractéristiques, avantages et inconvénients en termes de vitesse d'exécution, d'utilisation de la mémoire et de complexité.

### Voici quelques exemples d'algorithmes de tri couramment utilisés :

- Tri par insertion,
- Tri tri fusion,
- Tri rapide,
- Tri à bulles, etc...

Nous ici, nous allons principalement nous concentrer sur le tri à bulles.

### Principes du tri à bulles:

Le principe du tri à bulles est assez simple. L'algorithme parcourt la liste à trier à plusieurs reprises, en comparant les éléments adjacents deux à deux et en les échangeant si nécessaire pour les mettre dans le bon ordre. L'idée est de faire `"remonter"` les éléments les plus grands (ou les plus petits, selon le critère de tri) vers la fin de la liste, comme des "bulles" qui remontent à la surface. Dans notre cas, ça sera un tri dans l'odre croissant donc les plus grands remontent à la fin.

### Voici comment fonctionne l'algorithme du tri à bulles :

1. Parcourir la liste du début.
2. Comparer chaque paire d'éléments adjacents.
3. Si l'élément de gauche est plus grand que l'élément de droite, les échanger.
4. Répéter les étapes 1 à 3 jusqu'à ce que la liste soit complètement triée.

### Exemple avec la liste: [5, 1, 8, 2, 4]

![Bulle sort from www.codeurjava.com](http://4.bp.blogspot.com/-sn1uV0FwsMc/VkT3IohTtjI/AAAAAAAABAA/hnN9XR__gZE/s640/bubble%2Bsort%2B.jpg)

A la fin de cet exemple, nous aurons la liste suivante: [ 1, 2, 4, 5, 8 ]

### Remarque:

Le tri à bulles est souvent enseigné en tant qu'exemple algorithmique, car son principe est simple. Mais c'est le plus lent des algorithmes de tri communément enseignés, et il n'est donc guère utilisé en pratique.

Le tri à bulles a une complexité en temps assez défavorable par rapport à d'autres algorithmes de tri plus avancés, comme le tri rapide (quick sort) ou le tri fusion (merge sort). Sa complexité en temps est en moyenne O(n^2), où "n" est le nombre d'éléments dans la liste. Cela signifie que son temps d'exécution augmente rapidement avec la taille de la liste à trier.

### Tri à bulles en Python:

```python
1. def permute(tab: list, index):
2.     """
3.     Génère une nouvelle liste en échangeant deux éléments dans la liste donnée.
4.
5.     Paramètres :
6.         tab (list) : La liste d'entrée.
7.         index (int) : L'index du premier élément à échanger.
8.
9.     Renvoi :
10.        list : La liste modifiée avec les éléments aux indices spécifiés échangés.
11.    """
12.    tmp = tab[index]
13.    tab[index] = tab[index+1]
14.    tab[index+1] = tmp
15.    return tab


16. def bubble_sort(tab: list) -> list:
17.    """
18.    Trie une liste donnée de nombres par ordre croissant en utilisant l'algorithme de tri à bulles.
19.
20.    Paramètres :
21.    - tab (list) : La liste de nombres à trier.
22.
23.    Renvoi :
24.    - list : La liste triée de nombres.
25.    """
26.    i = 0
27.    tab_length = len(tab)
28.    while i < tab_length:
29.        if i+1 != tab_length and tab[i] > tab[i+1]:
30.            tab = permute(tab, i)
31.            i = -1
32.        i += 1
33.    return tab
```

Ce code est une implémentation du tri à bulles en Python.

### Explication de l'algorithme de tri à bulles ligne par ligne :

```python
1. def permute(tab: list, index):
```

Définit une fonction appelée `permute` qui prenant deux arguments : une liste tab et un index.

```python
2.     """
3.     Génère une nouvelle liste en échangeant deux éléments dans la liste donnée.
4.
5.     Paramètres :
6.         tab (list) : La liste d'entrée.
7.         index (int) : L'index du premier élément à échanger.
8.
9.     Renvoi :
10.        list : La liste modifiée avec les éléments aux indices spécifiés échangés.
11.    """
```

Ceci est la docstring de la fonction `permute`, fournissant une explication de ce que fait la fonction, les paramètres qu'elle prend et la valeur qu'elle renvoie.

```python
14.    tmp = tab[index]
15.    tab[index] = tab[index+1]
16.    tab[index+1] = tmp
```

Ces lignes effectuent un changement dans la liste `tab` en échangeant l'élément de l'index indiqué par `index` avec l'élément de l'index indiqué par `index+1`.

```python
17.    return tab
```

Renvoie la liste `tab` modifiée après l'échange d'éléments.

```python
19. def bubble_sort(tab: list) -> list:
```

Définit une fonction appelée `bubble_sort` qui prend un argument `tab` de type `list` et renvoie une liste de même type.

```python
20.    """
21.    Trie une liste donnée de nombres par ordre croissant en utilisant l'algorithme de tri à bulles.
22.
23.    Paramètres :
24.    - tab (list) : La liste de nombres à trier.
25.
26.    Renvoi :
27.    - list : La liste triée de nombres.
28.    """
```

Ceci est la docstring de la fonction `bubble_sort`, fournissant une explication de ce que fait la fonction, les paramètres qu'elle prend et la valeur qu'elle renvoie.

```python
31.    i = 0
```

Initialise une variable `i` à 0. Cette variable sera utilisée comme compteur pour itérer à travers les éléments de la liste lors de l'algorithme de tri à bulles.

```python
32.    tab_length = len(tab)
```

Calcule la longueur de la liste `tab` en utilisant la fonction `len()` et assigne cette valeur à la variable `tab_length`.

```python
33.    while i < tab_length:
```

Débute une boucle `while` qui continue tant que la valeur de `i` est inférieure à la longueur de la liste `tab`.

```python
34.        if i+1 != tab_length and tab[i] > tab[i+1]:
```

Vérifie si l'indice `i+1` n'est pas égal à la longueur de la liste (`tab_length`) et si la valeur à l'indice `i` dans la liste `tab` est supérieure à la valeur à l'indice `i+1`.

```python
35.            tab = permute(tab, i)
```

Si la condition précédente est vraie, appelle la fonction `permute` avec les arguments `tab` et `i` pour échanger les éléments aux indices `i` et `i+1` dans la liste `tab`.

```python
36.            i = -1
```

Réinitialise la valeur de `i` à -1. Lorsque la boucle itère, la valeur de `i` sera incrémentée à 0 à la ligne 26, effectuant ainsi une sorte de réinitialisation pour s'assurer que la vérification soit effectuée à partir du début après un échange.

```python
37.        i += 1
```

Incrémente la valeur de `i` de 1 à chaque itération de la boucle `while`.

```python
38.    return tab
```

Renvoie la liste `tab` une fois que la boucle `while` est terminée, ce qui signifie que la liste a été triée dans l'ordre croissant selon l'algorithme de tri à bulles.

### Code complet pour tester notre algorithme de tri à bulles :

```python
def permute(tab: list, index):
    """
    Génère une nouvelle liste en échangeant deux éléments dans la liste donnée.

    Paramètres :
        tab (list) : La liste d'entrée.
        index (int) : L'index du premier élément à échanger.

    Renvoi :
        list : La liste modifiée avec les éléments aux indices spécifiés échangés.
    """
    tmp = tab[index]
    tab[index] = tab[index+1]
    tab[index+1] = tmp
    return tab


def bubble_sort(tab: list) -> list:
    """
    Trie une liste donnée de nombres par ordre croissant en utilisant l'algorithme de tri à bulles.

    Paramètres :
    - tab (list) : La liste de nombres à trier.

    Renvoi :
    - list : La liste triée de nombres.
    """
    i = 0
    tab_length = len(tab)
    while i < tab_length:
        if i+1 != tab_length and tab[i] > tab[i+1]:
            tab = permute(tab, i)
            i = -1
        i += 1
    return tab


def main():
    # Initialisation d'une liste de nombres non triés
    numbers = [12, 4, 120, 8, 45, 7, -1, 44]

    # Affichage de la liste non triée
    print(f"Voici la liste : {numbers}")

    # Appel de la fonction de tri et affichage de la liste triée
    print(f"Voici la liste triée : {bubble_sort(numbers)}")


if __name__ == "__main__":
    main()
```

Voir le [code complet sur Github](https://github.com/Mah224Moud/MultiLang-Code-Snippets/blob/main/Python/bubble_sort.py).

Vous pourrez également accéder à notre collection passionnante de ressources sur Github intitulée ["MultiLang-Code-Snippets"](https://github.com/Mah224Moud/MultiLang-Code-Snippets/tree/main/Python) qui regroupe une variété de petits extraits de code dans différents langages de programmation tels que `Python`, `Php`, `C`, `C++`, `JavaScript`, et bien plus encore. N'hésitez pas à explorer et à contribuer à cette ressource polyglotte completement open source pour enrichir vos connaissances en programmation et découvrir de nouvelles perspectives.
