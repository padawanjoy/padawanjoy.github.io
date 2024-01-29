---
layout: post
title:  Managing Java Versions with SDKMAN!
date:   2024-01-29 12:17:00 +0900
author: padawanjoy
image:  '/images/posts/2024-01-29-managing-java-versions-with-sdkman/01.png'
tags:   [sdkman, java]
# tags_color: '#6b96df'
featured: false
---
Hello there! Today, I'm excited to guide you through managing multiple Java versions on Mac OS, all thanks to SDKMAN!. If you thought managing Java versions was complex, let SDKMAN! simplify it for you. Let's dive in!

## Installing SDKMAN!
First things first, we need to install SDKMAN!. On your Mac OS terminal, type the following command:

```bash
$ curl -s "https://get.sdkman.io" | bash
```

Once the installation is complete, to initialize SDKMAN! in the Zsh environment, add the following line to your .zshrc file:

```bash
$ source "$HOME/.sdkman/bin/sdkman-init.sh"
```

Finally, let's verify the installation:

```bash
$ sdk version
```

If everything went smoothly, you should see a version number:

```bash
SDKMAN!
script: 5.18.2
native: 0.4.6
```

## Managing Java with SDKMAN!
Now, let's explore how to manage Java versions using SDKMAN!.

### Listing Available Java Versions
To see what Java versions are available:

```bash
$ sdk list java
```

This command shows a variety of Java versions you can choose from.

### Installing a Specific Version
For instance, to install version **`11.0.17-zulu`**:

```bash
sdk install java 11.0.17-zulu
```

After the installation, you'll be prompted to set this version as the default. Simply choose ‘yes’ or press Enter.

### Uninstalling Java Versions
To remove a Java version that you no longer need:

```bash
$ sdk uninstall java 11.0.17-zulu
```

### Switching Between Installed Versions
To switch to another installed version, say **`11.0.1-zulu`**:

```bash
$ sdk use java 11.0.1-zulu
```

And to check the current active version:

```bash
$ sdk current
```

If you want the same Java version across all shells, use the **``default``** command:

```bash
$ sdk default java 11.0.1-zulu
```

## Upgrading Versions
To upgrade to the latest Java version:

```bash
$ sdk upgrade java
```

After the upgrade, you can confirm if the current version is the latest one.

## Wrap-up
And that's a wrap on managing Java versions with SDKMAN!. This tool makes it easy to install, manage, and upgrade Java versions. Now you can efficiently manage your Java environment using SDKMAN!. Happy coding! 💻 🖖