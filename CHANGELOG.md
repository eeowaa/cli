# Changelog

Items starting with `DEPRECATE` are important deprecation notices. For more
information on the list of deprecated flags and APIs please have a look at
https://docs.docker.com/engine/deprecated/ where target removal dates can also
be found.

## 17.12.0-ce (2017-12-DD)


### Builder

- Fix build cache hash for broken symlink [moby/moby#34271](https://github.com/moby/moby/pull/34271)
- Fix long stream sync [moby/moby#35404](https://github.com/moby/moby/pull/35404)
- Fix dockerfile parser failing silently on long tokens [moby/moby#35429](https://github.com/moby/moby/pull/35429)

### Client

* Remove secret/config duplication in cli/compose [docker/cli#671](https://github.com/docker/cli/pull/671)
* Add `--local` flag to `docker trust sign` [docker/cli#575](https://github.com/docker/cli/pull/575)
* Add `docker trust inspect` [docker/cli#694](https://github.com/docker/cli/pull/694)
+ Add `name` field to secrets and configs to allow interpolation in Compose files [docker/cli#668](https://github.com/docker/cli/pull/668)
+ Add `--isolation` for setting swarm service isolation mode [docker/cli#426](https://github.com/docker/cli/pull/426)
* Remove deprecated "daemon" subcommand [docker/cli#689](https://github.com/docker/cli/pull/689)
- Fix behaviour of `rmi -f` with unexpected errors [docker/cli#654](https://github.com/docker/cli/pull/654)
* Integrated Generic resource in service create [docker/cli#429](https://github.com/docker/cli/pull/429)

### Logging

* Logentries driver line-only=true []byte output fix [moby/moby#35612](https://github.com/moby/moby/pull/35612)
* Logentries line-only logopt fix to maintain backwards compatibility [moby/moby#35628](https://github.com/moby/moby/pull/35628)
+ Add `--until` flag for docker logs [moby/moby#32914](https://github.com/moby/moby/pull/32914)
+ Add gelf log driver plugin to Windows build [moby/moby#35073](https://github.com/moby/moby/pull/35073)
* Set timeout on splunk batch send [moby/moby#35496](https://github.com/moby/moby/pull/35496)

### Networking

* Move load balancer sandbox creation/deletion into libnetwork [moby/moby#35422](https://github.com/moby/moby/pull/35422)
* Only chown network files within container metadata [moby/moby#34224](https://github.com/moby/moby/pull/34224)
* Restore error type in FindNetwork [moby/moby#35634](https://github.com/moby/moby/pull/35634)
- Fix consumes MIME type for NetworkConnect [moby/moby#35542](https://github.com/moby/moby/pull/35542)
+ Added support for persisting Windows network driver specific options [moby/moby#35563](https://github.com/moby/moby/pull/35563)
- Fix timeout on netlink sockets and watchmiss leak [moby/moby#35677](https://github.com/moby/moby/pull/35677)
+ New daemon config for networking diagnosis [moby/moby#35677](https://github.com/moby/moby/pull/35677)

### Runtime

* Update to containerd v1.0.0 [moby/moby#35707](https://github.com/moby/moby/pull/35707)
* Have VFS graphdriver use accelerated in-kernel copy [moby/moby#35537](https://github.com/moby/moby/pull/35537)
* Introduce `workingdir` option for docker exec [moby/moby#35661](https://github.com/moby/moby/pull/35661)
* Bump Go to 1.9.2 [moby/moby#33892](https://github.com/moby/moby/pull/33892) [docker/cli#716](https://github.com/docker/cli/pull/716)
* `/dev` should not be readonly with `--readonly` flag [moby/moby#35344](https://github.com/moby/moby/pull/35344)
+ Add custom build-time Graphdrivers priority list [moby/moby#35522](https://github.com/moby/moby/pull/35522)
* LCOW: CLI changes to add platform flag - pull, run, create and build [docker/cli#474](https://github.com/docker/cli/pull/474)
* Fix width/height on Windoes for `docker exec` [moby/moby#35631](https://github.com/moby/moby/pull/35631)
* Detect overlay2 support on pre-4.0 kernels [moby/moby#35527](https://github.com/moby/moby/pull/35527)
* Devicemapper: remove container rootfs mountPath after umount [moby/moby#34573](https://github.com/moby/moby/pull/34573)
* Disallow overlay/overlay2 on top of NFS [moby/moby#35483](https://github.com/moby/moby/pull/35483)
- Fix potential panic during plugin set. [moby/moby#35632](https://github.com/moby/moby/pull/35632)
- Fix some issues with locking on the container [moby/moby#35501](https://github.com/moby/moby/pull/35501)
- Fixup some issues with plugin refcounting [moby/moby#35265](https://github.com/moby/moby/pull/35265)
+ Add missing lock in ProcessEvent [moby/moby#35516](https://github.com/moby/moby/pull/35516)
+ Add vfs quota support [moby/moby#35231](https://github.com/moby/moby/pull/35231)
* Skip empty directories on prior graphdriver detection [moby/moby#35528](https://github.com/moby/moby/pull/35528)
* Skip xfs quota tests when running in user namespace [moby/moby#35526](https://github.com/moby/moby/pull/35526)
+ Added SubSecondPrecision to config option. [moby/moby#35529](https://github.com/moby/moby/pull/35529)
* Update fsnotify to fix deadlock in removing watch [moby/moby#35453](https://github.com/moby/moby/pull/35453)
- Fix "duplicate mount point" when `--tmpfs /dev/shm` is used [moby/moby#35467](https://github.com/moby/moby/pull/35467)
- Fix honoring tmpfs-size for user `/dev/shm` mount [moby/moby#35316](https://github.com/moby/moby/pull/35316)
- Fix EBUSY errors under overlayfs and v4.13+ kernels [moby/moby#34948](https://github.com/moby/moby/pull/34948)
* Container: protect health monitor channel [moby/moby#35482](https://github.com/moby/moby/pull/35482)
* Container: protect the health status with mutex [moby/moby#35517](https://github.com/moby/moby/pull/35517)
* Container: update real-time resources [moby/moby#33731](https://github.com/moby/moby/pull/33731)
* Create labels when volume exists only remotely [moby/moby#34896](https://github.com/moby/moby/pull/34896)
* Fix leaking container/exec state [moby/moby#35484](https://github.com/moby/moby/pull/35484)

### Swarm Mode

+ Added support for swarm service isolation mode [moby/moby#34424](https://github.com/moby/moby/pull/34424)