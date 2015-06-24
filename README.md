# Mac OS X 10.10 Yosemite Setup

The process I use to get my Yosemite development environment up and running after a clean install. I use this guide to keep track of the software and steps I go through to quickly get a system up and running. Feedback and recommendations are appreciated.

Feel free to fork this and modify this guide to match your own needs and preferences.

## Software

### Prerequisites
I have the latest versions of the following software downloaded and ready to install following the first boot:
* [Little Snitch 3](https://www.obdev.at/products/littlesnitch/) (Make sure to register as the demo period ends after 3 hours)
* [BitDefender Antivirus for Mac](http://www.bitdefender.com/solutions/antivirus-for-mac.html)

### App Store
* [Airmail](https://itunes.apple.com/us/app/airmail-2.1/id918858936?mt=12)
* [Alternote](https://itunes.apple.com/us/app/alternote-beautiful-note-taking/id974971992?mt=12)
* [Amphetaminee](https://itunes.apple.com/us/app/amphetamine/id937984704?mt=12)
* [Dash](https://itunes.apple.com/us/app/dash-api-docs-snippets/id458034879?mt=12)
* [Evernote](https://itunes.apple.com/us/app/evernote/id406056744?mt=12)
* [Quiver: The Programmers Notebookk](https://itunes.apple.com/us/app/quiver-programmers-notebook/id866773894?mt=12)
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
* [Beyond Compare](http://www.scootersoftware.com)
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

## Set Hostname
```bash
$ sudo scutil --set HostName rye
```

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

## Beyond Compare Command Line Tools
`Beyond Compare > Install Command Line Tools`
If you get a "Failed to install command line tools" error issue the following commands in the Terminal:
```bash
$ ln -s /Applications/Beyond\ Compare.app/Contents/MacOS/bcomp /usr/local/bin/bcompare
$ ln -s /Applications/Beyond\ Compare.app/Contents/MacOS/bcomp /usr/local/bin/bcomp
```

## Install Homebrew
[Homebrew](http://brew.sh/), "the missing package manager for OS X."
```bash
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
$ brew tap homebrew/dupes
$ brew tap homebrew/versions
$ brew doctor
```
Look for the following message:
```bash
Your system is ready to brew
```

## Update Unix tools

### Install GNU core utilities
The ones that come with Yosemite are outdated
```bash
$ brew install coreutils
```
### Install GNU: find, locate, updatedb, and xargs
```bash
$ brew install findutils
```
### Install Bash 4
```bash
$ brew install bash

# Add the new shell to the list of legit shells
$ sudo bash -c "echo /usr/local/bin/bash >> /etc/shells"

# Change the shell
$ chsh -s /usr/local/bin/bash
```
Restart iTerm2 and check for Bash 4 and /usr/local/bin/bash:

```bash
$ echo $BASH && echo $BASH_VERSION
```
### Install more recent versions of some OS X tools
```bash
$ brew install homebrew/dupes/grep
```
You'll need to update PATH in your ~/.bash_profile to use these over their Mac counterparts:
```bash
$ echo export PATH="$(brew --prefix coreutils)/libexec/gnubin:$PATH" >> ~/.bash_profile
$ brew cleanup
```

## Install Oh My ZSH
[Oh My Zsh](http://ohmyz.sh/) is an open source, community-driven framework for managing your ZSH configuration. It comes bundled with a ton of helpful functions, helpers, plugins, and themes.
```bash
$ curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```

### Edit ~/.zshrc
Changes the following default values:
```bash
ZSH_THEME="agnoster"
plugins=(git bower brew gem node npm osx)
```
Set DEFAULT_USER to your regular username to hide the "user@hostname" info when you're logged in as yourself on your local machine.
```bash
DEFAULT_USER="cameronrye"
```

## Add Sublime Text CLI
```bash
$ mkdir -p ~/bin && ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" ~/bin/subl
```

## Customize iTerm2

### Create iTerm2 Profile
`iTerm2 > Preferences > Profiles > + > Name (Custom Shell)`

### Color Scheme
My current preference is the [Solarized](http://ethanschoonover.com/solarized) color scheme.

Grab [Solarized Dark](https://github.com/altercation/solarized/tree/master/iterm2-colors-solarized) and import into [iTerm2](http://iterm2.com/).

`iTerm2 > Preferences > Profiles > Colors Tab > Load Presets > Import > Select Solarized Dark Theme`

### Powerline Patched Font
If you haven't already install [Sauce Code Powerline](https://github.com/powerline/fonts/tree/master/SourceCodePro) a powerline patched version of Source Code Pro.

`iTerm2 > Preferences > Profiles > Text Tab > Change Font > Source Code Pro for Powerline`

# Git

## Install Git
```bash
$ brew update
$ brew doctor
$ brew install git
```
Verify your system is referencing the right version:
```bash
$ which git
```
You should see `/usr/local/bin/git` if you see `/usr/bin/git` then there is an issue with your `$PATH`

## Setup Github
```bash
# Set git config values
$ git config --global user.name "Cameron Rye"
$ git config --global user.email "your_email@example.com"
$ git config --global github.user cameronrye

git config --global core.editor "subl -w"
git config --global color.ui true

# Global git ignore file:
$ git config --global core.excludesfile '~/.gitignore'
$ echo '.DS_Store' >> ~/.gitignore

# Generate SSH Key
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

# Copy contents of the id_rsa.pub file to your clipboard
pbcopy < ~/.ssh/id_rsa.pub
# Add Key to Github

# Test connection
ssh -T git@github.com
```

## Make Beyond Compare Default Diff and Merge Tool
```bash
$ git config --global diff.tool bc3
$ git config --global difftool.prompt false
$ git config --global merge.tool bc3
```

# Install RVM with the latest Ruby and Rails
[Ruby Version Manager](https://rvm.io) allows you to install and manage multiple versions of Ruby and Rails on the same machine.

## Disable Documentation
```bash
echo "gem: --no-document" >> ~/.gemrc
```

## Install Ruby and Rails
curl -L https://get.rvm.io | bash -s stable --auto-dotfiles --autolibs=enable --rails

# Install Node.js and NPM
```bash
$ brew update
$ brew doctor
$ brew install node

# Verify successful install
$ npm version
```
This should return something like the following:
`{ npm: '2.11.1', http_parser: '2.3', modules: '14',
  node: '0.12.4', openssl: '1.0.1m', uv: '1.5.0',
  v8: '3.28.71.19', zlib: '1.2.8' }`

## Check for NPM Updates
Issue this command to update global NPM packages
```bash
$ npm install -g npm@latest
```

# Install MongoDB
[Website](http://www.mongodb.org) | [GitHub](https://github.com/mongodb)
```bash
$ brew update
$ brew doctor
$ brew install mongodb

# Automatically load on login
$ ln -sfv /usr/local/opt/mongodb/*.plist ~/Library/LaunchAgents
$ launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mongodb.plist

# Create the data directory
$ mkdir -p /data/db

# Check for errors
$ mongod
```

# NPM Packages

## Install Bower
[Website](http://bower.io/) | [GitHub](https://github.com/bower/bower)
```bash
$ npm install -g bower
```

## Install Grunt
[Website](http://gruntjs.com/) | [GitHub](https://github.com/gruntjs/)
```bash
$ npm install -g grunt-cli
```

## Insatll Gulp
[Website](http://gulpjs.com/) | [GitHub](https://github.com/gulpjs/gulp)
```bash
$ npm install --global gulp
```

## Install Yeoman
[Website](http://yeoman.io/) | [GitHub](https://github.com/yeoman/yeoman)
```bash
$ npm install -g yo
```

## Install Browserify
[Website](http://browserify.org/) | [GitHub](https://github.com/substack/browserify-website)
```bash
$ npm install -g browserify
```

## Install Webpack
[Website](http://webpack.github.io/) | [GitHub](https://github.com/webpack/webpack)
```bash
$ npm install webpack -g
```

## Install Broccoli.js
[Website](http://broccolijs.com/) | [GitHub](https://github.com/broccolijs/broccoli)
```bash
$ npm install -g broccoli-cli
```

## Install jspm
[Website](http://jspm.io/) | [GitHub](https://github.com/jspm/jspm-cli)
```bash
$ npm install jspm -g
```

## Install Babel
[Website](http://babeljs.io/) | [GitHub](https://github.com/babel/babel)
```bash
$ npm install -g babel
```

## Install Browser Sync
[Website](http://www.browsersync.io/) | [GitHub](https://github.com/Browsersync/browser-sync)
```bash
$ npm install -g browser-sync
```

# Sublime Text 3

## Add Sublime Text CLI
```bash
$ mkdir -p ~/bin && ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" ~/bin/sublimetext
```
## Install Package Control
Run [Sublime Text 3](http://www.sublimetext.com/3dev) and access the console via `CTRL + \``

`import urllib.request,os,hashlib; h = 'eb2297e1a458f27d836c04bb0cbaf282' + 'd0e7a3098092775ccb37ca9d6b2e4b7d'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)`

Check [Package Control](https://packagecontrol.io/) for the latest install script and for more information.

## Install Packages
 * [Babel](https://packagecontrol.io/packages/Babel)
 * [CSS3](https://packagecontrol.io/packages/CSS3)
 * [DashDock](https://packagecontrol.io/packages/DashDoc)
 * [Doc​Blockr](https://packagecontrol.io/packages/DocBlockr)
 * [HTML-CSS-JS Prettify](https://packagecontrol.io/packages/HTML-CSS-JS%20Prettify)
 * [Java​Script​Next - ES6 Syntax](https://packagecontrol.io/packages/JavaScriptNext%20-%20ES6%20Syntax)
 * [Material Theme](https://packagecontrol.io/packages/Material%20Theme)
 * [PrettyJSON](https://packagecontrol.io/packages/Pretty%20JSON)
 * [SASS](https://packagecontrol.io/packages/Sass)
 * [SideBarEnhancements](https://packagecontrol.io/packages/SideBarEnhancements)
 * [SideBarFolders](https://packagecontrol.io/packages/SideBarFolders)
 * [SublimeCodeIntel](https://packagecontrol.io/packages/SublimeCodeIntel)
 * [TabsExtra](https://packagecontrol.io/packages/TabsExtra)

[Material Theme Icon](https://dribbble.com/shots/2104476-Material-Theme-for-Sublime-Text-3/attachments/380650)

## Settings
`Sublime Text > Preferences > Settings - User`
```JSON
{
	"always_show_minimap_viewport": true,
	"bold_folder_labels": true,
	"caret_extra_width": 1,
	"caret_style": "phase",
	"close_windows_when_empty": false,
	"color_scheme": "Packages/Material Theme/schemes/Material-Theme.tmTheme",
	"copy_with_empty_selection": false,
	"drag_text": false,
	"draw_indent_guides": false,
	"draw_minimap_border": true,
	"enable_tab_scrolling": false,
	"findreplace_small": true,
	"font_face": "Source Code Pro",
  "font_size": 12,
  "font_options":
  [
    "no_round, gray_antialias"
  ],
	"highlight_line": true,
	"highlight_modified_tabs": true,
	"ignored_packages":
	[
		"Vintage"
	],
	"line_padding_bottom": 1,
	"line_padding_top": 1,
	"match_brackets_content": false,
	"match_selection": false,
	"match_tags": false,
	"material_theme_small_tab": true,
	"open_files_in_new_window": false,
	"overlay_scroll_bars": "enabled",
	"preview_on_click": false,
	"scroll_past_end": true,
	"scroll_speed": 5.0,
	"show_full_path": false,
	"spacegray_sidebar_font_normal": true,
	"spacegray_sidebar_tree_small": true,
	"spacegray_tabs_font_normal": true,
	"spacegray_tabs_large": true,
	"tab_size": 2,
	"theme": "Material-Theme-Darker.sublime-theme",
	"translate_tabs_to_spaces": true,
	"trim_trailing_white_space_on_save": true,
	"word_separators": "./\\()\"'-:,.;<>~!@#%^&*|+=[]{}`~?",
	"word_wrap": false
}
```

# OSX Preferences
Developer friendly enhancements for Yosemite.
```bash
# Enable repeat on keydown (default = true)
$ defaults write -g ApplePressAndHoldEnabled -bool false

# Set a shorter delay until key repeat (default = 68)
defaults write -g InitialKeyRepeat -int 28

# Add a context menu item for showing the web inspector
$ defaults write -g WebKitDeveloperExtras -bool true

# Enable Safari’s debug menu
$ defaults write com.apple.Safari IncludeInternalDebugMenu -bool true

# Show the ~/Library folder
$ chflags nohidden ~/Library
```

# Chrome Extensions
* [Addblock Plus](https://chrome.google.com/webstore/detail/adblock-plus/cfhdojbkjhnklbpkdaibdccddilifddb)
* [Edit This Cookie](https://chrome.google.com/webstore/detail/editthiscookie/fngmhnnpilhplaeedifhccceomclgfbg)
* [Evernote Web Clipper](https://chrome.google.com/webstore/detail/evernote-web-clipper/pioclpoplcdbaefihamjohnefbikjilc)
* [JSON Viewer](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh)
* [OneTab](https://chrome.google.com/webstore/detail/onetab/chphlpgkkbolifaimnlloiipkdnihall)