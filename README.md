<!-- SPDX-License-Identifier: MPL-2.0 -->
<!-- Copyright © 2026 Cristian Camargo Filho -->

![Harness Lens](assets/harness-lens-banner.png)

# Harness Lens Scoop Bucket

The official [Scoop](https://scoop.sh/) bucket for [Harness Lens](https://github.com/harness-lens/cli), a local-first CLI that produces evidence-backed reports about coding-agent harnesses.

This bucket contains Scoop manifests. It does not host compiled binaries. Scoop downloads each release from the Harness Lens GitHub release and verifies the pinned SHA-256 checksum before installation.

## Install

Install Scoop first, then add this bucket:

```powershell
scoop bucket add harness-lens https://github.com/harness-lens/scoop-bucket.git
scoop install harness-lens/harness-lens
```

Verify the installed command:

```powershell
harness-lens --version
harness-lens scan . --json
```

The current manifest publishes the 64-bit Windows build. The executable is named `harness-lens.exe` and is exposed through Scoop's normal shim directory.

## Update and remove

Update Scoop and Harness Lens with:

```powershell
scoop update
scoop update harness-lens/harness-lens
```

Remove the application, or remove the bucket as well, with:

```powershell
scoop uninstall harness-lens
scoop bucket rm harness-lens
```

Removing the bucket does not remove an already-installed application. Uninstall the application separately when it is no longer needed.

## VS Code extension

The Scoop CLI and the Harness Lens VS Code extension can be installed together. They use separate entry points:

- Scoop provides `harness-lens.exe` for terminal scans.
- The VS Code extension starts the separate `harness-lens-lsp` language server.

The extension is published from the [`harness-lens-vscode`](https://github.com/harness-lens/harness-lens-vscode) repository. This bucket does not replace or modify the extension.

## Releases and verification

Each manifest update must point to a versioned, immutable GitHub release URL and include its exact SHA-256 checksum. Do not use a mutable `latest` URL or replace a released checksum.

The application source, release notes, issue tracker, and platform support details are maintained in the [CLI repository](https://github.com/harness-lens/cli). Review the [distribution documentation](https://github.com/harness-lens/cli/blob/main/docs/distribution.md) before relying on a new release.

## Contributing

Open a pull request for manifest changes. A proposed update should include:

1. A reviewed Harness Lens release version.
2. A version-specific Windows x64 archive URL.
3. The matching SHA-256 checksum from the release checksum file.
4. A clean install, version, scan, update, and uninstall test on Windows.
5. No credentials, binaries, or generated secrets in this repository.

Keep manifest changes small and auditable. Changes to the CLI, release workflow, or binary belong in the [CLI repository](https://github.com/harness-lens/cli), not in this bucket.

## License

The bucket metadata is licensed under the [Mozilla Public License 2.0](LICENSE). The Harness Lens application is distributed under the license stated by its release metadata.
