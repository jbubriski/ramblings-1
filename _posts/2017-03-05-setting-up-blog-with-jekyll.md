---
layout: post
title:  "Blogging with Jekyll!"
categories: jekyll github-pages
---

# Setting up a blog on GitHub Pages with Jekyll

I just finished setting up my blog. It's still very much green, as am I, still I decided to begin my ramblings.

### What is GitHub Pages
GitHub Pages is a static site hosting service, [so they say](https://help.github.com/articles/what-is-github-pages/). The idea is basically to have a static site hosted by GitHub Pages from a github repository. Emphasis here on **static site**. It doesn't support _server side_ code.

You might want to take a look at the [terms of service](https://help.github.com/articles/github-terms-of-service/) and [community guidelines](https://help.github.com/articles/github-community-guidelines/), just so everyone's clear. 

~~Dr~~ Jekyll powers GitHub Pages. Jekyll is a simple, blog-aware, static site generator. They [did a better job](https://jekyllrb.com/docs/home/#so-what-is-jekyll-exactly) at explaining it than I would, so I'll just leave it at that.

We are going to set up our GitHub blog to run locally, then push it to github.

Assumptions: 
- You know about and have used GitHub before; which would imply
- You're comfy with the terminal.

Ok, shall we begin...

<br>

---

#### Run GitHub blog locally:

In your terminal;

```bash
# Install Jekyll and Bundler gems via RubyGems
~$ gem install jekyll bundler

# Create a new Jekyll site at ./name_of_blog. This would be the root directory of your blog
~$ jekyll new name_of_blog

# Change into your new directory
~$ cd name_of_blog
```

Next, edit your Gemfile. Within `name_of_blog` directory is a file called Gemfile. Open it with your favorite editor;

Remove or comment Jekyll gem:

```bash
# Comment jekyll gem
# gem "jekyll", "3.4.1"
```

Delete the `#` at the beginning of this line:

```bash
gem "github-pages", group: :jekyll_plugins
```

Then update bundle and run the server

```bash
# Rebuild snapshot
~/name_of_blog$ bundle update

# Run the site locally
~/name_of_blog$ jekyll serve
```

Now go to http://localhost:4000. The site should be running locally at that address.

<br>

---

#### Push the site to github

```bash
# Initialize your site directory as a Git repository
~/name_of_blog$ git init
```

At this point, we assume we have created a spanking new repo on Github. If we haven't, here's how to [create a repo](https://help.github.com/articles/create-a-repo/).

```bash
# Connect your remote repository on GitHub to your local repository
~/name_of_blog$ git remote add origin https://github.com/username-or-organization-name/your-remote-repository-name.git
```

One can make certain edits at this stage. some edits might include:

* editing the blog title / email / description / etc in the `_config.yml` file
* creating a README.md file
* etc


```bash
# Add or stage your changes
~/name_of_blog$ git add -p
```

The `-p` option steps through your changes, allowing you see exactly what was changed and giving you the option to accept or reject that change

```bash
# Commit your changes with a comment
~/name_of_blog$ git commit -m "Edit or update site"
```

Push your changes to your remote repository on GitHub. Because this is the the first push to the newly created remote branch, we add the upstream tracking reference using the `-u` flag
After pushing, this links the local branch with the remote branch, and the commands `git pull` or `git push` can be used without any arguments

```bash
# Pushing changes...
~/name_of_blog$ git push -u origin master
```

At this point, all your changes should be in the remote repository. To take our site live,

* Click the "__Settings__" button at the top right
* Scroll to the __GitHub Pages__, __Source__ section, click on the select-box and select `master branch`
* Click on the __Save__ button to the right of the select-box


You should see the message: 
`Your site is published at https://username.github.io/your-remote-repository-name/`

If you don't see this message, please refresh the page and check again.

Your blog should be live.

```markdown
__Note__: As of 5th March, 2017, the gem `github-pages` comes with jekyll version 3.3.1
Changing the theme in the repository's settings page causes the app to break. 
Removing the includes in the about.md page fixes this.
```