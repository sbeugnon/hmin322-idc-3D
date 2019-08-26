# HMIN322 : idc-3D

Projet *template* pour le TP sur l'insertion de données cachées dans les objets 3D.
Ce document contient la liste des activités à réaliser durant le TP.

## Pré-requis

- cmake
- g++/gcc
- make

## Préparation

Cloner le dépôt
```sh
git clone https://github.com/TsubameDono/hmin322-idc-3D.git
```
Construire la bibliothèque libigl et télécharger toutes les bibliothèques externes (eigen, etc.)
```sh
$ cd libigl # enter libigl directory
$libigl/ mkdir build # create build directory
$libigl/ cd build # enter build directory
$build/ cmake .. # build libigl project (automatically load external libs)
$build make # build libraries
```

## Explication

**libigl** : librairie contenant des méthodes de traitement des objets 3D (IO, lissage, remaillage, filtrage, métrique)
 - igl::readXXX(.) (OFF, STL, etc.)
 - igl::writeXXX(.)
 - igl::hausdorff(.)
 - igl::is_border_vertex(.)
**libigl/opengl** : sous-librairie permettant de prototyper un outil de rendu avec igl
```cpp
#include <igl/readOFF.h>
#include <igl/opengl/glfw/Viewer.h>

Eigen::MatrixXd V;
Eigen::MatrixXi F;

int main(int argc, char *argv[])
{
  // Load a mesh in OFF format
  igl::readOFF(TUTORIAL_SHARED_PATH "/bunny.off", V, F);

  // Plot the mesh
  igl::opengl::glfw::Viewer viewer;
  viewer.data().set_mesh(V, F);
  viewer.launch();
}
```
**eigen** : librairie de structures mathématiques matricielles pour la représentation
 - Eigen::MatrixXf ou Eigen::MatrixXd pour les coordonnées, Eigen::MatrixXi pour les indices
```cpp
Eigen::MatrixXd V;
Eigen::MatrixXi F;
```

## Travaux

1. Clôner le dépôt
2. Charger un maillage 3D à l'aide de la bibliothèque **libigl** en utilisant la fonction *read_triangle(.)*
3. Sauvegarder une copie du maillage 3D à l'aide de la bibliothèque **libigl** en utilisant la fonction *write_triangle(.)*
