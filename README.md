# GItHubChecker

## Goals

- Create app with automatic fetch of Spartans repos & pull requests based on Trainer GitHub account
- Create automatic file structure on Trainer pc 
> Divided to repos with pull request created before the deadline and repos with pull request created after the deadline.
- Automatically fetch data during the day (f.e. - daily @ 9:10am & 12pm?) 
>Spartans tents to post the pull requests a bit after the deadline but after my discussions with Jack, we feel that failing the homework just because it's after deadline is a bit harsh.

***

## Ideas

### Grading

- Front End - show grades based on a repo divided into 5 groups:
  * Created pull request
  * Is it before the deadline
  * Is it working
  * Indentation & code quality
  * Extra points

> These might be useful as Spartans' accessible end point where they might be able to see they grades online. 

> Created pull request & Is it before the deadline might be graded automatically based on fetch data.

- Weighted grade to round up for us up to 8 & automatically throw out JSON/text file we can use to fill out gradebook

- Maybe give Spartans ability to grade their work as well - so we will be able to set the expectations to be at the same level from both sides

### API

- Pull request endpoint - might be also used to automate reviewing pull requests without logging into GitHub.

***

## Requirements

- To properly fetch the data it is required for the Trainer to follow all his Spartans on GitHub (update on a regular basis - after course finish unfollow accounts)

## Authentication

Right now the API is being tested using Postman & Basic Auth

***

## Main GitHub API endpoints

#### Followers

https://api.github.com/user/following - gives every user followed by the trainer. Will be saved into array.

#### Repos

https://api.github.com/users/{user}/repos - shows given user's repos (might be feeded by array made from previous call). Will be saved into array. Also this endpoint is able to throw ssh_url or git_url value which might be used to get the link necessary for copying repo onto Trainer's pc

#### Pull requests

https://api.github.com/repos/{user}/{repo}/pulls - shows pull request for any given user's repos. Might be used for getting the date of pull request.

