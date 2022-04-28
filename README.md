<h1 align="center">
  <a href="#"><img src="https://i.imgur.com/kIeJdDm.png" alt="Hotdog"></a>
  Hotdog 🌭
</h1>
<p align="center">
    <img alt="Size" src="https://img.shields.io/github/languages/code-size/WilardzySenpai/Hotdog">
    <img alt="discord-ver" src="https://img.shields.io/badge/discord.js-v12.5.3-blue">
    <img alt="database" src="https://img.shields.io/badge/database-mongodb-informational?style=flat&logo=mongodb&logoColor=white&color=blue">
    <img alt="Stars" src="https://img.shields.io/github/stars/WilardzySenpai/Hotdog">
    <img alt="Fork" src="https://img.shields.io/github/forks/WilardzySenpai/Hotdog">
    <img alt="License" src="https://img.shields.io/github/license/WilardzySenpai/Hotdog">
</p>

## 💻 Requirements
1. Nodejs 12: **[Link](https://nodejs.org)**
2. Git: **[Link](https://git-scm.com)**
3. Discord Bot Token: **[Link](https://discord.com/developers/applications)**
4. OsuClientApi: **[Link](https://osu.ppy.sh/home/account/edit#new-oauth-application)**
5. MongoDB Database's URI: **[Link](https://www.mongodb.com)**
   
## Getting Started
Before you start editing or forking this code you should have a basic knowledge of JavaScript and Discord.js v12. Having a basic knowledge will help you to not get a error by running or let's say you won't get confused. Basic Knowledge means you should know the basic functions and Syntax's.

## Create Discord Application
Go to [Discord Developer Portal](https://discord.com/developers/applications) and click "New Application" then name your application then click "Create". Now head over to Bot. Click Add Bot, then you customize the name and avatar(If youd like). Now lets get coding.

## Coding
Make a folder where you want to store all your bot files. Open CMD with that Folder location and type `npm init` This will create a `package.json` file in your directory.Then open Visual Studio Code with that Directory.then make a file with your main file name, in my case its `index.js` then type this code
```js
// Important files and packages
const { prefix, bprefix, developerID, YTCK } = require("./config.json")
const math = require("mathjs")
const { config } = require("dotenv");
const fetch = require("node-fetch");
const db =require("quick.db");
const moment = require("moment");
const { ima, welc } = require("image-cord")
const Discord = require('discord.js')
const { Client, MessageEmbed, Collection }  = require('discord.js');
const fs = require("fs");
const { join } = require("path");
const configg = require("./configg.json");
const { Canvas, resolveImage } = require('canvas-constructor');
const canvas = require('canvas')
const DisTube = require("distube")
const mongoose = require('mongoose');
const SQLite = require("better-sqlite3")
const sql = new SQLite('./mainDB.sqlite')
const Levels = require("discord-xp");
const Schema3 = require('./util/level')
const filters = require("./JSON/filters.json")
//Events
client.on("ready", () => {
  console.log(`Successfully logined as ${client.user.tag}`)

  //Database connect
var colors = require('colors');
  
  mongoose.connect(configg.mongoPath, { useUnifiedTopology: true, useNewUrlParser: true, useFindAndModify: false, useCreateIndex: true })
        .then(() => console.log(`Connected to Mongo`.green))
        .catch((error) => { console.log(error) });
});
//Login
client.login(process.env.TOKEN);
```
## Command Handler Made by [Tomato6966](https://github.com/Tomato6966)
`command.js` This read all the file inside the command folder
```js
// Handler made by Tomato
var colors = require('colors');
const { readdirSync } = require("fs");
const ascii = require("ascii-table");
let table = new ascii("Commands");
table.setHeading("Command", "Load status");
console.log("Welcome to SERVICE HANDLER /--/ By https://milrato.eu /--/ Discord: Tomato#6966".yellow);
module.exports = (client) => {
  try{
    readdirSync("./commands/").forEach((dir) => {
        const commands = readdirSync(`./commands/${dir}/`).filter((file) => file.endsWith(".js"));
        for (let file of commands) {
            let pull = require(`../commands/${dir}/${file}`);
            if (pull.name) {
                client.commands.set(pull.name, pull);
                table.addRow(file, "Ready");
            } else {
                table.addRow(file, `error->missing a help.name,or help.name is not a string.`);
                continue;
            }
            if (pull.aliases && Array.isArray(pull.aliases)) pull.aliases.forEach((alias) => client.aliases.set(alias, pull.name));
        }
    });
    console.log(table.toString().cyan);
  }catch (e){
    console.log(String(e.stack).bgRed)
  }
};
```
## Event Handler also made by [Tomato6966](https://github.com/Tomato6966)
`event.js` Will load all the event inside the event folder
```js
// Event handler by tomato
var colors = require('colors');
const fs = require("fs");
const ascii = require("ascii-table");
let table = new ascii("Events");
table.setHeading("Events", "Load status");
const allevents = [];
module.exports = async (client) => {
  try{
    const load_dir = (dir) => {
      const event_files = fs.readdirSync(`./events/${dir}`).filter((file) => file.endsWith(".js"));
      for (const file of event_files){
        const event = require(`../events/${dir}/${file}`)
        let eventName = file.split(".")[0];
        allevents.push(eventName);
        client.on(eventName, event.bind(null, client));
      }
    }
    await ["client", "guild"].forEach(e=>load_dir(e));
    for (let i = 0; i < allevents.length; i++) {
        try {
            table.addRow(allevents[i], "Ready");
        } catch (e) {
            console.log(String(e.stack));
        }
    }
    console.log(table.toString());
    try{
      const stringlength = 69;
      console.log("\n")
      console.log(`     ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓`.bold.brightGreen)
      console.log(`     ┃ `.bold.brightGreen + " ".repeat(-1+stringlength-` ┃ `.length)+ "┃".bold.brightGreen)
      console.log(`     ┃ `.bold.brightGreen + `Welcome to SERVICE HANDLER!`.bold.brightGreen + " ".repeat(-1+stringlength-` ┃ `.length-`Welcome to SERVICE HANDLER!`.length)+ "┃".bold.brightGreen)
      console.log(`     ┃ `.bold.brightGreen + `  /-/ By https://milrato.eu /-/`.bold.brightGreen + " ".repeat(-1+stringlength-` ┃ `.length-`  /-/ By https://milrato.eu /-/`.length)+ "┃".bold.brightGreen)
      console.log(`     ┃ `.bold.brightGreen + " ".repeat(-1+stringlength-` ┃ `.length)+ "┃".bold.brightGreen)
      console.log(`     ┃ `.bold.brightGreen + `  /-/ Discord: Tomato#6966 /-/`.bold.brightGreen + " ".repeat(-1+stringlength-` ┃ `.length-`  /-/ By Discord: Tomato#6966 /-/`.length)+ "   ┃".bold.brightGreen)
      console.log(`     ┃ `.bold.brightGreen + " ".repeat(-1+stringlength-` ┃ `.length)+ "┃".bold.brightGreen)
      console.log(`     ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛`.bold.brightGreen)
    }catch{ /* */ }
    try{
      const stringlength2 = 69;
      console.log("\n")
      console.log(`     ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓`.bold.yellow)
      console.log(`     ┃ `.bold.yellow + " ".repeat(-1+stringlength2-` ┃ `.length)+ "┃".bold.yellow)
      console.log(`     ┃ `.bold.yellow + `Logging into the BOT...`.bold.yellow + " ".repeat(-1+stringlength2-` ┃ `.length-`Logging into the BOT...`.length)+ "┃".bold.yellow)
      console.log(`     ┃ `.bold.yellow + " ".repeat(-1+stringlength2-` ┃ `.length)+ "┃".bold.yellow)
      console.log(`     ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛`.bold.yellow)
    }catch{ /* */ }
  }catch (e){
    console.log(String(e.stack).bgRed)
  }
};
```
## Bot Status and Activity also made by [Tomato6966](https://github.com/Tomato6966)
can be inside the event folder and client
```js
// ready by tomato
var colors = require('colors');
module.exports = client => {
  try{
    const stringlength = 69;
    console.log("\n")
    console.log(`     ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓`.bold.brightGreen)
    console.log(`     ┃ `.bold.brightGreen + " ".repeat(-1+stringlength-` ┃ `.length)+ "┃".bold.brightGreen)
    console.log(`     ┃ `.bold.brightGreen + `Discord Bot is online!`.bold.brightGreen + " ".repeat(-1+stringlength-` ┃ `.length-`Discord Bot is online!`.length)+ "┃".bold.brightGreen)
    console.log(`     ┃ `.bold.brightGreen + ` /--/ ${client.user.tag} /--/ `.bold.brightGreen+ " ".repeat(-1+stringlength-` ┃ `.length-` /--/ ${client.user.tag} /--/ `.length)+ "┃".bold.brightGreen)
    console.log(`     ┃ `.bold.brightGreen + " ".repeat(-1+stringlength-` ┃ `.length)+ "┃".bold.brightGreen)
    console.log(`     ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛`.bold.brightGreen)
  }catch{ /* */ }
    let satutsswitch = false;
  try{
    client.user.setActivity(`h!help | ${client.guilds.cache.size} Guilds | Hotdog`, { type: "WATCHING" });
  }catch (e) {
      console.log(String(e.stack));
  }
  setInterval(()=>{
    try{
      if(satutsswitch){
        satutsswitch = !satutsswitch;
        for(const gid of client.guilds.cache.map(g => g.id))
        client.user.setActivity(`h!help | Hotdogs`, { type: "WATCHING" });
      }
      else{
        satutsswitch = !satutsswitch;
        client.user.setActivity(`h!help | ${client.guilds.cache.size} Guilds | Hotdog`, { type: "LISTENING" });
      }
    }catch (e) {
        console.log(String(e.stack));
    }
  }, 12*1000)
}
```
## Command Structure
```js
const Discord = require('discord.js');
const config = require('../../config.json');
module.exports = {
        name: '',
        description: '',
        category: '',
        aliases: [""],
        usage: '',
        accessableby: "",
        premium: ,// true or false,
    run: async (client, message, args) => {
     // PROCESSING CODE HERE
    }
}
```
## 📖License
Released under the [MIT License](https://github.com/WilardzySenpai/Hotdog/blob/main/LICENSE)
