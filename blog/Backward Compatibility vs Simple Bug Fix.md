# Backward Compatibility vesus Simple Bug Fix

## The Story

I was working on a templated Jenkins pipeline in one of the big 4 banks. The pipeline delivers built artefact to both Artifactory and AWS ECR. The bug was fairly simple: A configuration variable was used to stand for a path in both Artifactory and ECR. Artifactory delivery code expects no slash in the beginning of the path, ECR delivery code expects otherwise. Both delivery codes were in a shared template project managed by a platform team.

## The Naive Fix

**BY ME**

I thought this was easy to fix, 10 minutes later I raised an issue ticket in Github and a PR to fix it. The fix simply made the ECR delivery code change to expect a slash too.

## The Conversation

**BETWEEN ME AND PLATFORM TEAM**

I was also trying to get some traction in the team channel of the platform team. I did get some attention from the devops team member. But I was politely being asked to close the PR because it would create backward incompatibility issues for existing pipelines. I was referred to another team's pipeline and apparently it will cause issue for that pipeline, even though the problem would be too easy to fix. Not part of the platform team, I had no idea how wide spread the issue would be. I conceded.

## The UGLY Fix

So I did the next best thing: I fixed by essentially using two configuration variables, one with a leading slash while the other not.

## My Questions

Should I have conceded or pushed for the fix? 
There is an obvious method to manage the backward compatibility issue by versioning the change. What I don't know is the platform team's development policy and internal issues.

[Home](/index)