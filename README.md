# Mac OS X 10.10 Yosemite Setup

The process I use to get my Yosemite development environment up and runnning afer a clean install. I use this guide to keep track of the software and steps I go through to get my system up and running. Feedback and recommendations are appreciated.

Feel free to fork this and modify this guide to match your own needs and preferences.

## Software

### Prerequisites
I have the latest versions of the folowing software downloaded and ready to install following the first boot:
* [Little Snitch 3](https://www.obdev.at/products/littlesnitch/) (Make sure to register as the demo period ends after 3 hours)
* [BitDefender Antivirus for Mac](http://www.bitdefender.com/solutions/antivirus-for-mac.html)

### App Store
* [Airmail](https://itunes.apple.com/us/app/airmail-2.1/id918858936?mt=12)
* [Alternote](https://itunes.apple.com/us/app/alternote-beautiful-note-taking/id974971992?mt=12)
* [Amphetamine](https://itunes.apple.com/us/app/amphetamine/id937984704?mt=12)
* [Dash](https://itunes.apple.com/us/app/dash-api-docs-snippets/id458034879?mt=12)
* [Evernote](https://itunes.apple.com/us/app/evernote/id406056744?mt=12)
* [Quiver: The Programmers Notebook](https://itunes.apple.com/us/app/quiver-programmers-notebook/id866773894?mt=12)
* [Paw HTTP & Rest Client](https://itunes.apple.com/us/app/paw-http-rest-client/id584653203?mt=12)
* [Fantastical 2](https://itunes.apple.com/us/app/fantastical-2-calendar-reminders/id975937182?mt=12)
* [Magnet](https://itunes.apple.com/us/app/magnet/id441258766?mt=12)
* [Slack](https://itunes.apple.com/us/app/slack/id803453959?mt=12)
* [Textual 5](https://itunes.apple.com/us/app/textual-5/id896450579?mt=12)
* [Transmit](https://itunes.apple.com/us/app/transmit/id403388562?mt=12)
* [Tweetbot](https://itunes.apple.com/us/app/tweetbot-for-twitter/id557168941?mt=12)
* [WiFi Signal](https://itunes.apple.com/us/app/wifi-signal/id525912054?mt=12)
* [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12)

### Browsers
* [Chrome](http://www.google.com/chrome/index.html)
* [Chrome Canary](https://www.google.com/chrome/browser/canary.html)
* [Firefox](https://www.mozilla.org/en-US/firefox/new/)
* [Firefox Developer Edition](https://www.mozilla.org/en-US/firefox/developer/)

### Development
* [Beoynd Compare](http://www.scootersoftware.com)
* [Dropbox](https://www.dropbox.com/)
* [GitHub](https://mac.github.com/)
* [GitUp](http://gitup.co/)
* [Sublime Text 3](http://www.sublimetext.com/3dev)

### Utilities
* [Adobe Creative Cloud](https://www.adobe.com/)
* [Bartender](http://www.macbartender.com/)
* [iTerm2](http://iterm2.com/)
* [Spotify](https://www.spotify.com/)
* [Parallels Desktop](http://www.parallels.com/)

## Fonts
* [Source Code Pro](https://github.com/adobe-fonts/source-code-pro)
* [Sauce Code Powerline](https://github.com/powerline/fonts/tree/master/SourceCodePro) (Patched Source Code Pro for ZSH)

# Command Line

## Xcode Command Line Tools
In [iTerm2](http://iterm2.com/) execute this command to install [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12) command line tools.
```bash
# Note that there are two dashes, not one.
$ xcode-select --install
```
Once this is complete run the following, and if required, accept the Xcode license.
```bash
$ sudo gcc --version
```

## Install Homebrew
[Homebrew](http://brew.sh/), “the missing package manager for OS X.”
```bash
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
$ brew doctor
```
