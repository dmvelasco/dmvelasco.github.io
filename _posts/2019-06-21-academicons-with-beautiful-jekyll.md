---
layout: post
title: Academicons with beautiful-jekyll
image: /img/academicons_and_beautiful-jekyll.png
---

### Using [Academicons](http://jpswalsh.github.io/academicons/) with the [beautiful-jekyll](https://github.com/daattali/beautiful-jekyll) theme

For an academic or anyone in an academic-like field there are several important social or informational websites in common use, such as [Google Scholar](scholar.google.com), that host information on your academic history. 
Linking to this information is crucial yet it was not immediately apparent how to incorporate using Academicons with the clean and otherwise user friendly beautiful-jekyll theme. 
After some searching and a few failed attempts, I hit upon what worked, and have shared below the steps needed to utilize Academicons with beautiful-jekyll with no need to hardcode each one into the theme.

#### Step 1 - download Academicons
Download Academicons from http://jpswalsh.github.io/academicons/ and unzip the file

#### Step 2 - upload files to beautiful-jekyll theme
From the Academicons `css` directory add the `academicons.css` and `academicons.min.cssfiles` to your beautiful-jekyll css directory.
	
Upload the Academicons `fonts` directory to your main beautiful-jekyll directory. The `fonts` directory includes the files: `academicons.eot`, `academicons.svg`, `academicons.ttf`, and `academicons.woff`.

#### Step 3 - modify files
Modify the file `_data/SocialNetworks.yml` so each entry has a type element, one for fontawesome (`fa`) or academicons (`ai`) such that each entry looks either
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
Add any desired Academicons with the above format using the icon designation from [Academicons](https://jpswalsh.github.io/academicons/).

Modify `_includes/footer.html` so that the type element from `_data/SocialNetworks.yml` is coded properly for the element icon.
Change `fa` in `<i class="fa {{ element.icon }} fa-stack-1x fa-inverse"></i>` to `{{ element.type }}` so the line reads `<i class="{{ element.type }} {{ element.icon }} fa-stack-1x fa-inverse"></i>`.

Modify `_layouts/base.html` after the `common-ext-css:` line to	add the line `- "/css/academicons.css"` before `- "//maxcdn.bootstrapcdn.com/font-awesome/4.6.0/css/font-awesome.min.css"`. Both lines should have the same level of indentation.
