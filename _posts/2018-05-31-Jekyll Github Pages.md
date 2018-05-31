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

The manual is not very clear about the location of jekyll sites: are they beneath <site>? are they aside <site>?
I guess the latter since I would need git within git otherrwise. So use github UI to create site-jekyll-test
```sh
git clone site-jekyll-test
cd site-jekyll-test
git checkout -b gh-pages

  


**Notes**
- bundle install failed:  
  correction: do ```sudo apt install zlig1g-dev```
- short note about gem and bundle:
  - bundle maintains specific dependencies for the specific project in file Gemfile.lock;
  - gem specifies dependencies more loosely, and provides an executable for many projects.
  - if you want to create an app, then you want to commit Gemfile.lock; otherwise not.
- The manual is not very clear about the location of jekyll sites: are they beneath <site>? are they aside <site>?
  I opted for the latter since I would need git within git otherrwise 
  
