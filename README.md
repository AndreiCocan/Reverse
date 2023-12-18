# Reverse engineering - Sujet de TP

## Installation

### Avec la VM
#### Installez VirtualBox

https://www.virtualbox.org/wiki/Downloads

Puis si vous êtes sur Linux :
`sudo dpkg -i <paquet>.deb`

#### Téléchargez ensuite les VM : // lien
- VM Kali (exos 1 et 2) : ~3 Go au téléchargement, 8 une fois déployée
- VM Windows (exo 3) : 

#### Ouvrez l'application VirtualBox.
- importer l'archive de la VM qui vous intéresse selon l'exercice auquel vous êtes rendus
- login / mdp : 
	- VM Kali : kali / kali
	- VM Windows : win / win

### Sans la VM
Si vous ne souhaitez pas utiliser la VM, vous aurez besoin pour les exercices 1 et 2 de :
- Ghidra : https://github.com/NationalSecurityAgency/ghidra
- gcc
- un IDE

Pour l'exercice 3 :
- Windows
- dnSpy : https://github.com/dnSpy/dnSpy

Nous fournirons le contenu des exercices si vous êtes dans ce cas. C'est particulièrement pour éviter l'installation pénible de Ghidra que la VM est fournie, et pour que tout le monde dispose du même environnement.

## Exercices
Sur la VM Kali, vous trouverez sur le bureau un dossier `Reversing` et 2 sous-dossiers, un par exercice.

### Exercice 1

Dans le dossier `1`, vous trouverez l'exécutable d'un programme `INSA_entry_test`. Vous pouvez l'exécuter dans un terminal. Le but de l'exercise est de passer les trois épreuves (récupérer 3 mots de passe).

**Puisque l'exécutable vérifie les mots de passe que vous entrez, vous allez décompiler son code avec Ghidra, et essayer de retrouver les mots de passe dans le code décompilé.**

Pour cela, ouvrez un terminal et exécutez la commande

```bash
ghidra
```

Dans la fenêtre qui s'ouvre, faites File > New project. Sélectionnez 'Non-shared project' puis 'Next'. Choisissez ensuite le répertoire où vous créez votre projet Ghidra, où vous le souhaitez, avec le nom que vous voulez.
Cliquez ensuite sur la tête d'hydre verte (CodeBrowser) dans le Tool Chest. Une nouvelle fenêtre va s'ouvrir.

Glissez-déposez l'exécutable sur cette fenêtre. Dans les pop-up successives, cliquez sur OK > Yes > Analyze > OK sans modifier les paramètres affichés. Vous allez maintenant pouvoir parcourir le code décompilé.

// image d'illustration

La fenêtre est subdivisée en plusieurs parties. Au milieu vous trouverez l'assembleur de l'exécutable. A gauche, vous trouverez notamment le Symbol Tree. Ouvrez le dossier 'Functions' et double-cliquez sur 'main' pour trouver le point d'entrée de votre programme. Ghidra affiche dans la partie à droite le code reconstitué à partir de la décompilation (cela vous évitera de lire de l'assembleur).

<details><summary>Indice 1</summary>
Suite du walkthrough
</details>

<details><summary>Indice 2</summary>
Suite du walkthrough
</details>


### Exercice 2

Dans le dossier `2`, vous trouverez l'exécutable du 'malware' `totally_normal_binary` qui a chiffré un message que vous aviez reçu et n'avez pas eu le temps de lire, `encrypted.txt` (pour plus de détails sur le lore, lisez le `README.md` présent dans le dossier).

Pour déchiffrer le message, vous pourriez essayer de décompiler le malware afin de comprendre sa fonction de chiffrement. La fonction de déchiffrement sera la fonction inverse.

Dans Ghidra, de la même façon que précédemment, glissez-déposez l'exécutable `totally_normal_binary` et analysez-le pour pouvoir parcourir le code décompilé. Trouvez la fonction 'main'.

Dans cette fonction, vous devriez pouvoir identifier une fonction qui vous intéresse... Double-cliquez dessus pour afficher son code reconstitué. Tentez de comprendre la fonction pour trouver sa fonction inverse.

Vous n'aurez plus qu'à coder un programme C avec la fonction inverse, le compiler et l'utiliser sur `encrypted.txt` pour déchiffrer le message.

<details><summary>Indice 1</summary>
Suite du walkthrough
</details>

<details><summary>Indice 2</summary>
Suite du walkthrough
</details>


### Exercice 3

Eteignez maintenant la VM Kali en fermant la fenêtre et lancez la VM Windows. Vous trouverez sur le bureau un dossier `dnSpy` et le dossier `Reverse`. Ouvrez `dnSpy` et lancez l'exécutable. Ouvrez `Reverse`, vous y trouverez un exécutable `UltimateVault`. Glissez-déposez `UltimateVault` sur la fenêtre de dnSpy. 

Dans cet exercice, de la même façon qu'avec Ghidra, vous pourrez parcourir le code décompilé, mais aussi utiliser un debugger pour marquer des points d'arrêts.

// image d'illustration

<details><summary>Indice 1</summary>
Suite du walkthrough
</details>

<details><summary>Indice 2</summary>
Suite du walkthrough
</details>


## Conclusion

Félicitations ! Vous êtes un agent émérite de l'I.N.S.A.

Pour retrouver votre espace de stockage libre initial, faites un clic droit sur les VM dans VirtualBox puis 'Supprimer'.
Supprimez également les archives des VM là où vous les aviez enregistrées.
Désinstallez ensuite VirtualBox si vous le souhaitez.
