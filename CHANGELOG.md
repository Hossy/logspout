# Change Log
All notable changes to this project will be documented in this file.

## [Unreleased][unreleased]
### Fixed

### Added
- Added threshold debug logging for send() blocking on pushing a message to a route.  Threshold configurable via LOGSTREAM_THRESHOLD_MS environment variable.
- Added timeout to pushing a message to a route.  Timeout configurable via LOGSTREAM_SEND_TIMEOUT_MS environment variable.

### Removed

### Changed

## [v3.2.14] - 2021-12-03
### Fixed
- @0xflotus fix: typo error in project name

### Changed
- @skyzh upgrade dockerclient dependency
- @merowing1279 retrieve logs from already started containers
- @odidev Release docker image for arm64

## [v3.2.13] - 2020-11-26
### Changed
- @michaelshobbs bump golangci-lint to 1.27 and fix lintballs

### Fixed
- @michaelshobbs fix backlog() logic and add tests

## [v3.2.12] - 2020-10-22
### Changed
- @michaelshobbs bump alpine to 3.12

## [v3.2.11] - 2020-05-08
### Added
- @hhromic Add Syslog TCP framing documentation to README

### Changed
- @hhromic syslog adapter refactor
- @michaelshobbs use type assertion instead of reflection to determine connection type
- @michaelshobbs use // + space for all human readable comments

## [v3.2.10] - 2020-05-01
### Added
- @jszwedko Add optional TCP framing to syslog adapter

### Fixed
- @bbigras add missing syntax highlighting in README.md

## [v3.2.9] - 2020-04-30
### Fixed
- @bbigras add missing syntax highlighting in README.md

### Added
- @edorgeville Adds `db` log driver to `logDriverSupported`
- @renehernandez Add support for multiple exclusion labels
- @renehernandez Add support for EXCLUDE_LABELS envvar with fallback to existing EXCLUDE_LABEL
- @hhromic adapters/syslog: add ContainerNameSplitN utility message function

### Changed
- @hhromic adapters/syslog: enforce RFC size limits in message fields

## [v3.2.8] - 2020-04-03
### Changed
- @michaelshobbs bump alpine to 3.11 and go to 1.13.4-r1

## [v3.2.7] - 2020-04-03
### Fixed
- @CodeLingoBot @gbolo Fix function comments based on best practices from Effective Go

### Changed
- @michaelshobbs update alpine to 3.10/go 1.12.12-r0 and fix linting
- @whoisteri DOC Document accessible data in RAW_FORMAT template
- @tiagorlampert DOC typos
- @michaelshobbs DOC CHANGLELOG formatting
- @tomlankhorst DOC Suggest to disable userns-remap for logspout
- @StudioEtrange DOC add link to logspout-fluentd

## [v3.2.6] - 2018-10-04
### Fixed
- @jdgiotta Spelling corrections and fixed stack compose formatting in example
- @dylanmei dylanmei Update 3rd party module link in README

### Added
- @vbeausoleil added a simple healthcheck
- @gbolo added option to load TLS client certificate and key
- @gbolo added ability to control the TLS client trust store
- @gbolo added option to harden the TLS client
- @chopmann added option to bind the http server to an address
- @ibrokethecloud added ability to add custom key:value pairs as EXCLUDE_LABEL

### Changed
- @develar alpine 3.8 + golang 1.10.1
- @gbolo enforced the use of `go 1.8+` in order to accommodate some TLS settings

## [v3.2.5] - 2018-06-05
### Fixed
- @michaelshobbs fix working_directory so we don't duplicate test runs
- @gmelika panic if reconnect fails
- @masterada Added multiline adapter
- @billimek sleeping and syncing to fix issues with docker hub builds

### Added
- @chris7444 take the hostname from /etc/host_hostname if the file is there
- @chris7444 update README.md for swarm deployments PR #329
- @nvanheuverzwijn strip \r and \n when reading the file /etc/host_hostname
- @lucassabreu toJSON with examples

