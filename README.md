# JAVASCRIPT_WEB_REACTIVE
<!-- TOC -->

- [JAVASCRIPT_WEB_REACTIVE](#javascript_web_reactive)
- [Le debogage](#le-debogage)
    - [Acces a la console de degogage dans un navigagueur](#acces-a-la-console-de-degogage-dans-un-navigagueur)
    - [Degogage mobile](#degogage-mobile)
- [Degogage des styles](#degogage-des-styles)
    - [Selectionner un element du DOM](#selectionner-un-element-du-dom)
    - [Modifier le contenu d'un element du DOM](#modifier-le-contenu-dun-element-du-dom)
    - [L'onglet style](#longlet-style)
    - [L'onglet computed](#longlet-computed)
- [Debogage du javascript](#debogage-du-javascript)
    - [Onglets sources](#onglets-sources)
    - [Navigation dans le code](#navigation-dans-le-code)
    - [Les points d'arrets](#les-points-darrets)
    - [Beakpoint avances](#beakpoint-avances)
    - [La console](#la-console)
        - [Log et interpolation](#log-et-interpolation)
        - [Level et groupe](#level-et-groupe)
        - [Compteur de temps](#compteur-de-temps)
        - [Les tableaux](#les-tableaux)
        - [Debug](#debug)
- [Le reseau](#le-reseau)
    - [Usage avance du network](#usage-avance-du-network)
- [Application](#application)
- [Pour aller plus loin](#pour-aller-plus-loin)

<!-- /TOC -->
# Le debogage

Le debogage peux etre necessaires dans les cas suivant:
* Elements qui ne s'affichent pas ou qui est mal places, mauvaises couleur ...
* Une fonctionnalite defectueuse
* La securite que l'on souhaite eprouve

## Acces a la console de degogage dans un navigagueur

Connectez-vous a votre navigagueur (Chrome, firefox, edge) et taper sur la touche F12, ou bien cliquer sur les 3 petits points et cliquer sur Plus d'outil > outils de developpement.

![DEGOGUEUR](resources\degogue.bmp)

## Degogage mobile

Vous pouvez soit utiliser la precedente console en allant sur votre navigagueur de mobile et appuyer sur F12 soit emuler un terminal de degogage

# Degogage des styles

* L'onglet element de la console de degogage permet de visualiser a droite la partie html du site le DOM et a droite la partie CSS.
* Dans la partie de gauche (Element) nous pouvons mettre en surbrillance l'element selectionne en les survolant et deployer le contenu des balises pour les explorer.
* Dans la partie de droite, nous avons les onglets:
    * Styles: correspondant au style CSS de l'element selectionne.
    * Computed: corespondant au propriete CSS calcule apres application des regles.
    * Event listeners correspondant a la liste des listener present sur cet element selectionner.
    * DOM Breakpoints, le cas echeant lors de mise en place de breakpoint dans l'executio ndu code js.
    * Properties de l'element selectionner.
    * Accessibility les informations sur l'element selectionne.

## Selectionner un element du DOM

Vous pouvez soit: cliquer droit et faire inspecter soit cliquer dans la console de degogage sur la fleche de selection puis selectionner l'element de la page html ou enfin chercher dans les differents elements afficher dans le code html de la console de degogage.

## Modifier le contenu d'un element du DOM

Une fois l'element selectionne dans la console de degogage, vous pouvez:
* directement changer le contenu de celui-ci.
* masquer son contenu (Hide element)
* supprimer l'element (delete element)
* faire copy JS path puis dans la console faire coller. Nous avons ainsi creer un selecteur que nous pourrons reutiliser directement dans du code javascript.

## L'onglet style

L'onglet style, nous permet de travailler le css de notre page. 
Nous pouvons modifier les proprietes css directements (supprimer , ajouter , modifier ..).
Nous pouvons aussi creer un style css propre a l'element en editant la partie element.style (a la difference de l'element css du groupe).
Sur un element ayant une propriete d'effet dynamique (hover, active, focus ...) nous pouvons simuler celui-ci en cliquant dans la console sur :hov, se qui deplis des options de simulations.

## L'onglet computed

nous pouvons filter les proprietes css et ainsi acceder aux valeurs et styles appliques aux l'elements concernes, puis en cliquant sur la fleche, nous sommes directement dirige vers cette proprietes que nous pourrons changer a la vole.

# Debogage du javascript

Javascript n'est pas simple, il n'est pas type, est asynchrome et a un heritage par prototype.

## Onglets sources

Presente 3 grandes partie:
* a gauche l'arborescence des differents fichiers impliques dans le rendu de la page
* au centre une vue du contenu du code
* a droite les differents outils de debogage:
    * le controle de l'execution du code
    * watch : surveille le contenu des variables et retour de fonction
    * call stack: le chemin empreinte pour arrive a notre breakpoint
    * scope: representant les differentes variables et leurs scopes
    * breakpoint: presentant la liste des brekpoints.

## Navigation dans le code

3 solutions:
* utiliser le raccourci clavier CTRL+P puis taper le nom du fichier recherche.
* naviguer dans l'arborescence de droite pour rechercher le fichier.
* lorsque nous avons un message dans la console, cliquer dessus pour etre dirige vers le code. Et cliquer au besoin sur m'option {} pour avoir le bon format (reformatage du fichier a l'aide de pretty-print).

## Les points d'arrets

On ajoute un point d'arret dans la console de debogage sur le fichier main.js (par exemple).
Apres reexcution de la page le code s'arrete au breakpoint.
Dans la rubrique call stack nous pouvons voir le cheminement d'execution du code.
A des fin de visibilite nous pouvons "black box" les partie jquery par exemple en cliquant dessus et selectionnant "Blackbox script".
Si vous voulez remettre les blackbox precedent cliquer sur Setting > Blackboxing et les editer, supprimer ou modifier.
Nous pouvons observer lors d'un breakpoint le contenu des variables dans la rubrique scope et variable global.
Et voir les differents types de closure.
Pour executer le code pas a pas il faut cliquer sur step over de la barre de lecture.
Nous pouvons ajouter des watch sur des expressions qui seront evalue oubien sur des variables.

## Beakpoint avances

Differents point d'arret avances existent. Point d'arret:
* Conditionnel. Cliquer droit sur le breakpoint et faire "Edit breeakpoint" pour y ajouter votre condition (ex: person.name==="paul").
* XHR. Lorsque le code fait un appel au serveur, vous pouvez ajouter un XHR/fetch Breakpoints et y ajoutert une partie de l'url. Lors de l'appel le code s'arretera 
* Modification du DOM. Exemple lors d'un affichage d'une liste apres l'action sur un bouton.
* Listener d'event. Il suffit de selectionner dans la section de droite "Event Listener Breakpoints" le type d'event que l'on souhaite surveiller exemple sur "click". 
* Programmatique. Il suffit de taper dans le code source le mot "`debugger`", rafraichire la page de votr enavigateur avec la console de debug ouverte. Le programme s'arretera a la ligne debug lors de son execution.
* Exception. Lors de l'execution du code si une exeption est leve, celle-ci sera visible dans la console de debug et vous pouvez cliquer sur le bouton "pause on exception" si vous desirez avoir un point d'arret systematique lors d'une exception. Un arret sera effectue meme si l'exception n'est pas explicite, cad, si l'exception est du a une erreur de programmation (ex: null pointer exception).

## La console

### Log et interpolation

Les extraits de code suivant generent des message dans la console de debug suivant

```js
//simple console.log
console.log("Hello world")
    `Hello world`
// interpolation dans les console.log
// String
console.log("Je suis une chaine de caratere %s", "interpolé")
    `Je suis une chaine de caratere interpolé`
// double et float
console.log("Nous avons en decimal %d et en flottant %f",42,3.1415)
    `Nous avons en decimal 42 et en flottant 3.1415`
// objet
let excellent = {
    age: 42,
    poids: 70,
    nom:"Albert"
}
console.log("Avec un objet excellent !!: %O", excellent)
`Avec un objet excellent !!: Object`
// selection d'un element du DOM
console.log("ou un element du DOM html : %o",document.getElementById("bigbutton"))
`<a class="btn btn-primary btn-lg" href="#" role="button" id="bigbutton">Click Me </a>`
```
### Level et groupe

```js
console.log("simple log");
console.info("un log d'information");
console.warn("un log d'alerte");
console.log("une log d'erreur")
```
![consoleloglevel](resources\consolelog.bmp)

```js
console.group("Commencer le 1er groupe avec console.group de niveau 1");
console.log("console.log du niveau 1");
console.log("autre console.log du niveau 1");
console.log("autre console.log du niveau 1");
console.group("Suivi d'un 2eme groupe avec console.group de niveau 2");
console.log("console.log du niveau 2");
console.log("autre console.log du niveau 2");
console.groupEnd();
console.log("Nous retournons au niveau -1 , cad 1");
console.groupEnd();
console.log("Nous sommes hors du groupe");
```
![consoleloggroup](resources\group.bmp)

### Compteur de temps

Exemple de durée

```js
console.time("duree de concatenation");
output =0;
for(i=1;i<1e6;i++)
	output += i;
console.timeEnd("duree de concatenation");
console.time("asynchrone");
setTimeout(function(){
    console.timeEnd("asynchrone");
}, 2000);
```
![consolelogduree](resources\time.bmp)

Exemple de compteur

```js
nbBoucle = 7;
for(var foo = 0; foo < nbBoucle;foo++)
console.count("Combien de fois avons-nous parcouru la boucle ? : ");
```
![consolelogcompteur](resources\time_count.bmp)

Exemple de trace

```js
console.trace("Nous generons une trace");
```

### Les tableaux

Exemple:
![consolelogtable](resources\tableau.bmp)

### Debug

Dans la console, lors d'un point d'arret, nous pouvons appeler des fonctions, consulter les elements du Dom.

# Le reseau

L'onglet network permet d'analyser les echanges entre le navigateur et les differents serveurs.

![consolelognetwork](resources\network.bmp)

## Usage avance du network

Vous pouvez de plus:
* `filter` suivant le type css, media ...
* utiliser le moteur de recherche.
* `preserve log` permettant de garder un historique de navigation.
* `disable cache` permettant de ne pas travailler avec les headers de cache afin de s'assurer de travailler averc les derniers fichier.
* `online` permet de simuler une connexion plus lente , par exemple, ou fast 3G ...

# Application

Permet de gerer l'environnement des applications

# Pour aller plus loin

* Un enregistrement vidéo d'une conférence sur le sujet : https://www.youtube.com/watch?v=UNURXC9pqKY
* Une autre conférence : https://www.youtube.com/watch?v=par742RHhVM
* La documentation des devtools de Chrome : https://developers.google.com/web/tools/chrome-devtools
* La documentation des devtools de Firefox : https://developer.mozilla.org/fr/docs/Outils
* La documentation des devtools de Edge : https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide
* Pour des démonstrations d'utilisation avancée des outils de performance, vous pouvez consulter le blog de Addy Osmani : https://medium.com/@addyosmani
