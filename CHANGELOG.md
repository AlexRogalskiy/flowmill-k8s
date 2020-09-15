## [0.8.3190] - 2020-09-15
### Changed
    - Improve error handling on disconnects
    - Improve safeguards to prevent resource leakage
    - Agents now collect number of cpu cores

## [0.8.3033] - 2020-08-24
### Changed
    - Fix cpu hard limits collection
    - Added collection of TCP reset data
    - Other improvements to tcp data collection
    - Improvements to container metadata collection

## [0.8.3031] - 2020-08-21
### Changed
    - Helm chart update, deprecate extensions/v1beta1

## [0.8.2859] - 2020-07-28
### Changed
    - CPU/Mem/IO now collects the hard/soft cpu limits from the kernel

## [0.8.2824] - 2020-07-24
### Changed
    - CPU/Mem/IO now collects podname for processes running in k8s
    - Agent collects k8s metadata from the docker engine
    - Enable container metadata on k8s by default

## [0.8.2716] - 2020-07-06
### Changed
    - Increase max DNS packet size to 512 bytes
    - Fix issue with CPU/mem/io enrichment

## [0.8.2617] - 2020-06-23
### Changed
    - Minor enhancements to cpu/mem/io metric collection

## [0.8.2576] - 2020-06-17
### Changed
    - Improve cpu/mem/io metric enrichment

## [0.8.2533] - 2020-06-10
### Changed
    - Minor enhancements

## [0.8.2474] - 2020-06-04
### Changed
    - Fix issue downloading kernel headers on CentOS7

## [0.8.2441] - 2020-06-02
### Changed
    - Fix `yumdownloader` kernel headers issue
    - Fix CPU/mem/io sample irregularity

## [0.8.2397] - 2020-05-27
### Changed
    - Improvements to CPU/Mem/IO collection
    - Improvements to nomad metadata collection
    - Minor stability enhancements

## [0.8.2278] - 2020-05-12
### Changed
    - Implemented CPU/Mem/IO collection
    - Add nomad metadata collection (disabled by default)
    - Add ability to print bpf logs to a file
    - Fix for heartbeat connection

## [0.8.2167] - 2020-05-05
### Changed
    - Minor enhancements
    - eBPF stylistic fixups

## [0.8.2082] - 2020-04-27
### Changed
    - Multiple enhancements and data quality fixes
    - Improve authentication retry logic

## [0.8.1989] - 2020-04-13
### Changed
    - Better authentication handling for aws collector
    - Support for recent >5.0.0 kernels
    - Fixes for data quality issues

## [0.8.1778] - 2020-03-24
### Changed
    - Multiple enhancements and data quality fixes

## [0.8.1743] - 2020-03-17
### Changed
    - Set imagePullPolicy to Always, so restarts pull the latest image with the configured image tag

## [0.8.1741] - 2020-03-17
    - Release helm charts with `latest-v0.8` tag

## [0.8.1676] - 2020-03-10
### Changed
    - Report process end closer to process exit

## [0.8.1650] - 2020-03-09
### Changed
    - Better health reporting for Flowmill collectors
    - Multiple enhancements and data quality fixes

## [0.8.1540] - 2020-02-25
### Changed
    - Fix for kernel headers auto-fetching on GCP Container Optimized OS
    - Multiple enhancements and data quality fixes

## [0.8.1376] - 2020-02-03
### Changed
    - Flowmill agents automatically fetch and cache kernel headers for supported distros, if headers are not already pre-installed on the node.
    - Improve error handling in agent authentication process
    - Multiple enhancements and data quality fixes

## [0.8.1260] - 2020-01-17
### Changed
    - Improve error handling in agent authentication process

## [0.8.1067] - 2019-12-16
### Changed
    - Multiple enhancements and data quality fixes

## [0.8.897] - 2019-11-22
### Changed
    - New Agent version with multiple enhancements
    - Intake and Services now hosted on flowmill.com
    - Reduced number of required fields in chart
    - Automatically create or reuse agent key secret

## [0.2.9] - 2019-07-24
### Changed
    - New Agent version with multiple enhancements

## [0.2.8] - 2019-06-04
### Changed
    - Use a projected mount for config files; potential workaround for kubernetes/kubernetes#68211
    - New k8s-relay version (adjusted Dockerfile entrypoint, no significant code changes)

## [0.2.7] - 2019-04-16
### Changed
    - More ECS improvements

## [0.2.6] - 2019-04-10
### Added
    - Support for "ownerless" pods in k8s
### Changed
    - Improved NAT tracking

## [0.2.5] - 2019-04-02
### Changed
    - Increased in-flight limit on k8s-collector for larger environments

## [0.2.4] - 2019-04-02
### Changed
    - Override default k8s-relay heartbeat; set to 10 seconds

## [0.2.3] - 2019-04-01
### Added
    - [agent] Better k8s networking support
### Fixed
    - [relay] Retry connections on DNS error
    - [agent] Fixed rare crash at startup
