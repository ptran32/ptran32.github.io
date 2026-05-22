# ptran32.github.io

Personal blog built with [Jekyll](https://jekyllrb.com/) and the [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) theme, deployed to GitHub Pages.

## Local preview

Requires Ruby 3.1+ and Bundler:

```bash
bundle install
bundle exec jekyll serve
```

Open http://localhost:4000

## Deploy

Push to `master`. The [GitHub Actions workflow](.github/workflows/pages-deploy.yml) builds and publishes the site.

**Important:** In the repo **Settings → Pages**, set **Build and deployment → Source** to **GitHub Actions** (not “Deploy from branch”).
