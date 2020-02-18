# osDFS

Open Source Digital Freedom Society

# Contribute
Thank you for your interest in contributing!

# Project Structure

```bash
.
├── _config.yml
├── _data
|   |── events.yml
|   |── officers.yml
|   |── opportunities.yml
|   |── partners.yml
|   |── photos.yml
|   |── tech-challenges.yml
├── _includes
|   ├── banner.html
|   ├── footer.html
|   ├── head.html
|   ├── meetings.html
|   ├── navbar.html
|   ├── scripts.html
|   ├── subscribe.html
├── _layouts
|   ├── blog.html
|   ├── default.html
|   ├── post.html
|   ├── subscribe.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.md
|   └── 2009-04-26-barcamp-boston-4-roundup.md
├── _site
├── css
├── img
├── js
├── .jekyll-metadata
└── index.html
├── other html files # can also be an 'index.md' with valid front matter
```
- `/_data/` -Well-formatted site data should be placed here. The Jekyll engine will autoload all data files (using either the `.yml`, `.yaml`, `.json`, `.csv` or `.tsv` formats and extensions) in this directory, and they will be accessible via `site.data`. If there's a file `members.yml` under the directory, then you can access contents of the file through `site.data.members`. 

- `/_includes/` - These are the partials that can be mixed and matched by your layouts and posts to facilitate reuse. The liquid tag `{% include file.ext %}` can be used to include the partial in `_includes/file.ext`

- `/_layouts` - These are the templates that wrap posts. Layouts are chosen on a post-by-post basis in the [front matter](https://jekyllrb.com/docs/front-matter/), which is described in the next section. The liquid tag `{{ content }}` is used to inject content into the web page. 

- `/_posts` - Your dynamic content, so to speak. The naming convention of these files is important, and must follow the format: `YEAR-MONTH-DAY-title.MARKUP`. The [permalinks](https://jekyllrb.com/docs/permalinks/) can be customized for each post, but the date and markup language are determined solely by the file name.

- `/_site` - This is where the generated site will be placed (by default) once Jekyll is done transforming it. It’s probably a good idea to add this to your .gitignore file. 

- `/config.yml` - Stores [configuration](https://jekyllrb.com/docs/configuration/) data. Many of these options can be specified from the command line executable but it’s easier to specify them here so you don’t have to remember them. 

- `/index.html/` or `/index.md/` and other `HTML, Markdown Files` - Provided that the file has a [front matter](https://jekyllrb.com/docs/front-matter/) section, it will be transformed by Jekyll. The same will happen for any .html, .markdown, .md, or .textile file in your site’s root directory or directories not listed above. 

- `/css/` - Describe presentation in webpage 

- `/Other Files/Folders/` - Every other directory and file except for those listed above—such as `css` and `images` folders, `favicon.ico` files, and so forth—will be copied verbatim to the generated site. 

See the [jekyll Documentation](https://jekyllrb.com/docs/)

## Installation

This site is built on a static site generator called [Jekyll](https://jekyllrb.com/). So first, check out Jekyll's [quick start guide](https://jekyllrb.com/docs/quickstart/) and [installation docs](https://jekyllrb.com/docs/installation/). 
After you have installed Jekyll and all it's dependencies, open up your terminal window and then:
- `https://github.com/TeAmP0is0N/osDFS-s-Website.git` OR
   `git@github.com:TeAmP0is0N/osDFS-s-Website.git`
- `cd osDFS-s-Website`
- `bundle install`
- `bundle exec jekyll serve` (this command watches for local changes automatically)
- Open up a browser and go to `localhoest:4000`
At any point if you find yourself confused about any of the code, [Jekyll docs](https://jekyllrb.com/docs/home/) and google are your best friends. Otherwise you can drop message in whatsapp group but firstly you have to try on your own.

## Deployment

- Run `jekyll build`
(This will generate a fresh build of the project into the `_site` folder). 

After confirming that your all changes are working properly, then you are allowed to push your code. 
