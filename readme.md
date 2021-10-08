<h1>Kubecon 2021 Quest for the Ring Game</h1>

Thank you for participating in the Quest for the Ring Game with Replicated!

Please read through the entire instructions before you get started and let us know if you have any questions.

**Overview**

In this Quest, you are tasked with getting a Kubernetes Application up and running on a Linux host. Succeed, and there will be treasures beyond your wildest dreams! Well.. actually we have Kubernetes rings and some Replicated swag.

You will be armed with Replicated open source tooling to help you on your quest.

**Connecting to a virtual machine**

An Ubuntu virtual machine (VM) has been provisioned for you, and this is where our adventure begins.

If you do not have the IP address of your VM, please let us know. This should have been given to you in an email before to this session.

To connect to the VM, run an `ssh` command. We have created a default user named 'kots' to use. For example, you can run:

```shell
ssh kots@{IP_Address}
```

We will provide the default password in the session.

**Starting the installation**

After logging in to the remote host, copy and paste the following installation command in your terminal:

```shell
curl -sSL https://k8s.kurl.sh/ringquestapp | sudo bash
```

This downloads and installs Kubernetes on the Linux host. For the installation of the cluster, we are leveraging [KURL](https://kurl.sh), which is a Replicated Open Source project. This project allows you define Kubernetes add-ons, including the version and some configurations. One of the add-ons that will be deployed is [KOTS](https://kots.io), which is another Replicated Open Source project. This project helps people manage the deployment and maintenance of off-the-shelf Kubernetes applications.

**Deploying the application**

1. After the installation is complete, you should see output similar to the screenshot below. Scroll up, if needed, to find the URL for `Kotsadm`. Note the password.

  <p align="center"><img src="./content/term-output.png" width=500 ></img></p>

2. Browse to the address and you should see something like this, depending on your browser:

<p align="center"><img src="./content/tls-warn.png" width=400 ></img></p>

3. Click **Continue to Setup**, and follow the prompts.

  The following screen gives you an option to upload a certificate to secure the connection to the admin console. For this lab, just click on **Skip & Continue**.

  <p align="center"><img src="./content/upload-certs.png" width=400 ></img></p>

4. At the login screen, enter the password that was provided in the terminal output.

  If you closed the terminal and no longer have access to the password, you can reset it by running the following command.
  **Hint:** make sure to run <code>bash -l</code> on the terminal before running any other commands.

  ```bash script

  $ kubectl kots reset-password -n default

  ```

5. After you are logged in, you are prompted to upload a license. Download [this yaml file](./Lab_Participant.yaml), and drop it into the license box.

6. You'll be asked to choose the level of difficulty. The harder the challenge, the bigger the rewards! The more difficult option will have you spend more time in the terminal running `kubectl` commands.

  After you choose your difficulty level, app manager runs a series of preflights to ensure everything is ready to deploy our application. The preflights leverage another Open Source project from Replicated, called [Troubleshoot](https://troubleshoot.sh). This project allows you to declaratively define collectors and analyzers to help troubleshoot Kubernetes applications.

**Did the application deploy?**

After the preflight checks, the following window opens:

<p align="center"><img src="./content/admin-console.png" width=400 ></img></p>

As you can see, the status of the app is spinning. Something is wrong with the app and is not coming up.

1. Click on the **Details** link to get more information. The dialog displays which workloads or services may be malfunctioning.

  <p align="center"><img src="./content/service-status.png" width=250 ></img></p>


2. Click **Troubleshoot** to open the Troubleshoot tab:

  <p align="center"><img src="./content/troubleshoot-page.png" width=650 ></img></p>

3. Click **Generate Support Bundle**. This can take a few minutes. While it is generating, you will see a progress bar similar to this one:

  <p align="center"><img src="./content/bundle-progress.png" width=650 ></img></p>

  After the support bundle is finished running, it should display the following tile(s). It looks like the problem is that we are missing a configuration file.

  <p align="center"><img src="./content/tile-error.png" width=450 ></img></p>

4. Click on the link on the tile to find out how to solve this particular problem.
