
#  TP 2 : Spring IOC

---
### Réalisé par

**Abla MARGHOUB**

### Encadré par

**Pr. Mohamed LACHGAR**

### Module

**Techniques de Programmation Avancée**

### Établissement

**École Normale Supérieure - Université Cadi Ayyad**

---

##  Objectifs du TP
Ce TP a pour but de comprendre l’utilisation du framework Spring pour la gestion de l’injection de dépendances (IoC - Inversion of Control) et la configuration des composants via annotations, XML et profils Spring.
Plus précisément, il permet de :

- Créer un projet Maven dans IntelliJ IDEA.

- Comprendre le rôle du conteneur IoC de Spring dans la gestion automatique des dépendances.

- Déclarer des beans à l’aide de l’annotation @Component.

- Réaliser l’injection de dépendances avec les annotations @Autowired et @Qualifier.

- Configurer l’application à l’aide des annotations et d’un fichier XML.

- Utiliser les profils Spring (@Profile) pour gérer différents environnements (développement, production, etc.).

- Écrire et exécuter un test unitaire JUnit pour valider le bon fonctionnement de l’application.
---

##  Description des interfaces et classes

| **Nom** | **Type** | **Package** | **Rôle / Description** |
|----------|-----------|--------------|--------------------------|
| `IDao` | Interface | `dao` | Définit la méthode `getValue()` qui retourne une valeur de type double. |
| `DaoImpl` | Classe | `dao` | Implémentation principale de `IDao`, retourne 100.0. Annotée `@Component("dao")`. |
| `DaoImpl2` | Classe | `dao` | Deuxième implémentation de `IDao`, retourne 150.0. Annotée `@Component("dao2")`. |
| `IMetier` | Interface | `metier` | Déclare la méthode `calcul()` représentant la logique métier. |
| `MetierImpl` | Classe | `metier` | Implémente `IMetier`, utilise un objet `IDao` injecté par Spring. Annotée `@Component("metier")`. |
| `Presentation2` | Classe | `presentation` | Classe principale configurée avec `@Configuration` et `@ComponentScan` pour exécuter l’application. |
| `PresentationXML` | Classe | `presentation` | Classe utilisant une configuration XML (`applicationContext.xml`) pour charger les beans Spring. |
| `applicationContext.xml` | Fichier XML | `src/main/resources` | Fichier de configuration XML définissant les beans et l’injection de dépendances. |
| `MetierImplTest` | Classe de test | `metier` | Classe JUnit testant la méthode `calcul()` avec une implémentation fictive de `IDao`. |

---

##  Fonctionnement global

1. Le conteneur Spring charge les beans annotés avec `@Component`.  
2. Les dépendances (`IDao` → `MetierImpl`) sont injectées automatiquement via `@Autowired`.  
3. L’annotation `@Qualifier` permet de choisir quelle implémentation injecter (`dao` ou `dao2`).  
4. L’application est exécutée depuis la classe `Presentation2` ou `PresentationXML`.  

---

##  Résultats attendus

###  Exécution avec `DaoImpl`

<img width="749" height="245" alt="pp1" src="https://github.com/user-attachments/assets/053c9aeb-b36a-4b2f-a625-68558a7cfd53" />

###  Exécution avec `DaoImpl2`

<img width="714" height="228" alt="pp2" src="https://github.com/user-attachments/assets/afea8c4a-62c4-4dc5-9453-11e5087e555f" />

###  Exécution avec profils Spring

<img width="685" height="201" alt="pp5" src="https://github.com/user-attachments/assets/222879ab-0244-41be-9991-322aa1cf5fae" />

### Tests unitaires

<img width="753" height="225" alt="pp3" src="https://github.com/user-attachments/assets/0c215ad5-233c-4b16-a712-2194c7bb2900" />

### Configuration XML

<img width="778" height="198" alt="pp4" src="https://github.com/user-attachments/assets/2c324e43-47c1-4d3c-ad07-480d8134fb77" />



