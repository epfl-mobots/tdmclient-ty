# Changelog

Notable changes of tdmclient-ty. Release versions refer to [https://pypi.org/project/tdmclient-ty/].

## [Unreleased]

### Added

- Warnings for local variables which hide global variables (a declaration as global could be missing)
- `NameError` exceptions, raised by the transpiler e.g. if the Aseba dot syntax is used instead of names with underscores, are displayed in the Shell panel
- In error messages, code numbers are replaced by messages when their meaning is known
- Shortcut Control-Shift-T for menu command Tools>Transpile Program
- Menu commands moved to a separate "Thymio" menu

### Fixed

- Robot disconnections and reconnections

## [0.1.2] - 2022-02-23

### Added

- Line number in error messages
- Error message in the Shell panel when the program cannot be executed on the robot

## [0.1.1] - 2021-11-04

### Added

- Transpiler errors displayed in shell panel
- Code examples in documentation

## [0.1.0] - 2021-10-20

### Added

- First release on PyPI
