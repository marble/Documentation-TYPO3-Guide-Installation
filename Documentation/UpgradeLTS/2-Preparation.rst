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

   Make sure the new environment provides the necessary system
   requirements, especially PHP version (5.2 is not supported anymore).
   For details on the specific requirements, check the "INSTALL.md"
   file which is bundled with the TYPO3 Source package.

Preparation steps
-----------------

Still in the original 4.x TYPO3 installation, do the following:

Extensions
^^^^^^^^^^

#. Upgrade the extensions in use to the latest possible versions that
   still run in your old installation. Check if any extension that you
   might be using is not compatible with TYPO3 6.2.

#. Uninstall extensions that you are not using, cleaning up your
   installation from potentially deprecated code.

#. Remove extensions physically from your typo3conf/ext directory
   which are not installed, or move them away.

.. note::
   There are many extensions which provide compatibility with both 4.5
   and 6.2, thus are able to run perfectly fine in both TYPO3 releases.

Compatibility Check
^^^^^^^^^^^^^^^^^^^

Install the extension `smoothmigration` in your old installation. This
extension provides a module in the backend that is able to analyse your
current installation, in particular the installed extensions, and give
you hints on compatibility problems it finds.

The following checks will be done (and even more in future, as this
extension will be updated regularly):

- Calls to deprecated (and removed) static methods: Some of these can
  be automatically migrated!

- Calls to deprecated Fluid view helpers

- Call to PHP mysql\_* methods (removed since PHP 5.5)

- Use of removed constants (like PATH\_t3lib, etc)

- Usages of require\_once on Core files that were moved or renamed
  (simply remove the require\_once in your extensions and simply use
  the needed classes: TYPO3 will take care of loading these classes
  through the auto-loader): this can be automatically migrated through
  this extension!

- Usage of XCLASS: the XCLASS concept was removed in TYPO3 6.x, which
  comes with a new method of registering class replacements

- Calls to DAM classes or methods, since DAM will no longer work with
  TYPO3 6.2 (use FAL instead and adapt your extensions to use it)

- Usage of UTF-8 database: It was possible to still use other character
  sets for databases in TYPO3 4.5. This is no longer possible in TYPO3
  6.2, so this check will make sure you have already migrated: The
  smoothmigration extension provides an automatic migration routine for
  this problem.

