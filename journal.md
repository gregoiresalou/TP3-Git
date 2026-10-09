**1; Un dépôt neuf**
* Phrase affichée par git status sans commit : "No commits yet"
* Ce que Git dit de src/ : il affiche "src/" (le dossier) et non "src/App.java", car le dossier entier est non suivi
* Contenu de .git/ (ls -a .git) : 9 entrées en comptant . et .. sinon 7 : config, description, HEAD, hooks, info, objects, refs
* Entrée qui indique la branche courante : HEAD
* Entrée qui stocke le contenu : objects

**2. Le trajet d'un fichier, prédit puis vérifié**
* Prédiction de la paire : untracked/untracked
* Résultat réel après git status : untracked/untracked

**Étape git add README.md**
* Prédiction de la paire : staged/unmodified
* Résultat réel après git status : staged/unmodified 

**Étape Modification sans refaire git add**
* Prédiction de la paire : staged/modified
* Résultat réel après git status : staged/modified
* Combien de fois README.md apparaît-il ? : 2 fois
* Dans quelles sections ? : dans "Changes to be committed" et dans "Changes not staged for commit" 

**Étape Premier commit**
* Prédiction de la paire : unmodified/modified
* Résultat réel après git status : unmodified/modified (l'index est identique au dernier commit, mais le répertoire de travail contient encore la modification de l'étape 5)
* Que reste-t-il à l'écran ? : README.md en "modified" sous "Changes not staged for commit", et journal.md, pom.xml, src/ en untracked. 

**Étape Ajout puis commit du README**
* Prédiction de la paire : unmodified/unmodified
* Résultat réel après git status : unmodified/unmodified (README.md n'apparaît plus dans git status : l'index, le dernier commit et le répertoire de travail sont identiques). Il ne reste que journal.md, pom.xml et src/ en untracked.

**3. La vue courte**
* Que représente la première colonne ? : l'état du fichier dans la zone d'index, comparé au dernier commit (ce qui est prêt à être commité)
* Que représente la deuxième colonne ? : l'état du fichier dans le répertoire de travail, comparé à l'index (ce qui est modifié mais pas encore indexé)
* Code exact pour pom.xml : "A " 
* Code exact pour README.md : "MM" 
* Code exact pour src/App.java : "??" 

**4. Sortir de l'index**
* Commande trouvée dans la sortie de git status : git restore --staged README.md
* Résultat : README.md passe de "MM" à " M" dans git status -s
* Zone où se trouve le fichier après : le répertoire de travail uniquement (modifié, non indexé). Il n'est plus dans l'index, et ses modifications sont conservées.


* Nombre de commits : 2
* Sept caractères du commit le plus récent : d94ca85

**Sortie de git log --oneline**
d94ca85 (HEAD -> master) Complète le README
d4da004 Ajoute le README