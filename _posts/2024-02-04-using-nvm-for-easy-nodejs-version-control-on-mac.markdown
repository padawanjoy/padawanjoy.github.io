---
layout: post
title:  Using NVM for Easy Node.js Version Control on Mac
date:   2024-02-04 21:42:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-04-using-nvm-for-easy-nodejs-version-control-on-mac/01.png'
tags:   [nvm, node-js]
# tags_color: '#6b96df'
featured: false
---
If you're a developer working with Node.js, you're likely familiar with the challenge of managing different versions of Node.js across various projects. Enter Node Version Manager, or NVM, which might as well be considered a magic wand for your development environment. NVM allows you to easily install and manage multiple versions of Node.js. In this article, we'll explore the basics of NVM, its benefits, and how to set it up and use it on Mac OS with a zsh shell. For reference, this guide is based on the Mac OS platform.

## What is NVM?

NVM stands for Node Version Manager, a command-line tool that enables you to manage multiple installations of Node.js. It allows you to switch between versions seamlessly and use different versions of Node.js for different projects. By isolating each Node.js version, NVM ensures that you can maintain multiple versions on the same system without any conflicts.

## Benefits of Using NVM

Using NVM comes with several advantages over not using it:


**1. Ease of Version Management**: With NVM, you can install and switch between different Node.js versions with a few simple commands. This is especially useful when working on multiple development projects that require different Node.js versions.

**2. Project-specific Version Setting**: You can specify the version of Node.js to use for each project through a **`.nvmrc`** file. This helps to synchronize the development environment among team members.

**3. Simplified Installation and Updates**: Installing Node.js via NVM is straightforward, and updating to new versions as they are released is just as easy.

## Installing and Using NVM on Mac OS

### Installation

Installing NVM on Mac OS is as simple as running a single command. Open your zsh terminal and enter the following:

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

This command downloads and executes the NVM installation script. After the installation, your **`~/.zshrc`** file should include the following environment setup:

```sh
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

### Installing Node.js Versions

Installing a specific version of Node.js with NVM is straightforward. For example, to install version 14.17.0 of Node.js, use the following command:

```sh
nvm install 14.17.0
```

### Listing and Switching Versions

To see all installed Node.js versions, enter:

```sh
nvm ls
```

To switch to a specific version, simply run:

```sh
nvm use 14.17.0
```

### Setting a Project-specific Node.js Version

Create a **`.nvmrc`** file in your project directory and specify the desired Node.js version. For instance, to use version **`14.17.0`**, write this version number in the **`.nvmrc`** file. Then, running the following command in your project directory will automatically switch to that version:

```sh
nvm use
```

Development often requires managing different Node.js versions due to project environments or other reasons. This article aims to assist in those situations. We hope that managing your Node.js versions becomes more straightforward with NVM, contributing to a more efficient development setup. 🧑🏻‍💻