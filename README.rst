Introduction
============

CronUtility provides a global utility for handling asynchron scripts (crons),
it provides a view which handles registered crons and fires them if they are
active.

To register a new cron, just create a global or local utility providing the
ICron interface. The utility has to implement a "active" and "run" method.

CronUtility provides a view named "@@runRegisteredCrons" which has to be called
regularly by a user having the 'Manage portal' permission. It is suggested to
use zope clock server to call this view about ever minute or more, add the
following configuration to your instance part's zope-conf-additional variable:

::
  <clock-server>
    method [PATH_TO_YOUR_PLONE_SITE]@@runRegisteredCrons
    period 60
    user [MANAGER_USERID]
    password [MANAGER_PWD]
    host localhost
  </clock-server>