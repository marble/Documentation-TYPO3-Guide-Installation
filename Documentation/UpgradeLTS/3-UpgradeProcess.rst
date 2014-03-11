.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt

Upgrading from 4.5 LTS to 6.2 LTS
=================================

When the preparations are done the :ref:`upgrade` XXX upgrade process` itself is the
same as before for minor level releases like from 6.1 to 6.2.

You can even skip minor versions in between, so there is no need to do
any intermediate upgrades to upgrade from 4.5 (or 4.7) to 6.2.

.. note:: 
   You need to at least have upgraded to TYPO3 4.5 in order to
   upgrade to 6.2.

Some notes when upgrading from a 4.x installation nevertheless:

- when you first call the Install Tool after switching typo3\_src to
  the new release, and enabling the Install Tool with the
  "ENABLE_INSTALL_TOOL" file, some things will automatically be done
  even before the Install Tool starts. So be aware of it and make a
  backup of the installation in case you want to be able to restore
  your old installation:

  - the typo3conf/localconf.php will be adapted to the new 6.x style of
    configuration "LocalConfiguration.php"

  - installed extensions will be moved to "PackageStates.php" file

  - saltedpasswords Extension will be installed and activated if it
    wasn't used before

- in the Install Tool use the "System Environment" module to see if
  your system fullfills all required preconditions.

- use the "Important Actions", item "Check for broken Extensions". If
  there are extensions that might break your current installation (i.e.
  calling removed methods in their ext_localconf.php or ext_table.php),
  you will want to remove them until they are updated.

- then use the "Upgrade Wizard" as usual to migrate your installation

Post Upgrade
------------

If you have not used DAM before and were just using regular files with
core TYPO3 Content Objects, the "Upgrade Wizards" will have converted
your structure to FAL and you are all set and ready.

If you have been working with "DAM" (Digital Asset Management) in TYPO3
4.5 or 4.7, you will want to migrate your data to the core "FAL" (File
Abstraction Layer). DAM and it's related extensions no longer work with
TYPO3 CMS 6.x. For this, read on in the next chapter.
