[![Build Status](https://travis-ci.com/joshuayuen99/discordbot.svg?token=EpUAuzH5nzhMPCzTTrCx&branch=master)](https://travis-ci.com/joshuayuen99/discordbot)

# TundraBot

A personal Discord bot made in my free time and used by me and my friends. I've been developing it in chunks ever since November 2019, and still plan to continue improving it and adding new features moving forward. Updated for Discord.js v12.

# Table of Contents

<!--ts-->
- [TundraBot](#tundrabot)
- [Table of Contents](#table-of-contents)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installing](#installing)
- [Using the Bot](#using-the-bot)
  - [Setting up the Bot](#setting-up-the-bot)
  - [Starting the Bot](#starting-the-bot)
  - [Inviting the Bot to Servers](#inviting-the-bot-to-servers)
- [Commands](#commands)
  - [Info](#info)
  - [Music](#music)
  - [Moderation](#moderation)
  - [Utility](#utility)
  - [Fun](#fun)
- [Contributing](#contributing)

<!--te-->

# Getting Started

These instructions will get you a copy of the bot up and running on your local machine for development and testing purposes.

If you'd like to just use my bot on your server without setting anything up yourself locally, invite my bot to your Discord server [here](https://discord.com/api/oauth2/authorize?client_id=647196546492006423&permissions=309587062&scope=bot)!

## Prerequisites

![node-current](https://img.shields.io/badge/node-%3E%3D12.0.0-brightgreen?style=flat)
[![NPM Version](https://img.shields.io/badge/npm-v6.14.5-blue?style=flat)]()

### [Node.js v12.x](https://nodejs.org/en/download/)

To check if you have Node.js installed, run this command in your terminal:
```
node -v
```

### [FFmpeg (built with v0.0.4)](https://www.ffmpeg.org/)

To install on Debian/Ubuntu, run this command in your terminal:

```
sudo apt-get install ffmpeg
```

To install on Windows:

- Download FFmpeg from their [website](https://www.ffmpeg.org/download.html)
- Unzip the .tar.bz2 file twice with a tool such as [7-Zip](https://www.7-zip.org/)
- Save the resulting ffmpeg folder wherever you want to keep it
- Add the absolute path of your new ffmpeg folder to your computer's [environment variables](https://www.howtogeek.com/118594/how-to-edit-your-system-path-for-easy-command-line-access/)

To check if you have FFmpeg installed, run this command in your terminal:
```
ffmpeg -version
```

# Installing

Download or clone this repository with the command:
```
git clone https://github.com/joshuayuen99/discordbot.git
```

Navigate to the newly created `discordbot` directory and type the following command:
```
npm install
```

And that's all for installing!

# Using the Bot

If you'd like to just use my bot on your server without setting anything up yourself locally, invite my bot to your Discord server [here](https://discord.com/api/oauth2/authorize?client_id=647196546492006423&permissions=309587062&scope=bot)!

## Setting Up the Bot

To start using the bot, you will first need to generate a Discord API token.

1) Visit https://discord.com/developers/applications/ and log in to your Discord account.
2) Click "New Application" at the top right and give it a name.
3) Click the "Bot" tab on the left.
4) Click the "Add Bot" button at the top right and give it a name.
5) Where it says "Token", click the "Copy" button.
6) Open up the `.env` file in your `discordbot` directory and paste your token directly after `DISCORDTOKEN=`

Secondly, for the music playing functionality to work correctly, you will need to provide a YouTube API key as well.

1) Visit https://console.developers.google.com/apis/dashboard and log in to your Google account.
2) Click "Create Project" and give it a name.
3) Select your newly created project from the dropdown at the top left.
4) Click the "Enable APIs and Services" button.
5) Enter "YouTube" in the search bar and click on "YouTube Data API v3".
6) Enable the API.
7) On the left hand side, click the "Credentials" tab.
8) Select "YouTube Data API v3" from the dropdown menu.
9) Select "Web server (node.js)" for where you will be calling it from.
10) Select "Public data" for which type of data you will be accessing.
11) Click "What credentials will I need?".
12) Copy your new API key and click done.
13) Open up the `.env` file in your `discordbot` directory and paste your key directly after `YOUTUBEKEY=`

## Starting the Bot

Once you've set up your Discord and YouTube APIs, you're ready to start the bot.

To start the bot, simply navigate to your `discordbot` directory and enter the command:
```
npm start
```

## Inviting the Bot to Servers

1) Visit https://discord.com/developers/applications/ and log in to your Discord account.
2) Click on your newly created project.
3) Click the "OAuth2" tab on the left.
4) Under "Scopes", check the "bot" box.
5) Check all the permissions you want your bot to request upon joining a new server (the server owner will still have to agree to these upon the bot joining). The following are the bare minimum permissions the bot needs to function properly, but checking "Administrator" is a safe bet to make sure it has everything it needs.

