# github-rank-project
Project to rate quality of github repositories like we vote for cool posts on hacker news.

> This Document is an ongoing work on what the project could be and how to get there. 
> Feel free to fork and pull request.

Come and discuss the project with us !

[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/callicles/github-rank-project?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

## The Problem
There are tons of open-source projects out there, especially in the javascript community, and it is difficult to choose between project that does the same thing.

Part of the difficulty of choosing is lack of actionnable intelligence on key features on a project:

* Code Quality
* Community size
* Support
* Dependencies
* Documentation

The way we do things is to google the kind of thing we want, check out reviews and comparisons written by peers and finally to look at the documentation to really assess it. 

**That's tedious**

## A Solution
A solution would be to rank repositories according to some criterias that will reflect the quality of a repository. There are already metrics to get the *popularity* of a project (stars, commits, pull-requests, issues, downloads) some others to get some automatic code quality check (CodeClimate, Codacy, Coveralls ...). 

The problem with those automatic tools is that the metric they produce does not guarantee any quality. You have to use a project, test it in the real world to get this kind of info. Plus code style is something opinionated.

**Sometimes the best way to do things is to make them do by humans**

A good illustration of that is [Hacker News](https://news.ycombinator.com/). The idea is that the community votes for the best news posted by peers. Peers that get their news upvoted have their karma improved. The top posts are a combination of up-votes and freshness. That way the Top news change and they represent a quality sample of what's being published out there. *Without any complicated machine learning in the background*

A solution can be to use this peer rating principle and apply it to the open source world. Having peers score repositories against some defined criterias and weight their vote with their Karma. A user's Karma gets only as good as a combination of the scores of the repositories he contributed to.

We can then add some other automatic metrics in the computing of a repository score once we have defined those relevant.

### How User Karma should work (WIP)
* Your Karma gets better when you contribute to a well rated project.* 
* Your Karma dimishes when projects you contribute to are badly rated.*
* **(OPTIONAL)** Karma could also be augmented by Stack-Overflow karma.

*: How much it influences your karma should be proportional to your overall contribution.

### How Repository score should work (WIP)
#### Rules
* Score is base on some determined criterias evaluated by other users.
* Score can also be influenced by some key automatic metrics
* A user cannot vote for a repository he contributes to.

#### Scoring criterias 
Score criterias from 1 to 5. While scoring a user has to justify in a comment why he scored the repository as he did.

* Documentation
* Code Quality
* Support

#### Automatic Criterias
* Community Size

## Technical aspects (WIP)

### Technologies
Right now the technologies in the pipeline for the implementation are:

* Scala
* Neo4j
* Play Framework for scala
* Angular
* Sass
* Bootstrap

## Ideas
* User badges to display the repository rank and access the rating page of the repository.
