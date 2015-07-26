# Change Log
All notable changes to this project will be documented in this file.
This project adheres to [Semantic Versioning](http://semver.org/).

## [Unreleased][unreleased]
### Added
- Enumaration for access specification.
- Message for class parents (**CxxRecordParent**).
- Field **access** to message **CxxFunctionDef**.
- Field **access** to message **Field**.

### Changed
- Field **parent** (in **CxxRecord**) to new parent message (**CxxRecordParent**).
- Option **java_package** in all files to "nl.rug.search.cpptool.proto".
- Message **ClassFunctionDef** to **CxxFunctionDef**.
- Message **ClassVar** to **Field**.

## 0.1.0 - 2015-07-24
### Added
- Project info files (README, LICENSE, CHANGELOG)
- Protobuf files containing the messages exported by cpptool.

[unreleased]: https://github.com/search-rug/cpptool-proto/compare/v0.1.0...HEAD