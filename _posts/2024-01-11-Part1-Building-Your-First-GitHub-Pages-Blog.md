---
layout: post
title: "Creating a Github Blog: Part 1 - Building Your First GitHub Pages Blog"
date:   2024-01-11 16:43:00 +0900
author: padawanjoy
tags: [github, blog, github-pages]
featured: true
---

Hello, everyone! Today, I'm excited to share with you a fun and easy way to create your own GitHub blog. GitHub blogs have many advantages, but the process might seem a bit complex for beginners. I hope this post helps you out. 

Written in January 2024 on a Mac OS, remember that the steps may vary slightly depending on updates to [github.com](http://github.com/) or the tools involved.

<br>
## **Before We Start**

1. First, go to [github.com](http://github.com/) and log in. If you haven’t registered yet, complete the registration process.
1. Once logged in, click the “Create repository” button on your Dashboard.

![Click the “Create repository” button]({{ "/images/posts/2024-01-11-Part1-Building-Your-First-GitHub-Pages-Blog/01.png"}})

<br>
## **Creating Your Repository**

1. Time to enter your Repository name. Make sure to use the format **`yourusername.github.io`**. This is essential for your GitHub blog to work correctly.
1. Choose “Public” and check the “Add a README file” option.
1. Click “Create repository” and your **`yourusername.github.io`** repository will be created.

![Creating Repository]({{ "/images/posts/2024-01-11-Part1-Building-Your-First-GitHub-Pages-Blog/02.png"}})

<br>
## **Downloading Your Blog Source Files**

1. Next, click the "Code" button and copy the Clone address that appears.
![Copy the Clone address]({{ "/images/posts/2024-01-11-Part1-Building-Your-First-GitHub-Pages-Blog/03.png"}})
1. Open your terminal.
- For Mac users, you can find the Terminal using Cmd+Space for “Spotlight Search”.
- Windows users can search for "cmd" in the search bar to open CMD.
1. Navigate to the directory of your choice. You can move to a directory by typing **`cd yourpath`**.
1. Enter **`git clone yourcopiedrepositoryaddress`** and execute it.
<br>
    If GitHub authentication is required, enter your GitHub username as the username and your personal access token as the password. If you are not familiar with what a personal access token is, or if you have not yet obtained one, refer to the post below.
    
    > [Generating a GitHub Personal Access Token](https://padawanjoy.com/blog/generating-a-github-personal-access-token)

<br>
If you want to clone to the folder path **`/Users/padawanjoy/Documents/Blog`**, then you should enter it as follows.
```bash
padawanjoy@MacStudio / % cd /Users/padawanjoy/Documents/Blog
padawanjoy@MacStudio / % git clone https://github.com/padawanjoy/padawanjoy.github.io.git
```
<br>
## **Creating Your Blog**

1. You should now have a **`yourusername.github.io`** folder. Go to this folder.
1. Create an index.html file there with the text “Welcome to my new GitHub Blog.”
1. Check if the file is created correctly, then Add, Commit, and Push your changes.

For example, if the name of the cloned folder is _padawanjoy.github.io_ then...
```bash
padawanjoy@MacStudio Blog % cd padawanjoy.github.io
padawanjoy@MacStudio padawanjoy.github.io % echo "Welcome to my new GitHub Blog" > index.html
padawanjoy@MacStudio padawanjoy.github.io % git add *
padawanjoy@MacStudio padawanjoy.github.io % git commit -m "Initial commit"
padawanjoy@MacStudio padawanjoy.github.io % git push -u origin main
```
<br>
## **Checking Your Blog**

1. Visit **`https://github.com/yourusername/yourusername.github.io`** to ensure everything has been pushed correctly.
<br>
    As shown in the picture below, a green check mark in the area circled in red indicates that the _git push_ is complete. When the _git push_ is in progress, an yellow dot will be displayed.
    ![git push is complete]({{ "/images/posts/2024-01-11-Part1-Building-Your-First-GitHub-Pages-Blog/04.png"}})
1. Now, access **`https://yourusername.github.io`** in your browser. You should see the message "Welcome to my new GitHub Blog!"

<br>
## **Wrapping Up**

That’s the entire process of creating a GitHub blog. Not too difficult, right? Now, you can have your own space on the internet. However, it's not quite looking like a blog yet. It's now time to start decorating your blog. [Stay tuned for the next post, where we’ll explore how to beautify your newly created blog](https://padawanjoy.com/blog/part2-applying-a-jekyll-theme). Stay excited! 🌟