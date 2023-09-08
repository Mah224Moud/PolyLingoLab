---
author: Mamoudou DIALLO
pubDatetime: 2023-09-07T08:00:00.000Z
title: Conversion décimal en binare avec Python
postSlug: conversion-decimal-en-binare-python
featured: true
tags:
  - python
  - conversion
  - binaire
  - decimal
  - decimaltobinary
description: Decouvrez comment convertir un nombre décimal en binaire avec Python
---

# Conversion d'un nombre décimal en binaire avec Python

Avant de parler code, essayons d'abord de comprendre ce que c'est qu'un nombre binaire et nombre décimal.

## Nombre Binaire

Un nombre binaire est un nombre en base 2 c'est à dire un nombre composé que de 0 et 1.

### Exemple:

```python
10010100110 #ceci est un nombre binaire
```

## Nombre décimal

Un nombre décimal est un nombre en base 10. Si vous avez compris le principe, c'est un nombre composé des chiffres de 0 à 9.

### Exemple:

```python
245857 #ceci est un nombre décimal
```

Maintenant qu'on sait c'est quoi un nombre décimal et un nombre binaire, voyons comment faire cette fameuse conversion.

Imaginons avoir le nombre `115` à convertir en bianire c'est à dire combien vaut ce nombre en base 2 ? En d'autres termes quelle est sa représentation en base 2 ? 🤔

### Méthode de résolution:

Pour ce faire, nous devons effectuer une division successive du nombre par `2` jusqu'à obtenir un quotient nul (avoir un quotient qui est égal à 0)

### Exemple avec notre nombre de depart `115`:

![Decimal to Binary](https://github.com/Mah224Moud/BlogImages/blob/main/Python/decimal_to_binary.png?raw=true)

Ici, dans notre exemple nous avons representé tous les quotients en rouge et les restes en vert.

### C'est bien beau tout ça mais comment obtenir sa représentation binaire ? 🤔

Bonne question 😉  
Pour obtenir sa representé en binaire, il suffit de lire en partant de la fin (derniere division), toutes les valeurs obtenues dans les restes des divisions successives.

### Exemple:

![Decimal to Binary result](https://github.com/Mah224Moud/BlogImages/blob/main/Python/final%20decimal_to_binary.png?raw=true)

En lisant les restes des divisions successives suivant la flèche bleue, on peut donc dire que: `115` en base 10 vaut `1110011` en base 2

### Remarque:

Bien que Python dispose d’une fonction native `built-in function` pour convertir des nombres décimaux en binaires, il est important de comprendre l’algorithme pour saisir pleinement les concepts.  
Laissez-moi donc vous expliquer comment fonctionne l’algorithme de conversion.

## Code en Python

```python
1. def decimal_to_binary(number: int) -> int:
2.     """
3.     Convertit un nombre décimal en sa représentation binaire.
4.
5.     Paramètres:
6.         number (int): Le nombre décimal à convertir.
7.
8.     Renvoie:
9.         int: La représentation binaire du nombre décimal.
10.     """
11.    binary = ""
12.    while (number > 0):
13.        binary += f"{number % 2}"
14.        number = number // 2
15.    return int(binary[::-1])
```

Ce code est une fonction Python qui convertit un nombre binaire en décimal. Voici comment cela fonctionne :

### Voici une explication ligne par ligne du code :

```python
1. def decimal_to_binary(number: int) -> int:
```

Définit une fonction appelée `decimal_to_binary` prenant un argument `number` de type `int` et renvoyant une valeur de type `int`.

```python
2."""
3.  Convertit un nombre décimal en sa représentation binaire.
4.
5.  Paramètres:
6.      number (int): Le nombre décimal à convertir.
7.
8.  Renvoie:
9.      int: La représentation binaire du nombre décimal.
10."""
```

Fournit une documentation de la fonction qui explique son objectif et ses paramètres.

```python
11. binary = ""
```

Initialise une chaîne de caractères vide appelée `binary`.

```python
12. while (number > 0):
```

Commence une boucle `while` qui se poursuit tant que `number` est supérieur à `0`.

```python
13.    binary += f"{number % 2}" # str(number % 2) etait une autre solution
14.    number = number // 2
```

À chaque itération de la boucle, onajoute le reste de la division de `number` par 2 à la fin de la chaîne `binary`. Ensuite, on divise `number` par 2 et affecte le résultat à `number`.

```python
15. return int(binary[::-1])
```

Une fois que la boucle `while` est terminée, renvoie la valeur entière obtenue en inversant la chaîne `binary`.

## Code complet pour tester la fonction :

```python
def decimal_to_binary(number: int) -> int:
    """
    Convertit un nombre décimal en sa représentation binaire.

    Paramètres:
        number (int): Le nombre décimal à convertir.

    Renvoie:
        int: La représentation binaire du nombre décimal.
    """
    binary = ""
    while (number > 0):
        binary += f"{number % 2}"
        number = number // 2
    return int(binary[::-1])


def main():
    # Demande à l'utilisateur d'entrer un nombre decimal
    number = int(input("Type a number : "))

    # Affiche la représentation binaire du nombre
    print(
        f"The binary representation of {number} is {decimal_to_binary(number)}")


if __name__ == "__main__":
    main()

```

### Bonus avec la methode built-in (native) `bin()` de python:

```python
number = 115
binary = bin(number) # On obtient 0b1110011
binary_representation = int(binary[2:])  # [2:] Pour supprimer le préfixe "0b" et int pour convertir en entier

print(f"La représentation binaire de {number} est {binary_representation}") # On obtient 1110011
```

Voir le [code complet](https://github.com/Mah224Moud/MultiLang-Code-Snippets/blob/main/Python/decimal_to_binary.py) sur [Github](https://github.com/Mah224Moud/MultiLang-Code-Snippets/), où vous aurez accès à une collection passionnante de ressources intitulée ["MultiLang-Code-Snippets"](https://github.com/Mah224Moud/MultiLang-Code-Snippets/tree/main/Python) qui regroupe une variété de petits extraits de code dans différents langages de programmation tels que `Python`, `Php`, `C`, `C++`, `JavaScript`, et bien plus encore. N'hésitez pas à explorer et à contribuer à cette ressource polyglotte completement open source pour enrichir vos connaissances en programmation et découvrir de nouvelles perspectives.