### Changed
- @michaelshobbs pass debug to test container
- @jgreat Strip header bytes from log stream
- @trondvh chmod +x build.sh
- @develar alpine 3.7 + golang 1.9.2

## [v3.2.3] - 2017-09-23
### Added
- @guigouz guigouz Add `RAW_FORMAT` to the documentation
- @stevecalvert Allow docker log tail to be specified, default to 'all

### Fixed
- @jeanlouisboudart RawTerminal should be set to true if we want to collect tty logs
- @michaelshobbs fix new golint lintballs

## [v3.2.2] - 2017-05-25
### Fixed
- @michaelshobbs router: fix empty routes response. fixes #299
- @Crashthatch Close existing routes when adding a new route with an existing ID. fixes #305

### Changed
- @mattaitchison router/pump: remove logstream send timeout

## [v3.2.1] - 2017-04-13
### Fixed
- @michaelshobbs build: fix missing ca-certificates. closes #294

### Added
- @michaelshobbs build: add tls test case

### Changed
- @michaelshobbs use circleci 2.0

## [v3.2] - 2017-04-13
### Fixed
- @ekkinox FIX: add build-base package install to fix missing gcc
- @bobzoller reconnect log stream unless container is dead
- @mattaitchison Fix locking around custom route loading
- @bobzoller avoid duplicate pumps with mutex lock
- @markine Use InactivityTimeout to work around a bug in docker (#204)
- @mattaitchison install ca-certificates fixes #247
- @mattaitchison Dockerfile: use alpine 3.5 to fix build issue from missing context pkg

### Added
- @micahhausler Add Graylog GELF module
- @Selim Ekizoglu  Exclude containers by label.
- @treeder Some help for working on custom modules
- @davidnortonjr Add more configuration examples to README
- @davidnortonjr Filter by label (#236)
- @mattaitchison first pass at tests (#218)
- @grosskur syslog: Add support for SYSLOG_TIMESTAMP (#260)
- @michaelshobbs add linting with go vet and golint
- @andrewgaul Allow configuration of retry count via environment
- @davidnortonjr Allow containers with TTY enabled using environment variable ALLOW_TTY
- @michaelshobbs add golint in ci and filter /vendor/ from linting
- @ebr add env.var switch to turn off backlogs
- @michaelshobbs add test for max image size

### Changed
- @selimekizoglu Ignore empty EXCLUDE_LABEL values
- @pmbauer ignore containers with unsupported log drivers
- @robertjustjones Updated README to include tls
- @jmreicha custom: Update README and include example build script
- @josegonzalez Add a note about build.sh needing to be in the docker build directory
- @treeder Much, much faster builds
- @michaelshobbs set common test name prefix for -run ease
- @michaelshobbs make ignoreContainerTTY more testable and add test
- @michaelshobbs make retryCount testable and add test
- @michaelshobbs use glide in dockerfile
- @michaelshobbs use alpine + build script and add test for custom image building
- @michaelshobbs attempt to preserve buffer on reconnect()
- @michaelshobbs race detector for alpine is broken. disable it for now
- @michaelshobbs make vet more reliable
- @luketurner Don't retry sending on ECONNRESET

## [v3.1] - 2016-05-23
### Fixed
- Panic when renaming stopped container #183
- won't start without route configuration #185
- RouteManager.Name() didn't return name
### Added
- update container name if we get a rename event. closes #144 (#180)

### Removed

### Changed
- Now using Alpine Linux 3.3 and GO 1.5.3, removed the "edge" package repo for building the official Docker image (#174)
- Fix exposed ports in Dockerfile and readme. Remove references to /tmp/docker.sock from readme

## [v3] - 2016-03-03
### Fixed
- use start/die like old version not create/destroy
- performance fix, generalizing SyslogMessage, minor cleanups
- Initialize Route options map
- Fixed a couple of typos, updated narrative
- UDP message delivery should not kill the program
- Exit with return code 1 on job setup failure
- Simplify and add early exit to RoutingFrom
- Unmarshal without buffering
- Remove unnecessary closure
- Undo change introduced in 07555c5
- Fix port number in httpstream example
- Use correct nilvalue for structured data as per rfc 5424
- retry tcp errors and don't hang forever on failure

### Added
- mention irc channel
- allowing easy custom builds of logspout
- Allow env vars in stream URLs
- Allow you to ignore log messages from individual containers by setting container environment variable, LOGSPOUT=ignore, when starting
- Add URL for Logstash module
- Adding CircleCI, Docker and IRC badges to readme.
- Add TLS transport. Fixes #116

### Removed
- Removed attach on restart event
- remove dev containers
- Removed deprecated library hosted in google code in favor of its new home

### Changed
- switched to gliderlabs org
- assume build
- rough pass at breaking logspout.go into separate packages
- fully split up packages. major refactoring of router
- simpler matching. working routesapi. dropped old utils
- make sure all uri params get into route options
- readme updates and module specific readmes
- renamed ConnectionFactory to AdapterTransport
- updated readme to use current schema
- names and parama
- more readable
- hold handler from returning until streamer finishes
- primarily designed new boot output, but came with it architectural changes
- updating docker sock location
- support old location for docker socket
- force link in case its run again, such as with custom builds
- analytics test
- update analytics
- Update README.md
- Update README with tls module
- Wrong port in README.md #136


## [v2] - 2015-02-12
### Added
- Allow comma-separated routes on boot
- Added project versioning
- Development Dockerfile and make task
- Deis sponsorship / support

### Removed
- Staging binary. Built entirely in Docker.
- Dropped unnecessary layers in Dockerfile

### Changed
- Base container is now Alpine
- Moved to gliderlabs organization

[unreleased]: https://github.com/gliderlabs/logspout/compare/v3.2.14...Hossy:logspout:master
[v3.2.14]: https://github.com/gliderlabs/logspout/compare/v3.2.13...v3.2.14
[v3.2.13]: https://github.com/gliderlabs/logspout/compare/v3.2.12...v3.2.13
[v3.2.12]: https://github.com/gliderlabs/logspout/compare/v3.2.11...v3.2.12
[v3.2.11]: https://github.com/gliderlabs/logspout/compare/v3.2.10...v3.2.11
[v3.2.10]: https://github.com/gliderlabs/logspout/compare/v3.2.9...v3.2.10
[v3.2.9]: https://github.com/gliderlabs/logspout/compare/v3.2.8...v3.2.9
[v3.2.8]: https://github.com/gliderlabs/logspout/compare/v3.2.7...v3.2.8
[v3.2.7]: https://github.com/gliderlabs/logspout/compare/v3.2.6...v3.2.7
[v3.2.6]: https://github.com/gliderlabs/logspout/compare/v3.2.5...v3.2.6
[v3.2.5]: https://github.com/gliderlabs/logspout/compare/v3.2.4...v3.2.5
[v3.2.4]: https://github.com/gliderlabs/logspout/compare/v3.2.3...v3.2.4
[v3.2.3]: https://github.com/gliderlabs/logspout/compare/v3.2.2...v3.2.3
[v3.2.2]: https://github.com/gliderlabs/logspout/compare/v3.2.1...v3.2.2
[v3.2.1]: https://github.com/gliderlabs/logspout/compare/v3.2...v3.2.1
[v3.2]: https://github.com/gliderlabs/logspout/compare/v3.1...v3.2
[v3.1]: https://github.com/gliderlabs/logspout/compare/v3...v3.1
[v3]: https://github.com/gliderlabs/logspout/compare/v2...v3
[v2]: https://github.com/gliderlabs/logspout/compare/v1...v2
