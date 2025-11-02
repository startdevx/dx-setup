# Get Started With DX CLI

## What Value Does DX CLI bring?

This guide walks you through the one-time setup and configuration of DX CLI within your organization.

## 🔥 Prerequisites

[![Windows Supported](https://img.shields.io/badge/Windows-Supported-green?logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQBAMAAADt3eJSAAAAIVBMVEUAd9IAeNQAeNMAeNQAd9MAd9IAd9IAeNQAdtEAd9MAeNTK64shAAAACnRSTlODu8G1j3df/kORpJ63bAAAAERJREFUCNdjaHFxmZbp4uLBwLVq1SKpVasWgBgLiWYkGxsbMBsbmzEkKSmpOCkpqZGmnau8fKFUefkChtbQ0LDU0NAIAAiqOKf+3anXAAAAAElFTkSuQmCC)]()
[![Linux Not Supported (Coming Soon)](https://img.shields.io/badge/Linux-Coming%20Soon-red?logo=linux)](https://shields.io/)
[![Git Required](https://img.shields.io/badge/Git-2.x+-lightblue?logo=git)]()

DX CLI currently supports Windows operating system as it relies on .NET libraries available only in Windows PowerShell 5.1 (not in PowerShell Core). Linux support will be added in a future release.

Before getting started, make sure the following **required** components are installed and configured on your users’ environments. These prerequisites are necessary to run DX CLI.

* **Git**<br>
    Git must be installed, and its execution path must be included in the users’ `PATH` environment variable. To verify, run the following commands in a command prompt:

    ```bash
    where git
    echo %PATH%
    ```

* **Windows PowerShell 5.1**<br>
    Available by default on Windows. DX CLI requires Windows PowerShell 5.1 to run in `FullLanguage` mode. You can verify the current mode by running the following command in a PowerShell session:

    ```powershell
    $ExecutionContext.SessionState.LanguageMode
    ```

## 📖 Setup Git Repositories

### Create Empty Repositories

Start by creating empty repositories into your organization’s internal source control platform (e.g., **GitHub**, **GitLab**, **Azure DevOps**, or **Bitbucket**). You can name them however you like, as long as you make a clear distinction between them:

| Repository | Usage | Is Mandatory |
| ---------- | ----- | ------------ |
| `dx-installer` | A repository used to store users' installation script. Your users will use it to install DX CLI on their Windows environment. | `true` |
| `dx-core` | A repository used to store DX CLI core binaries. | `true` |
| `dx-packages` | A repository used to store all custom configuration scripts your organization will create. | `true` |
| `dx-analytics` | A repository used to store DX CLI users’ usage analytics. | `false` |

### Copy DX CLI Source Code Into Your Repositories

* Copy the source code from the `main` branch of [dx-installer](https://github.com/startdevx/dx-installer) on GitHub into your organization’s `dx-installer` repository.
* Copy the source code from the `main` branch of [dx-core](https://github.com/startdevx/dx-core) on GitHub into your organization’s `dx-core` repository.

`dx-packages` and `dx-analytics` repositories remain empty for now.

## ⚙️ Update `dx-installer` Settings File

After copying the repositories in previous step, from your `dx-installer` repository, open the `settings.json` file and update the following fields:

| Field | Type | Is Mandatory | Description |
| ----- | ---- | ------------ | ----------- |
| `emailDomain` | `string` | `true` | The email domain of your organization. |
| `ldapDirectory` | `string` | `false` | Enables LDAP directory integration. DX CLI will retrieve the user’s name and email from the LDAP directory to configure Git (for example, `LDAP://startdevx.com`). If this is not set, DX CLI will default to the local system user information. |
| `useProxy` | `boolean` | `false` | If set to `true`, DX CLI will attempt to detect your organization proxy and automatically set the `HTTP_PROXY` and `HTTPS_PROXY` environment variables with the proxy URL. |
| `repositories.core` | `string` | `true` | The Git clone URL for your organization's `dx-core` repository. |
| `repositories.packages` | `string` | `true` | The Git clone URL for your organization's `dx-packages` repository. |
| `repositories.analytics` | `string` | `false` | If you have created an empty `dx-analytics` repository, enter the Git clone URL for your organization's `dx-analytics` repository. Make sure your organization’s users have **write access** to this repository so they can push data to the `default` branch. |

## ✅ Congratulations! DX CLI Is Now Ready To Be Used Within Your Organization

Users in your organization can now install DX CLI on their Windows environment by following the instructions in the `README.md` file of your organization's `dx-installer` repository.

## ⏭️ Next Step: Create Your First Package

DX CLI without packages is an empty shell. Create your first package by following the instructions in the `README.md` file of your organization's `dx-core` repository.

## 🪙 Credits

DX CLI is an open-source solution available on [GitHub](https://github.com/startdevx/dx-getstarted), crafted by [Start DevX](https://github.com/startdevx) organization.
