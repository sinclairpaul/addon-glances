# Home Assistant Community Add-on: Glances

[![GitHub Release][releases-shield]][releases]
![Project Stage][project-stage-shield]
[![License][license-shield]](LICENSE.md)

![Supports armhf Architecture][armhf-shield]
![Supports armv7 Architecture][armv7-shield]
![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]
![Supports i386 Architecture][i386-shield]

[![GitLab CI][gitlabci-shield]][gitlabci]
![Project Maintenance][maintenance-shield]
[![GitHub Activity][commits-shield]][commits]

[![Discord][discord-shield]][discord]
[![Community Forum][forum-shield]][forum]

[![Sponsor Frenck via GitHub Sponsors][github-sponsors-shield]][github-sponsors]

[![Support Frenck on Patreon][patreon-shield]][patreon]

Glances is a cross-platform system monitoring tool written in Python.

![The Glances Hass.io add-on](images/screenshot.png)

## About

Glances is a cross-platform monitoring tool which aims to present a maximum of
information in a minimum of space through a Web-based interface.

Glances can export all system statistics to InfluxDB, allowing you to look
at all your system information and its behavior over time.

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Home Assistant add-on.

1. Search for the "Glances" add-on in the Supervisor add-on store
   and install it.
1. Disable "Protection mode" in the add-on panel.
1. Start the "Glances" add-on.
1. Check the logs of the "Glances" to see if everything went well.
1. Click the "OPEN WEB UI" button take a glance at Glances.

## Configuration

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```yaml
log_level: info
process_info: false
refresh_time: 10
ssl: false
certfile: fullchain.pem
keyfile: privkey.pem
influxdb:
  enabled: false
  host: a0d7b954-influxdb
  port: 8086
  username: glances
  password: "!secret glances_influxdb_password"
  database: glances
  prefix: localhost
  interval: 60
  ssl: false
```

**Note**: _This is just an example, don't copy and paste it! Create your own!_

### Option: `log_level`

The `log_level` option controls the level of log output by the addon and can
be changed to be more or less verbose, which might be useful when you are
dealing with an unknown issue. Possible values are:

- `trace`: Show every detail, like all called internal functions.
- `debug`: Shows detailed debug information.
- `info`: Normal (usually) interesting events.
- `warning`: Exceptional occurrences that are not errors.
- `error`:  Runtime errors that do not require immediate action.
- `fatal`: Something went terribly wrong. Add-on becomes unusable.

Please note that each level automatically includes log messages from a
more severe level, e.g., `debug` also shows `info` messages. By default,
the `log_level` is set to `info`, which is the recommended setting unless
you are troubleshooting.

### Option: `process_info`

If set to `true`, it will enable the process module of Glances and gives
detailed insight into each individual process running on the system.

**Note**: _Enabling this feature will increase CPU usage significantly._

### Options: `refresh_time`

Sets refresh time (in seconds).

**Note**: _Refreshing more quickly will result in a higher CPU usage._

### Option: `ssl`

Enables/Disables SSL (HTTPS) on the Glances Web UI. Set it `true` to enable it,
`false` otherwise.

### Option: `certfile`

The certificate file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_

### Option: `keyfile`

The private key file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_

### Option group `influxdb`

---

The following options are for the option group: `influxdb`. These settings
only apply to the Glances InfluxDB data export.

#### Option `influxdb`: `enabled`

Enables/Disables the Glances data export to InfluxDB.

#### Option `influxdb`: `host`

The hostname where InfluxDB is running.

**Note**: _If you are using the Community InfluxDB add-on,
use `a0d7b954-influxdb` as the hostname._

#### Option `influxdb`: `port`

The port on which InfluxDB is listening.

#### Option `influxdb`: `username`

The username that you have created for Glances to authenticate against
InfluxDB.

#### Option `influxdb`: `password`

The password for the above username option.

#### Option `influxdb`: `database`

The name of the database to store all Glances information into.

**Note**: _It is strongly recommended to create a separate database for glances
and not store this in the same database name as Home Assistant._

#### Option `prefix`: `localhost`

The hostname to append for exported data.

**Note**: _For the Grafana Glances dashboard set this to `localhost`._

#### Option `influxdb`: `interval`

Defines the interval (in seconds) on how often Glances exports data to InfluxDB.

#### Option `influxdb`: `ssl`

Adding this option will allow SSL to be used on the InfluxDB connection.  If not
set will default to `false` which is the required setting for the Community
InfluxDB add-on.

