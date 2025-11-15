# TP1 - Programmation Dynamique par Réflexion

Ce projet est un exemple simple d'injection de dépendances en utilisant la réflexion en Java. Il est divisé en trois couches : DAO, Metier et Présentation.

## Structure du projet

```
.
├── config.txt
├── src
│   ├── dao
│   │   ├── DaoImpl.java
│   │   └── IDao.java
│   ├── metier
│   │   ├── IMetier.java
│   │   └── MetierImpl.java
│   └── presentation
│       └── Presentation2.java
└── ...
```

## Description des fonctionnalités

### Couche DAO (Data Access Object)

- **`IDao.java`**: Interface qui définit le contrat pour l'accès aux données. Elle contient une méthode `getValue()`.
- **`DaoImpl.java`**: Implémentation de l'interface `IDao`. Dans cet exemple, `getValue()` retourne une valeur statique (100.0).

### Couche Métier

- **`IMetier.java`**: Interface qui définit le contrat pour la logique métier. Elle contient une méthode `calcul()`.
- **`MetierImpl.java`**: Implémentation de l'interface `IMetier`. Elle a une dépendance sur `IDao` pour effectuer ses calculs. La méthode `calcul()` récupère la valeur de la couche DAO et la multiplie par 2.

### Couche Présentation

- **`Presentation2.java`**: C'est le point d'entrée de l'application qui démontre l'injection de dépendances dynamique. Au lieu d'instancier les classes `DaoImpl` et `MetierImpl` directement (couplage fort), il lit leurs noms à partir du fichier `config.txt`. Ensuite, il utilise la réflexion Java pour créer des instances de ces classes, injecter la dépendance DAO dans la classe Metier, et enfin appeler la méthode de calcul.

### Fichier de configuration

- **`config.txt`**: Fichier texte qui contient les noms complets des classes d'implémentation à utiliser pour les couches DAO et Metier. Cela permet de changer les implémentations sans recompiler le code.

```
dao.DaoImpl
metier.MetierImpl
```

## Comment exécuter l'application

Pour exécuter l'application, il faut lancer la méthode `main` de la classe `presentation.Presentation2`. L'application lira le fichier `config.txt`, instanciera les classes dynamiquement et affichera le résultat du calcul.

```
Résultats = 200.0
```
