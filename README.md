# Discord.js Music Bot Addon  
[![npm package](https://nodei.co/npm/discord.js-musicbot-addon.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/discord.js-musicbot-addon/)  
[![Discord Server](https://discordapp.com/api/guilds/350862388385546241/embed.png)](https://discord.gg/fj5jPEn)  [![Downlaods](https://img.shields.io/npm/dt/discord.js-musicbot-addon.svg?maxAge=3600)](https://www.npmjs.com/package/discord.js-musicbot-addon)  [![Version](https://img.shields.io/npm/v/discord.js-musicbot-addon.svg?maxAge=3600)](https://www.npmjs.com/package/discord.js-musicbot-addon)  
***
This module way be buggy and need some fine tuning. Feel free to let me know what problems you encounter by opening an issue on the repo.
This was originally an update of the original bot from [ruiqimao](https://github.com/ruiqimao/discord.js-music) by [nexu-dev](https://www.npmjs.com/package/discord.js-music-v11), but is now a updated version for [Discord.js](https://discord.js.org/)'s version 11.2^. Fixes deprecated warnings, video playback issues, along with various other add-ons and tweaks to the priors.
***
__The commands available are: (default names)__  
* `musichelp [command]`: Displays help text for commands by this addon, or help for a specific command.
* `play <url>|<search string>`: Play audio from YouTube.
* `skip [number]`: Skip a song or multi songs with skip [some number],
* `queue`: Display the current queue.
* `pause`: Pause music playback. (requires music manager).
* `resume`: Resume music playback. (requires music manager).
* `volume`: Adjust the playback volume between 1 and 200 (requires music manager).
* `leave`: Clears the song queue and leaves the channel.
* `clearqueue`: Clears the song queue.

__Permissions:__  
* If `anyoneCanSkip` is false then only admins and the user that requested the song can skip it.
* If `anyoneCanAdjust` is true, anyone can adjust the volume. False is only admins.

__Things I added & Changed:__  
* Videos won't (or are otherwise less likely to) end before the song stops.
* Help command added.
* Text replies were changed.
* Added more options.  
***
# Installation
***  
__Pre-installation:__  
1. `npm install discord.js` // The core discord.js framework (recommended stable > dev branch).  
2. `npm install ffmpeg-binaries` or `ffmpeg installed` // Allows the bot to join voice.  
3. `npm install node-opus` or `npm install opusscript` // Required to stream audio. Discord.js prefers node-opus.

__Installation:__  
* `npm install discord.js-musicbot-addon`

__Common installation issues:__  
__Issue:__ FFMPEG was not found on your system, so audio cannot be played. Please make sure FFMPEG is installed and in your PATH.  
__Fix:__ `npm install ffmpeg-binaries`  

__Issue:__ Couldn't find an Opus engine.  
__Fix:__ `npm install node-opus` or `npm install opusscript`  

__Issue:__ Any node-gyp errors. (build fail, missing cl.exe, etc.)  
__Fix:__ This one is a little more complicated.  
1. Download and install [Visual Studio 2015](https://www.visualstudio.com/downloads/)  
2. New project -> Visual C++  
3. Install Visual C++  

If that doesn't fix your issue;  
1. Download and install the [Windows 8.1 SDK](https://developer.microsoft.com/en-us/windows/downloads/windows-8-1-sdk)  

***
# Examples & Options
***  
This addon is easy to use, and doesn't require any configuration.  
More examples can be found on the repo in `examples` or once downloaded.  

__Example basic code, standalone:__
```javascript
const Discord = require('discord.js');
const music = require('discord.js-musicbot-addon');
const <client> = new Discord.Client(); //replace <client> with what you want your Discord Client to be. Don't include < > on your client.

<client>.on('ready', () => {
    console.log(`[Start] ${new Date()}`);
});

music(<client>);
<client>.login(token);
```

All options are optional and thus not needed.  
The options you can pass in music(client, options) is as followed:  
* prefix: Prefix to set for commands.  
* global: true/false. If set to true, will use global queues, false will use server. (default false)  
* maxQueueSize: Max size of queues.
* anyoneCanSkip: Whether or not anyone can skip, true/false. Defaults false.
* anyoneCanAdjust: Whether or not anyone can set volume. Defaults false.
* clearInvoker: Whether or not to clear the command message.
* volume: Default volume. Anywhere from 1 to 200, default is 50.
* helpCmd: Name of the help command.
* playCmd: Sets the play command name.
* skipCmd: Sets the skip command name.
* queueCmd: Sets the queue command name.
* pauseCmd: Sets the name for the pause command.
* resumeCmd: Sets the name for the resume command.
* volumeCmd: Sets the name for the volume command.
* leaveCmd: Sets the name for the leave command.
* clearCmd: Sets the name for the clearqueue command.
* enableQueueStat: Disables or enables queue status (useful to prevent errors sometimes, defaults true).  

An example of a few custom commands would be:  
```javascript
music(client, {
  prefix: ">",
  maxQueueSize: "10",
  anyoneCanSkip: false,
  helpCmd: 'mhelp',
  playCmd: 'music',
  leaveCmd: 'begone'
});
```

Again if you have any issues, feel free to open one on the repo, or join my [Discord server](https://discordapp.com/invite/fj5jPEn).
