---
permalink: /icpc24
layout: page
---

{% include main_title.html text="ICPC Team Local Qualifier 2024" %}

If you are interested in competing in the ICPC contests in 2024, the
local qualifier will happen this **Friday October 25 at 5:00pm**
and it will take place in **Friend Center 004**. This will consist of
a 2.5-hour teamed contest (so it finishes at 7:30pm) which will be
held on CodeForces. Try to show up before 5pm so you can have time to
setup, since the contest will start at 5pm sharp.

To sign up to compete please see the notice on the announcements
channel on discord or contact [Pedro
Paredes](https://www.cs.princeton.edu/~pparedes/)
(pparedes_at_cs.princeton.edu).

## Contest Information

From the best ranked participants in the local contest, we will be
forming teams to represent Princeton in the Greater NY Regional
Contest, which will take place **Sunday, November 10**. Do not sign up
to participate in the local qualifier unless you are planning on
attending the regional contest. See the section below on ICPC
qualification for information about how the teams will be formed.

This year the regional contest is going to be "siteless", so our
Princeton teams will participate in the competition from Princeton
(the building and room are TBD). You can see more info
[here](https://gny.na.icpc.global/)).

## Contest Rules

Please read these carefully.

* You need to be registered in order to be eligible to advance to the
  ICPC regional. To do so, please see the notice on the announcements
  channel on discord or contact [Pedro
  Paredes](https://www.cs.princeton.edu/~pparedes/)
  (pparedes_at_cs.princeton.edu).

* The contest will take exactly 2 hours and a half. In the event of a
  prolonged codeforces outage (which is rare, but unfortunately happens),
  an extension might be granted to everyone. No extensions will be
  granted in case of lateness (so try to be on time).

* The contest is individual, so you will participate on your own. You
  are not allowed to communicate with anyone, even if you are planning
  to eventually form a team with them for the regional.

* You are allowed to use any code you have stored locally, which
  includes solutions you wrote up to previous problem, implementations
  of data structures or algorithms, or any code templates. However,
  you are not allowed to search the internet for anything. You are
  also not allowed to use chatGPT or GitHub Copilot (or any LLM tool,
  running locally or on the internet) to generate any type of code.

* There will be 7 problems of ranging difficulties, which can be in
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

* You will be able to see the scoreboard through out the contest,
  except for the last hour. During this last half hour the scoreboard
  will be shown as "frozen" and it won't be updated. Obviously your
  submissions will still count, but you won't be able to see them on
  the scoreboard. The ranking will be revealed shortly after the time
  is up.

## ICPC Qualification

From the best ranked participants in the local contest we will be
forming (at least) 10 teams to participate in the official ICPC
regional contest.

To form teams we will use the following "draft" process, which will be
based on the results of this local qualifier.

```
eligible_pool = {participants with >= 1 solved problem in the local qualifier}
icpc_teams = {}

while icpc_teams.size < 10:
  drafter = eligible_pool.get_highest_ranked_contestant()
  team = drafter picks 2 other people currently in eligible pool (regardless of rank)
  icpc_teams.add(team)
  eligible_pool.remove(team)
```

So in summary, the highest ranked contestants get to pick their team
(as long as the other members want to be in that team, if not, they'll
have to pick someone else). Because of the tight ICPC deadlines, this
process will have to be run quickly, we will need to have the teams
decided by November 5.

I am hoping that this will basically mean that everyone gets to pick
their preferred team, but doing this as a draft makes the process
fairer to contestants that don't have a team yet. So feel free to have
teams in mind before the contest.

## Contest Instructions

Please follow these carefully.

* The contest will be on the [Princeton ICPC
  Group](https://codeforces.com/group/hNnRWqFua0/contests) as
  "Princeton ICPC Selection Contest 2024-25", and it will show up
  there around an hour before the competition starts.
  
* To participate in the contest you will need to register on
  codeforces. Once the contest is up, click the register button on the
  [Princeton ICPC
  Group](https://codeforces.com/group/hNnRWqFua0/contests).

* Looking at the problems and submitting solutions will work exactly
  like the usual weekly problem solving sessions.

If you have any questions ask [Pedro
Paredes](https://www.cs.princeton.edu/~pparedes/)
(pparedes_at_cs.princeton.edu) for help.