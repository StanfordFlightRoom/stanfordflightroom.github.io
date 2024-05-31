Website source for the [Stanford Flight Room](https://stanfordflightroom.github.io/)

How to set up GitHub pages locally with Jekyll:
https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/

Run the site locally with:
```
$ bundle exec jekyll serve
```


## Development Environment Setup

First follow [these instructions](https://jekyllrb.com/docs/installation/) to install Ruby and Jekyll.

Then clone the repository and install the dependencies:
```bash
bundle install
```

Then you can run the site locally with:
```bash
bundle exec jekyll serve
```

### Debugging

If you get the error `LoadError: cannot load such file -- webrick` you may need to install the `webrick` gem:
```
bundle add webrick
bundle install
```