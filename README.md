# github-rank-project
Project to rate quality of github repositories like we vote for cool posts on hacker news.

> This Document is an ongoing work on what the project could be and how to get there.
> Feel free to fork and pull request.

Come and discuss the project with us !

[![Join the chat at https://gitter.im/gitlinks/github-rank-project](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/gitlinks/github-rank-project?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

## Meetings
We meet every Monday at 20:00 over Skype. If you are interested in joining us, feel free to ask !

## The Problem
There are tons of open-source projects out there, especially in the JavaScript community, and it is difficult to choose between project that does the same thing.

Part of the difficulty of choosing is lack of actionable intelligence on key features on a project:

* Code Quality
* Community size
* Support
* Dependencies
* Documentation

The way we do things is to google the kind of thing we want, check out reviews and comparisons written by peers and finally to look at the documentation to really assess it.

**That's tedious**

## A Solution
A solution would be to rank repositories according to some criteria that will reflect the quality of a repository. There are already metrics to get the *popularity* of a project (stars, commits, pull-requests, issues, downloads) some others to get some automatic code quality check (CodeClimate, Codacy, Coveralls ...).

The problem with those automatic tools is that the metric they produce does not guarantee any quality. You have to use a project, test it in the real world to get this kind of info. Plus code style is something opinionated.

**Sometimes the best way to do things is to make them do by humans**

A good illustration of that is [Hacker News](https://news.ycombinator.com/). The idea is that the community votes for the best news posted by peers. Peers that get their news upvoted have their karma improved. The top posts are a combination of up-votes and freshness. That way the Top news change and they represent a quality sample of what's being published out there. *Without any complicated machine learning in the background*

A solution can be to use this peer rating principle and apply it to the open source world. Having peers score repositories against some defined criteria and weight their vote with their Karma. A user's Karma gets only as good as a combination of the scores of the repositories he contributed to.

We can then add some other automatic metrics in the computing of a repository score once we have defined those relevant.

### How User Karma should work (WIP)
#### Rules
* Your Karma gets better when you contribute to a well rated project.*
* Your Karma gets lower when projects you contribute to are badly rated.*
* Looking back, people that initially rated a project accurately should be rewarded by Karma.
* **(OPTIONAL)** Karma could also be augmented by Stack-Overflow karma.

*: How much it influences your karma should be proportional to your overall contribution.

#### Score propagation
* A Karma change **should not** affect the scores that the user voted for.

### How Repository score should work (WIP)
#### Rules
* Score is base on some determined criteria evaluated by other users.
* Score can also be influenced by some key automatic metrics
* A user cannot vote for a repository he contributes to.
* Weight score with user usage of the repository. If we can detect that one user has used a project, then we should give more weight to its rating.
* We also should ask a user to review its rating 2 months or so after having rated it for the first time so that he can have a more insightful opinion on a project.
* The score of a repository should also be affected by the score in the system of its dependencies. A repository with low score dependencies should not be rated well.
* The score of a repo isn't changed if the Karma of one of the people who voted for it changes.
* For a repo, the distribution of scores for each criteria should be displayed.

#### Score propagation
* A repository score change affects all contributors immediately

#### Scoring criteria
Score criteria from 1 to 5. While scoring a user can justify for each criteria his rating in a comment.

* Documentation
* Design
* Maturity
* Support

#### Repository owner Feedback
The UI should also enable the owner of a repository to have details on why the score of his repository is what it is. He/She should also be alble to read the potenatial reviews people might have left when rating the repo.

## Technical aspects

### Technologies
Right now the technologies in the pipeline for the implementation are:

**Plateform**

* Scala
* Neo4j
* Play Framework for Scala
* Less
* Bootstrap
* Silhouette for authentication with GitHub

**Infra**

* Docker

### Propagation algorithm
Use of an actor model to propagate the score between users and repos

### Neo4J Database model
![Neo4j Model](https://docs.google.com/drawings/d/1rwcvb2adpUhAopaPPc2P3KJ6-3NBPEttNSc0vwCOH88/pub?w=1145&h=732)

We should mention that for the moment we so not get any history on the user karma and the repository score. Would the need rise, we would add a Postgres database to handle time series.

Furthermore, contributions should be merged so that only the timestamp of the last contribution and the total amount of lines added and removed by the user on the project is kept.

### Storage
Store score/karma history outside the user/repo node.

### Badge

Using shield.io to have svg badges.

![badge](https://img.shields.io/badge/gitrank%20score-3%2F5-yellow.svg)

## Repositories

* This one is the general repository project. It is where we discuss general matters of the project.
* [Gitrank-web](https://github.com/gitlinks/gitrank-web) : implementation
* [Docker-builds](https://github.com/gitlinks/docker-builds): Builds of the implementation
* [Notebooks](https://github.com/gitlinks/notebooks): algorithm prototyping with ipython notebook
