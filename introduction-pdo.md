# DEMO 1

## SE CONNECTER À LA BDD

**Objectif : instancier la classe PDO en utilisant le constructeur**

```php
    public __construct(
    string $dsn,
    string $username = null,
    string $password = null,
    array $options = null
)
```

La classe PDO possède un constructeur qui accepte les paramètres suivants :
*https://www.php.net/manual/fr/pdo.construct.php*

```php
 - $dsn
 - $username
 - $password
 - $options
```

**Quels sont les paramètres ?**

- `$dsn` (Data Source Name) contient :

  - le pilote/driver servant à communiquer avec la bdd
  - le nom de la BDD
  - l'adresse du serveur SQL
  - le charset : l'encodage des caractères utilisés lors de la communication PDO <-> BDD

- `$username` : identifiant de l'utilisateur du serveur SQL (par ex : explorateur)

- `$password` : mot de passe de l'utilisateur du serveur SQL

- `$options` : tableau associatif contenant des options comme le mode d'erreur utilisé (bavard ou silencieux )

  - `PDO::ERRMODE_WARNING` permet un mode bavard, utile pour débogguer lorsqu'on dev.
  - `PDO::ERRMODE_SILENT` permet de rendre totalement silencieux ces messages.

### LE FAMEUX DSN :star:

```php
  $dataSourceName = 'mysql:dbname=oclock_radium;host=localhost;charset=UTF8';
  $username = 'root';
  $password = 'root';
  $options = [PDO::ATTR_ERRMODE => PDO::ERRMODE_WARNING];
```

### CRÉATION DE LA CONNEXION

```php
  $pdoDBConnection = new PDO($dataSourceName, $username, $password, $options);

  // en cas d'erreur de connexion
  // PHP affiche directement un FATAL ERROR (soit problème DSN, soit problème lié à la connexion : mauvais utilisateur ou mauvais mot de passe)
```

**En cas de succès, PHP affiche un objet PDO**

```php
var_dump($pdoDBConnection);
```
