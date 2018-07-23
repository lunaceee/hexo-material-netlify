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
$ git clone --recursive https://github.com/lunaceee/hexo-material-netlify.git
$ cd hexo-material-netlify
$ npm install
$ hexo server
```
_Notice that the `--recursive` flag is important here, as the `material` theme is [introduced as a submodule](https://stackoverflow.com/questions/3796927/how-to-git-clone-including-submodules)._

Alternatively, you can update submodules manually:
```
cd hexo-material-netlify
git submodule init
git submodule update
```

## Netlify CMS editor workflow
The Netlify CMS `admin` panel is already set up in the repo. You can access it via `yourwebsite.com/admin`, e.g. `localhost:4000/admin`.
To understand more about the configuration, check out [Netlify CMS docs](https://www.netlifycms.org/docs/intro/).

## Internationalization with Language-Based Redirects
Netlify supports a wide range of [Redirect & Rewrite Rules](https://www.netlify.com/docs/redirects/). 
Our example site is featuring the [Language-based redirecs](https://www.netlify.com/docs/redirects/#geoip-and-language-based-redirects), which comes in handy for any sites that support multiple languages.

To enable language based redirects, make sure the following configurations in your root `_config.yml` file is included:

```
language: 
  - [language_01]
  - [language_02]
  - [language_03]
```

```
i18n_dir: :lang
```
In the markdown file, make sure you specify the language of the post in the front matter:
```
lang: [language of preference]
```

Now, if your browser language is set to `zh-cn`, you'll be taken to https://yourwebsite.com/zh-cn/ automatically. You can apply this technique for any other languages. 

### Display a single language on the home page
By default, our theme shows posts in all languages on the home page. For the purpose of language based redirects, ideally we only want to show posts written in the prefered language. I found a nice plug-in [hexo-generator-index-i18n](https://github.com/xcatliu/hexo-generator-index-i18n) to filter out the unrelated posts. So if you go to https://yourwebsite.com/zh-cn/, you'd only see the posts written in Chinese. Same applies to all other languages.
