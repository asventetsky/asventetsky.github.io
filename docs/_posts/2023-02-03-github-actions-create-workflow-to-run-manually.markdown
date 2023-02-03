---
layout: post
title:  "GitHub Actions: manually running a workflow"
date:   2023-02-03 00:00:00 +0600
categories: github-actions
---
![GitHub Actions logo!](/assets/2023-02-03-github-actions-create-workflow-to-run-manually/1.png "GitHub Actions logo")

Sometimes it's necessary to create a GitHub Actions workflow which is triggered manually (not only by creating a pull
request of pushing changes to a branch). In this case the worflow should be triggered by `workflow_dispatch` event.
Just create a file inside the `.github/workflows` directory with the following content:
{% highlight yaml %}
name: ...

on:
  workflow_dispatch:
    inputs:
      ....

jobs:
    ...
{% endhighlight %}
The real example of such a file can be find [here][github-actions-yaml-example]
> Pay attention, please, to the branch which is used to run the workflow. The workflow could be run manually only in a
> default branch. Otherwise, a workflow in a feature branch can be run only by GitHub CLI (article in progress). 

[github-actions-yaml-example]: https://github.com/asventetsky/s3-terraform-backend-initializer/blob/main/.github/workflows/init.yml
