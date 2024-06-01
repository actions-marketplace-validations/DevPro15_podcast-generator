# Podcast Feed Generator

A Github action to generate a podcast feed from YAML file. YAML is much 
easier to read and write than XML, and this action will convert you YAML file into valid podcast feed.

## Usage

## Turn on Github Pages

In your repository, got to Settings > Pages and select the main branch as the source. This will create a link to your page and give all of the content in the main branch a URL. Note the URL for the next step.

## Create a YAML file

Create a YAML file in your repository with the following format:

```YAML
title: <Podcast Title>
subtitle: <Podcast Subtitle>
author: <Author Name>
description: <Podcast Description>
image: <Artwork Location>
language: <Podcast Language e.g. en-us>
category: <Podcast Category e.g. Technology https://podcasters.apple.com>
format: <format of files e.g. audio/mpeg>
link: <Github Page URL>
item:
  - title: <Podcast Episode Title>
    description: <Podcast Episode Description>
    published: <Date Published - e.g. Thu, 12 Jan 2023 18:00:00 GMT>
    file: <Filename e.g. /audio/TFIT01.mp3>
    duration: <duration e.g. 00:00:36>
    length: <length e.g. 576,324 (Get Info on your files)>
... Repeat for each episode
```

## Sample Workflow

You're also going to need your own worflow file . Here's a sample

```YAML
name: Generate Podcast Feeds
on: [push]
jobs: 
  build: 
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repo
        uses: actions/checkout@v3
      - name: Run Feed Generator
        uses: DevPro15/podcast-generator@main
```

