---
layout: default
parent: GIT
grand_parent: Articles
title: Deploy on Git Pages
last_modified_date: 2020-08-09
tags: [git, deploy]
summary: Summary of the article
---

# Deploy on Git Pages
{: .no_toc }
**jekyll-deploy-action** A GitHub Action to deploy the Jekyll site conveniently for GitHub Pages.
[view in git](https://github.com/jeffreytse/jekyll-deploy-action)

## Story

As we known, GitHub Pages runs in `safe` mode and only allows [a set of whitelisted plugins](https://pages.github.com/versions/). To use the gem in GitHub Pages, you need to build locally or use CI (e.g. [travis](https://travis-ci.org/), [github workflow](https://help.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow)) and deploy to your `gh-pages` branch.

Therefore, if you want to make Jekyll site run as if it were local, such as let
the custom plugins work properly, this action can be very useful for you,
beacause it's really convenient to build and deploy the Jekyll site to Github
Pages.


## 1. Create build-jekyll.yml
At First, you should add a github workflow file (e.g. `.github/workflows/build-jekyll.yml`) in your repository's `master` branch as below:

```yml
name: Build and Deploy to Github Pages

on:
  push:
    branches:
      - master  # Here source code branch is `master`, it could be other branch

jobs:
  build_and_deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      # Use GitHub Actions' cache to cache dependencies on servers
      - uses: actions/cache@v1
        with:
          path: vendor/bundle
          key: ${{ runner.os }}-gems-${{ hashFiles('**/Gemfile.lock') }}
          restore-keys: |
            ${{ runner.os }}-gems-

      # Use GitHub Deploy Action to build and deploy to Github
      - uses: jeffreytse/jekyll-deploy-action@v0.1.1
        with:
          provider: 'github'
          token: ${{ secrets.GH_TOKEN }} # It's your Personal Access Token(PAT)
          repository: ''             # Default is current repository
          branch: 'gh-pages'         # Default is gh-pages for github provider
          jekyll_src: './'           # Default is root directory
          jekyll_cfg: '_config.yml'  # Default is _config.yml
          cname: ''                  # Default is to not use a cname
          actor: ''                  # Default is the GITHUB_ACTOR
```

To schedule a workflow, you can use the POSIX cron syntax in your workflow file. The shortest interval you can run scheduled workflows is once every 5 minutes. For example, this workflow is triggered every hour.

```yml
on:
  schedule:
    - cron:  '0 * * * *'
```

## 2. Create GH_TOKEN
After this, we should provide permissions for this action to push to the `gh-pages` branch:

2.1. Create a [Personal Token](https://github.com/settings/tokens) with repos permissions and copy the value.  
2.2. ☑︎repo - Full control of private repositories  
2.3. Copy created value   
2.4. Go to your repository’s Settings and then switch to the Secrets tab.  
2.5. Create a token named `GH_TOKEN` (important) using the value copied.  

## 3. Create gh-pages
3.1. Additionally, if you don't have the `gh-pages` branch, you can create it as below:

```bash
git checkout --orphan gh-pages
git rm -rf .
git commit --allow-empty -m "initial commit"
git push origin gh-pages
```

3.2. In the end, go to your repository’s Settings and scroll down to the GitHub Pages
 section, choose the `gh-pages` branch as your GitHub Pages source.


**💡 Tip:** The `gh-pages` branch is only for the site static files and the `master` branch is for source code.


