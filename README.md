# Cloud Agent Releases

Public release-only repository for Cloud Agent Linux Web packages, desktop installers, and Electron updater metadata. The source code remains in the private `BrianOGG/cloud-agent` repository. This repository contains no source checkout, pairing material, credentials, or MCP tokens.

## Linux Web publishing

The private Cloud Agent repository builds the Linux ARM64 package in GitHub Actions. After a successful build, a short-lived signed download URL and the authenticated artifact digest are sent to the `cloud-agent-linux-web-release` repository-dispatch event. The publishing workflow verifies the artifact digest, package checksum, manifest, and required archive files; it creates a draft release, runs `Validate published release`, and publishes the prerelease only after validation succeeds. The signed URL must not be printed in workflow logs.
