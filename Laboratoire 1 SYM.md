# Laboratoire 1 SYM



## Question 1

Pour obtenir un application multilangue, il faut Utiliser l'outil "Translations Editor" d'Android Studio.
Si la traduction en une langue donné n'est pas disponible, la langue par défaut la remplacera.
Si une clé donnée ne possède pas de valeur par defaut, la compilation ne se lance pas

## Question 2

La ressource utilisée dans l'expemple est directement disponible dans le SDK. Pour utiliser une ressource tierce trouvée par exemple sur le site proposé : https://design.google.com/icons/ , il est nécessaire de les importer dans le projet. Pour cela il suffit de drag and drop les ressources dans le dossier app/res/ . Les icones ajoutés sont disponibles dans 6 formats différents pour s'adapter à la taille des différents device cible. 

Pour l'utilser on peut la référencer de cette façon : 

```
R.drawable.xxx
```

Dans notre cas la ressource s'est mise dans un dossier drawable. R permet d'accéder au dossier res et xxx doit être remplacer par le nom de l'icon ajouter.

## Question 3

Lorsque l'on appuie sur le bouton back, l'application disparaît pour afficher le bureau. L'applicaiton n'est pas arrêtée, elle est simplement mise en arrière plan.

Pour résoudre ce problème, il faut "Override" une méthode nommée :

```java
@Override
public void onBackPressed() {
    // your code.
}
```

Ceci nous permet de réagir de la façon que l'on désire sur l'appui du bouton. Dans notre cas, l'idée serait de revenir à la page "MainActivity" lorsque l'on appuie sur le bouton.

## Question 4

Pour pouvoir récupérer une information dans la seconde activité et ensuite la transmettre dans l'activité de départ, il faut d'abord démarrer l'activité en utilisant la  méthode : startActivityForResult() au lieu de startActivity(). Cette méthode prend un paramètre supplémentaire nommé "Request code" qui sera retourné lorsque l'on voudra récupérer le résultat.

Lorsque l'activité principale est reprise, la méthode onActivittyResult() est appelée. On peut donc utiliser cette méthode pour récupérer la valeur transmise par la seconde activité. Cette méthode reçoit trois paramètres : le request code précédemment défini un code de résultat pour savoir si l'activité s'est terminée correctement ainsi qu'un intend permettant de récupérer les données.

## Question 5

Le problème de cette méthode qui est dépréciée est qu'elle ne pourra pas être utilisé si l'on veut développer une application qui sera disponible sur le store. Comme android demandera d'ici la fin de l'année que l'application soit compilée avec un SDK vieux d'une année au maximum.

La méthode proposée dans la documentation officiel est d'utilisé la méthode "getImei()". Cette méthode demande les mêmes permissions que la méthode précédente.

## Question 6

### Pour créer un nouveau layout spécifique 

Pour créer un nouveau layout spécifique, il faut faire un clic droit sur le package "layout" qui se trouve dans le dossier "res" et allé sur "new" -> "Layout resource file".

Après avoir cliqué sur "Layout resource file" une fenêtre dans laquelle on peut définir notre nouveau layout s'ouvre.

### Pour qu'il soit utilisé automatiquement à l'utilisation

Pour créé la version horizontal du layout "authent", il faut selectionner l'"Available qualifiers" orientation  et lui définir l'orientation "Landscape" dans la fenêtre ouverte au point précédent et lui donner le même nom que le layout "authent".

Une fois cette étape réaliser le layout "authent" passera automatiquement du premier layout au second en fonction de l'orentation du smartphone.

## Question 8

onCreate() : Appeler lorsque le système crée l'activité.

onStart() : appeler lorsque l'activité devient visible pour l'utilisateur.

onResume() : appeler lorsque l'activité devient interactive avec l'utilisateur. 

onPause() : appeler lorsque l'activité n'est pas visible par l'utilisateur.

onStop() : appeler lorsque l'activité n'est plus visible par l'utilisateur.

Si on a une connexion Bluetooth ou autre, il serait préférable voir nécessaire d'allouer ces ressources lors de l'appel à onStart ou onResume, et libérer ces ressources lorsque l'on appel respectivement onStop ou onPause. Cela dans un but d'économie d'énergie et de partage des ressources.