# My Colab Notebook Website

This site hosts static HTML previews of my notebooks and one-click "Open in Colab" links.

## How to use

1. Create a new GitHub repository and upload these files.
2. Edit `config.js` with your GitHub `user`, `repo`, and `branch`.
3. Create a folder `ipynb/` and upload your `.ipynb` files there.
4. Push to `main`. The GitHub Action converts notebooks to HTML into `notebooks/`.
5. Enable GitHub Pages in Repo Settings → Pages → Build and deployment → Source: `Deploy from a branch`, Branch: `main` and Directory: `/ (root)`.
6. Visit your site at the Pages URL. The homepage lists notebooks from `/ipynb/` and links to:
   - the generated HTML in `/notebooks/`
   - a Colab button that opens the GitHub copy in Colab

## Local build (optional)

If you want to convert notebooks locally instead of or in addition to CI:

```bash
pip install nbconvert jupyter
mkdir -p notebooks
jupyter nbconvert --to html ipynb/YourNotebook.ipynb --output-dir notebooks