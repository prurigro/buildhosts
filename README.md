# BuildHosts #

Download and use custom hosts sources to build _/etc/hosts_

## Commands ##

* `buildhosts build`: generate `/etc/hosts` using `/etc/hosts.core` and the configured sources
* `buildhosts revert`: remove lists imported from hosts list sources and restore `/etc/hosts`
* `buildhosts help`: display the help

## Configure Hosts Sources ##

1. Running `buildhosts build` for the first time will move _/etc/hosts_ to _/etc/hosts.core_ and create _/etc/hosts.sources_ with a set of default hosts sources that focus on ad-blocking, and these will be downloaded before a new _/etc/hosts_ is then created using _/etc/hosts.core_ and the contents of the hosts sources.
2. Once this is finished, you can add/edit/delete or comment (lines starting with #) hosts sources in _/etc/hosts.sources_, and running `buildhosts build` again will re-create _/etc/hosts_ using your updated sources.

## Remove Hosts Sources ##

1. To disable the configured hosts lists and restore your original configuration, run `buildhosts revert` and `/etc/hosts.core` will be moved back to `/etc/hosts` (*/etc/hosts.sources* will need to be manually deleted).

## Environment Variables ##

These variables can be configured before running buildhosts to run with custom locations

* **HOSTS_DIR**: Directory containing the hosts file (default: _/etc/_)
* **HOSTS_SYSTEM**: The system hosts file (default: _$HOSTS_DIR/hosts_)
* **HOSTS_CORE**: The file containing the custom hosts configuration (default: _${HOSTS_SYSTEM}.core_)
* **HOSTS_SOURCES**: The file containing a list of hosts sources to download (default: _${HOSTS_SYSTEM}.sources_)
* **HOSTS_WHITELIST**: The file containing a list of domains to skip when parsing $HOSTS_SOURCES (default: _${HOSTS_SYSTEM}.whitelist_)

## Extra ##

* The `p2p-to-hosts` script included in this repo can be used to convert blocklists in p2p format to hosts format (usable with this package).

## Credits ##

Written by Kevin MacMartin:

* [GitHub Projects](https://github.com/prurigro)
* [Arch Linux AUR Packages](https://aur.archlinux.org/packages/?SeB=m&K=prurigro)

## License ##

Released under the [MIT license](http://opensource.org/licenses/MIT).
