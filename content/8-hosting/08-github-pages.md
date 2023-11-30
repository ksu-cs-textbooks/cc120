---
title: "GitHub Pages"
pre: "8. "
weight: 80
date: 2018-08-24T10:53:26-05:00

---

There are endless number of website hosting options out there with varying ranges of prices and effort to maintain. For now, we are going to go with a middle ground option with GitHub Pages. GitHub pages offers an easy way of hosting static websites (static websites have no back-end server logic, like databases, users, etc.). You can host one public facing website for free with a basic account and more if you have a pro account. Here, we are going to walk through how to get a webpage setup on GitHub Pages.

## 1. Getting an Account

Getting an account on GitHub is pretty easy. To sign up, follow this link: [https://github.com/signup](https://github.com/signup). If you still have a few years left before you graduate, I highly recommend you use your K-State email address for your account so you can get the free student developer pack [https://education.github.com/pack](https://education.github.com/pack) which has lots of free goodies. If you already have an account, you should be able to change your email address to take advantage of this perk.

## 2. Creating the Repository

To get starting making our webpage, we need a repository. Repositories are quite similar to file folders in Cloud Storage like OneDrive or Google Drive, they are a central storage location where people can collaborate, track changes, and develop software (among other things). The git version control system is developed with programming in mind and is a much better storage solution compared to your standard cloud storage built for documents and other types of data. You wont become a git pro in this chapter, but you can at least get an idea for what it is.

1. To make your repository, sign-in to GitHub and click the "+" button in the top right corner, then click "[New Repository](https://github.com/new)".
![Create New Repository](/images/hosting/new-repo-menu.png)

 - That should take you to a page that looks like this:
 ![New Repository](/images/hosting/new-repo-page.png)

2. To finish creating the repository, you need to name it "**\<user\>.github.io**" where `<user>` is your GitHub username. For example, mine is named "weeser.github.io". For settings, leave the repository as "**Public**" and also check the "**Add a README File**" box. Then you can click the **"Create repository**" button at the bottom.

## 3. Configuring Page Settings

Before we make any of our web pages, we need to configure a few things on our repository because GitHub pages are not enabled by default. 

1. Open your repo's settings. The link to these can be found under your repository name. If you do not see the "**Settings**" tab, click the ... to reveal the drop down menu.
![Repository Settings](/images/hosting/settings-menu.png)

2. On the settings page, there should be a menu on the left. Under the "*Code and automation*" section, click on "**Pages**"
![Pages Settings Menu](/images/hosting/settings-menu-pages.png)

3. Now, under "**Build and deployment**", under "**Source**" select the "**Deploy from a branch**" option.
4. You can now use the branch dropdown menu to select a publishing source. For this example, select the "**main**" branch.
![Deploy from Branch](/images/hosting/pages-settings-build-branch.png)

5. You do not need to select a folder for your publishing source. It should, by default, be "**/(root)**"
![Branch Folder](/images/hosting/pages-settings-build-branch-folder.png)

6. That's it for now as far as settings go! You should see something like the following when looking at the "**Page**" settings, you should see something like the following...though note that your url will look quite different than mine since I use a custom domain. Yours should be something like "**http://\<user\>.github.io**".
![Site Live in Settings](/images/hosting/site-live.png)



