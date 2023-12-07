# Phonexia gRPC application interface

## 1.0.2 (2023-12-07)
### Added 
- Added `pyproject.toml` file for `poetry` package manager
- Building and publishing package to PyPI
- Added `pypi-README.md` file for PyPI

## 1.0.0 (2023-12-06)
### Added
- Common interface for microservices in `src/phonexia/grpc/common/core.proto`
- Interface for `licensing` in `src/phonexia/grpc/common/licensing.proto`
- Interface for `health_check` in `src/phonexia/grpc/common/health_check.proto`
- Interface for `voiceprint extraction` and `comparison` in `src/phonexia/grpc/technologies/speaker_identification/speaker_identification.proto`