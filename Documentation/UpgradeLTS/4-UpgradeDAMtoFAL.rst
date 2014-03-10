.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt

Upgrading from DAM to FAL
=========================

If you have been working with "DAM" (Digital Asset Management) in TYPO3
4.5 or 4.7, you will want to migrate your data to the core "FAL" (File
Abstraction Layer). DAM and it's related extensions no longer work with
TYPO3 CMS 6.x.

- Install the "dam_falmigration" extension
  (https://github.com/b13/t3ext-dam_falmigration)

- On the shell, call the migration tools one after the other:

typo3/cli_dispatch.phpsh extbase
