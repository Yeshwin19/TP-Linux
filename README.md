# TP-Linux

# Le jeu de plus ou moins.

#!/bin/bash

secretNumber=$(( ((`date +%N` / 1000) % 100) +1 ))     `#Le numéro secret est obtenu en prenant la date du jour, en la divisant par 1000, en en faisant un modulo de 100 puis en lui ajoutant 1.`

guess=-1                                               `#Initialiser le nombre de guess.`

while [ "$guess" != "$secretNumber" ]; do              `#Si devine n'est pas égal à secretnumber, imprimez le message ci-dessous.`
    echo -n "I am thinking of a number between 1 and 100. Enter your guess:"
    
   read guess                                         
    
   if [ "$guess" = "" ]; then                         `#ça c'est pour gérer les exceptions.`
        
   echo "Please enter a number."
    
   elif [ "$guess" = "$secretNumber" ]; then           
        
   echo -e "\aYes! $guess is the correct answer!"
    
   elif [ "$secretNumber" -gt "$guess" ]; then
        
   echo "The secret number is larger than your guess. Try again."
    
   else
        
   echo "The secret number is smaller than your guess. Try again."
    
   fi

done



## Outil de sauvegarde.

#!/bin/bash

DATE=$(date +%Y-%m-%d-%H%M%S)       `#Ceci est fait pour que plusieurs sauvegardes puissent être séparées en toute sécurité. Les variables ont par exemple le format suivant: Year-Month-Day-HourMinuteSecond, par exemple 2017-09-07-152833`

BACKUP_DIR="/targetdirectory/backup" `#Ici, j'ai spécifié le répertoire dans lequel la sauvegarde devrait être créée. Le dernier sous-répertoire ne se termine pas par “/”, bien que.`

SOURCE="$HOME/sourcedirectory"    `#Dans cette ligne, j'ai spécifié quels répertoires vous souhaitez inclure dans l'archive.`

tar -cvzpf $BACKUP_DIR/backup-$DATE.tar.gz $SOURCE  `#-cvzpf crée une archive (-c), les étapes sont affichées (-v), compressées avec gzip (-z), les droits d'accès sont conservés (-p) et tout est affiché dans le fichier suivant (-f). . Pour finir, informez tar en utilisant la variable $ SOURCE ce qu’il faut absolument archiver. Il est concevable que vous puissiez également exclure des répertoires ou des fichiers avec --exclude ou -X qui n’ont pas besoin d’être inclus dans la sauvegarde. $ BACKUP_DIR / backup- $ DATE.tar.gz désignait le répertoire ($ BACKUP_DIR) et le fichier dans lequel la sauvegarde devait être sauvegardée.`


## Youtube-dl.

#!/bin/bash

youtube-dl -x https://www.youtube.com/watch?v=kda8QGA3i-c   `#C’est la ligne de commande qui permet de télécharger une vidéo à partir de YouTube puis d’extraire la musique de la vidéo.`
