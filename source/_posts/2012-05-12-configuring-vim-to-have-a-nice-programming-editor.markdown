---
layout: post
title: "Configuring Vim to have a nice programming editor"
date: 2012-05-12 18:18
comments: true
categories: [vim, janus, solarized, programming] 
---

My intention is not to enter into the eternal debate of what is better
to use: an *IDE* or a powerful text editor like *Vim* or *Emacs*,
this depends on the task, your experience, your timing
*(if you're in a project with short time deadlines)*, your wishes to learn
something new and get into troubles... The thing is that believe or not
sometimes less is more (like the bash pager 'less' that is better than
'more'), sometimes the best way to focus and get things done is to get
rid of all the super features and functions that many programs have and
return to the simple life. For example: right now I'm writing this post
in plain text using a very simple markup language called *Markdown*
using Vim as editor, the simplicity of the whole picture *(dont' get
confused, this doesn't mean lack of features)* helps me to
focus, Why? because I'm not being bother by things like the WYSIWYG
editor *(put a name)* has ruined the format, or all the fraking
notifications of the web browser, or if my cat threw down the router
when I was going to save the article into my beloved web blog platform  *(put
another name here)*. I'm just focus on what I'm writing in plain old
english using a delightful text editor.
<!-- more -->
So now, returning to the subject we're going to configure our beloved
editor Vim with a set of plugins that will ease our life as developers
and bloggers wannabe. Vim is like this little houses that from the outside look
very humble and small but when you enter you find yourself into a
huge palace. The truth is that configuring Vim to enable the features that
you want as you want them to be can be a very demanding task, that's why for many
years people have been sharing their configuration scripts, but
nowadays we also have compilation of features (we can think of them as a
distribution in the linux world) for installing and
forgetting of the vast majority of the configuration tasks.

### Janus
[Janus](https://github.com/carlhuda/janus) is a vim distribution that packs a lot of popular plugins and mappings
providing a minimal and enjoyable working environment.
Janus come with a set of vim customizations as the following:

* Line numbers
* Ruler
* Soft 2-spaces tab
* Shows trailing whitespaces as "."
* Searching is highlighted, incremental and case insensive
* Always show a status line
* A lot lot more.

Also provides some of the following plugins:

* NERDCommenter: allows you to wrangle your code comments, regardless of
  filetype
* NERDTree: shows a very nice file explorer tree inside vim
* SuperTab: autocompletation based on the context
* Syntastic: a syntax checking plugin
* Fugitive: git support
* etc, etc, etc

I advice you to check the web page project for a more complete
description of the capabilities of Janus.

#### Installation
As easy as 1,2,3 using the automatic installer, which backs up any vim
configuration file that you may already have.
{% codeblock lang:bash %}
$ curl -Lo- http://bit.ly/janus-bootstrap | bash
{% endcodeblock %}

For more info about customizing Janus, I recommend visiting the project
web page at <https://github.com/carlhuda/janus>

### Solarized
If you are into web development specially if you are a *mac fanboy*, there
are many chances that you already know
[Solarized](http://ethanschoonover.com/solarized) a very nice color
palette with a incredible well picked set of colors. Solarized comes
basically in two flavors: **The dark style** and the **light style**. *Janus*
has a built in support for solarized but it doesn't work as expected
because the color settings apparently are wrong.
Here you have the code snippet that you have to put in
**~/.vimrc.after**

{% codeblock lang:bash %}
" sets up solarized properly
let g:solarized_termcolors=256
set t_Co=16
set background=dark
colorscheme solarized
{% endcodeblock %}

Now you should be asking How it looks like?, well if you pay attention to
the nice colors in the previous code blocks you already saw it.
*Octopress* my blogging platform use it by default for the code blocks. 
Now for make it more clear here you have a longer block with an example piece of code 
(using solarized as color scheme), this code is taken from one of my 
projects (A text simplifier platform):
{% codeblock Example Java code lang:java %}
/**
 * This transform one sentence per line into something that the parser can
 * process
 */
 private void executeParsingProcess() {
 
   String path = PipelineHelper.getResourcePath("/ext-resources/input");
   
   logger.info("Mate-tools input: " + path);

   File folder = new File(path);

   if (!folder.isDirectory()) {
     return;
   }

   for (File file : folder.listFiles()) {
     String filename = file.getName();

     if (filename.contains(".tok") || filename.contains(".lem") ||
         filename.contains(".tag") || filename.contains(".mtag"))
       continue;
 
     tokenizeRawFile(file);
     lemmatize(file);
     taggify(file);
     mtaggify(file);
     dependencyParse(file);
   }
}
{% endcodeblock %}

Well this is all for today.

Have fun kids.

