---
permalink: /icpc25
layout: page
---

{% include main_title.html text="ICPC Team Local Qualifier 2025" %}

If you are interested in competing in the [ICPC contests]({{ site.baseurl
}}/icpc) in 2025, the local qualifier will happen **Friday October 24 at
5:00pm** and it will take place in **Friend Center 004**. This will consist of a
2-hour contest (so it finishes at 7pm) which will be held on CodeForces. Try to
show up before 5pm so you can have time to setup, since the contest will start
at 5pm sharp.

We will be selecting up to 18 students to represent Princeton at the ICPC
Greater NY Regional on **Sunday, November 9** (details about it below).

To sign up to compete please fill out the Sign-Up Google Form, which you can
find in the announcements channel on discord, or contact [Pedro
Paredes](https://www.cs.princeton.edu/~pparedes/) (pparedes_at_cs.princeton.edu)
if you are not on Discord and you wish to participate. If you want to go to the
regional, but you have a hard conflict with the local qualifier date, please
contact Pedro ASAP

## Contest Information

From the best ranked participants in the local contest, we will be forming teams
of 3 to represent Princeton in the Greater NY Regional Contest, which will take
place **Sunday, November 9** at Columbia University. Do not sign up to
participate in the local qualifier unless you are planning on attending the
regional contest. See the section below on ICPC qualification for information
about how the teams will be formed.

The university will cover the travel expenses and the registration fee for all
teams. You can find more information about the regional
[here](http://acmgnyr.org/year2025/).

## Contest Rules

Please read these carefully.

* You need to fill out the Sign-Up Google Form in order to be eligible to
  advance to the ICPC regional. You can find in the announcements channel on
  discord, or contact [Pedro Paredes](https://www.cs.princeton.edu/~pparedes/)
  (pparedes_at_cs.princeton.edu) if you are not on Discord

* The contest will take exactly 2 hours. In the event of a prolonged codeforces
  outage (which is rare, but unfortunately happens), an extension might be
  granted to everyone. No extensions will be granted in case of lateness (so try
  to be on time).

* The contest is individual, so you will participate on your own. You
  are not allowed to communicate with anyone, even if you are planning
  to eventually form a team with them for the regional.

* You are allowed to use any code you have stored locally, which
  includes solutions you wrote up to previous problem, implementations
  of data structures or algorithms, or any code templates. However,
  you are not allowed to search the internet for anything. You are
  also not allowed to use chatGPT or GitHub Copilot (or any LLM tool,
  running locally or on the internet) to generate any type of code.

* There will be 6 problems of ranging difficulties, which can be in
  any order of difficulty (so problem A might **not** be the
  easiest). These are not original problems, they are taken from other
  public contests available online, so you are not allowed to try to
  find any information about the original contest.

* Unlike the usual weekly competitive programming sessions, you should
  not ask other people for help, nor will you be allowed to look at
  test cases you are failing. You will be 100% on your own. Please do
  report any issues you find, though.

* The standings will be determined as follows: first number of
  problems solved (more is better), tie breaking by the sum of the
  number of minutes taken to solve each problem plus 20 extra minutes
  per incorrect submission to an accepted problem (less is better),
  which is the default CodeForces ranking method.

* You will be able to see the scoreboard throughout the contest, except for the
  last 30 minutes. During this last half hour the scoreboard will be shown as
  "frozen" and it won't be updated. Obviously your submissions will still count,
  but you won't be able to see them on the scoreboard. The ranking will be
  revealed shortly after the time is up.

## ICPC Qualification

From the best ranked participants in the local contest we will be forming (at
most) 5 teams of 3 contestants each to participate in the official ICPC regional
contest.

To form teams we will use the following "draft" process, which will be
based on the results of this local qualifier.

```
eligible_pool = {participants with >= 1 solved problem in the local qualifier}
icpc_teams = {}

while icpc_teams.size < 5:
  drafter = eligible_pool.get_highest_ranked_contestant()
  team = drafter picks 2 other people currently in eligible pool (regardless of rank)
  icpc_teams.add(team)
  eligible_pool.remove(team)
```

So in summary, the highest ranked contestants get to pick their team
(as long as the other members want to be in that team, if not, they'll
have to pick someone else). Because of the tight ICPC deadlines, this
process will have to be run quickly, we will need to have the teams
decided by November 1 (so you'll have about a week).

I am hoping that this will basically mean that everyone gets to pick
their preferred team, but doing this as a draft makes the process
fairer to contestants that don't have a team yet. So feel free to have
teams in mind before the contest.

I will share the list of eligible contestants one day after the local qualifier.
Note that list of eligible contestants might include a few exceptions from
students with hard conflicts with the qualifier date. These students will have
the lowest rank, but they are eligible to be picked into teams in the draft
process.

## Contest Instructions

Please follow these carefully (preferably at least one day before the contest
date).

* To participate in the contest you need a [codeforces](https://codeforces.com)
  account. If you don't have one, click on the link and then click on *Register*
  in the top right corner and fill out the required details.

* You will also need to be in the Princeton ICPC group on codeforces. To join
  this group, go to the following
  [link](https://codeforces.com/group/hNnRWqFua0/) and click on the *join*
  button on the right.

* The contest will be on the [Princeton ICPC
  Group](https://codeforces.com/group/hNnRWqFua0/contests) as "Princeton ICPC
  Selection Contest 2025-26", and it will show up there around an hour before
  the competition starts. Click on the register button once the contest is up.

* Looking at the problems and submitting solutions will work exactly
  like the usual weekly problem-solving sessions. See our [intro
  guide](https://competitive-programming.cs.princeton.edu/intro_guide)
  if you are not familiar with this process.

If you have any questions ask [Pedro
Paredes](https://www.cs.princeton.edu/~pparedes/)
(pparedes_at_cs.princeton.edu) for help.