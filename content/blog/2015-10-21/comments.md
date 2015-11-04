+++
Categories = ["website"]
Tags = ["code"]
date = "2015-10-21T20:27:03+01:00"
title = "Adding Comments"
image = "/images/thumbnail.png"
imagealt = "Website Thumbnail"


+++

I mentioned in my last website post that I needed to add a way to get feedback into my site. In the end 
I went for adding comments over getting my build/deployment process over to github. I'm sure that'll be 
next as the deployment process is more than a little clunky.


In the end I've gone with [disqus](https://disqus.com). I'm not a fan of just jumping on the bandwagon 
of the biggest player so I did look around but in the end I returned back to disqus. If you want to know
which solutions I considered etc read on.


**TL;DR**


A quick google search came up with:

* disqus
* disclosure
* mutt

  
All of which seem to fit the bill. A quick google for comparisons didn't really show any real differences 
between the major players. All of them seem to be heavily integrated (i.e. facebook login etc) none of the 
sort of features which really interest me.


### Cowments


After more searching I came across [Cowments](http://cowments.com) which looked promising. I went ahead 
and setup an account. It seems to be a hybrid where you configure the form (Allowing you complete control 
over styling) and then a Javascript include (like disqus) that imports the comments for you.


I spend a little time getting it up and running and change the form styling and load up on my development 
instance running against localhost. This is where it starts going down hill. It doesn't look like Cowments 
supports a localhost host environment.


I go ahead and make what I think are the required changes and then go through my clunky deployment process.
I then check my live site and it's not working... I try and submit a post and I get an error in Chrome's console
"Bad Gateway" I think but essentially an error 4XX.


That's it time to throw it away. Bad citizen or what, if it was open source project I'd have at least ensured 
there was a issue on github. It's closed source so it's not an investment I'll make.


### Where next?


The theme I've used for [Hugo](http://gohugo.io) is hacked from the [polymer theme](https://github.com/pdevty/polymer)
which already has disqus support built in. Not to waste any more time (It's not like anyone's using it yet) I created
a disqus account and configured it on the site. Removing it from the pages it shouldn't appear on etc.


Anyway it's up and running let's see how it goes.
