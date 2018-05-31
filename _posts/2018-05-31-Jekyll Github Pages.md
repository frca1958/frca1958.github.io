## Goal
To setup a website using github-pages, and to test it locally.

## Reference Docs
- [Setup github pages locally](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)
- [Learn about Ruby Gems](https://guides.rubygems.org/)
- [Learn about bundler](https://bundler.io/)


## Traces and Notes

```sh
# Use github UI to create git repo 'site-jekyll'
git clone <site-url>
cd <site>
git checkout -b gh-pages
# create Gemfile which installs jekyll
gem install bundler
bundle install
git add Gemfile Gemfile.lock
```

Creation of the jekyll site:
```sh
bundle exec jekyll _3.3.0_ new site_jekyll_test
#you must be in the site-jekyll repo in order to execute this! Even using ```jekyll _3.3.0_ ...``` wont work.
cd site_jekyll_test
```

  


**Notes**
- bundle install failed:  
  correction: do ```sudo apt install zlig1g-dev```
- short note about gem and bundle:
  - bundle maintains specific dependencies for the specific project in file Gemfile.lock;
  - gem specifies dependencies more loosely, and provides an executable for many projects.
  - if you want to create an app, then you want to commit Gemfile.lock; otherwise not.

