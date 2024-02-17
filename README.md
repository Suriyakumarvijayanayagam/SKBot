

# TARS 


> A simple Nodejs BOT for whatsapp web

<a href="#-preview">Preview</a> •
<a href="#-features">Features</a> •
<a href="#-downloads-">Downloads</a> •
<a href="#how-to-start-the-bot">How to?</a> •
<a href="#-technologies">Technologies Used</a> •
<a href="#why">Why?</a> •
<a href="#goals">Goals</a> •
<a href="#faq">FAQ</a>


## 🔍 Preview 

### Quick preview
![Screenshot gif]()



## ⚡ Features 

* 🎨 Highly customizable json.
* 💯 Totally Free for personal use.
* 🔒 Complete Privacy. Your data stays with you always.
* 💻 Download media files automatically.
* 👥 Multiple instances.

## ⬇ Downloads ⬇

macOS | Windows | Linux
-----------------| ---| ---|
[Download Latest Release](https://github.com/Suriyakumarvijayanayagam/Tars/releases/tag/v1.0.0)

## Supported Platforms
The following platforms are supported by TARS:

**macOS:**
The minimum version supported is macOS 10.9.

**Windows:**
Windows 7 and later are supported.

**Linux:**

- Ubuntu 12.04 and later
- Fedora 21
- Debian 8

## How to start the TARS?

### STEPS

After downloading, extract the zip file and navigate to that location in your terminal. There will be a file named ```Tars-*``` . Run it and you should be good to go.

For Linux you need to provide executable permission before you execute the binary. 
Run the command - 
```
chmod +x Tars-linux && Tars-linux
```

Note: On Linux you need a running display server (X11 or Wayland).
If you run Linux on a headless server or want to run chmomium without visible display try ```xvfb-run-Tars-linux```.

*I haven't tested Mac and Linux binaries. If you find any issues using them feel free to raise one from [here]()*

### Configurations 

Basic configuration is in ```bot.json``` file like replying to ```Hi, hello and happy birthday```. 
You can change this config file as per your need. Keep in mind that you need to restart the TArs to see the effects of your changes. Make sure the JSON is valid. Use VSCode or [jsonlint](https://jsonlint.com/) to validate the JSON.

### bot.json 

**appconfig**

This is where all the application related (node application behavior and such things) config will stay. Will add more in future.

- **headless:** whether to start chrome as headless or not. this is regarding #4. Apparently, Whatsapp doesn't allow headless instances.
- **isGroupReply:** whether to send replies in group or not. If set to false, Bot will not reply if message received in group chat.

- **webhook:** A URL which will be called for every message with payload data. This can be useful if you want to do other operation over messages in your server. 

- **downloadMedia:** Whether to download incoming message media or not. 

- **replyUnreadMsg:** If there are pending unread messages which bot hasn't replied to then by making this flag true, bot will respond to those messages. Keep in mind that bot will not be able to mark those messages as read/seen. Please open the chat manually in the phone to mark that chat as read otherwise bot will reply to it at every start. 

- **CustomInjectionFolder** relative path of the folder from current directory which has JS file which needs to be injected in the browser. for example if you have something like following 
```
└── Tars  /
    ├── bot.json
    ├── hi.jpg
    ├── bye.jpg
    ├── Tars.exe
    └── injection/
        ├── index.js
        └── utils.js
```

then you need to set the value of this property as ```./injection```

**bot**

An array of objects. Properties of Object are self explanatory. 

- **Contains:** If message has one of that word anywhere in the message
- **exact:** If message is exactly as one of the messages form array

- **Response:** If any of the above conditions becomes true then corresponding response string or [spintax](https://spintaxtool.appspot.com/) will be sent as message to the user or group. There are two variable: `name` and `phoneNumber` which you can use to create custom message for sender.
- Sample message with variable is in `bot.json`.

- **file:** Name of the file (from current directory) which you want to send along with response.

- **afterSeconds:** Number of seconds bot should wait before sending a reply. 
- **Webhook:** You can call your webhook on certain keywords as well instead of calling it on every message. 
- **responseAsCaption:** This will be applied in case you want to reply with image. If true then response block will be sent as a caption of the image. If false then response block will be shared as separate text message.

**Blocked**

Array of numbers with county code to which this bot will not reply to.

**noMatch**

Default reply message or [spintax](https://spintaxtool.appspot.com/) when no exact match found in Tars

**smartreply** *(This feature is under maintenance at the moment.)*

An object which contains suggestions and it's configs.

- **suggestions** An Array of suggestions
- **clicktosend** Whether to send or just write message when user clicks on suggestion

here is how that looks

![smart reply gif](https://user-images.githubusercontent.com/6497827/58412366-f1653380-8093-11e9-8427-1ca19235faed.gif)


## Run the latest code from Github

**This is only recommended for advanced 'node.js' users or for development purpose.**

Open a Terminal and create a new directory in your home directory, e.g. 'node' and goto there.
Now download and run the latest version of Tars


If you run Linux on a headless server or want to run chromium without visible display try ```xvfb-run Tars-linux```.

## Known bugs
Sometimes, closing the `node` server directly does not clear browser cache. Next time when the bot is started, it runs into errors due to which smart reply is not setup correctly. A temporary fix to this is to clear `node` cache.

```java-script 
npm cache clean
```


## 💻 Technologies
* [Node](https://nodejs.org/en/)
* [puppeteer](https://github.com/GoogleChrome/puppeteer)


## Why?

The main reason I decided to build this is that I needed a simple tool to reply to my "happy birthday" messages. I know it is kind of blunt and rude but it would take me 2-3 days to reply to all and by that time that moment would be gone. I needed a good solution to this problem. I really don't need a full-fledged AI-BOT or BOT with NLU (or some other acronym). I believe there are many people who also have such needs.

## Goals
With that in mind, I know that Tars would need to satisfy these criteria:

* 🚀 Fast!!!
* 👍 Friendly CLI UX
* 🔒 Does not touch user’s data
* 💰 Free! for personal use

If you think Tars delivers these, let me know by putting a **star ⭐** on this project


## FAQ

* **Is this app built with NodeJS?**

  Yes, it's built with [NodeJS](https://nodejs.org/en/). Please see the [Technologies](#-technologies) section for more info.

* **What boilerplate did you use?**

  None. The idea was to get a better understanding of how things work together, But I do take a cue from other projects.

* **What npm modules did you use?**

  - [Ora](https://www.npmjs.com/package/ora) for spinner 
  - [cli-progress](https://www.npmjs.com/package/cli-progress) for download progress bar in terminal
  - [qrcode-terminal](https://www.npmjs.com/package/qrcode-terminal) to generate QRCode in terminal 
  - [mime](https://www.npmjs.com/package/mime) detect mime file sent
  - [mel-spintax](https://www.npmjs.com/package/mel-spintax) to support spintax


## 📃 Legal
This code is in no way affiliated with, authorized, maintained, sponsored or endorsed by WhatsApp or any of its affiliates or subsidiaries. This is an independent and unofficial software. Use at your own risk.
**Commercial use of this code/repo is strictly prohibited.**


