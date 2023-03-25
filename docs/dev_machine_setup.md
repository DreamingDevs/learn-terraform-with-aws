# Development Machine Setup

This document outlines different required and optional tools, frameworks, cli, configuration etc., required on your local machine to learn terraform with AWS.

## My Local Machine Details (Just FYI)

Please find below details of my local machine. I have shared the details to make it easy for people with similar configuration to get started quickly. Infact, `mac` with latest OS should be sufficient to get started.

<br />

> NOTE: In future, I will try to come up with the detailed steps required on Windows OS. However for now, Windows users should find a way to install the required tools by themselves. 

<br />


| Parameter | Value |
|--|--|
| OS | mac  |
| Version | Monterey 12.5.1  |

<br />

## Terminal Setup (optional)

This section describes my terminal setup details. Except `brew` package manager, this terminal setup is completely optional. 

I am only sharing my terminal setup details because I find this setup is cool and especially the split window capability of `iTerm2` improves my productivity. 

<br />

> NOTE: If any of the below tools are already installed using brew, use `brew upgrade` to update the formula of specific package.

<br />

| Tool | Installation Steps | Version |
|--|--|--|
| Brew | `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"` | 4.0.6 |
| iTerm2 | `brew install --cask iterm2` | 3.4.19 |
| On-My-Zsh | `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` <br /><br /> Edit `~/.zshrc` and set `ZSH_THEME` to `agnoster`| 5.9 (x86_64-apple-darwin21.3.0) |
| PowerLevel10k | `brew install romkatv/powerlevel10k/powerlevel10k` <br /> <br /> Execute `echo "source $(brew --prefix)/opt/powerlevel10k/powerlevel10k.zsh-theme" >>~/.zshrc` <br /> <br /> Run `p10k configure` to discover all options | 1.17.0 |
| MesloLGS NF | Download and install from `https://github.com/romkatv/dotfiles-public/tree/master/.local/share/fonts/NerdFonts` | N/A |

<br />

> Configure iTerm2 with theme and fonts:  <br/> - `Profiles -> Select Default Profile -> Edit Default Profile -> Colors -> Color Presets… -> Solarized Dark` <br /> <br />  -`Profiles -> Select Default Profile -> Edit Default Profile -> Text -> Font -> MesloLGS NF`

<br />

At the end of above exercise, iTerm2 terminal should look like as below.

![iTerm2](../images/iTerm2.png "iTerm2")

<br />

## Development Tools Setup (Required)

Following development tools are used by me for curatung all the learning exercises of Terraform with AWS. There are other alternatives as well (for example, instead of using VS Code, we can opt for any other IDE as well), feel free to use any of the available alternatives.

| Tool | Installation Steps | Version |
|--|--|--|
| Git | `brew install git`| 2.40.0 |
| VS Code | `brew install --cask visual-studio-code`| 1.76.2 |

<br />

## Create AWS Account

<br />

 - Navigate to [create AWS Account](https://portal.aws.amazon.com/billing/signup#/start/email) page. 
 - Enter a valid email id and root username. Proceed to verify the email id.
 - Provide contact and address information.
 - Enter Credit / Debit card information for billing purpose. Proceed to verify the card details through the respective bank's authentication system (typically OTP).
    - A nominal fee of 2 INR (Indian currency) will be deducted to verify the authenticity of the card.
    - Going forward card will not charged if the usage is within the limits of free tier. But once exceeded, card will be charged based on usage.
 - Confirm the identity by entering mobile no. and verifying it with OTP.
 - Lastly select the Basic Support - Free plan as we only need this AWS account of executing our exercises.

