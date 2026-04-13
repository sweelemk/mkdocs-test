# Installation

Follow these steps to install and verify your local development environment.

## Prerequisites

- **Python** 3.9 or later
- **Node.js** 18 or later (for the web dashboard)
- **Docker** 24 or later (optional, for local service emulation)

## Install the CLI

=== "macOS / Linux"

    ```bash
    curl -sSL https://install.example.com | sh
    ```

    Or via Homebrew:

    ```bash
    brew tap example/product
    brew install product
    ```

=== "Windows"

    Download the installer from the [releases page](https://example.com/releases) or use `winget`:

    ```powershell
    winget install Example.Product
    ```

=== "Docker"

    ```bash
    docker pull example/product-cli:latest
    docker run --rm example/product-cli:latest product --version
    ```

Verify the installation:

```bash
product --version
# product v2.0.1 (darwin/arm64)
```

## Install the Python SDK

```bash
pip install product-sdk
```

For development extras (testing utilities, type stubs):

```bash
pip install "product-sdk[dev]"
```

## Authenticate

```bash
product auth login
```

This opens a browser window where you complete the OAuth flow. Your token is stored in `~/.product/credentials`.

To authenticate non-interactively (CI environments):

```bash
export PRODUCT_TOKEN=your_token_here
product auth verify
```

## Initialize a Project

```bash
mkdir my-project && cd my-project
product init
```

You'll be prompted to choose a workspace and project name. This creates a `product.yml` in the current directory.

!!! success "You're ready"
    At this point you have a working installation. Head to the [Features](../features/index.md) section to start exploring what Product can do.

## Building the Documentation as PDF

This documentation site is configured with the `mkdocs-with-pdf` plugin. After cloning the docs repo:

```bash
# Activate the virtual environment
source venv/bin/activate

# Build — PDF is generated at site/pdf/document.pdf
mkdocs build

# Or serve locally (PDF is NOT generated in serve mode)
mkdocs serve
```

The generated PDF will be at `site/pdf/document.pdf`.
