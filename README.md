# Memo Git

### Bon à savoir ...

1) Les depots  

    - Depot local (Local Repository).
        - Le dépôt local est la copie du projet Git présente sur votre machine locale.

    - Depot distant (Remote).
        - Le dépôt distant est une copie du dépôt local située sur un serveur ou un service de gestion de code source

        - /!\ ATTENTION /!\
            - Pour pouvoir pousser des modifications sur le serveur, il est important de s’assurer que le repository local est à jour, c'est-à-dire qu’il a bien récupéré les dernières modifications. Si nous essayons de pousser des modifications alors que des modifications sur le serveur ne sont pas présentes en local, git nous générera une erreur.

2) Type de zones de stockages  
    - Workspace.
        - Répertoire de travail ou sont les fichiers non-modifiés et modifiés

    - Index ou zone de staging.
        - Zone intermédiaire avant le commit

    - Repository.
        - Le dépot ou est sauvegarder le projet

3) Les états de fichiers  

    - Untracked.
        - Non suivi, nouveau fichier pas encore indexer

    - Unmodified.
        - Fichier non modifié

    - Modified.
        - fichier à indéxer

    - Staged.
        - Fichier indéxer pret pour le commit  

####        
---
####

### Depuis un depot distant

- Cloner un dépot distant  
    - `git clone nom_du_depot_distant`

- Indexation de fichier ( fichier's' modifié's' )

    - Un fichier  
        - `git add nom_du_fichier`
    
    - Plusieurs fichiers  
        - `git add .` <- Ne pas oublier le point

- Faire un commit ( une fois les fichiers indexés )  
    - `git commit -m "Message du commit"`  
        - l'option "-m" permets de saisir un message en relation avec le fichier à commiter

- Envoyer les commits sur le depot distant  
    - `git push -u origin main`  
        - L'option -u définit la branche locale « main »

####        
---
####

### Depuis un depot local

- Créer un nouveau depot distant sur GitHub
- Créer un dossier projet et s'y rendre pour l'initialiser  
- Créer le fichier README.md  
    - `echo "# test_projet" >> README.md`

- Configurer la base de Git pour être lié à votre compte GitHub  
    
    - Configure le username  
        - `git config --global user.name "Nom_createur_du_repository"`

    - Configure l'email  
        - `git config --global user.email "Adresse_email"`
    
    - Active la coloration syntaxique  
        - `git config --global color.ui true`

- Initialiser le repository  
    - `git init`

- Indexer les fichiers  
    - `git add .`

- Faire le 1er commit  
    - `git commit -m "first commit"`  

- Ajouter le remote  
    - `git remote add origin <url_depot_distant>`  

- Envoyer les commits vers le depot distant  
    - `git push -u origin main`

####        
---
####

### Historique des commits

- Afficher l'historique des commits
    - `git log`

- Afficher l'historique des commits en mode "graph" 
    - `git log --graph`

- Afficher "x" commit  
    - `git log -3`
        - Affiche 3 commits

- Afficher 4 commits avec le detail des modifications
    - `git log -p -4`

- Afficher un commit specifique
    - `git show "identifaitn_du_commit"`

- Afficher des informations supplémentaires, telles que les noms de branches et les tags, aux commits
    - `git log --decorate`

- Filtrer par auteur
    - ` git log --author="<author>"`

- Filtrer par periode
    - `git log --since="2023-01-01" --until="2023-01-31"`

- Comparer 2 commits
    - `git diff "commit_1" "commit_2"`

- Comparer les différences entre le dernier commit et l’avant-dernier
    - `git diff HEAD HEAD~1`

-  rechercher des mots-clés spécifiques dans l’historique des commits
    - `git grep "mot_cle"`

- Quitter l'historique  
    - Appuyer sur "Q" pour quitter

####        
---
####

### Les branches  

     Une branche est une ligne de développement indépendante qui permet de travailler sur des modifications de manière isolée par rapport à la branche principale (généralement appelée « branche principale » ou « branche maître »).

- La création d'une nouvelle branche
    - `git branch <nom_de_branche>`
        
- Renomer une branche
    - `git branch -M main`
        - Cette commande renomme la branche principale (habituellement « master ») en « main »

- Basculer vers une branche existante
    - `git checkout <nom_de_la_branche>`

- Connaitre la liste des branches existantes
    - `git branch --list`

- Connaitre le SHA de la branche
    - `git rev-parse nom_de_la_branche`

- Supprimer une branche
    - `git branch -d "nom_de_la_branche"`

- Supprimer une branche sans fusion avec la branche principale
    - `git branch -D "nom_de_la_branche"`

- Comparer 2 branches
    - `git diff "branche_1" "branche_2"`

- Pousse les modifications de votre branche locale vers la branche correspondante sur la remote  
    - `git push <remote> <branche>`

- Récupère les modifications de la branche sur la remote et les fusionne dans votre branche locale  
    - `git pull <remote> <branche>`

####        
---
####

### Les fusions ( Merge/Rebase )

- Le merge

        Le git merge est une opération qui permet de fusionner 2 ou plusieurs branches en une seule, en créant un nouveau commit qui contient les modifications des branches fusionnées.
        
    - Se placer sur la branche principale "main"
        - `git checkout main`

    - Ensuite fusionée les deux branche  
        - `git merge branche_a_fusionneé`

    - En cas de conflit git le spécifira et la résolution devra etre faites à la main, une fois les conflits reglé éxecuter les commandes suivantes
        - `git add -A`
            - La commande git add -A est une commande Git qui permet d'ajouter tous les fichiers modifiés, supprimés et nouvellement créés à l'index Git

        - Finaliser le merge
            - `git merge --continue`

    - Utilisez la commande "git status" pour vérifier que les fichiers ont bien été ajoutés à l'index.
        - `git status`


- Le rebase

        Le git rebase est une opération qui permet de fusionner des branches, mais en réécrivant l'historique de développement de manière linéaire. Cette opération déplace tous les commits de la branche à fusionner en amont de la branche cible, ce qui crée un historique de développement plus facile à comprendre et à gérer. Cependant, le Git rebase peut être plus complexe à utiliser et peut provoquer des conflits lorsqu'il réécrit l'historique de développement.
        
    - Se placer sur la branche principale "dev"
        - `git checkout dev`

    - Ensuite fusionée les deux branches  
        - `git rebase main`

    - En cas de conflit git le spécifira et la résolution devra etre faites à la main, une fois les conflits reglé éxecuter les commandes suivantes
        - `git add -A`
            - La commande git add -A est une commande Git qui permet d'ajouter tous les fichiers modifiés, supprimés et nouvellement créés à l'index Git

        - Finaliser le merge
            - `git rebase --continue`

    - Utilisez la commande "git status" pour vérifier que les fichiers ont bien été ajoutés à l'index.
        - `git status`

####        
---
####

### Les fichiers

- Gitignore :

    - C’est un fichier texte qui contient une liste de règles de filtrage pour exclure certains fichiers et répertoires du suivi de Git

    - Un repository sur Github propose un certain nombre de fichier .gitignore pour divers langages ou aller sur "gitignore.io" en ligne pour en créer un personnel

####        
---
####

### Commandes utiles

- Afficher les informations sur l'état actuel du dépot si besoin  
    - `git status`

- Affiche la liste des remotes configurées pour votre dépôt local  
    - `git remote -v`
