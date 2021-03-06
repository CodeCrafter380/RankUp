# RankUp 1.3

A MCPE server plugin for servers running on ImagicalMine or PocketMine builds.
Player gets a higher rank as reward for voting or after some time playing on the server.
Player can also start/stop jobs.

For mcpe 0.12.1 / 0.13.1 with api 1.12.0 / 1.13.0

RankUp requires PurePerms v1.1.12 or higher on your server

##Download and Install

### [Download: RankUp.phar v1.3](https://s3-eu-west-1.amazonaws.com/devron/RankUp_v1.3.phar)


and copy the file into your plugins folder.

restart your server.

modify the config.yml

restart again

##Usage / Command

###vote / get next rank for voting

```
/vr
```
```
/voteranks
```
```
/vote
```

###check time played / time to play for next rank

own status

```
/tr check
```

status of other players

```
/tr check <playername>
```

###start / stop jobs

job list

```
/job list
```

start job

```
/job start <jobname>
```

stop job, player will reseted to his actual AutoRank Group

```
/job stop
```

##Configuration

```
# API key; Can be found on your server settings page (minecraftpocket-servers.com)
APIKey: ""

# URL where players can vote for this server;
VoteURL: ""

# list of ranks that can be reached. cutomize this with your server ranks
# ranks must have the same name like the group in pureperms
# add all groups that exists, and add the order by giving them a value from 1 to X
# where 1 is the lowest rank and X the highest
Ranks:
    Guest: 1
    rank2: 2
    rank3: 3
    rank4: 4
    rank5: 5
    job1: 6
    job2: 7
    job3: 8
    Admin: 20
    Owner: 50
    OP: 100

JobRanks:
    job1: 5
    job2: 5
    job3: 5

# the fallback rank if a player stop the job, for cases where players
# reached a rank by voting but dint reached the required time in autoranks
JobStopFallback:
    id: 5
    title: "rank5"

VoteRanks:
    Guest: 1
    rank2: 2
    rank3: 3

# time to reach this rank, ranks must have the same name like in pureperms
AutoRanks:
    Guest: true
    rank1: 20
    rank2: 60
    rank3: 120
    rank4: 240
    rank5: 720

#messages
Messages:
    command-in-game: "Command must be used in-game."
    error-fetching-vote: "[RankUp] Error fetching vote status! Try again later."
    no-permission: "You do not have permission to vote."
    pureperms-loaded: "Successfully loaded with PurePerms"
    pureperms-notfound: "Dependency PurePerms not found"
    rank-new: "You are now rank ##rank##"
    rank-failed: "RankUp failed with rank: ##rank##"
    vote-nextday: "You've already voted today! Come back tomorrow to vote again."
    vote-success: "##player## voted with /vote and got a higher rank!"
    vote-open: "You haven't voted yet!\n +++ ##voteurl## +++ \nVote to get higher rank!"
    timer-usage: "Use /tr check ##player##"
    timer-neverplayed: "Player ##player## never played on this server"
    timer-newplayer: "##player## has played less than 1 minute on this server"
    timer-newrank: "##player## reached new Rank: ##rank##"
    timer-rankis: "Rank is: ##rank##"
    timer-timeplayed: "You have played ##timeplayed## minutes on this server.\n ##timetoplay## minutes until next rankup"
    timer-timeplayer: "Has played ##timeplayed## minutes on this server"
    job-list: "You can choose one of this jobs: ##joblist##"
    job-choose: "Please choose one of the jobs: ##joblist##"
    job-rank-low: "You can't choose this job, your rank is to low"
    job-rank-error: "Upps there is an ERROR, try again later"
    job-usage: "list jobs: /job list\nchoose job: /job start <jobname>"
    job-no-stop: "You do not have a job to stop, use /job start <jobname> to start a job"
```

##Permissions

```
permissions:
    voteranks.command:
        description: "rankup a player as vote reward"
        default: true
    timeranks.command:
        description: "check time to play for next rank"
        default: true
    jobranks.command:
        description: "list or choose jobranks"
        default: true
```