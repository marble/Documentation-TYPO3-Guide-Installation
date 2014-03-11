.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt

.. _lts_upgrade_preparation:

Preparation in 4.x installation
===============================

Preconditions
-------------

#. TYPO3 Version

   Make sure your installation is upgraded to at least TYPO3 4.5 LTS.
   The TYPO3 6.2 upgrade process is possible from any version starting
   with 4.5 (i.e. 4.6, 4.7, 6.0 or 6.1). If you are running a lower
   version of TYPO3, please consider upgrading to 4.5 first.

#. New system requirements

   Make sure the new environment fullfills the necessary system
   requirements, especially PHP version (5.2 is not supported anymore).
   For details on the specific requirements check the "INSTALL.md"
   file which is bundled with the TYPO3 Source package.

Preparation steps
-----------------

Still in the original 4.x TYPO3 installation, do the following:

Extensions
^^^^^^^^^^

#. Upgrade the extensions in use to the latest possible version that
   is available for your old installation. Check if any extension that you
   are using is not compatible with TYPO3 6.2.

#. Uninstall extensions that you are not using to clean up your
   installation and remove deprecated and potentially dangerous code.

#. Remove unneeded extensions physically from your typo3conf/ext directory.

.. note::

   There are many extensions which provide compatibility with both 4.5
   and 6.2 and thus are able to run perfectly fine in both TYPO3 releases.

Compatibility Check
^^^^^^^^^^^^^^^^^^^

Install the extension `smoothmigration`__ in your old installation. This
extension provides a module in the backend that is able to analyse your
current installation, in particular the installed extensions, and give
you hints on compatibility problems.

__ http://forge.typo3.org/projects/typo3cms-smoothmigration

The following checks will be done (and even more in future, as this
extension will be updated regularly):

- Calls to deprecated and removed static methods: Some of these can
  be automatically migrated!

- Calls to deprecated Fluid view helpers

- Calls to PHP mysql\_* methods (removed since PHP 5.5)

- Usages of removed constants (like PATH\_t3lib, etc)

- Usages of require\_once of core files that were moved or renamed.
  Simply remove the require\_once in your extensions and just use
  the needed classes: TYPO3 will take care of loading these classes
  by means of the auto-loader. This can be automatically migrated by
  this extension!

- Usages of XCLASS: The XCLASS concept was removed in TYPO3 6.x. Instead
  there now is a new method for registering replacement classes.

- Calls to DAM classes or methods, since DAM will no longer work with
  TYPO3 6.2. Use FAL instead and adapt your extensions to using it.

- Usage of UTF-8 database: It was still possible to use other character
  sets for databases in TYPO3 4.5. This is no longer possible in TYPO3
  6.2, so this check will make sure you are using UTF-8 already in your
  database. The smoothmigration extension provides an automatic migration
  routine for this problem as well.

