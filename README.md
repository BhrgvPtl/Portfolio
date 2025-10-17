# Portfolio (Jekyll + GitHub Pages)

## Quick start
1. **Use this repo as template** or push it to a GitHub repo (e.g., `portfolio`).
2. Go to **Settings → Pages** and set:
   - Source: *Deploy from a branch*
   - Branch: `main` / `/ (root)`
3. Your site will be at `https://<username>.github.io/Portfolio`.
   - If you name your repo `<username>.github.io`, set `baseurl: ""` in `_config.yml`.

## Customize
- Edit `_config.yml` (title, description, social links).
- Edit `index.md` for sections/projects.
- Replace images in `/images` and `pdf/resume.pdf`.

## Local preview (optional)
```bash
gem install bundler jekyll
bundle init
echo 'gem "github-pages", group: :jekyll_plugins' >> Gemfile
bundle install
bundle exec jekyll serve
```
Open http://127.0.0.1:4000/portfolio