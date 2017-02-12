# Docker container metadata for FreeNAS (*org.freenas* namespace)
Here are all of the various "knob settings" specific to FreeNAS which your container can set, and their meanings.  In most cases, the user can also choose to override these settings at container creation time if the defaults are not suitable to their needs.
* `org.freenas.autostart`  (default value: "false")
Whether container should be set to automatically start at boot time or not.
* `org.freenas.bridged` (default value: "false", e.g. NAT)
Whether container should use bridged or NAT networking by default.
* `org.freenas.capabilities-add` (default value: "")
A list of Docker capabilities to add to container's privileges, in the form of a comma-separated string values, e.g. `SYS_ADMIN,SYS_MODULE`. See https://docs.docker.com/engine/reference/run/#/runtime-privilege-and-linux-capabilities for a full list of Docker privileges.
* `org.freenas.capabilities-drop` (default value: "")
A list of Docker capabilities to remove from container's privileges, in the form of a comma-separated string values, e.g. `SYS_CHROOT,SETCAP`. See https://docs.docker.com/engine/reference/run/#/runtime-privilege-and-linux-capabilities for a full list of Docker privileges that are set by deafult and can be removed.  Warning:  This may cause containers to malfunction if used incorrectly!
* `org.freenas.command` (default value: "")
A command to be run in the container, e.g. `/bin/sh`.
* `org.freenas.privileged` (default value: "false").
This is a boolean property which allows all extra privileges for a container to be turned on (e.g. "the big hammer").  It should only be used with caution, when absolutely required or when docker security is simply not a concern.
* `org.freenas.dhcp` (default value: "false")
Whether container should use DHCP to obtain an IP address.  Only applies to bridged="true" containers.
* `org.freenas.expose-ports-at-host` (default value: "false")
Whether container should expose its ports list on the host's IP address.  Only applies to bridged="false" (e.g. NAT'd) containers.
* `org.freenas.interactive'` (default value: "false")
Whether container is an interactive container or not, which is to say that its Console will attach to a single, interactive process (and when this process exits, that container will stop).  Generally only useful for "raw OS" containers like Ubuntu.
* `org.freenas.port-mappings` (default value: none)
A list of container:host port mappings for the container in the following format `containerport`:`hostport`/`udp|tcp`
* `org.freenas.settings` (default value: [])
An array of `variable name`: `Long description` fields for various variables the container wishes to export as "user settable" (this need not be every possible variable the container supports, but those the container author wishes the user to see and set).
* `org.freenas.static-volumes` (default value: [])
An array of directory or file mapping dictionary entries that should be set just to allow the container to work at all and aren't user visible or settable (see `org.freenas.volumes` below for user-settable volume options).  Format for each dictionary entry is `name` and `descr` for the directory/filename and description, respectively (see existing Dockerfile for more helpful examples).
* `org.freenas.upgradeable` (default value: "false")
If set to true, the container is capable of upgarding itself internally.
* `org.freenas.version` (default value: '0')
A synthetic version number to present to the user.  Since docker containers don't really have "versions" so much as "tags", yet users tend to think of software (like Plex Media Server) as having specific version numbers, this allows the container author to present a version number that indicates when the container might present an upgrade opportunity.
* `org.freenas.volumes` (default value: [])
An array of directory or file mapping dictionary entries that user can set to control the per-directory, per-file mappings of host (or VM) paths to container paths.  Format for each dictionary entry is `name` and `descr` for the directory/filename and description, respectively (see existing Dockerfile for more helpful examples).
* `org.freenas.web-ui-path` (default: none)
If the container provides a web UI, this should be the path component of the URL to it (the hostname or IP will be filled-in automatically and the port and protocol have their own entries, so this should just be the `/path` component of `http://host[:port]/path`
* `org.freenas.web-ui-port` (default value: none)
If the web UI requires a specific port number, this property should be set.
* `org.freenas.web-ui-protocol` (default value: none)
If the web UI requires a specific protocol, this property should be set
