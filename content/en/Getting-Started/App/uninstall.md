---
title: "Uninstalling"
linkTitle: "Uninstalling"
weight: 3
description: >
  How to uninstall the Neurodesk App
---

{{< tabpane text=true >}}
{{% tab header="macOS" %}}

Find `NeurodeskApp.app` in Finder (in `/Applications` or `~/Applications`) and move it to Trash (`CMD + Delete`). Then remove application data:

```bash
rm -rf ~/Library/neurodeskapp
rm -rf ~/Library/Application\ Support/neurodeskapp
```

{{% /tab %}}
{{% tab header="Windows" %}}

Go to **Start Menu > Settings > Apps** and uninstall Neurodesk App.

To remove application cache, delete `C:\Users\<username>\AppData\Roaming\neurodeskapp`. The AppData directory is hidden -- enable hidden items in Windows Explorer under **View > Show > Hidden Items**.

{{% /tab %}}
{{% tab header="Linux" %}}

```bash
# Debian / Ubuntu
sudo apt-get purge neurodeskapp
sudo rm /usr/bin/neurodeskapp
rm -rf ~/.config/neurodeskapp

# Fedora / RHEL / SUSE
sudo rpm -e neurodeskapp
sudo rm /usr/bin/neurodeskapp
rm -rf ~/.config/neurodeskapp

# Arch-based
sudo pacman -Rs neurodeskapp-bin
```

{{% /tab %}}
{{< /tabpane >}}
