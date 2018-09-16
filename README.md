Ce projet fournit plusieurs API qui fournissent des requêtes de produits, un accès au panier pour inclure, supprimer et interroger des éléments en plus de l'authentification.


Utilise des technologies:
<ul>
<li>Java 8</li>
<li>Spring Boot</li>
<li>JPA</li>
<li>H2 in memory</li>
<li>REST Webservice</li>
<li>JUnit</li>
</ul>
Le projet a été créé à Maven et Java 8.
Il peut être importé via un projet Maven dans l'IDE de votre choix (eclipse, netbeans, etc).

Après avoir importé le projet, exécutez simplement la classe <b>com.nexio.ricardo.test.TestApplication</b>


Le script SQL s'exécute lorsque Spring Boot s'exécute.
src\main\resources\data.sql

```
INSERT INTO UTILISATEUR(NOM, MOT_PASSE) VALUES('ricardo', '123456');
INSERT INTO UTILISATEUR(NOM, MOT_PASSE) VALUES('thuana', '112233');

INSERT INTO PRODUIT(ID,CODE,NOM,PRIX,DESCRIPTION,FABRICANT) VALUES(1,'2344XH','Z5', 1190.99, 'Celulaire Z5', 'Sony');
INSERT INTO PRODUIT(ID,CODE,NOM,PRIX,DESCRIPTION,FABRICANT) VALUES(2,'7485RT','K10', 790.99, 'Celulaire K10', 'LG');
INSERT INTO PRODUIT(ID,CODE,NOM,PRIX,DESCRIPTION,FABRICANT) VALUES(3,'8743KW','MOTO G', 870.99, 'Celulaire MOTO G', 'Motorola');
```

Les API suivantes ont été développées:
<ul>
<li>[/api/utilisateur/connecter],methods=[POST] Faire la connexion à un compte d'utilisateur</li>
  Ex. réquisition {
	"nom":"ricardo",
	"motPasse":"123456"
}
<br></br>
<li>[/api/utilisateur/deconnecter],methods=[POST] Faire la déconnexion d'utilisateur connecté</li>
 Il n'y a pas de paramètre de réquisition
<br></br>
<li>[/api/panier/ajouter-produit],methods=[POST]  Ajouter le produit au panie </li>
Ex. réquisition {
	"idProduit": 1,
	"quantite": 2
}
<br></br>
<li>[/api/panier/enlever-produit],methods=[DELETE] Enlever le produit au panier</li>
 Ex. réquisition {
	"idProduit": 2,
	"quantite": 1
}
<br></br>
<li>[/api/panier/afficher-contenu],methods=[GET] Afficher le contenu au panier</li>
  Il n'y a pas de paramètre de réquisition
  </br>
  Ex. de répondre
  [
    {
        "produit": {
            "id": 3,
            "code": "8743KW",
            "nom": "MOTO G",
            "description": "Celulaire MOTO G",
            "prix": 870.99,
            "fabricant": "Motorola"
        },
        "quantite": 1
    }
]
<br></br>
<li>[/api/produit/catalogue],methods=[GET] Liste tous les produits</li>
  Il n'y a pas de paramètre de réquisition
  </br>
  Ex. de répondre
  [
    {
        "id": 1,
        "code": "2344XH",
        "nom": "Z5",
        "description": "Celulaire Z5",
        "prix": 1190.99,
        "fabricant": "Sony"
    },
    {
        "id": 2,
        "code": "7485RT",
        "nom": "K10",
        "description": "Celulaire K10",
        "prix": 790.99,
        "fabricant": "LG"
    }]
<br></br>
<li>[/api/produit/detail/{idProduit}],methods=[GET] Détailler un produit</li>
Ex. réquisition /api/produit/detail/2
</br>
Ex. de répondre
  {
    "id": 1,
    "code": "2344XH",
    "nom": "Z5",
    "description": "Celulaire Z5",
    "prix": 1190.99,
    "fabricant": "Sony"
}
<br></br>
</ul>


Il faut se connecter via le menu <b>/api/utilisateur/connecter</b> avant d'accéder aux autres services.

Les tests d'intégration peuvent être exécutés via l'outil JUnit.
