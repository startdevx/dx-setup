# Get Started With DevX CLI

## Prerequisites

DevX CLI currently supports Windows operating system. Linux will be supported in future releases.

To run it on Windows, it requires:

* **Windows PowerShell 5.1**, built-in Windows operating system. It should be able to run in `FullLanguage` mode. The language mode can be checked in a Windows PowerShell session by executing:

```powershell
PS C:\Users\startdevx> $ExecutionContext.SessionState.LanguageMode
FullLanguage
```

* **Git** must be installed on users's environment.

## Get started

Copy the following repositories in your corporate internal source control manager such as *GitHub*, *GitLab*, *Azure DevOps* or *Bitbucket*:
* [devxcli-installer](https://github.com/startdevx/devxcli-installer)
* [devxcli-core](https://github.com/startdevx/devxcli-core)
* [devxcli-packages](https://github.com/startdevx/devxcli-packages)

You can rename the repositories or leave them unchanged. This will not impact how DevX CLI behaves.

## Update required fields in DevX CLI Installer

In the `settings.json` file in **DevX Installer** repository, update the following required fields:
* `emailDomain` - **string**: the email domain of your company, e.g. for an email address like kevin@startdevx.com, the email domain will be `startdevx.com`
* `repository.core` - **string**: the Git repository clone url of DevX CLI core you have created in the previous section
* `repository.packages` - **string**: the Git repository clone url of DevX CLI packages you have created in the previous section

## Optional installer configuration fields

You have the options to activate other features from DevX CLI installer. Update the following fields to use them:
* `ldapDirectory` - **string**: DevX CLI will try to access the LDAP directory to retrieve user's email address and name to configure Git. If not set, it will use default user name from the users' local environment.
* `setProxy` - **boolean**: if set to `true`, DevX CLI will auto discover if a company proxy is setup. If it is the case, DevX CLI will configure both `HTTP_PROXY` and `HTTPS_PROXY` with the discovered proxy.
* `repository.analytics` - **string**: if you want to activate analytics on DevX CLI, initialize an empty repository in your company internal source control manager and specify its Git repository clone url in this field. The analytics repository should be configured so all users using DevX CLI have `write` access on this repository in order to push data on the `default` branch.