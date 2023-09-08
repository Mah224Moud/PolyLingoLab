---
author: Mamoudou
pubDatetime: 2023-08-25T08:30:00.000Z
title: Conversion binaire en decimal avec Python
postSlug: conversion-binaire-en-decimal-python
featured: false
tags:
  - python
  - binaire
  - decimal
  - conversion
  - binarytodecimal
description: Nous allons voir comment convertir un nombre binaire en un nombre decimal avec Python.
---

# Conversion d'un nombre binaire en décimal avec Python

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
245897 #ceci est un nombre décimal
```

Maintenant qu'on sait c'est quoi un nombre décimal et un nombre binaire, voyons comment faire cette fameuse conversion.

Imaginons avoir le nombre `101011` à convertir en décimal c'est à dire combien vaut ce nombre en base 10 ? 🤔

Pour ce faire, nous allons nous servir de deux choses:

1. donner des indices au nombre à convertir en partant de la droite ,
2. nous servir de la puissance 2.

### Remarque:

Les indices commence forcément à 0.

### Comment mettre les indices ? 🤔

![Binary to Decimal](https://github.com/Mah224Moud/BlogImages/blob/main/Python/binary_to_decimal.png?raw=true)

Ici, dans notre exemple nous avons representé le nombre en noir et ses indices en rouge conformément à ce qu'on avait dit à savoir en partant de la droite du nombre et les indices commencent à 0.

### Comment utiliser la puissance de 2 ? 🤔

Là aussi, c'est très simple. Nous allons suivre un petit principe qui est le suivant: `(2 ^ indice) * valeur`.

### Exemple avec notre nombre de départ `101011`

```python
(2 ^ 5) * 1 #valeur du debut
(2 ^ 4) * 0
(2 ^ 3) * 1
(2 ^ 2) * 0
(2 ^ 1) * 1
(2 ^ 0) * 1 #valeur de fin
```

Si vous avez bien suivi le principe, notre nombre `101011` est de taille 6 et ce qui veut dire qu'il aura forcément 6 indices en partant de 0 à 5.

### Remarque:

`^` signifie ici, puissance donc 2 ^ 0 = 2 à la puissance 0

### Obtentions du résultat des indices et des valeurs:

```python
(2 ^ 5) * 1 # on obtient 32
(2 ^ 4) * 0 # on obtient 0
(2 ^ 3) * 1 # on obtient 8
(2 ^ 2) * 0 # on obtient 0
(2 ^ 1) * 1 # on obtient 2
(2 ^ 0) * 1 # on obtient 1
```

### C'est bien beau tout ça mais comment obtenir la valeur en décimal ? 🤔

Bonne question 😉  
Pour obtenir la valeur en décimal, rien de compliquer. Il suffit de faire la somme de toutes les valeurs qu'on obtient.

```python
32 + 0 + 8 + 0 + 2 + 1 # on obtient 43
```

donc `101011` en binaire = `43` en décimal

### Remarque:

Bien que Python dispose d'une fonction native `built-in function` pour convertir des nombres binaires en décimaux, il est important de comprendre l'algorithme sous-jacent pour saisir pleinement les concepts. Laissez-moi donc vous expliquer comment fonctionne l'algorithme de conversion.

## Code en Python

```python
1. def binary_to_decimal(number: int) -> int:
2.     """
3.     Convertit un nombre binaire en décimal.
4.
5.     Args:
6.         number (int): Le nombre binaire à convertir.
7.
8.     Returns:
9.         int: La représentation décimale du nombre binaire.
10.     """
11.    values = list(str(number))
12.    result = 0
13.    pow_index = len(values) - 1
14.    for i in values:
15.        if i == "1":
16.            result += pow(2, pow_index)
17.        pow_index -= 1
18.    return result
```

Ce code est une fonction Python qui convertit un nombre binaire en décimal. Voici comment cela fonctionne :

### Voici une explication ligne par ligne du code :

```python
1. def binary_to_decimal(number: int) -> int:
```

Définit une fonction appelée `binary_to_decimal` prenant un argument `number` de type `int` et renvoyant une valeur de type `int`.

```python
2.     """
3.     Convertit un nombre binaire en décimal.
4.
5.     Args:
6.         number (int): Le nombre binaire à convertir.

8.     Returns:
9.         int: La représentation décimale du nombre binaire.
10.     """
```

Fournit une documentation de la fonction qui explique son objectif et ses paramètres.

```python
11. values = list(str(number))
```

Crée une liste `values` en convertissant chaque chiffre du nombre binaire `number` en caractères individuels

```python
12. result = 0
13. pow_index = len(values) - 1
```

Initialise la variable `result` à `0` et `pow_index` à la longueur de la liste `values` moins 1.

```python
14. for i in values:
```

Commence une boucle `for` qui itère à travers chaque valeur `i` dans la liste `values`.

```python
15. if i == "1":
16.   result += pow(2, pow_index)
```

Vérifie si la valeur `i` est égale à "1". Si oui, ajoute 2 élevé à la puissance `pow_index` à la variable `result`.

```python
17.   pow_index -= 1
18. return result
```

Décrémente `pow_index` à la fin de chaque itération et, une fois la boucle terminée, renvoie la valeur calculée dans `result`.

## Code complet pour tester la fonction :

```python
def binary_to_decimal(number: int) -> int:
    """
    Convertit un nombre binaire en décimal.

    Args:
        number (int): Le nombre binaire à convertir.

    Returns:
        int: La représentation décimale du nombre binaire.
    """
    values = list(str(number))
    result = 0
    pow_index = len(values) - 1
    for i in values:
        if i == "1":
            result += pow(2, pow_index)
        pow_index -= 1
    return result

def main():
    # Demande à l'utilisateur d'entrer un nombre binaire
    number = int(input("Enter the binary number you want to convert: "))

    # Affiche une bannière de résultat
    print("\n\n*********************************************")
    print("****************** Result *******************")
    print("*********************************************")

    # Appelle la fonction binary_to_decimal pour convertir le nombre
    decimal_value = binary_to_decimal(number)

    # Affiche le résultat de la conversion
    print(f"The decimal number of {number} is {decimal_value}")


if __name__ == "__main__":
    main()

```

### Bonus:

Pour ceux qui ce demandent, on aurait aussi pu le faire nativement en utilisant la fonction `int()` de python.

```python
binaire = "101011"
decimal = int(binaire, 2)
print(decimal) # on obtient 43

```

Voir le [code complet du programme](https://github.com/Mah224Moud/MultiLang-Code-Snippets/blob/main/Python/binary_to_decimal.py) sur [Github](https://github.com/Mah224Moud/MultiLang-Code-Snippets/), où vous aurez accès à une collection passionnante de ressources intitulée ["MultiLang-Code-Snippets"](https://github.com/Mah224Moud/MultiLang-Code-Snippets/tree/main/Python) qui regroupe une variété de petits extraits de code dans différents langages de programmation tels que `Python`, `Php`, `C`, `C++`, `JavaScript`, et bien plus encore. N'hésitez pas à explorer et à contribuer à cette ressource polyglotte completement open source pour enrichir vos connaissances en programmation et découvrir de nouvelles perspectives.
