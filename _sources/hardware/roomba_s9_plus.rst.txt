Roomba S9+
======================================

.. NOTE:: This is not a review. It is additional information that I was not able to find
	  prior to purchase.

Learning behavior and room labeling
-----------------------------------

As advertised, the Roomba needs to learn your space before it will allow you to map out different
rooms and have it go to specific rooms to clean. This can be more frustrating than first apparent,
the more so the larger your living space is. The following experience is for a living space
slightly over 2000 square feet.

First, be aware there is a dedicated mapping mode. The dedicated mapping mode causes the roomba *not*
to run the vacuum; instead it will just navigate around the space. This is supposed to be a little faster
than vacuuming per documentation. However, unless your living space is small enough for charging not to
matter, the biggest difference lies in avoiding charging. In our case, a mapping run of the entire
apartment took 6-8 hours, including one charging session. Had we attempted to let it finish a normal
"clean all" run it would have taken more than twice as long just from charging, which would have meant
more than reasonable day and would have been untenable.

The Roomba is documented to require 2-3 complete runs before an initial map is made, which allows you
to begin labeling rooms and clean individual rooms.

In our case, we suspect we encountered a bug on our first attempt - possibly due to the first mapping
run being cut short due to the Roomba getting stuck while we were away and us not making it back in time
to avoid the Roomba cancelling the job entirely. After that partial run + 3 additional we still didn't
get a map, and decided to have the roomba forget the map entirely and restart from scratch. After we
did, it completed mapping in 2 mapping runs.

Be aware that the Roomba, when it encounters a problem such as beeing stuck, requires human intervention
within a certain amount of time (I think it's like an hour and a half) before it automatically cancels the
job. This can prove difficult when your goal is to finish a complete run end to end without cancellations,
unless you're home for the entire stretch of the run (6-8 hours in our case).

All in all it took us about a week of having the roomba run every day for 6-8 hours w/o cleaning, before
we finally had a map covering the entire living space and we could start running actual vacuum runs.

Can you break up a cleaning run or does it have to finish all in one go?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Documentation is silent on this matter, but my best estimate is that the answer is
*no*. At least not reliably. From what I can tell, if you cancel a mapping run or a
clean all run, it'll just start fresh as if the prevous run didn't happen. There is
evidence that it still stores and remembers whatever it saw while it was out, but
I have not seen any evidence that it will "resume where it left off" in terms of
navigating the apartment.

Can you complete initial mapping in a smaller area and add rooms later?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This would be great, as it would avoid needing to finish the entire area in
a single uninterrupted run multiple time. From what I can tell though, this
does not appear to be supported but I can't be sure. Let me elaborate.

The documentation and other information online is a slittle conflicting,
with some accounts claiming it will keep learning after initial mapping
and others saying the opposite.

From observations, there is definitely *some* amount of learning that goes
on after initial mapping. For example, if upon mapping you had a giant box
in the middle of the room the Roomba might conclude there's a wall/pillar
there. After subsequent runs without the box, it will update the map realizing
that there is open space (but it may take multiple runs). You can tell this is
happening because the visualization of the map in the app updates clearly
showing changes like this.

However, I tried opening the door adjacent to a room already within the mapped
area. I would tell the roomba to clean the adjacent room, and I was hoping it
would find its way into said room and expand the map. While it *did* enter the
room a little (maybe 1-2 meters in and back), it did not keep exploring the
room in its entirety. The map also did not expand to include that room. I
speculate that there may be a limit to how far the roomba is willing to go
beyond its previously mapped area. It's also possible it needs to encounter
the new room multiple times before concluding it exists and updating
the map.

Because experimenting takes a *lot* of time, and as described we suffered
an entire week before finally getting our area mapped, I don't have a lot of
data to share here. It's possible that had I been patient and repeated the process
a few times, it would have eventually mapped out the new space entirely - I
can't know for sure.
