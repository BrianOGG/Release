# Cloud Agent Releases

Public release repository for Cloud Agent Linux Web packages, macOS Desktop installers, and Electron updater metadata. Product source remains in the private `BrianOGG/cloud-agent` repository. Build and release workflows run from this repository and check out the private source at `main`.

## Workflows

- `Cloud Agent Desktop source CI`: manually checks and compiles the private Desktop source on an Ubuntu runner; signed macOS packaging remains on the macOS OTA workflow.
- `Build Cloud Agent Desktop OTA`: manually builds and signs the private source, then dispatches its verified artifact to the macOS OTA publisher in this repository.
- `Build Cloud Agent Linux Web release asset`: manually builds the private source, then dispatches its verified artifact to the Linux publisher in this repository.
- The publisher workflows validate artifacts and public release assets. Linux publication also invokes `Validate published release`.

## Required Actions secrets

- `CLOUD_AGENT_SOURCE_READ_TOKEN`: fine-grained token restricted to `BrianOGG/cloud-agent`, with repository Contents read-only permission. The checkout disables persisted credentials.
- `CLOUD_AGENT_MACOS_CERTIFICATE_P12_BASE64` and `CLOUD_AGENT_MACOS_CERTIFICATE_PASSWORD`: required only for the signed macOS Desktop OTA workflow.

The build workflows are manual; publishing begins automatically only after a successful package build. Do not place source code, pairing material, API credentials, or MCP tokens in this public repository.
