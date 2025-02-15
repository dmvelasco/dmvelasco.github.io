---
layout: post
title: Academicons with beautiful-jekyll
subtitle: How to include academic icons for linking to academic websites
---

### Using [Academicons](http://jpswalsh.github.io/academicons/) with the [beautiful-jekyll](https://github.com/daattali/beautiful-jekyll) theme

For an academic or anyone in an academic-like field there are several important social or informational websites in common use that host information on your academic history, such as [Google Scholar](scholar.google.com). 
Linking to this information is crucial, yet icons representing these sites are not available through the icon repository used by beautiful-jekyll, [Font Awesome](https://fontawesome.com). 
However, these academic icons are available from Academicons. 
It was not immediately clear how to utilize Academicons with the clean, and otherwise user friendly, beautiful-jekyll theme. 
After some searching and a few failed attempts, I hit upon how to make it work. 
Below I have shared the steps taken to utilize Academicons with beautiful-jekyll, without needing to hardcode each one into the theme.

![Academicons](/img/academicons_and_beautiful-jekyll.png)

#### Step 1 - download Academicons
Download Academicons from [http://jpswalsh.github.io/academicons/](http://jpswalsh.github.io/academicons/) and unzip the file

#### Step 2 - upload files to beautiful-jekyll theme
From the Academicons `css` directory add the `academicons.css` and `academicons.min.css` files to your beautiful-jekyll `css` directory.
	
Upload the Academicons `fonts` directory to your main beautiful-jekyll directory. The `fonts` directory includes the files: `academicons.eot`, `academicons.svg`, `academicons.ttf`, and `academicons.woff`.

#### Step 3 - modify files
Modify the file `_data/SocialNetworks.yml` so each entry has a type element, one for fontawesome (`fa`) or academicons (`ai`) such that each entry looks like either
```
github:
     name: "GitHub"
     baseURL: "https://github.com/"
     type: "fa"
     icon: "fa-github"
```
or
```
scholar:
    name: "Google Scholar"
    baseURL: "https://scholar.google.com/"
    type: "ai"
    icon: "ai-google-scholar"
```
Add any desired Academicons with the above format using the icon designation from [Academicons](https://jpswalsh.github.io/academicons/) just as you would any Font Awesome icon designation.

Modify the file `_includes/footer.html` so that the type element from `_data/SocialNetworks.yml` is encoded properly for the element icon.
Change `fa` in `{% raw %}<i class="fa {{ element.icon }} fa-stack-1x fa-inverse"></i>{% endraw %}` to `{% raw %}{{ element.type }}{% endraw %}` so the line reads `{% raw %}<i class="{{ element.type }} {{ element.icon }} fa-stack-1x fa-inverse"></i>{% endraw %}`.

Modify the file `_layouts/base.html` after the `common-ext-css:` line by adding the line `- "/css/academicons.css"` before `- "//maxcdn.bootstrapcdn.com/font-awesome/4.6.0/css/font-awesome.min.css"` and looks like the following.
```
common-ext-css:
  - "/css/academicons.css"
  - "//maxcdn.bootstrapcdn.com/font-awesome/4.6.0/css/font-awesome.min.css"
```

Modify the `_config.yml` file to add your academic social networks of interest in the `social-networks-links` section. 
Follow the existing formatting by adding the academic social network name and a colon followed by your username.

#### Step 4 - refresh and enjoy
Your academic icon links should now be included in your page footer. Yay you!
