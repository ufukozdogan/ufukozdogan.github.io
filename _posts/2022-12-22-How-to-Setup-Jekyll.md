---
title: "Tutorial: Setup Ruby and Jekyll on Apple Silicon"
date: 2022-12-22T00:00:00+00:00
author: Ufuk Ozdogan
layout: post
permalink: /setup-jekyll-on-apple-silicon/
categories: DevOps
tags: [devops, tutorial]
---
M1 and M2 Macs are amazing. They offer great performance paired with a phenomenal stability. But every 
good thing has its negatives and for Macs it's their compatibility. Especially when we're dealing
with DevOps related stuff, it can cause problems easily. Of course we have stuff like Rosetta (you can learn more about that [here](https://www.computerworld.com/article/3597949/everything-you-need-to-know-about-rosetta-2-on-apple-silicon-macs.html)) to get ahead of some problems
but at the end, it's not the definite solution for everything. 

On top of this, these compatibility issues also start to happen when we try to install or modify the system related software like Ruby or Python. Because these types of utilities are also being used (thus pre-installed) by the Darwin core set so we have to proceed carefully in order to install them in the correct way.

## Install Xcode and Homebrew

{% highlight bash %}
xcode-select --install
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
{% endhighlight %}

## Install Ruby 3.0.x
MacOS systems generally come with Ruby 2.x. You can check it with:

{% highlight bash %}
ruby -v
{% endhighlight %}

To install Ruby 3.1.x:

{% highlight bash %}
brew install ruby@3.1
{% endhighlight %}

After that follow the shell output and export the `PATH` according to the terminal you're using. 

Exit the terminal and open up a new one. Type `ruby -v` to make sure it's 3.x.

## Install Jekyll and Bundler

{% highlight bash %}
gem install --user-install bundler jekyll
{% endhighlight %}

And only thing left is to export the `PATH` again for the gems.

{% highlight bash %}
# Learn your SHELL
echo $SHELL
  # For zsh, type:
  echo 'export PATH="$HOME/.gem/ruby/3.0.0/bin:$PATH"' >> ~/.zshrc
  # For bash, type:
  echo 'export PATH="$HOME/.gem/ruby/3.0.0/bin:$PATH"' >> ~/.bash_profile
# Check out the GEM PATH and make sure they all refer to the Ruby 3.x one.
gem env
{% endhighlight %}


After this you're all set. You can either create brand new Jekyll sites or build the existing ones following their guidelines.

## Resources
* [https://github.com/BillRaymond/install-jekyll-apple-silicon](https://github.com/BillRaymond/install-jekyll-apple-silicon)
* [https://utpalkumar.medium.com/how-to-install-jekyll-on-apple-m1-macbook-c87894b7fc70](https://utpalkumar.medium.com/how-to-install-jekyll-on-apple-m1-macbook-c87894b7fc70)