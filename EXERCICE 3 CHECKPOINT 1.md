 GNU nano 7.2                                                                                                  addUsers.sh                  Fait à la maison en 3h ..... ( plus 40 minspour mettre en forme le .md )                                                                                        

1)pseudo code :

$# représente le nombre d'argument donné en lançant le script.
on fait une condition qui rejette le nombre d'argument si il est nul, et on informe de quel manière il faut indiquer les noms de nouveaux utilisateurs.
Puis  pour chaque argument $# on fait correspondre un nom d'utilisateur à créer .
on verifie si cet user dans la liste d'utilisateur existe déjà et si oui on informe et on passe à l'argument suivant .
on crée le nouvel utilistaur, si c'est bon on informe que le nouvel user a été créé et si il n'est pas dans la nouvel liste c'est qu'il y a un problème et on sort en informant.

ca donne ca mais ca peut être améliorer je sais mais la je sature ...;


````
#!/bin/bash

if [ "$#" -eq 0 ]
then
echo "mettez les arguments avant de lancer le script de cette manière  : $0 user1 user2 ..."
exit 1
fi
#on boucle maintenant sue le nombre d'argument.
#il faut passer du'numero de l'argument ' au nom d'utilisateur 
    for user in "$@"
    do
        if id "$user" >/dev/null
        then
        echo "Utilisateur $user existe déjà"
        else
        echo "OK pour crée "$user""
        useradd "$user"
        echo "utilsateur "$user" créé"
            if id "$user" >/dev/null
            then
            echo "utilsateur "$user" créé"
            else
            echo "Erreur à la création de l'utilisateur "$user""
            exit 1
	        fi 
        fi

	done
	exit 0





```



