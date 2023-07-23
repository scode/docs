# Chrome tweaks

## More aggressive relaunch prompting for updates

TLDR:

    defaults write com.google.Chrome RelaunchNotification -int 1

This appears to work - triggering an actual pop-up and requiring restart
within a few days, thus making it harder to accidentally just forget to
restart your browser. However, I don\'t know how to make it more
aggressive. At first I wasn\'t convinced it worked, probabably because I
did not wait long enough for the pop-up to appear after the update badge
changed color. I eventually forgot about it and finally did get the
pop-up a few weeks later after another update.

More info:

-   <https://cloud.google.com/docs/chrome-enterprise/policies/?policy=RelaunchNotification>
-   <https://www.alansiu.net/2019/11/24/forcing-updates-to-google-chrome-using-chrome-preferences-a-chrome-profile/>
