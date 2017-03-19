Omeka On OVH (extension Omeka)
==============================


[Omeka On Ovh] est une extension pour [Omeka] qui permet d’utiliser le serveur
partagé d’OVH et d’y créer les images dérivées. Il ajoute simplement une
bibliothèque intermédiaire. Il est utilisé pour la [bibliothèque des phares].

OVH changeant régulièrement sa configuration (au moins quatre fois depuis 2012),
sans avertissement, les paramètres doivent être régulièrement mis à jour.


Important
---------

Cette extension n’est plus nécessaire, puisqu’Ovh active désormais l'extension
PHP Imagick par défaut sur les nouvelles instances.

Pour les anciennes instances, il suffit de modifier une ligne dans le fichier
`.ovhconfig` à la racine de son serveur et de passer en stable ou au delà et,
par la même occasion, de passer à PHP 7 si ce n’est déjà fait :

```
    app.engine=php
    app.engine.version=7.0
    http.firewall=none
    environment=production
    container.image=stable
```

Toutes les infos se trouvent dans la [documentation d’Ovh].

Il ne faut pas oublier de désinstaller le plugin et le supprimer du serveur et
surtout de réinitiliser la configuration d’Omeka pour activer la stratégie
"Imagick".

Pour cela, dans `application/config/config.ini`, ajouter ou remplacer les
paramètres de création des fichiers dérivés par :

```
fileDerivatives.strategy = "Omeka_File_Derivative_Strategy_Imagick"
```

Pour la configuration du php en arrière plan, il faut indiquer dans le même
fichier le chemin cli indiqué sur [cette page].

```
background.php.path = "/usr/local/php7.0/bin/php"
```

L’extension fonctionne encore pour ceux qui veulent rester en version "legacy"
(obsolète).


Installation
------------

Uncompress files and rename plugin folder "OmekaOnOvh".

Then install it like any other Omeka plugin. The plugin has no configuration.

Dans `application/config/config.ini`, ajouter ou remplacer les paramètres de
création des fichiers dérivés par :

```
fileDerivatives.strategy = "OmekaOnOvh_ExternalImageMagick"
fileDerivatives.strategyOptions.convert_path = "convert"
```


Warning
-------

Use it at your own risk.

It’s always recommended to backup your files and your databases and to check
your archives regularly so you can roll back if needed.


Troubleshooting
---------------

No issue. Simply update when Ovh is updated.


License
-------

This plugin is published under the [CeCILL v2.1] licence, compatible with
[GNU/GPL] and approved by [FSF] and [OSI].

In consideration of access to the source code and the rights to copy, modify and
redistribute granted by the license, users are provided only with a limited
warranty and the software’s author, the holder of the economic rights, and the
successive licensors only have limited liability.

In this respect, the risks associated with loading, using, modifying and/or
developing or reproducing the software by the user are brought to the user’s
attention, given its Free Software status, which may make it complicated to use,
with the result that its use is reserved for developers and experienced
professionals having in-depth computer knowledge. Users are therefore encouraged
to load and test the suitability of the software as regards their requirements
in conditions enabling the security of their systems and/or data to be ensured
and, more generally, to use and operate it in the same conditions of security.
This Agreement may be freely reproduced and published, provided it is not
altered, and that no provisions are either added or removed herefrom.


Contact
-------

Current maintainers:

* Daniel Berthereau (see [Daniel-KM])

First version of this plugin has been built for [École des Ponts ParisTech].


Copyright
---------

* Copyright Daniel Berthereau, 2014-2017


[Omeka On Ovh]: https://github.com/Daniel-KM/OmekaOnOvh
[Omeka]: https://omeka.org "Omeka.org"
[documentation d’Ovh]: https://docs.ovh.com/fr/fr/web/hosting/modifier-lenvironnement-dexecution-de-mon-hebergement-web/
[cette page]: https://gist.github.com/floptwo/8867068
[bibliothèque des phares]: http://bibliothequedesphares.fr
[CeCILL v2.1]: https://www.cecill.info/licences/Licence_CeCILL_V2.1-en.html
[GNU/GPL]: https://www.gnu.org/licenses/gpl-3.0.html
[FSF]: https://www.fsf.org
[OSI]: http://opensource.org
[École des Ponts ParisTech]: http://bibliotheque.enpc.fr
[Daniel-KM]: https://github.com/Daniel-KM "Daniel Berthereau"
