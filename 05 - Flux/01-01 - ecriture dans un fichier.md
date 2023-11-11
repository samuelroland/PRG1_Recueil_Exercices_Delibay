# Sauvegarde de texte dans un fichier

Écrivez un programme en C++ qui fait ce qui suit :

- Demandez à l'utilisateur de saisir le nom du fichier de sortie.
- Si le fichier existe déjà, il ne doit pas être écrasé.
- Demandez à l'utilisateur de saisir du texte et enregistrez le texte saisi dans le fichier de sortie. Répétez cette action tant que l'utilisateur n'a pas terminé. 
- Pour terminer la saisie, l'utilisateur pourra tapez #exit# dans une ligne séprée ou utiliser Ctrl+D.
- Assurez-vous que le programme gère les erreurs d'ouverture de fichier.

Ps : simlulation du *EOF* (End of File)<br>
- Ctrl+D et Ctrl+Z sur Unix et Windows, respectivement.<br>
- Cmd+D sur Mac

<details>
<summary>Solution</summary>

~~~cpp
#include <iostream>
#include <fstream>
#include <string>

int main() {
    std::string nom_fichier;

    // Demandez à l'utilisateur le nom du fichier où enregistrer le texte
    std::cout << "Entrez le nom du fichier où enregistrer le texte : ";
    std::getline(std::cin, nom_fichier);

    // Ouvrez le fichier en mode écriture
    std::ofstream fichier_sortie(nom_fichier, std::ios::app);

    // Vérifiez si l'ouverture du fichier a réussi
    if (!fichier_sortie) {
        std::cerr << "Erreur : Impossible d'ouvrir le fichier. \n";
        return EXIT_FAILURE;
    }

    std::string texte;
    const std::string terminer = "#exit#";

    // Demandez à l'utilisateur de saisir du texte
    std::cout << "Entrez le texte à enregistrer dans le fichier (Ctrl+D ou #exit# pour terminer la saisie) :\n";
    while (std::getline(std::cin, texte)) {
        if (texte == terminer) break;
        // Écrivez le texte dans le fichier
        fichier_sortie << texte << std::endl;
    }

    // Fermez le fichier
    fichier_sortie.close();

    std::cout << "Le texte a été enregistré avec succès dans le fichier." << std::endl;

    return EXIT_SUCCESS;
}

~~~



</details>
