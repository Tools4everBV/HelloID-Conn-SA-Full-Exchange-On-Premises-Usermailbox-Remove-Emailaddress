# Changelog

All notable changes to this project will be documented in this file. The format is based on [Keep a Changelog](https://keepachangelog.com/), and this project adheres to [Semantic Versioning](https://semver.org/).

## [2.0.0] - 2026-08-26

### Added

- Added TLS 1.2 support for secure connections
- Added comprehensive error handling with actionMessage context
- Added finally block for reliable session cleanup
- Added ExchangeGuid-based mailbox identification for improved reliability
- Added detailed property selection to optimize memory usage and performance
- Added wildcard filter support for multiple search fields (Name, SamAccountName, Alias, PrimarySmtpAddress)

### Changed

- Refactored form control from duallist to multiselectgrid for better user experience
- Updated datasource naming convention to include full descriptive names
- Improved session management with splatted parameters for better readability
- Simplified error handling by removing nested try-catch blocks
- Enhanced audit logging with consistent message formatting
- Changed session option parameters to use named hashtable splatting

### Fixed

- Fixed session cleanup to properly handle null session scenarios
- Corrected error variable handling in audit logs
- Improved error messages to include script line numbers and context

## [1.0.2] - 2022-08-24

### Added

- Added version number and updated code for SA-agent and auditlogging

## [1.0.1] - 2021-11-16

### Added

- Added version number and updated all-in-one script

## [1.0.0] - 2021-04-29

Initial release of HelloID-Conn-SA-Full-Exchange-On-Premises-Usermailbox-Remove-Emailaddress.

### Added

- Initial release for removing email addresses from Exchange On-Premises user mailboxes
