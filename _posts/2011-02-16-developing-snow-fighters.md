---
layout: post
title: Developing Snow Fighters
date: 2011-02-16 22:02
author: spdenne
comments: true
---
I’ve had a lot of fun in the last few weeks developing code as part of the ACM Queue
[2011 ICPC Challenge](http://queue.acm.org/icpc/) also known as the Icy Projectile Challenge.
There are a lot of ideas that I never had time to investigate,
but I thought I’d blog about the ideas I did investigate.

<!--more-->

As I write this, I’m waiting for the tournament phase to run, so have no idea how well I’ve done. Quite early on in
the competition, I had tried out the submission process, uploading minor changes to the example hunter game, so I had
competed is as many preliminary rounds as anyone else, and had won 59 of the 78 of the randomly selected preliminary
round matches, including 23 of the last 27, so I think I’ve got a good chance of doing well.

## The Game

The game is basically a snow fight between two teams of four players, looking out for the trees. You write code to
control one team, deciding what to do each turn, for 180 turns.

There were two ways of scoring points in the game, the first is by throwing snowballs at opponents, and the second is
by building snowmen to increase your domain. Snowmen can be destroyed, or your opponents can build snowmen close by,
both of which reduce your domain score, and it is only the domain at the end of the game that matters (except for
extremely rare tie breaker scenarios).

## Strategy and Development History

Sample code was provided for three example teams. Each example had all four players executing a single strategy, pretty
much independently. There was a team that build a protective snow fort, stock piled snow balls, and threw them at any
opponent that came close. There was a team of players that ran around trying to build snowmen, and there was a team of
players that ran around throwing snow balls at opponents.

I started by adapting the snowman maker and the hunter examples into strategies that individual team members could
adopt, and found that three hunters with one snowman maker seemed to work quite well.

I set about improving the strategies, concentrating first on the hunter, till I had code in the basic structure:

1. Each of 4 “Player” objects have a “Strategy”
2. “Game” controller that sets up the 4 players, each with their specific strategy. Then repeatedly:
   * Reads game state input,
   * Determines who can throw snowballs at what,
   * Asks each of 4 players to determine their move
   * If there are combination of players that have said they could use a snowball, and players who say they’re willing to give up a snowball, and the throw is possible, do that
   * Picks a run destination for players who don’t have anything better to do, repeating till the player can follow the shortest (simple) path to:
     * Closest uncharted territory,
     * Closest unsighted territory,
     * Random location
   * Report each player’s move
3. Profit

Hitting an opponent gets 10 points that can’t be taken back, and as an added bonus dazes the opponent for 4 turns.
Building a snowman in a good position is worth up to 193 points, but can be easily undone by the opponent.

The three hunter team members ended up attempting the following actions:

1. Finish a snowman that they’re standing next to.
2. Avoid being hit by a likely throw from an opponent.
3. Throw a snow ball at an opponent.
4. Take the head off an opponent’s snowman.
5. Pick up a snow ball.
6. Throw a snow ball at an opponent’s snowman.
7. Create a snow ball.
8. Stand up.

When none of those were appropriate, the game controller would send the player running off to explore.

I improved the hunters to divide the targets amongst the players, and to not throw multiple snowballs at the same
opponent, since each hit sets the dazed count back to 4, when there was a good chance that a new opponent would come
into range and be able to be dazed next turn (particularly at the start of the game when the opponents first meet).

The throw calculation was extended to examine every possible throw, from each player, seeing what could be hit, rather
than trying to calculate the best throw in order to try and hit a specific target.

I then improved my snowman builder, improving both determining the optimal places to build, and the actual build
process.

If the opponent was seen to be moving, I estimated their next movement, and considered where they were likely to be
when a thrown snowball might hit them, and also changed the targeting code to prefer the furthest throw (from each
player) that would hit an opponent, rather than the first or last found.

I think that was the last submitted state.

## Snowman Difficulties

The best place to build a snowman is right where an enemy snowman is, since it only takes two moves (once crouching):
picking up their (snowball) head, and putting it back again. The domain change is at best -193 and +193 to me, for a
differential of 386 in 2 turns… why would you bother spending 3 turns to make and throw a snowball for a measly 10
points?

I tried multiple snowman makers, who’d take pot-shots at the enemy too, but they all decided on the same spot to try
building snowmen, and got in each other’s way.

I tried getting them to build in different spots, by allocating locations in turn, removing the area round each new
location from consideration, but this wasn’t optimised, nor terribly good. In order for them to not be pummelled by
the enemy (code for my previous submissions), they needed to be carrying around a snowball, which they’d need to drop
when they started building. It wasn’t working out very well for them.

I tried specialising the snowman making players, having two hunters, and one player that makes the snowman base and
head, while the last player makes the snowman’s middle. However that was twice as susceptible to long delays in
building, since either player could get hit and dazed.

I tried to figure out the best player each turn to be a snowman builder, thinking that when one player is hit, another
can take over, and that as soon as a snowman is built, the player who just built it is better off becoming a hunter, and
someone else is more likely to be close to a better spot for building a snowman… and that’s where I started running
into bugs.

Specifically, I’d have 2 players fighting to be the snowman maker. If one was chosen as a fighter this turn, it’d
crouch to make themselves a snowball. If chosen as the snowman it’d stand to run to the best place to build the
snowman. However the “best” player – new snowman location combination kept switching to the player who was
crouching, so I had two players who were ignoring the fight, and pretending they were on a virtual see-saw.

## Route Finding

I thought that the reason for the flipping of best snowman making player was due to the different path a standing
person follows from that which a crouching person follows. The first time I took a good look at the situation, the
closer player to the best spot was crouching next to a hedge, and I presumed that the crawling path would go along the
hedge and the running path would try and fail to go through the hedge, so that player was good, was picked, would stand,
and not be able to move to the best location, but another crouching player who was further away could get there, and
roles would switch.

I had also had in the back of my mind that the simple arrangement of trees in the examples might not be so simple in
the tournament, so I spent a long Sunday evening coding a variety of path finding algorithms. I implemented
[Floyd-Warshall](http://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm) first (here is a
[applet](http://students.ceid.upatras.gr/~papagel/project/kef5_7_2.htm)), since I needed to know path distances between
a large combination of points, but it takes far too long to calculate. 
I then implemented [Hadlock’s algorithm](http://cadapplets.lafayette.edu/HadlockRouter/HadlockRouter.html), which was fast enough, but still had the
strange flip-flopping behaviour! I then identified that I had a bug where I calculated the potential benefit of a
snowman location; I was accidentally ignoring the path distance for each player, so crouching players were better, not
because of any path restrictions, but because they were one move closer to picking up snow.

Once I’d got that fixed, I played against a number of my previous submitted players, but lost badly on more maps than
I narrowly won on, so instead of submitting my new code, I decided to go with the previous code, and went to sleep.

## Postscript

I’ve since found and squashed more bugs in my path finding algorithm, and I had only been using it to determine the
distance - my players were still moving according to the much simpler path rules.

One interesting thing is that a really minor weighting change on whether one action is better than another, can affect
a single move, and the entire game after that is different, often with a large difference in who gets pinned down and
pelted with snowballs, instead of running around switching heads of opponents snowmen, and consequently a very large
difference in scores.

The best player in the preliminary rounds appears to be winning in the prisoners dilemma stakes… by assuming a newly
seen opponent able to throw at it will do so, and he’ll try and catch the throw, end up with two snowballs, and throw
one right back the next turn. My strategy was to likewise assume such a throw from an opponent, and dodge sideways if I
thought the dodge would work. Unfortunately dodging was pretty rare, and I think I should probably have tried to catch
first too.

## Competition Results

I hope to edit this post and write something about the actual tournament when it completes.
