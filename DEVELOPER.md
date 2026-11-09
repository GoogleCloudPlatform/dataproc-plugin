# DEVELOPER.md

This document provides instructions for setting up your development environment
and contributing to the Dataproc Agent skills project.

## Prerequisites

Before you begin, ensure you have the following:

1.  **Gemini CLI:** Install the Gemini CLI version v0.6.0 or above.
2.  **Dataproc Resources:** Access to active Dataproc clusters and jobs for testing.

## Developing the Extension

### Running from Local Source

This extension uses **Agent Skills** to interact with Firestore. The development process involves generating these skills locally and linking the extension to the Gemini CLI.

1.  **Clone the Repository:**

    ```bash
    git clone https://github.com/GoogleCloudPlatform/dataproc-plugin.git
    cd dataproc-plugin
    ```

2.  **Install the Extension Locally:** Use the Gemini CLI to install the
    extension from your local directory.


    ```bash
    gemini extensions install .
    ```
    The CLI will prompt you to confirm the installation. Accept it to proceed.


3.  **Testing Changes:** After installation, start the Gemini CLI (`gemini`).
    You can now interact with the `dataproc` skills to manually test your changes.

## Testing

### Automated Presubmit Checks

A GitHub Actions workflow (`.github/workflows/presubmit-tests.yml`) is triggered
for every pull request. This workflow primarily verifies that the extension can
be successfully installed by the Gemini CLI.

All tools are currently tested in the [MCP Toolbox GitHub](https://github.com/googleapis/mcp-toolbox).

The skills themselves are validated using the `skills-validate.yml` workflow.

### Other GitHub Checks

*   **License Header Check:** A workflow ensures all necessary files contain the
    proper license header.
*   **Conventional Commits:** This repository uses
    [Release Please](https://github.com/googleapis/release-please) to manage
    releases. Your commit messages must adhere to the
    [Conventional Commits](https://www.conventionalcommits.org/) specification.

## Maintainer Information

### Team

The primary maintainers for this repository are defined in the [`.github/CODEOWNERS`](.github/CODEOWNERS) file:

*   `@GoogleCloudPlatform/senseai-eco`
*   `@GoogleCloudPlatform/dataproc-plugin-maintainers`

### Releasing

The release process is automated using `release-please`. It consists of the manual merging of a Release PR. When the Release PR is merged, `release-please` creates a new GitHub tag and a corresponding GitHub Release.

#### Release Process

1.  **Release PR:** When commits with conventional commit headers (e.g., `feat:`,
    `fix:`) are merged into the `main` branch, `release-please` will
    automatically create or update a "Release PR".
2.  **Merge Release PR:** A maintainer approves and merges the Release PR. This
    action triggers `release-please` to create a new GitHub tag and a
    corresponding GitHub Release.
