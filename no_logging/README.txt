No Logging for Elgg 1.9
Latest Version: 1.9.0
Released: 2013-09-11
Contact: iionly@gmx.de
License: GNU General Public License version 2
Copyright: (c) iionly


This plugin disables the Elgg system log.

The logging is disabled by unregistering the system_log_default_logger and system_log_listener event handlers of Elgg core. There won't be any more log entries by Elgg core or any other plugins created that utilize these event handlers.



What to do and NOT to do:

* do NOT delete the system_log table in the database even after you enabled the No Logging plugin! Deleting this table will result in fatal errors if you ever disable the No Logging plugin again (or in case any plugin tries to write into / read from this table by other means beside the default events controlled by the No Logging plugin). This table will not be re-created automatically. Simply keep the system_log table even if it is empty.

* you can / should keep the Log Rotate plugin enabled at least for a while after enabling the No Logging. The entries in the system_log table will be archived into the system_log_<timestamp> tables in the course of time until the system_log table is emptied completely. You can delete the system_log_<timestamp> tables without risk or let the Log Rotate plugin delete them according to the configured schedule. Once the system_log table is empty you can disable the Log Rotate and the Logbrowser plugin if you want to.

* the Garbage Collector plugin is something different. It's not connected with the system_log table, the Log Rotate or Logbrowser plugins or the No Logging plugin. Keep it enabled.



Installation:

1. copy the no_logging folder into the mod folder of your site,

2. enable the plugin in the admin section of your site.



Changelog:

1.9.0:

* Updated for Elgg 1.9.


1.8.0:

* Initial release for Elgg 1.8.
