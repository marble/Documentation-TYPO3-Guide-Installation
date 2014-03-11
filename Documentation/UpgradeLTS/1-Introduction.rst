﻿.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt

.. _upgrade:

Introduction
============

This chapter will give you an historical perspective on what happened
since TYPO3 4.5 and why things changed the way they changed, and what
to expect from the migration from 4.5 to 6.2.

Deprecation Strategy
--------------------

With TYPO3 CMS up until Version 4.5 users were used to be able to
upgrade from one version to the next with little very little effort. By
upgrading users gained new functionality but usually the "old
technology" would still work. This is called *backwards compatibility*,
and TYPO3 CMS users are used to have a high grade of backwards
compatibility.

But with backwards compatibility comes the downside: The code base gets
larger and larger, the old code needs to be further maintained
(security, tests and when considering new features or change of
features / interfaces) and users (developers, integrators) only very
slowly adapt to newer technologies and best practices that emerge with
newer versions.

This is why several years ago (during 4.3 development - back in 2009)
the core team agreed to introduce a consistent deprecation policy:

TYPO3 CMS deprecation policy
  If a method or API in the Core is replaced by a new one and is
  no longer used by the Core itself, it can be marked as "deprecated" and
  can be removed two releases later. Deprecated API methods are
  marked in the PHP code using @deprecated annotation.

At the same time the "deprecation log" was introduced in order for
users to be able to identify potential old methods still being used by
an existing installation. At that time (2009) there were already many
methods marked as deprecated (some as early as "TYPO 3.5").

Up to version 4.5 LTS (2011) the core team hasn't practiced the
"removal" part of the strategy consistently. In fact with 4.5 LTS it
was decided for the last time to keep all deprecated methods and start
removing them in 4.6 (and later) - which is also why 4.6 is called
"rebase".

2014, four years later (with the releases 4.6, 4.7, 6.0 and 6.1) lots
of methods are finally really *gone*. Some users doing the first
upgrade after 4.5 LTS to 6.2 LTS therefore will face some major breaking of their
sites.

Smooth Migration
----------------

To help and guide admins, integrators and developers for the challenges
posed by the mentioned changes in the Core, the TYPO3 6.2 created a
"Smooth Migration" project, which had the goal to make the Upgrade
process as smooth as possible. It followed three goals:

#. migration is possible in all areas
#. migration can be planned and is quotable
#. migration works out as planned

Read in the next chapters how you can plan, prepare and execute the
migration from TYPO3 CMS 4.5 (and also 4.7) to the latest 6.2 LTS
release.
