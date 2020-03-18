## [0.8.1740] - 2020-03-17
### Changed
    - Release helm charts to use tag `latest-v0.8` by default

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
