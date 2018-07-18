# Hexo + Netlify CMS Starter

## Intro
This is an example site built with [Hexo](https://hexo.io/) and [Netlify CMS](https://github.com/netlify/netlify-cms), based on [Viosey's](https://github.com/viosey) [Hexo material theme](https://github.com/viosey/hexo-theme-material).

[Live demo](https://hexo-material-cms.netlify.com)

## Deploy to Netlify
Use the following deploy button to get your own copy of the repository up and running:

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/lunaceee/hexo-material-netlify&stack=cms)

The Deploy to Netlify button clones a copy of this repository to your own GitHub or GitLab account. You can clone this repository to your computer for local development.

## Local Development
```
$ git clone --recursive https://github.com/lunaceee/hexo-material-netlify.git [REPO_NAME]
$ cd [REPO_NAME]
$ npm install
$ hexo server
```
Notice that the `--recursive` flag is NECESSARY here, as the `material` theme is [introduced as a submodule](https://stackoverflow.com/questions/3796927/how-to-git-clone-including-submodules).

Alternatively, you can update submodules manually:
```
cd [REPO_NAME]
git submodule init
git submodule update
```

## Netlify CMS editor workflow
The Netlify CMS `admin` panel is already set up in the repo. You can access it via `yourwebsite.com/admin`, e.g. `localhost:4000/admin`.
Please refer to [Netlify CMS docs](https://www.netlifycms.org/docs/intro/) for more info.

## Internationalization with Language-Based Redirects
Netlify supports a wide range of [Redirect & Rewrite Rules](https://www.netlify.com/docs/redirects/). 
Our example site is featuring the [Language-based redirecs](https://www.netlify.com/docs/redirects/#geoip-and-language-based-redirects), which comes in handy for any sites that support multiple languages.
For example, the folder structure under our site's root `source` folder is set up like this:
```
    source/
    ├── _data
    │   └── head.json
    ├── _posts
    │   └── hello-world.md
    ├── _redirects
    ├── admin
    │   ├── config.yml
    │   └── index.html
    ├── en
    │   └── about
    │       └── index.md
    ├── es
    │   ├── _posts
    │   │   ├── Platero
    │   │   │   └── platero.jpg
    │   │   └── Platero.md
    │   └── about
    │       └── index.md
    ├── zh-cn
    │   ├── about
    │   │   └── index.md
    │   └── index.md
    └── zh-tw
        └── about
            └── index.md
```

And in my `_redirects` file, I specified the following rule to redirect the URL based on the default browser language:
```
/*  /zh-cn/:splat  302  Language=zh
```

In this specific example, it means if your browser language is set to `zh-cn`, you'll be taken to https://yourwebsite.com/zh-cn/ automatically. You can apply this technique for any other languages. The key is to make sure your folder structure matches the path in your `_redirects` file.