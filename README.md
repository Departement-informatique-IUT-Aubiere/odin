# Plateforme Odin

La plateforme Odin est un ensemble d'outils permettant de faciliter la gestion d'un département en IUT. Cette plateforme permet aux différents acteurs d'un IUT (étudiant, enseignant, administratif) de gagner du temps dans les différents besoins qui peuvent s'offrir à eux.


# Installation
## Prérequis
1. Serveur Apache (tests validés sur 2.4.38)
2. PHP (tests validés sur 8.1.2)
3. Mariadb (tests validés sur 10.4.27)

## Etapes de dépoiement
1. Clonez le dépôt odin branche master

```bash
git clone -b master git@github.com:Departement-informatique-IUT-Aubiere/odin.git
```

2. Donnez le droit d'écriture à tous les dossiers. Cette action provoque l'invalidation de tous les fichiers git. Afin de réinitialiser les modifications, resetez le dépôt entier.

```bash
chmod -R 777 *
git reset --hard
```

3. Sur votre serveur de base de données, créez une base de données vide dont vous mémoriserez le nom, et les informations de connexion. Ces informations vous seront demandées dans les sections suivantes.
4. Rendez-vous, via votre navigateur, à l'adresse : [votre_serveur]/admin/install.php
5. Laissez-vous guider jusqu'à la fin de la procédure
6. Une fois la procédure complète, exécutez sur le serveur à la racine d'Odin

```bash
composer install
```

7. Afin de remettre les droits adéquats sur les fichiers, exécutez :

```bash
find . -type d -exec chmod 701 "{}" \;
find . -type f -exec chmod 604 "{}" \;
find . -name .gitignore -exec chmod 600 "{}" \;
find . -name .git -exec chmod 700 "{}" \;
chmod 700 odin
chmod 700 trombi/downloadPhotos
chmod 700 trombi/getPhotos
find . -name cache -exec chmod 703 "{}" \;
find . -name uploads -exec chmod 703 "{}" \;
find . -name fonts -exec chmod 705 "{}" \;
```

8. A partir de ce moment, Odin est prêt à fonctionner. Il ne vous restera plus qu'à renommer le fichier comon/configCAS.php.config en common/configCAS.php et à le configurer selon vos propres spécificités.
