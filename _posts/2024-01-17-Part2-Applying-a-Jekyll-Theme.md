---
layout: post
title: "Creating a Github Blog: Part 2 -  Applying a Jekyll Theme"
date:   2024-01-17 12:37:00 +0900
author: padawanjoy
tags: [github, blog, github-pages, ruby, rbenv, Jekyll]
---

Hello everyone! [Last time, we learned how to start a GitHub blog](https://padawanjoy.com/blog/part1-building-your-first-github-pages-blog). Now, let's decorate our blog by applying a Jekyll theme.

<br>
## **Installing Ruby**
First, to use a Jekyll theme, we need to install Ruby. Though Mac OS comes with Ruby, let's install it anew.

* #### **Managing Ruby Versions with rbenv**
rbenv is a tool that manages different versions of Ruby. It allows you to install multiple versions and use different versions for different projects.

* #### **Installing rbenv**
Move to your GitHub blog folder and install rbenv.
```bash
padawanjoy@MacStudio / % cd yourgithubblogpath
padawanjoy@MacStudio padawanjoy.github.io % brew install rbenv
```

* #### **Checking and Installing Ruby Versions**
Check the list of available Ruby versions and install the one you prefer. 
```bash
padawanjoy@MacStudio padawanjoy.github.io % rbenv install -l
3.0.6
3.1.4
3.2.2
jruby-9.4.3.0
mruby-3.2.0
picoruby-3.0.0
truffleruby-23.0.0
truffleruby+graalvm-23.0.0
```
For instance, if you choose version 3.1.4, you would install it like this:
```bash
padawanjoy@MacStudio padawanjoy.github.io % rbenv install 3.1.4
```

<br>
## **Setting the Ruby Version**
Set the newly installed Ruby version as the default for your system.
```bash
padawanjoy@MacStudio padawanjoy.github.io % rbenv global 3.1.4
```

<br>
## **Installing Jekyll and Bundler**
Now, install Jekyll along with Bundler.
```bash
padawanjoy@MacStudio padawanjoy.github.io % gem install jekyll bundler
```

<br>
## **Removing the Existing index.html File**
If you created an index.html file in the last post, remove it now.
```bash
padawanjoy@MacStudio padawanjoy.github.io % rm -f index.html
```

<br>
## **Creating a Jekyll Blog Structure**
Transform your blog into a Jekyll structure.
```bash
padawanjoy@MacStudio padawanjoy.github.io % jekyll new ./
```
If you encounter any issues like blow, use the --force option.
```bash
Conflict: /Users/padawanjoy/Documents/Padawan_Joy/padawanjoy•github.io exists and is not empty.
Ensure /Users/padawanjoy/Documents/Padawan_Joy/padawanjoy•github.io is empty or else try again with '—force' to proceed and overwrite any files.

padawanjoy@MacStudio padawanjoy.github.io % jekyll new ./ --force
```

<br>
## **Finalizing Jekyll Setup with Bundle Install**
```bash
padawanjoy@MacStudio padawanjoy.github.io % bundle install
```

<br>
## **Previewing Your Jekyll Blog Locally**
```bash
padawanjoy@MacStudio padawanjoy.github.io % bundle exec jekyll serve
```
Visit `http://127.0.0.1:4000/` or `http://localhost:4000/` in your browser to see your blog.

![Previewing Your Jekyll Blog Locally]({{ "/images/posts/2024-01-17-Part2-Applying-a-Jekyll-Theme/01.png"}})

To stop the server running on your computer, press `Cmd+C` if you're using a Mac, or `Ctrl+C` if you're on Windows.

<br>
## **Choosing and Applying a Jekyll Theme**
Browse through various sites to find a Jekyll theme that you like and download it.
- [http://jekyllthemes.org/](http://jekyllthemes.org/)
- [https://jekyllthemes.io/free](https://jekyllthemes.io/free)
- [http://themes.jekyllrc.org/](http://themes.jekyllrc.org/)
- [https://github.com/topics/jekyll-theme](https://github.com/topics/jekyll-theme)

<br>
## **Applying the Theme**
Copy the files and folders from the downloaded theme and paste them into your blog folder. If there is already a file with the same name, overwrite it.

<br>
## **Installing the Theme with Bundle**
```bash
padawanjoy@MacStudio padawanjoy.github.io % bundle install
```

<br>
## **Verifying the Theme Application**
Run your local server to see the new theme applied.
```bash
padawanjoy@MacStudio padawanjoy.github.io % bundle exec jekyll serve
```
Depending on the theme, you might need to enter a subpath beyond `http://127.0.0.1:4000/` or `http://localhost:4000/`. You can find out the exact address by checking the 'Server address' section in the terminal output.
```bash
padawanjoy@MacStudio padawanjoy.github.io % bundle exec jekyll serve

[...] (portion omitted for brevity)

done in 1.149 seconds.
Auto-regeneration: enabled for '/Users/padawanjoy/Documents/Padawan_Joy/padawanjoy.github.io'
Server address: http://127.0.0.1:4000/Type-on-Strap/
Server running... press ctrl-c to stop.

```
![Verifying the Theme Application]({{ "/images/posts/2024-01-17-Part2-Applying-a-Jekyll-Theme/02.png"}})
The theme has been successfully applied.

<br>
## **Customizing the Theme**
You can customize each theme by modifying the config.xml file.

Detailed customization instructions can be found on the GitHub page of the downloaded theme. Those familiar with development can directly modify the source code to customize the theme. However, be sure to check the license applied to the theme before making any changes.

<br>
## **Uploading the Updated Blog to GitHub**
```bash
padawanjoy@MacStudio padawanjoy.github.io % git add *
padawanjoy@MacStudio padawanjoy.github.io % git commit -m "Applied new theme"
padawanjoy@MacStudio padawanjoy.github.io % git push -u origin main
```

<br>
## **Checking Your Blog**
Visit `https://yourusername.github.io` to see your blog with the new theme applied. Note that it might take some time for the changes to apply after performing a git push.

That wraps up our guide on applying a Jekyll theme to your GitHub blog. Now, go ahead and create a stunning blog of your own!