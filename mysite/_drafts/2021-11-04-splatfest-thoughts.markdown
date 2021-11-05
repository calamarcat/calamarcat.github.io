---
layout: post
title:  "Splatfest Thoughts"
date:   2021-11-04 01:08:44 +1000
shortdate: 2021-11-04
categories: [splatoon, tournaments, events, organisation, splatfest]
excerpt_separator: <!--more-->
---

Oceanink recently ran a week-long Splatfest event for charity, with the help of Martin from Atlassian. The event raised $2300 for Sydney Childrens Hospital's Fund (SCHF), which was later doubled by Atlassian. To do this, we ran a couple of Splatfest sessions for the divise debate Martin had come up with - Meat Pie vs Sausage Roll.

It was a lot of fun to run, and also quite novel for me as I hadn't run a Splatfest before. So, I figured why not write down some of the discussions we had when organising it, and the decisions we made, in case they help anyone looking to run their own Splatfest in the future.
<!--more-->

# Splatfest Team Voting

## Standard Teams
The gimick of Splatfests is, of course, that there are sides to vote for, and your match wins go towards helping your side win the event. In Splatoon, to play in a Splatfest with friends you have to find 3 other people who have voted for the same side. This makes it easy to calculate how wins affect the Splatfest results - either you have: 

- two teams who voted for different sides playing against each other (i.e. "head to head" matches), and the result affects the Splatfest result
- two teams who voted for the same side (i.e. a "mirror match"), in which case the result isn't as important for the Splatfest result

The latter - mirror matches - can also be less exciting to players, because the matches aren't as important to the goal of the Splatfest. Unfortunately, unless you manage to get exactly the same number of teams on each side, or you make some of the teams on the less-popular side play extra matches, you can not avoid mirror matches.

## Mixed Teams
There is a third option for forming Splatfest teams for community-run Splatfest events though: allowing mixed teams. That is, individuals vote for their side and then can play with whoever they like. This means you may get teams where 2 people voted for one Splatfest side and 2 voted for the other, or even a 3:1 split, which can make calculating results a little more interesting. However, when organising the recent Oceanink Splatfest event, I had a theory:

> Players might be more keen to enter, and might enjoy the event more, if they were able to play with any of their friends without having to worry about Splatfest sides.

Without a decent number of teams, any event can be underwhelming, so target audience and limitors to entry are always important to consider. Higher registration numbers are especially important right now though, due to the community being less active at this point in Splatoon 2's lifecycle (that is, Splatoon 2 has been out for *a while* and we know Splatoon 3 is coming). It was also just a fun twist on the Splatfest format that we wanted to try out too. 

One quirk of this format is that you no longer just have head to head and mirror matches - you also have mixed matches. For example, a team who all voted for side A could go up against a team that's half side A and half side B. How then do you calculate how the result of that match affects who wins the Splatfest? I'll explain how we did this below, along with some other options.

# Calculating the Winning Side
There are a few ways you could calculate who won a Splatfest, and some of it depends on factors not discussed in this article, but I'll link those separately. 

First, to explain how Splatoon itself runs Splatfests. The Inkipedia wiki article is a pretty good resource if you want to read more. However, I want to particularly highlight how mirror matches affect the Splatfest result:

> Mirror matches: If the game can't find an enemy team in time, teams of the same side will battle each other. Prior to Version 4.0.0, **the win was not counted when tallying up the results**. After 4.0.0, the Clout system was added, which also **does not award Clout for mirror matches**. This is likely done to avoid giving an advantage to the more popular side, as they are more likely to have mirror matches.

That is: they don't. 

## Calculating for Standard Teams
So for a Splatfest that uses the standard team model, we have two options:

1. Count wins as points towards the side's total, regardless of if it's a mirror match or not
2. Only count wins as points towards the side's total if they aren't mirror matches

The first is easier, but you have the issue that if one team is much more popular than the other, that will bias the points from wins. The second is a little harder, but it's not too bad. Let's look at some examples. 

First, assumptions:

- We have Splatfest sides A and B
- We using a nebulous "wins" concept - that could be matches won or rounds won depending on your format, but we're not accounting for that right now
- Everyone plays an equal number of matches

Say we have five teams that play a Round Robin bracket that looks something like this:

![Bracket example](/assets/images/2021-11-04-splatfest-thoughts_rr-example.png)

