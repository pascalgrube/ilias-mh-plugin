# ilias-oc
An ILIAS Repository Object plugin for Opencast 5.x

This plugin creates a tight ingration of Opencast 5.x, 4.x, 3.x(1.6 and 2.0 see older releases) and ILIAS.
This plugin also requires to a workflow handler for Opencast, which enables distributing the files in a way that
are usable by this plugin. This plugin is currently only available in the [Github Repo](https://github.com/pascalseeland/opencast)
and not part of the official Opencast Distribution.

## Installation

__REQUIRED__ Databases: MySQL/MariaDB

It __MUST__ be installed into `Customizing/global/plugins/Services/Repository/RepositoryObject/`.

The plugin folder __MUST__ be named 'Matterhorn'.

## Configuration

### Plugin-Configuration

#### Opencast directory

This __MUST__ be **org.opencastproject.storage.dir**.

For nginx add the config:
```
location /__ilias_xmh_mh_directory__/ {
   internal;
   alias ${org.opencastproject.storage.dir}/;
}
```

For apache add the config:
```
XSendFilePath ${org.opencastproject.storage.dir}
```

#### XSendfile header

For nginx select `X-Accel-Redirect`.
For apache select `X-Sendfile` and enable **mod_xsendfile**.

#### Distribution directory

This __MUST__ be the path were episodes are available after upload, so this plugin can serve them to users.

For nginx add the config:
```
location /__ilias_xmh_distribution_directory__/ {
   internal;
   alias ${distribution_directory}/;
}
```

For apache add the config:
```
XSendFilePath ${distribution_directory}
```
