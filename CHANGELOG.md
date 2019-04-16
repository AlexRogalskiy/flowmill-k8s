
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
