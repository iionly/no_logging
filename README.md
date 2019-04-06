No Logging for Elgg 3.0 and newer Elgg 3.X
==========================================

Latest Version: 3.0.0  
Released: 2018-10-02  
Contact: iionly@gmx.de  
License: GNU General Public License version 2  
Copyright: (c) iionly


Description
-----------

This plugin disables the Elgg system log.

The logging is disabled by unregistering the system_log_default_logger and system_log_listener event handlers. As of Elgg 3 these two event handlers are registered by the bundled System Log plugin of Elgg core. If you keep this plugin disabled (or have never enabled it to begin with), you would not need the No Logging plugin at all as without this plugin there won't be any more log entries by Elgg core or any other plugins created that utilize these event handlers.

Nevertheless, it might still make sense to temporarily use the No Logging plugin because the System Log plugin is not only responsible for the creation of the log entries but also is responsible to deal with archiving the log table and delete the the archived log tables (before Elgg 3 this functionality was part of the bundled Logrotate plugin). While disabling the System Log plugin results in no new log entries being added to the log table any already existing entries will remain. Now you could make use of the No Logging plugin to stop new log entries from being created until the log table gets rotated, i.e. the log table itself gets emtpied after a log archive table has been created. Once the rotation has happened (the when depends on what cron intervall you have set for the log rotate) and the log table is empty you can disable the System Log plugin, then also the No Logging plugin and safely delete the log archive table(s) - but please NOT the log table itself.


What to do and NOT to do
------------------------

* Do NOT delete the system_log table in the database even after you enabled the No Logging plugin! Deleting this table will result in fatal errors if you ever disable the No Logging plugin again (or in case any plugin tries to write into / read from this table by other means beside the default events controlled by the No Logging plugin). This table will not be re-created automatically. Simply keep the system_log table even if it is empty.
* You can / should keep the System Log plugin enabled at least for a while after enabling the No Logging. The entries in the system_log table will be archived into the system_log_<timestamp> tables in the course of time until the system_log table is emptied completely. You can delete the system_log_<timestamp> tables without risk or let the Sytem Log plugin delete them according to the configured schedule. Once the system_log table is empty you can disable the System Log plugin if you want to.
* The Garbage Collector plugin is something different. It's not connected with the system_log table, the System Log or the No Logging plugins. Keep it enabled.


Installation
------------

1. If you have a previous version of the No Logging plugin installed, first remove the old no_logging plugin folder from your mod directory before copying/extracting the new version to your server,
2. Copy the no_logging folder into the mod folder of your site,
3. Enable the plugin in the admin section of your site.
