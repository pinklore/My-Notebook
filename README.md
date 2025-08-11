# My Colab Notebook Website

link: https://pinklore.github.io/My-Notebook/

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

## Enable live notebook editing

This project can turn your static previews into interactive notebooks using
[Thebe](https://github.com/executablebooks/thebe), which connects the HTML
pages to a Binder kernel. To enable this feature:

1. Download the Thebe library (for example from
   <https://unpkg.com/thebe@latest/dist/index.js>) and save it locally.
2. Copy the downloaded file into `assets/thebe.js` in this repository,
   overwriting the placeholder file. Keeping it within your repository
   avoids dependence on external CDNs that might be blocked.
3. Commit and push the updated `assets/thebe.js` file. Once deployed,
   the **Make Live** button on your site will activate interactive editing.

Without the real Thebe library in place, clicking **Make Live** will
display a message indicating that the library could not be loaded.

## Local build (optional)

If you want to convert notebooks locally instead of or in addition to CI:

```bash
pip install nbconvert jupyter
mkdir -p notebooks

jupyter nbconvert --to html ipynb/YourNotebook.ipynb --output-dir notebooks
