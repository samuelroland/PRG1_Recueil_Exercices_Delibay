# Affichage de caractères compris entre 2 bornes
Ecrire une fonction qui prend 2 paramètres de type *char* et qui affiche, sur une même ligne, tous les caractères non accentués compris entre deux paramètres *debut* et *fin*, bornes comprises.
</br>Rien n'est affiché si *debut* > *fin*.

Exemples

- listerCaracteres('A', 'A') => A
- listerCaracteres('A', 'C') => ABC 
- listerCaracteres('B', 'A') => 
- listerCaracteres('0', '9') => 0123456789
- listerCaracteres(65, 67)   => ABC

La fonction retourne un booléen indiquant si des caractères ont été affichés.

<details>
<summary>Solution</summary>

~~~cpp
#include <cstdlib>
#include <iostream>

using namespace std;

bool listerCaracteres(char debut,
                      char fin);

int main() {
   int n;

   cout << "1) 'A' => 'A' : ";
   n = listerCaracteres('A', 'A');
   cout << endl;

   cout << "2) 'A' => 'C' : ";
   n = listerCaracteres('A', 'C');
   cout << endl;

   cout << "3) 'B' => 'A' : ";
   listerCaracteres('B', 'A');
   cout << endl;

   cout << "4) '0' => '9' : ";
   listerCaracteres('0', '9');
   cout << endl;

   cout << "5) 65  => 66  : ";
   listerCaracteres(65, 66);
   cout << endl;

   cout << "6) 147 => 155 : ";
   listerCaracteres('\x93', '\x9B');
   cout << endl;

   cout << "7) 120 => 127 : ";
   listerCaracteres(120, 127);
   cout << endl;

   cout << "8) 120 => 140 : ";
   listerCaracteres(120, 140);
   cout << endl;

   cout << endl;
   cout << "/!\\ DANGER" << endl;
   cout << "\tint(char(65))  : " << int(char(65))  << endl
        << "\tint(char(127)) : " << int(char(127)) << endl
        << "\tint(char(128)) : " << int(char(128)) << endl;
   cout << ".. sera vu plus tard dans le cours."   << endl;

   cout << endl;
   cout << "Fin des tests" << endl;
   return EXIT_SUCCESS;
}

//------------------------------------------------------------
bool listerCaracteres(char debut,
                      char fin) {

   // /!\ boucle infinie si signed char et fin=127
//   for (char c = debut; c <= fin; ++c)
//      cout << c;

   if(debut > fin)
      return false;

   int n = fin - debut + 1;
   for(int i = 0; i < n; ++i, ++debut) {
      cout << debut;
   }

   return true;
}

//
//      1) 'A' => 'A' : A
//      2) 'A' => 'C' : ABC
//      3) 'B' => 'A' :
//      4) '0' => '9' : 0123456789
//      5) 65  => 66  : AB
//      6) 147 => 155 : ���������
//      7) 120 => 127 : xyz{|}~
//      8) 120 => 140 :
//
//      /!\ DANGER
//      int(char(65))  : 65
//      int(char(127)) : 127
//      int(char(128)) : -128
//      int(char(140)) : -116
//      .. sera vu plus tard dans le cours.
//
//      Fin des tests

~~~
</details>
