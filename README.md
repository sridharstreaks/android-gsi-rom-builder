# android-gsi-rom-builder

Custom Android ROM builder tool for processing and flashing GSI (Generic System Images) images.

This repository is a starter toolkit for building a Treble-aware Android GSI patching and packaging workflow. It provides a modular Python-based pipeline, a sample CI workflow, and documentation for non-technical users.

WARNING: This project can modify system images and device partitions. Always back up `/boot`, `/vendor`, and `/data` before flashing. Use at your own risk.

## Features

- JSON/YAML profile ingestion for device diagnostics
- Modular builder pipeline under `src/builder/`
- Vendor patch overlay support under `patches/`
- GitHub Actions workflow for automated builds
- Basic usage and flashing instructions

## Quick start

1. Install dependencies:
   `bash scripts/install_tools.sh`
2. Prepare a profile file, for example:
   `sample_profile.json`
3. Download a base GSI image.
4. Run the builder:
   `python3 -m src.builder.main --profile sample_profile.json --system gsi/system.img --workdir work --output out`

## Project structure

- `src/builder/` - Python patching engine
- `patches/` - vendor-specific overlays and patch scripts
- `scripts/` - setup and environment automation
- `docs/` - user-facing guides
- `.github/workflows/` - CI/CD automation

## Safety notes

- Do not flash a GSI on a device without a backup.
- Verify the partition layout matches your device.
- Disable AVB only when required and only in the intended target image.
- Use the correct architecture and Treble metadata for your device.
