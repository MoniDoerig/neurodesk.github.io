---
title: "Neurodesk App"
linkTitle: "Neurodesk App"
weight: 1
aliases:
- /getting-started/local/neurodeskapp/
- /getting-started/local/neurodeskapp
- /getting-started/neurodesktop/portable/
- /getting-started/neurodesktop/portable
- /docs/getting-started/neurodesktop/neurodeskapp/
- /docs/getting-started/neurodesktop/portable/
- /docs/getting-started/neurodesktop/portable
- /docs/getting-started/local/neurodeskapp/
- /docs/getting-started/local/neurodeskapp
- /docs/Getting-Started/Local/neurodeskapp
description: >
  A cross-platform desktop application for Neurodesk: The easiest way to use Neurodesktop
---

## Step 1: Download and install

Download the Neurodesk App for your operating system, then follow the install instructions below.

{{< tabpane text=true >}}
{{% tab header="macOS" %}}

**Download:**
- [macOS Apple Silicon (M1/M2/M3/M4)](https://github.com/neurodesk/neurodesk-app/releases/latest/download/NeurodeskApp-Setup-macOS-arm64.dmg)
- [macOS Intel](https://github.com/neurodesk/neurodesk-app/releases/latest/download/NeurodeskApp-Setup-macOS-x64.dmg)

**Install:**
Double-click the downloaded `.dmg` file and drag NeurodeskApp into your Applications folder. To open: right-click `NeurodeskApp.app` and select "Open".

Alternatively, install with Homebrew:
```bash
brew install neurodesk/homebrew-neurodesk/neurodeskapp
```

{{% /tab %}}
{{% tab header="Windows" %}}

**Download:**
- [Windows Installer](https://github.com/neurodesk/neurodesk-app/releases/latest/download/NeurodeskApp-Setup-Windows.exe)

{{% alert color="info" %}}
**On Microsoft Edge**, follow these steps to download the executable file:

<img src="{{< relurl "/static/docs/getting-started/neurodeskapp/neurodeskapp-edge-download.png" >}}" style="max-width: 800px; width: 100%;" alt="Microsoft Edge download steps">
{{% /alert %}}

**Install:**
Double-click the downloaded `.exe` file. Accept to install from an unknown publisher with "Yes", then accept the license agreement and click "Finish".

{{% /tab %}}
{{% tab header="Linux" %}}

**Download:**

| Distribution | x64 | arm64 |
|---|---|---|
| Debian / Ubuntu | [.deb (x64)](https://github.com/neurodesk/neurodesk-app/releases/latest/download/NeurodeskApp-Setup-Debian-x64.deb) | [.deb (arm64)](https://github.com/neurodesk/neurodesk-app/releases/download/v1.8.0/NeurodeskApp-Setup-Debian-arm64.deb) |
| Fedora / RHEL / SUSE | [.rpm (x64)](https://github.com/neurodesk/neurodesk-app/releases/latest/download/NeurodeskApp-Setup-Fedora-x64.rpm) | [.rpm (arm64)](https://github.com/neurodesk/neurodesk-app/releases/latest/download/NeurodeskApp-Setup-Fedora-arm64.rpm) |
| Arch-based | [AUR package](https://aur.archlinux.org/packages/neurodeskapp-bin) | |

**Install:**
```bash
# Debian / Ubuntu
sudo apt install -f ./NeurodeskApp-Setup-Debian.deb

# Fedora / RHEL / SUSE
sudo rpm -i NeurodeskApp-Setup-Fedora.rpm

# Arch-based
yay neurodesk
```

{{% /tab %}}
{{< /tabpane >}}

{{% alert color="info" %}}
**Already have [GitHub Store](https://komistore.app/) installed?**

Search for `Neurodesk-app` to install directly -- works on all operating systems.

<img src="{{< relurl "/static/docs/getting-started/neurodeskapp/github-store.png" >}}" style="max-width: 400px; width: 100%;" alt="Neurodesk App in GitHub Store">
{{% /alert %}}

### Minimum system requirements

- At least 8 GB free disk space for the Neurodesktop base image
- A container engine (see Step 2 below)

## Step 2: Set up a container engine

The Neurodesk App needs a container engine to run neuroimaging tools. Which engine you use depends on whether you have admin (root) privileges on your system.

<img src="{{< relurl "/static/docs/getting-started/neurodeskapp/engine-options.png" >}}" width="400" style="filter: drop-shadow(5px 5px 10px rgba(0,0,0,0.5));" alt="Engine selection screen showing Docker, Podman, and TinyRange options"></br>

{{< tabpane text=true >}}
{{% tab header="Docker (recommended)" %}}

**Requires:** Admin/root access on your machine.

If you already have Docker installed, skip to [Step 3](#step-3-launch-the-app). Otherwise, install Docker:

- [Docker Desktop for Windows](https://docs.docker.com/docker-for-windows/install/)
- [Docker Desktop for Mac](https://docs.docker.com/docker-for-mac/install/)
- [Docker Engine for Linux](https://docs.docker.com/engine/install/)

Verify your installation:
```bash
docker --version
docker run hello-world
```

**Apple Silicon users:** Enable Rosetta support in Docker Desktop settings for best performance.

{{% /tab %}}
{{% tab header="Podman" %}}

**Requires:** Admin/root access on your machine.

Podman is a drop-in replacement for Docker. Install it using your system's package manager or from [podman.io](https://podman.io/docs/installation).

{{% /tab %}}
{{% tab header="TinyRange (no admin needed)" %}}

**Use this if you do NOT have admin/root access.**

TinyRange is included with the Neurodesk App -- no separate install is needed on Windows and Linux.

**macOS only:** You also need to install QEMU:
```bash
brew install qemu
```

Verify with:
```bash
qemu-system-aarch64 --version
```

{{% /tab %}}
{{< /tabpane >}}

## Step 3: Launch the app


Open the Neurodesk App from your operating system's application menu, or run `neurodeskapp` from the command line.

On the Welcome Page you have two options:

- **Open Local Neurodesk** -- starts a Neurodesk session on your machine.
- **Connect to remote Neurodesk server** -- connects to an existing Neurodesk server running elsewhere.

<img src="{{< relurl "/static/docs/getting-started/neurodeskapp/neurodesk-desktop.png" >}}" style="filter: drop-shadow(5px 5px 10px rgba(0,0,0,0.5)); max-width: 600px; width: 100%;" alt="Start session">

### Local sessions

Click "Open Local Neurodesk" to launch a local session. This opens a JupyterLab interface with two ways to use Neurodesk:

- Click the **NeurodeskApp** icon to launch the full desktop interface in a new window.
- Use the **command line** in JupyterLab and load tools via the module system in the left sidebar.

<img src="{{< relurl "/static/docs/getting-started/neurodeskapp/connect-to-local.png" >}}" style="filter: drop-shadow(5px 5px 10px rgba(0,0,0,0.4)); max-width: 400px; width: 50%;" alt="Connect to local">

### Remote sessions

Click "Connect to remote Neurodesk server" to connect to a server running elsewhere.

Enter the URL of the server. If authentication is required, include the token as a query parameter: `/lab?token=<token-value>`. Press Enter to connect.

<img src="{{< relurl "/static/docs/getting-started/neurodeskapp/connect-to-server.png" >}}" style="max-width: 600px; width: 100%;" alt="Connect to server">

<!-- Check "Persist session data" to save the connection for next time. You can clear saved sessions in Settings > Privacy > Clear History. -->

## Data storage

Neurodesk stores data in the following default locations:

| Location | Path |
|---|---|
| Inside the app | `/home/jovyan/neurodesktop-storage` |
| On your machine (macOS/Linux) | `~/neurodesktop-storage` |
| On your machine (Windows) | `C:/neurodesktop-storage` |

User can set `neurodesktop-storage` to be in different location if need to.

### Adding a custom data directory

In Settings, select "Additional Directory" in the sidebar, click "Change" to choose a local directory, then click "Apply & restart". The directory will appear at `/home/jovyan/data` inside the app.

<img src="{{< relurl "/static/docs/getting-started/neurodeskapp/additional_dir.png" >}}" style="max-width: 600px; width: 100%;" alt="Additional Directory settings interface">

{{% alert color="info" %}}
**Windows:** Mounting external hard drives is not currently supported. Copy data to your local disk first.
{{% /alert %}}

{{% alert color="info" %}}
**macOS with Podman:** To mount an external drive, run these commands once:
```bash
podman machine reset -f
podman machine init --rootful --now -v /Volumes:/Volumes -v $HOME:$HOME podman-machine-default
```
Then set the path in the Neurodesk App settings.
{{% /alert %}}

{{% alert color="info" %}}
If you use conda environments to install packages or kernels, see the [conda tutorial](https://neurodesk.org/edu/tutorials/programming/conda.html).
{{% /alert %}}
