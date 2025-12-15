This is the source code for my blog (Hugo + blogdown).

## Local preview (no R required)

If you only need to **preview the site** locally (including pages rendered to HTML already), you just need Hugo.

- **Install Hugo** (Homebrew):
  - `brew install hugo`
  - `hugo version`

- **Run the local dev server**:
  - `hugo server -D`
  - Open `http://localhost:1313/`

### Important: dev vs prod base URL

This repo uses Hugo’s modern config directory layout:

- `config/_default/config.toml`: shared config
- `config/development/config.toml`: local overrides (sets `baseurl = "http://localhost:1313/"`)
- `config/production/config.toml`: production overrides (sets canonical `baseurl`, GA ID, etc.)

If you ever see CSS/JS links pointing at production while running locally, make sure you are running Hugo in the **development** environment:

- `hugo server -D -e development`

## Authoring posts (R/blogdown workflow)

Many posts are authored as `.Rmd` under `content/post/`. Hugo ignores `.Rmd` directly, and blogdown renders them into `.html` that Hugo serves.

If you need to **create or re-render** `.Rmd` posts, use the RStudio/blogdown workflow:

1. In RStudio: `Addins > New Post`.
2. Put header images in `static/images/`.
3. For in-line static images, enable Page Bundle mode, put the image in the same directory as the file, and use a Hugo shortcode, e.g. `{{< figure src="myimg.png" title="My Title" >}}`.
4. In RStudio: `Addins > Serve Site` and make sure it looks good locally.
5. Commit the code to GitHub.
6. Confirm it deployed via [Netlify](https://app.netlify.com/).

## License

This work is licensed under a
[Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License](http://creativecommons.org/licenses/by-nc-nd/4.0/).
