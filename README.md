# Overview

- Git repo is here: https://github.com/vdavid/blog.veszelovszki.hu-hexo/
- Netlify deploy settings are here: https://app.netlify.com/sites/gallant-hodgkin-575fcf/deploys

# Common tasks
## Creating new new blog post

- Open my [article ideas spreadsheet](https://docs.google.com/spreadsheets/d/1oxPuH4ZkkKty4QoBaoM27OCdgCCKFu4WHwZYn9XLn1M/edit#gid=0)
- Decide on the topic
- Run<br>`hexo new post <article-slug>`
- Open newly created md file and enter the article title in the header.

## Testing
- Use `hexo server` then see the site at http://localhost:4000. It will auto-update (press F5 after changes). 

## Adding assets
- Images and other files: Just paste them to the `source/_posts/{article-slug}` folder
- Pages: Run<br>`hexo new page <page-slug>`

## Markdown syntax

- Link: `[text](url)`
- Image: `{% asset_img example-image.jpg This is an example image %}`
  (Put image in a folder with the same name as the post filename in `_posts`)
- Asset link: `{% asset_link slug title %}`
- Asset path: `{% asset_path filename.ext %}`
- More tips in [theme documentation](https://github.com/LouisBarranqueiro/hexo-theme-tranquilpeak/blob/master/DOCUMENTATION.md).

## Publishing a blog post

- Run<br>`hexo generate`
- Push it to `master`.
- The blog is at https://blog.veszelovszki.hu.

## Updating the theme

- Download latest version from its [website](https://github.com/LouisBarranqueiro/hexo-theme-tranquilpeak/blob/master/)
- Delete old version and copy new one to the `themes` folder.
- Review _config.yml line by line, revert most (or all) changes
- In `languages/en.yml`, make sure not to overwrite the `author.bio` and `author.job` texts at the bottom.
- Keep the updated Merriweather fonts, they include Hungarian accents ([Downloaded from here](https://fonts.google.com/specimen/Merriweather?selection.family=Merriweather:300,300i,400,400i,700,700i))