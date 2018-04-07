ThinkPad T580 impressions (with Linux)
======================================

.. NOTE:: This is not a review.
          These are various impressions after using it and is not intended to be a complete review. In
          particular, don't assume something works for me if I didn't specifically spell it out.

The following impressions are based on running Ubuntu 17.10 a
dual-battery T580 with Xorg and i3. The T580 only has
the Intel graphics (on purpose for Linux compatibility).

Changelog (significant updates only)
------------------------------------

* 2018-04-07

  * Initial version, about 3 weeks or so after receiving the laptop.

The touchpad
------------

The touchpad is physically clickable *but* it appears to use a
"hinged" design, with the hinge being on top. In other words, clicking
the very bottom of the touchpad works fine and only requires a small
amonunt of force (and it differentiates between the left/right side to
simulate left/right mouse buttons).

The further up the touchpad you go, the harder you need to press to
generate a click. The implicdation is that as you move your hand
around while moving the cursor, it's a crapshoot as to what it feels
like to click the touchpad - and if you're far up enough you end up
with a lot of "ugh the click didn't take" situations.

My only explanation for this design is that the touchpad is not
intended to be a clickable touchpad in the sense you'd expect of a
MacBook, but rather that it is intended to behave as if you had
dedicated buttons on the bottom of the touchpad (the actual dedicated
physical buttons are on top).

That is not really how I want to use a touchpad. I pretty quickly
stopped trying to get used to it, and am instead trying to get used to
the trackpoint.

TrackPoint
----------

It's a trackpoint :) The only thing I'll say is that I'm not a
traditional trackpoint user and after several weeks of use, I'm "used"
to it in the sense that I automatically use it without having to think
about it. However, at this point I'm not feeling nearly as
quick/effective/painless as a MacBook touchpad.

(If I remember I will update this in the future after more prolonged
use.)

Of course this is obviusly highly subjective.


The fact that the keyboard/touchpad isn't centered
--------------------------------------------------

This definitely irks me a lot, but I'm *mostly* okay with it. It is
legit annoying, especially when using the laptop in my actual lap,
because of the balance is off but also because there isn't as good
support for my palm/arm on the left hand side as there is on the right
hand side.

I should note that this is my private laptop, and the nature of my use
is very different than my work laptop. In particular, I don't tend to
use it constantly for 12 hours or similar things, and I do worry what
would happen if I used it more intensively.

Noise
-----

Spinning a single CPU core for several seconds appears approximately
enough to cause the fan to run at a noticable volume. I don't really
mind for most cases since I have noise canceling headphones with
music in them most of the time. However, it would be enough that I
think it will bother me to use the T580 as the chrome casting source if
watching TV w/o headphones in the living room with the laptop next to
me, for example. (This assumes the browser is streaming video;
i.e. use of chrome cast with a non-supported site.)

I would not call it terribly loud, but noticeably so. I am generally
not super sensitive to noise compared to some folks, for whatever that
is worth in terms of calibration.


Keyboard
--------

As usual with Thinkpads, the keyboard is quite good even if not as
good as the classic Thinkpads of old. The primary "annoyance" for me
compared with what I've become used to with MacBooks is that the arrow
keys are small and stuffed in with other keys making them harder/more
risky to use.

This isn't a big deal for me since all my heavy duty keyboard use
(text editing) does not involve use of arrow keys, but it does affect
certain random things where I don't have other bindings.

Battery
-------

The large cylindrical battery (which is opt-in when you purchase the
laptop) sticks out from the laptop and acts as a "foot" for the
laptop - slightly elevating the back of it. I have no problem with
this myself, but I wanted to mention it in case some folks may prefer
it flush.

In terms of battery time, all these experiences based on using Linux
and i3; other operating systems, or potentially graphically heavy
desktop environments, may see different results.

With both batteries fully charged, it appears that sitting around
idling with the screen on and reasonably (but not maximally) bright, I
can get *around* 12 hours.

Playing a typical 1080p YouTube video (without video decoding
acceleration) it's *around* 5-6 hours.

These numbers are currently based on the battery estimate given to me
by ``acpi``. I have not spent time measuring how correct they are, or
down full draining to confirm rate of reported discharge doesn't
change. That said, it feels roughly consistent with what I've
experienced when spending multiple hours off battery and keeping a
casual eye on battery levels.

Battery problems, possibly gone with BIOS update
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The behavior I observed at first was that the large cylindrical
battery would be drained first, followed by the smaller battery. This
makes sense, since one may want to use the built-in battery as the
bridge to allow a battery swap. Upon charging it would fill up the
built-in battery first, followed by the cylindrical.

I started observing some anomalies with respect to the wrong battery
draining, and the charging happening in the wrong order. Finally, I
ended up in a state where the built-in battery would just not charge,
even when drained all the way down to 37%.

After much ado, I got a USB CD drive and CDR discs, and did a BIOS
update using Lenovo's bootable CD (I had some trouble converting it
into a bootable USB stick). Sorry, I lost the exact bios version but
this was done early April or late Mars and using whatever was the
latest BIOS version at the time.

