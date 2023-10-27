# Development Machine Setup

This document outlines different required and optional tools, frameworks, cli, configuration etc., required on your local machine to learn terraform with AWS.

<br />

## My Local Machine Details (Just FYI)

Please find below details of my local machine. I have shared the details to make it easy for people with similar configuration to get started quickly. Infact, `mac` with latest OS should be sufficient to get started.

<br />

> NOTE: In future, I will try to come up with the detailed steps required on Windows OS. However for now, Windows users should find a way to install the required tools by themselves. 

<br />


| Parameter | Value |
|--|--|
| OS | mac  |
| Version | Sonoma 14.0  |

<br />

## Terminal Setup

This section describes my terminal setup details. Except `brew` package manager, this terminal setup is completely optional. 

I am only sharing my terminal setup details because I find this setup is cool and especially the split window capability of `iTerm2` improves my productivity. 

<br />

> NOTE: If any of the below tools are already installed using brew, use `brew upgrade` to update the formula of specific package.

<br />

| Tool | Installation Steps | Version |
|--|--|--|
| Brew | `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"` | 4.1.17 |
| iTerm2 | `brew install --cask iterm2` | 3.4.21 |
| On-My-Zsh | `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` <br /><br /> Edit `~/.zshrc` and set `ZSH_THEME` to `agnoster`| 5.9 (x86_64-apple-darwin21.3.0) |
| PowerLevel10k | `brew install romkatv/powerlevel10k/powerlevel10k` <br /> <br /> Now to add `powerlevel10k` zsh theme to `.zshrc`, check the path `/usr/local/opt/powerlevel10k/share/powerlevel10k/powerlevel10k.zsh-theme` in your machine. If the path do not exists, find the path to `powerlevel10k.zsh-theme` <br /> <br /> Finally execute `echo "source /usr/local/opt/powerlevel10k/share/powerlevel10k/powerlevel10k.zsh-theme" >>~/.zshrc` <br /> <br /> Run `p10k configure` to discover all options | 1.19.0 |
| MesloLGS NF | Download and install from `https://github.com/romkatv/dotfiles-public/tree/master/.local/share/fonts/NerdFonts` | N/A |

<br />

> Configure iTerm2 with theme and fonts:  <br/> - `Profiles > Select Default Profile > Edit Default Profile > Colors > Color Presets… > Solarized Dark` <br /> <br />  - `Profiles > Select Default Profile > Edit Default Profile > Text > Font > MesloLGS NF` <br /> <br /> We can turn off the mark indicators in iTerm2 <br /> - `Profiles > Select Default Profile > Edit Default Profile > Terminal > scroll down to "Shell Integration" > turn off "Show mark indicators"`.

<br />

At the end of above exercise, iTerm2 terminal should look like as below.

![iTerm2](../images/iTerm2.png "iTerm2")

<br />

## Development Tools Setup

Following development tools are used by me for curatung all the learning exercises of Terraform with AWS. There are other alternatives as well (for example, instead of using VS Code, we can opt for any other IDE as well), feel free to use any of the available alternatives.

| Tool | Installation Steps | Version |
|--|--|--|
| VS Code | `brew install --cask visual-studio-code`| 1.83.1 |
| Git | `brew install git`| 2.42.0 |
| AWS CLI | `brew install awscli`| 2.13.29 |
| Terraform | `brew tap hashicorp/tap` <br/> `brew install hashicorp/tap/terraform`| 1.6.2 |
| Hashicorp Terraform Plugin (VS Code) | | 2.28.2 |

<br />