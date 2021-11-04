# Rbenv Cocoapods Install Guide

If you are someone like me who updated the mac to a newer OS and while running cocoapods or cocoapods-keys, ran into problems like:

> Pods not found

OR

> Error while executing gem ... because you don't have persmission ... etc

Then this guide is for you. 

I stumbled upon rbenv and it has made my life easier since then. Basically, rbenv helps you manage your ruby environment. So, we will use it to install a ruby version which goes with Cocoapods `1.11.2` and we will keep it as a global version so we don't have to deal with Mac's own locked ruby going forward.

## Pre-requisites:

1. [Homebrew](https://brew.sh/) ( best package manager for mac. IMO )
2. Xcode commandline tools ( you can use Xcode or download them separately to install them)

## Below are the steps you can follow in your terminal

### 1. install rbenv

```
brew update && brew install rbenv ruby-build
```

#### 1.a. Looking at the terminal output, follow the suggestion if it says to add this line to ~/.zshrc or ~/.bash_profile (if you are using bash) then only add it (optional)

```
export RUBY_CONFIGURE_OPTS="--with-openssl-dir=$(brew --prefix openssl@1.1)"
```

### 2. Initialise rbenv
Add this line in ~/.zshrc or ~/.bash_profile (if you are using bash) to initialise rbenv everytime you open your terminal

```
if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
```

### 3. Install Ruby 
```
rbenv install 2.7.4
```

### 4. Configure and Rehash rbenv 
To use it globally so we don't need to rely on Mac's own ruby version
```
rbenv global 2.7.4
```

Just to make it work properly with the installed ruby version along with some terminal housekeeping
```
source ~/.zshrc && rbenv rehash
```

To confirm if it worked
```
ruby --version
```

### 5. Install Bundler, if you want to install multiple gems for single project (optional)
[Bundler](https://bundler.io/) is like Cocoapods for Ruby to manage it's gems and dependencies.

```
gem install bundler
```

### 6. Install Cocoapods

#### a. Only Cocoapods
```
gem install cocoapods
```

#### b. Install Cocoapods with multiple gems using Bundler (recommended to future proof)

Create the Gemfile
```
bundler init
```

Update the Gemfile to include your gems
```
source 'https://rubygems.org'

gem 'cocoapods', '1.11.2'
gem 'cocoapods-keys', '2.2.1'
gem 'jazzy', '0.14.1'
gem 'xcpretty', '0.3.0'
```

Install these gems
```
bundle install
```

That's it!