## Adding Glances as a sensor into Home Assistant

The Home Assistant Glances sensor platform is consuming the system information
provided by the Glances API.

This enables one to track and display their stats in Home Assistant,
and even build automations based on that data.

Set up the integration through **Configuration -> Integrations -> Glances**.

**Note**: _Once the add-on is running, add the integration with all
defaults, except for port, which should be 61209_

More information about the Glances sensor platform can be found in the
Home Assistant documentation:

<https://www.home-assistant.io/components/sensor.glances/>

## Changelog & Releases

This repository keeps a change log using [GitHub's releases][releases]
functionality. The format of the log is based on
[Keep a Changelog][keepchangelog].

Releases are based on [Semantic Versioning][semver], and use the format
of ``MAJOR.MINOR.PATCH``. In a nutshell, the version will be incremented
based on the following:

- ``MAJOR``: Incompatible or major changes.
- ``MINOR``: Backwards-compatible new features and enhancements.
- ``PATCH``: Backwards-compatible bugfixes and package updates.

## Support

Got questions?

You have several options to get them answered:

- The [Home Assistant Community Add-ons Discord chat server][discord] for add-on
  support and feature requests.
- The [Home Assistant Discord chat server][discord-ha] for general Home
  Assistant discussions and questions.
- The Home Assistant [Community Forum][forum].
- Join the [Reddit subreddit][reddit] in [/r/homeassistant][reddit]

You could also [open an issue here][issue] GitHub.

## Contributing

This is an active open-source project. We are always open to people who want to
use the code or contribute to it.

We have set up a separate document containing our
[contribution guidelines](CONTRIBUTING.md).

Thank you for being involved! :heart_eyes:

## Authors & contributors

The original setup of this repository is by [Franck Nijhof][frenck].

For a full list of all authors and contributors,
check [the contributor's page][contributors].

## We have got some Home Assistant add-ons for you

Want some more functionality to your Home Assistant instance?

We have created multiple add-ons for Home Assistant. For a full list, check out
our [GitHub Repository][repository].

## License

MIT License

Copyright (c) 2019-2020 Franck Nijhof

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[armhf-shield]: https://img.shields.io/badge/armhf-yes-green.svg
[armv7-shield]: https://img.shields.io/badge/armv7-yes-green.svg
[commits-shield]: https://img.shields.io/github/commit-activity/y/hassio-addons/addon-glances.svg
[commits]: https://github.com/hassio-addons/addon-glances/commits/master
[contributors]: https://github.com/hassio-addons/addon-glances/graphs/contributors
[discord-ha]: https://discord.gg/c5DvZ4e
[discord-shield]: https://img.shields.io/discord/478094546522079232.svg
[discord]: https://discord.me/hassioaddons
[dockerhub]: https://hub.docker.com/r/hassioaddons/glances
[forum-shield]: https://img.shields.io/badge/community-forum-brightgreen.svg
[forum]: https://community.home-assistant.io/t/home-assistant-community-add-on-glances/97102?u=frenck
[frenck]: https://github.com/frenck
[github-sponsors-shield]: https://frenck.dev/wp-content/uploads/2019/12/github_sponsor.png
[github-sponsors]: https://github.com/sponsors/frenck
[gitlabci-shield]: https://gitlab.com/hassio-addons/addon-glances/badges/master/pipeline.svg
[gitlabci]: https://gitlab.com/hassio-addons/addon-glances/pipelines
[home-assistant]: https://home-assistant.io
[i386-shield]: https://img.shields.io/badge/i386-yes-green.svg
[issue]: https://github.com/hassio-addons/addon-glances/issues
[keepchangelog]: http://keepachangelog.com/en/1.0.0/
[license-shield]: https://img.shields.io/github/license/hassio-addons/addon-glances.svg
[maintenance-shield]: https://img.shields.io/maintenance/yes/2020.svg
[patreon-shield]: https://frenck.dev/wp-content/uploads/2019/12/patreon.png
[patreon]: https://www.patreon.com/frenck
[project-stage-shield]: https://img.shields.io/badge/project%20stage-experimental-yellow.svg
[reddit]: https://reddit.com/r/homeassistant
[releases-shield]: https://img.shields.io/github/release/hassio-addons/addon-glances.svg
[releases]: https://github.com/hassio-addons/addon-glances/releases
[repository]: https://github.com/hassio-addons/repository
[semver]: http://semver.org/spec/v2.0.0.htm
