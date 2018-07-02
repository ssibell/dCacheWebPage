---
layout: post
title:  "dCache 3.1 Release Notes!"
date:   2017-04-03 10:27:23
author: Mathias de Riese
excerpt: WHAT’S NEW IN DCACHE 3.1! 
category: posts
---

What’s new in dCache 3.1
The release notes


Highlights
*   Plenty of NFS door improvements
*   Chimera can track file upload status
*   OpenID connect support for WebDAV 3rd party copy

## Incompatibilities

*   Dropped support for regular expression matching in alarms

## Acknowledgments

Thanks to Johan Guldmyr for his constributions.

## Release 3.1.15

### cells

The current release improved handling of rogue domains with badly formatted dCache versions.

### configuration

There are configuration options in zookeeper that may affect how well the zookeeper cluster will work with dCache. The lack of documentation of how dCache uses zookeeper prevents admins from tuning their zookeeper instance. This is now fixed and zookeeper configuration is updated with hints on how dCache uses zookeeper, along with the corresponding zookeeper configuration properties.

### pool

The current release fixed loading `setup` that requires queues created by `pool.queues`.

### webdav

The current release fixed the stack-traces on bad client input.

### Changelog 3.1.14..3.1.15


- [aa82c54](https://github.com/dcache/dcache/commit/aa82c54ada7f0754786fc16e61edecc87fa15205) [maven-release-plugin] prepare release 3.1.15
- [3dfcc64](https://github.com/dcache/dcache/commit/3dfcc64903ba4af8ca9e28d30a488f6357eab2af) cells: better handling of rogue domains with badly formatted dCache versions
- [0dd102e](https://github.com/dcache/dcache/commit/0dd102efe617e8a6591d16c83d2d28b4caa3a703) configuration: update zookeeper configuration with hints
- [ad3e9b0](https://github.com/dcache/dcache/commit/ad3e9b03c272f41f4b6c25561b2c2f037d2db6c7) pool: fix loading ‘setup’ that requires queues created by ‘pool.queues’
- [ca1667d](https://github.com/dcache/dcache/commit/ca1667d408bde7ce50f5181465839502f1de63ee) webdav: avoid stack-trace on bad user requests
- [ad54a1f](https://github.com/dcache/dcache/commit/ad54a1f0a98da9c2775351ce5b8dd9ef62f9c02a) alarms: guard against NPEs on LogEntry getters
- [265141c](https://github.com/dcache/dcache/commit/265141c39e12dda93e3e4822ee4476d6ae69309d) [maven-release-plugin] prepare for next development iteration



## Release 3.1.14

### admin

While `migration move` tasks on pools were working correctly, for `migration info` command an error occurred, that the current user (root) wasn’t allowed to execute anything (due to missing ACLs). This is now fixed.

### pool

The current release fixed fix regression in HTTP third-party transfer with redirection and third-party transfers work again when uploading to services that redirect-on-PUT (such as dCache, if so configured).

### webdav

The current release several regressions with `CredentialSource.NONE`.

The current release fixed regression in third-party copy with no delegation.

### Changelog 3.1.13..3.1.14



- [21911f4](https://github.com/dcache/dcache/commit/21911f431841fb0b4d59549af595b2a9145a972d) [maven-release-plugin] prepare release 3.1.14
- [5f4a0b9](https://github.com/dcache/dcache/commit/5f4a0b9cccc2434ef88348c9a1799e7136d2e074) admin: Fix Inconsistent ACL enforcement, RT 9207
- [d1e8a12](https://github.com/dcache/dcache/commit/d1e8a12a2e7f22bf34f1af7268118e559c6732ef) webdav: fix more regressions with CredentialSource.NONE
- [170d278](https://github.com/dcache/dcache/commit/170d278c1164e9d8bc29b224fcaf5c5c2f40906f) pool: fix regression in HTTP third-party transfer with redirection
- [f9d721f](https://github.com/dcache/dcache/commit/f9d721f98165c8a8c790bf9771fc6a37c732b71e) webdav: fix regression in third-party copy with no delegation
- [7d31759](https://github.com/dcache/dcache/commit/7d31759fbadfe9cb784ca183ac16d97a42845e1d) [maven-release-plugin] prepare for next development iteration



## Release 3.1.13

### configuration

For some services it was unclear what were the admin’s responsibilities in terms of consistent configuration. The current release updated the documentation describing what is needed to deploy redundant services.

### resilience

The current relase improved configuration for namespace provider properties by making them immutable.

### srm

The current release improved configuration for `srmPing` responses.

### Changelog 3.1.12..3.1.13



- [2bd7e5e](https://github.com/dcache/dcache/commit/2bd7e5e8293093a41d3368a78bf1fdb3305c084c) [maven-release-plugin] prepare release 3.1.13
- [9132256](https://github.com/dcache/dcache/commit/913225689a49f093f8d2ccc11914c58572020632) configuration: update description for replicable
- [928749b](https://github.com/dcache/dcache/commit/928749b3611625ced865e089d97c658b96608489) resilience: remove reference to pnfsmanager property
- [9b00497](https://github.com/dcache/dcache/commit/9b004979059e504d98a62e0de392b29aec90af95) srm/srmmanager: fix srmPing confusion
- [0675c6b](https://github.com/dcache/dcache/commit/0675c6bcf0fa46d1e9c4ae340b6d0b6734862bc9) [maven-release-plugin] prepare for next development iteration
- [3399e1b](https://github.com/dcache/dcache/commit/3399e1b4511038c9bc4f6f1bdadd6b60b2c135c9) removed the conflict markers
- [17b3f2d](https://github.com/dcache/dcache/commit/17b3f2d5c2fc173d3053425a3f222ba2feaf7492) resilience: make namespace provider properties immutable



## Release 3.1.12

### billing

The current release added documentation that describes how a `CellAddress` and its fields expand.

### config

The current release improves documentation for dCache admins by adding `obsolete|forbidden` annotation for dropped properties. This helps admins to discover changes that might affect their dCache instance. This is both through manual inspection and through the `dcache check-config` command.

### ftp

It has been discovered that timestamp facts reported by dCache GFTP server are expressed in local (to server) time. This is now fixed. Timestamp facts are reported in GMT. Clients like `globus-url-copty -sync` work properly and `ubefrtp -ls` returns correct timestamp.

### srm

The current release added new configuration properties to allow easy modification.

It upstated as well `srm/manager.properties` documentation to describe the relationship between `srmmanager.root` and `srm.loginbroker.root` properties.

### Changelog 3.1.11..3.1.12



- [760f8ef](https://github.com/dcache/dcache/commit/760f8efdbd4a4f2167cb6270a30632244b625599)  [maven-release-plugin] prepare release 3.1.12
- [0f7291d](https://github.com/dcache/dcache/commit/0f7291d493960ec26bb642e2460a2b9f15353c43)  srm/srmmanager: update documentation about root path
- [595d260](https://github.com/dcache/dcache/commit/595d2601b29dfd933cae210a87251b0d832f3f40)  ftp: convert timestamps to GMT (to follow RFC 3659)
- [3a0f6c0](https://github.com/dcache/dcache/commit/3a0f6c0484fc0a25a8fd2d24cebdab3afe29c1a9)  config: use consistent terminology
- [eda1b59](https://github.com/dcache/dcache/commit/eda1b5996834805018a195f388d7be7a4f8f8086)  billing: update documentation to describe CellAddress
- [1299362](https://github.com/dcache/dcache/commit/12993622bb8d247f8b792d5966cec346ddcc726b)  srm,srmmanager: add configuration property to allow easy modification of srm root
- [1f9600d](https://github.com/dcache/dcache/commit/1f9600deef93c2d0f385b76ae45ca8f4ac5dd220)  logback: make socket appender construction depend on log level
- [75c5b3a](https://github.com/dcache/dcache/commit/75c5b3ae5eea49bdf80698930c3f399d01a6682f)  dcache: release dcache-view 1.2.2 for dcache 3.1
- [878dc3b](https://github.com/dcache/dcache/commit/878dc3bf911120295194da3f504ebbad8d8a4a83)  config: add obsolete|forbidden annotation for dropped properties
- [3867d1f](https://github.com/dcache/dcache/commit/3867d1f1d69f354f8fc1869c2cd97a6c9dfcb3ef)  [maven-release-plugin] prepare for next development iteration
- [7f39fab](https://github.com/dcache/dcache/commit/7f39fabd2ac15926725762defaa030aa0afb300d)  config: add obsolete|forbidden annotation for dropped properties
- [4f4ed8f](https://github.com/dcache/dcache/commit/4f4ed8f14bcb68d1d4c423ffd91f3d4bb214164f)  pnfsmanager: remove obsolete comments from properties file



## Release 3.1.11

### Changes affecting multiple services

Christoph Anton Mitterer submitted several corrections to the comment string in properties files.

### srm

The ‘-version’ command-line option previously only returned information about which SRM specification version is supported, but not the srmclient version. This patch changes the srmclient version information string to include both client version and SRM compatibility.

### zookeeper

A race condition in zookeeper caused irrelevant stacktraces to be logged on shutdowns. Since this problem is not easily solvable with Zookeeper 3.4, we decided to change the log-level threshold for NIOServerCnxnFactory. Note that the suppressed class is only used by ZooKeeper server (i.e., not the client). Therefore, only the ‘zookeeper’ service is affected.

### Changelog 3.1.10..3.1.11



- [a1aa2a9f55](https://github.com/dcache/dcache/commit/a1aa2a9f55a81b94e3c69bf351ff4da114c827c8)  [maven-release-plugin] prepare release 3.1.11
- [ad5be09e65](https://github.com/dcache/dcache/commit/ad5be09e6577f78a586d508228e0a5c86483f79f)  use correct terminology
- [d5fc3fc153](https://github.com/dcache/dcache/commit/d5fc3fc1539ce13f5d112beb23d79e4fd18481dd)  fixed several typos in the documentation
- [fa30bd0e02](https://github.com/dcache/dcache/commit/fa30bd0e02bbe7c37c1b3e4e68345dad19aea2c1)  added hint that pnfsmanagers must use the same DB
- [75413984e0](https://github.com/dcache/dcache/commit/75413984e0e5962d7911fab0fa7e8fcbbba86a01)  srmclient: give version of srmclient
- [84f55fb998](https://github.com/dcache/dcache/commit/84f55fb9982e6486801b8878af7256f7a2c967ae)  zookeeper: work-around race-condition in zookeeper server shutdown
- [35722dbac3](https://github.com/dcache/dcache/commit/35722dbac31290eb415730afd9466aa3c827f221)  [maven-release-plugin] prepare for next development iteration



## Release 3.1.10

### admin

Fix idle timeout so that dCache honours the configuration properties `admin.ssh.idle-timeout` and `admin.ssh.idle-timeout.unit`.

### httpd

The “Disk Space Usage” webpage (`/usageInfo`) contains a table showing information about each pool in the dCache cluster. The “Layout” column showed the capacity usage graphically, with different colours showing how much of that pool’s capacity is being used for different tasks. This release fixes the Layout heading to describe a previously undocumented colour.

### Changelog 3.1.9..3.1.10



[6eb681a](https://github.com/dcache/dcache/commit/6eb681a98ede51951c17438b8f622fcc4e38dc9e)

[maven-release-plugin] prepare release 3.1.10

[ed07ba5](https://github.com/dcache/dcache/commit/ed07ba53d2367abb78f9d82d900a38ce4cd89d73)

ssh: fix handling of ssh idle timeout

[7fc55df](https://github.com/dcache/dcache/commit/7fc55dfd2f8deb9cb214e8e3a7bbfc8f7657cd2d)

system-test: add series of functional test for frontend service

[aa735b3](https://github.com/dcache/dcache/commit/aa735b39a24c4e790f4701b58363115cbc53e053)

[maven-release-plugin] prepare for next development iteration

[53177d0](https://github.com/dcache/dcache/commit/53177d064cc98a8901d6bc5b642eb5fae5c9d082)

httpd: Fixed table headers in usageInfo



## Release 3.1.9

### frontend

Several improvements are added to frontend such as restriction usage is improved and easily configurable JSON is now available via frontend.

### poolmanager

The current improved unit-tests to make them more reliable.

### srm

The current release enforced restrictions on `srmSetPermission` operations.

### zookeeper

The current release fixed race-condition when ZooKeeper server accepts requests before the server is fully initialised.

### Changelog 3.1.8..3.1.9



[fa7ba27](https://github.com/dcache/dcache/commit/fa7ba27962ab3af7c9f8f79dc18d4f403a9c2454)

[maven-release-plugin] prepare release 3.1.9

[63aeaf7](https://github.com/dcache/dcache/commit/63aeaf724ea617fe0b6e62dada22563daaed7700)

frontend: refactor static (configuration) data

[7a1b024](https://github.com/dcache/dcache/commit/7a1b0245ecaeeabd8e217281233ff9f550a9b557)

spacemanager: dont try to release expired spaces

[6aee043](https://github.com/dcache/dcache/commit/6aee043cdabfbcb8304a9c34ab475a05d4e8d64d)

srmmanager: use path to support srmSetPermission operations

[183e58d](https://github.com/dcache/dcache/commit/183e58da98229a8051741486e6e3768cd100059a)

frontend: fix Restriction usage

[d3f2ed0](https://github.com/dcache/dcache/commit/d3f2ed0e3037bcaa02a472a75628dd0c2318146d)

poolmanager: fix unit-test to avoid race-condition

[357de74](https://github.com/dcache/dcache/commit/357de74f1a994167b69af706381975b55e8237e6)

zookeeper: work-around SessionTracker racy initialisation on startup

[d24abfa](https://github.com/dcache/dcache/commit/d24abfae7dc1aa0b45ef1ffd4e6ca93d30e55c67)

[maven-release-plugin] prepare for next development iteration



## Release 3.1.8

### Changes affecting multiple services

dCache previously shipped both log4j and log4j-over-slf4j libraries. This patch simplifies deployment and prevents possible problems due to non-deterministic library loading sequences by removing log4j dependencies.

### frontend

If frontend was asked to create a directory listing while a file was being uploaded into the directory being listed, previously, an error would occur. This patch addresses that issue.

This release includes a new dCacheView version.

### info

The info cell can occasionally send messages before it is properly registered. This can lead to `Cannot send message with callback in state...` messages that do not correspond to any valid error condition. This patch ensures that messages are only sent as soon as the cell is properly registered.

### pool

If the communication between a pool and PnfsManager times out, the error message is not well suited to diagnosing the problem: `Failed to instantiate mover due to unsupported checksum type: Request to [>PnfsManager@local] timed out.` The checksum type is not playing an important role here. Hence, this patch updates the error message.

### zookeeper

Embedded Zookeeper instances would occasionally log stack-traces on startup. This patch adds a work-around.

Zookeeper logs a stack-trace in cases where the client disconnects unexpectedly. This is unnecessary and potentially confusing, so this patch changes Zookeeper’s behaviour to just logging the incident.

### Changelog 3.1.7..3.1.8



[e5b9c6f94b](https://github.com/dcache/dcache/commit/e5b9c6f94b08046736af9e2cdaa0a75e4c851434) [maven-release-plugin] prepare release 3.1.8

[a5939058d3](https://github.com/dcache/dcache/commit/a5939058d39a57a5db4269b8a3fb41f46de589f1) dcache: release dcache-view 1.2.1 for dcache 3.1

[a2092a23a3](https://github.com/dcache/dcache/commit/a2092a23a3d9e8f98fbb4936a52379fc7b73ffc0) zookeeper: work-around racy startup

[cc8cae2998](https://github.com/dcache/dcache/commit/cc8cae2998245de56e1ac9bc4fb187948f24e6a0) zookeeper: silence ZK server errors

[592d7ecb9f](https://github.com/dcache/dcache/commit/592d7ecb9fb9015d02eba96090eb620623b7e097)

dependencies: remove log4j jar

[61e49d91b7](https://github.com/dcache/dcache/commit/61e49d91b77ade3e0a9bdc4d9bd93d125583d22e)

frontend: fix “Attribute is not defined: SIZE” bug

[b63a3e361f](https://github.com/dcache/dcache/commit/b63a3e361f746513108fdf9a48e943aa8a070c53)

pool: fix error message on timeout

[1a76715347](https://github.com/dcache/dcache/commit/1a76715347986c9984e18c976532a54f97af141b)

info: avoid sending messages too early.

[c1d00aa457](https://github.com/dcache/dcache/commit/c1d00aa457b87f77b290ae58f9c5e21c80e46358)

frontend,webdav: add supress-wwwauthenticate to allow headers

[b4cae3b794](https://github.com/dcache/dcache/commit/b4cae3b794fe6edfb646c3c58055af31ce114cce)

[maven-release-plugin] prepare for next development iteration



## Release 3.1.7

### frontend

Clients can now send a `Suppress-WWW-Authenticate` header in order to avoid the native login dialog in browsers.

### hsm

A potential space leak in staging requests has been mitigated.

### pool

Since there are various reasons for why a mover may be terminated, the previous log message “Transfer was forcefully killed” is not detailed enough to deduce the reason behind the problem. This patch enables more detailed error messages both in the log files and in billing. Note, however, that the door’s report of the failed transfer may duplicate this information.

### webdav

A recent update, commit 5abc0e1c, improved the behaviour of the Milton WebDAV libraries if an IOException occurs during an upload. That patch, unfortunately, did not address all issues, and when non-spec-conformant clients are used against dCache, stacktraces can be triggered.

This patch corrects that behaviour. Also, in case of errors, the error code returned in case of any problems was changed from 400 to 500, which should signal cliens that they are free to retry the transfer after a timeout.

In case of failing transfers, doors will log more accurate information.

### Changelog 3.1.6..3.1.7



[5a4f1135fc](https://github.com/dcache/dcache/commit/5a4f1135fc57387b5c952db7f6c9ae1cb6abbb22)

[maven-release-plugin] prepare release 3.1.7

[759ea0e32f](https://github.com/dcache/dcache/commit/759ea0e32f3f0293544d58893c2c38d2f1c65040)

authentication: suppress WWW-Authenticate if requested

[ddbb94b2c3](https://github.com/dcache/dcache/commit/ddbb94b2c3cf065eaebf5bea5b68f9f2c73c8a11)

webdav: improve logging on transfer failures

[ee9dbc1848](https://github.com/dcache/dcache/commit/ee9dbc1848cf9abe2495bb07cec48c846253d038)

pool: log why a transfer was forcefully aborted

[a3eecab1d4](https://github.com/dcache/dcache/commit/a3eecab1d495e4a53becdf913f4c81279c1ce760)

webdav: make Milton work-around more robust

[60942b1a88](https://github.com/dcache/dcache/commit/60942b1a88b09f5f6f9f6e45addedf51b9456fae)

script-nearline-spi: fix space leak when polling script is used

[3b21208792](https://github.com/dcache/dcache/commit/3b21208792dc6826f2c400fe48684d0aab166373)

[maven-release-plugin] prepare for next development iteration



## Release 3.1.6

### http

In an HA setup with multiple pool managers, the httpd (old) service failed to fetch the list of restore requests from all instances. Instead the service would query one of the instances, possibly alternating depending on the grouping of services in domains. This behaviour has been corrected, so that the http interface now shows all restored entries even in HA configurations.

### webdav

File transfers through WebDAV doors could potentially bypass any Restrictions checks in PnfsManager. This patch ensures that Restrictions are always checked and observed, and improves PnfsManager’s logging to give information in case a Restrictions check is not posssible.

### Changelog 3.1.5..3.1.6



[c2ec867943](https://github.com/dcache/dcache/commit/c2ec867943497143501510a357a9a814d6a67a6c)

[maven-release-plugin] prepare release 3.1.6

[8e85ea4593](https://github.com/dcache/dcache/commit/8e85ea459318734d2d53ddbb5839486a3925cbb7)

webdav: Fix restriction check when downloading a file

[716085c663](https://github.com/dcache/dcache/commit/716085c663762562282d43288b45448364280b8b)

[maven-release-plugin] prepare for next development iteration

[fd903fee0c](https://github.com/dcache/dcache/commit/fd903fee0c56d7293d5c574a8f95ef0ce008187b)

httpd: Fix incomplete restore list in HA setup



## Release 3.1.5

### frontend

OpenID connect can now be enabled from dCacheView. This change introduces three new properties in the `frontend.properties` file, `frontend.dcache-view.oidc-provider-name-list`, `frontend.dcache-view.oidc-client-id-list` and `frontend.dcache-view.oidc-authz-endpoint-list`, all of which are documented in the properties file.

### pinmanager

Upgrades from dCache 2.13 could occasionally fail during the Liquibase update stage. The database table `pinsv3` can not be dropped if it is still referenced by foreign keys of other tables. This modification adds a `cascadeConstraints=true` modifier to the dropTable command used during the conversion process. Thereby, updates are possible without errors and PinManager starts without issues after an upgrade.

### rest-api

Requests to /api/v1/user now include the username of the requestor. This is intended to make working with OpenID Connect tokens easier.

### Changelog 3.1.4..3.1.5



[af98d898fa](https://github.com/dcache/dcache/commit/af98d898fa5bf4efcaf504c777de962eecd82163)

[maven-release-plugin] prepare release 3.1.5

[fef385d10b](https://github.com/dcache/dcache/commit/fef385d10bbc3a9d5bc4b039e245f97f836b8952)

httpd, admin: Fix some hard-coded cell names

[f57cf0a61c](https://github.com/dcache/dcache/commit/f57cf0a61c5674e641c760cdd3f2b03dd6ad4ce0)

frontend: expose open-id connect to dcache-view

[2d0550e065](https://github.com/dcache/dcache/commit/2d0550e065e7e683ff0e3981b1cce9bbeefa1284)

rest-api: include username to the user attributes

[1f0c8ad40a](https://github.com/dcache/dcache/commit/1f0c8ad40a2f33c65d11843b3b30be5990b1f044)

Add cascadeConstraints=“true” to liquibase dropTable action on pinsv3 table

[801ca79374](https://github.com/dcache/dcache/commit/801ca793742ab89e9c1ba2ca12703a1d9ed62fb0)

[maven-release-plugin] prepare for next development iteration



## Release 3.1.4

### nfs

Invalidation of VFS caches has been improved, so that there is no stale information left for dot files.

### pool

Error handling in pools was improved for systems using CEPH backends.

### Changelog 3.1.3..3.1.4



[711ad6df22](https://github.com/dcache/dcache/commit/711ad6df22e9f7ab66d665416b47235c20a656ae)

[maven-release-plugin] prepare release 3.1.4

[fcc95b32bc](https://github.com/dcache/dcache/commit/fcc95b32bc15b629859e439706eed40095f2d5be)

nfs: bind vfs cache invalidation with file’s layout

[c4266f72ce](https://github.com/dcache/dcache/commit/c4266f72ce6135aa35f979465f6485540762c025)

ceph: map RadosException to corresponding IOException

[f7d067ca03](https://github.com/dcache/dcache/commit/f7d067ca03dcca645f0b39c8503f7cc2506ca060)

[maven-release-plugin] prepare for next development iteration



## Release 3.1.3

### nfs

Debugging of stuck transfers has been facilitated by adding the status of transfers to the output of the `show transfers` command.

The assignment of movers to NFS doors has been made more robust.

### system-test

The system-test module, used for demonstration or testing purposes, comes with a built-in X.509 infrastructure. With this release, expired certificates are replaced by new ones.

### Changelog 3.1.2..3.1.3



[1d031ae198](https://github.com/dcache/dcache/commit/1d031ae1989259a3ce2a0e260b5825387a1ce0c4)

[maven-release-plugin] prepare release 3.1.3

[8d6a141f84](https://github.com/dcache/dcache/commit/8d6a141f84064e0f12c046a4faef1ef34eb45fd6)

nfs: show transfer status when displayed

[14df6b8234](https://github.com/dcache/dcache/commit/14df6b82341eaac9b30ed25f7714f9573ecb53e5)

system-test: update disposable-CA generated credentials

[e1ddd06f0f](https://github.com/dcache/dcache/commit/e1ddd06f0f0a24e92e71a3f8fd40d10415be7e90)

nfs: fix loosing movers due to short timeout

[17579bc177](https://github.com/dcache/dcache/commit/17579bc177db30a2ddad1c13893edb5f6bb9537b)

[maven-release-plugin] prepare for next development iteration



## Release 3.1.2

### chimera

In order to improve IO performance, the way dCache updates `atime` values was modified.

### nfs

An internal change in the NFS door code helps reducing irrelevant exceptions being logged.

### srm

SRM no longer times out file requests. This alleviates a rare race condition where timeouts for the file request and file access competed. Requests that time out now always return SRM_REQUEST_TIMED_OUT at request level and SRM_FAILURE for the SURLs in that request.

### Changelog 3.1.1..3.1.2



[b08390f331](https://github.com/dcache/dcache/commit/b08390f3313b50d0cf46419b9ef14b90ce0f8010)

[maven-release-plugin] prepare release 3.1.2

[956da34325](https://github.com/dcache/dcache/commit/956da343253d4355e16c5ab2f105bf66efb4556a)

ceph: log repository IO error

[809b7f43bf](https://github.com/dcache/dcache/commit/809b7f43bfbda8482e84d086e7d7f7bbde643e55)

srm: remove file-level timeout

[b734aae1ba](https://github.com/dcache/dcache/commit/b734aae1baa915940ced9d519f3c894318f099c0)

chimera: do not update inode generation on atime only update

[a68318b6a0](https://github.com/dcache/dcache/commit/a68318b6a041ecbd9eb077cc05a4abe008055770)

nfs: do not add Origin to read-only subject

[c30c9c244c](https://github.com/dcache/dcache/commit/c30c9c244c763c1bdc1aee01da3582ae1e71d494)

[maven-release-plugin] prepare for next development iteration

[c9baa6fa10](https://github.com/dcache/dcache/commit/c9baa6fa1061e9b56e8857a8abb2184996fc51c8)

parent/dcache: add mail jar to deployment



## Release 3.1.1

### pool

Current release improves handling of CEPH exceptions, so that pools can react appropriately when request for a missing file.

Fixes double close on p2p.

### restful-api

Current release adds mime-type to file attributes.

### Changelog 3.1.0..3.1.1



[ccb9e51](https://github.com/dcache/dcache/commit/ccb9e5161398b44ee6c3cc4e068d6022f2e3d510)

[maven-release-plugin] prepare release 3.1.1

[e64219b](https://github.com/dcache/dcache/commit/e64219b7ccf62bc626157d7f8d68c2ac03306a18)

[maven-release-plugin] prepare for next development iteration

[562d467](https://github.com/dcache/dcache/commit/562d467a7157f8d6bb65af431099394ce734a7fa)

restful-api: add file mime-type to file attribute

[671d35b](https://github.com/dcache/dcache/commit/671d35b68540451c889bc1cf3587639731bd4d45)

pool: handle CEPH exceptions

[10e8925](https://github.com/dcache/dcache/commit/10e89256f562ef8921ed2c51cc174a9592a99017)

pool: fix double close on p2p



## Release 3.1.0

#### Chimera CLI can query access latency and retention policy

If you ever needed to query the access latency or retention policy of a file you will be delighted to learn the the Chimera shell now supports doing just that.

To support this, some configuration properties have been added.

Previously, the `chimera` shell reused the `pnfsmanager` properties. With dCache v3.1, the `chimera` shell has its own set of properties. See the `/usr/share/dcache/defaults/chimerashell.properties` file for the details.

In addition, the configuration properties `dcache.default-access-latency` and `dcache.default-retention-policy` have been added. These new properties are the default values for `chimerashell.default-access-latency` & `chimerashell.default-retention-policy` (respectively), and `pnfsmanager.default-access-latency` & `pnfsmanager.default-retention-policy` (respectively).

If you have configured `pnfsmanager.default-access-latency` or `pnfsmanager.default-retention-policy` then dCache will continue to work as before; however, the `chimera` shell may show incorrect information when querying access-latency or retention-policy information of a directory.

To fix this, you should update your configuration so that `dcache.default-access-latency` and `dcache.default-retention-policy` are adjusted instead. These `dcache.` properties should be configured on all nodes where you host a pnfsmanager service or intend to run the `chimera` client.

#### Fail fast on lack of stage permission

If you rely on the pool manager stage protection feature, know that you are a rare breed. We have not forgotten about you though and fixed a problem that would cause staging to be retried and fail repeatedly has been fixed. A user who lacks permission to stage a file is now told so right away.

#### Allow regular expression matching of storage units in resilience manager

Pool manager allows matching storage unit names by regular expressions. Resilience manager failed to mirror this feature in previous versions. Expect this to no longer be the case. As the developer put it: Resilience also supports what PoolManager supports.

#### Drop support for regular expression matching in alarms

Since we needed regular expression matching in resilience, we had to remove it from alarms…

Just kidding. We removed it because it limited scalability and greatly complicated the code and a poll among users showed nobody used it. Alarms can now be defined at any logging level without risk of denial of service on the server. In order to guarantee such alarms be sent, the remote logging property should be set to an adequately low level. Currently this would be WARN.

#### Storage URIs can be set through NFS dot commands

A dot command, `.(suri)(<file>)`, has been added to NFS by which one can store, retrieve and modify the URI string(s).

#### Chimera now tracks file state

Traditionally it was difficult to distinguish a file that is still being uploaded from one for which upload has completed. Chimera now holds this state information, which improves the reliability of detecting this state and reduces load on the database. The change is backwards compatible and does not require schema changes.

#### RESTful improvements

Now it is even easier to get rid of your files thanks to a new RESTful API for file deletion.

The MIME type of files can be queried. This is particularly useful for dcache-view which can now show a file type specific icon.

#### gPlazma can parse IGTF info files

The x509 gPlazma plugin can now parse IGTF info files and generate IGTF policy principals. These are currently unused.

#### Migration module can now define target pool by attached HSM

A new `-target=hsm` option was added to the migration commands to define target pools in terms of attached HSM system.

#### Option to disable h-flag update after upload

Pools set a flag in the level 2 name space entry after upload to indicate whether the file is uploaded to a tape connected area or not. This is mostly a historic flag and most sites do not use it. Pools now have an option to disable this update, which reduces latency upon upload, load on the namespace database and the namespace disk requirements.

#### Support for Third Party WebDAV copy for OpenID connect authenticated sesssions

The WebDAV door support third party copy for clients that authenticate through OpenID connect. See configuration details in `/usr/share/dcache/defaults/webdav.properties`.

Somewhat related, the gPlazma `multimap` plugin has gained support for mapping OpenID connect groups.

#### NFS

The NFS support now has better support for the Mac OS NFS 4 client due much improved lock support.

The NFS door now detects when pools are disabled and informs NFS clients to no longer connect to such a pool. This means that read transfers can now survive pool restarts, and can possible be redirected to another pool containing another replica of the file. Disabling a pool in pool manager will trigger a p2p copy of open files to allow NFS clients to be redirected.

The NFS pool selection logic has been refined to avoid live lock in case of high latency pools (either because the pool is very busy or because of a high latency WAN connection).

### Changelog from 3.0.0 to 3.1



[26dc5c0a1f](https://github.com/dcache/dcache/commit/26dc5c0a1f76a87c96736efa7fcb03e8be40e6d6)

nfs: recall file layout on pool disable

[1b7f246d42](https://github.com/dcache/dcache/commit/1b7f246d4212409ad9d86c8fd719f03da1219966)

libs: update to bug fix release nfs4j–0.14.2

[8112a3f116](https://github.com/dcache/dcache/commit/8112a3f116da56bcc608928b3ddb7527ccd68841)

srmclient: fix handling of checksum options

[9fe6a3ff0c](https://github.com/dcache/dcache/commit/9fe6a3ff0ca4ecd86c9c19a896314a4d7af35502)

srmclient: fix compatibility with castor

[9e8ebba22c](https://github.com/dcache/dcache/commit/9e8ebba22c7aec5feb78fab118474f6f3ce673c8)

chimera : handle empty paths elements path2inumber stored procedure

[adcddbfa0e](https://github.com/dcache/dcache/commit/adcddbfa0ee9aea4f0b1081346b288cc39dcb03b)

ftp: prevent execution of most commands when unwrapped

[42e4098b36](https://github.com/dcache/dcache/commit/42e4098b364250736f262c5ef8f523536e8e9c73)

[maven-release-plugin] prepare branch 3.1

[1ac8040457](https://github.com/dcache/dcache/commit/1ac80404572fddcf1369c41b50b8c9e4c7ce933b)

ftp: do not fail proxy transfer if read returns zero bytes

[b1339b3a85](https://github.com/dcache/dcache/commit/b1339b3a859bf8ce306f6ebbae63318864423849)

lm: Do not rely on thread interrupt for shutdown

[364a089b89](https://github.com/dcache/dcache/commit/364a089b892e831b8c6d3f6cc06f0741de1c085c)

chimera-nfs: add get and set for storage uri

[ae1017c854](https://github.com/dcache/dcache/commit/ae1017c85445faeccef4a2a220abda6c2bfa2bd4)

migration: `migration copy` can filter target pools by `hsm` values

[88aa842a79](https://github.com/dcache/dcache/commit/88aa842a79bdb3cd2b78d0d1bf6a1f741a829fee)

utils: add common place where default TCP port numbers are resolved.

[1bc02c3a1c](https://github.com/dcache/dcache/commit/1bc02c3a1c0de8653a73a1bda59b63ca22612298)

ftp: implement the MLSC command

[4a22f6e939](https://github.com/dcache/dcache/commit/4a22f6e939de7be24b4e4d4d4a8d55b6da78688e)

srm-client: use default GridFTP port if not specified

[55c7b56ef6](https://github.com/dcache/dcache/commit/55c7b56ef6c54ada337c85ad4725fcbd377ca11f)

ftp: Add support for SITE WHOAMI command

[0080ec5331](https://github.com/dcache/dcache/commit/0080ec53312eb0390127ecae6ce7b740429cfd16)

resilience: restore inaccessible file handler interface

[0076f80ba6](https://github.com/dcache/dcache/commit/0076f80ba69d0e1ed15f85cff7b280f42d572934)

ftp: update parsing of CLIENTINFO command

[d223ffb538](https://github.com/dcache/dcache/commit/d223ffb538afc0c49f4d02a405514e907c0f552f)

srm: include remaining request lifetime in various responses

[e1692b7bb0](https://github.com/dcache/dcache/commit/e1692b7bb00622d3ab1c414cbf21661cdcb3244d)

srm: update srm request.*.lifetime configuration properties documentation

[ba6664d04f](https://github.com/dcache/dcache/commit/ba6664d04fbed33c28103f9b2a3ec05a2b32e131)

ftp: modify facts describing namespace ownership

[5ba2dcdb11](https://github.com/dcache/dcache/commit/5ba2dcdb112012e3dee525b31944f00f3e945d5a)

nfs: bind mover shutdown to open-state

[fb639a896c](https://github.com/dcache/dcache/commit/fb639a896c4a5406be220a937fcb1e267e89430b)

ftp: add support for SITE TASKID command

[2604f72771](https://github.com/dcache/dcache/commit/2604f727717f9b243c4ffb8df07f19db133f587f)

ftp: add initial support for checksum performance markers

[476018c6ab](https://github.com/dcache/dcache/commit/476018c6ab75ab00af967764d80e51d2d30f90a0)

libs: update to bugfix release nfs4j–0.14.1

[cf35e28dfd](https://github.com/dcache/dcache/commit/cf35e28dfd6d67936f7f660b5df3bbce5d8ef6f5)

Revert “lib: Update to liquibase 3.5.3”

[bb7e326ab2](https://github.com/dcache/dcache/commit/bb7e326ab269f1de00214b75234bf0655acb07be)

nfs: fix broken commit d2da5ba

[d2da5ba4ef](https://github.com/dcache/dcache/commit/d2da5ba4efe80964e9f2bf71ef016512a06e8c5e)

libs: update to nfs4j–0.14.0

[9d07a6d398](https://github.com/dcache/dcache/commit/9d07a6d398e865e9187b4d728a070ae8010b704b)

lib: Update to liquibase 3.5.3

[3a10b0bfdf](https://github.com/dcache/dcache/commit/3a10b0bfdf1d481b3739832c5968da1ab84041b2)

pool: Port several commands to annotated command infrastructure

[9e0ef1461c](https://github.com/dcache/dcache/commit/9e0ef1461c574c1ecd9b66cc925dcdc910f41490)

pool: Clean up logging in PoolV4

[a9c653871e](https://github.com/dcache/dcache/commit/a9c653871e899992b5043a7d6dc7854bdf11caab)

pool: Allow concurrent replica updates in migration modules

[0ee24c622b](https://github.com/dcache/dcache/commit/0ee24c622b3b6ebb76b75f4ed5127fec1d03d733)

rest: add home directory to user info

[60606a6321](https://github.com/dcache/dcache/commit/60606a6321a1d33d1b5b4c25ec2c993a6b3a3216)

restful: support querying QoS through namespace

[38238a40d0](https://github.com/dcache/dcache/commit/38238a40d0c62028ef2bb07216ecf69c05831a59)

restful: improve error handling

[51cfcea25c](https://github.com/dcache/dcache/commit/51cfcea25c65a338ef9339763819c0d604f73232)

ftp: add support in OPTS RETR for specifying performance marker frequency

[4ce227afd7](https://github.com/dcache/dcache/commit/4ce227afd7de9cdcee38b0521253cbc4853414a2)

ftp: show SIZE facts for directories

[1c6d7cd7b7](https://github.com/dcache/dcache/commit/1c6d7cd7b7a0c9358129f9985f2cb290e1885b11)

ftp: add support for paths relative to home directory

[f3590f018d](https://github.com/dcache/dcache/commit/f3590f018dca4db75c170392421b746713a02512)

xrootd : use lower case for checksum algorithm names when replying to checksum queries.

[583477ac75](https://github.com/dcache/dcache/commit/583477ac752fc53073bb830d1e06a1e1dac895fc)

dcache: update dcache-view version to 1.2.0

[c171139ba0](https://github.com/dcache/dcache/commit/c171139ba061995c81ecfe704b12fcd648b8164d)

nfs: move mover shutdown logic into NfsTransfer class

[fb30d68350](https://github.com/dcache/dcache/commit/fb30d6835011e1763eb27080f277fcd6e62165e7)

gplazma: Support for OpenId Connect groups in MultiMap file

[2fba197cd1](https://github.com/dcache/dcache/commit/2fba197cd1d78bba006908ccd0e541ddbade0d53)

common, gplazma: Added OpenId Connect Groups Principal

[9d27520c5b](https://github.com/dcache/dcache/commit/9d27520c5bf095ed442f6fd87a149d1ef474645f)

dcache: canonicalize values in any-of properties

[63a154e8b9](https://github.com/dcache/dcache/commit/63a154e8b9f057dcc9018c95ffddbb4da2927d51)

cleaner: show delete notification targets

[dcf2dd9292](https://github.com/dcache/dcache/commit/dcf2dd9292c836b18a4189a8737db9a55ccf9118)

systemtest: allow anonymous dcap activity

[44dc08f1bd](https://github.com/dcache/dcache/commit/44dc08f1bdb152d2c7748181211a1a2cbb0c174b)

srm: use Jetty jar to supply DTD

[389f43353a](https://github.com/dcache/dcache/commit/389f43353abc226285f395d254c931a83fadf2c6)

rest-api: remove restriction on delete

[ecf5d2607f](https://github.com/dcache/dcache/commit/ecf5d2607faf2f1368bf1e04abcd057fca3532cf)

pool: Fix race and nested transaction problem during deletion

[2469be06e6](https://github.com/dcache/dcache/commit/2469be06e6a2795a7c7a8ad64bfc52026c946094)

pool: Fix transactional behaviour with Berkeley DB

[0c13fa2fa6](https://github.com/dcache/dcache/commit/0c13fa2fa67708c9aef8418816e3539c4d330c2c)

lm: Fix lost thread interrupt that prevents shutdown

[cb737383d2](https://github.com/dcache/dcache/commit/cb737383d23c9be6cd087932f4a133f5cce76124)

lm: Log when connectors are killed

[5165e846c8](https://github.com/dcache/dcache/commit/5165e846c8903bdb8f5c6f1a4b393a0e5bcc715a)

cells: Schedule watcher notifications on cell event thread

[dd3d4894ff](https://github.com/dcache/dcache/commit/dd3d4894ff8697dab93e1f7c4126b2f5417d33b7)

srm: fix recovery procedure in internal copy if source is deleted

[de3802e907](https://github.com/dcache/dcache/commit/de3802e90718fcf27cc57383c05bb9ae315e2340)

gplazma-ldap: fix default properties for root and home

[00fbe6d28d](https://github.com/dcache/dcache/commit/00fbe6d28db9200eab6a22c8f480aea3df0788a3)

srmclient: consolidate credential expiry, don’t use RuntimeException

[1deea832e6](https://github.com/dcache/dcache/commit/1deea832e6eb37e0ec7b71e39000cb7d8f0a9f5c)

dcache: update dcache-view version to 1.1.2

[721d6a35ca](https://github.com/dcache/dcache/commit/721d6a35caf63a6e458bb35126f49f92a3dce1e4)

resilience: fix fairness algorithm bugs in file operation map

[9324747ef6](https://github.com/dcache/dcache/commit/9324747ef6017a91126fb365bb9cb7c969db2959)

nfs: rework pool selection to get rid of too many retries

[57e9f6b2a3](https://github.com/dcache/dcache/commit/57e9f6b2a3f5fa2147656c5994d60e921885e6c7)

minor typo corrections

[66e218503b](https://github.com/dcache/dcache/commit/66e218503b7e536556198dd78b42358a74e615d2)

Fix botched commit

[5e5a0f002a](https://github.com/dcache/dcache/commit/5e5a0f002af5fcde7a0c65414cbfa10f8f6db02f)

Never declare @Command callable to throw Exception

[9f31f06508](https://github.com/dcache/dcache/commit/9f31f06508e139fb5d139fdb34a97c618024c981)

srmclient: avoid deprecated Guava API

[fc90079234](https://github.com/dcache/dcache/commit/fc900792344f0413424a7ab2d0773c752fbab02c)

srmclient: add lint checks, fix various minor issues

[eaa63192c9](https://github.com/dcache/dcache/commit/eaa63192c9ae607d3d75b8830e61c47015eaad16)

pool: make update of level2 with hsm flag optional

[267b923f30](https://github.com/dcache/dcache/commit/267b923f305ff5897741581c99478c212187b197)

chimera: fix file state initialization for non postgres backends

[32324e6789](https://github.com/dcache/dcache/commit/32324e6789dcd4c33e966c353a733f649d4a9a2d)

chimera: introduce file state field

[65c0b2614e](https://github.com/dcache/dcache/commit/65c0b2614e1941d47c4a94ff9ec6802d8045b6ba)

Motivation:

[896bf55950](https://github.com/dcache/dcache/commit/896bf559507fe23cc785237d2fdcf466747e1118)

resful-api: add file’s MIME type to the file attributes

[4e22dd0b6a](https://github.com/dcache/dcache/commit/4e22dd0b6afc4fc161f759f95a365af32c8232be)

gplazma-ldap: rewrite junit tests in java

[4d4b45d142](https://github.com/dcache/dcache/commit/4d4b45d1425e8e2091350b9a2347d6ed0be353a5)

pool: fix URISyntaxException in ceph backend

[ead5889a46](https://github.com/dcache/dcache/commit/ead5889a469b232a5f03bf0a075b3169f4350b9b)

dcache: correct the output directory

[9e08ca3a66](https://github.com/dcache/dcache/commit/9e08ca3a663d05ca6594226cb1f307fe9b7c67d5)

dcache: update dcache-view version

[12df63eb72](https://github.com/dcache/dcache/commit/12df63eb72fe5cd3581834776190a2347b50b22a)

PoolManager : stage protection add protocol to the list of discriminators

[761f19b652](https://github.com/dcache/dcache/commit/761f19b652a33149400b3c1b21a06cc594e9f793)

dcache-restful-api: add restful call to delete files

[2483b81204](https://github.com/dcache/dcache/commit/2483b8120490d2b0d6c8a11c70c4b49dec33bf7a)

dcache-restful-api: Path mapping between client requested paths and corresponding dCache internal paths.

[5a11546083](https://github.com/dcache/dcache/commit/5a115460837353745501ab36cc3d06a3ad3f6f51)

correct chimerashell.db.url property

[1aa72c0d6c](https://github.com/dcache/dcache/commit/1aa72c0d6c9fbb32713bc9dd4adf4f7039d0c838)

pool: ‘hsm ls’ must show all configured hsm if no argument is provided

[db0a2b1490](https://github.com/dcache/dcache/commit/db0a2b1490e57125b4b6c3285dab95aab36cc10b)

dcache-chimera: add get AccessLatency and ger RetentionPolicy command to CLI

[d9ec1e52f8](https://github.com/dcache/dcache/commit/d9ec1e52f89a85eff860bb8016539d21cb286e9e)

srm-common: don’t retry when JVM runs out of memory

[ceb73be210](https://github.com/dcache/dcache/commit/ceb73be210751b49b69d39bf3712d841be02f619)

transfermanager: tidy up output from ‘info’ ‘queue’ and the two ‘ls’ commands

[ed91fd0759](https://github.com/dcache/dcache/commit/ed91fd07592992d0d4d460cf605677e8ad9f1fd1)

cells: fix ‘This stopwatch is already stopped’ error

[ec7ac10845](https://github.com/dcache/dcache/commit/ec7ac10845df731b213b68ab5c62e6ba6361e56a)

srmclient: use streaming deserialisation, allow more memory.

[8d685bec46](https://github.com/dcache/dcache/commit/8d685bec4605dc728cd9c4b7aaaea5edf8aea58f)

chimera-enstore: specify fields order on insert

[cf4ced3da0](https://github.com/dcache/dcache/commit/cf4ced3da049eefa4c337c0a7a54a8d958aab7df)

cells: do not fall-back to DEBUG if invalid log level provided

[c6c18c927f](https://github.com/dcache/dcache/commit/c6c18c927f890d015ef8a8b55d5c0caf5a2fb616)

NFS: throw FileNotFoundHimeraFsException in case of fumbled “.(get)” command

[7b9f49aa30](https://github.com/dcache/dcache/commit/7b9f49aa30170b48e06175df90a2d989060905fb)

nfs41: fix open-stateid leak introduced in 0702d73

[be2d292925](https://github.com/dcache/dcache/commit/be2d29292520709005b407e158a3c84448517473)

srmclient: support srmfs with command on command-line

[d7c3d9d2aa](https://github.com/dcache/dcache/commit/d7c3d9d2aaaf4b165e3fdd2a1d4ada37d55b2356)

srmclient: show SOAP response from server when debug enabled

[c6912edb27](https://github.com/dcache/dcache/commit/c6912edb274379d463050478e7eeca2c54a75aa8)

srmclient: percent-encode paths that require it

[bd93f70aec](https://github.com/dcache/dcache/commit/bd93f70aecb4eb8f48cc7c49334541a4c4a3217d)

srmclient: fix stat/ls caching for glob expansion for DPM

[ef12033cc8](https://github.com/dcache/dcache/commit/ef12033cc899f7a593e54e68d3fc405741401c38)

srmclient: fix deploying srm-client in path with spaces

[6d0044838b](https://github.com/dcache/dcache/commit/6d0044838bbc456b9534b79aa213261f2fc7acf2)

srmclient: fix Java 7 compatibility for srmfs

[33c18788e2](https://github.com/dcache/dcache/commit/33c18788e25e02941ab66fb507344d7609c1ed5b)

doors: add diagnostic information for NIC auto-discovery

[ece9982a98](https://github.com/dcache/dcache/commit/ece9982a985d5b4eeb86cbea48896eb8ae45a157)

pool: Delete files concurrently

[c993db8124](https://github.com/dcache/dcache/commit/c993db8124f5c32e616246205df3a1a673d5e636)

cleaner: Send notification more often

[81af267c13](https://github.com/dcache/dcache/commit/81af267c13e9682faf041ffd0e5fec0b2fbf9692)

pool: Fix csm check command in the pressence of broken files

[0702d733bd](https://github.com/dcache/dcache/commit/0702d733bd534c529f203640169f29fe2e7b475b)

nfs: discover open-stateid during layout return

[bbdd62cd58](https://github.com/dcache/dcache/commit/bbdd62cd58b159d69638fc3c7cde7f839c6819a9)

cells+dcache: fix Reply handling in batch processing

[d082578292](https://github.com/dcache/dcache/commit/d08257829224df807602c22a0a8b54578c06650f)

ftpclient: fix compatibility with Globus FTP server

[ef74fd7b69](https://github.com/dcache/dcache/commit/ef74fd7b6908371fce745e3726631b2bf2a0705f)

pool: optimize checksum channel calculation

[67915f657b](https://github.com/dcache/dcache/commit/67915f657b9d7cabbd54ffb6b26afbe3e6940314)

srmclient: ensure a reasonable error message

[067b39cede](https://github.com/dcache/dcache/commit/067b39cede76da450703982f47156d447893441c)

srmclient: fix DPM compatibility with SRM transfer requests

[7186653283](https://github.com/dcache/dcache/commit/7186653283814589b0d06ec2a8ecd71b5ff440c1)

ftpclient: fix multiline ADAT reponses

[4ac1cea2df](https://github.com/dcache/dcache/commit/4ac1cea2df1612abee0c984151bee7e040aaed65)

ftpclient: encrypt SITE CLIENTINFO command

[5c8fc8085e](https://github.com/dcache/dcache/commit/5c8fc8085e18452c8fd4e6f5ba44bd9493c03943)

pool: add a possibility to control nfs movers threading policy

[f24bf0b18b](https://github.com/dcache/dcache/commit/f24bf0b18b283e8a129eacd844307ca1bb265457)

nearline storage: remove masking of HSM return codes

[3d1371a170](https://github.com/dcache/dcache/commit/3d1371a1704e24a6589447b557310a58d3d78dca)

nfs: remove deviceid to data server mapping when pool is removed

[f70172aefe](https://github.com/dcache/dcache/commit/f70172aefe49e6f69cde914146c5c76d98204a22)

PoolManager : set return code to CacheException.PERMISSION_DENIED if staging is not allowed due to stage protection.

[0c0ee5b17b](https://github.com/dcache/dcache/commit/0c0ee5b17be3dbfeeca487ca239fafd4b3afa3a6)

nfs: do not log NFS errors when creating proxy adapter

[a328fa64f4](https://github.com/dcache/dcache/commit/a328fa64f471c0789b5d29eca5345cfe6ab0336f)

srmclient: avoid NPE when stat directory with DPM

[c8f219ef02](https://github.com/dcache/dcache/commit/c8f219ef024719ea3ecf1be3970b71fb1cca405f)

pool: Use concurrent collections for high level parts of migration module

[9570497848](https://github.com/dcache/dcache/commit/9570497848bc5ea549ac0874446ed42d5d9e7ef7)

pom: Update third party dependencies

[9692af7a8b](https://github.com/dcache/dcache/commit/9692af7a8b2bd9be81b0e693cb91ab39fca7e85b)

pom: Update SMC to 6.6.0

[522648c8fd](https://github.com/dcache/dcache/commit/522648c8fd3d4d2805cf112fd048cc0ff0279489)

pom: Update to Guava 20

[720216df2f](https://github.com/dcache/dcache/commit/720216df2ff40b2498015b2e45820ba316345bef)

nfs: do not use AtomicInteger where access already protected by lock

[74ae82647e](https://github.com/dcache/dcache/commit/74ae82647ef9fb1e284ba6c8ecfd3b19d3a3ee83)

srmclient: add glob support for lls and ls

[5d75b18c2c](https://github.com/dcache/dcache/commit/5d75b18c2cc8b20eea0c4f352af31f6358acb827)

resilience: python script for making database changes necessary for migration from old replica manager setup

[dbe2429b06](https://github.com/dcache/dcache/commit/dbe2429b061699d54253ab0550d560c5f96a9683)

pool: Reduce lock contention in migration module

[2db55843f4](https://github.com/dcache/dcache/commit/2db55843f4b13c43144e7174f552f9c625cfdff3)

srmmanager: Adjust semantics of concurrent upload detection

[9e34beba62](https://github.com/dcache/dcache/commit/9e34beba6208c322694ac1933cdbc830334e9f40)

srmclient: by default show only CN of owner in ‘ls -l’ output

[45a584b583](https://github.com/dcache/dcache/commit/45a584b583ba145571159f5700927ff75a1da5e2)

spacemanager: Fix shutdown bug causing a file to leak from a reservation

[af7c8dce40](https://github.com/dcache/dcache/commit/af7c8dce40b86adb562f42a6914a9fbd1e0cd9cb)

spacemanager: Fixes a message bounce bug

[e3e293c9b8](https://github.com/dcache/dcache/commit/e3e293c9b8142b93a3a590a303f4f1e37a66a849)

Change version to 3.1.0-SNAPSHOT

[61264724d9](https://github.com/dcache/dcache/commit/61264724d95108d30b849fbbbf7ab9714b748836)

srmclient: add SRM call statistics

[5b327a5017](https://github.com/dcache/dcache/commit/5b327a5017da9528d26f6d232fb1b9990278e20f)

srmclient: update command names in srmfs

[2edc97bb1d](https://github.com/dcache/dcache/commit/2edc97bb1daf40fbef24211bf7b3bacade8f9fe7)

srmclient: fix srmfs ‘get permission’ command

[b861be09a8](https://github.com/dcache/dcache/commit/b861be09a8e6d561957ebe5e89a72fe8a6f9998a)

gplazma: add IGTF policy princpals with X.509 login

[40c3485f71](https://github.com/dcache/dcache/commit/40c3485f7190d9dafc0b9a755a82df3fdea8e1cb)

srmclient: fix compatibility with Bestman

[30d7604513](https://github.com/dcache/dcache/commit/30d7604513529520b53a9763f6615e7020da521c)

srm: Sumbit token less releaseFiles requests to all backends

[4a477c95a0](https://github.com/dcache/dcache/commit/4a477c95a03d55361e28800b720f35f2a481b95b)

srmmanager: Support upload detection in clustered environments

[d300515d4a](https://github.com/dcache/dcache/commit/d300515d4a75efe072e4a8cad7b399ed076d49b5)

srm: Redefine the semantics of active upload checks

[7ab3f5e8f7](https://github.com/dcache/dcache/commit/7ab3f5e8f7144b4349bb6362907247a805139755)

srmmanager: Refactor how various operations handle active transfers

[bd75e3dc88](https://github.com/dcache/dcache/commit/bd75e3dc88ed0f1d24d9979df099d0167ff70e01)

srmclient: probe for SRM endpoint parameters that the user doesn’t specify

[f9eabd2666](https://github.com/dcache/dcache/commit/f9eabd2666836333f45830af92ad6a85e8deac24)

Resilience: Restore support for regex matching on storage unit names

[fab9727aab](https://github.com/dcache/dcache/commit/fab9727aab57922725477d5353970d66827d976c)

Resilience: separate out the data structures for handling storage units from those for pool groups

[5d2aa238bd](https://github.com/dcache/dcache/commit/5d2aa238bd994adc8100d7eaceeeeb9c7e5238bd)

Resilience: Support matching the universal and class default storage unit expressions

[7cb18615f8](https://github.com/dcache/dcache/commit/7cb18615f8f4635efc4828d3893b77552cfff743)

core: make it optional whether builder creates a readOnly subject

[12fbe75fb8](https://github.com/dcache/dcache/commit/12fbe75fb85478b0e6a8a42e67bbc4bae149010f)

pool: simplify checksum channel logic

[37bb8dc937](https://github.com/dcache/dcache/commit/37bb8dc937537d9abd7b3eb3b0b1c6c222a98317)

core: update stage protection unit-tests

[f6a8284ca8](https://github.com/dcache/dcache/commit/f6a8284ca86164d026fb592f2dd2b3d1411181e6)

dcap: don’t create stack-trace if tunnel fails due to bad client

[fa7b0fb8bd](https://github.com/dcache/dcache/commit/fa7b0fb8bdb481efd46d3946bfc753bb99099ff9)

PoolManager : stage protection, fix error in stage.fragment

[e1c2aabb47](https://github.com/dcache/dcache/commit/e1c2aabb4725262a320e5074babe82fbaac677a1)

alarms: shift alarm filtering to client side

[154a1f65a1](https://github.com/dcache/dcache/commit/154a1f65a12dcb30c995d4eef7037e12160e7f24)

alarms: remove support for custom server-side regex alarm definitions

[9d286e7142](https://github.com/dcache/dcache/commit/9d286e714212af073de1a1510e81b07a16922cb2)

webdav: fix thrown NPE when CORS is set

[002b13352a](https://github.com/dcache/dcache/commit/002b13352a0091ffb338bf0c1a9e9b97efa6a15f)

dcap: expose dcap client version limit

[b18a63fc02](https://github.com/dcache/dcache/commit/b18a63fc027c87b739dfb1a3344bd9df8ae121e7)

dcap: Register DCAP interpreter as a command listener

[efda7f2a4c](https://github.com/dcache/dcache/commit/efda7f2a4cdc8e706eb517c803a37870f31ce7a5)

dcap: fix Kerberos dcap if principal contains a ‘-’

[4ee298e6c4](https://github.com/dcache/dcache/commit/4ee298e6c44757a0d65921279262a6ff13b87218)

dcap: fix regression in handling old version

[93c0ec161e](https://github.com/dcache/dcache/commit/93c0ec161ef2077401f31819b313252a057a720b)

cells: Fix NPE in location manager

[df12c09d68](https://github.com/dcache/dcache/commit/df12c09d68a96e25095e7a1a95961378fd60ab27)

srmmanager: Add interface to query and abort transfers

[f34c7f2734](https://github.com/dcache/dcache/commit/f34c7f2734ea42b300ac8b7cf6c3e8582198e84b)

cells: Remove meaningless logging in location manager

[2fb8d33e62](https://github.com/dcache/dcache/commit/2fb8d33e62d8a51be835afd71af7c301c922ce7d)

cells: Log expanded cell name

[26ce471a96](https://github.com/dcache/dcache/commit/26ce471a962e8157133297301f35f46f01a18863)

cells: Remove resubmission to event thread in location manager

[ede86ad03a](https://github.com/dcache/dcache/commit/ede86ad03a7fb7aa1707bb260b0ca4a6e8f7f2a2)

cells: Add safe guards to connector create and process update events

[406df24882](https://github.com/dcache/dcache/commit/406df248824b05c1ad4f86bd4222fba3101baa6c)

srmclient: fix ‘cd’ compatibility with StoRM

[01efa18dc4](https://github.com/dcache/dcache/commit/01efa18dc45ccee91eeb84c1fb9d38bc53e1fc8d)

poolmanager: Log pool name rather than SelectPool object id

[0b782a5bed](https://github.com/dcache/dcache/commit/0b782a5bedb6433629f07b85fb268f6198375a2c)

pool: Suppress two stack traces in nearline storage handling

[73919be57a](https://github.com/dcache/dcache/commit/73919be57a13667ddc0977126bdeb0f5e244e209)

srm: Log correct request token in access log

[b1b2af95a1](https://github.com/dcache/dcache/commit/b1b2af95a1685d7a00619b2876b8e3ca46b701ba)

httpd: Enable X-Forwarded-For processing in httpd

[431ae2f929](https://github.com/dcache/dcache/commit/431ae2f929fcd75af774fbd2efebe763dbfbdb32)

httpd: Don’t insist on using http for unauthenticated webadmin pages

[45f265354a](https://github.com/dcache/dcache/commit/45f265354ad6e51b13787d15a90efe7162fa39d9)

nfs: allow dCache to start up without DNS

[26d16f20d3](https://github.com/dcache/dcache/commit/26d16f20d365ac3745e22c8577927ee622fb7a89)

billing: fix stacktrace and slow shutdown if in refresh

[2bca29803b](https://github.com/dcache/dcache/commit/2bca29803b3c26124f063044f8280ee8a56fbe1e)

webdav: improved the description for the usage of 3rd-party transfer with OpenId Connect via Token Exchange

[e85ae7cd2b](https://github.com/dcache/dcache/commit/e85ae7cd2ba91b4ffae518da34cf6c076f20a28e)

webdav: fix error during context initialization of webdav

[d132d86052](https://github.com/dcache/dcache/commit/d132d86052507b3f459c72c8b6788ba5deb5d638)

webdav, dcache: Support for third party copy on the Webdav door using OpenId Credentials

[b8bc5b1553](https://github.com/dcache/dcache/commit/b8bc5b1553d2cb74915fef1a4109a4fc11187f71)

common: fix alignment of abbreviated byte column in ColumnWriter

[14ac12415c](https://github.com/dcache/dcache/commit/14ac12415c1614ef07bd6703ad44c6b333aba6b2)

srmclient: add initial support for glob expansion

[f02a23afc8](https://github.com/dcache/dcache/commit/f02a23afc897811ce566199ad4a769fd25cd4ab8)

cleaner: Send notifications concurrently

[20fdc8130b](https://github.com/dcache/dcache/commit/20fdc8130b4666f18aed9d5788d051ac2f675020)

poolmanager,spacemanager: Do not reply to pool manager query replies

[b78cb3a869](https://github.com/dcache/dcache/commit/b78cb3a869c81e3efb48f190d352dbf11d06aad1)

dcache: Add column to `dcache services` for proxy-protocol

[9a83eb35cb](https://github.com/dcache/dcache/commit/9a83eb35cb467b99b0dbcc55c522d69df6e7b3a2)

doors: Allow setting an empty list of login broker tags

[41fde87693](https://github.com/dcache/dcache/commit/41fde876938a3c3d1511a287e11d647208d11498)

common: update ColumnWriter to remove any trailing whitespace

[245cc0bd08](https://github.com/dcache/dcache/commit/245cc0bd0807151e57a7b2156601b36895dae06b)

srmclient: add additional help text to srmfs

[9d55e4d562](https://github.com/dcache/dcache/commit/9d55e4d562f4b695f7465e8aef9da1e5be67c85a)

spacemanger: Fix interception of PoolAcceptFileMessage

[5484c3f7dd](https://github.com/dcache/dcache/commit/5484c3f7dd54d797f9e67d07b87231f9c8db2a2c)

xrootd: Upgrade to xrootd4j 3.2.1

[e576407c42](https://github.com/dcache/dcache/commit/e576407c4251b0b546e0180060a7d73b732211b5)

admin: Send requests to a fully qualified address once connected to a cell

[e8e729efaa](https://github.com/dcache/dcache/commit/e8e729efaa1d196ec1f3a09333a2305076c36cbc)

dcache: Do not hide NoRouteToCellException behind a timeout

[9204dc39fe](https://github.com/dcache/dcache/commit/9204dc39fe2bdf64308b47db36cc43094cb6876c)

webdav: Fix initialization of html template


