#Twitter Follow Bot

A Python bot that can automatically follow users and favorite/RT tweets associated with a specific search query on Twitter. Also has the ability to unfollow all users not currently following you back.

##Disclaimer

I hold no liability for what you do with this script or what happens to you by using this script. Abusing this script *can* get you banned from Twitter, so make sure to read up on proper usage of the Twitter API.

##Dependencies

You will need to install Python's [python-twitter](https://github.com/sixohsix/twitter/) library first:

    easy_install twitter
    
You will also need to create an app account on https://dev.twitter.com/apps

1. Sign in with your Twitter account
2. Create a new app account
3. Modify the settings for that app account to allow read & write
4. Generate a new OAuth token with those permissions
5. Manually edit this script and put those tokens in the script

##Usage

This bot has several functions for programmatically interacting with Twitter:

####Automatically follow any users that tweet something with a specific phrase

    from twitter_follow_bot import auto_follow
  
    auto_follow("phrase")
    
You can also search based on hashtags.
  
By default, the bot looks up the 100 most recent tweets. You can change this number with the `count` parameter:

    from twitter_follow_bot import auto_follow
  
    auto_follow("phrase", count=1000)

####Automatically follow any users that follow a user
    
    from twitter_follow_bot import auto_follow_followers_for_user
    
####Automatically follow any users that tweet from a specific geolocation
    
    from twitter_follow_bot import auto_follow_geo
    
    auto_follow_geo("geocode") eg. "-27.4678802490,153.0470428467,20km" latitude,longitude,radis
    
####Automatically follow any users that have followed you

    from twitter_follow_bot import auto_follow_followers
    
    auto_follow_followers_for_user("jack")

    By default, the bot looks up the 100 most recent tweets. You can change this number with the `count` parameter:

        from twitter_follow_bot import auto_follow_followers_for_user
      
        auto_follow_followers_for_user("jack", count=1000)

####Automatically favorite any tweets that have a specific phrase

    from twitter_follow_bot import auto_fav
  
    auto_fav("phrase", count=1000)
    
####Automatically retweet any tweets that have a specific phrase

    from twitter_follow_bot import auto_rt
  
    auto_rt("phrase", count=1000)

####Automatically unfollow any users that have not followed you back (with exceptions that you can set)

**Warning: If you have over 5,000 followers, the auto unfollow functionality may not work properly for you.**

I advise against using auto unfollow if you have more than 5,000 followers at this point. See [this issue](https://github.com/rhiever/twitter-follow-bot/issues/14) for more details.

    from twitter_follow_bot import auto_unfollow_nonfollowers
  
    auto_unfollow_nonfollowers()
  
You will need to manually edit the code if you want to add special users that you will keep following even if they don't follow you back.

####Automatically mute all users that you have followed (with exceptions that you can set)

    from twitter_follow_bot import auto_mute_following
    
    auto_mute_following()

You will need to manually edit the code if you want to add special users that you will not mute.

####Automatically unmute everyone you have muted (with exceptions that you can set)

    from twitter_follow_bot import auto_unmute
    
    auto_unmute()
    
You will need to manually edit the code if you want to add special users that will remain muted. 
