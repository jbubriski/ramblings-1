#Setting up a blog using GitHub Pages

I just finished setting up my blog. It's still very much green, as am I, still I decided to begin my ramblings.

###What is GitHub Pages
GitHub Pages is a static site hosting service, [so they say](https://help.github.com/articles/what-is-github-pages/). The idea is basically to have a static site hosted by GitHub Pages from a github repository. Emphasis here on **static site**. It doesn't support _server side_ code.

You might want to take a look at the [terms of service](https://help.github.com/articles/github-terms-of-service/) and [community guidelines](https://help.github.com/articles/github-community-guidelines/), just so everyone's clear. 

Jekyll (not the Doctor :D) powers GitHub Pages. Jekyll is a simple, blog-aware, static site generator. They [did a better job](https://jekyllrb.com/docs/home/#so-what-is-jekyll-exactly) at explaining it than I would, so I'll just leave it at that. 

We are going to set up our GitHub blog to run locally, then push it to github.

Assumptions: 
- You know and have used github before. 
- You're comfy with the terminal.

Ok, shall we begin...

### Run the site locally: 

# Install Jekyll and Bundler gems via RubyGems
~ $ gem install jekyll bundler

# Create a new Jekyll site at ./name_of_blog
~ $ jekyll new name_of_blog

# Change into your new directory
~ $ cd name_of_blog

# Edit your Gemfile; 
  # remove/comment the following line:
  gem "jekyll", "3.4.1"

  # delete the `#` at the beginning of this line:
  gem "github-pages", group: :jekyll_plugins

# Rebuild the snapshot from scratch
~ $ bundle update

# Run the site locally
~ $ jekyll serve

# Now browse to http://localhost:4000

The site should be running locally at that address.


### Push the site to github

# Initialize your site directory as a Git repository
~ $ git init

At this point, we assume we have a created a spanking new repo on Github.

# Connect your remote repository on GitHub to your local repository
~ $ git remote add origin https://github.com/_username-or-organization-name_/_your-remote-repository-name_.git

One can make certain edits at this stage. some edits might include 
- editing the blog title / email / description / etc in the _config.yml file
- creating a README.md file
- etc


# Add or stage your changes
~ $ git add -p

The `-p` option steps through your changes, allowing you see exactly what was changed and giving you the option to accept or reject that change

# Commit your changes with a comment
~ $ git commit -m "Edit or update site"

# Push your changes to your remote repository on GitHub. 
Because this is the the first push to the newly created remote branch, we add the upstream tracking reference using the `-u` flag
After pushing, this links the local branch with the remote branch, and the commands `git pull` or `git push` can be used without any arguments
~ $ git push -u origin master

At this point, all your changes should be in the remote repository. To take our site live, 
- Click the "Settings" button at the top right
- Scroll to the GitHub Pages, Source section, click on the select-box and select master branch
- Click on the Save button to the right of the select-box


You should see the message: 
Your site is published at https://_username_.github.io/_your-remote-repository-name_/ 

If you don't see this message, please refresh the page and check again.

Your page should be live. 

Note: As of 5th March, 2017, the gem `github-pages` comes with jekyll version 3.3.1
Changing the theme in the repository's settings page causes the app to fail. Removing the includes in the about.md page fixes this