![Bot Permissions](/images/bot_permissions.png)

You're done! All you need now is to copy the link at the bottom of the "Scopes" section and share that with any server owner that wants to use the bot.

# Commands

`<>`s in commands indicate required arguments.

`[]`s in commands indicate optional arguments.

`|`s in either `<>`s or `[]`s indicate that any of the choices will work.

`mention` indicates an @someone format (eg. @TundraBot).

`username` indicates someone's display name in a server (eg. TundraBot).

`id` indicates the unique id associated with each Discord account. Generally hidden from users unless retrieved via a bot command.

## Info

- `Help [command | alias]` Displays a list of all commands, or detailed info about the provided command (can provide command aliases as well).

- `Whois [username | id | mention]` Displays user information such as the date someone joined the server, their roles, and when they created their account. If a user is not given, it will display user information about the person who used this command.

- `Oldest <member | user | account>` Returns information about the oldest member (server member) or user (account) of the server. When considering the oldest member of the server, it disregards the original creator of the server as they will always be the oldest except for when ownership is transferred.

- `Serverinfo` Displays information about the server such as the date it was created and how many people are currently in the server.

- `Botinfo` Displays basic information about the bot.

- `Ping` Gives you the delay between sending this command and getting a response as well as the current API latency.

## Music

My bot can play music or other YouTube links directly through Discord via a voice channel in a server. It's able to serve multiple servers at the same time such that music playing in one server has no effect on music playing in another server. I've also implemented a dynamic queuing system so that you can not only add new songs to the queue while music is already playing, but you can also shuffle, pause, and skip songs at any point as well.

- `Play <YouTube link | search phrase>` Plays music from YouTube! Accepts either a YouTube link (playlists included) or a search phrase. If given a search phrase, it will search YouTube directly and give you the option to choose from the top 5 results.

- `Skip` Skips the currently playing song and moves on to the next one in queue.

- `Stop` Stops playing music, clears the queue of songs, and leaves the voice channel.

- `Playing` Displays and links the currently playing song.

- `Queue` Displays the next 5 songs to be played in queue.

- `Repeat` Sets the currently playing song to repeat after it's done. Can be toggled on or off.

- `Shuffle [toggle | t]` Shuffles the current queue of songs once. If provided the [toggle] or [t] option, it toggles the queue to be shuffled every time a new song is added to the queue.

- `Pause` Pauses the currently playing song.

- `Resume` Resumes the currently paused song.

- `Restart` Restarts the currently playing song immediately.

## Moderation

- `Ban <mention | id> <reason>` Bans a member of the server and logs the reason to the admins.
- `Kick <mention | id> <reason>` Kicks a member of the server and logs the reason to the admins.
- `Mute <mention | id> <time (#s/m/h)>` Mutes a member of the server for the given amount of time, preventing them from typing in text channels and from talking in voice channels.
- `Report <mention | id> <reason>` Reports a member of the server to the admins, without letting everyone else in the server see what the reason was.
- `Suggest <suggestion>` Suggests a feature or other form of input to me! My bot will forward me your suggestion via DM.

## Utility

- `RNG [min max]` Randomly picks a number between [min] and [max] if provided, or 0-100 otherwise.
- `Emoji <emoji> [...emoji]` Gives the unicode for the entered emoji(s).

## Fun

- `RPS (rock paper scissors)` Play a game of rock paper scissors against the bot. Choose your move by reacting to the bot's response message.
- `Love [mention | id | username]` Displays how much love a given person has for you (just a random fun command). If a user is not given, it randomly chooses someone else in the server.

# Contributing

Contributions of any kind are welcome! Please submit them to the repository via pull requests.
