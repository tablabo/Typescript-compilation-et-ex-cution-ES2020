# Typescript-compilation-et-ex-cution-ES2020
Salut, à la fin de ce document vous allez apprendre à mettre en place l’environnement de base pour les applications cotée serveur dit (Backend Applications) en anglais, aussi nommée API (Application Programming Interface) et automatiser la compilation de Typescript dans Visual Code Studio. Donc je vous invite a gardé précieusement ce document dans votre caisse a outil de développeur.

## Installation

- `git clone https://github.com/tablabo/Typescript-compilation-et-ex-cution-ES2020.git` - cloner le répertoire
- `npm install` - installer
- `npm run build` - pour compilation
- `npm run dev` - pour éxecution


* Etape 01


# Note: La taille totale du projet fini est de : 3,0 Mo
# Ctrl-Shift-p et choisir (Create New Intergrated Terminal)
# ouvrir le cmd est créer un dossier intitulé serveur
~$ mkdir serveur/
# naviguer dans le dossier
~$ cd serveur/ 
# exécuter la commande npm init --yes
~$ npm init --yes
# Remarque un fichier intitulé package.json est créer
# Voire Aperçu suivant:
------------------------------------------------------------------
# Créer un dossier intitulé (src) 
~$ mkdir src/
# créer aussi un fichier (index.ts) dans le répertoire src/
~$ touch src/index.ts # écrire dans le fichier index.ts
~$ echo "console.log('IT WORKS!')" >> src/index.ts 
# Voire Aperçu suivant :
{
  "name": "serveur",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
----------------------------------------------------------------
# Pour obtenir la commande (tsc) installer typescript
# ouvrir le cmd est tapé (npm install g typescript) "g" pour global
~$ npm install g typescript
# En suite en en exécute (tsc --init) 
# Cette commande ajoute un fichier intitulé (tsconfig.json)
# Ouvrir ce dernier pour édition
# Chercher la ligne ("target": "es5") remplacé  es5 avec es6
# Chercher la ligne (//"outDir": "./") remplacé ("outDir": "./build")
# Basculer vers le terminal 
# Exécuter la commande (tsc)
--------------------------------------------------------------
* Etape 02
**  Après exécution de la commande (tsc) le Typescript est compiler en JavaScript, remarquer le nouveau dossier (build) et fichier (index.js) créer. Dans la troisième étape nous automatiseront le processus de la compilation par l'ajout d'une ligne de code au fichier package.json.
---------------------------------------------------------------
* Etape 03
** Dans cette troisième étape nous automatiseront le processus de la compilation par la modification d’une ligne de code au fichier package.json, à la ligne numéro 6. Supprimer la ligne \mintinline{latex}{("test":"echo \"Error: no test specified\" && exit 1")} et remplacer avec \mintinline{latex}{("build":"tsc -w")},  prière de ne pas copier les parenthèses.
{
  "name": "serveur",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "build": "tsc -w"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}

--------------------------------------------------------------
* Etape 03

** Maintenant chaque foi que le fichier (index.ts) est modifié, typescript écrit les modifications sur (index.js), donc la compilation est automatique.
--------------------------------------------------------------

* Etape 03
** Pour automatiser l'exécution des fichiers JS on installe un package appeler Nodemon avec la commande \mintinline{latex}{ $ npm install nodemon -D} Puis ajouter le code \mintinline {latex}{ "dev": "nodemon build/index.js"  } comme afficher dans le fichier package.json a la ligne 7:
{
  "name": "serveur",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "build": "tsc -w",
    "dev": "nodemon build/index.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}

-------------------------------------------------------------
Etape 03
** À la fin pour tester le tous, il va falloir ouvrir deux sessions dans le terminal, dans la première tapée \mintinline{latex}{$  npm run build }, et dans la deuxième tapé \mintinline{latex}{$  npm run dev}, puis juste ajouter du code dans index.ts est enregistré, le tous sera compilé est exécuté automatiquement, comme l'indique le titre du document.