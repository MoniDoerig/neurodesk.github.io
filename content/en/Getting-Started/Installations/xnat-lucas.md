---
title: "XNAT at the Lucas Centre Stanford"
linkTitle: "XNAT Lucas"
weight: 4
aliases:
- /docs/getting-started/installations/xnat-lucas
- /docs/getting-started/hosted/xnat-lucas
- /getting-started/hosted/xnat-lucas
description: >
  Transfer imaging data to the Lucas Centre XNAT and process it interactively with Neurodesk
---

The Stanford Lucas Centre XNAT is available at [xnat-lucas.neurodesk.org](https://xnat-lucas.neurodesk.org/). This guide explains how to transfer scanner data and additional files to XNAT, then start Neurodesk for interactive processing.

{{< toc >}}

## Before you transfer data

You will need:

- your XNAT username (which is your stanford useraccount),
- the project name you want to create, and
- a subject identifier that is appropriate for your study.

Always, use a de-identified subject identifier - The XNAT deployment is not approved for PHI data. 

## Transfer DICOM images from a scanner

DICOM images are sent from each scanner to **RSL60** using the scanner's network transfer function.

Before starting the transfer, set the DICOM **Patient ID** to this exact format:

```text
subject@username/project
```

For example:

```text
sub-001@jsmith/my-project
```

The three parts control where the images are stored and who has access to them.

| Part | Purpose |
| --- | --- |
| `subject` | The subject identifier created in XNAT |
| `username` | The XNAT user assigned as the project owner |
| `project` | The XNAT project created for the upload |

{{< alert color="warning" >}}
Check the Patient ID carefully before sending the images. The `@` and `/` characters are required, and the username must be the intended owner's XNAT username.
{{< /alert >}}

Once the Patient ID is set:

1. Select **RSL60** as the network transfer destination on the scanner.
2. Send the DICOM study.
3. Open [the Lucas Centre XNAT](https://xnat-lucas.neurodesk.org/) and check that the project, subject, and imaging session appear as expected.

The transfer creates the XNAT project, assigns `username` as its owner, and uploads the images under `subject`.

![Scanner DICOM network transfer screen with RSL60 selected as the destination](/static/docs/getting-started/installations/xnat-lucas/xnat-dicom-transfer.jpg)

## Transfer additional files

Files that are not part of the DICOM transfer, such as physiological recordings or raw Siemens TWIX meas.dat files, must be uploaded through the **public** Samba share on RSL60.

In the share, create the following directory structure under `xnat-upload`:

```text
xnat-upload/
└── owner/
    └── project/
        └── subject/
```

Replace:

- `owner` with the project owner's XNAT username,
- `project` with the XNAT project name, and
- `subject` with the XNAT subject identifier.

Copy the additional files into the `subject` directory. After the files have been processed, they are moved from `xnat-upload/` to `xnat-upload-done/`. This move is expected and indicates that the upload service has picked them up.

Keep your original files until you have confirmed that the upload completed successfully in XNAT. The files will be deleted automatically after 28days from RSL60.

![RSL60 public Samba share showing the xnat-upload owner, project, and subject directory structure](/static/docs/getting-started/installations/xnat-lucas/xnat-raw-and-physio-transfer.jpg)

## Download data from XNAT or transfer it to Oak

There are several tools for downloading data through the XNAT REST API. The [XNAT Web Services Client Tools](https://wiki.xnat.org/xnat-tools/xnat-web-services-client-tools) documentation describes options including PyXNAT, XNATpy, the XNAT Data Client (XDC), and YAXIL.

These tools can also be run on a Stanford system that has Oak mounted. Set an approved Oak project directory as the download destination to transfer data directly from XNAT to Oak instead of downloading it through your local computer.

{{< alert color="warning" >}}
The original XNAT command-line tool suite is deprecated. Select a current client that is compatible with the Lucas Centre XNAT version, and store data only in an Oak location approved for your project.
{{< /alert >}}

## Run processing with XNAT Container Service

XNAT Container Service can run predefined processing pipelines directly from XNAT without starting an interactive Neurodesk session. Select the processing scope that matches the input required by the pipeline:

| Scope | Start from | Use for |
| --- | --- | --- |
| Session level | The session's **Actions** menu | Pipelines that process the whole imaging session or combine multiple scans |
| Series level | The **Run** menu for an individual scan | Pipelines that process one selected scan or series |

The available containers depend on the data and the pipelines currently enabled by the Lucas Centre administrators.

### Run a container on a session

1. Open the subject's imaging session in XNAT.
2. In the **Actions** menu, select **Run Containers**.
3. Select the required pipeline. Session-level options may include fMRIPrep, ASLPrep, QSMxT, whole-session dcm2niix, DICOM to BIDS, and MRIQC. More containers can be added when needed.
4. Review the pipeline settings, provide any required inputs, and submit the job.

![XNAT imaging session Actions menu showing session-level container pipelines](/static/docs/getting-started/installations/xnat-lucas/xnat-container-service-session.png)

### Run a container on a series

1. Open the subject's imaging session and scroll to the **Scans** table.
2. Find the scan or series you want to process.
3. Open its menu in the **Run** column on the right.
4. Select the required pipeline. Series-level options may include Spinal Cord Toolbox, MuscleMap, and dcm2niix. More containers can be added when needed.
5. Review the pipeline settings, provide any required inputs, and submit the job.

![XNAT Scans table showing the series-level Run Container menu](/static/docs/getting-started/installations/xnat-lucas/xnat-container-service-series.png)

## Start Neurodesk for interactive processing

Neurodesk can be launched from an XNAT project, with access limited to the project data permitted by your XNAT account.

1. Go to [xnat-lucas.neurodesk.org](https://xnat-lucas.neurodesk.org/) and sign in.
2. Open the project you want to process.
3. In the project actions, select **Launch JupyterHub**. Select the required resources.
4. Wait for your Neurodesk environment to start. The browser will redirect to the interactive JupyterLab environment.
5. Use the file browser or a terminal to locate the mounted XNAT project data, then start the required Neurodesk application or analysis workflow.
6. Save scripts and working files in your personal workspace. XNAT project data is mounted according to your project permissions and may be read-only.

![XNAT Start Jupyter Notebook dialog with NeuroDesk selected and hardware resource options](/static/docs/getting-started/installations/xnat-lucas/xnat-neurodesk-start.png)

![Neurodesk JupyterLab session showing mounted XNAT data and an interactive NIfTI image viewer](/static/docs/getting-started/installations/xnat-lucas/xnat-neurodesk-jupyter.png)

### Upload processed data back to XNAT

You can send files produced in your Neurodesk session back to XNAT:

1. Open the JupyterLab **Launcher** and select **XNAT Upload**.

   ![Neurodesk JupyterLab Launcher showing the XNAT Upload tile](/static/docs/getting-started/installations/xnat-lucas/xnat-upload.png)

2. Before connecting for the first time, create an alias token in XNAT. Open your XNAT user account, select **Manage Alias Tokens**, and click **Create Alias Token**.

   ![XNAT user profile page for creating and managing alias tokens](/static/docs/getting-started/installations/xnat-lucas/xnat-alias-token.png)

3. Click **View** beside the new token to display its token name and secret.
4. Return to **XNAT Upload**, enter the token name in **Alias Token**, enter its secret in **Secret**, and click **Connect to XNAT**.

   ![XNAT Upload authentication form for entering an alias token and secret](/static/docs/getting-started/installations/xnat-lucas/xnat-upload-token.png)

5. Select the destination project and enter the subject and session IDs. Configure the modality, scan ID, scan type, and resource label as required. Leave **Scan ID** empty when uploading at session level.
6. Select the processed files in the file browser, or add their paths manually.

   ![XNAT Upload form for selecting the XNAT destination and processed files](/static/docs/getting-started/installations/xnat-lucas/xnat-upload-config.png)

7. Click **Upload**. The selected files will be stored in the configured XNAT project, subject, session, and optional scan location.

{{< alert color="warning" >}}
An alias token and its secret authenticate actions as your XNAT account. Treat them like a password: do not share them or include them in screenshots, and remove tokens that are no longer needed.
{{< /alert >}}

When you have finished, save your work and close the session. Your personal workspace is persistent, while inactive compute sessions may be stopped automatically.

## Related information

- [Neurodesk on XNAT](/getting-started/hosted/xnat/)
- [Using Neurodesktop](/getting-started/neurodesktop/)