*Bracket generated using [BracketHQ](https://brackethq.com/maker).*

Then we might get results something like this:

| Team    | Side | Head to head wins | Mirror matches | Head to head losses |
|---------|------|-------------------|----------------|---------------------|
| Alpha   | A    | 3                 | 1              | 0                   |
| Beta    | A    | 0                 | 1              | 3                   |
| Gamma   | B    | 2                 | 2              | 0                   |
| Delta   | B    | 1                 | 2              | 1                   |
| Epsilon | B    | 2                 | 2              | 0                   |

Note that the "Mirror matches" column doesn't account for whether those matches were won or lost - they don't count towards the Splatfest result, so we ignore them. Why include mirror matches and head to head losses then? Because I'm pedantic, and I like having all the numbers to check my math. (^-^;;)

So the total head to head wins for each side are:

- Side A: 3 + 0 = 3
- Side B: 2 + 1 + 2 = 5

Therefore, Side B wins. 

An alternative set of results for this event: 

| Team    | Side | Head to head wins | Mirror matches | Head to head losses |
|---------|------|-------------------|----------------|---------------------|
| Alpha   | A    | 3                 | 1              | 0                   |
| Beta    | A    | 1                 | 1              | 2                   |
| Gamma   | B    | 0                 | 2              | 2                   |
| Delta   | B    | 1                 | 2              | 1                   |
| Epsilon | B    | 2                 | 2              | 0                   |

Total wins are:

- Side A: 3 + 1 = 4
- Side B: 0 + 1 + 2 = 3

So, Side A wins in this case.

But what if we did count mirror matches? Let's see an example using the first example above, but with mirror matches added in:

| Team    | Side | Head to head wins | Mirror match wins | Mirror match losses | Head to head losses |
|---------|------|-------------------|-------------------|---------------------|---------------------|
| Alpha   | A    | 3                 | 1                 | 0                   | 0                   |
| Beta    | A    | 0                 | 0                 | 1                   | 3                   |
| Gamma   | B    | 2                 | 2                 | 0                   | 0                   |
| Delta   | B    | 1                 | 1                 | 1                   | 1                   |
| Epsilon | B    | 2                 | 1                 | 1                   | 0                   |

How does this change the scores? Well, if do we head to head wins + mirror match wins for each side...

- Side A: (3 + 0) + (1 + 0) = 4
- Side B: (2 + 1 + 2) + (2 + 1 + 1) = 9

4:9 is a rather different score to 3:5. The same side still won overall, but the affect of counting mirror matches would grow as you increase the number of teams and the different between the number of teams who voted for each side.

What if we add the same mirror match results to our example when Side B lost?

| Team    | Side | Head to head wins | Mirror match wins | Mirror match losses | Head to head losses |
|---------|------|-------------------|-------------------|---------------------|---------------------|
| Alpha   | A    | 3                 | 1                 | 0                   | 0                   |
| Beta    | A    | 1                 | 0                 | 1                   | 2                   |
| Gamma   | B    | 0                 | 2                 | 0                   | 2                   |
| Delta   | B    | 1                 | 1                 | 1                   | 1                   |
| Epsilon | B    | 2                 | 1                 | 1                   | 0                   |

- Side A: (3 + 1) + (1 + 0) = 5
- Side B: (0 + 1 + 2) + (2 + 1 + 1) = 7

This time, counting mirror matches has switched which side wins.

### Is it ever safe to count mirror matches?

Yes - when either the number of teams for each side is very, very close (preferrably 50% of course) and/or the difference in final points (i.e. combined wins of all teams on each side) is so large, it isn't possible for the result to be changed based on if you counted mirror matches or not.

### Adding popularity, etc.
Of course, the other caveat here is that Splatfests aren't often decided just on wins. Splatoon 1 used a formula to account for popularity (how many players voted for a side), while Splatoon 2 was decided by a best-of-3 situation - whoever won the most of the following won the Splatfest overall:

- Popularity
- Normal Mode Clout
- Pro Mode Clout

With the Splatoon 1 system, miscalculating the wins (e.g. by including mirror matches) could have more of an affect on the results. If you do something like the Splatoon 2 system though, where this is multiple win conditions, then it may not matter as much. 

For example, for the Oceanink Splatfest we used the following since it was a charity event where people could also donate to vote for a side:

- Popularity
- Wins
- Donations

In the end, for our event, one side won all three categories. So technically, if we'd messed up counting wins, it wouldn't have mattered to the overall Splatfest result anyway.