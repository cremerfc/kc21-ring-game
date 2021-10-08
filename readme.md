# Kubecon 2021 Quest for the Ring Game

Thank you for participating in the Quest for the Ring Game with Replicated!

Please read through the entire instructions before you get started and let us know if you have any questions.

## Overview

In this Quest, you will be tasked with getting a Kubernetes Application up and running on a Linux Host. Succeed and there will be treasures beyond your wildest dreams! Well.. actually we have Kubernetes rings and some Replicated swag.

You will be armed with Replicated open source tooling to help you on your quest.

## Connect to VM

An Ubuntu machine has been provisioned for you and this is where our adventure begins.

If you do not have the IP address of your VM, please let us know. This should have been given to you in an email prior to this session.

1. Connect to the VM with `ssh`

    We have created a default user named 'kots' to use. We'll provide the default password in the session. For example, you may run something like:

    ```shell
    ssh kots@{IP_Address}
    ```

## Start Installation

1. Run the following install command, once you have logged in to the remote host.

    ```shell
    curl -sSL https://k8s.kurl.sh/ringquestapp | sudo bash
    ```

    This will download and install kubernetes on the Linux host. For the installation of the cluster, we are leveraging [KURL](https://kurl.sh) which is a Replicated Open Source project. This project allows you define Kubernetes Add-ons, including the version and some configurations. One of the Add-ons that will be deployed is [KOTS](https://kots.io), which is another Replicated Open Source project. This project helps people manage the deployment and maintenance of Off-the-Shelf Kubernetes Applications.

1. Take note of the **URL and password** provided in the output. You may need to scroll up

    <p align="center"><img src="./content/term-output.png" width=500 ></img></p>

    You can reset the password later, in case you forget it with the following command:

    ```bash script
    kubectl kots passwordreset ringquestapp -n default
    ```

1. Run the following command to reload your shell session

    ```shell
    bash -l
    ```

## Deploy the Application

1. Browse to the address provided. You should see something that looks like this (will depend on your browser):

    <p align="center"><img src="./content/tls-warn.png" width=400 ></img></p>

1. Click on 'Continue to Setup' and follow the prompts to continue.

1. Accept and continue past any browser warnings

1. Click 'Skip & Continue' on the screen for uploading a cert.

    This is used to provide the admin console a cert to secure the connection. This is not required for this lab.

    <p align="center"><img src="./content/upload-certs.png" width=400 ></img></p>

1. Enter the password provided from the terminal output at the login screen.

1. Choose the lab type and difficulty level in the configuration screen. The harder the challenge the bigger the rewards!

    > The "Hard" option will have you spend more time in the terminal running `kubectl` commands.

1. Click 'Continue' after the preflights have run.

    Preflights ensure everything is ready to deploy our application. The preflights leverage another Open Source project from Replicated, called [Troubleshoot](https://troubleshoot.sh). This project allows you to declaratively define collectors and analyzers to help troubleshoot Kubernetes Applications.

## Did the Application Deploy?

After preflights, you should arrive at this window:

<p align="center"><img src="./content/admin-console.png" width=400 ></img></p>

As you can see, the status of the app is "unavailable". Something is wrong with the app. It is not coming up.

1. Click on the 'Details' link to get more information (next to the "Unavailable" application status).

    The dialog will display which workloads or services may be malfunctioning.

    <p align="center"><img src="./content/service-status.png" width=250 ></img></p>

1. Click on the 'Troubleshoot' button.

    This is a shortcut to take you to the 'Troubleshoot' tab:

    <p align="center"><img src="./content/troubleshoot-page.png" width=650 ></img></p>

1. Click the 'Analyze Quest for the Ring of Kubernetes' button.

    This may take a few minutes and while it is generating. You should see a progress bar similar to this one:

    <p align="center"><img src="./content/bundle-progress.png" width=650 ></img></p>

    Once the Support Bundle is finished running it should display the following tile(s). Looks like the problem is that we are missing a configuration file.

    <p align="center"><img src="./content/tile-error.png" width=450 ></img></p>

1. Click on the 'article' link to find out how to solve this particular problem
