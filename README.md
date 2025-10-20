# Get Started With DX CLI

This guide walks you through installing and configuring **DX CLI** on Windows environment within your organization.

## 🔎 DX CLI Overview

TO DO

## 🔥 Prerequisites [![Windows Support](https://img.shields.io/badge/OS-Windows-blue?logo=windows)]() [![Git Required](https://img.shields.io/badge/Dependency-Git-orange?logo=git)]() [![PowerShell](https://img.shields.io/badge/PowerShell-5.1+-lightblue?logo=powershell)]()

Currently, **DX CLI** supports **Windows** operating system. ***Linux** support will be introduced in future releases.*

Before installing, ensure the following **required** components are available on your system:

* **Windows PowerShell 5.1**

    Installed by default on Windows. DX CLI requires Windows PowerShell to run in `FullLanguage` mode. You can verify the current mode by running the following command in a PowerShell session:

```powershell
$ExecutionContext.SessionState.LanguageMode
```

* **Git**

    Git must be installed and available in the users' system’s PATH.

## 📓 Repositories Setup

To get started, copy the following repositories into your organization’s internal source control platform (e.g., **GitHub**, **GitLab**, **Azure DevOps**, or **Bitbucket**):

* DX CLI installer: [dx-installer](https://github.com/startdevx/dx-installer)
* DX CLI core: [dx-core](https://github.com/startdevx/dx-core)

And create an empty repository `dx-packages` that will be used for DX CLI packages.

***Note**: You can rename these repositories if needed. DX CLI will function correctly regardless of the repository names.*

## ⚙️ Configure DX CLI Installer

After copying the repositories into your organization’s internal source control platform, open the `settings.json` file located in the **DX CLI installer** repository and update the following required fields:

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| `emailDomain` | `string` | The corporate email domain. For example, for kevin@startdevx.com, use `startdevx.com` |
| `repositories.core` | `string` | The corporate Git clone URL of your DX CLI core repository |
| `repositories.packages` | `string` | The corporate Git clone URL of your DX CLI packages repository |

## ✨ Optional Configuration

You can enable additional features in **DX CLI installer** by configuring the following optional fields in `settings.json`:

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| `ldapDirectory` | `string` | Enables LDAP directory integration. DX CLI will retrieve the user’s name and email from the directory to configure Git. For example, `LDAP://startdevx.com`. If not set, it defaults to the local system user name.  |
| `useProxy` | `boolean` | If `true`, DX CLI automatically detects and configures corporate proxies by setting the `HTTP_PROXY` and `HTTPS_PROXY` environment variables |
| `repositories.analytics` | `string` | To enable analytics, create an empty repository in your organization’s source control platform and specify its Git clone URL here. Ensure all DX CLI users have **write access** to this repository to allow pushing analytics data to the `default` branch |

## ✅ DX CLI Is Now Ready To Be Used Within Your Organization

Software engineers can now install it following the `README.md` instructions file located in the **DX CLI installer** repository.

## ⏭️ Next Step: Create Your First Feature

**DX CLI** without features is an empty shell. Create your first feature by following the tutorial in the `README.md` file in the **DX CLI core** repository.

## 🪙 Credits

**DX CLI** is an open-source solution available on [GitHub](https://github.com/startdevx/dx-getstarted), crafted by [Start DevX](https://github.com/startdevx) organization.