# Personal Academic Website

My personal academic website built with [Jekyll](https://jekyllrb.com/) using the [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) theme, hosted on [GitHub Pages](https://pages.github.com/).

## Structure

- `index.md` — Homepage / About
- `_pages/notes.md` — Expository writings and notes
- `_pages/blog.md` — Blog index
- `_posts/` — Blog posts
- `_pages/course.md` — Courses attended at ISI Kolkata
- `_data/navigation.yml` — Site navigation
- `_includes/head/custom.html` — KaTeX support for math rendering

## Features

- KaTeX for rendering mathematical expressions
- Author profile sidebar with links
- Responsive design

## Running Locally

Make sure you have Ruby 3.0+ and Bundler installed.

```bash
bundle install
bundle exec jekyll serve
```

Then visit `http://127.0.0.1:4000`.

## Built With

- [Jekyll](https://jekyllrb.com/)
- [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) by Michael Rose
- [KaTeX](https://katex.org/) for math rendering
- [GitHub Pages](https://pages.github.com/) for hosting

## License

The Minimal Mistakes theme is licensed under the [MIT License](https://github.com/mmistakes/minimal-mistakes/blob/master/LICENSE).