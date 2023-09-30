---
author: Mamoudou DIALLO
pubDatetime: 2023-09-30T08:00:00.000Z
title: Nombres premiers
postSlug: nombres-premiers-python
featured: true
tags:
  - python
  - premiers
  - nombres
  - prime
  - nombrespremiers
  - primes
description: Allons à la rencontre des nombres premiers avec Python.
---

# C'est quoi un nombre premier ? 🤔

Un nombre premier est un entier positif supérieur à 1 qui n'a que deux diviseurs positifs distincts : 1 et lui-même. Autrement dit, un nombre premier ne peut être divisé que par 1 et par lui-même sans laisser de reste.  
Les nombres premiers sont un concept fondamental en mathématiques.

### Important :

Il doit avoir **_exactement_** deux diviseurs à savoir 1 et lui-même.

### Exemple:

[![Divisors from wikipedia](https://github.com/Mah224Moud/BlogImages/blob/main/Python/divisors.png?raw=true)](https://upload.wikimedia.org/wikipedia/commons/thumb/a/aa/Nombrepremier_2017.png/220px-Nombrepremier_2017.png)

### Remarque:

Dans notre exemple ici, seul 7 admet exactement deux diviseurs : 1 et lui-même.  
6, 8 et 9 en ont au moins 3.

## Liste des nombres premiers compris entre 0 et 100:

[![Primes from wikipedia](https://github.com/Mah224Moud/BlogImages/blob/main/Python/primes.png?raw=true)](https://upload.wikimedia.org/wikipedia/commons/thumb/5/50/Primencomposite0100.svg/220px-Primencomposite0100.svg.png)

### Remarque:

- Dans notre exemple ici, seuls les nombres en rouge sont des nombres premiers.
- La liste des nombres premiers est infinie, et il existe une infinité de façons de les répartir sur la ligne des nombres entiers.

### Maintenant qu'on connait tout ça, comment peut-on savoir si un nombre est premier ? 🤨

Euuuh la question est énorme ! 🤔  
En fait, il y'a plusieurs façons de le savoir. On va en citer quelques-uns :

- Test de primalité de [Fermat](https://fr.wikipedia.org/wiki/Test_de_primalit%C3%A9_de_Fermat),
- Test de primalité de [Miller-Rabin](https://fr.wikipedia.org/wiki/Test_de_primalit%C3%A9_de_Miller-Rabin),
- Test de primalité de [Lucas-Lehmer](https://fr.wikipedia.org/wiki/Test_de_primalit%C3%A9_de_Lucas-Lehmer),
- Test de primalité de [Solovay-Strassen](https://fr.wikipedia.org/wiki/Test_de_primalit%C3%A9_de_Solovay-Strassen) et tant d'autres.

### Euh... 😲 On dirait que c'est compliqué ! 🙆‍♂️

Pas de panique ! 😉  
Nous allons utiliser une méthode bien plus conviviale qu'on va appeler la méthode de la `racine carrée`.

### Qu'est-ce que ce que ce truc ? 🙄

L'idée de base de cette méthode repose sur le fait que si un nombre `n` n'est pas premier, alors il doit avoir un diviseur `d` tel que `1 < d ≤ √n`.  
Donc, si aucun diviseur n'est trouvé jusqu'à `√n`, le nombre est très probablement premier.

### Voici les étapes de la méthode avec la racine carrée pour tester la primalité d'un nombre n :

1. Calculez la valeur de `√n`
2. Pour chaque diviseur potentiel `d` de `2` à `√n`:

- Si `n` est divisible par `d` (c'est-à-dire `n` modulo `d` est égal à zéro), alors `n` n'est pas premier.
- Sinon, continuez à tester les autres diviseurs.

## Voyons le problème autrement 😉

Autrement dit, si aucun diviseur n'est trouvé dans l'intervalle de `2` à `√n`​, alors le nombre `n` est premier.

### Remarque :

En suivant le principe même de notre définition, on peut donc dire que tout nombre inférieur ou égal à 1 n'est pas premier. En d'autres termes, tout nombre premier doit strictement être supérieur à 1.

## Voyons maintenant ce que ça donne avec du code en Python 🙂

```python
1. import math
2.
3. def is_prime(number: int) -> bool:
4.     """
5.     Vérifie si un nombre donné est premier.
6.
7.     Args:
8.         number (int): Le nombre à vérifier.
9.
10.     Returns:
11.         bool: True si le nombre est premier, False sinon.
12.     """
13.     if (number <= 1):
14.         return False
15.
16.     number_sqrt = int(math.sqrt(number)) + 1
17.     for i in range(2, number_sqrt):
18.         if ((number % i) == 0):
19.             return False
20.     return True
```

Ce code est une fonction qui implémente la méthode de la racine carrée pour tester la primalité d'un nombre.

### Voici une explication ligne par ligne du code :

```python
1. import math
```

Cette ligne importe le module `math`, qui fournit des fonctions mathématiques pour effectuer des calculs plus avancés.

```python
3. def is_prime(number: int) -> bool:
```

Définit une fonction appelée `is_prime` qui prend un argument `number` de type `int` et renvoie une valeur booléenne.

```python
4.     """
5.     Vérifie si un nombre donné est premier.
6.
7.     Args:
8.         number (int): Le nombre à vérifier.
9.
10.     Returns:
11.         bool: True si le nombre est premier, False sinon.
12.     """
```

Ce bloc de commentaires est appelé "docstring" et fournit une explication de la fonction. Il décrit brièvement ce que fait la fonction, les arguments qu'elle prend et la valeur qu'elle renvoie.

```python
13.     if (number <= 1):
14.         return False
```

Vérifie si `number` est inférieur ou égal à 1. Si c'est le cas, la fonction renvoie `False`, car les nombres premiers sont strictement supérieurs à 1.

```python
16.     number_sqrt = int(math.sqrt(number)) + 1
```

Calcule la racine carrée entière du nombre donné à l'aide de la fonction `math.sqrt()` du module `math`. Cette racine carrée est ensuite augmentée de 1 pour obtenir la borne supérieure de la boucle de recherche de diviseurs.

```python
17.     for i in range(2, number_sqrt):
```

Commence une boucle qui itère sur tous les nombres de 2 à `number_sqrt - 1` inclus. Ces sont les diviseurs potentiels que nous allons tester.

```python
18.         if ((number % i) == 0):
19.             return False
```

Vérifie si le nombre donné est divisible par `i` (un diviseur potentiel). Si oui, cela signifie que le nombre n'est pas premier, car il a un diviseur autre que 1 et lui-même. Dans ce cas, la fonction renvoie `False`.

```python
20.     return True
```

Si aucun diviseur n'a été trouvé dans la boucle précédente, la fonction renvoie `True`, indiquant que le nombre est premier.

## Code complet pour tester la fonction :

```python
import math

def is_prime(number: int) -> bool:
    """
    Check if a given number is prime.

    Args:
        number (int): The number to be checked.

    Returns:
        bool: True if the number is prime, False otherwise.
    """
    if (number <= 1):
        return False

    number_sqrt = int(math.sqrt(number)) + 1
    for i in range(2, number_sqrt):
        if ((number % i) == 0):
            return False
    return True


def main():
    # Demander à l'utilisateur d'entrer un nombre
    number = int(input("Type a number: "))

    # Vérifier si le nombre est premier ou non à l'aide de la fonction is_prime
    if (is_prime(number)):
        print(f"{number} is prime")
    else:
        print(f"{number} is not prime")


if __name__ == "__main__":
    main()

```

## Bonus: Trouvez les n premiers nombres premiers :

```python
import math  # Importation du module math pour les opérations mathématiques

def is_prime(number: int) -> bool:
    """
    Check if a given number is prime.

    Args:
        number (int): The number to be checked.

    Returns:
        bool: True if the number is prime, False otherwise.
    """
    if (number <= 1):
        return False  # Si le nombre est inférieur ou égal à 1, il n'est pas premier

    number_sqrt = int(math.sqrt(number)) + 1  # Calcul de la racine carrée du nombre pour la boucle de test
    for i in range(2, number_sqrt):  # Boucle pour tester la divisibilité par les nombres de 2 à la racine carrée du nombre
        if ((number % i) == 0):
            return False  # Si le nombre est divisible par i, il n'est pas premier
    return True  # Si aucun diviseur n'a été trouvé, le nombre est premier

def generate_n_primes(limit: int) -> list:
    """
    Generate a list of the first n prime numbers.

    Parameters:
    limit (int): The maximum number of prime numbers to generate.

    Returns:
    list: A list of the first n prime numbers.
    """
    start = 2  # On commence avec le premier nombre premier
    prime_list = []  # Liste pour stocker les nombres premiers
    while limit > 0:
        if (is_prime(start)):  # Vérifie si le nombre actuel est premier
            prime_list.append(start)  # Ajoute le nombre à la liste des nombres premiers
            limit -= 1  # Décrémente le nombre de nombres premiers restants à générer
        start += 1  # Passe au nombre suivant
    return prime_list  # Retourne la liste des nombres premiers générés

def main():
    limit = input("Entrez une limite : ")  # Demande à l'utilisateur de fournir une limite
    print("Voici les premiers", limit, "nombres premiers :", generate_n_primes(int(limit)))  # Affiche les nombres premiers générés

if __name__ == "__main__":
    main()

```

Voir le [code complet pour tester la primalité d'un nombre](https://github.com/Mah224Moud/MultiLang-Code-Snippets/blob/main/Python/prime.py) et le [code complet pour générer les n premiers nombres premiers](https://github.com/Mah224Moud/MultiLang-Code-Snippets/blob/main/Python/generate_n_primes.py).

Vous pourrez également accéder à notre collection passionnante de ressources sur Github intitulée ["MultiLang-Code-Snippets"](https://github.com/Mah224Moud/MultiLang-Code-Snippets/tree/main/Python) qui regroupe une variété de petits extraits de code dans différents langages de programmation tels que `Python`, `Php`, `C`, `C++`, `JavaScript`, et bien plus encore. N'hésitez pas à explorer et à contribuer à cette ressource polyglotte completement open source pour enrichir vos connaissances en programmation et découvrir de nouvelles perspectives.
