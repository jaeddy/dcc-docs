# Setup


This document details the setup instructions required to develop DCC based projects. Note that the instructions are for both frontend and backend development. It assumes that the developer is using MacOS Sierra or above.

Once complete, please see [general](/software/development/general.md) for general conventions used during development.

## Homebrew

Homebrew, `brew`, is the defacto package manager for MacOs. Most software described here requires it. 

To install follow the directions below:

[http://brew.sh/](http://brew.sh/)

## Cask

It is recommended to install all applications with Cask to promote automation (hopefully one day this page can be scripted).

[https://caskroom.github.io/](https://caskroom.github.io/)

To install:

```shell
brew tap caskroom/cask
```

## Slack

We use Slack almost entirely for internal communication, so install this ASAP.

```shell
brew cask install slack
```

## XCode and Command Line Tools

Follow the instructions below:

[http://railsapps.github.io/xcode-command-line-tools.html](http://railsapps.github.io/xcode-command-line-tools.html)

Alternatively, install XCode from AppStore and execute the following (untested):

```shell
xcode-select --install
```

## Java

Install Java 8:

```shell
brew cask install java
```

Add the following to `~/.bash_profile`:

```shell
export JAVA_HOME="$(/usr/libexec/java_home -v 1.8)"
```

Source `~/.bash_profile` or open a new terminal and ensure this reports Java 8:

```shell
java -version   
                                                                                                                                         
java version "1.8.0_31"
Java(TM) SE Runtime Environment (build 1.8.0_31-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.31-b07, mixed mode)
```

## Elasticsearch

```shell
brew install elasticsearch14
brew switch elasticsearch14 1.4.4
```

### Head Plugin

```shell
/usr/local/Cellar/elasticsearch/1.4.4/libexec/bin/plugin --install mobz/elasticsearch-head
```

## MongoDB

```shell
brew install mongo
brew switch mongo 2.4.4-x86_64
```

## Git

```shell
brew install git
```

## HubFlow

```shell
brew install hubflow
```

See [https://github.com/icgc-dcc/dcc-portal/blob/develop/CONTRIBUTING.md](https://github.com/icgc-dcc/dcc-portal/blob/develop/CONTRIBUTING.md) for details on how we use this.

## GitHub

### Setup

Create an account and send to [@btiernay](https://oicr-icgc.slack.com/messages/@btiernay/).

## Maven

### Installation 

Install Maven 3.2.1 or what is specified in [icgc-dcc/dcc-parent/pom.xml](https://github.com/icgc-dcc/dcc-parent/blob/develop/pom.xml#L1340) `maven-enforcer-plugin.requireMavenVersion`

```shell
brew install maven
brew switch maven 3.2.1
```

To check your installation, run:

```shell
mvn -v

...
Java version: 1.8.0_31, vendor: Oracle Corporation
...

```

## Eclipse

### Installation

Download and install Eclipse 4.6.x or latest for Java EE developers:

[http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)

Alternatively, you may try the following (untested):

[http://macappstore.org/eclipse-jee/](http://macappstore.org/eclipse-jee/)

```shell
brew cask install eclipse-jee
```

### Settings

Install and configure IDE settings:

[https://github.com/icgc-dcc/dcc-cm/tree/develop/ide](https://github.com/icgc-dcc/dcc-cm/tree/develop/ide)

### Lombok Support

A number of the DCC projects are using [Lombok](https://projectlombok.org/) to reduce boilerplate code (e.g., getters, setters, `toString()`, `hashCode()`, `equals()`, `static Logger log`, etc.). This is seemless to `javac` via `mvn`, but the Java 6 [transformations](http://notatube.blogspot.ca/2010/12/project-lombok-creating-custom.html) will not be reflected in Eclipse which will in turn cause compilation errors in your editor. To fix this, execute 

```shell
wget http://projectlombok.googlecode.com/files/lombok.jar
java -jar lombok.jar
```

And point it to your Eclipse installation. See [http://projectlombok.org/features/index.html](http://projectlombok.org/features/index.html) for details. 

### Maven m2e

Activate source downloading in the maven plugin, tick the following: 

**Preferences > Maven > Maven Download Artifact Sources**

Open to XML view, tick the following:

**Preferences > Maven > User Interace > Open XML page in the POM editor by default**

Hide warnings for incomplete mappings, tick the following:

**Preferences > Maven > User Interace > Hide warnings for incomplete mapping**

### Java Static Import Favorites

Add some classes to your favorite static imports via:

**Preferences > Java > Editor > Content Assist > Favorites**:

*   Guava's `Preconditions`
*   PowerMock's `PowerMockito`
*   Mockito's `Mockito`
*   AssertJ's `org.assertj.core.api.Assertions.*`

### Plugins

#### MoreUnit Plugin

Useful JUnit Eclipse integration extensions can be installed by following the instructions here:

[http://moreunit.sourceforge.net/](http://moreunit.sourceforge.net/)

Or try the following (untested):

```shell
eclipse -nosplash -application org.eclipse.equinox.p2.director -repository http://moreunit.sourceforge.net/update-site/ -installIU org.moreunit.feature.group 
eclipse -nosplash -application org.eclipse.equinox.p2.director -repository http://moreunit.sourceforge.net/update-site/ -installIU org.moreunit.mock.feature.group
```

#### FindBugs Plugin

Locally run FindBugs within your IDE:

[http://findbugs.sourceforge.net/manual/eclipse.html](http://findbugs.sourceforge.net/manual/eclipse.html)

Or try the following (untested):

```shell
eclipse -nosplash -application org.eclipse.equinox.p2.director -repository http://findbugs.cs.umd.edu/eclipse/ -installIU edu.umd.cs.findbugs.plugin.eclipse.feature.group
```

#### Grep Console Plugin

Plugin for colorizing and filtering the Eclipse console. Follow the instructions here (configuration is available in the Eclipse section):

[http://marian.schedenig.name/projects/grep-console/](http://marian.schedenig.name/projects/grep-console/)

Or try the following (untested):

```shell
eclipse -nosplash -application org.eclipse.equinox.p2.director -repository http://findbugs.cs.umd.edu/eclipse/ -installIU edu.umd.cs.findbugs.plugin.eclipse.feature.group
```

## VS Code

Most frontend developers choose to use the VS Code IDE for development.

To install:

```shell
brew cask install vscode
```

## Node.js

This is only required for projects that use a UI built by `npm` (e.g. `dcc-docs`, `dcc-portal`, `dcc-submission`, `dcc-dev`, etc.)

```shell
brew install nvm
```

Then read [https://davidwalsh.name/nvm](https://davidwalsh.name/nvm) for usage information.

Then follow instructions in each GitHub's repo for the required node / npm versions (e.g. [https://github.com/icgc-dcc/dcc-portal/tree/develop/dcc-portal-ui](https://github.com/icgc-dcc/dcc-portal/tree/develop/dcc-portal-ui)).

## Projects

After installing the above, navigate to the project(s) that you will be working on in [GitHub](https://github.com/icgc-dcc) and follow the top-level `README.md`s and linked sub-module `README.md`s.

### All Projects

Clone a project from GitHub:  

```shell
cd ~/Workspaces/dcc
git clone git@github.com:icgc-dcc/<project>.git
```

Init Git-flow (default settings):  

```shell
cd <project>
git hf init
```

### Eclipse Projects

To import an Eclipse based project, click on the following in the file menu:

**File > Import > Maven > Existing Maven Projects**

## Reference Data

You will need to download the DCC reference genome from our [Artifactory](https://artifacts.oicr.on.ca/artifactory) server: 

[https://artifacts.oicr.on.ca/artifactory/dcc-dependencies/org/icgc/dcc/dcc-reference-genome/GRCh37.75.v1/](https://artifacts.oicr.on.ca/artifactory/dcc-dependencies/org/icgc/dcc/dcc-reference-genome/GRCh37.75.v1/)

and extract it to `/tmp`. Ensure that the contents of the file are not in a nested folder and are in the tmp folder. Once extracted, symlink `GRCh37.fasta` to `GRC37.75.fasta` and `GRCh37.fasta.fai` to `GRCh37.75.fasta.fai` by executing the following:

```shell
ln -s GRC37.75.fasta GRC37.fasta
ln -s GRC37.75.fasta.fai GRC37.fasta.fai
```

## Utilities

Consider all of these utilities optional, but highly recommended.

### Trailer

Track pull requests and issues across repositories, directly in your Notification Center or on any Apple device.

[https://ptsochantaris.github.io/trailer/](https://ptsochantaris.github.io/trailer/)

```shell
brew cask install trailer
```

### Docker

Docker for Mac:

[https://docs.docker.com/engine/installation/mac/](https://docs.docker.com/engine/installation/mac/)

Or try (untested):

```shell
brew cask install docker-beta
```

### MacDown

MacDown is an open source Markdown editor for OS X, released under the MIT License. It is heavily influenced by Chen Luo’s Mou.

[http://macdown.uranusjr.com/](http://macdown.uranusjr.com/)

```shell
brew cask install macdown
```

### iTerm2

Very powerful terminal emulator for Mac:

[http://www.iterm2.com/](http://www.iterm2.com/)

```shell
brew cask install iterm2 
```

### zsh

Great shell alternative that is mostly compatible with Bash:

```shell
brew install zsh zsh-completions
```

### Oh My Zsh

Plugin system for `zsh`

[https://github.com/robbyrussell/oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)

Add the following to `~/.zshrc` / `~/.bash_profile`:

```shell
plugins=(git git-hubflow mvn brew nvm node npm vagrant httpie)
```

### httpie

Modern alternative to `curl`:

[https://github.com/jkbrzt/httpie](https://github.com/jkbrzt/httpie)

```shell
brew install httpie
```

### jq

`jq` is a lightweight and flexible command-line JSON processor:

[https://stedolan.github.io/jq/](https://stedolan.github.io/jq/)

```shell
brew install jq
```

## Other

Other useful things:

- [https://danielmiessler.com/blog/first-10-things-new-mac](https://danielmiessler.com/blog/first-10-things-new-mac)
- [spf13](http://vim.spf13.com/)
- `brew cask install google-chrome`
- `brew cask install virtualbox`
- `brew cask install vagrant`