After the BIOS update, it successfully charged the smaller built-in
battery. However, after charging it fully (it was at like 99%), it
kept simmering on the built-in battery for I think even hours and I
was worried that it would never swap over and charge the larger
battery.

I left it overnight and in the morning the larger battery was charged.

I have not exercised the battery a lot, and so lack further anecdotes.


Linux compatibility and tweaks
------------------------------

I only briefly booted Windows for a few minutes, so I effectively only
have experience running Linux on this laptop.

xorg driver + avoiding screen tearing
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ``modesetting`` driver appears to be picked by default by Xorg on this
laptop, and there is signficant screen tearing noticable when doing
simple things like scrolling a web page.

A solution is to force the ``intel`` driver to be used, *and* to
enable the ``TearFree`` option (I don't know what the trade-off is;
presumably there is *some* trade-off if it's not enabled by default).

In my case, I dropped the following into a file in ``/usr/share/X11/xorg.conf.d``::

  Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "TearFree" "true"
  EndSection

Wayland
^^^^^^^

My only use of wayland has been through the default Ubuntu desktop
that uses Wayland+XWayland. Seems to superficially work, but I spent
as little time as possible in this mode until I got my i3 environment
bootstrapped.

There was no particular problem with Wayland, and I may still try it
out. However, my priority was getting my environment set up rather
than playing with Wayland. I am hopeful Wayland will work well and
that `sway <https://github.com/swaywm/sway>`__ is a good i3
replacement - I just don't know yet.


Suspend/resume
^^^^^^^^^^^^^^

I have had zero issues and have had to do zero tweaking. It appears to
"just work". Resume seems to take maybe 2-3 seconds or so.

Bluetooth audio
^^^^^^^^^^^^^^^

My use of Bluetooth audio is almost entirely for watching videos
(including YouTube) and listening to Audio (in Chrome).

My primary headset is the Bose QC35 (though I have briefly tried the
Avantree Audition as well).

I am using pulseaudio.

I have *not* tried the microphone; if you care about bluetooth audio
*input*, I can't help much.

The good news is that overall, Bluetooth works. I did not require any
tweaks w.r.t. bluetooth drivers or bluez etc (the standard ``pair X``,
``connect X`` works), but there are a few quirks/things to keep in
mind.

* In order to put the headset into the appropriate mode to get high
  quality audio, ``pacmd set-card-profile N a2dp_sink`` (whatever your
  card ``N`` is). It appears to be defaulting into a headset
  profile (where the mic theoretically works, but audio quality is
  horrible.)

* Once (but only once so far), a *huge* amount of latency built up; it
  was on the order of half a second to a second of delay. I "fixed" it
  by restarting my headset.

* During normal operation, latency is low enough that I don't
  consciously notice anything annoying. That said, I should mention
  that I haven't used this setup to watch a lot of human faces
  speaking (though I have some).

* Contrary to the behavior on macOS, the PulseAudio volume control
  does not appear to affect the hardware volume of the headset. I did
  not find a way to do this through software, but in the case of the
  Bose QC35 there are physical buttons on the headset to control the
  hardware volume. The significance of this is that software volume
  above 100% will cause distortion, and so it is important that 100%
  is sufficient volume. If you have a bluetooth headset without
  physical volume buttons, *maybe* this could be a problem. I'm not
  sure.

* Most of the time, turning on the Bose headset after having resumed
  the laptop will either (a) cause it to connect after a couple of
  seconds, or (b) require me to turn the headset back off and back on
  again and *then* connect after an additional couple of seconds.

  I have had a few cases that required more attempts. Once I spent
  almost 5 seconds restarting the headset, flipping ``scan on/scan
  off`` and doing suspend/resumes until it finally started working.

  So TLDR: As usual, Bluetooth pairing/connection is freaking
  horrible. However, it has been a bit more horrible than I'm used to
  with macOS, though not incredibly so. With macOS you have random
  issues sometimes as well, but the biggest difference is that having
  to turn the headset on and off an extra time seems to be the common
  case right now. But at least it's mostly consistent.

  I am not entirely sure what these issues are correlated with, and
  whether e.g. suspend/resume cycles make it more likely.

Battery
^^^^^^^

It's worth nothing that two separate batteries could potentially
complicate matters from a UI perspective.

In my case, I mostly monitor the battery using ``i3status`` which will
by default aggregate all batteries in the system (configurable, though
I did not try it).

But, I mention this just in case the reader may anticipate any
problems resulting from the fact that there are multiple batteries
exposed logically through ACPI.

Misc tweaks
^^^^^^^^^^^

I've done various tweaking to my environment since getting the
laptop. If interested you can check out `scode/dotfiles
<https://github.com/scode/dotfiles>`__ - in particular `i3status.conf
<https://github.com/scode/dotfiles/blob/master/dotfiles/i3status.conf>`__,
my `i3 config
<https://github.com/scode/dotfiles/blob/master/dotfiles/i3/config>`__,
my `keyboard layout
<https://github.com/scode/dotfiles/tree/master/dotfiles/xkb>`__ and my
`backlight script
<https://github.com/scode/dotfiles/blob/master/scode-overlay/backlight.py>`__.
