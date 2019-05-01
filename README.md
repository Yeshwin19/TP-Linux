# TP-Linux

# Le jeu de plus ou moins.

#!/bin/bash
secretNumber=$(( ((`date +%N` / 1000) % 100) +1 ))     `#The secretnumber is derived by taking today's date, dividing it by 1000,making a modulo of 100 out of it and then adding 1 to it.`

guess=-1                                               `#Initialise the numberoff guess.`
while [ "$guess" != "$secretNumber" ]; do              `#If guess is not equal to secretnumber then print the message below.`
    echo -n "I am thinking of a number between 1 and 100. Enter your guess:"
    read guess                                         
    if [ "$guess" = "" ]; then                         `#This is to deal with exceptions in case a letter is inserted.`
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
DATE=$(date +%Y-%m-%d-%H%M%S)       `#Thisi s done so that several backups can be safely separated from one another. The variables are given the following format, for example: Year-Month-Day-HourMinuteSecond, so for example 2017-09-07-152833.`

BACKUP_DIR="/targetdirectory/backup" `#Here I specified the directory in which the backup should be created. The last subdirectory is not ended with “/”, though.`

SOURCE="$HOME/sourcedirectory"    `#n this line, I specified which directories you want to include in the archive.`

tar -cvzpf $BACKUP_DIR/backup-$DATE.tar.gz $SOURCE  `#-cvzpf creates an archive (-c), the steps are displayed (-v), it’s compressed with gzip (-z), the access rights are retained (-p), and everything is output in the following file (-f). To finish up, inform tar using the variable $SOURCE what should absolutely archive. It’s conceivable that you can also exclude directories or files with --exclude or -X that don’t need to be included in the backup. $BACKUP_DIR/backup-$DATE.tar.gz denoted the directory ($BACKUP_DIR) and the file in which the backup should be saved.`
