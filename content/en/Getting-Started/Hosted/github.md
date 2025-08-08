---
title: "Github Codespaces"
linkTitle: "Github"
weight: 1
alias: 
- /docs/getting-started/hosted/github
description: >
  Use Neurodesk on GitHub Codespaces
---


Start a GitHub Codespace in the repository of your choice:
</br>
<img src="/static/docs/getting-started/hosted/github_codespace.png" alt="Start GitHub Codespace" width="500">

Then start the neurodesktop container in a terminal:
```bash
docker volume create neurodesk-home &&
sudo docker run \
  --shm-size=1gb -it --security-opt apparmor=neurodeskapp --privileged --user=root --name neurodesktop \
  -v ~/neurodesktop-storage:/neurodesktop-storage \
  --mount source=neurodesk-home,target=/home/jovyan \
  -e NB_UID="$(id -u)" -e NB_GID="$(id -g)" \
  -p 8888:8888 \
  -e NEURODESKTOP_VERSION={{< params/neurodesktop/jupyter_neurodesk_version >}} ghcr.io/neurodesk/neurodesktop/neurodesktop:{{< params/neurodesktop/jupyter_neurodesk_version >}}
```

Then open Neurodesktop in the browser by clicking the "Open in Browser" Button displayed
</br>
<img src="/static/docs/getting-started/hosted/github_codespace_open.png" alt="Pop up on GitHub Codespace" width="400">

The token for authentication is displayed in the terminal:
![alt text](/static/docs/getting-started/hosted/ghc_terminal.png)
