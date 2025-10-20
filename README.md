# Getting Started with DevX CLI in your organization

[![Windows Support](https://img.shields.io/badge/OS-Windows-blue?logo=windows)]()
[![Git Required](https://img.shields.io/badge/Dependency-Git-orange?logo=git)]()
[![PowerShell](https://img.shields.io/badge/PowerShell-5.1+-lightblue?logo=powershell)]()

This guide walks you through installing and configuring **DevX CLI** on Windows environment within your organization.

## Credits

DevX CLI is an open source solution available on [GitHub](https://github.com/startdevx/devxcli-get-started) and crafted by [Start DevX](https://github.com/startdevx) organization.

## 🧠 DevX CLI Overview (TO DO)

## 🔥 Prerequisites

Currently, **DevX CLI** supports **Windows** operating system. ***Linux** support will be introduced in future releases.*

Before installing, ensure the following **required** components are available on your system:

* **Windows PowerShell 5.1**

    Installed by default on Windows. DevX CLI requires PowerShell to run in `FullLanguage` mode. You can verify the current mode by running the following command in a PowerShell session:

    ```powershell
    $ExecutionContext.SessionState.LanguageMode
    ```

* **Git**

    Git must be installed and available in the users' system’s PATH.

## 📓 Repository Setup

To get started, clone the following repositories into your organization’s internal source control platform (e.g., **GitHub**, **GitLab**, **Azure DevOps**, or **Bitbucket**):

* [devxcli-installer](https://github.com/startdevx/devxcli-installer)
* [devxcli-core](https://github.com/startdevx/devxcli-core)
* [devxcli-packages](https://github.com/startdevx/devxcli-packages)

***Note**: You can rename these repositories if needed. DevX CLI will function correctly regardless of the repository names.*

## ⚙️ Configure DevX CLI Installer

After cloning the repositories, open the `settings.json` file located in the **DevX CLI Installer** repository and update the following required fields:

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| `emailDomain` | `string` | The corporate email domain. For example, for kevin@startdevx.com, use `startdevx.com` |
| `repositories.core` | `string` | The corporate Git clone URL of your DevX CLI Core repository |
| `repositories.packages` | `string` | The corporate Git clone URL of your DevX CLI Packages repository |

## ✨ Optional Configuration

You can enable additional features in **DevX CLI Installer** by configuring the following optional fields in `settings.json`:

| Field | Type | Description |
| ----------- | ----------- | ----------- |
| `ldapDirectory` | `string` | Enables LDAP directory integration. DevX CLI will retrieve the user’s name and email from the directory to configure Git. If not set, it defaults to the local system user name. For example, `LDAP://startdevx.com` |
| `useProxy` | `boolean` | If `true`, DevX CLI automatically detects and configures corporate proxies by setting the `HTTP_PROXY` and `HTTPS_PROXY` environment variables |
| `repositories.analytics` | `string` | To enable analytics, create an empty repository in your organization’s source control platform and specify its Git clone URL here. Ensure all DevX CLI users have **write access** to this repository to allow pushing analytics data to the `default` branch |

## ✅ DevX CLI is now ready to be used within your organization

Software engineers can now install it following the `README.md` instructions file located in the **DevX CLI Installer** repository.

## ⏭️ Next Step: Create Your First Feature

**DevX CLI** without features is an empty shell. Create your first feature by following the tutorial in the `README.md` file in the **DevX CLI Packages** repository.