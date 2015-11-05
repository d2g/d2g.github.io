+++
Categories = ["website"]
Tags = ["code","gohugo","continuous deployment"]
date = "2015-11-04T20:26:59Z"
draft = false
title = "Continuous Deployment"
image = "/images/thumbnail.png"
imagealt = "Website Thumbnail"

+++

As I mentioned before I found the whole deployment process for Hugo rather clunky. The advantage of WordPress and co is that you can deploy content changes without too much hassle.

A quick google doesn't really bring up anything that fits my use case. I don't use S3 etc I'm still have a classic old school webhosting with [ukhost4u](http://www.ukhost4u.co.uk).

Time to roll my own...

### Hugo Continuous Deployment (Github -> Codeship -> FTP to Website)

1. Webhost Setup

You need an FTP username & Password that will be used to send the generated HTML files to your website. Make sure when it logs in the directory it starts you in is where you want your files delivered.

2. Github Setup

Setup your github repository to contain all the files you require (this includes your theme etc). The one for this site can be found [here](https://github.com/d2g/d2g.org.uk).

2. Codeship Setup
    * Next get yourself over to [Codeship](https://codeship.com) create an account. 
    * Then create a new project. Select connect with Github Repository.
    * Select the repository which contains all the files needed by Hugo.
    * Scroll down and delete the test pipeline..
    * In "Setup Commands" enter 
```
go get -v github.com/spf13/hugo
hugo -b http://www.d2g.org.uk/ -t polymer
```
Replacing `http://www.d2g.org.uk/` with your URL and `polymer` with your template.

* Save the page and you'll be greeted with a page asking you to push to your repository to trigger a build. Ignore that for now.
* Select Project Settings -> Deployment
* Select `Branch is exactly` and type `master` and Save Pipeline settings
* Select Custom Script
* Enter the deployment command `lftp -c "open -u $FTP_USER,$FTP_PASSWORD ftp.d2g.org.uk; set ssl:verify-certificate no; mirror -R ${HOME}/clone/public/ ."` replacing ftp.d2g.org.uk with your FTP server address. Press Create/Save.
* Select Environment in the Menu
* Add two variables:
  * Key: `FTP_USER` Value: The FTP user for your Webhost (From point 1).
  * Key: `FTP_PASSWORD` Value: The FTP password for your Webhost (From point 1).
* Save Changes
* Click on the project name / github name in the top left. You'll be back at the page asking you to push to trigger a build.
* Push a change, you should see the codeship deployment process running and it deployed directly to your website.
 
Now you can deploy directly from github.

Enjoy.
