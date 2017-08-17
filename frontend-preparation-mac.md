# Initial setup for frontend development for your Mac

* Open your Terminal. It's inside Apps > Utilities (or search for it using Spotlight [the magnifying glass in the upper right]).
* Install Apple's Xcode Command-Line Tools
  - Run `xcode-select --install`
* Install [Homebrew](http://brew.sh)<sup><a href="#homebrew" id="homebrew-token">1</a></sup>.
  - Run `sudo /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
  - Follow the instructions.

## Git

* `brew install git`
* Open a fresh Terminal tab and check the version.
	* `git --version`
	* Should read `git version 2.11.0` (or higher)
    * If it doesn't, try `brew upgrade git`
* Remember when you set up an account on [GitHub](https://www.github.com) (it was in the prework). Well, we need to tell Git who you are there so things will match up later.
	* `git config --global user.name "YOUR NAME"`
	* `git config --global user.email "YOUR EMAIL ADDRESS"` (this should be the same email address you used to sign up for GitHub)
	* `git config --global credential.helper osxkeychain` (rather than go into detail on what this does, [see GitHub's docs](https://help.github.com/articles/caching-your-github-password-in-git/).
    * If you're feeling more adventurous, go with the SSH key approach
      outlined here: <https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/>
* We're going to want to ignore some Mac-specific files in our git commits. Run the follow commands:
  * `echo .DS_Store >> ~/.gitignore_global`
  * `git config --global core.excludesfile ~/.gitignore_global`

# Node

  There are some tools in Atom which require Node, so let's go ahead and get that out of the way.

  Go here: <https://nodejs.org/en/download/> and download the Mac installer. Click the installer and follow the instructions.

# Atom and Atom Package Manager

We're going to be using [Atom](https://atom.io/), but in the next step we're going to add packages to Atom from the Terminal, so here's how to install the CLI (command-line interface) helpers for Atom:

- Run `which apm` in your Terminal. If it returns a file path, then Atom and its package manager are already installed in your command-line correctly. If it says instead, "apm not found" (or returns nothing), then open Atom the traditional way, find "Install Shell Scripts" in the Atom menu, and click it. Close your Terminal and re-open it.

### Tweaking Atom

One of the things that makes Atom powerful is its package system. I've curated a list a recommended packages that will make your life easier over the coming weeks. *Run this in Terminal:*

`apm stars --user davegregg --install`

Packages this will install:

- [atom-beautify](https://atom.io/packages/atom-beautify)
    - Beautify HTML, CSS, JavaScript, PHP, Python, Ruby, Java, C, C++, C#, Objective-C, CoffeeScript, TypeScript, Coldfusion, SQL, and more in Atom

- [linter-htmlhint](https://atom.io/packages/linter-htmlhint)
    - Helps correct and clean up HTML documents by fixing markup errors and upgrading legacy code to modern standards.

    - **Before we can use this, we'll need to run `npm install htmlhint --global`.**
- [linter-scss-lint](https://atom.io/packages/linter-scss-lint)
    - Helps you correct errors in your SCSS.

    - **Before we can use this, we'll need to run `gem install scss_lint`.**
    
- [linter-eslint](https://atom.io/packages/linter-eslint)
    - Helps you correct errors and some bad practices in your JavaScript.
    
    - **Before we can use this, we'll need to run `npm install eslint --global`.**

- [livereload](https://atom.io/packages/livereload)
    - Watches for changes in files and automatically reloads the associated browser page.

    - **Before we can use this, we need to install the [LiveReload extension for Chrome](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei?hl=en).**
    - After installing this extension, in Chrome, navigate to `Tools` > `Extensions` > `LiveReload` and enable the "Allow access to file URLs" checkbox.
    - Look in the status bar at the very bottom of the Atom window. You will see "LiveReload: Off". We need to turn it on. So, navigate to `Packages` > `LiveReload` > `Toggle Server`. The status will change to "LiveReload: XXXXX" (where XXXXX will be a port number). Click the status to copy a link to the LiveReload JavaScript file to your clipboard. Use that link in a script tag at the bottom of any HTML file you want to refresh automatically.
- [atom-wrap-in-tag](https://atom.io/packages/atom-wrap-in-tag)
    - Select text you want to wrap in an HTML tag, and hit Alt + Shift + w. Then type the name of tag ('div', 'script', etc.), and both the opening and closing HTML tags will be created for you.

- [autoclose-html](https://atom.io/packages/autoclose-html)
    - Automatically adds closing tags when you complete the opening tag.

- [color-picker](https://atom.io/packages/color-picker)
    - Right-click somewhere you need some code to represent a color. Select Color Picker and pick a color you like. Hit Enter and you're done.

- [pigments](https://atom.io/packages/pigments)
    - Displays the color of a color code as the background color behind the color code itself, so you can see the color at a glance.

- [rainbow-delimiters](https://atom.io/packages/rainbow-delimiters)
    - Highlights matching pairs of parentheses, brackets, and braces on either side of your cursor. Each pair has its own color so you can more-easily tell which matches which!

- [minimap](https://atom.io/packages/minimap)
    - Provides a visual overview of a file's full source code, for ease of moving about in long files.

- [minimap-highlight-selected](https://atom.io/packages/minimap-highlight-selected)
    - Highlights all occurrences of a selected word.

- [todo-show](https://atom.io/packages/todo-show)
    - TODO-show reveals comments scattered through your project containing keywords such as TODO, IDEA, NOTE, CHANGED (and others). Use one of those keywords and TODO-show will keep track of each one and where you put it.

- [auto-detect-indentation](https://atom.io/packages/auto-detect-indentation)
    - Automatically detects and configures default indentation for each file.

- [emmet](https://atom.io/packages/emmet)
    - Provides tools for automating repetitive HTML tasks. You'll want to ignore this for now until you have grown comfortable with both HTML and CSS (see https://emmet.io/).

- [rest-client](https://atom.io/packages/rest-client)
    - Lightweight REST client for testing APIs. You'll can use this later in the course.

- And a few dependencies necessary for the above plugins to use: [linter](https://atom.io/packages/linter), [linter-ui-default](https://atom.io/packages/linter-ui-default), [intentions](https://atom.io/packages/intentions), and [busy-signal](https://atom.io/packages/busy-signal).

Review the linked documentation for those when you get a chance to discover more about how they're used and how you can tweak them for your projects.

Also:

 - If you don't see line numbers of the left side of your files, use Cmd-Shift-P to open the Command Palette. Type "line numbers" and hit Enter to toggle the "Show Line Numbers" setting to enabled.
 - Hit Cmd-Comma on your keyboard to open Preferences, navigate to Packages, type "autosave" in the text box at the top. Click Settings and put a checkmark next to Enabled.

### Set up Git to use Atom for long commit messages

- Run `git config --global core.editor "atom --wait"`

# Other Mac niceties

Since many of you are also new to the Mac, I wanted to throw in some other helpful Mac tips.

None of these are _required_, but they're nice-to-haves.

* **An app launcher:** Hunting around your Mac for a particular application to open gets tedious fast. You can use the built-in Spotlight (typically available via `⌘-Space`). Or you can use a purpose-built app launcher like [Alfred](http://www.alfredapp.com). In general, I find specific app launchers like Alfred (generally available via `Command-Space`) a bit snappier and they tend to have additional features that you might find handy.
* **A password manager:** You're going to have a ton of passwords floating around and the typical options - one password for them all, or trying to remember them all - are both _horribly_ unsafe. Password managers such as [KeePass](http://keepass.info/download.html) (locally-installed only, so you'll have to backup your password database yourself), [1Password](https://agilebits.com/onepassword) (recommended, but pricey - $35-$50), [Dashlane](http://lp.dashlane.com/cjv2/?utm_source=adwords&utm_campaign=US_Search_Brand_Exact&utm_medium=15594053097&utm_term=dashlane&gclid=CPWqiLWyl8YCFQYuaQodm0MA1g), or [LastPass](https://lastpass.com) will make your life _significantly_ better and much more secure.
* **A better Terminal:** The default Terminal application on your Mac is _fine_, really. But if you want to take it a step further, I can highly recommend [iTerm 2](https://www.iterm2.com). Bonus: It's _free_. Note: Download the test release (iTerm2 3.0.10 beta (OS 10.8+))

## What _not_ to install

There is only a single application we're going to ask you to _not install_ during class:

[GitHub for Mac](https://mac.github.com).

It's a fine app, but for class purposes, we want to learn Git from the bare metal. That way, said the GitHub desktop app actually makes sense if you decide to use it later.


<ul id="footnotes">
	<li><a href="#homebrew-token" id="homebrew">1</a>: For a bit of background, homebrew is a "package manager" for OSX. Package managers are commonly found on Linux servers and operating system to make the installation of command line programs easier. On the Mac, homebrew does much the same thing. <a href="#homebrew-token">Back</a></li>
</ul>
