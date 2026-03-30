# Paal Kristian

This Hugo site uses the `paper` theme and is configured for GitHub Pages. Use the instructions below to keep the repository synchronized and let GitHub build and publish the site automatically.

## Local workflow

1. Install Hugo (the extended version is not required unless you add SCSS) and run `hugo server` while editing content from the `content/` tree.
2. Run `hugo` to emit a production copy of the site into `public/`. That directory is git-ignored because GitHub Actions builds the site before deployment.
3. Keep the theme submodule current with `git submodule update --remote --merge` (the theme lives under `themes/paper`).

## GitHub setup

1. Create a GitHub repository that will host the site (for example `https://github.com/<user>/<repo>`).
2. Set the Hugo `baseURL` in `hugo.toml` to the eventual Pages URL (`https://<user>.github.io/<repo>/` for project pages or `https://<user>.github.io/` for a user page).
3. Point `origin` at your GitHub repository and push `main`:
   ```sh
   git remote add origin git@github.com:<user>/<repo>.git # or https:// if you prefer
   git add -A
   git commit -m "Initial site"
   git push -u origin main
   ```

## Continuous deployment

GitHub Actions builds the public site and publishes it to `gh-pages` every time you push to `main`. The workflow is defined in `.github/workflows/hugo.yaml` and relies on the Hugo official action plus `peaceiris/actions-gh-pages`.

## Troubleshooting

- Adjust `hugo.toml` if you change the theme or add modules. Hugo config changes should be followed by a local `hugo` run to confirm everything still renders.
- If GitHub Pages shows an empty site, confirm the workflow finished successfully under Settings > Actions and that the Pages source branch is `gh-pages`.
