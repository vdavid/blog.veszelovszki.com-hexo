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
- Link: `{% asset_link slug title %}`
- Path: `{% asset_path filename.ext %}`
- More tips in [theme documentation](https://github.com/LouisBarranqueiro/hexo-theme-tranquilpeak/blob/master/DOCUMENTATION.md).

## Publishing a blog post

- Run<br>`hexo generate`
- Push it to `master`.
- The blog is at https://blog.veszelovszki.hu.