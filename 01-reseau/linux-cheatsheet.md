# Aide-mémoire Linux

Commandes apprises en semaine 1 (terminal Kali). Les exemples utilisent des fichiers fictifs.

## Connexion
- `ssh utilisateur@hôte -p port` : se connecter à une machine distante. Exemple : `ssh alice@exemple.org -p 2222`
- `exit` : fermer la session et revenir à la machine précédente.

## Se repérer
- `pwd` : afficher le dossier courant.
- `ls -la` : lister tous les fichiers (cachés compris) avec droits, propriétaire et taille en octets. Exemple : `ls -la /etc`
- `cd dossier` : entrer dans un dossier ; `cd ..` remonte d'un niveau. Exemple : `cd /var/log`
- Touche Tab : complète automatiquement un nom de fichier ou de dossier.

## Lire et analyser un fichier
- `cat fichier` : afficher le contenu. Exemple : `cat notes.txt`
- `cat ./-fichier` : lire un fichier dont le nom commence par un tiret (le `./` évite qu'il soit pris pour une option). Exemple : `cat ./-notes`
- `cat "nom avec espaces"` : guillemets ou antislash devant chaque espace. Exemple : `cat "mon fichier.txt"` ou `cat mon\ fichier.txt`
- `file ./*` : donner le type de contenu de chaque fichier (texte, données...). Exemple : `file ./*`
- `wc -c fichier` : taille exacte en octets. Exemple : `wc -c notes.txt`
- `strings fichier` : extraire le texte lisible d'un fichier binaire. Exemple : `strings programme`

## Chercher et filtrer
- `find dossier -type f -size +1M` : chercher des fichiers par type et taille (`c` octets, `k` Ko, `M` Mo). Exemple : `find /var/log -type f -size +1M`
- `find / -user alice -group staff 2>/dev/null` : chercher par propriétaire et groupe ; `2>/dev/null` masque les erreurs de droits.
- `find . -type f ! -executable` : exclure les fichiers exécutables.
- `grep motif fichier` : afficher les lignes qui contiennent un motif. Exemple : `grep "erreur" journal.txt`
- `commande1 | commande2` : envoyer la sortie de la première commande à la seconde. Exemple : `strings programme | grep "http"`
- `sort fichier | uniq -u` : garder les lignes qui n'apparaissent qu'une fois (trier d'abord, car `uniq` ne compare que les lignes voisines). Exemple : `sort liste.txt | uniq -u`

## Décoder
- `base64 -d fichier` : décoder du contenu en base64. Exemple : `echo "Ym9uam91cg==" | base64 -d` affiche `bonjour`.
- Ajout de l'aide-mémoire Linux (semaine 1)
