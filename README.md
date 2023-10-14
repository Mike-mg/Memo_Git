1) Cloner un dépot distant  
    `git clone <nom_du_depot_distant>`

    - Initialisation du projet.
        - git init
        
        
        
        

    - Afficher les informations sur l'état actuel du dépot si besoin.
        - git status"





- Type de zones de stockages :

    - Workspace.
        - Répertoire de travail

    - Index ou zone de staging.
        - Zone intermédiaire avant le commit

    - Repository.
        - Le dépot ou est sauvegarder le projet



- Les états :

    - Untracked.
        - Non suivi, nouveau fichier pas encore indexer

    - Unmodified.
        - Fichier non modifié

    - Modified.
        - fichier à indéxer

    - Staged.
        - Fichier indéxer pret pour le commit



- Indexation de fihcier :

    - Un fichier.
        - git add <nom_du_fichier>

    - Plusieurs fichiers :
        - git add . <- Ne pas oublier le point



- Faire un commit ( une fois les fichiers indexés ):

    - git commit -m "Message du commit" <- l'option "-m" permets de saisir un message en relation avec le fichier à commiter



- Fichier gitignore :

    - C’est un fichier texte qui contient une liste de règles de filtrage pour exclure certains fichiers et répertoires du suivi de Git

    - Un repository sur Github propose un certain nombre de fichier .gitignore pour divers langages ou aller sur "gitignore.io" en ligne pour en créer un personnel



- Depot local et distant :

    - Depot local (Local Repository).
        - Le dépôt local est la copie du projet Git présente sur votre machine locale.

    - Depot distant (Remote).
        - Le dépôt distant est une copie du dépôt local située sur un serveur ou un service de gestion de code source

    - Commandes utiles :

        - Ajoute une nouvelle remote avec le nom spécifié et l'URL du référentiel distant
            - git remote add <nom> <url>

        - Affiche la liste des remotes configurées pour votre dépôt local
            - git remote -v

        - Pousse les modifications de votre branche locale vers la branche correspondante sur la remote.
            - git push <remote> <branche>

        - Récupère les modifications de la branche sur la remote et les fusionne dans votre branche locale.
            - git pull <remote> <branche>

        /!\ ATTENTION /!\

        - Pour pouvoir pousser des modifications sur le serveur, il est important de s’assurer que le repository local est à jour, c'est-à-dire qu’il a bien récupéré les dernières modifications. Si nous essayons de pousser des modifications alors que des modifications sur le serveur ne sont pas présentes en local, git nous générera une erreur.



- Les branches :

    - Une branche est une ligne de développement indépendante qui permet de travailler sur des modifications de manière isolée par rapport à la branche principale (généralement appelée « branche principale » ou « branche maître »).

    - Commandes utiles :

        - La création d'une nouvelle branche
            - git branch <nom_de_branche>
        
        - Renomer une branche
            - git branch -M main <- cette commande renomme la branche principale (habituellement « master ») en « main »

        - Basculer vers une branche existante
            - git checkout <nom_de_la_branche>


- Les fusions (Merge/Rebase):

    - Le merge

        - Il s'agit du processus de fusion de deux branches différentes, généralement dans le but de combiner les modifications apportées sur ces branches et de créer un nouveau commit intégrant ces changements.

    - Commandes utiles :
    
     - *****
     - *****
     - *****
     - *****
     - *****

     
     
- Brancher un dépôt distant :

    - Commande pour ajouter une référence à un dépôt distant appelé « origin »
        - git remote add <origin> <depot_distant>
        
    - Commande qui envoie vos commits locaux vers le dépôt distant spécifié par « origin ». L'option -u définit la branche locale « main » comme branche de suivi pour la branche « main » du dépôt distant
        - git push -u <origin> <main>

        
        
- Configurer la base de Git pour être lié à votre compte GitHub :

    - git config --global user.name "Nom d'utilisateur GitHub" <- configure le username
    - git config --global user.email "Adresse email GitHub" <- configure l'email
    - git config --global color.ui true <- Active la coloration syntaxique










